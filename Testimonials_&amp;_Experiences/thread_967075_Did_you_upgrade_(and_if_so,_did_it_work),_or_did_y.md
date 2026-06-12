---
title: "Did you upgrade (and if so, did it work), or did you install fresh?"
date: 2008-11-01
forum: Testimonials &amp; Experiences
---

### Post by diablo75 on 2008-11-01
It seems like a lot of people have problems when they upgrade Ubuntu from one point release to another (such as from 8.04 to 8.10 and so on).  I am curious to see just how often this actually happens in hopes of finding a way to address this because it seems as though most people are told that, in the event of an epic upgrade failure, to backup all of their data (a big hassle for most people) and then install fresh.  Should upgrading *just work*?  And if for some reason it fail, there be safety nets in place that can at the very least roll the system back to the way it was before the upgrade was initiated?

---

### Post by diablo75 on 2008-11-02
Bump?  C'mon.  It's just a poll.

---

### Post by Northsider on 2008-11-02
Upgraded fine via Update Manager

---

### Post by JohnFH on 2008-11-02
You forgot about the option "I haven't upgraded yet.  I will at some point but don't have time at the moment."

---

### Post by shen-an-doah on 2008-11-02
I upgraded and it failed but I managed to fix it via suynaptic. I might still do a fresh install though as I've broken various things on my system over time and it'll just be simpler to sort that all out with a fresh install...

---

### Post by ratmandall on 2008-11-02
Backed up my data and did a fresh install, but now I'm in 800x600 resolution :(

---

### Post by deltaprime on 2008-11-02
i ran out of space on my hdd so i gotta repartition and take some away from xp and vista all for UBUNTU = )

delta4

---

### Post by Phreaker on 2008-11-02
Fresh install

---

### Post by Eisenwinter on 2008-11-02
> **JohnFH said:**
> You forgot about the option "I haven't upgraded yet.  I will at some point but don't have time at the moment."
And the option "I don't want to upgrade".

---

### Post by Corfy on 2008-11-02
I upgraded two computers through update manager, and they both went fine.

---

### Post by mrgnash on 2008-11-02
I have upgraded since at least Gutsy. I have /home on a separate partition, so I don't need to worry about losing any data.

---

### Post by alzie on 2008-11-02
I'm currently undecided.  My aging computer (1.8 Ghz AMD 768 Meg ram) is working ok with Hardy but I did feel a bit of a performance hit with the upgrade from Gutsy.

As Hardy is LTS I'm seriously considering staying with it until I can afford to upgrade my system.  If anyone can tell me if they noticed that Intrepid runs the same or better then I may move up.

On a side note, my Updates are currently coming in at about 20 Kb/s so I won't be doing any upgrade today:lolflag:

---

### Post by AndyCooll on 2008-11-02
Did a clean install.

I've had issues with upgrading in the past so these days I just automatically do a clean install. It also gives me the opportunity to clean out any crap I've installed in the last six months and such like. And since I too have my /home on a separate partition it doesn't take long before I'm back with a running system and my customisations.

:cool:

---

### Post by userundefine on 2008-11-02
I upgraded and rebooted to the very annoying fact that parts of my keyboard didn't work (my right arrow didn't work, and I couldn't figure out why).r  So I burned an ISO to do a fresh install, the ISO was flawed even after burning on a low speed (thank you, gnome burning app) I found out at 47% during the install, so my system was rendered completely useless.  Luckily I had an old feisty install on an external hard drive that I booted to from USB, reconfigured X on that install to work with my laptop, mounted my laptop's internal hdd, then downloaded k3b to burn and verify that the data was correct.  THEN I installed from that cd afresh, and it was fine.  Except now I've got a few issues with the kernel locking up my system randomly.  I'm not impressed at all with ubuntu's upgrade ability.

---

### Post by kyalee on 2008-11-02
I loaded fresh, mainly because I put in a new hard drive, but also because I was hoping it would solve some nagging problems I was having and it did...mostly...

---

### Post by K.Mandla on 2008-11-02
Moved to Testimonials and Experiences.

---

### Post by Warren Watts on 2008-11-02
I used the update manager to upgrade from 7.04 to 7.10 (which I am using now) and didn't encounter any problems.  This particular machine is a 550 MHz PIII with only 384 MB of RAM, so I think I am gonna stick with 7.10 rather than upgrading this machine any further.  
  
I have read quite a few posts that seem to indicate that with each successive new release, Ubuntu seems to get more and more sluggish.  Since this machine is pretty sluggish already running 7.10, I am reluctant to #1, slow the system down any further, and #2, risk the chance of borking Ubuntu while upgrading.

---

### Post by delanov on 2008-11-03
Down loaded popped in the CD and let 8.1 wipe the HD of XP and 8.4.  8.1 installed smoothly and I'm pleased with results :)

---

### Post by vikramaditya on 2008-11-03
**Massive phailure!!!** :-x Oh no...wait...Mummy's Only Looking for Her Hand in the Snow.

---

### Post by TimboUK on 2008-11-03
I dont want to bang on that Im very happy with the smooth upgrade to 8.10 (as Ive already made a thread on it)

However, I think when Jaunty is released I will do a clean install instead of just upgrading 8.10.  I like to "fiddle" with Ubuntu and by the time Jaunty is release Ill of done about a year of it, so a clean install will probably be for the best.

---

### Post by armandh on 2008-11-03
with the ability to change anything comes the opportunity to foul every thing including a future upgrade

there is no guarantee once you have loaded restricted drivers/codex/unsupported programs/etc.

actually there is no guarantee at all

so if you are not satisfied there is no extra charge

---

### Post by kenono on 2008-11-03
I upgraded, I did backup all my data before hand though.
Nothing went wrong, very smooth upgrade, I was pleased.

---

### Post by shen-an-doah on 2008-11-03
I must say, the wonder of Linux/Ubuntu means that a clean install is pretty quick and easy.

- Copy home directory to external drive
- Reinstall
- Install everything you need/want (just a few clicks thanks to synaptic)
- Copy home directory back

And bang! All your settings and everything is back to normal. I defy anyone to find a way to do that with Windows...

---

### Post by VanCardboardbox on 2008-11-03
Did a clean install. I dual boot Ubuntu/XP and since it was time for an XP re-installation anyway I decided to just nuke everything and start from scratch. Got a new larger HDD for the OS's (lots of room for virtual machines now) and finally created a separate partition for /home. 

I hit one snag, but it was quickly fixed after some research. I use Ext2IFS in XP to read/write to Ext3 partitions. When I installed Ext2IFS this time around XP would not recognize a shared Ext3 partition I created while installing Intrepid. Turns out the inode size on the Ext3 partition was 256 (newer distros will use this inode size by default), but Ext2IFS can only cope with 128. Rebuilt the file system specifying inode of 128 and XP could read and write to the partition.

So far so good with Intrepid. Now to see how well XP will cope with My Documents pointing to directory on the Ext3 partition...

---

### Post by inportb on 2008-11-03
I did a clean install and did not backup or format my home partition. It was pretty smooth.

---

### Post by malleus74 on 2008-11-03
I installed 8.04 a couple weeks ago, doing a dual partition with Vista. This worked fine... only thing I had a problem with was getting madwifi to work with atheros drivers (AR5007).

I allowed a kernel upgrade to .24-21, and my wifi died, and the upgrade failed. We figured out on another thread if I reinstalled grub (I was using gfxboot only), the update worked, but I still didn't have wifi. After tinkering around with it for a while, I installed the upgrade for "critical security", and lost the gui, but could still get use the distro through the older .24-19 kernel.

I tried to upgrade to 8.10, thinking this might help the issues, but the upgrade didn't work. I was left with some kind of hybrid 8.04 / 8.10.

So, I started over with 8.10, and so far all the hardware (including wifi) right away. I'm now trying to get all the multimedia, etc, to work, but it's looking good. Since I'm pretty happy right now, I'm going to image the partition soon, just in case :) , maybe with remastersys or partimage. Any suggestions?

---

### Post by rfarmer on 2008-11-04
I was advised early in my linux experience to create a separate /home partition and do a fresh install. And since the debacle of the 7.04 to 7.10 upgrade I have followed that path. 8.10 installed flawlessly and corrected several issues I had with 8.04. 

It is a shame to see so many having issues with this release, for me this might be the one that gets me away from windows completely. :)

---

### Post by BigSilly on 2008-11-04
Installed 8.10 afresh on Halloween, and it's been fantastic, just as all the previous versions have. Set it up with multimedia and whatnot within an hour, and it's been a dream to use since. When I read of other people's problems, I can hardly believe it's the same OS we're talking about.

No OS is perfect, but this is about as close as I've ever been to it on this PC. Very happy user indeed.

---

### Post by Dorkenfarber on 2008-11-05
I upgraded with the update manager and everything went perfectly. :)

---

### Post by Datalanche on 2008-11-05
Interesting poll results versus what you'd think reading the forum. ;)

I upgraded my 8.04 install using update manager and was successful, but I made sure to take precautions such as removing my EnvyNG-installed Nvidia driver before doing so. It worked just fine. I see only one hitch. I tried using the nvidia driver supplied with Intrepid since it's the 177 version, which I had very good luck with in the past on Windows and Linux, and it seems to forget my monitor's top resolution of 1680x1050. If I go into the NVidia X Server Settings panel, I can set it, hit apply, and I'm back in business, but the Screen Resolution panel does not list this resolution until I set it in the NVidia one.

Compared to some past upgrades, it was VERY smooth.

---

### Post by Gausian on 2008-11-05
i did both.  i upgraded first and everything worked fine.  although i then did a clean install for some unknown reason, and that worked fine as well:guitar:

---

### Post by michaelzap on 2008-11-05
I voted that I did and upgrade and it worked fine, which is sort of true. The upgrade process went flawlessly, but I'm having a helluva time actually using my new system because all browsers crash constantly (see my other threads for everything I've tried to do to fix it, and how heartbreaking an epic fail it's been so far). I'm really swamped with work so I don't want to make time to try a fresh installation, but I may have to if I can't get this fixed (and if browsers still crash constantly after that I'm just gonna sit on the stoop and weep).

---

### Post by RichardLaurenson on 2008-11-06
yep upgraded via synaptic manager. 
A numb er of things didn't work, 
most importantly

OOfice3 crashed when I try to display red squiggles under bad thpelling.
Crossover office would not play nice with one note 2007 anymore
and since these things I need, for different reasons, i reinstalled 8.04 and am working again quite stable. I shall wait a while before trying again.
and the new networking thingi I like seeing what Is happening, and couldn't figure how to get it to dial via celphone which the only reason i use vista, as my phone does not play nice with linux.

---

### Post by deltaprime on 2008-11-06
i upgraded my server and it messed up my ebox and some config files that i had configured.
so i reinstalled 8.04 and updated it to see if the problems came from the updates.

yes!

i had to reinstall my  server again and make sure not to update anything that is related to samba, my mail server or any of that. 
system is up and running again :popcorn:

but no 8.10:(

ohh well its stable tho so i am just going to leave it until i have a couple of days off. and am willing to mess with finding out which config file caused the error.

---

