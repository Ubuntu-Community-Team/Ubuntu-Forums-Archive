---
title: "Problems installing Ubuntu Server on RAID"
date: 2009-05-08
forum: Server Platforms
---

### Post by distance42 on 2009-05-08
Hi everyone,
I've been trying to get Ubuntu Server to run on my new machine for three days now and I'm really stuck.

The machine:
AMD Athlon 64 X2 5050E
Gigabyte GA-MA78GM-US2H Mainboard
2x 1GB RAM PC800
2x Samsung HD-103UI 1TB HDD
LG GSA-H22N DVD

The goal:
I want to use this as a home server, providing a fairly secure (RAID-1ed) location for backups and things like photos, MP3 and for openVPN.

What I did:
I just got the machine from my dealer and started out enabling RAID in the BIOS. In the additional RAID-BIOS, I set up the two HDDs to work together as an array, which seemed to work just fine. After a bit of fiddling with the options in the Ubuntu-Setup, I got it to work and already did some configuration of the system.
When I rebooted for the first time, the RAID-check told me something about "critical", but the system booted okay. When I rebooted for a second time, it stopped, and I found the RAID-Configuration to have changed: Instead of one array with two disks, I had TWO arrays of two disks each, where in each array, one disk was missing and producing the "critcal"-message.
But this, unfortunately, is not the actual problem. At this point, I thought I just had made some mistake during the installation and wanted to retry, so I corrected the RAID-config and started again. But now, the Ubuntu-setup started to do strange things: It didn't detect the RAID-array, but rather one of the single drives I previously configured as the array. Without changing anything (I just checked the RAID-config was correct), the next time I started the setup, it displayed no HDD at all. I tried again several times and got almost all of the possible results (no disk, one of the real disks, both the real disks and the raid-array). When I finally got the raid-array, I tried to partition it, but the setup got stuck with a kernel panic. The same happened with my Knoppix-LiveCD and my GPartEd-LiveCD. In the following, I tried several other things (dis- and then reenabling the RAID, formatting the drives on their own and then putting them back to RAID-mode etc.), but now I only get to see the empty drive-list in the Ubuntu-Setup. So when it promts me for the partitioning, the list of drives is just empty and I can't do anything about it. One step before (detect HDDs), the setup finds the RAID and asks me whether to use it or not. I usually answer "yes", but even if not, it doesn't make any difference.

Now, I'm completely lost and I don't have a single idea what to do more as, like said above, the setup worked just fine when I ran it for the first time. Any ideas would be highly appreciated.

Thanks in advance
Manuel

---

### Post by brendan.lefoll on 2009-05-08
Raid on the BIOS - ie fakeraid sucks.

The problem with fakeraid is just that it is not at all comparable to real hardware raid which has advantages - mainly in speed and supported interfaces.

I cant really be bothered to go in all the details, look it up, but for a simple raid1 it is absolutely the better solution compared to onboard cheap desktop motherboard raid. 

What you want to do is use softraid. One that'll sort all yuor problems out, and two it'll work so much better. It'll be faster and easier to manage. Just use the Ubuntu alternate disk and off you go.

Just found out a page that will explain things nicely

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

It starts off saying fakeraid is not supported.

---

### Post by distance42 on 2009-05-08
Thanks brendan,

this makes several things clear to me. Looks like I've been misadvised by my dealer, as I explicitly asked if there were any real disadvantages of what I now know is fakeraid and they said no. Great. :mad:

Anyway, if I wanted to buy a real hardware-controller instead of using softraid (I don't actually, but I would like to know), is there any way to see if it is a "real" raid-controller that I have before me?

Thanks again for enlightening me ;)
Manuel

---

