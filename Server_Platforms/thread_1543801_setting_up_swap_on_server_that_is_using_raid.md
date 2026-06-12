---
title: "setting up swap on server that is using raid"
date: 2010-08-01
forum: Server Platforms
---

### Post by realmrealm on 2010-08-01
**_Setup:_**
I'm in the process of setting up my very first ubuntu server.

Using 10.04 and has 2gb ram

I am using Ubuntu's software raid (mdadm)

It will be a file server, with 4 hard drives (3 in RAID5 and 1 as a spare)

All 4 drives have 2 partitions:
Partition 1 - 100mb
Partition 2 - The remaining drive space

I setup the first 3 drives' partition 1's to be RAID1 with the 4th drive's partition 1 as a spare. This is where I'm mounting "/boot" (it's my understanding that /boot cannot be on a RAID5)

I setup the first 3 drives' partition 2's to be RAID5 with the 4th drive's partition 2 as a spare. This its where I'm mounting "/"

**_Goal:_**
I believe so far I'm setup correctly to be able to deal with a drive failure and the system should operate just fine. What I don't know what to do is with the /swap. I want to retain the ability to be able to operate with a drive going down. But I have also read warnings about putting /swap on a raid.

**_Question:_**
How would you setup /swap?

-AndyS-

---

### Post by abix_adam_pl on 2010-08-01
You should prepare the place for swap before partitioning and making RAID.

So in my opinion the best would be to create 3 partitions on each hard drive, 1st and 2nd as you described and 3rd for SWAP. On the end just make mkswap /dev/sdX on each one disk and put in /etc/fstab lines for each one of them. 

You will have then SWAP 4 x each partition on disk. Should be enough.

Adam

---

### Post by realmrealm on 2010-08-02
> **abix_adam_pl said:**
> You should prepare the place for swap before partitioning and making RAID.

So in my opinion the best would be to create 3 partitions on each hard drive, 1st and 2nd as you described and 3rd for SWAP. On the end just make mkswap /dev/sdX on each one disk and put in /etc/fstab lines for each one of them. 

You will have then SWAP 4 x each partition on disk. Should be enough.

Adam

Thanks Adam,

I have to be honest I really don't know what you mean. But I am very good at learning, so I am going to research what you just said so that I can fully understand it and then I'll try it out.

-AndyS-

---

### Post by Xianath on 2010-08-03
Two questions on spreading out swap across multiple drives:
[LIST=1]
[*]How do you ensure it's load-balanced and not used sequentially?
[*]How do you configure it so that it boots with one disk down?
[/LIST]

---

### Post by realmrealm on 2010-08-03
> **Xianath said:**
> Two questions on spreading out swap across multiple drives:
[LIST=1]
[*]How do you ensure it's load-balanced and not used sequentially?
[*]How do you configure it so that it boots with one disk down?
[/LIST]

From what I have found out so far the answer to your first question is if you setup the "/etc/fstab" to look something like this:

```
/dev/sda2       swap           swap    defaults,pri=1   0 0
/dev/sdb2       swap           swap    defaults,pri=1   0 0
/dev/sdc2       swap           swap    defaults,pri=1   0 0
/dev/sdd2       swap           swap    defaults,pri=1   0 0
/dev/sde2       swap           swap    defaults,pri=1   0 0
/dev/sdf2       swap           swap    defaults,pri=1   0 0
/dev/sdg2       swap           swap    defaults,pri=1   0 0
```

that makes the swap partitions all the same priority, and allows *nix to actually stripe the swap across multiple partitions (if it chooses)

-------------
[COLOR="SlateGray"]not 100% sure about this answer:
[/COLOR]
as far as booting with one disk down I'm not sure yet, but I believe if it doesn't see a partition defined in "/etc/fstab" then it just uses the other ones. I believe it's like you saying "if you happen to see any of these partitions go ahead and use them for swap" so a disk going down would maybe require a reboot, but then the computer should be able to continue to operate.

[COLOR="SlateGray"]/not 100% sure about this answer
[/COLOR]
-AndyS-

---

### Post by LightningCrash on 2010-08-03
FYI: you'll need to do swapoff before pulling a failed drive on a hot-swap drive-replacement... or else the kernel will be very unhappy.

---

### Post by doogy2004 on 2010-08-04
I use a swap file that lives on my RAID 5 array.  It is listed on my fstab AFTER by raid array.

[https://help.ubuntu.com/community/SwapFaq#How do I add more swap?](https://help.ubuntu.com/community/SwapFaq#How do I add more swap?)

---

