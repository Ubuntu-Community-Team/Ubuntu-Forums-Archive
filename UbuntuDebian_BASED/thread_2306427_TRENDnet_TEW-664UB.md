---
title: "TRENDnet TEW-664UB"
date: 2015-12-15
forum: Ubuntu/Debian BASED
---

### Post by yagami2 on 2015-12-15
Chili555 you're a hero for being able to configure these adapters for Linux. I've followed your procedure, downloaded to Linux via my Virtual Machine. Unzipped and ran the code but I ran into this. It's the EXACT same Belkin adapter as this guy's that you redirected here [http://ubuntuforums.org/showthread.php?t=2157571&page=2](http://ubuntuforums.org/showthread.php?t=2157571&page=2) 

[http://prntscr.com/9ec492](http://prntscr.com/9ec492)

---

### Post by chili555 on 2015-12-15
> **yagami2 said:**
> Chili555 you're a hero for being able to configure these adapters for Linux. I've followed your procedure, downloaded to Linux via my Virtual Machine. Unzipped and ran the code but I ran into this. It's the EXACT same Belkin adapter as this guy's that you redirected here [http://ubuntuforums.org/showthread.php?t=2157571&page=2](http://ubuntuforums.org/showthread.php?t=2157571&page=2) 

[http://prntscr.com/9ec492](http://prntscr.com/9ec492)Your screenshot is barely readable. My most powerful magnifier tells me that you are running Kali, which we know nothing about, and that the kernel headers matching your running kernel version are not installed. If this were Ubuntu, I'd recommend:```
sudo apt-get install linux-headers-generic
```And then try again. I'm confident that isn't quite correct for Kali and so the exact process I leave to you.

I'd also point out that, when you encountered an error, to stop and fix it as all further steps will also error out, as you see.

Sorry I can offer no further assistance. Kali R *not* us.

---

### Post by howefield on 2015-12-15
Posts moved to own thread and to the "*Ubuntu/Debian BASED*" forum.

---

