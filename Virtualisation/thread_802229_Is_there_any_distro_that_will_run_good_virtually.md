---
title: "Is there any distro that will run good virtually?"
date: 2008-05-21
forum: Virtualisation
---

### Post by Fzang on 2008-05-21
Lightweight distros would, of course, run well in a virtual PC as they aren't that demanding

But is there any distros specifically designed for running virtually?

Just curious...

---

### Post by fjgaude on 2008-05-21
If you find one let us all know... for, I haven't heard of one yet, though this company is getting close, very close:

[http://desktoplinux.com/news/NS3749512299.html](http://desktoplinux.com/news/NS3749512299.html)

And you might consider this, the DSL distro:

[http://damnsmalllinux.org/cgi-bin/forums/ikonboard.cgi?;act=ST;f=36;t=20117](http://damnsmalllinux.org/cgi-bin/forums/ikonboard.cgi?;act=ST;f=36;t=20117)

---

### Post by bradmkjr on 2008-05-21
Currently there is only 1 which I'm aware of.
 
Ubuntu JeOS.

[http://www.ubuntu.com/products/whatisubuntu/serveredition/jeos](http://www.ubuntu.com/products/whatisubuntu/serveredition/jeos)

Just enough OS for your virtual appliance

Ubuntu Server Edition JeOS (pronounced "Juice") is an efficient variant of our server operating system, configured specifically for virtual appliances. Currently available as a CD-Rom ISO for download, JeOS is a specialised installation of Ubuntu Server Edition with a tuned kernel that only contains the base elements needed to run within a virtualized environment.

2 Notes:

1. This is a server install, there is no gui, and adding in a gui sort of ruins the idea of a minimal operating system
2. This is designed to work best with VMware Server and ESX, it has been shown to work on other platforms, with mixed results.

Hope this helped,
Bradford Knowlton
[http://x86Virtualization.com](http://x86Virtualization.com)

---

### Post by Fzang on 2008-05-22
Thanks!

...Though I'm a windows noob, so the no GUI kind of kills me

---

### Post by dcstar on 2008-05-24
> **Fzang said:**
> Lightweight distros would, of course, run well in a virtual PC as they aren't that demanding

But is there any distros specifically designed for running virtually?

Just curious...

I can run Ubuntu (64 & 32bit), Kubuntu, Xubuntu, Mandriva, OpenSuse & XP in VMWare VMs, and they all work fine (though I do get some performance issues when I have **all** of them running simultaneously......)

All of these can be tuned to reduce their resource demands, but if your host has enough grunt thay may not be necessary.

No VM will run as efficiently as a native OS, but that is the price you pay for this sort of flexibility.

---

### Post by toobuntu on 2008-07-07
Check out SliTaz [http://www.slitaz.org/en/]("http://www.slitaz.org/en/").  It's similar in concept to Puppy Linux and DSL, uses Openbox as the window manager (in the "cooking" version), and provides a GUI without consuming too many system resources. 

From the website:

> SliTaz GNU/Linux is a free operating system working completely in memory from removeable media such as a cdrom or USB key. It is light, speedy and fully installable on a hard drive. SliTaz is distributed in the form of a LiveCD that you can easily burn to a cdrom and boot from.

Root filesystem taking about 80 MB and 
ISO image less than 30 MB.

---

