---
title: "XP in Vmware? On a mac g4"
date: 2008-06-01
forum: Virtualisation
---

### Post by ruialexbarbosa on 2008-06-01
Hi,

would windows work on VMWARE in a mac g4? I'm sorry if this is a dumb question...

---

### Post by fjgaude on 2008-06-01
Yes, it will, but you have to buy the virtualization program, Fusion, to do it.

---

### Post by bradmkjr on 2008-06-01
Sorry, NO!!!! These are the system requirements for VMware Fusion:

System requirements for VMware Fusion

    * An Intel-based Mac (64-bit guest operating systems require a EM64T-capable processor)
    * 512 MB of RAM (1 GB or more recommended)
    * 275 MB free disk space for VMware Fusion
    * 1 GB free disk space for each virtual machine (10 GB or more recommended)
    * Mac OS X version 10.4.9 or later


Most Virtualization products are based on virtualizing the Intel x86 Hardware. The only reason why new Apples can be virtualized is the move to the Intel CPU. the G4 or G5 is not likely to find virtualization software. There are linux distributions which will work on the g4/g5 cpu, as they are compiled to run on those hardware platforms. Just because it is Ubuntu doesn't mean it can run any application unless it is compiled for the correct hardware.

This post here, which I don't think is clear to the casual reader claims that Virtual PC will run on the G4. This is correct, but it isn't virtualization. It is emulating the Intel chipset on the Mac. That is an old version of Virtual PC, prior to Microsoft buying it. That was the Connectix's version of Virtual PC. 

[http://www.macworld.com/article/2810/2003/04/virtualpc6.html](http://www.macworld.com/article/2810/2003/04/virtualpc6.html)


Other related forum post:
[http://ubuntuforums.org/showthread.php?t=428726](http://ubuntuforums.org/showthread.php?t=428726)

Sorry about the bad news but Try virtual PC,
Bradford Knowlton
[http://x86Virtualization.com/](http://x86Virtualization.com/)

---

### Post by fjgaude on 2008-06-02
If the G4 uses PPC CPU then what I said about Fusion is not right. Sorry, but Intel CPUs seem to be the main way to go these days.

---

