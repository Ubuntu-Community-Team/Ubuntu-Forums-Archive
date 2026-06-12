---
title: "apache2 chokes on folder named 'icons'"
date: 2013-02-10
forum: Server Platforms
---

### Post by GordThompson on 2013-02-10
Just finished my first website move from IIS on Windows to Apache on Ubuntu 12.04 LTS Server. It went quite smoothly, but there was one "gotcha":

The site had a directory named 'icons' that contained a bunch of .bmp files. On the old server (IIS) a link like...

[http://sitename/icons/foo.bmp](http://sitename/icons/foo.bmp)

...would retrieve the file. On the new Ubuntu server (Apache) the same link produced a "File not found" error. 

After checking for mismatched case and verifying that .bmp had a registered MIME type I decided to enable directory listing on the 'icons' folder, but no matter what I did Apache always gave me a "Forbidden" error.

Finally, after verifying that I *could *browse a folder named 'stuff' I renamed the 'icons' folder to 'icon_files' and my problems went away.

So, could someone please give me a hint as to why a folder named 'icons' is (apparently) evil? This is a straight-up 12.04 Server install with LAMP as configured by `tasksel`.

Thanks!

---

### Post by Doug S on 2013-02-10
I am not an expert, but I think that the "icons" directory, by default, is a reserved alias to "/usr/share/apache2/icons/". See "/etc/apache2/mods-available/alias.conf", where is says you can comment it out if you want.
 
Hope this helps.

---

### Post by GordThompson on 2013-02-10
> **Doug S said:**
> I am not an expert, but I think that the "icons" directory, by default, is a reserved alias to "/usr/share/apache2/icons/". See "/etc/apache2/mods-available/alias.conf", where is says you can comment it out if you want.
 
Hope this helps.
Aha! It certainly does help. Thanks, Doug!

For the record, I just confirmed that /icons causes problems when that alias is enabled, but /foo/icons works okay....

---

