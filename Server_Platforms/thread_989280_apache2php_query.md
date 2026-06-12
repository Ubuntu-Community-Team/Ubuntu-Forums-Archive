---
title: "apache2/php query"
date: 2008-11-21
forum: Server Platforms
---

### Post by mfraser on 2008-11-21
I've recently started using php on my website and wanted to be able to try out the site locally before uploading, so I decided to install apache2 and php5 on my computer.

It all seems to be working apart from the fact that whenever I try to use the php variable $_SERVER["DOCUMENT_ROOT"] it points to [http://localhost/var/www/](http://localhost/var/www/) instead of just [http://localhost/](http://localhost/).

For example I've got /var/www/index.php and in a menu <a href='<?php echo $_SERVER["DOCUMENT_ROOT"] ?>index.php' class="link">Home</a> where I would expect it to be [http://localhost/index.php](http://localhost/index.php) I'm getting [http://localhost/var/www/index.php](http://localhost/var/www/index.php) which doesn't exist.

---

### Post by cdenley on 2008-11-21
$_SERVER['DOCUMENT_ROOT'] is the LOCAL path to your document root (/var/www). The URI equivalent would always be "/". If you want the URI for the current script, that would be $_SERVER['PHP_SELF']. What exactly are you trying to accomplish?
[http://php.net/manual/en/reserved.variables.server.php](http://php.net/manual/en/reserved.variables.server.php)

---

### Post by mfraser on 2008-11-21
My website consists of a menu.php and index.php in the main directory with various subdirectories containing their own index.php which include the menu.php.

If I'm viewing one of the index pages the menu links don't point to the right places.

At the moment I've given up with using $SERVER and instead have different menu.php for the different levels of subdirectories which seems to work.

---

### Post by cdenley on 2008-11-21
> **mfraser said:**
> My website consists of a menu.php and index.php in the main directory with various subdirectories containing their own index.php which include the menu.php.

If I'm viewing one of the index pages the menu links don't point to the right places.

At the moment I've given up with using $SERVER and instead have different menu.php for the different levels of subdirectories which seems to work.

You still haven't explained what you are expecting from the $_SERVER variables. Why don't you just make your menu:
[HTML]
<a href="/index.php">index</a><br/>
<a href="/menu.php">menu</a><br/>
<a href="/subdir/index.php">subdir</a>
[/HTML]

---

### Post by mfraser on 2008-11-21
My website's tree is:

index.php
|
/downloads - index.php
|
/gallery -
         |
        /2007 - index.php
         |
        /2008 - index.php

/waug - index.php

etc...

in the top level with the main index.php is a menu.php which I've included into all pages with

[PHP]<?php include("menu.php"); ?>[/PHP]


If I try to select menu items from pages in a subdirectory, the page isn't found as it's looking in the wrong place. eg. if I'm in /gallery/2008 and I click on 'home' I'll be trying to go to /gallery/2008/index.php instead.

I wanted some way of having all links relative to the main directory using $_SERVER["DOCUMENT_ROOT"], but it looks like that variable doesn't work that way.

---

### Post by cdenley on 2008-11-21
> **mfraser said:**
> My website's tree is:

index.php
|
/downloads - index.php
|
/gallery -
         |
        /2007 - index.php
         |
        /2008 - index.php

/waug - index.php

etc...

in the top level with the main index.php is a menu.php which I've included into all pages with

[PHP]<?php include("menu.php"); ?>[/PHP]


If I try to select menu items from pages in a subdirectory, the page isn't found as it's looking in the wrong place. eg. if I'm in /gallery/2008 and I click on 'home' I'll be trying to go to /gallery/2008/index.php instead.

I wanted some way of having all links relative to the main directory using $_SERVER["DOCUMENT_ROOT"], but it looks like that variable doesn't work that way.

I already posted what you should do. Just make all the links absolute!
[HTML]
<a href="/index.php">index</a>[/HTML]
That will work no matter which page you put it on. The root URI will always be "/".

---

### Post by mfraser on 2008-11-21
Thanks cdenley, it works. Should've tried the simple answer first!!

---

