---
title: "Starcraft 2 installation"
date: 2011-03-10
forum: Wine
---

### Post by Somanayr on 2011-03-10
Hi there!
I'm trying to install SC II on my computer (Ubuntu 10.10). I followed a tutorial on installing, but something funny happened... buttons aren't showing up. For example, the install button, the exit button. I can click them, but not see them. Here's a picutre:

[IMG]http://img138.imageshack.us/img138/7695/scproblem.png[/IMG]


Help, please :D

---

### Post by anagor on 2011-03-10
Have you tried installing it from playonlinux?
I'm currently running the installation, but since it's a digital download it will take some time before I can report if everything went smoothly.

Cheers,

---

### Post by fijiblue on 2011-05-25
Hey, 

I was having this exact same problem earlier today, but I managed to solve it. 

I'm running 11.04 on an Acer 3820TG with an interchangeable graphics setup (Intel onboard and ATI dedicated). I only attempted installing SC2 after I had installed the ATI Catalyst driver and when I attempted to install it through Wine, I never got the buttons to show.

Solution:
Disabling the (ATI) graphics card seemed to work simply by going into the ATI Catalyst Center and switching to my secondary graphics card. 
Because you may not have this option, and because you may be using a different graphics card/driver, I suggest using the following method.

Reboot your computer and access the GRUB menu by holding shift. Select the recovery mode and run Ubuntu in the low graphics setting. Finally, attempt to install through Wine. 

I hope that solution helps - even though I haven't had a need to use it. I'm just basing this solution off of what limited knowledge I have on Ubuntu (and that's not a lot!).

Anyways, good luck on your install!

---

