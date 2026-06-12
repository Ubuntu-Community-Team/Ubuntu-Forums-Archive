---
title: "LAMP Server and other uses"
date: 2011-04-27
forum: Server Platforms
---

### Post by xkaijinx on 2011-04-27
Hello, 

I am planning on using Ubuntu 32bit Desktop as a server.  I already installed the necessary LAMP server components via a tutorial.  I am now trying to see how I can put media and/or pics on this and then access it on my main Windows machine. 

Anyone have any ideas?  Totally drawing a blank on this

---

### Post by volkswagner on 2011-04-27
On your server install and configure [SAMBA]("https://help.ubuntu.com/10.04/serverguide/C/samba-fileserver.html").

Once configured and Windows machines connect, you can map the share as a network drive in Windows for automatic connection on boot.

---

### Post by falko on 2011-04-28
You could also set up WebDAV: [http://www.howtoforge.com/how-to-set-up-webdav-with-apache2-on-ubuntu-10.04](http://www.howtoforge.com/how-to-set-up-webdav-with-apache2-on-ubuntu-10.04)

---

