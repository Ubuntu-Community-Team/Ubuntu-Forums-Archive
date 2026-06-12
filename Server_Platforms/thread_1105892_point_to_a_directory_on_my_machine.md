---
title: "point to a directory on my machine"
date: 2009-03-25
forum: Server Platforms
---

### Post by funkyali on 2009-03-25
Hi

I did a the normal LAMPP installation on my ubuntu machine. I know my installation is stored under /opt/lampp and my webpages are under /opt/lampp/htdocs.

My question is how do I point to another directory in PHP. I want to point to /opt/lampp/web_site_copy/pictures

Do i need to make changes to my apache config file and if so how do i do it?

I looked throught my phpinfo() and doc_root is not specifed and neither is user_doc.

I am new at using php/apache so please bear with me and thanks for the support its really appreciated.
[PHP]<?php
$dir    = '/tmp';
$files1 = scandir($dir);
$files2 = scandir($dir, 1);

print_r($files1);
print_r($files2);
?>[/PHP]



When I run this code it does return some values but I'm not sure where there "tmp" directory is.

---

### Post by BkkBonanza on 2009-03-25
You're asking how to reference various directories in php. There are two ways. 1. any path that doesn't start with '/' is relative to the directory your script is running in. 2. any path that starts with '/' is absolute and starts from root.

/tmp means the directory named tmp at the root level.
tmp means the directory named tmp in the current script directory.

You should run through a tutorial on linux/unix basics before starting to program. It will be less confusing and much easier to find your way around. Use Google. There are heaps of tutorials for linux basics out there.

To answer your first question: 

$dir = '/opt/lampp/web_site_copy/pictures';

---

