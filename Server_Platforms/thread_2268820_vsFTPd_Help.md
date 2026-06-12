---
title: "vsFTPd Help"
date: 2015-03-11
forum: Server Platforms
---

### Post by ThePie on 2015-03-11
Hello,

 I saw a thread on [Easy FTP with vsftpd]("http://ubuntuforums.org/showthread.php?t=518293"). I made a thread [HERE ]("http://www.raspberrypi.org/forums/viewtopic.php?f=31&t=98149&p=713961#p713961")a few days ago on Raspberry Pi forums cause this is what I'm running this on. It was a continuation of what I've been setting up so *you can see what I've done so far *on that thread.

I also saw this thread [HERE ]("http://ubuntuforums.org/showthread.php?t=2264954&highlight=vsftpd")about vsftpd solution for some small health company. Thought I should post it cause some where saying that vsftpd is unsecure now it seemed like. It posted 4 weeks ago.

Anyways,
 I'm trying to FTP into the directory where my Apache is getting the files from off my USB. But I'm getting the error below.
 ```
[FONT=Courier New]500 OOPS: vsftpd: refusing to run with writable root inside chroot()[/FONT]
``` when I try to log in to it. 
Also I never specified any users or anything or like that. Which I saw some one else doing. I'm just using the Pi user.

[FONT=arial] Is there a way so you can allow to write files to the root? Also technically I'm not writing files to the folder im specifying which is 
[/FONT][FONT=Courier New]/media/external/var
[/FONT][FONT=arial]but the files are being written to the www folder. So no changes would ever be written to the var folder.
 [/FONT][FONT=courier new]/media/external/var/www[/FONT]

 Thanks in advance.

---

### Post by Thirtysixway on 2015-03-19
> **ThePie said:**
> Hello,

 I saw a thread on [Easy FTP with vsftpd]("http://ubuntuforums.org/showthread.php?t=518293"). I made a thread [HERE ]("http://www.raspberrypi.org/forums/viewtopic.php?f=31&t=98149&p=713961#p713961")a few days ago on Raspberry Pi forums cause this is what I'm running this on. It was a continuation of what I've been setting up so *you can see what I've done so far *on that thread.

I also saw this thread [HERE ]("http://ubuntuforums.org/showthread.php?t=2264954&highlight=vsftpd")about vsftpd solution for some small health company. Thought I should post it cause some where saying that vsftpd is unsecure now it seemed like. It posted 4 weeks ago.

Anyways,
 I'm trying to FTP into the directory where my Apache is getting the files from off my USB. But I'm getting the error below.
 ```
[FONT=Courier New]500 OOPS: vsftpd: refusing to run with writable root inside chroot()[/FONT]
``` when I try to log in to it. 
Also I never specified any users or anything or like that. Which I saw some one else doing. I'm just using the Pi user.

[FONT=arial] Is there a way so you can allow to write files to the root? Also technically I'm not writing files to the folder im specifying which is 
[/FONT][FONT=Courier New]/media/external/var
[/FONT][FONT=arial]but the files are being written to the www folder. So no changes would ever be written to the var folder.
 [/FONT][FONT=courier new]/media/external/var/www[/FONT]

 Thanks in advance.

[https://www.benscobie.com/fixing-500-oops-vsftpd-refusing-to-run-with-writable-root-inside-chroot/](https://www.benscobie.com/fixing-500-oops-vsftpd-refusing-to-run-with-writable-root-inside-chroot/)

---

