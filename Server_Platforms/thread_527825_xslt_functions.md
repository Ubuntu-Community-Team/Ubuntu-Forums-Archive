---
title: "xslt functions"
date: 2007-08-17
forum: Server Platforms
---

### Post by q-rios on 2007-08-17
I would like to test the xslt functions of php.
Than i installed php5-xlst with apt-get and I restarted the Apache deamon.
phpinfo() gives me this informations:

/etc/php5/apache2/conf.d/xsl.ini 
 
xsl 
XSL 	enabled 
libxslt Version 	1.1.20 
libxslt compiled against libxml Version 	2.6.27 
EXSLT 	enabled 
libexslt Version 	1.1.20

But the functions are not available.
I've tested it with:

[PHP]<?php
functions_exists('xslt_create') or die('not found');
?>[/PHP]

The result was: not found


(Sorry my english is bad :/)

---

### Post by q-rios on 2007-08-18
anyone? :(

---

