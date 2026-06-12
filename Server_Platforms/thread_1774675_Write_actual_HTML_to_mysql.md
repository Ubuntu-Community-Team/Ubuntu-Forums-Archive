---
title: "Write actual HTML to mysql"
date: 2011-06-03
forum: Server Platforms
---

### Post by CrusaderAD on 2011-06-03
If I have a ton of html files and folders... is it possible to write a php script that will open each one, pull the file name and then write the name and all html in the file to mysql fields?

---

### Post by elico on 2011-06-04
i think its useless to put the html files in a MYSQL database.
you most likely would like to use mysql to list the files location only and this is also almost useless.
filesystem is most likely the best way to use these files cause it will be much faster.

but it depends on the purpose of the DATABASE...

---

### Post by dtfinch on 2011-06-04
I agree it's generally a bad idea, compared to just reading the files.

To do it, you'd probably want to use either opendir() and readdir(), or scandir(), to read the directory. Then file_get_contents() to read each file as a string. When inserting into the database, you'll need to either escape the file contents with mysql_real_escape_string() or use prepared/parameterized queries.

---

### Post by Lars Noodén on 2011-06-04
If all you are trying to do is to make a searchable index, then there  are a lot of ready-to-use tools available.

Here are three:

Solr: [http://lucene.apache.org/solr/](http://lucene.apache.org/solr/)
Swish-E: [http://swish-e.org/](http://swish-e.org/)
Xapian: [http://xapian.org/](http://xapian.org/)

---

### Post by CrusaderAD on 2011-06-05
Hey thanks for all the replies. I'm not trying to read from the mysql and display it in the browser... I just want the datin from my HTML files to be put into a mysql field. I hope that makes sense :) I know it's a little unusual.

---

### Post by SeijiSensei on 2011-06-05
> **CerealCypher said:**
> If I have a ton of html files and folders... is it possible to write a php script that will open each one, pull the file name and then write the name and all html in the file to mysql fields?

To answer this original question, yes you can.  It's probably easiest if you embed the PHP script in a bash script and let it iterate over the files and directories.  Something like:

```

#!/bin/bash

cd /path/to/HTML/directory

for f in *.html
do php /path/to/myscript.php $f
done


```

Use $argv[1] in PHP to get the filename from the command string.  You can read the entire file into a string with file_get_contents() then write it to the MySQL database.  You might want to use htmlentities() on the pages before storage to avoid problems with special characters and quotes. Alternatively make sure you use addslashes() to ensure that any single quotes are handled correctly.

I don't know why you're doing this, but like others I thought perhaps you wanted to create a search index.  If so, I strongly recommend using [Sphinx]("http://sphinxsearch.com/") for this purpose.  It's designed to index fields in a database, and it's blazingly fast when queried.

---

### Post by Lars Noodén on 2011-06-05
Like for anything else, there are perl modules for parsing HTML, [HTML:: Parser](http://search.cpan.org/~gaas/HTML-Parser-3.68/Parser.pm),[HTML::TokeParser](http://search.cpan.org/~gaas/HTML-Parser-3.68/lib/HTML/TokeParser.pm).  Both can extract what ever elements you want and then you can use DBI to insert (*) into the MySQL database.

A normal XML parser would work too but the HTML parsers are much more tolerant of defective XML.


(*) Note that if you use the API, place holders and the prepare/execute statements then your script should be rather secure as far as MySQL goes.

---

