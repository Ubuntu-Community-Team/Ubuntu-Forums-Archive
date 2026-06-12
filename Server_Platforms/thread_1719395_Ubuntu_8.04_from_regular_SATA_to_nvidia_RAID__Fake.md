---
title: "Ubuntu 8.04 from regular SATA to nvidia RAID / FakeRAID"
date: 2011-04-01
forum: Server Platforms
---

### Post by lightninhopkins on 2011-04-01
I had Ubuntu 8.04 installed on server#1 and moved it to server#2. Everything works fine, including the changing of eth2/3 back to eth0/1.

I was wondering if it's possible to use the nvidia onboard raid and make a raid 1 with this OS not getting wiped out. It's a bios level cheesy raid and it warns that it's erasing the data (which is didn't erase), but wont boot anyway. 

I'm assuming it's probably best to just create a software raid in the working OS with a fresh 2nd drive. 

update: just discovered dmraid. cool stuff.

---

### Post by Vegan on 2011-04-01
Stay away from software RAID.

The NVRAID is OK but you have to erase the disks to create a new array.

Also watch the 2 TB MBR limit.

---

### Post by lightninhopkins on 2011-04-05
Thanks for your advice. Yup, I tried the /md0 creation using /sda and /sdb then rsyncing, but it became a nightmare getting it to boot (I have no more patience to learn). 

Just going to set up a new mirror with an Areca card and copy over the old OS.

I've been building high-end storage servers for over 10 years, and have built tons of 48 drive raid arrays, but this transition from a single standalone drive to a raid wasn't as easy as I thought.

---

