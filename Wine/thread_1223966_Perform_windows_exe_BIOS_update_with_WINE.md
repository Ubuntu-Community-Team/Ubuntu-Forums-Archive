---
title: "Perform windows exe BIOS update with WINE"
date: 2009-07-26
forum: Wine
---

### Post by artshark on 2009-07-26
Is this possible? I have a HP Mini 1000 Mi and theres a battery issue that the new firmware update fixes. Unfortunately, HP only issued this is a .exe, so it seems like wine is the only way to actually run it. would this work? Or would I need to fully simulate the windows environment?

---

### Post by OrbJinzo on 2009-07-26
I would not recommend this. you would prolly have to have a full windows enviorment i would assume there is some low level system calls that wine prolly cant handle.

---

### Post by RaviC on 2009-07-28
> **OrbJinzo said:**
> I would not recommend this. you would prolly have to have a full windows enviorment i would assume there is some low level system calls that wine prolly cant handle.
I had a battery issue with my Dell Laptop a while ago and they sent a BIOS flasher as well - but I had XP on a dual boot then.  You should be able to do it with a [BartPE live cd]("http://www.nu2.nu/pebuilder/") for Windows.  All you will need to make one is another PC with XP or higher.  That way you won't have to install XP on your computer.

---

### Post by Grenage on 2009-07-28
For the love of God, please don't do anything critical such as BIOS re-writes using WINE, or any Windows emulation.

---

### Post by 67GTA on 2009-07-28
+1 for BartPE. You can install BartPE in Wine, and create the BartPE CD from Ubuntu if you have a Windows install disc for BartPE to use. It basically makes and then boots in to a live Windows pre install CD. You can install the BIOS update from there. This is how I do all of my BIOS updates since HP only releases them in .exe format and there are no longer any Windows partitions on my two HP machines.

---

### Post by gsauthof on 2011-10-22
> **67GTA said:**
> You can install BartPE in Wine, and create the BartPE CD from Ubuntu if you have a Windows install disc for BartPE to use.

No, you can't install BartPE in Wine ( [http://bugs.winehq.org/show_bug.cgi?id=22124](http://bugs.winehq.org/show_bug.cgi?id=22124) ).

---

