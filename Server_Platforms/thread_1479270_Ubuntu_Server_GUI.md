---
title: "Ubuntu Server GUI"
date: 2010-05-10
forum: Server Platforms
---

### Post by Loki57701 on 2010-05-10
I would like to have a GUI for my server, something light weight like XFCE. I've read a few guides online for this but it seems if I simply did:

```

sudo apt-get install xubuntu-desktop

```Than I would get all the extra stuff I don't want (evolution, open office, etc..). Also, from what I understand, this update would change my kernel to a desktop version instead of a server one.

So, is there a way to install the xubuntu GUI without all the extra crap and keep my kernel version the same?

Edit: Would: ```
sudo aptitude  install --no-install-recommends  xubuntu-desktop
``` work?

---

### Post by wojox on 2010-05-10
Why don't you try [Webmin]("http://en.wikipedia.org/wiki/Webmin")

---

### Post by Sub101 on 2010-05-10
> **wojox said:**
> Why don't you try [Webmin]("http://en.wikipedia.org/wiki/Webmin")

+1

One of the best ways of administering a server in my opinion

---

### Post by arrrghhh on 2010-05-10
I second (third?) Webmin.  Much better than installing a full-blown GUI.  Besides, this is a server!  You probably won't be using the GUI much except maybe to set it up.  Webmin is perfect for (most) configuration stuff you'll need.

---

### Post by tgm4883 on 2010-05-10
> **wojox said:**
> why don't you try [webmin]("http://en.wikipedia.org/wiki/webmin")

+1

---

### Post by Loki57701 on 2010-05-10
I actually have webmin installed already and it works great.

I'm not installing the GUI for myself; without going into detail.. someone else will be managing the server and I want to put a GUI on there for them.

---

### Post by tgalati4 on 2010-05-10
Might be quicker to install xubuntu or linux mint xfce and then install the server kernel over that.  Once your desktop works the way you want, you can start to remove open office and other apps that aren't needed.

---

### Post by lavinog on 2010-05-10
xubuntu-minimal
ubuntu-minimal

actually lubuntu might be lighter.

---

### Post by Iowan on 2010-05-10
[Here]("https://help.ubuntu.com/community/ServerGUI") is a help page with some options.

---

### Post by Loki57701 on 2010-05-11
Thanks for all the advice everyone, I appreciate it.

---

