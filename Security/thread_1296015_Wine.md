---
title: "Wine"
date: 2009-10-20
forum: Security
---

### Post by haz13 on 2009-10-20
If i download and install wine so i can run itunes does this mean i will be open to all of the windows viruses and problems?

---

### Post by aim on 2009-10-20
> **haz13 said:**
> If i download and install wine so i can run itunes does this mean i will be open to all of the windows viruses and problems?

the short unswer is no. until you run one.

---

### Post by haz13 on 2009-10-20
All i want to run is itunes...so that means i will be safe?

---

### Post by aim on 2009-10-20
> **haz13 said:**
> All i want to run is itunes...so that means i will be safe?

yes. until you run a  virus yourself you're safe. 

if you run some selected apps taken from trusted safe source - you're safe.

---

### Post by __p1n__ on 2009-10-20
Wine provides some light-weight paravirtualization functionality by supplying Win32 and DX implementations as well as directory/drive remapping.  This set of system call intercepts does not create a full PVM let alone an HVM environment; it's only really a ring 3 (userland) rootkit for windows applications.

Windows malware running in wine can:

1. Corrupt the wine installation
2. Depending upon symlinks and hard links, affect the linux filesystem that it's installed upon
3. Corrupt SMM (regardless of o/s)

so yes, there's some risk.

Imho a better choice than wine would be to run itunes in some form of true virtual machine with windows installed within it (if your windows license permits this.)  My personal preference atm is xen however that is extremely complex to set up.  An easier choice would be kvm or virtualbox.

Good luck.

---

### Post by howefield on 2009-10-20
> **haz13 said:**
> If i download and install wine so i can run itunes does this mean i will be open to all of the windows viruses and problems?

You may find it a moot point as itunes appears to run poorly in wine.

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=1347](http://appdb.winehq.org/objectManager.php?sClass=application&iId=1347)

A better bet might be virtualising windows with something like Virtualbox. In which case, you would treat it as a normal windows install, and protect it in the same way.

---

### Post by Lars Noodén on 2009-10-20
> **__p1n__ said:**
> Wine provides some [s]light-weight paravirtualization[/s] ...

WINE actually provides the APIs not virtualizaton.  Hence the name Wine Is Not an Emulator...  If the Windows malware obeys the APIs then they should run well.  ClamAV is available.  

@*haz13  : which applications are you running under WINE?  There might be tips on securing them or even more advanced alternatives.

---

