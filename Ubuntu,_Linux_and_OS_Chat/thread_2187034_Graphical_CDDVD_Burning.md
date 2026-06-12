---
title: "Graphical CD/DVD Burning"
date: 2013-11-10
forum: Ubuntu, Linux and OS Chat
---

### Post by dbass81 on 2013-11-10
I need something lightweight to burn ISO images.  I have tried Brasero and XFBurn in the past.  Brasero requires GNOME.  XFBurn require Xfce libs so I try to stay away from it.  I was looking for a lightweight CD/DVD burner for ISO files or mastering that only uses GTK or something similar.  Doesn't matter if it is a front-end.   Tried using synaptic to find something with no luck.  List what you got here.

---

### Post by philinux on 2013-11-10
Moved to general help. What version ubuntu are you running?

---

### Post by dbass81 on 2013-11-10
> **philinux said:**
> Moved to general help. What version ubuntu are you running?

I'm not using Ubuntu. I guess thats why I posted it under Linux/OS Chat.   I'm using Debian/Openbox.  I try to not use GNOME dependencies when possible.  I got an older laptop.

---

### Post by philinux on 2013-11-10
Would have helped if you included that info in the OP. Good luck

---

### Post by dbass81 on 2013-11-12
> **philinux said:**
> Would have helped if you included that info in the OP. Good luck

I ended up installing Brasero using --no-install-recommends.  Its actually doesn't use too many GNOME dependencies, and I like it better than XFBurn.

---

### Post by Ender Shadow on 2013-11-12
You could try K3b. It's arguably one of the best disc burning programs for Linux, plus, it doesn't require any GNOME dependencies.
It does need KDE dependencies, though.
Regardless of that fact, it is much better than Brasero and XFBurn, imo.

---

### Post by alphacrucis2 on 2013-11-12
I prefer k3b as well but if the op didn't like gnome dependencies, he probably wont like KDE dependencies either. k3b will also require qt. May be better off using command line tools like mkisofs.

---

### Post by craig10x on 2013-11-12
I use to use k3b myself because Brasero wasn't being properly maintained and it wasn't reliable....however, a new maintainer took it over and has turned it around....now it works really well...
very reliable and no more coasters like in the past (lol)...however, there is one little tip: go to the settings (plug in section) and uncheck the two CHECKSUM entries...they waste a lot of burning time...once you turn them off, i find that Brasero burns just as fast as k3b does....Brasero even will rip an encrypted dvd and make you an un encrypted copy (just as k3b will) if you have the libdvdcss2 codec installed in your system...

So, now i use Brasero again and don't need to download all the kde stuff just to have a good burner... ;)

---

### Post by help_me2 on 2013-11-12
Why not just install xfburn? Just because it downloads some extra libs, doesn't mean it's going to slow down your computer. Those are there for the app only. Either that, or just do it via command line.

---

### Post by dbass81 on 2013-11-13
> **craig10x said:**
> I use to use k3b myself because Brasero wasn't being properly maintained and it wasn't reliable....however, a new maintainer took it over and has turned it around....now it works really well...
very reliable and no more coasters like in the past (lol)...however, there is one little tip: go to the settings (plug in section) and uncheck the two CHECKSUM entries...they waste a lot of burning time...once you turn them off, i find that Brasero burns just as fast as k3b does....Brasero even will rip an encrypted dvd and make you an un encrypted copy (just as k3b will) if you have the libdvdcss2 codec installed in your system...

So, now i use Brasero again and don't need to download all the kde stuff just to have a good burner... ;)

I agree, Brasero is quite usable, and its interface is simplistic.  I didn't care for XFBurn's interface, and it kept popping up an error for me saying gstreamer not found.  The reason I don't use k3b is for that very reason, it uses qt and kde libs, and I try to keep my Openbox distro very lightweight for my older laptop.  It seems most apps use either GTK or GNOME so I'm trying to run everything using them.  I also installed Network Manager using --no-install-recommends and that keeps it to bare minimum.

---

