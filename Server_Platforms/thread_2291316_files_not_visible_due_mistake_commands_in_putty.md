---
title: "files not visible due mistake commands in putty"
date: 2015-08-19
forum: Server Platforms
---

### Post by Pischus on 2015-08-19
hi, 

i did a really stupid mistake on my server. 

I was creating new entries in /etc/apache2/sites-available/default (no-auth), and wanted to create the symbolic link in /var/www, which worked always fine.  But somehow i copied the whole text in /default (no-auth) and copied it into putty as root user. - i know really stupid

without pressing enter putty started running the copied text.

After that i was unable to access ne new added sites = permisssion denied. 
After checking, all files seem to be gone, but HDD is still uses the same amount of space, like the files are still there. But i don't see them. 

EDIT: all files got moved to another folder and i was able to locate them.

---

