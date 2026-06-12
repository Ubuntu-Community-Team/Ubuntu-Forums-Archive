---
title: "How is your HDD set up"
date: 2011-06-03
forum: The Cafe
---

### Post by vehemoth on 2011-06-03
I'm planning on doing a fresh install of linux over the next few days. How do you set up your drive Hardware/software RAID 0/1, GPT/MBR, dual boot, / and home, multi partitions or one large one.

---

### Post by Legendary_Bibo on 2011-06-03
Single HDD, no RAID, two partitions. One for Ubuntu, one for Windows.

---

### Post by Thewhistlingwind on 2011-06-03
Right now one drive, All ubuntu (For now) and one partition.

However, I think you should use a separate home partition and mount it at boot. Theres many benefits to this, but it should be easy enough to do that I don't need to explain them. (I'll be doing this on my next install.)

---

### Post by vehemoth on 2011-06-03
I used to have a software RAID0, grub on the mbr, just debian squeeze on a single partition home included but I don't know whether it was really worth it. I find linux fast enough and don't need 1tb (2 x 500gb), maybe this time I'll try RAID 1 but I don't know if you can duplicate the boot loader and all that to work as well.

---

### Post by TenPlus1 on 2011-06-03
120gb hard-drive (no raid), 20mb assigned to '/' and the rest to '/home', all works perfectly...

---

### Post by vehemoth on 2011-06-03
> **TenPlus1 said:**
> 120gb hard-drive (no raid), 20mb assigned to '/' and the rest to '/home', all works perfectly...

Do you mean 20gb or is that some really tiny distro that you're running?

---

### Post by Dustin2128 on 2011-06-03
> **vehemoth said:**
> Do you mean 20gb or is that some really tiny distro that you're running?
If it is megabytes, he's going to have some severe problems in about... now.

---

### Post by vehemoth on 2011-06-03
So which RAID set up is best for what.
I heard RAID 1 is better than RAID 0 for seek time, is that true.
Best thing about linux is you can afford to try every set up imaginable if you have the time.

---

### Post by BrokenKingpin on 2011-06-04
I just pick use the full disk on all my PC/Laptops as I store most of my files on my home server. The home server has a RAID 5 setup.

---

### Post by vehemoth on 2011-06-04
> **BrokenKingpin said:**
> I just pick use the full disk on all my PC/Laptops as I store most of my files on my home server. The home server has a RAID 5 setup.

What's your home server run?

---

### Post by wolfen69 on 2011-06-04
> **BrokenKingpin said:**
> I just pick use the full disk on all my PC/Laptops as I store most of my files on my home server. The home server has a RAID 5 setup.

You are smart. Sometimes. ;)  

Backup is the key to tech happiness. I never keep "important" stuff on my OS install. It stays on separate drives and partitions. (backed up twice) The only reason I like a huge /home partition, is so I can host many instances of virtualbox. 

Having your files in /home doesn't make them any easier to access. And if your hard drive dies, you're screwed.

---

### Post by TenPlus1 on 2011-07-25
> **vehemoth said:**
> Do you mean 20gb or is that some really tiny distro that you're running?

ahahaha yeah, meant 20gb :P

---

### Post by disabledaccount on 2011-07-25
> **vehemoth said:**
> Do you mean 20gb or is that some really tiny distro that you're running?:)
Just yesterday I've installed 10.04.2 on Medion MAM1250: Turion@1.8G/1GB RAM/ATI Radeon XPRESS 300M GFX/20GB Fujitsu HDD - works very very nice, even compiz effects are perfectly smooth (open drivers, no proprietary drivers available). HDD is splitted into 2 partitions: ~16GB for OS and 4GB for special data (invoice database) - laptop will be used in small shop.

My home desktop has mixed set of Raid partitions on 3xHDD 500GB, 2x HDD 80GB and 1 SSD 60GB - set of 6 drives gives wide field for experimenting :)

---

### Post by mips on 2011-07-25
> **tomazzi said:**
> HDD is **splitted** into 2 partitions...

Sorry but every time I see that I something happens to me, I will not elaborate more on what that something is.

There is no such word as 'splitted', it's just plain old 'split'.

Not aimed at you directly but I see it a lot on the net.

---

### Post by disabledaccount on 2011-07-25
...ok
As an excuse I can say that english is not my native language ;)

---

### Post by mips on 2011-07-25
> **tomazzi said:**
> ...ok
As an excuse I can say that english is not my native language ;)

No worries, you're English is pretty good. It's just I see so many people, native speakers included, using the word 'splitted' and it grates me at some low level :biggrin:

You have to excuse me, I'm just getting old and grumpy, apologies.

---

