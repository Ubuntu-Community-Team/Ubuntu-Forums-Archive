---
title: "Precendence of DirectoryIndex on Apache2"
date: 2007-07-03
forum: Server Platforms
---

### Post by rumblestrut on 2007-07-03
I'm working on a project where I've got an index.shtml file and an index.php file side-by-side in a directory.
My httpd.conf file shows the DirectoryIndex like this:

DirectoryIndex index.shtml index.html index.php index.html.var index.HTM

It's my understanding that with the above order, index.shtml would take precedence over index.html, index.shtml would take precedence over index.php and so on.

What I'm wanting to do is to have index.shtml and index.php in the same directory, but when a user visits [www.mysite.com](www.mysite.com), the index.shtml shows up by default and not the index.php. When I'm done with index.shtml, I'll delete it, which would cause index.php to bump to the top of the list.

However, index.php is overriding index.shtml. Any ideas on how I can get index.shtml to override index.php?

---

### Post by bashologist on 2007-07-03
That's looks right to me, although I don't know much about servers. Maybe you need to restart apache? I think the command's "apache2-restart". Make sure you saved it too; you might not have write permissions.

---

### Post by rumblestrut on 2007-07-03
I did a restart and the permissions are exactly the same on both files. Index.php is still showing up over index.shtml.

> **bashologist said:**
> That's looks right to me, although I don't know much about servers. Maybe you need to restart apache? I think the command's "apache2-restart". Make sure you saved it too; you might not have write permissions.

---

### Post by bashologist on 2007-07-04
What about case sensitivity? You have one capitalized and the other lowercase.

---

### Post by rumblestrut on 2007-07-04
Nope, that has nothing to do with it, since the index.HTM is last, making it the lowest in precedence order. All I'm working on is index.shtml and index.php, which I have lowercase in the conf file and with my files on the server.

---

### Post by MJN on 2007-07-05
Do you have any other instances of DirectoryIndex that may be overriding the one quoted? Try [B]grep -ir directoryindex /etc/apache2/

[/B]Presumably you can explicitly identify <domain>/index.shtml in a browser and you do get it? (just checking that the file is present and working)
Mathew

---

### Post by rumblestrut on 2007-07-05
MJN,

Yep, that was it. (I really need to learn more about grep.)

It was the php conf file overriding the httpd.conf file. Glorious!

Thanks a bunch!

Eric

---

### Post by MJN on 2007-07-05
Great!

---

