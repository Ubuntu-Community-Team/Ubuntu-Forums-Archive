---
title: "[SOLVED] uninstall evolution"
date: 2008-03-23
forum: The Cafe
---

### Post by stainless_steel on 2008-03-23
so i have no use for evolution and it kept wanting updates, but it turns out that is part of ubuntu's meta-package and cant really be uninstalled.
this kinda reminds me of some crap windows does called Internet Explorer.
its sad to see this in a linux distro. i thought i left all that behind me.
comments? perhaps i dont know what im talking about?

---

### Post by %hMa@?b&lt;C on 2008-03-23
well, ubuntu-desktop is just a meta package, so you can uninstall evolution.  It is just part of the gnome desktop, along with software such as nautilus and the others.

---

### Post by DoktorSeven on 2008-03-23
Well, it can be uninstalled but it might cause issues if you do a major system update (to the next version of Ubuntu or something).  Otherwise, though, there's no harm at all from removing the metapackage, and even if you want to update you can always reinstall it beforehand (therefore getting Evo back), update, then remove Evo again...

So no, it's not as bad as IE :)

---

### Post by mthei on 2008-03-23
It can be removed without any issue. I'm sure I've removed Evolution in favout of IceDove before upgrading from Feisty to Gutsy. It doesn't even remove the "ubuntu-desktop" metapackage when you remove Evolution (unlike removing GnomeBitTorrent, for example). Removing Evolution should not damage any future dist-upgrades.

---

### Post by stainless_steel on 2008-03-23
ok, i guess i dont know what im talking about.

---

### Post by p_quarles on 2008-03-23
Well, I believe that the Gnome-Panel calender uses Evolution's built-in calendar application. This is the main problem that would be caused by removing that package. 

Generally speaking, the ubuntu-desktop metapackage (the one that contains Evolution) is designed to be a nicely integrated, fully featured and user-friendly environment. For those wanting a more modular graphical environment, there are dozens of other options, including a minimal Gnome setup or an alternate window manager. So, yes, comparing this to the integration of Explorer into the base of Windows functionality is incorrect.

---

### Post by 23meg on 2008-03-23
[QUOTE=stainless_steel]so i have no use for evolution and it kept wanting updates, but it turns out that is part of ubuntu's meta-package and cant really be uninstalled.[/QUOTE]

That's not been the case since Fesity. You can uninstall it without removing ubuntu-desktop.

```
$ sudo apt-get remove evolution
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  evolution evolution-exchange evolution-plugins
0 upgraded, 0 newly installed, 3 to remove and 2 not upgraded.
Need to get 0B of archives.
After unpacking 11.8MB disk space will be freed.
Do you want to continue [Y/n]? 

```

---

### Post by stainless_steel on 2008-03-23
oh ok, awesome, i guess i was just reading old forum posts

---

