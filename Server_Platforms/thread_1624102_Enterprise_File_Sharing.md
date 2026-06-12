---
title: "Enterprise File Sharing"
date: 2010-11-17
forum: Server Platforms
---

### Post by hambone79 on 2010-11-17
I wanted to see if anyone knew of a system that can be used for sharing files between companies? What I am looking for is a web based system that will allow an engineer to upload drawings or CAD models and put them in a "mailbox" for someone at another company. Here are the requirements I need:

1. Any type of file can be uploaded with no restrictions of file size (needs to be able to handle several GB of CAD data).
2. Only the person who the files are intended for can see or download the files.
3. A record of all transactions (uploads & downloads) must be kept.

Basically, I need a web based mailbox system that can handle huge files. Anyone know of such a beast?

---

### Post by Vegan on 2010-11-17
I use SAMBA for file server services on my Linux box. CITADEL is the tool I am using for email and other services.

WEBMIN can manage SAMBA from a browser and CITADEL is browser based as well.

email systems are unsuitable for large files. Better is to use FTP which can be managed with VSFTPD readily.

---

### Post by CharlesA on 2010-11-17
Wouldn't a normal secured ftp server handle that?

I've used [Cerberus FTP]("http://www.cerberusftp.com/") before, but it only runs on a Windows box.

---

### Post by HermanAB on 2010-11-17
Howdy,

Actually, the best way to share engineering schtuff is with Subversion over a SSL link, because it allows you keep track of the versions and users very easily.

You can get a pre-installed SVN VM here: [http://bitnami.org/](http://bitnami.org/)  and you can get WinSVN here: [http://www.winsvn.org/](http://www.winsvn.org/)

---

### Post by koenn on 2010-11-17
I concur 
(always have wanted to say that)

the traditional way of doing this would be ftp - it's this sort of thing it was invented for. and todays ftp clients aren't any more complicated than the a web browser or a mail client, so users shouldn't have trouble with it.

Working out the server side, especially "2. Only the person who the files are intended for can see or download the files." might require some thought and tweaking : people need write access to put the file their, yet noone can see or download it(except 1 specific user) ... hm.


I also like Herman's idea of using svn as a document repository

---

### Post by druhboruch on 2010-11-17
I just setup IFolder from the ppa.
Works great for my company and our clients.

---

