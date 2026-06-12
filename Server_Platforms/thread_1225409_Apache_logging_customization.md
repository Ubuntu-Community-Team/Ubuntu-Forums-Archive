---
title: "Apache logging customization"
date: 2009-07-28
forum: Server Platforms
---

### Post by Cyked on 2009-07-28
So I use PHP with Apache on a page basically as a photo album, so anytime I hit a page 24 thumbnails load, which means 24 hits are logged into access.log.  As you can imagine that might cause an issue especially if I'm testing things (for example an access.log file with 820k+ lines).

I looked at the Apache conf file and see the default CustomLog entry, but I see NOTHING referencing logging to access.log.  Where would this exist?  I assume if I create a CutstomLog line in the Apache conf file I would be logging to that new location AND access.log?  I don't want to change it, just trying to understand where this configuration is.

Also, regarding the "PHP issue", can I customize Apache logging to NOT log for anything .php?  I'd like to log GET requests for images/files, but not when PHP is doing the getting.  

I'm probably looking at this from the wrong angle, but I want to be selective in what is logged if I can.

---

### Post by Cyked on 2009-07-29
Any thoughts?

---

### Post by FerociousTwig on 2009-07-29
Well, first of all all apache config files that I know of are in /etc/apache2/ so my first guess is to look in there.

Once you find somewhere you can edit, I would suggest a python script to simply clear all the log's lines that deal with the info you don't want. I'm not that experienced with logging in apache so I can't really help other than to point you where to start. Good luck!

---

### Post by Cyked on 2009-07-30
> **FerociousTwig said:**
> Well, first of all all apache config files that I know of are in /etc/apache2/ so my first guess is to look in there.

Once you find somewhere you can edit, I would suggest a python script to simply clear all the log's lines that deal with the info you don't want. I'm not that experienced with logging in apache so I can't really help other than to point you where to start. Good luck!

I was thinking of something like another script to clear lines I don't want.  I've looked at the Apache config files and don't think there is anything I can do with that to accomplish what I want.  I still don't understand where the access.log file is declared.  I assume it has to be set somewhere in an Apache file somewhere...

---

