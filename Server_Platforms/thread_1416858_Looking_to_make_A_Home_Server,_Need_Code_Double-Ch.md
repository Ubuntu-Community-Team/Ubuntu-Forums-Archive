---
title: "Looking to make A Home Server, Need Code Double-Checked"
date: 2010-02-26
forum: Server Platforms
---

### Post by agonoruci on 2010-02-26
I found this page online. And I thought it was really nice, and I really like the way torrentflux was added, thats a must for me. I am wondering if there is a better approach now, or if this approach is still good, and I was just wondering if someone could double-check the code, see if its good. I have an old dell laying around, and I thought it was finally time to put it to good use. So here it is.

[http://jonpeck.blogspot.com/2006/11/how-to-configure-80-fileserver-in-45.html](http://jonpeck.blogspot.com/2006/11/how-to-configure-80-fileserver-in-45.html)

---

### Post by FuturePilot on 2010-02-26
I don't understand why they enabled the root account yet continued to use sudo for everything. I would recommend **not** enabling the root account and use sudo instead. Also, that was written for Ubuntu 6.10 which is really old (and not even supported anymore) so some things may have changed since then and need to be configured differently.

---

### Post by Jive Turkey on 2010-02-26
There are a lot more current guides than that, in addition to what agonoruci said about not enabling the root account, i would avoid installing SWAT too.  It has been abandoned by its developers and likely has security holes that will never be fixed.  Samba is easy enough to configure without it.

---

### Post by tekkidd on 2010-02-26
looks just about right but i would obviously use a more updated version of ubuntu

---

### Post by Iowan on 2010-02-27
[howtoforge]("http://www.howtoforge.com/howtos/linux/ubuntu") has several "perfect server" articles you might consider...

---

