---
title: "never seen memory upgrade locks 10.10 raid"
date: 2011-12-15
forum: Server Platforms
---

### Post by michaeljeshurun on 2011-12-15
I'm running a fakeraid 1 of Ubuntu 10.10, which will erased and become a webserver with a fresh install in six months hopefully.  It's been working fine with 2Gb of memory, but I decided to  upgrade to 4Gb.  The bios shows all the new memory being found, I can start into a CD, but the computer locks up with a blinking prompt when I try to boot to the OS. 
The boot order is fine, and I've tried enabling and disabling memory remapping in the BIOS.  

A search online brought up nothing, and also I couldn't find anything like this reported anywhere in the forums here either.  Although I haven't tried this time, from experience when I remove the additional memory, the computer goes back to booting perfectly.  

I installed this with the 2Gb but I've pillaged memory from other computers before, and had this problem.  This time I went and purchased exactly the same memory from the same manufacturer hoping that would solve this issue.  The motherboard is an Asus P5QL-epu, the disks are name brand Sata 100GB 7200K, with loads of room left, using three partitions, one swap, one boot, and one home.

I don't want to reinstall from scratch until I've finished purchasing a few more disks and changed the fakeraid level completely, and that's at least six months away.

---

### Post by ian dobson on 2011-12-16
Hi,

Are you sure your memory is OK? (run memtest).
Are the new and old memory modules exactly the same? Maybe try swapping the order of the modules around.

Your new memory could be OK, but if the BIOS configures the memory access timing based on the values used for the OLD modules for all modules and your new modules need a different timing then things could blow up.

Regards
Ian Dobson

---

### Post by ian dobson on 2011-12-16
Hi,

Oh and before I forget, get rid of fakeraid (it's just a hack to be compatible with windows raid systems) and use a real raid system designed for linux (mdadm).

I've been using mdadm on my big video server (8 x 2Tb drives split over 3 raid arrays) for almost 3 years now without any problems (Appart from drives dying, but thats normal).

Regards
Ian Dobson

---

### Post by michaeljeshurun on 2011-12-16
Thanks Ian,

I'm sure the memory sticks are exactly the same all registering fine, from Kingston, marked very well, with the same timing.

I might have goofed when I said fake raid. I created the raid with the Ubuntu alternate installer CD, and I think it's manageable with mdadm.  It's run extremely solid and acting as a good model until I wipe the disks and get a server edition installed.  I'm recalling fakeraids are the hardware side?

Sounds like you have a very impressive setup.  I recently got a tour of MIT's (Massachusetts Institute of Tech.) video servers here in Boston, and if my recollection is right, they've had video open classrooms since dawn.  They might have been the very first.  It was an eye opener.

---

### Post by ian dobson on 2011-12-16
Hi,

Fake RAID is just that. It's just a combination of BIOS and driver with a minimum amount of hardware.

Still try running memtest and maybe try swapping the order of the modules. Also what happens if you only install the new modules?

Do you have the RAID options disabled in the BIOS?

My backend server not that bad (Intel 2600,16Gb ram, RAID5 array for video files). I installed MythTV about 3years ago and since then my harddisk requirements has doubled almost every year. So this year I just went mad with buying harddisks.

Regards
Ian Dobson

---

### Post by michaeljeshurun on 2011-12-16
When I went with your suggestion to only use the new modules, the OS started right up.  I put the old modules in the other slots, or any time I have more than the original 2GB of memory, the computer locks after posting.

This mb has no RAID settings onboard or in the Bios.

I'm going to leave the computer running tonight if I can get to sleep, or tomorrow all day and see if this is a long sync problem.

I might give up after that and leave it dormant until I've bought the disks for the RAID I'm planning, and just start from scratch.

---

### Post by ian dobson on 2011-12-17
> **michaeljeshurun said:**
> When I went with your suggestion to only use the new modules, the OS started right up.  I put the old modules in the other slots, or any time I have more than the original 2GB of memory, the computer locks after posting.

This mb has no RAID settings onboard or in the Bios.

I'm going to leave the computer running tonight if I can get to sleep, or tomorrow all day and see if this is a long sync problem.

I might give up after that and leave it dormant until I've bought the disks for the RAID I'm planning, and just start from scratch.

Then it could well be a bios bug. Try updating the BIOS to the newest version.

Regards
Ian Dobson

---

### Post by michaeljeshurun on 2011-12-17
The BIOS is up to date.

Last night I switched three settings, just to see if the jolt would wake up the raid.  They were 1) plug and play from yes to no, 2)Enable of ACPI 2.0 support, and 3) Enable of Memory Remap Feature.  I got as far as seeing the desktop, but without the panel bar or bottom bar, and the OS startup got stuck again.  I left it on at that stage for over an hour.  I should have had ACPI 2.0 support on during installation, since my OS is 64-bit.

I did get to sleep with the machine on, too, but no improvement.

The install disk still boots fine.  I'm totally frustrated.

---

### Post by ian dobson on 2011-12-18
Hi,

Does the system boot OK with only 3 modules installed?

Also can you try editing the kernel command line parameter (in grub menu press e for edit ) and remove the quiet option. This should cause the kernel to dump alot of debug info to the screen. Maybe then we can see where it's dying.

Regards
Ian Dobson

---

### Post by michaeljeshurun on 2011-12-18
It wouldn't boot with three sticks of memory either.

I decided to unplug the raid disks and try some start up CDs with the empty ones, and started finding a lot of flakiness a lot of the time.  Then I tried re-flashing the memory.  As I was looking at related articles at Asus I came across the easy answer.  I reset the CMOS jumper and things are running smooth again.  I don't know why flashing didn't work and the jumper did, but I know which to try first next time, if there is a next time.

That proves you were right at every turn, suggesting BIOS problems.  Thanks very much.  

In between, I'd one by one taken out the empty raid cards, replaced the graphics card, and finally, the wireless card came out too.  What a waste of a day to find out the reset jumper was seemingly the only repair necessary.  At least the U.S. football game was an exciting one.

---

### Post by ian dobson on 2011-12-18
Hi,

Glad to see the problem is solved. Maybe mark the thread as such.

Regards
Ian Dobson

---

