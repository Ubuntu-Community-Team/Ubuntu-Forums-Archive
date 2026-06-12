---
title: "VirtualBox Windows guest insanely slow."
date: 2016-07-28
forum: Virtualisation
---

### Post by 1clue on 2016-07-28
Hi.

Host: i7 920 (1st gen i7) 24g ram, plenty of disk, desktop system. Ubuntu 15.10. Mix of SSD, spinner and raid1 on spinners. I don't have any trouble with my disks.

VirtualBox guest: Windows 7, 4g ram, 100g disk.

I've been trying to run the upgrade to Windows 10 for a week or so now.  It starts out slow but workable, and then rapidly slows down. Today it got to about 8% fairly quickly, then significantly slower to 12, then extremely slow up to 15%.  Measured time sitting at 15% was 3 hours 17 minutes before the upgrade app crashed.

During this time, the Linux system performs normally and the Windows guest is extremely sluggish.  Click start menu, wait a few minutes, menu shows up. Click an item, probably the app doesn't even start. Start task manager, wait 5 minutes (measured!) and it shows up. Open control panel, not including the menu operation, took 10 minutes while the system was at 15% upgraded.

My Linux system monitor shows VirtualBox taking no more than 3% cpu. My Windows task manager shows everything idle.

My VBox.log: [http://paste.ubuntu.com/21325541/](http://paste.ubuntu.com/21325541/)

---

### Post by TheFu on 2016-07-29
15.10 support ended yesterday. Move to 16.04 or back to 14.04.

For slow virtualbox, follow this guide: [http://blog.jdpfu.com/slowVbox](http://blog.jdpfu.com/slowVbox) Should be able to get 90-95% of native performance. It is for older versions of vbox, but I know people running the latest versions are getting good performance following it still.

---

### Post by kyrithis on 2016-07-29
I'm having trouble determining a problem at this moment, but for now while I go over the log, check in your Vbox settings. Confirm your execution cap is set to the highest you can set it (Without Vbox complaining about optimal settings anyway), make sure it's using all of your cores/CPUs, and let us know if that changes anything (assuming it wasn't already set properly).

---

### Post by 1clue on 2016-07-29
I upgraded to 16.04. My disk is no longer readable. I restored the backup and cloned it, but it's in vdi sparse and the docs TheFu pointed at strongly recommend not using sparse.

The disk file is 500g with 100g as C. Nothing else on it yet.  Can I somehow move this C partition to a smaller non-sparse vdi image, and switch?

I'd also like to get virtio disk driver involved too.

Thanks.

---

### Post by 1clue on 2016-07-29
Since I've upgraded to 16.04 I've had 4 hard freezes.  Not just the window manager, but I can't switch to a virtual terminal, and the system can no longer be pinged from another computer.

It's been years since this happened to me, even  compiling my own kernels is better than this.

---

### Post by 1clue on 2016-07-29
Hi,

Just upgraded from 15.10 to 16.04 today.

I've had 4 hard crashes since upgrading.  I haven't had a kernel panic for years, even compiling my own kernels.

This doesn't go to a black screen, everything just freezes.  No mouse, no keyboard, no screen activity, can't switch to a virtual terminal (Just checked, the key combo still works when the system is up) and can't ping from another box to this one's static IP, Host is down. NMap fails as well.

I really need this to stop.  Can somebody give me an idea what might be happening?  I can't find the word 'panic' in any file in the /var/log heirachy. Not sure where a  core file would be.

Please help.

---

### Post by TheFu on 2016-07-29
vboxmanage will convert disk image types.
Or you can manually create an image disk file sized the way you want, boot off alternate media and use dd/ddrescue/rsync/ or whatever backup/restore tool you always use to move the data from old.vdi to new.img.  Ah ... it is Windows ... can't recommend anything, sorry.

No real need to use virtio for network/disk in Windows. I'm using it, but it was more hassle than it was worth. The e1000 NIC driver and SATA disk driver are fine.

I haven't seen the stability issues you mention with 16.04, but only have it running on 1 system. Most servers are running 14.04 or stable debian here. Perhaps in the fall, I'll move a few to 16.04. No hurry.   OTOH, the push to integrate systemd has left me concerned.  I think it needed 2+ more years to stew before it would be ready for production, but Debian stable put it into their distro, so it can't be all bad.

Lastly, I stopped using virtualbox years ago. Switched to KVM/libvirt for all my VM needs beginning in 2010 and finally finished the migration around 2012. Never regretted that decision. Not once. Stability has been rock solid. No issues, except the migration of a Windows VM from the 2010 LTS to the 14.04 LTS VM.  Seems the motherboard presented to Windows had changed, so I ended up using a migration tool so all my program data wouldn't be lost. I was working from a retail version of Win7 and don't plan to migrate it again until 2019-ish. ;)

My recent virtualbox knowledge comes from weekly LUG meetings and installfests that we have in the area.

---

### Post by 1clue on 2016-07-29
I created a new disk with fixed size which is big enough to hold both partitions and used a Windows cloning app to copy the relevant partitions. It's done.  I couldn't get virtio-blk to work at all.  In the interest of speed (I have about 10 hours left to do the upgrade) I just smashed it in there and it's working.

I don't want to move backward in the upgrade process, so I went to 16.04.  This is a desktop box, my development workstation.  I'm not a systemd fan at all, and even less a fan of the guy whose initials are L.P. who is involved in its design. Do Not Want to Start Something Here, so I won't say his whole name.

I've never really used VirtualBox.  I started because my teammates all insist on it as a common ground.  I'd much rather use QEMU with KVM as a backend. IMO VirtualBox is a waste of time. I'm doing it because the people who pay me want me to use it.

---

### Post by 1clue on 2016-07-29
Oh yeah, it's now 5 times that my system has locked up tight since my upgrade this morning.

---

### Post by 1clue on 2016-07-29
6 times.

---

### Post by TheFu on 2016-07-29
16.10?  Why. Why?  Why!  Stay with LTS.  Please try to teach them this.  Do non-LTS stuff inside VMs, if you must.

VirtualBox isn't a waste of time for most people.  For desktop-on-desktop people, it is the least evil choice for Windows users.  BTW, they probably need to read the ToS and license agreement. Oracle expects to be paid if people use virtualbox in a business.  The license is different for the "guest additions" - not OSS at all last time I checked.

---

### Post by kyrithis on 2016-07-29
This external topic seems relevant, the symptoms appear to match yours.

[http://askubuntu.com/questions/761706/ubuntu-15-10-and-16-04-keep-freezing-randomly](http://askubuntu.com/questions/761706/ubuntu-15-10-and-16-04-keep-freezing-randomly)

Good luck, I will be standing by with more if needed. Research is my strong suit :D

---

### Post by 1clue on 2016-07-29
Another crash.  Looking at your page, reduced cores available to cpu on vm to ensure one is available to my linux box.  VM is much slower now.

I'm running Ubuntu as host, virtualbox image is Windows, trying desperately to upgrade to Win10 before the time is up.

---

### Post by 1clue on 2016-07-29
I appear to have some sort of video driver wierdness, not the same as on that page since I have different hardware.  Couldn't even open my control panel.

I paused/saved the VM state and manually updated my video drivers and firmware. Rebooted, now my control panel opens up at any rate, and I can configure screens.

I started the vm again, it seem to be going moderately faster than last time but still not as fast as with 4 cores enabled.

I hope this is the end of it.

Thanks.  Please check back later as I may have more wierdness.

---

### Post by kyrithis on 2016-07-29
Of course. I'm subscribed to the thread, so I'll see any posts made in it. Hope it's all good, good luck.

---

### Post by 1clue on 2016-07-29
sorry that was a typo.  It's 16.04

---

### Post by 1clue on 2016-07-29
We (both me, and the company I work with) are well aware of the  relationship of various Open Source licenses and their interactions with  commercial software. We know about the VirtualBox for business terms. The Powers That Be have Written the Law. The Law Says that VirtualBox is the Virtualization Engine of Choice.  The Law Sucks. The company is not averse to paying for a per-seat license, or they wouldn't be doing Windows images in the first place.

For that matter, I'm more than willing to pay money of my own for software as long as I see personal value in it that justifies its use. VirtualBox is not one of those things, therefore I'm billing those other guys for it.

I have, however, and will again, pay for software on Linux for my personal use. [https://www.sublimetext.com/3](https://www.sublimetext.com/3) comes highly recommended by me, and I'm looking at a license for [https://www.jetbrains.com/idea/buy/#edition=commercial](https://www.jetbrains.com/idea/buy/#edition=commercial) as well.

---

### Post by 1clue on 2016-07-29
Halleluja!

I upgraded to win10 before the deadline.

I hope everyone else got theirs done too.

Question: I saved the machine state and made a snapshot before I rebooted my system for video driver fixes. I'm not stuck with staying on that snapshot am I?

---

### Post by cariboo on 2016-07-29
Merged two threads on the same topic.

---

