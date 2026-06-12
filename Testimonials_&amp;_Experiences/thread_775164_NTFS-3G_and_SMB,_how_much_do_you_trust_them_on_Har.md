---
title: "NTFS-3G and SMB, how much do you trust them on Hardy?"
date: 2008-04-29
forum: Testimonials &amp; Experiences
---

### Post by ZeusABJ on 2008-04-29
I did not know where else to post this thread so I hope this is the right place:

I've been an avid user of Gutsy Gibbon at home since it came out last year. I currently work in the Oil Industry and the company I work for is a 100% Microsoft shop. To aid in interoperability I build a small Windows 2003 file server that I added to my home network. This server functions as a sort of "go-between" when I need to transfer files between my Windows laptop and my Ubuntu desktop. When I first deployed Gutsy last year I also installed a second hard drive formated to NTFS in my Ubuntu box to experiment with using NTFS-G to read and write an NTFS partition. 

With Gutsy my results were mixed. As long as I did not try to move large quantities of data around I seemed to be fine. It was when I tried to transfer my massive 160GB music collection that I ran into trouble which cryptic error messages and general stop events. Especially when I copied to or from an SMB share. Now that I've upgraded to Hardy I'm pleased to see copy operations seem much improved and faster in most cases. I'm particularly thrilled to no longer have to reboot X just to see my server shares when I happened to boot up the Windows server AFTER booting my Ubuntu box. However, my experience with Gutsy has left me a little concerned about interoperability.

When you look at solutions like SMB or NTFS-3G you're basically looking at an open source implementation of a technology that was reverse engineered from a proprietary technology right? In that scenario have to worry that maybe something was not totally reverse engineered correctly. What if I use one or both of these technologies to move some critical data between drives or across my network and it fails or corrupts my data simply because the software is buggy? I was just wondering if anyone else has experienced anything that gives them pause before attempting to use NTFS-3G or SMB to transfer files. Does anyone feel my my concerns are unfounded? So far Hardy seems to work like a pro, but maybe I've just been lucky so far. Has anyone had any bad experiences using these two technologies in Hardy yet? Would you be comfortable with the thought of moving a massive quantity of critical data between an ext3 Ubuntu partition and an NTFS partition? How about the same scenario with an Ubuntu machine and a Windows server?

---

### Post by hyper_ch on 2008-04-30
there's a huge difference between ntfs-3g and samba

With ntfs-3g linux takes active control on the according ntfs-drive and reads/writes to it.

With samba, you are just sending data over the network and let the operating system at the other end do the read/writing part.

while ntfs-3g works great, samba won't hurt the system at all as it does not directly take action.

---

### Post by armandh on 2008-04-30
network attached storage seems to work for most OS.
my NSLU2 is happy with XP and Ubuntu

---

### Post by Delever on 2008-04-30
Wow, I recently had to move huge amounts of data around (~500GB), that involved, let's see: from NTFS tp NTFS partition on different drives, from NTFS to ext3, from fat32 to NTFS, from ext3 to another PC with Hardy Beta, from NTFS to another PC with Windows XP, from NTFS to another PC with Vista. And then moving it all back :)

Just pray you don't have lockup. (i had to say that :D)

---

### Post by PmDematagoda on 2008-04-30
By the way, Samba won't need reverse engineering any more since Microsoft opened up the networking specifications, so there shouldn't be any worry of that.

---

### Post by szaka on 2008-04-30
> **ZeusABJ said:**
> With Gutsy my results were mixed. As long as I did not try to move large quantities of data around I seemed to be fine. It was when I tried to transfer my massive 160GB music collection that I ran into trouble which cryptic error messages and general stop events. Especially when I copied to or from an SMB share.

Ok, SMB is unrelated to NTFS-3G, so unfortunately I can't comment that. As for NTFS-3G, I can only suggest to use the latest stable release: [http://ntfs-3g.org/releases.html](http://ntfs-3g.org/releases.html)

> **ZeusABJ said:**
> 
However, my experience with Gutsy has left me a little concerned about interoperability.

Regards to NTFS-3G, Gutsy had an old release, version 1.913 or even earlier. Please see the above link about the changes. The latest version includes more new functionality and performance improvements and bug fixes.

> **ZeusABJ said:**
> 
When you look at solutions like SMB or NTFS-3G you're basically looking at an open source implementation of a technology that was reverse engineered from a proprietary technology right? In that scenario have to worry that maybe something was not totally reverse engineered correctly. 

This is computer science, not wooodooo ;-) A reverse engineered driver with the source code is a much more correct documentation than whatever amount of redundant paper could be which describes how the driver works in __theory__. 

In real life, all programmers (Microsoft ones included) make mistakes, so the driver sometimes misbehaves. These things are rarely documented, still it must be considered if one wants to interoperate reliably.

Any fault, if you find in NTFS-3G, would be an engineering error, not the lack of the documentation from Microsoft. We never blamed Microsoft not releasing the specification, only ourself when we made an implementation mistake. 

> **ZeusABJ said:**
> 
What if I use one or both of these technologies to move some critical data between drives or across my network and it fails or corrupts my data simply because the software is buggy? 

The most common reasons are not software but hardware related. For example it's explained here: [http://ntfs-3g.org/support.html#ioerror](http://ntfs-3g.org/support.html#ioerror)

In the past years we have also tracked down many faults in different part of the systems which were originally believed to be NTFS-3G problems but in fact they were not. A very partial list:

SELinux (several), ALSA, laptop hardware, partition, MBR, grub, qtparted, gparted, ide cable, bad memory, bad sector, Windows NTFS driver, CVS, getcwd, gnulib, samba, activesync, vmware, nautilus, LTP, dbench, ntfsmount, wifi/nvidia drivers, rdiff-backup, chkdsk, slow disk (dma, bad sector, low-speed USB), metalog, slow boot, firefox, squasfs file manager drag-srp crash, network-manager (unmount/mount), mdadm --create, captive-ntfs, amarok (amarokcollectionscanner high memory usage), kernel (several), ext3 (kernel panic in dx_probe, ext3 always unreliable dir_index feature), encfs, wine, thunderbird, gcc, visible CPU usage (being in user space), Windows (can't boot if disk is full: [http://support.microsoft.com/kb/291808](http://support.microsoft.com/kb/291808)) EVMS (device busy: [https://bugs.launchpad.net/bugs/115616](https://bugs.launchpad.net/bugs/115616))

Regards, Szaka

---

### Post by ZeusABJ on 2008-04-30
> **PmDematagoda said:**
> By the way, Samba won't need reverse engineering any more since Microsoft opened up the networking specifications, so there shouldn't be any worry of that.

Very good point, and that really puts my mind at ease.

---

### Post by ZeusABJ on 2008-04-30
WOW!!!!

I was just fishing for some feedback from other users on their experiences using these two technologies to talk to windows machines and NTFS formated drives. I never expected to get a reply from one of the lead developers on the NTFS-3G project!!! First off, let me thank you Szaka so much for even taking the time to respond to my post. On the surface I know it may have seemed like I was bad mouthing NTFS-3G, but I assure you that was not my intention. I just wanted to know what sort of experiences (good, bad, etc) other users were having when using NTFS-3G to transfer large quantities of data between NTFS and EXT3 formatted drives. As I said, I noticed that NTFS-3G seems to work so much better in Hardy than it did in Gutsy. I just wanted to know if anyone else noticed significant improvements and if they felt it was at a point where they would be comfortable using it to move the aforementioned massive quantities of critical data.

You'll have to forgive my geeky fanboy nature, but now I have to take a moment here to shamelessly praise you and the entire NTFS-3G team for your hard work. I can't imagine what a daunting task it must have been to make this work. I'm just so thrilled that there are people out there like you guys that are dedicated to free use and work so hard to create tools like this to help liberate us from our Windows world. I keep the latest Ubuntu Live CD in my toolkit at work and have used NTFS-3G countless times to mount windows drives and recover data from them when all other tools failed. Your contribution has saved me a tremendous amount of time and energy and I'm just so grateful for everything you have done. I am truly humbled that after all of that you would still find time to respond to my post. 

Thank you so very much for your contributions.

---

