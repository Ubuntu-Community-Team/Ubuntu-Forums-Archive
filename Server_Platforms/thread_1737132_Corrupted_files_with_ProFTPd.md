---
title: "Corrupted files with ProFTPd"
date: 2011-04-23
forum: Server Platforms
---

### Post by Annielover on 2011-04-23
Hello,

I'm having problems with the ftp-server ProFTPd,
If I transfer files from a Linux host to a Windows client, it says that my transfered files are damaged, so I'm unable to open them...

I've searched this forum and several people say I have to set the default transfer mode to 'binary' mode.
I did that, but it didn't work at all for me... so despite the binary transfer mode my files are still damaged when I transfer them.

when I do it through SSH, it works fine, so the problem is the FTP-server...
What do I wrong??

I use Ubuntu Server 10.04.2 with proFTPd 1.32...

Thanks!!

---

### Post by falko on 2011-04-23
Any errors in your logs? 

What FTP client do you use? Have you tried another one?

Did you try both active and passive transfers in your FTP client?

---

### Post by Annielover on 2011-05-02
Here are some screenshots of my log file...

[IMG]http://img571.imageshack.us/i/ftp2.png/[/IMG] [IMG]http://img17.imageshack.us/i/ftp1p.png/[/IMG][http://img17.imageshack.us/i/ftp1p.png/](http://img17.imageshack.us/i/ftp1p.png/)

[http://img571.imageshack.us/i/ftp2.png/](http://img571.imageshack.us/i/ftp2.png/)

But I don't think there are errors in it...

I use FileZilla Client as ftp client and sometimes Mozilla Firefox, but it doesn't matter which one I use, they all give the same error when I open it: "the file is corrupt".

---

### Post by Annielover on 2011-05-02
Normally I use passive mode, however, when I try to use active mode it gives me the following error:  [COLOR=Red]ECONNABORTED[/COLOR] [COLOR=Red]- connection aborted[/COLOR]

I did it with filezilla client.

Here's my config file, you can open it with Wordpad :-)

[http://www.fileserve.com/file/jjD29vR](http://www.fileserve.com/file/jjD29vR)

---

