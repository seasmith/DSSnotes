#Notes

###Components of Tidy Data
* Raw data - the file from which data is taken; the original format
  * No software or processing associated with data
  * No manipulation
  * No summarization
* Tidy data - processed data that is ready for analysis
  * One variable per column (readable variables)
  * Unqiue rows
  * One table for every kind of data (one file per table)
  * Multiple tables should have foreign keys
* Code book - meta data; explains variables and what the data are trying to say
  * Information about variables (units, etc)
  * Information about summary choices (was mean and median taken in addition to total?)
  * Experimental study design
  * Markdown file format
* Recipe - exact and explicit detailing of steps taken to go from one data format (raw) to the next (tidy)
  * A computer script
  * Input is the raw data
  * Outpus is processed data (tidy data)
  * No parameters to the script (everything is fixed and ready-to-go)
  * Explicitly state steps that cannot be script

###Downloading Files
* Download through R to include in scripts that you can share
* Record the date when you download a fiel (in case it changes at a later date)
* `download.file()` = download file from the internet (especially text)
  * `url` = website
  * `destfile` = where to download on computer (and what file format i.e. .csv, .txt, .las, etc)
  * `method` = secured? (https)

###Reading Local Files
* `read.table()` = read data into R
  * `quote` = sets the characters that represent a quote
  * `na.strings` = sets the character that represents missing values (i.e. "Missing Value")
  * `nrows` = how many rows to read
  * `skip` = number of lines to skip

###Reading Excel Files
* `library(xlsx)`
  * `read.xlsx()`
    * `dest` = file path
    * `sheetIndex` = which worksheet (based on ordinal position)
    * `header` = is there a header? (`TRUE` or `FALSE`)
  * `read.xlsx2()` = faster than `read.xlsx()` but unstable for reading subsets of rows
* `library(XLConnect)` = for a lot of processing

###Reading XML
* Tags = labels defining the category or type
  * `<start></end>`
  * `<empty />`
* Element = what is inside the tag
  * `<tag>this is the element</tag>`
* Attribute = components of the tag/label
  * `<tag an-attribute = "2">`
* `library(XML)` = reads XML files
  * `rootNode` = `rootNode[[1]]` returns the first element; `rootNode[[1]][[1]]` extracts the first subnode of the first root node
* XPath - HTML stuff; see: http//www.stat.berkley.edu/~statcur/Workshop2/Presentations/XML.pdf
  * `/node` = top level node
  * `//node` = node at any level
  * `node[@attr-name]` = node with an attribute name
  * ` node[@attr-name='bob']` = node with an attribute name attr-name='bob'
  * `xpathSApply()`
    * `rootNode` = the root node
    * `//node` = the name of the node
    * `xmlValue` = the XML value (elements)