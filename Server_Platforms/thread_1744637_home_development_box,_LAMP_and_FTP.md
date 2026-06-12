---
title: "home development box, LAMP and FTP"
date: 2011-04-30
forum: Server Platforms
---

### Post by JohnWillyam on 2011-04-30
using 10.10 server I installed the LAMP package and vsftpd.
 
I'm just not sure how I should approach the solution appropriately.
 
I can ftp to /home/jonw/
and I can view the default web files served out of /var/www/
but neither are together so it's not useful for me.
 
So, I tried to set the default apache virtual server to /home/jonw/website/ (mkdir and copied the default page to there) but I get 403 forbidden.
 
And I've tried to set the ftp directory to /var/www/ but then I'm not allowed to upload like that.
 
I'm assuming I need to do something good with groups and permissions, but it seems like there's various solutions(and opening root seems dumb). And I'm not familiar enough to really know what that is.
 
perhaps I can symlink some stuff?
 
I'd like to make it as easy as our game-clan-rented-server, so I can simply use ftp directly on the website files and they will immediately show up without me having to ssh and go adjust permissions or something.
 
Also there's a friend that will occasionally up/download files, and I have no problem just giving him my direct account info, but it might not be hard to just set him up with the same access properly.
 
what's a good design paradigm here?

---

### Post by Lars Noodén on 2011-04-30
Since you have SSH already installed you might try upgrading to SFTP instead of FTP.  It will be easier to manage.  Filezilla, Nautilus and other common clients support SFTP.

For the directories, make a group like 'webmasters' or something and change the directory to be in that group and then set the directory to be writable by that group.  Be sure you are in that group, too.

---

### Post by JohnWillyam on 2011-04-30
does this seem right?
 
It appears to work, at least re-uploading that index file.
```
 
 
jonw@fubunty:~$ sudo addgroup webmasters
jonw@fubunty:~$ sudo adduser jonw webmasters
 
jonw@fubunty:~$ sudo chown -R jonw:webmasters /home/jonw/website/
 
jonw@fubunty:~$ ls -la /home/jonw/website/
total 28
drwxrwxr-x 2 jonw webmasters  4096 2011-04-30 15:01 .
drwxrwxrwx 5 jonw jonw        4096 2011-04-30 13:38 ..
-rw-r--r-- 1 jonw jonw         192 2011-04-30 15:01 index.html
-rwxrwxrwx 1 jonw webmasters 12797 2011-04-30 00:04 _real-config.cfg
 

```
 
although I'm not really sure what changed to where apache is now serving those files without a problem. I thought apache needs to own it, or have rights to it? or the user or group needs to be in the apache data group?
 
anyway, I guess it works.

---

### Post by Lars Noodén on 2011-05-01
Looks good except for _real-config.cfg, which should be not be universally writable. Set it to 664 or something like that.  Same for the directory jonw, which should be 775 or 755.

> **JohnWillyam said:**
>  I thought apache needs to own it, or have rights to it? or the user or group needs to be in the apache data group?
 

It shouldn't own it.  Apache only needs to be able to read the directory.  That's doable if the directory permissions are set  to 755 or 775 or even 555.  If it can write to the directory then there are a lot of security concerns.

You can also set the sticky bit for group (g+s) 2775.

---

### Post by JohnWillyam on 2011-05-01
ok great, thank you very much Lars.
 
yea, the permissions were botched because I had been messing around the day before trying to get it to work.
 
I didn't understand the permission relationship very much.
 
I've set it like you mentioned and it's all fine.  In fact I confirmed (simply with filezilla client) that the permissions are the same setup as our rented server so that's probably a good thing.
 
thanks again!

---

