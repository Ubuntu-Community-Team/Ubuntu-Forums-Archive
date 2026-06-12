---
title: "ubuntu server edition"
date: 2008-10-07
forum: Server Platforms
---

### Post by tatazhang on 2008-10-07
I'm a very new user, just installed a ubuntu desktop version in my laptop, very cool, then i try to install a server edition to instead office server which use windows server 2003 installed as a apache + php + mysql server.
but after installed, it's look no GUI platform, that's real hard for me, is that anyway make the apache + php +mysql server install on ubuntu desktop version or make the ubuntu server edition have GUI form like desktop version?
thanks
Jeff

---

### Post by lykwydchykyn on 2008-10-07
```

sudo aptitude install xorg gnome

```

Even with a GUI, though, most of your config may need to by via command line/config file editing.  You might want to look at webmin and ebox, and they both provide web-based GUI's for a lot of services.

---

### Post by Iowan on 2008-10-07
> **tatazhang said:**
>  make the apache + php +mysql server install on ubuntu desktop version [This ]("https://help.ubuntu.com/community/ApacheMySQLPHP") link may be helpful.

---

