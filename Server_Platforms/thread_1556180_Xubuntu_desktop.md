---
title: "Xubuntu desktop"
date: 2010-08-19
forum: Server Platforms
---

### Post by xendistar on 2010-08-19
I know I can have the gnome desktop on my server by typing

sudo apt-get install ubuntu-desktop

But can I install the xubuntu (XFCE) desktop instead?

---

### Post by snowpine on 2010-08-19
Of course!

sudo apt-get install xubuntu-desktop

---

### Post by cascade9 on 2010-08-19
If you already have ubuntu-desktop installed, I'd just install Xfce, not xubuntu-dekstop. Since you already would have gdm, etc, all you should need is Xfce, then to log into xfce from the gdm screen.  

apt-get install xfce4

---

### Post by xendistar on 2010-08-19
When I try

sudo apt-get install xubuntu-desktop

I get

E: Couldn't find package xunbuntu-desktop

This is a brand new install of 10.04 server

Tim

---

### Post by xendistar on 2010-08-19
Seem like it I have sorted it, the sources.list was empty!! Not sure why but it is now sorted and currently downloading the xubuntu desktop as we speak.

Thanks for the earlier information

Tim

---

### Post by snowpine on 2010-08-19
Preface it with "sudo apt-get update" and make sure to spell Xubuntu correctly:

```
sudo apt-get update
sudo apt-get install xubuntu-desktop
```

(edit) Looks like you got it fixed! Glad to hear it. :)

---

