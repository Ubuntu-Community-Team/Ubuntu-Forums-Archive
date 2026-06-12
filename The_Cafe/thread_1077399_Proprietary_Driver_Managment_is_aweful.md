---
title: "Proprietary Driver Managment is aweful"
date: 2009-02-22
forum: The Cafe
---

### Post by beattyml1 on 2009-02-22
I would really like to know why on earth the proprietary driver manager works the way it does.  

In 8.04 using the proprietary driver manager my graphics worked ok, but then I upgraded to 8.10 and every thing just stopped working, apparently they had switched to a new **_*beta*_** version of the driver.  Does anyone else out there feel like the driver manager should always use the most recent final release driver available, and actually update it as updates come out.  

Not that I don't appreciate what the developers do it just seems like using a beta driver that doesn't work when previous drivers work doesn't seem very logical, and updating drivers as they come out seems like the logical choice.

---

### Post by cb951303 on 2009-02-22
AFAIK 177 was stable when 8.10 was released. 

EDIT: Sorry you have an ATI card

---

### Post by Skripka on 2009-02-22
> **beattyml1 said:**
> I would really like to know why on earth the proprietary driver manager works the way it does.  

In 8.04 using the proprietary driver manager my graphics worked ok, but then I upgraded to 8.10 and every thing just stopped working, apparently they had switched to a new **_*beta*_** version of the driver.  Does anyone else out there feel like the driver manager should always use the most recent final release driver available, and actually update it as updates come out.  

Not that I don't appreciate what the developers do it just seems like using a beta driver that doesn't work when previous drivers work doesn't seem very logical, and updating drivers as they come out seems like the logical choice.

Just because a driver is a "final release" doesn't mean you want it on your machine.  The 177.8 Nvidia driver had many many issues yet was *old enough* by Ubuntu's standards to be called "stable", yet it caused many headaches and problems.  But it was called "stable".

Back in the good old days, ATi was known for it's final release drivers  for windows being in fact beta quality.

---

### Post by beattyml1 on 2009-02-22
My point was more that it should 

A. Not use a Beta driver that doesn't work when a better stable driver is available 

B. Update when a significantly better driver is offered rather than just leave people with whatever was the newest driver at ubuntu release

If they adopted either of these I would be satisfied, both would be great

I am sorry if this sounds like flaming as it was not meant as such, just a little bit of constructive criticism

---

### Post by igknighted on 2009-02-22
They shipped a beta driver because there was no final release from ATI that worked with the kernel in intrepid.  What card do you have?  Did it reach EOL?

EDIT: It was either the kernel or the xserver version, I forget which.  Either way, the alternatives for Ubuntu were to stiffle its own development because ATI can't make a driver in time, or ship a beta release.  I think you ship a beta release every time in the situation, because you can pass the final as an update.

---

### Post by sloggerkhan on 2009-02-22
Nice thing about ATI cards and their proprietary driver is that you can just download the latest driver and build debs for it.

---

### Post by Vince4Amy on 2009-02-22
> **sloggerkhan said:**
> Nice thing about ATI cards and their proprietary driver is that you can just download the latest driver and build debs for it.

It also just works on most distros so you can go through the Automatic installer. I recommend to never use the Restricted Manager on Ubuntu for drivers as it usually contains a really out of date version.

---

### Post by sloggerkhan on 2009-02-23
Also, if you follow an FGLRX install guie for ubuntu that doesn't use proprietary driver manager or have you make .deb files, the instructions are bad and out of date.

---

### Post by toupeiro on 2009-02-23
I would be fine if I could just find some better documentation on DKMS...  I NEED to use proprietary drivers for some of the modeling I work with, and I would love to learn how to better use dkms to hook into kernel updates with a beta driver.   I thought DKMS was a huge breakthrough for seamless kernel updates on GUI intensive linux installations, but its rather limited if you can only use it with a specific accompanying distro repository based driver.

---

### Post by sloggerkhan on 2009-02-23
DKMS has worked fine for me with the build deb options in the fglrx driver in the past. I haven't used my ATI based system nearly at all lately, but I seem to recall as long as you had a few basic build dependancies used by the DKMS system installed things went fine.

---

### Post by beattyml1 on 2009-02-26
I just wish that it would change what driver it used if the one it used didn't work and one that does work comes out, I've heard all the stuff about just do it yourself but every time I try it seems to mess up my computer.  
Once again may I restate that I greatly appreciate what the dev's do I am just pointing out somewhere where ubuntu needs to grow if it is to get any reasonable market share, and yes I do realize that the primary blame lies with ATI, which is why I plan to get an nVidia card. :)

PS part of me wishes I hadn't started this thread, and I shall probably never make another cafe post without waiting at least a few hours after I get up.

---

