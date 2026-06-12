---
title: "[kubuntu] Win7 Virtualbox refuses to boot after updating to trusty"
date: 2014-08-20
forum: Virtualisation
---

### Post by martin_2 on 2014-08-20
Hi,

I recently upgraded from kubuntu 12.04 to 14.04 (64Bit). 
Since then my Windows7 prof 32bit virtualbox (4.3.10) inside kubuntu is not working anymore giving 

```

**"BOOTMGR is missing"**

```

 error. After a few hours of searching the web I ended up here. 

What I tried so far: 

1) Reinstall virtualbox including all packages

2) Reboot Win7 from disk and try to recover the bootmgr by: 

```

**bootrec /FixMbr**
**bootrec /FixBoot**
**bootrec /RebuildBcd**

```

without any success. Does anyone have a hint how to repair the Virtualbox?

Thanks for your help,

Martin

---

### Post by T.J. on 2014-08-21
I apologise if this sounds bad, but I have to ask in case we need to restore a damaged/missing file.  Before your upgrade, did you backup your data? I can't emphasize that enough when upgrading any OS, regardless of who makes it.  

Did you uninstall the "guest additions" from your VM before the upgrade?

To help you in fixing your problem, my first suggestion is to verify that your settings have not changed between versions of the VirtualBox and that all disc files are in their proper places on the virtual controllers.  This is easily done, just look in settings to see if everything looks as it should.  The next thing that I would do is remove the Ubuntu version of the package if you are using it, and try the official Oracle one at virtualbox.org instead to see if that will be the easy fix.  

If that doesn't work, please let me know and we will try something else.

---

