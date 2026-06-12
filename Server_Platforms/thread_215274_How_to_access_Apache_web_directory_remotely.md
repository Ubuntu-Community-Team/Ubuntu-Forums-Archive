---
title: "How to access Apache web directory remotely"
date: 2006-07-13
forum: Server Platforms
---

### Post by Sajji on 2006-07-13
Newby question:

Just installed LAMP version.  I have a number of questions:

1.  Where is the default Apache web directory?
2.  How do I access this directory remotely?  For example, how do I put files into it using a tool like Dreamweaver?

Thanks,

Sajji

---

### Post by FredSambo on 2006-07-13
your default web directory in apache is /var/www/

you can just drop your index.htm file in there if you want and immediately view it via [http://localhost/](http://localhost/)

there should be a default HTML page already in there that you can see via [http://localhost/](http://localhost/) at the moment.

---

### Post by FredSambo on 2006-07-13
ok, i happen to be on my windows computer at the moment, so the address isn't [http://localhost/](http://localhost/), but the actual name of my server [http://server/](http://server/).  but you get the point:

this is what you should see by default.  (you are lucky that i just installed apache on this machine today!)

[img]http://www.skeletonmedia.com/fred/apache_default_desktop01.png[/img]

and if you click on that link you'll see:

[img]http://www.skeletonmedia.com/fred/apache_default_desktop02.png[/img]

---

### Post by FredSambo on 2006-07-13
if you are going to set up dreamweaver, you can either share the /var/www/ directory over your network and save directly to it, or you can set up an ftp server.

i'm sure a pro will jump in here and clarify things.  :p

---

### Post by LordHunter317 on 2006-07-13
If you install the SSH server, you can use SFTP to transfer files, which is what I recommend.

You'll need to change ownership on the /var/www directory to be owned by your user and group in order to write files there.  This is perfectly fine.  All files and directories will need read access to the world for Apache to serve them.  This ought to happen by default.

---

### Post by FredSambo on 2006-07-13
good advice, thanks!

---

### Post by Sajji on 2006-07-13
Thanks guys - you've earned plenty of good-Karma points!

:KS

---

