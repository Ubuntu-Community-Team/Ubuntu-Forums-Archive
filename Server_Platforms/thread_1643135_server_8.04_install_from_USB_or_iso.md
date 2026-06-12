---
title: "server 8.04 install from USB or iso?"
date: 2010-12-11
forum: Server Platforms
---

### Post by doglover56 on 2010-12-11
Hello. I am trying to install Ubuntu Server 8.04.x to my Poweredge 2450 from either an iso file or USB drive, though the machine is natively bootable from neither.  

1.  It is clear that installing from CD will not work on this machine.  The CD player seems to like some CDs (Ubuntu Server 10.10, Slackware) and not others (Ubuntu 8, any flavor), have tried multiple burns, and Server 8 is just not going to work.
2.  Tried mounting the Ubuntu 8.04 USB as a CD, which seems to work fine from the command line in terms of being able to browse the files on the mounted USB though the install program still won't accept it, still insists on a CD.  Not sure why since other distro USB installs on this machine do work using a PLOP boot floppy and the USB.
3.  Just don't know how to install from iso.  Need to research it.
Thanks for the help,
IMF

---

### Post by arrrghhh on 2010-12-11
Hrm... sounds like you're dealing with old hardware?

Have you tried PXE?  If it's really old, you'll need a floppy again to kick it off... Hopefully it's not that old ;)

---

