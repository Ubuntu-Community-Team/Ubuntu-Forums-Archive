---
title: "moving files"
date: 2006-10-22
forum: Server Platforms
---

### Post by mzracer360 on 2006-10-22
I have files in /var/www/HLstatsX/web and I need to move them to /var/www/HLstatsX and remove the web folder.  How do I do this?  I know i need to use the mv command, but how?

---

### Post by Ronbo on 2006-10-22
If the files are in the folder '/var/www/HLstatsX/web' and you want to move them into the folder '/var/www/HLstatsX' just use either:

to move
> sudo mv /var/www/HLstatsX/web/* /var/www/HLstatsX/* 

or copy
> sudo cp /var/www/HLstatsX/web/* /var/www/HLstatsX/*

(with a space between the 2 directories on each command, kinda hard to see)

these will copy or move everything in /var/www/HLstatsX/web.


How'd you make out with the webserver?

Edited - thanks for the tip Meng, I need to get out of MS mode.

---

### Post by meng on 2006-10-22
Minor correction - you don't use the form *.*, just * is sufficient.
*.* is harking back to DOS/Windows, it's not a relevant form in Linux.

---

### Post by meng on 2006-10-22
In fact a more straightforward way is:
cd /var/www/HLstatsX/web [this changes your working directory]
mv * .. [this moves everything to the parent directory]
cd .. [this moves to the parent directory]
rmdir web [this removes the directory]

You may need to prepend the 2nd and 4th command with sudo, i.e.
sudo mv * ..
sudo rmdir web

---

### Post by mzracer360 on 2006-10-22
Thanks for the quick replies, im still learning how to work without GUI and a mouse lol.  While we are on this topic, is there a command to view the items inside a folder?

---

### Post by bunnynuts on 2006-10-22
use ls for the list, ls -l is useful, and ls -a comes in handy at times too...or ls -la if you please.

---

### Post by meng on 2006-10-22
ls is akin to dir if you're an MS user!
ls -l gives a long listing (more detail)
ls -a shows hidden files
ls -la gives both!

---

### Post by mzracer360 on 2006-10-25
I have another problem with moving files.  I had files in "/var/www/motd/" but decided I wanted them in "/var/www/srcds/".  So I did ```
$ sudo mv /var/www/motd/* /var/www/srcds/*
```  Now instead of having the files in "/var/www/srcds/", I now have them in "/var/www/srcds/motd/".  How to I get it so the files are in the  "srcds" folder not "motd"?

---

