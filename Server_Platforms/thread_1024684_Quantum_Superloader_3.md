---
title: "Quantum Superloader 3?"
date: 2008-12-29
forum: Server Platforms
---

### Post by shizakapayou on 2008-12-29
Looking to add a Superloader 3 to my Ubuntu Server 8.04.1 system.  Just wanted to make sure the hardware will work before pulling the trigger.  The Superloader is the SAS model - unless there are other suggestions, the HBA was going to be a Dell PERC5/E.

---

### Post by shizakapayou on 2009-01-21
Has anyone here used one of these?  I got it hooked up to my server without too much issue, but need some help getting going on using it.  I've installed mt-st and mtx, and found the device under /dev/st0.  However, I don't have much of a starting point in configuring /etc/stinit.def, or proceeding from there.

---

### Post by speedkreature on 2009-07-21
Any luck with this?  I've got a Superloader3 and I've commissioned an Ubuntu server to handle the backups.  Don't have a SCSI card yet (in route), and I was wondering if it will be worth my time.

I mean, if it takes me 3 days to get it working and I don't need to fuss with it after that, then that's great.

---

### Post by shizakapayou on 2009-07-22
Yes, it works great.  Mine's running connected to a Dell Poweredge 2950 III using an SAS5/e card.  I use Bacula 3 on Hardy to handle it all, highly recommended.

---

### Post by druhboruch on 2009-07-22
> **shizakapayou said:**
> I use Bacula 3 on Hardy to handle it all, highly recommended.

Did you compile bacula 3 or use binaries from Debian?

---

### Post by shizakapayou on 2009-07-23
I downloaded it from Bacula's site and compiled it.  The version available in the repositories is old and never worked correctly for me.  This was useful for me, as the Ubuntu setup guides made no mention of MySQL:

[http://wiki.bacula.org/doku.php?id=howto_compile_and_install_bacula_on_debian_4.0_etch](http://wiki.bacula.org/doku.php?id=howto_compile_and_install_bacula_on_debian_4.0_etch)

It still works well for version 3.01 of Bacula.  My make install kept bombing on me - if you check what it's telling you, there's an error with an extra dependency.  I don't remember what it was, but I think it had to do with SSL - find what it's after and it installs perfect.

---

### Post by speedkreature on 2009-07-28
Thanks, that's very useful.

I'm using Barracudaware Yosemite Backup 8.8 on HH (8.04.3 x86-64)  with an ATTO Celerity FC-42ES and a Promise VTrack E310f/s, and an Adaptec ASC-29320LPE (PCIe version of the 29320ALP) which is connected to the SuperLoader3 (LTO-3 HH).

Ubuntu automatically loaded the aic79xx module for the SCSI card but I cannot see the SuperLoader.  :-(  However, knowing that it should work gives me the hope to keep moving forward.  

This is my current employer's first production Linux...er, Non-Windows server so a lot is riding on this one.

Backups to disk are going great; I'm sustaining around 4GB/m.  Just need to get that autoloader working.
Any other modules that need to be loaded or should it "just work" if the SCSI card does?

---

### Post by speedkreature on 2009-07-29
Nevermind.  I got it to work by rebooting.  When the server came back up, it detected that I had connected the SuperLoader3 and it works flawlessly.  :D

---

