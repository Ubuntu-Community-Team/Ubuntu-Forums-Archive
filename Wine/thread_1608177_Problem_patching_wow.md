---
title: "Problem patching wow"
date: 2010-10-28
forum: Wine
---

### Post by TheStelz on 2010-10-28
Every time i run the launcher it opens the downloader, the first time it downloaded patch 3.3.x-4.0, then opened an error message saying "Failure to initialize. Check your internet connection. If the problem persiests contact blizzard" and i can never remember the last part. has anyone heard of this happening? Or know what to do?

---

### Post by TheStelz on 2010-10-31
anyone?

---

### Post by cwwilson721 on 2010-10-31
First, make sure the correct ports are open in your router and firewall (That's what the issue is about 99% of time).

From [http://us.blizzard.com/support/article.xml?locale=en_US&articleId=21015](http://us.blizzard.com/support/article.xml?locale=en_US&articleId=21015)> World of Warcraft & Burning Crusade use TCP port numbers 1119, 3724, 6112, 6113, 6114, and 4000 to play, and UDP port 3724 for in game Voice chat. The Blizzard Downloader, which downloads patches, also uses TCP ports 3724, 6112, 6113, 6114, 4000 and the range 6881-6999

---

### Post by TheStelz on 2010-10-31
the only firewall i'm using on my computer is firestarter, and even when i disable it i still have the problem. i'll try opening all of the ports though

---

### Post by cwwilson721 on 2010-10-31
A common misconception has to do with firewall differences between Linux and Windows.

In Windows, a firewall program actually opens/closes ports. So if you 'disable' or 'close' the firewall program, the ports are open to the network.

In Linux, in contrast, the 'firewall program' configures the kernel to open/close ports. So if you 'disable' or 'close' Firestarter, all you are doing is closing a configuration program. The ports are still opened or closed. You have to tell firestarter to open the ports, or they stay closed.

Hope this VERY simplistic explanation helps you out in the future.

---

### Post by TheStelz on 2010-10-31
yes that does help, very much appreciated. One more thing is that i am  on a college campus, and i've heard that they disable ports 6881-6999  because they are known torrent ports. Will opening them work?

---

### Post by MSPdwalt on 2010-10-31
Probably not, might want to go to a coffee shop or somewhere with a little less security and run your updates.

---

### Post by TheStelz on 2010-10-31
well i have a pc with windows 7 and i had no problems installing the updates on that computer. but i opened a bunch of the ports between 6881-6999, and all others, and still nothing

---

