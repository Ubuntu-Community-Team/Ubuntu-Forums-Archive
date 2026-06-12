---
title: "Ubuntu on a HP DL360 G5"
date: 2006-09-27
forum: Server Platforms
---

### Post by stakk on 2006-09-27
Hi all,

I just got a new HP DL360 G5 with a Smart Array P400i Controller for its SCSI disks.

I tried to install 6.06, but the setup freezes after language selection. So I downloaded a daily image from edgy, and that took me up to the formatting and mounting of the disk.

The selectable filesystems are only XFS, FAT16/32 and swap (and some other standard stuff), I miss ext3.
So I think it was not completely recognized...

However I then tried to use XFS, after setting up everything I wanted to write it to the disk - I'm not sure if that worked, the installer sais "Mounting of the disks failed".

I don't know what Kernel version edgy works with, but I think I found that the controller in this server is supported as of 2.6.18.

So any suggestions how I can get Ubuntu on that server?
I know there is something like deboostrap, but I never did that and I think I even need one Linux (Live) System that finds the disks...

Any suggestions? 
I wouldn't really mind using Debian, but the Sarge installer wasn't even able to mount the install CD.

So thank you guys for any answer!
stephan

---

### Post by kruppa on 2006-10-12
Same here, I also noticed the USB devices keep getting discovered, a couple of times a second, resulting is a lot of /dev references, when you start up the Ubuntu 6.06 live CD. NIC doesn't work either, aren't even discovered (on Knoppix 5.0.1 DVD the NIC's are discovered as Broadcom Netxtreme II 5708 whilst they are HP NC373i's, could be that it's the same chipset off-course).

I asume the solution would be booting live with a 2.6.18 kernel and than - as you suggested - debootstrapping.
Question know is which distro has live boot with the 2.6.18 kernel? I'm affraid it's a bit too early to assume there's one, not?

Peter

---

### Post by stakk on 2006-10-13
Well... I had to finish that server soon I tried to install openSuSE 10.1.

And it worked like a charm... with Kernel 2.6.16!
Maybe there are other drivers. I don't know, and I didn_t have the time to go further into this.

Sorry I can't help you.

---

### Post by kruppa on 2006-10-14
Thanks for the input stakk.

I tried Kanotix beta with kernel 2.6.18 without luck (it didn't even started up - dev problems) and then tried Ubuntu server 6.10 beta.

I know beta's aren't the way, but hey, than again I've been running Debian unstable for ages now.
And furthermore in a week of two maximum it will be released.

Anyway good news, disks were found correctly while installing, nic's weren't, but after booting in the new system even those nic's are found.

Running kernel is 2.6.17.

Peter

---

### Post by eseixas on 2006-12-09
Hello,

You should have to install in advanced mode and skip the keyboard configuration.

You won't be able to detect the network adapater, but after the first boot, the network will detect.:-D

---

