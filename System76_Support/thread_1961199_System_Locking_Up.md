---
title: "System Locking Up"
date: 2012-04-18
forum: System76 Support
---

### Post by Balthazar_Droid on 2012-04-18
I am posting this here because I have a System 76 system, but I'm pretty sure it doesn't have anything to do with System 76. If I need to move this post please let me know.

So, I have a System 76 Wildebeest Performance desktop that I bought with a 2TB harddrive and an i7 processor and 8GB of memory. I have since added another 2TB harddrive (SATA) and an older 500GB harddrive (PATA). I recently purchased an Intel 520 Series Cherryville SSD (2.5" 120GB SATA III MLC Internal Solid State Drive). Since we are so close to the release of 12.04 I went ahead and installed the latest release candidate instead of 11.10. The SSD is my primary hard drive and I have it partitioned with 20GB for / and the remainder on /home. Swap is on on of my hdd.

The problem I'm having is that occasionally my computer will just freeze. I am using it to host media files for my HTPC and the HTPC can still get video from it but the interface is locked up. I can't even drop down to a terminal. The only way to reboot it is to Alt-Rescue-REISUB. Once it reboots it will get past the BIOS screen and just hang on a black screen with a flashing cursor. I do not even get a GRUB prompt. At this point I have to boot off of the live USB I used to install 12.04, run Boot Repair and fix Grub. Once I reboot I can get to the GRUB menu and everything runs fine. This little cycle will repeat itself every two or three days.

So my question is this: Has anybody experienced a similar problem before? And if so, what can I do to fix my system? Like I said before, I don't think it has anything to do with my Wildebeest system as it was working perfectly before I added the SDD. Could it be a faulty SATA cable on the SSD, a bad SSD, complications from installing 12.04? If it helps I have pasted the latest syslog at [http://pastebin.com/W8pDachA](http://pastebin.com/W8pDachA). I am a noob; I didn't know what to look for. Any help you guys have would be greatly appreciated.

---

### Post by isantop on 2012-04-19
Is there any particular reason you have the partitions divvyed up like that? I would keep all the swap I can on the SSD, and it's unecessary to keep a separate /home these days.

---

### Post by Balthazar_Droid on 2012-04-19
I put swap on the spinning disk because 1) I thought the constant read and writes would affect the life of the SSD, and 2) I have 8 GB of RAM and don't hibernate, so I don't think it even gets used.

I have my / and /home on different partitions because I like to tinker, and being pretty new to Linux, I wind up screwing stuff up more often than not. Having separate partitions allows me to do a fresh install without losing my data.

I pulled a section of my most recent syslog (it happened again today) and there seems to be a lot of connection status errors for ata1 right before it freezes. / is on SDA1, am I correct in assuming the SSD is losing connection for some reason? 

Syslog: [http://pastebin.com/WxHdRAAq]("http://pastebin.com/WxHdRAAq")

---

### Post by isantop on 2012-04-20
With Ubuntu's modern installer, you can actually perform an "Upgrade" from any version of Ubuntu to any other version, even if the two are the same. In this case you would simply start the installer, and choose upgrade to reinstall the OS without affecting files in /home (Technically, this process performs a fresh installation without formatting the partition first, and it only erases system directories like /usr /bin /var etc.)

As for the swap, since it likely won't be used very often, I would definitely keep the swap partition on the SSD, since in the event that the system does need to use it, this will prevent it from dragging the performance of the rest of the system down. 

You might consider re-downloading and reinstalling Precise. My guess is that there was a slight error with either the download or the burn, and that caused something to get installed incorrectly.

---

### Post by Balthazar_Droid on 2012-04-23
> **isantop said:**
> With Ubuntu's modern installer, you can actually perform an "Upgrade" from any version of Ubuntu to any other version, even if the two are the same. In this case you would simply start the installer, and choose upgrade to reinstall the OS without affecting files in /home (Technically, this process performs a fresh installation without formatting the partition first, and it only erases system directories like /usr /bin /var etc.)

As for the swap, since it likely won't be used very often, I would definitely keep the swap partition on the SSD, since in the event that the system does need to use it, this will prevent it from dragging the performance of the rest of the system down. 

You might consider re-downloading and reinstalling Precise. My guess is that there was a slight error with either the download or the burn, and that caused something to get installed incorrectly.

Thanks for the advice, but it didn't work. I actually decided to download Oneric, thinking I would eliminate the chance of something buggy in Precise. I am still having the same issues. I also replaced the SATA cable and used a different SATA port on the motherboard. Still the same problem. From what I can tell when I boot into a live usb my two partitions on the SSD won't stay mounted. If I open Nautilus I can see all of my drives. I can mount all of the HDDs and they will stay mounted. My SSD (both partitions) will show up one second and randomly not be detected the next. This happens whether they are mounted or not. Then they will pop back up a couple of seconds later.

Is there something I should have done with the SSD when I installed it that I am overlooking? Some kind of BIOS setting? FSTAB setting? Did I just get a bad SSD? :confused:

---

### Post by isantop on 2012-04-24
> **Balthazar_Droid said:**
> Thanks for the advice, but it didn't work. I actually decided to download Oneric, thinking I would eliminate the chance of something buggy in Precise. I am still having the same issues. I also replaced the SATA cable and used a different SATA port on the motherboard. Still the same problem. From what I can tell when I boot into a live usb my two partitions on the SSD won't stay mounted. If I open Nautilus I can see all of my drives. I can mount all of the HDDs and they will stay mounted. My SSD (both partitions) will show up one second and randomly not be detected the next. This happens whether they are mounted or not. Then they will pop back up a couple of seconds later.

Is there something I should have done with the SSD when I installed it that I am overlooking? Some kind of BIOS setting? FSTAB setting? Did I just get a bad SSD? :confused:

My guess right now would be a funky SSD. I would see about getting it exchanged.

---

### Post by Balthazar_Droid on 2012-04-24
> **isantop said:**
> My guess right now would be a funky SSD. I would see about getting it exchanged.

Will do. Thanks for the help.

BTW - I really dig your mock-ups for the indicator menus [http://omgubuntu.co.uk/2012/04/indicator-menus-re-imagined-unity-style/](http://omgubuntu.co.uk/2012/04/indicator-menus-re-imagined-unity-style/)

I hope it gets implemented!

---

