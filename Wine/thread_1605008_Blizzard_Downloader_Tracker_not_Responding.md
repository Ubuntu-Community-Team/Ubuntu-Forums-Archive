---
title: "Blizzard Downloader Tracker not Responding"
date: 2010-10-24
forum: Wine
---

### Post by TheStelz on 2010-10-24
Hello
 First off I'm very new to linux. But I installed it on my older laptop and am trying to install WoW. I got the first part installed, but when i open the launcher it says a new launcher is out, opens blizzard downloader and never downloads. The green circle turns yellow and says that the tracker is not responding. I tried downgrading to an older version of wine, because previously i could not click agree on the terms of service agreement, and neither of the versions i tried have worked. What should i do?

---

### Post by cwwilson721 on 2010-10-24
First, make sure the correct ports are open in your router and firewall (That's what the issue is about 99% of time).

From [http://us.blizzard.com/support/article.xml?locale=en_US&articleId=21015](http://us.blizzard.com/support/article.xml?locale=en_US&articleId=21015)> World of Warcraft & Burning Crusade use TCP port numbers 1119, 3724, 6112, 6113, 6114, and 4000 to play, and UDP port 3724 for in game Voice chat. The Blizzard Downloader, which downloads patches, also uses TCP ports 3724, 6112, 6113, 6114, 4000 and the range 6881-6999

---

### Post by _outlawed_ on 2010-10-24
You can switch options to download patches directly via HTTP from Blizzard servers if the P2P doesn't work all that great.

---

### Post by TheStelz on 2010-10-25
Thanks for the help, just de-activated firestarter and it seemed to work fine

---

### Post by TheStelz on 2010-10-25
ok so i got wow installed, and now when i try and sign in it never gets past connected....
any advice?
Edit: i ran the updater and it finished downloading the patch, but then an error window came up that said unable to initialize streaming. Blizzard Updater was unable to start up. and every time i run the launcher it repeats the process of checking the 3.3.x-4.0.0 patch, then opening the same error message.  Please Help =P

---

