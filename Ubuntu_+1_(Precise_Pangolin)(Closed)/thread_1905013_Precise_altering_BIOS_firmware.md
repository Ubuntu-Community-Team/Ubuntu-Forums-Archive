---
title: "Precise altering BIOS firmware"
date: 2012-01-05
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by VMC on 2012-01-05
I've never seen any thing of this sort nor how to create a bug report.

For the past three ISO sessions, my BIOS gets altered using Precise.

First I thought it was my USB ports going bad, then I found out it was only happening using Precise. It happens on both USB sticks and USB hard drives, and now I found it it happens on CD/DVD's as well.

Everything boots correctly but on reboot my BIOS time is reset and some other settings are effected.

I then tried using UNetbootin with the same results. Thinking it was Startup Disk Creator as the culprit.

To make sure I created another USB boot using an older Ubuntu distro and other distro's as well. They all work without incident.

 All pointing to Precise Pangolin as the culprit.

I'm wondering if anyone else has noticed any strange behavior after using Precise.

I have an **HP Pavilion Slimline s5310y** PC.

---

### Post by jfernyhough on 2012-01-05
Have you tried an earlier kernel?

It could be that the power saving patches with 3.2, I'm thinking the ASPM stuff, is having some effect. Might be a quirk of your system?

---

### Post by VMC on 2012-01-05
I'm using 3.2 kernel on Fedora without any issues.

---

### Post by grahammechanical on 2012-01-05
It would be interesting to know what BIOS settings specifically are altered and by how much the time has changed.

Also, what do you mean by iso sessions. I am confused. Are you installing Ubuntu Precise on to the hard disk or booting from an install on USB memory stick with persistence?

During an installation of Ubuntu we set the time zone. Is the OS time zone different from the BIOS time zone? Is the OS time set to be adjusted automatically from the Internet?

I am thinking that Ubuntu is being developed in a direction where it will be (it is hoped) pre-installed on tablets and even mobile phones. The Unity interface will unite the look across all the devices that Ubuntu is on. So, setting the time and date of the device through the User Interface is not such a strange idea.

This may be a design feature that is being made functional in Precise.

Regards.

---

### Post by teh603 on 2012-01-05
Y'know, I've been having system time issues with Precise as well. But then again, when you set the system clock, isn't it supposed to change the one in the BIOS? Its not like you're flashing it or anything...

---

### Post by VMC on 2012-01-06
> **grahammechanical said:**
> > It would be interesting to know what BIOS settings specifically are altered and by how much the time has changed.The system time is completely reset to factory settings of 01/01/2002, and time is set at 00:00
Also each time I find one of my partitions is corrupted. fsck fixes that, nonetheless.

[QUOTE]Also, what do you mean by iso sessions. I am confused. Are you installing Ubuntu Precise on to the hard disk or booting from an install on USB memory stick with persistence?I mean I use the precise ISO and startup disk creator to create a usb boot disk, either hard drive, stick or cd/dvd. Then upon booting said device and using it as live session. After reboot is when firmware is altered.

> During an installation of Ubuntu we set the time zone. Is the OS time zone different from the BIOS time zone? Is the OS time set to be adjusted automatically from the Internet?
This has nothing to do with it. If I just boot up to menu then reboot without even using livecd, my BIOS has been tampered with.

edit:The reason I even notice this happening is my BIOS on boot up delivers a blue screen with color lettering, when Precise boot disk is used on reboot my BIOS is in a black and white lettering and unusual font. I have never seen that before I tried booting with Precise.

---

### Post by dino99 on 2012-01-06
some times ago i've posted the same issue:
[http://ubuntuforums.org/showthread.php?t=1902573](http://ubuntuforums.org/showthread.php?t=1902573)

i got this trouble only 2 days on Precise i386 + q9550 + microcode
what i've seen:
- boot error message about time/date lost
- but bios settings are ok (not changed)

so it seems that the bios time settings was not understood correctly (at least for these 2 days on my system) by some boot processes, but in any case bios settings are modified.
Anyway package upgrades have been done since, and i've not seen this issue back.

Maybe force a reconfig:

sudo dpkg-reconfigure -phigh -a
( can take a while, be patient and dont stop it before it end itself)

note: i'm only using genuine packages, no ppa around. If you are using extra archives, maybe purge them (ppa-purge for ppa)

---

### Post by portis on 2012-01-06
I had the same problem on a Lenovo T410 laptop.
I thought it was my BIOS battery run out.
Where should we fire a bug report?

---

### Post by sammiev on 2012-01-06
My clock and date has been out to lunch for a bit now. Yesterday I only used Win7 and everything was good this morning. I bet by lunch time I will be showing the year 2018 again now I'm using Precise this morning.

---

### Post by dino99 on 2012-01-06
> **portis said:**
> I had the same problem on a Lenovo T410 laptop.
I thought it was my BIOS battery run out.
Where should we fire a bug report?

when we dont know exactly which package to blame, then report against ubuntu

ubuntu-bug linux

---

### Post by rajeev1204 on 2012-01-06
Is it possible to alter the BIOS through the OS? What if the BIOS Is password protected? Will it still be altered?

---

### Post by dino99 on 2012-01-06
> **rajeev1204 said:**
> Is it possible to alter the BIOS through the OS? What if the BIOS Is password protected? Will it still be altered?

altered no, as the bios is on a rom; only flashable one's can be updated with genuine factory tool. The os only can modify the bios settings loaded into ram, but never change bios itself.

---

### Post by kaldor on 2012-01-06
I use the latest daily build (via unetbootin) roughly once a week. Last time I did it was on January 3. I have had no such problems at all.

Using a modern HP Pavilion PC also.

---

### Post by ramesh1.k on 2012-01-07
I can confirm what VMC has seen. Please refer to the link below. 

Long things short. I had raised a bug for harddrive sound on shutdown and was suggested to use the latest kernel. 

I used mainline build v3.2-rc7 and I faced the same problem namely; 
1. my clock in bios is messed up (sometimes it defaults to 2010 and sometimes 2018 ) 
2. Windows 7 became unstable (surprisingly) 
3. Ubuntu did a disk check 
4. my clock in windows7/ ubuntu runs either fast or slow or resets!!!. Please refer to post #3 for the same.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/908310](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/908310)

---

### Post by dino99 on 2012-01-07
> **ramesh1.k said:**
> I can confirm what VMC has seen. Please refer to the link below. 

Long things short. I had raised a bug for harddrive sound on shutdown and was suggested to use the latest kernel. 

I used mainline build v3.2-rc7 and I faced the same problem namely; 
1. my clock in bios is messed up (sometimes it defaults to 2010 and sometimes 2018 ) 
2. Windows 7 became unstable (surprisingly) 
3. Ubuntu did a disk check 
4. my clock in windows7/ ubuntu runs either fast or slow or resets!!!. Please refer to post #3 for the same.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/908310](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/908310)

how old is your bios battery ? seems not able to save your config.

---

### Post by Basher101 on 2012-01-07
> **dino99 said:**
> how old is your bios battery ? seems not able to save your config.

this is the most plausible explanation. system time uses a small battery that is implemented somewhere on your motherboard (i had similar system time problems on a stone-age computer my dad once found lying in the basement...) looks like the battery is almost empty?

---

### Post by zika on 2012-01-07
> **Basher101 said:**
> this is the most plausible explanation. system time uses a small battery that is implemented somewhere on your motherboard (i had similar system time problems on a stone-age computer my dad once found lying in the basement...) looks like the battery is almost empty?
[http://en.wikipedia.org/wiki/CR2032_battery](http://en.wikipedia.org/wiki/CR2032_battery) ;)

---

### Post by sammiev on 2012-01-07
After using Win7 for one day I seem no longer to have troubles with my bios. Time, date and year are bang on which was out by many years, hours and so on. Well in Linux trying to set the following I could watch it change by the min if not the hour.

---

### Post by xyzzyman on 2012-01-07
> **sammiev said:**
> After using Win7 for one day I seem no longer to have troubles with my bios. Time, date and year are bang on which was out by many years, hours and so on. Well in Linux trying to set the following I could watch it change by the min if not the hour.

Then try the mainline 3.2 kernel: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.2-precise/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.2-precise/)

That is without ubuntu's tweaks such as the ASPM backport fix, etc.. That should be as close to the 3.2 kernel that you use with Fedora. That'll narrow it down. I know this happens on some systems when setting up a hackintosh including my own, so researching why it happens on those may also lead you in the right direction.

---

### Post by ramesh1.k on 2012-01-08
> **dino99 said:**
> how old is your bios battery ? seems not able to save your config.

This is a new HP DV6T; a couple of months old, at best. Didn't know if the battery could go this fast.

Windows 7 and Ubuntu 3.0.x kernels seem to be able to hold date & time without problem. I am now pretty sure the problem is with 3.2 kernel as it is reproducible whenever I boot into it.

Hope this helps.

---

### Post by Irihapeti on 2012-01-08
I was having a few problems with the BIOS time settings about a week or so ago and I was also getting file system errors on a shared partition when booting into Precise (I dual boot with Lucid).

From what I could see, the time issue was due to confusion between NZDT and UTC. Possibly, Precise was thinking that the BIOS should be set to NZDT, which caused the time to appear 13hrs ahead when I booted into Lucid.

Neither error has happened for a while now, so I'm assuming that one of the updates fixed it.

---

### Post by VMC on 2012-01-10
I will mark this as solved as I can work around the BIOS time issue.

It might be just the way ubiquity has ordered the install.

 Although I have installed ubuntu testing for years now, this is the first time I encountered this unusual BIOS behavior.

In the past, I I use Livecd to test it. After rebooting nothing has been changed. This release changes my time no matter if I install or just use Livecd.

---

### Post by Telengard C64 on 2012-01-10
Is it just me, or is there some confsion in this thread between the terms [BIOS](http://en.wikipedia.org/wiki/BIOS), [CMOS](http://en.wikipedia.org/wiki/Nonvolatile_BIOS_memory), and [RTC](http://en.wikipedia.org/wiki/Real-time_clock)? Feel free to ignore the rest of this post if I'm mistaken.

The RTC (Real Time Clock) is the equivalent of a wristwatch on your motherboard. It relies on a battery to keep time when there is no power to the motherboard (such as when the power cable is unplugged.)

The CMOS is a small memory device outside the system's main memory. It is a physically separate component. It is used to store hardware configuration information needed to make the computer operational on powerup.

BIOS is the program used to configure the computer's hardware, such as the RTC and CMOS settings. It is stored in an area of erasable ROM called flash memory. BIOS is the first program run when powering on the computer, and is responsible for finding a media to boot the OS from.

---

