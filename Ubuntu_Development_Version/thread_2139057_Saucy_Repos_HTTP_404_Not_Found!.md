---
title: "Saucy Repos HTTP 404 Not Found!"
date: 2013-04-25
forum: Ubuntu Development Version
---

### Post by kevpan815 on 2013-04-25
Could someone please tell me what I am doing wrong? 404 Not Found on UEFI!

---

### Post by cariboo on 2013-04-25
Check here:

[http://archive.ubuntu.com/ubuntu/dists/](http://archive.ubuntu.com/ubuntu/dists/)

To see if the mirror you are using has saucy repos yet.

BTW whether you are using UEFI has nothing to do with the repos, only the kernel.

---

### Post by kevpan815 on 2013-04-25
Nevermind, I figured the problem was most likely the UEFI, so I changed it to Legacy BIOS, and then Reinstalled 13.04, I'm in now as well! Just FYI.

---

### Post by kevpan815 on 2013-04-26
Actually, some of the 13.10 Archives AMD64 13.04 is trying to download ATM are I386 Archives so UEFI may very well be the issue even if you say it's NOT!

---

### Post by kevpan815 on 2013-04-26
Please let me know if you would like me to File a Bug Report on this issue and if yes then tell me how I can file it as I am NOT getting an Apport Window when these Errors Occur. Just FYI.

---

### Post by kevpan815 on 2013-04-26
Also what I can tell you is only 4 Archives are NOT working with Legacy BIOS where as OVER 10+ Archives are NOT working with UEFI Firmware. I am in the Chicago Area so I would assume that the Closest Mirror to me would be ANL.GOV.

---

### Post by dino99 on 2013-04-26
Maybe you are too tired, but read again what post #2 above said; and most important try to understand it. Here you are only sharing your ignorance.
Look at your sources.list, and clean it.

---

### Post by kevpan815 on 2013-04-26
Sir, what I can tell you is that I followed Ventrecal's Instructions to the Letter, this is a Fresh (A.K.A. Clean Install) of AMD 64 Unity Desktop Ubuntu, NOT an UPGRADE from 12.04.2 or 12.10! 13.04 is indeed offering me I386 Archives of 13.10 which you should know that I386 is NOT Compatible with UEFI Firmware!

---

### Post by dino99 on 2013-04-26
As "ubuntu" says: you are supposed to understand what you are doing, and not only following a fake "good howto".
[http://ubuntuforums.org/showthread.php?t=2138987&page=2&p=12619419#post12619419](http://ubuntuforums.org/showthread.php?t=2138987&page=2&p=12619419#post12619419)

---

### Post by kevpan815 on 2013-04-26
ANL.GOV otherwise known as Argonne National Labratory is currently at "Up to Date Status," And it usually has the Alpha's/Beta's on it too! Just FYI.

---

### Post by kevpan815 on 2013-04-26
Just took a good look @ my Sources List and Found Entries that were still Referring to Raring! I changed them to Saucy and they are all working now. Plus there are actually Saucy Upgrades!

---

### Post by JMB74 on 2013-04-26
There are upgrades if you enable the "proposed" repo. Not usually advised to do that as it can cause problems with package version mismatches, build faiures/delays on some architectures so messing up multiarch support and dependencies etc.

[http://ubuntuforums.org/showthread.php?t=2076448&p=12319215#post12319215](http://ubuntuforums.org/showthread.php?t=2076448&p=12319215#post12319215)

---

### Post by kevpan815 on 2013-04-26
That's why I am keeping a Backup Copy of 13.04 with no Updates Included on an 8 GB USB Flash Drive. Just FYI. BTW, I am a Very Experienced MSFT/Apple Beta Tester who has previously tested Both Windows AND Mac Beta's, Just FYI!

---

### Post by JMB74 on 2013-04-26
> **kevpan815 said:**
> That's why I am keeping a Backup Copy of 13.04 with no Updates Included on an 8 GB USB Flash Drive. Just FYI. BTW, I am a Very Experienced MSFT/Apple Beta Tester who has previously tested Both Windows AND Mac Beta's, Just FYI!

Don't doubt it. Not necessarily pointing that out for your benefit, but other people reading might think "great, saucy updates if I have the proposed repo enabled". Then run into packager mismatch hell sometime down the line. Happened with raring at the beginning.

---

### Post by kevpan815 on 2013-04-26
> **JMB74 said:**
> Don't doubt it. Not necessarily pointing that out for your benefit, but other people reading might think "great, saucy updates if I have the proposed repo enabled". Then run into packager mismatch hell sometime down the line. Happened with raring at the beginning.

Thanks for letting me know about that. This is actually the first time I Edited my Sources.List and began testing the Next Release before Alpha 1 was Released.

---

