---
title: "Public Library"
date: 2007-04-26
forum: The Cafe
---

### Post by zantar2580 on 2007-04-26
Hello,
    First of all let me say that i am still green when it comes to linux. I am MS certified (i have my Id10T cert.) and prefer to use linux if nothing else than the fact that if you want to do something all you have to do is look for it and someone has created a package for you. ok with all that said i work in a little town called fayetteville arkasas and we have a library in a town not too far from here and they are running 9 pcs for public use to surf. i have set them up with an IPCop for a gateway router and content filter using dansguardian. but now i want to look at getting the workstations turned over to linux and ubuntu seams to have the most user friendly support and desktop gui, what my question is, is should i use edubuntu, xubuntu or just plain ubuntu. all they really need is web surfing and open office. but i don;t want sime 15 year old coming in and trashing the box just because he can. also i want the machins to logout every 30 minutes for the kids i have XP running on the kids boxes with MS shared tool kit and it has an option to boot the user every 30 minutes. BTW upkeep on these boxes are hell because you have 20 people a day trashing them on the net an spyware just loads up and then you have to try to clean them and they are on 256mb of ram and thats just killing me. anyway any help on this would be awsome thanks guys

Scott

BTW i am downloading Edubuntu right now to test on a box to see whats in it

---

### Post by AndyCooll on 2007-04-26
I'd say run straight Ubuntu or Kubuntu.

For the XP pc's you need something like Deepfreeze.  Kids can then trash a pc as much as they want. You then simply reboot and its back to its original state, no need to spend all that time cleaning up the pc.

:cool:

---

### Post by Iceni on 2007-04-26
I'd say Kubuntu because it can look a lot like windows. Sounds like the ram could be a problem tho - what about Xubuntu?

---

### Post by BarfBag on 2007-04-26
The 256 MB of RAM could be a problem.  If possible, I recommend upgrading to 512 MB in every machine.  If you can't, you should be able to pull it off; but it's going to be close.

Use the alternate CD, and not the live-CD.  On low RAM machines, the alternate CD is faster.

What kind of processor do these machines have?  The low RAM won't be as much of a deal if the processors are over 800 MHz.  If they're slower then 800 MHz, you should definitely go for Xubuntu.  It might be a little harder to get running, but it'll give you the best performance.  If they're at least 800 MHz, straight up Ubuntu should run fine.

---

### Post by tbroderick on 2007-04-26
I'd recommend using Debian Etch. There is no real sense in being bleeding edge, stability and security might be what you are looking for. You can always upgrade individual applications like Firefox if you want to. 

For auto-logout, you can use cron. Take a look at this example.

[http://skindley.wordpress.com/2006/12/11/fedora-core-6-controlling-logins-by-time/](http://skindley.wordpress.com/2006/12/11/fedora-core-6-controlling-logins-by-time/)

It explains how do logout a user, jordon, based on days of the week and hours, but you can easily change that so cron runs every half hour (replace 15 12 * * 6-7 with 30 * * * *). That should work. It also shows you how to make a simple pop-up warning message with zenity. That way you can alert the user that they only have *x* amount of time left before a forced logout.

---

### Post by zantar2580 on 2007-04-30
Thanks Guys all great info the cpu speed on these machines is 2.0 ghz P4. they are HP workstations.  about the deepfreeze after installing it we had weird things happen like random slow downs where the machine would lock and we reboot and its fine for a while then suddenly lock. after the removal of deepfreeze it stopped. also i know this is going to sound crazy but after a month of use with deep freeze we thaw and go updates and for giggles i ran a spybot and found some goodies. so i cleaned them and the next month same thing not the same ones and i know it wasn't in the freeze so i don't have a clue. but it would be great to switch to linux up there i think i will do a test run on one of the boxes to see how it flys

thanks again guys

Scott

---

