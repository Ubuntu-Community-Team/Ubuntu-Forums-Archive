---
title: "other distros with multi monitor support?"
date: 2010-08-29
forum: The Cafe
---

### Post by Manolicious on 2010-08-29
I can't seem to find a single one.  It seems the first implementation was  xrandr, but I gave this a go with one distro and it crashed.  I just tried Chakra and while it seems to have its own display manager, I can hardly rotate screens relative to each other w/out crashing.

I remember back in ubuntu 8.04 seeing thread after thread about messing with the xorg.config files to enable dual monitor support, and it was only till someone insisted I just upgrade to 9.04 that I was introduced to the wonderful world of multi monitor setups.  Even kubuntu didn't seem to have a multi monitor manager, though I lucked out for that system after I used the proprietary graphics driver which lucky came with dual monitor support.

---

### Post by Dayofswords on 2010-08-29
i bet [Fedora]("http://fedoraproject.org/") does

---

### Post by Windows Nerd on 2010-08-29
Arch Linux does. I bet Debian does too.

If you are willing to poke around your Xorg config adding another monitor is moderately simple.

---

### Post by Manolicious on 2010-09-01
> **Windows Nerd said:**
> Arch Linux does. I bet Debian does too.

If you are willing to poke around your Xorg config adding another monitor is **moderately simple**.

I have broken an OS's display configuration once before by tooling around with its Xorg config file, and the fact that you could very well break your graphics card by not setting the virtual size correctly to your monitors' standard doesn't encourage me much to play with it.  Even xrandr had problems setting virtual display sizes, which I couldn't pin down as being a limitation of my graphics card or of the software.  This is why I gave up on Slackware.  Ubuntu's gui however seems very cabable of knowing the limitations of my graphics card and keeping me within those limitations.

I hoped I would have better luck with Chakra which is based on Arch, but while its display configuration gui can "sort of" rotate screens relative to each other, it can only clone displays.  As of yet I haven't tried Fedora, and I'd figure Debian would support something like Ubuntu has since Ubuntu is based on it.  It's just unfortunate that the vast repositories of the Debian distribution airn't easily exportable to other distros, or at least the ones I like.

I should have been more explicit in my question that I am looking for distros with gui that can enable multi monitor support, and bonus if they can do so across different graphics cards rather than just multi head cards.

---

### Post by MaxIBoy on 2010-09-01
*Any* recent distro should be able to do this. Have you tried system->preferences->display?

---

### Post by wojox on 2010-09-01
I purchased a NVidia dual-monitor card years ago for Windows and I've been able to use multi monitor's for Arch, Debian, Fedora Opensuse, Ubuntu...

---

### Post by WalmartSniperLX on 2010-09-01
I know for a fact Fedora does, and so should all of the other popular desktop distributions (Gentoo, Debian, Arch, Slackware, openSuse, etc). Actually, out of the many, many distros that I have used, both small and big, it will work. If they don't have a GUI tool for doing it, then you need to edit xorg.conf. Read the man pages for xorg.conf and your current driver to find the correct lines to add when editing the file. Always remember to make backups so if your last settings break the system, you can recall your last working xorg.conf and re-save it to /etc/X111/xorg.conf.

Edit: Editing xorg.conf correctly should enable multiple display devices and loaded drivers so that you can extend beyond your dual-head card if you have another device.

---

### Post by johnboy1313 on 2010-09-01
> **Dayofswords said:**
> i bet [Fedora]("http://fedoraproject.org/") does

I did it with Fedora 10, cant imagine why it would go away

---

