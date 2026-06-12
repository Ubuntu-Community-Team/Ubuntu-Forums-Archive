---
title: "ubi-language failed with exit code 141"
date: 2016-04-10
forum: Ubuntu Development Version
---

### Post by Bucky Ball on 2016-04-10
Hi all,
 
Attempting to install Xubuntu-core 16.04 LTS on my HP Stream 11, 32Gb eMMC card, 2Gb RAM, Intel Celeron CPU  N2840 @ 2.16GHz processor. I have Xubuntu 14.04 LTS on there currently and works beautifully so hardware's good to go. 

My issue: 16.04 works great in a Live session, I double click the install icon and all goes well until I get to the timezone section. Once I hit 'continue' there the machine crashes with 'ubi-language failed with exit code 141'. It also says to check syslog. [Find it here]("http://paste.ubuntu.com/15730200/") (my attempts in the last 45 minutes).

Oddly, the live session doesn't crash (typing from it now after two failed install attempts), and I can get back to the desktop and all good. So I try again and this time slightly different. It tells me immediately there is a problem and I should try the part of the install again that crashed (I'm figuring) or the install may be broken. (Sorry, didn't take a screenie of that bit.)

At the timezone 'continue', I now get the attached message instead of the previous one. Close all that and back to desktop no problem. It's running sweetly. 

Any ideas? I had a bit of a dig and noticed this *identical* issue reported as a bug, but three or four years ago, all one-posters or dribbled away through lack of interest (that I found, but I'll keep looking). TIA.

---

### Post by Bucky Ball on 2016-04-10
Ok, fixed. How? Persistence! No, not a persistence USB. :| :)

I just stuck with it. I don't know if it makes any difference, but where it was crashing at the choose keyboard part, I chose to detect keyboard and let it decide it was English (US) after I'd hit some keys. Away it went and I now have Xubuntu 14.04 LTS and Xubuntu-core 16.04 LTS  on the HP Stream. Updating/upgrading it now.

I can't think that I did anything different from the umpteen other variations that I'd tried, but there you go. Solved. :)

---

