---
title: "[SOLVED] Remastersys and Vivid Vervet - Xubuntu/Ubuntu 15.04"
date: 2015-07-02
forum: Ubuntu, Linux and OS Chat
---

### Post by halfnote52 on 2015-07-02
Okay, so I've been MEANING to check out systemback, which is theoretically the perfect alternative to those of us who WANT all our files and settings in a live disk, but I've been too lazy, and I've been meaning to check out BLIC, but I'm WAY too cheap.

That out of the way,  Remastersys3.0.4-2 DOES work on Xubuntu/Ubuntu 15.04 - HOWEVER! - you have to manually install syslinux-utils and isolinux packages. The DEB pkg does not force them to install.  Otherwise it give you an empty 36K iso file.

Cheers!

---

### Post by halfnote52 on 2015-07-02
Okay, followup - resulting remastersys iso has a few quirks, but systemback, as it turns out, is AMAZING, so... there you go.

---

### Post by joseluismurillogarcia on 2015-07-31
Hello, halfnote52, how have done you?

---

### Post by halfnote52 on 2015-07-31
I ended up installing systemback and using the "Live Disc" creation option. Then I used the "Create iso" option, and it was all good. = )

One caveat though:  If a folder is in the ROOT directory [/ ] and it is NOT one of the standard ones the OS put there, then systemback will NOT back it up.  If you have, say, a custom /scripts folder on the root directory mapped to keyboard shortcuts or ACPI events, it needs to be moved INSIDE one of the regular folders (and remapped accordingly to the shortcuts) before running systemback or it won't be there when you load the live boot.  (I found this out the hard way.)

---

### Post by joseluismurillogarcia on 2015-08-01
Thanks. It is that I like more remastersys iso is then installed. I've also  tried try [Respin]("http://www.linuxrespin.org"), but I have not managed  to work.

---

### Post by joseluismurillogarcia on 2015-08-01
The repo of respin: [https://launchpad.net/~sergiomejia666/+archive/ubuntu/respin](https://launchpad.net/~sergiomejia666/+archive/ubuntu/respin)

---

