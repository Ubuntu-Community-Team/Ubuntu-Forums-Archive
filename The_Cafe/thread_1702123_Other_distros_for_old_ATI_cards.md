---
title: "Other distros for old ATI cards?"
date: 2011-03-07
forum: The Cafe
---

### Post by bcoffield on 2011-03-07
Hi everyone,

Does anyone know of an up to date distro that will give me ubuntu8.10 levels of graphical performance?  

So: something that uses x 1.5 and fglrx 9.3 ?

Or perhaps know where there is a list of distro's with this type of data attached to it so I can browse?  I've had no luck searching...


I'm fed up with the horrible performance/no compiz of all the ubuntu releases 9.4 and after... thoughts on a workable solution?

---

### Post by cascade9 on 2011-03-07
Did you even try galluim3D? 

[http://ubuntuforums.org/showthread.php?t=1701035](http://ubuntuforums.org/showthread.php?t=1701035)

---

### Post by bcoffield on 2011-03-07
I didn't have a chance yet to do that, though I plan on it.  I value your good suggestion in the other post.  

This thread was simply to see if anyone had ideas on other distros, spurned, of course, but the same issue as my initial post...

---

### Post by LowSky on 2011-03-07
The problem is the Linux kernel. AMD decided not to support the older cards. I know it sucks but its something you will need to live with or use old distros.

Software may still work on the older kernel just fine. You will just have to install it by hand or find the source to add to synaptic

---

### Post by cascade9 on 2011-03-07
> **LowSky said:**
> The problem is the Linux kernel.

Nope, not just the kernel, its xorg.

---

### Post by disabledaccount on 2011-03-07
Nope, not kernel and not xorg:
[http://support.amd.com/us/gpudownload/windows/Legacy/Pages/radeonaiw_vista32.aspx?type=2.4.1&product=2.4.1.3.13&#9001;=English]("http://support.amd.com/us/gpudownload/windows/Legacy/Pages/radeonaiw_vista32.aspx?type=2.4.1&product=2.4.1.3.13&lang=English")

...just old hardware.

Some time ago I've installed 9.04 on X1600, Athlon64 s.754, 512MB RAM - native xorg drivers are far better in scope of compatibility and often performance for old unsupported ATI HW. Compiz, flash video and some (older) games trough wine are working ok. +hibernation +fast user switching +multihead (problematic or not working at all with old ATI drivers)
(... that was my neighbour's desktop - He looked like :shock:... and now He is using linux :) )

Back to the topic: I have HD5670 in one of my desktops and everything is working just perfect (including full control over fan speed, GPU overclocking and monitoring) - so I would like to know what is the GPU model that we are talking about - this is essential information at this point.

---

### Post by bcoffield on 2011-03-07
Hi... my laptop is running an ATI mobility x600...

---

### Post by handy on 2011-03-08
If you are using Ubuntu, follow the how-to down in the "Ubuntu Stuff:" of this post:

[http://ubuntuforums.org/showthread.php?t=1238129](http://ubuntuforums.org/showthread.php?t=1238129)

it will show you how upgrade your kernel & how to install the xorg-edgers ppa. After which you should be running Gallium & getting the best performance available for your legacy GPU.

You might enjoy looking at this, I know I do these days:

[http://www.x.org/wiki/RadeonFeature](http://www.x.org/wiki/RadeonFeature)

I've been running the dev' kernel & driver stack for my AMD/ATi GPU for almost 18 months. You won't have any reliability problems. I'm currently using the .38 kernel & it is smooth as glass. :)

---

### Post by bcoffield on 2011-03-08
Thanks a lot for the info, I'm excited to try this out when I get home from work.  Last night I think I did the edgers part that you describe, however that halved my frame rate lol.  So I look forward to updating the kernel.

---

### Post by bcoffield on 2011-03-08
Oh and another thing, to address my initial question in this post regarding other distros....

Puppy linux has a version named "Wary Puppy" that is said to be long-term supported and created with older hardware in mind.  [http://puppylinux.org/main/Long-Term-Supported%20WaryPuppy.htm](http://puppylinux.org/main/Long-Term-Supported%20WaryPuppy.htm)

Puppy is a distro that I've played around with before and like a lot.  It's a tiny distro but I've seen demonstrations of compiz, KDE etc running in that environment so perhaps that too is an option for people with older hardware (in addition to this Gallium3d solution for Ubuntu).

Hopefully tonight I can fix my ubuntu and hard-drive install puppy.  fun!

---

### Post by dh04000 on 2011-03-08
I'm on Ati x1400 here. I still can't belive that they dropped support for the x1400 on my windows and linux machine a year after I bought my lappy..... still amazes me. The old Dell driver produces errors on XP service pack 3..... I'm buying an nvidia next if I can. I hear the optimus thing is REALLY screwing things up for linux users though.

ANYWAY, OP try the gallium 3D drivers in the Xorg edgers repo(google it). They are so good now that penumbra is working as well as tf2 working in wine a few weeks ago.

---

### Post by bcoffield on 2011-03-08
Hmmmmm.... okay so I'm having some issues and I'm hoping someone can guide me even further....

I followed the directions handy linked to...(i mean, i think i did...and that's prob the issue) 

I downloaded the three kernel files, the most recent version.  installed them in the correct order.  I ran ppa-purge for my other edgers attempts.  and when i went to install the package xserver-xorg-video-radeonhd it said I already had it (probably from a prior flailing around)... so i rebooted and voila!  nothing had changed...

What edgers package should i install for my card... its a radeon mobility x600

How do I manage what driver I want to actively be using?  like is there an interface something where I can choose from possible drivers that I have installed on my system.  Like how would i revert back to the base install open source driver if I wanted?  How do I even know what driver i'm currently using?

I apologize for being so dense on this... there's just something about video drivers and the like that just makes my brain go fuzzy as I'm reading about it.  I really appreciate any guidance that can be offered.

---

### Post by handy on 2011-03-08
Did you follow the how-to in the correct order from step 1. through to 6. ?

---

### Post by bcoffield on 2011-03-08
Yes I did, although I'm almost certain that I messed up somewhere in the xorg edgers step, particularly with "update, upgrade."  

Once I add the PPA what is that that I should exactly be doing?  Installing one of the packages they list?  If so, how do i determine which one is appropriate for my system?  

Thank you!

---

### Post by handy on 2011-03-09
> **bcoffield said:**
> Yes I did, although I'm almost certain that I messed up somewhere in the xorg edgers step, particularly with "update, upgrade."  

Once I add the PPA what is that that I should exactly be doing?  Installing one of the packages they list?  If so, how do i determine which one is appropriate for my system?  

Thank you!

I don't use Ubuntu, & therefore have never used the xorg-edgers ppa.

That said, my understanding is that after you have upgraded your kernel & enabled the ppa; rebooted; you should do a full system upgrade, as the ppa will have many files that are newer than what are on any standard Ubuntu install.

So go to Synaptic or whatever method you use & go through the process to upgrade/update (whatever Ubuntu calls it) of everything on your system that now can be.

---

### Post by jwbrase on 2011-03-09
I've since stopped using Ubuntu on our Radeon HD 2400 machine, but when I was using it I found that while GNOME + Compiz was unusably broken on Jaunty, LXDE + Compiz worked.

But frankly, having used one ATI and one NVidia card, I'm likely to go for NVidia for my third card. Even under Windows, I'm finding that ATI doesn't do well with OpenGL...

---

### Post by bcoffield on 2011-03-09
@handy: Ahhhhhhh!  enlightening!  thank you.  that makes good sense now.  and since, incidentally, i managed to mess up my primary ubuntu partition last night as I installed puppy to hard drive (my own dumb mistake) I will next be trying to get this working on a completely fresh 10.04 install.  And it sounds like I should be able to finally get it working.  can't wait.

@jwbrase:  thanks for the heads up, I'll keep that in mind.

---

