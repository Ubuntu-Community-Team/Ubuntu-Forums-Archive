---
title: "Help a novice get past &quot;error: invalid arch independent ELF magic.&quot;?"
date: 2011-01-30
forum: Server Platforms
---

### Post by HeroKid on 2011-01-30
Ok I'm new to Linux in general and as a result I'm still learning the ropes of Ubuntu Server. I had an old Mac Mini set up with Ubuntu Server which I use as a home seedbox. However yesterday I did a "sudo reboot" via ssh and the server hasn't been able to boot since. 

To my knowledge I didn't update anything, there is no windows partition on the drive (never has been) so I don't know what is going on. I'd like to not have to reinstall everything just to get it working again but I can if I have too (files are on an external, would just loose system settings). 

Here is the message I get when I try and boot:
> error: invalid arch independent ELF magic.
grub rescue>_

When I try and reinstall grub using recovery mode from on the disc, I get "error code 1". So that hasn't been much help either. 

Before you flame me for not searching, I did. But because I don't really understand the jargon - the solutions may as well have been written in Chinese. So please go easy on me.

---

### Post by HeroKid on 2011-01-30
Bump? I'd really like to be able to get this sorted as quickly as possible. Any help would be greatly appreciated! :/

---

### Post by HeroKid on 2011-01-30
Stuff it. I'll just start again. :x

---

### Post by kysersoze on 2011-07-13
Hi Guys,
            I'm having a simmilar issue with my current setup. Server was functioning fine and then power went out a couple of days ago and now it wont boot.
 
basic setup 5x 1tb SATA hard drives in software RAID 5 with 3 LV's /os /home /swap
 
the original issue was this
[https://help.ubuntu.com/community/Grub2#File%20Not%20Found%20(Error%2015]("https://help.ubuntu.com/community/Grub2#File%20Not%20Found%20%28Error%2015"))
 
Grub file not found
 
Encountered another issue that a live usb will not mount my raid array once desktop is loaded. not all devices available to mount. this turned out to be the onboard 6 port sata controller being 1 4x port and 1 2x port with a PATA port. Live dvd has the same issue. A server install disk with rescue option does not have any issues in finding and mounting the lvm on raid but the commands on the link above dont work.(
 
After much toiling i gave up and decided to run a fresh installation of 11.04 64bit server (same as previous install) on the /os lv 
 
Basicly I came up with the same issue.
 
After much fooling around trying to do a repair I found an article (can't find it now) that said the issue is that 11.04 64 uses GUID partition tables instead of MBR. and that it would not be a problem on earlier installations of Ubuntu server.
So I installed 10.04.2 LTS 64
 
Also point to make is i have run memtest on the ram and the drives are all fine
 
Now I have the problem
error: invalid arch independent ELF magic
grub rescue> _
 
The thing is this ........ 
my /home on lvm2 is encrypted and I think now that that is the issue stopping the system to boot.
 
All that really matters to me is getting my data out from the /home and then I can start from scratch, the rest really doesn't matter.
 
But fixing the issue to save me from re-installing again would be nice ;)
 
Thanks all,
Kyser

Edit:

I have done a Wubi install of Ubuntu 11.04 on my main system (i7) setup  the system with the same User name and password plugged the drives in. A  quick

sudo apt-get update && sudo apt-get install lvm2 mdadm

and I was able to mount the volume in a degraded state (should of  realized that it dropped a drive earlier) with Disk Utility , mounted  the lv and then mounted the partition. 

As far as the encryption goes it must of passed straight through due to  the same user-name and password as I am currently coping over 2tb of my  families movies happily.

Once I have everything up and running again ill just nuke the array and start again fresh.... with a ups.

---

