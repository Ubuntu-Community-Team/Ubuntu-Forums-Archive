---
title: "A critical review of Feisty"
date: 2007-04-30
forum: The Cafe
---

### Post by Tux Aubrey on 2007-04-30
Check out this review [LINK]("http://apcmag.com/5981/hands_on_with_ubuntu_7_04_part_1") 

I think he makes some good points (and I had exactly the same problem with a widescreen monitor).  

Aubrey

---

### Post by aysiu on 2007-04-30
While I agree with the observation that Ubuntu's configuration of screen resolution could improve a lot (including a GUI frontend for Xorg), I disagree with the conclusions, for the usual reasons:

1. Any Windows user who bothers to install a new operating system is a power user and can suck it up and add a modeline to the /etc/X11/xorg.conf--it's a lot easier than hacking the registry, which power users have all done in the past.

2. Most other Windows users would never install Ubuntu themselves anyway. In a dream world, they'd buy Ubuntu preinstalled or get a more tech-savvy friend to fix any problems (which is what happens now in Windows anyway... do you think my mom solves all her Windows problems herself?)

3. Nvidia drivers are separate from the kernel, so that makes things a bit more complicated. Good thing Ubuntu is working on Nouveau.

---

### Post by jrusso2 on 2007-04-30
Yes all these problems need to be addressed.

---

### Post by Tux Aubrey on 2007-04-30
I agree with you 100%, aysiu.  I made a reply to the author along the same lines.  I think the "Desktop readiness hurdle" for Linux is much higher than it is for Windows given that it has to be installed by the user.

It would be interesting, but probably pointless, to set up a controlled experiment giving a random sample of computer users a bare machine and the installation disks for several flavours of Linux and Windows.  I know that the last (hopefully the very last!) time I installed XP it took me several hours and lots of tweaking.

---

### Post by aretei on 2007-04-30
very honest review and exactly what the community needs.
it was also interesting to read people's comments at the bottom of the page 2.

---

### Post by Dr. C on 2007-04-30
I recently changed my monitor to a 24 in LG L246WP runing at 1920 X 1200 on my Dapper system. 

The first  thing I did was open a terminal and entered 

sudo gedit /etc/X11/xorg.conf  

and then added "1920x1200" twice  to all the modes lines, removed the duplicate "1600x1200", saved the file  then shut the system down. 

I then removed the "Certified for Windows Vista" sticker from the new monitor unpluuged the old one and plugged the new monitor it into the DVi output of my Nvidia 6200 Video card (I am using the NVIDIA Drivers) Then I restarted the system and it has worked great ever since. Did not think much about this until I saw this post. I have been using Ubuntu for just under a year.

---

### Post by jiminycricket on 2007-04-30
maybe xorg 7.3 can fix it.  Then there's SimpleXSelector that's might be in GutsyGibbon, you can read a spec of it on the Ubuntu wiki.

I agree a nice mouse configuration tool would be great.  It seems that X knows that all my buttons exist, I just can't map anything to them.

---

### Post by DoctorMO on 2007-04-30
The odd thing about monitors is that some of them report the wrong supported resolutions in their ddc and i2c data. I mean how the heck is xorg supposed to guess what resolutions are available?

In the end ddc/i2c will mealy concern them selves with grabbing monitor id's and using a big database of monitor supported resolutions and sync data; once this is done and done right and a few gui tools created so you can edit this information about your own monitor and maybe send it back to the xorg devs.

All this stuff will come, but as always some of the major problems are where the hardware makers don't bother to follow the specifications of standards.

(don't get me started on ieee1394 devices and no product ids)

---

### Post by FoolsGold on 2007-04-30
Very useful review.

It's important to pay attention to such articles, particularly when they're well written and with good intentions. The only was to improve Linux/Ubuntu is to be honest about its shortcomings.

---

### Post by thekat on 2007-09-21
> **FineE said:**
> I recently changed my monitor to a 24 in LG L246WP runing at 1920 X 1200 on my Dapper system. 

The first  thing I did was open a terminal and entered 

sudo gedit /etc/X11/xorg.conf  

and then added "1920x1200" twice  to all the modes lines, removed the duplicate "1600x1200", saved the file  then shut the system down. 

I then removed the "Certified for Windows Vista" sticker from the new monitor unpluuged the old one and plugged the new monitor it into the DVi output of my Nvidia 6200 Video card (I am using the NVIDIA Drivers) Then I restarted the system and it has worked great ever since. Did not think much about this until I saw this post. I have been using Ubuntu for just under a year.

I also have this LG monitor.. followed your instructions..
Works like a charm.
Much Thanks
tk

---

