---
title: "Ubuntu was cool but..."
date: 2008-03-13
forum: Testimonials &amp; Experiences
---

### Post by Foxray on 2008-03-13
I've used Ubuntu since Fiesty came out and I loved it but I was excited when Gutsy came out. So I installed a fresh copy of gutsy on the comp, but ever since then I've been having so many problems. I love Ubuntu's huge repository and its a cool distro and all but I just might go back to Fedora. 

My computer ramdomly locks up every now and then at random intervals. I'm not exactly sure whats going on but I've restarted my computer like more than 10+ times today. I'm pretty sure ubuntu isn't supposed to lock up that way.

By Lockup I mean display freezes no keyboard commands work, no mouse nothing. Alt-Ctrl-Bksp or Alt-Ctrl-F1 or Alt-Ctrl-Del none of them work. Its like the lights are on but no one is home.

It could be flaky nvidia drivers it could be something else but I can't find out since once it locks up and I reboot to take a look at /var/log/messages and other log files show nothing out of the ordinary. Maybe I'll try Hardy Heron when it comes out but Gutsy just doesn't like my computer. Hardy's only a month away so I just might put off reinstalling until then but as of now this comp is barely usable at its current condition.

---

### Post by kellemes on 2008-03-14
If Fedora works.. go for it, nothing wrong with that.. well, except for RPM that is.. ;-)

Don't forget there are 350+ distributions out there and a couple BSD's that are really cool too.
If Ubuntu isn't able to run your hardware go get Sidux, Zenwalk, PCLOS, openSUSE, Mint, Fedora, CentOS or the best freeking distro of all.. Debian!! ;-)

---

### Post by sandysandy on 2008-03-14
does ubuntu freeze while u r working on it  or when it is idle (screen saver mode)

regards

---

### Post by 3rdalbum on 2008-03-14
Do the lights on your keyboard start flashing? If they do, then that's a kernel panic. If any messages have been written to a log, they will be in /var/log/kern.log. If you have any error messages near the end of the log for that particular session that begin with [nvidia], it's likely that the Nvidia driver is the cause (I had this problem).

Otherwise, it might not be a kernel panic - it might just be an Xorg crash. In which case, pressing Alt-Printscreen-R should put your keyboard into "raw" mode, and then the Control-Alt-F1 terminal command should work.

---

### Post by Foxray on 2008-03-14
I have a hunch that it might be a bad power supply thats causing the freezing problem. But this psu is only a couple months old, its a SeaSonic S12-330 ATX12V 330W Power Supply. 

I run a Asus IC7-G, Pentium 4 3ghz, 1gb pc2700 ddram, Geforce 6600gt on Xubuntu. Maybe the power supply isn't providing enough power to the system so it locks up?

I've checked the kern.log file and it doesn't show any nvidia driver problems and the keyboard doesn't start flashing so its not a kernel panic. I'll try a 500W psu on this comp next week just to be sure it isn't the psu.

---

### Post by fillintheblanks on 2008-03-14
I have the same gfx card (xfx 6600 gt)

I'm pretty sure it needs at least 420 watts PSU, what it said on the box anyway..

my psu is 400 no lock ups thankfully

---

### Post by ukripper on 2008-03-14
Are you using COMPIZ?

---

### Post by Foxray on 2008-03-14
Nope not using compiz

---

### Post by ShodanjoDM on 2008-03-14
> **Foxray said:**
> I have a hunch that it might be a bad power supply thats causing the freezing problem. But this psu is only a couple months old, its a SeaSonic S12-330 ATX12V 330W Power Supply. 

I run a Asus IC7-G, Pentium 4 3ghz, 1gb pc2700 ddram, Geforce 6600gt on Xubuntu. Maybe the power supply isn't providing enough power to the system so it locks up?

My previous pc had a Nvidia AGP 6600 (non GT version). It won't even booted up with the 350W PSU.

---

### Post by Joeb454 on 2008-03-14
Lets us know what happens with the bigger PSU in :)

---

### Post by kamaboko on 2008-03-14
> **3rdalbum said:**
> Do the lights on your keyboard start flashing? If they do, then that's a kernel panic. .

This has been happening to my Vostro 1400 laptop a lot.  It's driving me nuts!

---

### Post by freebeer on 2008-03-14
> **3rdalbum said:**
> that's a kernel panic. 

hmm... would a copy of the Hitchiker's Guide to the Galaxy help?  Is it in the repos yet? :D

---

### Post by Foxray on 2008-03-14
Well I decided to wipe the partition and install a fresh gutsy on it. Went thru all the updates and installed the nvidia drivers again. It seems it only happens when I run opengl it freezes. I decided to run glxgears for a couple minutes and a couple minutes later it locked up again. Oh Well it was worth a try.

---

### Post by Foxray on 2008-03-15
Update: I memtest my ram that was fine, I replaced the PSU with a 500W power supply and it still freezes so bad psu is out of the question. Now its either the motherboard or the video card. I'm swapping an older video card into it today, then we'll see what happens.

---

### Post by Foxray on 2008-03-15
ITS THE VIDEO CARD!!! I replaced the current Geforce 6600gt video card with something from my dusty hardware closet, a Geforce2 MX400 video card and bam no freezes or crashes. A bit tad slow but it works, I'm thinking of getting an ATI 9xxx card from the store is it possible to uninstall nvidia drivers and install ati ones? or do I need to reinstall ubuntu?

Thank you all for your inputs its been very helpful and now I can stick with ubuntu :)

---

### Post by Perfect Storm on 2008-03-15
Install the ATI drivers, and change the xorg.conf should do it.


But be adviced and examin which card you had in mind and search the forums for eventual problems and if the card is supported.

---

### Post by chewearn on 2008-03-15
I have a nvidia geforce 6150; after reinstall to Gutsy around November last year, I have random lock-ups for few weeks.   The lock-ups were like yours; hard locks, the mouse and keyboard failed totally.

Right around Christmas, nvidia release 169.09 driver; there was also a kernel update around the same time.  I'm not sure which of the change did it, but the problem no longer occurred.

Just thought you might want to give it a try: update to the latest nvidia driver.

---

### Post by Joeb454 on 2008-03-15
**Artificial Intelligence** has a point, you should make sure you're not going to run into any issues with the ATi card, we all know that ATi support still sucks in Linux :p

---

### Post by Foxray on 2008-03-15
Its confirmed its the video card problem. The crashing was a prelude and indication that the card was going bad. Now it won't even boot up anymore higher than 1024x768 resolution before the nvidia driver was even loaded, also did the same thing using the nv driver. I swapped a spare video card and everything is fine now.

This old geforce2 mx400 card may be crappy but it does the job. No need for 3d no compiz (not like I ever used it anyway) I only use my comp to chat on irc and watch some videos and this old card works like a charm on those things.

Getting a new computer soon anyway to replace this old pentium 4 I built back in my college days. Thank you everyone who offered their support to me. The Ubuntu Community is best I've seen since the gentoo days.

---

### Post by Joeb454 on 2008-03-15
Why thankyou (on behalf of the community of course ;))

---

### Post by ukripper on 2008-03-15
> **kamaboko said:**
> This has been happening to my Vostro 1400 laptop a lot.  It's driving me nuts!

My Vostro runs perfect without any kernel panic lights on Gutsy. Have you installed Hardy kernel?

---

