---
title: "request:ePSXe"
date: 2005-04-15
forum: Ubuntu Backports
---

### Post by poofyhairguy on 2005-04-15
I want to try out a playstation emulator, but I'm scared of Sid packages. ePSXe is by far the best. The packages are found here:

[http://www.fbriere.net/debian/psx-emu/sid/](http://www.fbriere.net/debian/psx-emu/sid/)

The source packages are here:

[http://www.fbriere.net/debian/psx-emu/src/](http://www.fbriere.net/debian/psx-emu/src/)

Only things (I'm pretty sure) that ePSXe needs are the psemu video and sound pluggins.

Thanks either way...

---

### Post by JDay on 2005-04-15
ePSXe is closed-source and I don't see much point in packaging it since you can just grab the archive that you linked to and run the binary in there. PCSX, however is GPL and also quite good, although it doesn't seem to be developed anymore. Also, I believe that they both require a playstation bios, although PCSX has a native, legal bios you can use (no, it isn't very good).

---

### Post by kingrayray on 2005-10-16
I installed epsxe after haggling with deps it wanted.. (they were all available on the page posted) and it seems to be installed fine, but when i go to launch epsxe i get it whining about not having **lndir**.

I can't figure out what package provides it, i've searched and everything. This seems to be the only hangup associated with it, at least as far as i can see.

If anybody knows where to get lndir, let me know. I really want to play castlevania ;)

---

### Post by endy on 2005-10-18
Hmm, it's working fine for me but I can't remember what extra packages I may have installed. Do you have the exact error message?

---

### Post by kingrayray on 2005-10-18
[1d21h51m] kingrayray@euclid $epsxe
/usr/games/epsxe: line 25: lndir: command not found

simple as that. :confused:

google says it should be in xutils, but as far as i can see xutils just installed a copyright file and some other text file. nothing of any relevance. the file is nowhere to be found on my system.. i went as far as to **sudo updatedb && locate lndir** .. this is kind've a useful tool afaik, i don't know why i don't have it.

---

### Post by Heretic09 on 2005-10-18
Usually lndir is located in the xutils package:

[http://packages.ubuntu.com/hoary/x11/xutils](http://packages.ubuntu.com/hoary/x11/xutils)

Ubuntu should have it, it may have been trimmed it off like alsaconf.

---

### Post by kingrayray on 2005-10-19
I know. The hoary page shows it, but the breezy page just shows it as a transition package. 

[http://packages.ubuntu.com/breezy/x11/xutils](http://packages.ubuntu.com/breezy/x11/xutils)

So what I'm wondering is how I'd go about installing the hoary package? I think that's what I need to do. I don't know :P (that's why i'm posting on here :P)

---

### Post by chaumurky on 2005-10-24
Damn it! now I need it to install 'tablaunch'. Isn't this a rather common command???

---

### Post by xsence on 2005-10-26
Could someone make a howto for installing this psx emulator?

---

