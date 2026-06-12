---
title: "gksudo gedit and the extra tab"
date: 2012-08-13
forum: The Cafe
---

### Post by vasa1 on 2012-08-13
I came across [this]("http://forums.linuxmint.com/viewtopic.php?f=42&t=110021") to prevent gedit from opening an extra tab. It doesn't bother me much and I haven't tried it but what got me was this quote ([https://bugzilla.gnome.org/show_bug.cgi?id=658100):](https://bugzilla.gnome.org/show_bug.cgi?id=658100):)
> Christian Persch [developer] 2011-09-03 08:35:38 UTC
You shouldn't start GNOME programmes with elevated privileges, it's not
supported.

So it's not just Nautilus!

Paddy Landau had posted about it here: [http://ubuntuforums.org/showpost.php?p=12071894&postcount=81](http://ubuntuforums.org/showpost.php?p=12071894&postcount=81)

---

### Post by philinux on 2012-08-13
Use gksu-polkit.

It doesn't stop the blank extra doc but it's supposed to replace gksudo.

---

### Post by vasa1 on 2012-08-13
Reading a bit more, I get the impression the Gnome devs don't approve of *any* graphical program running with elevated privileges.

---

### Post by philinux on 2012-08-13
> **vasa1 said:**
> Reading a bit more, I get the impression the Gnome devs don't approve of *any* graphical program running with elevated privileges.

Yes and that's a shame because not everyone likes nano or other terminal based editors.

I'll carry on regardless. It's my machine and I'll break it if I want to. :P

---

### Post by forrestcupp on 2012-08-13
> **philinux said:**
> Yes and that's a shame because not everyone likes nano or other terminal based editors.

I'll carry on regardless. It's my machine and I'll break it if I want to. :P
Exactly. I'll do it whether they like it or not. This is the whole reason that gksudo was created. I doubt if they want us to start using sudo to open GUI apps.

---

