---
title: "php5 and xml"
date: 2009-04-09
forum: Server Platforms
---

### Post by bas_vdl on 2009-04-09
Hello,

i have installed apache2.x and php5.x using the apt-get install method. but my server is not supporting the build in xml from php5.

did i forgot something?


ERROR: Fatal error: Call to undefined function domxml_new_doc()

---

### Post by hyper_ch on 2009-04-09
I guess you need some of those packages:

php5-xmlrpc - XML-RPC module for php5
libapache2-modxslt - XSLT processing module for Apache 2.x based on libxml2
php-xml-htmlsax3 - SAX parser for HTML and other badly formed XML documents
php-xml-parser - PHP PEAR module for parsing XML
php-xml-rss - RSS parser
php-xml-serializer - swiss-army knife for reading and writing XML files
php-xml-util - a XML utility for php-pear

---

### Post by bas_vdl on 2009-04-09
Thxnk, i installed all but it is still not working, same error.

i restarted en reloaded apache

---

### Post by Dr Small on 2009-04-09
This is just about all the info I can find on it:
[http://www.php.net/manual/en/domxml.installation.php](http://www.php.net/manual/en/domxml.installation.php)

Maybe it's pear module

---

