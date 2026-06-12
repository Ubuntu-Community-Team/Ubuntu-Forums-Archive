---
title: "Missing RAM"
date: 2007-05-15
forum: Server Platforms
---

### Post by nodej on 2007-05-15
Hi all,

I recently did a fresh install of feisty server edition x64 on a HP DL585 with 32 GB of RAM but when I do a lshw, only 10 GB is detected.  Where did the other 22 GB went?  :( 

Thanks in advance,

Jon

---

### Post by godd4242 on 2007-05-15
That's a beastly system you've got going on for starters.

Second off, is this the first time you've installed Feisty on it, or has it worked before?
I get the impression that it has worked before but I'm just wondering.

---

### Post by Death_Sargent on 2007-05-15
first of all 10 gigs of ram is extravigant and 32 is rediculous. what is on that server? every freaking world in WOW?

that aside I am willing to bet that its hardware related and as stupid as it sounds i recomend opening it up. talking qtip and alcohol (CLEAN THE PINS) to each ram card and firmly pugging them back in.

i had this problem on my laptop before. 

and if nothing else having to preform this tedium should humble those of us who really have way to much ram.

---

### Post by nodej on 2007-05-15
This is the first time I installed Feisty on it.  Upon boot up the BIOS detects all 32 GB, but once the OS boots up the other 22 GB is gone.

Hehe, it needs 32 GB because it'll be processing a lot of data. :) 

I'll have to go on site to do some hardware troubleshooting, but I'm hoping it's a OS config issue.  I'll keep you guys posted after I mess around with it.

Thanks!

---

### Post by rickyjones on 2007-05-15
> **Death_Sargent said:**
> first of all 10 gigs of ram is extravigant and 32 is rediculous. what is on that server? every freaking world in WOW?

that aside I am willing to bet that its hardware related and as stupid as it sounds i recomend opening it up. talking qtip and alcohol (CLEAN THE PINS) to each ram card and firmly pugging them back in.

i had this problem on my laptop before. 

and if nothing else having to preform this tedium should humble those of us who really have way to much ram.

Nah, 32 is definitely not extravagant. I intern at a company where we run a production VMWare ESX environment of 3 HP DL580s. Each of those boxes has at least 16GB of RAM, one should be running 32GB I do believe. This allows several hundred vmsessions to run without issue.

-Richard

---

### Post by nodej on 2007-05-16
Thanks for all the replies, I resolved the issue by replacing the processor boards.  Now I have all 32 GB at my disposal.

---

### Post by Death_Sargent on 2007-05-16
HAH told you it was hardware,  anyway good for you to finding the problem oh and since you have all 32 gigs what the hell are you going to do with it?

---

