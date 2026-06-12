---
title: "Cloud File Sharing Service"
date: 2011-07-17
forum: Server Platforms
---

### Post by alberion on 2011-07-17
Hi all, ive created a simple web server using this instructions:

[http://www.howtoforge.com/perfect-server-ubuntu-11.04-ispconfig-3](http://www.howtoforge.com/perfect-server-ubuntu-11.04-ispconfig-3)

Everything seems to be working very well for now, but i would like to add, if possible, another service, i want people to upload and download files/folders using drag and drop from the browser, like if they where doign it in their own computers, but all the files are in the server.

For example, they enter to [http://www.server.com/sharing](http://www.server.com/sharing)

you "login" and you can start downloading/uploading files/folder using drag and drop from your computer.

I know, you  may say make ppl use ftp, but i dont want to make ppl use a ftp program, im wondering if there is a web app to make that possible.

im new to all of this, hope you guys can help

tnxx

---

### Post by HermanAB on 2011-07-17
Howdy,

It could be as simple as VsFTPd, Woof or Mute, but there are various Web based programs for file sharing, for example AjaxPlorer, OpenDocman, KnowledgeTree and many others.  

Otherwise, you can go the DIY route and configure WebDAV on Apache:
[http://www.howtoforge.com/setting-up-webdav-with-apache2-on-debian-etch](http://www.howtoforge.com/setting-up-webdav-with-apache2-on-debian-etch)
[http://www.howtoforge.com/how-to-set-up-webdav-with-apache2-on-ubuntu-9.04](http://www.howtoforge.com/how-to-set-up-webdav-with-apache2-on-ubuntu-9.04)

---

### Post by alberion on 2011-07-17
hi, tnx for your answer, ive been checking out webdav, ill check the other ones you said, tnx a lot :)

---

### Post by alberion on 2011-07-19
hi again, ive read a lot about this, and the one that actually meets all the reqs is ajaxplorer, BUT the problem is, that the best thing about it, the drag and drop feature, DOESNT work with ie8 or earlier versions of it, and it sux :(

so i was wondering if you guys can help me with that, telling me more names of ajax/php scripts to put on my website to share info, specially if they have drag and drop feature

hope it works on ie8 lol

tnx again

cheers

---

