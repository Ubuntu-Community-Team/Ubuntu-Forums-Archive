---
title: "Remote Desktop"
date: 2007-04-09
forum: Server Platforms
---

### Post by pingman on 2007-04-09
Hi, looking for something similar to Remote Desktop in Windows environment, for remote management/control of my ubuntu server.

Thanks,
Atif

---

### Post by kooseefoo on 2007-04-10
Well, if you are running Ubuntu Server Edition, there is no GUI or desktop system by default.

However, for command-line functionality, you can use SSH. the OpenSSH server is really easy to set up. If you look on this forum, one of the stickys contains the Ubuntu Server howto.

Here's the OpenSSH bit of it:
[https://help.ubuntu.com/6.10/ubuntu/serverguide/C/openssh-server.html](https://help.ubuntu.com/6.10/ubuntu/serverguide/C/openssh-server.html)

---

### Post by jorgerosa on 2007-04-10
Can this help you? (see the links on it) [http://ubuntuforums.org/showthread.php?t=405574](http://ubuntuforums.org/showthread.php?t=405574)
Note: **Usermin** authors say: "(...) they would be able to perform if logged in via **SSH** (...)" - Seems to be a good thing, but im not skilled enought to comment this.
Discuss post: [http://ubuntuforums.org/showthread.php?t=401151&highlight=gui+for+server](http://ubuntuforums.org/showthread.php?t=401151&highlight=gui+for+server)

---

### Post by kooseefoo on 2007-04-10
Yes, jorgerosa is right that with some web-based GUIs and a proper apache setup, you could administrate it from any system on the internet :)

But, having your server configuration accessible over the internet like that has security implications. I'm not an expert, so I'm not going to try to give you a bunch of advice, but I would recommend using Apache with SSL (HTTPS) at the very least...

Yet again, I'm no security expert. I just go  by the rule of "The more you open up, the more possible security holes you have"

---

### Post by pingman on 2007-04-12
Thanks Guys..

---

