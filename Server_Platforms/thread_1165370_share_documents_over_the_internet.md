---
title: "share documents over the internet"
date: 2009-05-20
forum: Server Platforms
---

### Post by wenek18 on 2009-05-20
Hi 

I need to share document over the internet through my ubuntu so that my colleagues can work on these docs and save there work to be accessible for the others.

Similar to share point 

any ideas ?

Thanks
Justin

---

### Post by MikeEvans on 2009-05-20
If your looking for a commercial product check out

[http://www.alfresco.com/]("http://www.alfresco.com/")
[http://www.wrike.com/]("http://www.wrike.com/")

---

### Post by HermanAB on 2009-05-20
Opendocman works.  There are others.  They are all the same really.

---

### Post by sickdude on 2009-05-20
Well if you want your server to be in the middle, ftp is a great way to share stuff. Win XP can mount a ftp disk and acts like a normal disk. Well not really you have to login of course.

There is a better option, which i use because it supports sync'ing and it also supports Mac, Linux and Window$ 

[http://www.getdropbox.com](http://www.getdropbox.com)

It's awesome and free, check it out you will be surprised!

---

### Post by cariboo on 2009-05-20
I would stay away from ftp, use sftp/scp instead. For windows use winscp and nautilus for sftp.

---

### Post by Vegan on 2009-05-21
if you want to have a more sophisticated setup, samba can be configured to run over the internet.

there are lots of ways to set a shared resource.

I use samba on my LAN to let Linux be a file server that works with Windows clients.

If you secure it, it can be exposed to the internet.

---

### Post by wenek18 on 2009-05-31
Thanks guys for your help will check them out !!

---

### Post by HermanAB on 2009-05-31
Don't run Samba over the internet.  Although the server runs Linux and may be OK, the Windows clients are still running Windows...

---

### Post by grantemsley on 2009-06-01
On top of that, most ISPs block Samba through the internet.  Because 99% of the time, people don't really want it shared on the internet.

---

### Post by mister_p_1998 on 2009-06-01
Dropbox is quite nice, and you get 2gb free, over 2gb you gotta pay.
Steve

---

### Post by volkswagner on 2009-06-01
you may accomplish your goals with your own wiki.  You can set up foswiki and many others with Apache login.

---

