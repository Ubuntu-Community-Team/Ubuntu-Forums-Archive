---
title: "hi i'm new please help"
date: 2005-04-19
forum: Repositories &amp; Backports
---

### Post by necorium on 2005-04-19
well i'm busy downloading ubuntu... should get it eventually. my question is how should i set it up on my system. i would like the choice of choosing either windows or ubuntu when i start up. i have partitioned my HD into 2 parts one 10gig part which hosts windows and program files and another 110gig part for everything else. should i install it on the 10gig with windows or what should i do. i'm so sick sick of formatting my pc i just wanna get this right first time. much thanks.. alex ;-)

---

### Post by az on 2005-04-19
[QUOTE=necorium]well i'm busy downloading ubuntu... should get it eventually. my question is how should i set it up on my system. i would like the choice of choosing either windows or ubuntu when i start up. i have partitioned my HD into 2 parts one 10gig part which hosts windows and program files and another 110gig part for everything else. should i install it on the 10gig with windows or what should i do. i'm so sick sick of formatting my pc i just wanna get this right first time. much thanks.. alex ;-)[/QUOTE]

That depends.  Do you wantto share the 10 gigs with windows?  Do you want both OSes to be able to access the storage space?

If that is the case, use the installer to shrink the 10 gig partition andinstall Ubuntu there.  That should be just enough space for both (but not a lot of room to install stuff for the long term...)  Also, use theinstaller to format the 110 partition into a vfat filesystem.  Make a mountpoint called storage or whatever you want to name it.  Being vfat, both windows and linux will be able to access it.

Otherwise, just make a 10 gig partition out of the free space and put Ubuntu there.  Use the 100 gigs as sotage as I just described.  Either way, the installer will allow you to dual boot...

---

### Post by necorium on 2005-04-19
[QUOTE=azz]That depends.  Do you wantto share the 10 gigs with windows?  Do you want both OSes to be able to access the storage space?

If that is the case, use the installer to shrink the 10 gig partition andinstall Ubuntu there.  That should be just enough space for both (but not a lot of room to install stuff for the long term...)  Also, use theinstaller to format the 110 partition into a vfat filesystem.  Make a mountpoint called storage or whatever you want to name it.  Being vfat, both windows and linux will be able to access it.

Otherwise, just make a 10 gig partition out of the free space and put Ubuntu there.  Use the 100 gigs as sotage as I just described.  Either way, the installer will allow you to dual boot...[/QUOTE]
 hmmm... don't understand all of that but i think i will make a seperate partition. thank you for helping

---

### Post by necorium on 2005-04-19
Hey if i install linux on my 10gig partition that has windows on it will that mess up windows or cause any problems?? What MUST I NOT do?? If anything..

---

