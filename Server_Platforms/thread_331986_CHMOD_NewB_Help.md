---
title: "CHMOD NewB Help"
date: 2007-01-05
forum: Server Platforms
---

### Post by zempher on 2007-01-05
I have an FTP server that receives images from an IP camera on a constant 15 minute basis.  I then use cron to run a script which renames the file and places it in a different folder for "http" reasons.  Here is my problem...

Regardless of what chmod changes I make, I cannot get the new files to inherit the security I want.  Basically, I need for the posted .jpg file in the /var/www folder to allow anyone to read, but only a specified user to write.  As for the FTP, I need for anonymous users to always be able to read and execute, but not write.  

At first I tried chmod -R 755 /<ftp directory>.  I then changed to chmod -R 705 />ftp directory>.

What am I doing wrong, because any file changes after the chmod do not inherit the applied security.

Thanks and please be kind, as I am very new to Ubuntu!

---

### Post by kingmonkey on 2007-01-05
you dont need to be able to execute jpg files. 644 permission would be ideal for you.

Are you running chmod from cron? As which user are you running chmod from? and who owns the jpg files?

---

### Post by zempher on 2007-01-05
no, I am not running chmod from cron and I am using root to run chmod.  As for the jpg files, it is a specified user.  I will try the following:

chmod -R 644 /ftp directory

Thanks

---

### Post by zempher on 2007-01-05
OK - that was scary.  I ran the 644 chmod and discovered the nothing worked at all..., file systems access, desktop access, etc.  After going into recovery mode, I was able to reverse the action.

Any other suggestion?

---

### Post by rth on 2007-01-05
```
chmod -R 644 /ftp_dir_goes_here
```
That should set your FTP (and all subfiles and subdirectories) directory to R/W for owner, read for group, and read for everyone else. Is there anything in particular that is in your FTP directory? I can see 644 breaking lots of stuff if you do it to "/" or "/home" or any other important folder that has lots of things under it.

Using the same command on the "/var/www" directory should also accomplish what you wish as long as you also change the ownership to the user account that you are concerned about. root should have access to the files regardless... But the same applies, everything in that directory and its subdirectories will receive the new permissions, so if something under there needs to run with different permissions, this will break it.

---

