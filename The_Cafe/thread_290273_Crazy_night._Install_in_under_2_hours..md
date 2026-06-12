---
title: "Crazy night. Install in under 2 hours."
date: 2006-11-01
forum: The Cafe
---

### Post by jalm111 on 2006-11-01
So here's what happened tonight, thought some people would find it funny.

Finally (after about 4 years) decided to boot into my Windows OS and clear out any remaining junk and free up the 150 Gig data NTFS partition. Here's how my PC was configured:

0,0: 80gigs 
1,0: 150 gigs NTFS
1,1: /boot
1,2: /swap
1,3: 40 gigs /root

Anyways, so I clear out the 1,0 partition and delete it in windows (DOH DOH DOH!!!!!). Boot into ubuntu.... initab gone...crap.... Live CD  mount /old root  cd etc   ls  --nothing--  ](*,) 

Well so somehow deleting that NTFS partition through Windows destroyed my etc?? Can't really think of anything else but this has got to be the weirdest thing I've ever seen happen, especially because everything else (/home /var etc.) is still there. Tried fsck and etc... no good. 

So the past 2 hours I spent installing Edgy (had dapper before) and returning things back to normal. I am almost at full speed after playing with beryl I just decided to use compiz because it is much more stable. Had to reinstall JDK 5.0 and etc but overall I really like Edgy. After tweaking my xorg and a bunch of other settings it seems to be running very smooth even with compiz (using nvidia beta not xgl).

So as a warning to others, do not do any partitioning and etc through windows. I'm beat so goodnight.  :)

---

### Post by viper on 2006-11-01
Sleep tight!!! sounds like you need it.:)

---

