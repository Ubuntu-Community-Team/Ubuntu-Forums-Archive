---
title: "Problems installing FreeNX Server"
date: 2011-12-02
forum: Server Platforms
---

### Post by JamesGeddes on 2011-12-02
Hey everyone,

I'm trying to install FreeNX on my Ubuntu 11.10 server, but am having some difficulties.

Thus far, I have been following the guide on the ubuntu documentation site;

[https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX)

This is very clear, however when I get to step 3, which is to enter...

```
sudo sed -i 's/natty/lucid/g' /etc/apt/sources.list.d/freenx-team-ppa-natty.list
```

...the following error is returned

```
sed: can't read /etc/apt/sources.list.d/freenx-team-ppa-natty.list: No such file or directory

```

What am I doing wrong? Am I missing something?

Thanks!

James

---

### Post by JamesGeddes on 2011-12-03
**Update**

I think that I've managed to (sort of) install NXFree on my Ubuntu 11.10 server, but when I connect with the client, the following error messages are returned;

**First Message**
> Xsession: unable to launch "gnome-session" X session --- "gnome-session" not 
found; falling back to default session.


**Second Message**
> Xsession: unable to start X session --- no "/home/james/.xsession" file, no 
"/home/james/.Xsession" file, no session managers, no window managers, and no 
terminal emulators found; aborting.

What is going wrong there?

Thanks everyone!

James

---

