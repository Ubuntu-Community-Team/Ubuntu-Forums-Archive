---
title: "index.php in dir (apache2)"
date: 2005-12-14
forum: Server Platforms
---

### Post by zhorty on 2005-12-14
Hi.
I'm running apache2 with php4, and it works fine. But in a directory I have an index.php (or .html) file, the file doesn't "auto open" in the dir. Just check here: [http://pysjamas.sytes.net/hentai/](http://pysjamas.sytes.net/hentai/)

How do I fix this?
Thanks!

---

### Post by slazh on 2005-12-14
> 
You also may want to allow index.php to be a directory index. To do this, simply add index.php (or filename of your choice) to the DirectoryIndex line:

<IfModule mod_dir.c>
DirectoryIndex index.html index.htm index.php
</IfModule>

[http://www.sanbeiji.com/tech/tutorials/php/index.php](http://www.sanbeiji.com/tech/tutorials/php/index.php)

PS: Hentai ey? :cool:

---

### Post by lutrafobic on 2005-12-14
step-by-step:

```
sudo nano nano /etc/apache2/apache2.conf 
```
(inside nano) press CTRL-W and enter keyword:  index.html

You should then find a row looking something like this:
```
DirectoryIndex index.html index.cgi index.pl index.xhtml
```

Were you simply go to the end of the row and enter: index.php

cheers

---

### Post by NotJustANewbie on 2005-12-14
> PS: Hentai ey? ;) lol

---

### Post by zhorty on 2005-12-14
Ah, thanks guys. Works fine now :) 

And it's just a fun name for my counter-strike clan :p

---

