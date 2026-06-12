---
title: "ssh copy files single multiple"
date: 2013-10-05
forum: Server Platforms
---

### Post by remo2 on 2013-10-05
How do you take a secure FTP connection to serwer for?
With what command you are copying a single file from serwer to a portable?
With what command you copy multiple files  from serwer at once to a portable?

---

### Post by Lars Noodén on 2013-10-05
You [can't use FTP for secure transfers](http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp).  You can use Anonymous FTP for public file download, but that is something special.  Use SFTP instead.  That's built into Nautilus and the other file managers.  Press ctrl-L and then enter the URI of your remote server. e.g. *sftp://remo2@someserver.example.org/home/remo2/*  From there it's drag and drop.  

If you use the regular text based [sftp](http://manpages.ubuntu.com/manpages/raring/en/man1/sftp.1.html) client then you can use *get -r* to recursively transfer files.  See the manual page for sftp(1) for details.

---

