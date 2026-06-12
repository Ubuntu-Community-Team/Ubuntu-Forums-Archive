---
title: "Do I need a swap partition?"
date: 2014-04-04
forum: Ubuntu, Linux and OS Chat
---

### Post by Lancro on 2014-04-04
This is at least curious, I thought that linux needed a swap partition, but in the last install I forgot to create one, the installation continued, and my system runs smoothly, I have 16 GB of ram, so I think it wont use it ever, but Im no expert in linux, so I dont know if at upgrading the system, for example, I will need it, or not, my ubuntu is working with a partition for / and another for /home, nothing else, so thats my question, do I need to make room for a swap partition with gparted using the live usb?, in that case, what size?, 16GB its too much, I have it installed on a 256GB SSD, so free space matters, and I dont want to create a useless partition, what do you think?.

Thanks.

---

### Post by David D. on 2014-04-04
With 16GB of RAM, you will not likely use swap during normal operations, as you have already found.

If you ever plan to hibernate, you will need a swap partition as this is where the contents of RAM is stored.  This is why a swap at least the size of RAM is recommended.

---

### Post by TheFu on 2014-04-04
NEED?  No.
Is it a REALLY, REALLY, good idea? Probably. Hard to know.  It completely depends on the workload.

I do run many servers without any swap - the workloads are known and understood. RAM allocations are setup to be adequate for the workload.  On a desktop, don't think I'd ever set one up without swap.  Swap has purpose, it lets us know when we are getting low on RAM by having the entire machine get slower.  Without swap, things just refuse to launch.  Ran out of RAM yesterday on a netbook - took me about 15 minutes to realize the issue.  Even after I freed RAM, no knew processes would launch. Only a reboot solved that.  I really need to setup some swap. seriously.  BTW, this is running chubuntu with a default config - so I never had a chance to setup swap during the auto-install.

---

### Post by Lancro on 2014-04-04
If I decide to set up a swap partition of 16 GB, is as easy as puting there a swap partition, does ubuntu autodetects it?, or do I have to execute something to set up it as a swap partition?.


Edit: Ok Ive googled it, forget it ;).

Thanks.

---

### Post by monkeybrain20122 on 2014-04-05
If you have a laptop and use suspend/hibernate then you need it.

---

### Post by help_me2 on 2014-04-05
> **monkeybrain20122 said:**
> If you have a laptop and use suspend/hibernate then you need it.
Not true about suspend. I don't have swap and suspend works just fine. I don't use hibernate, so I don't know about that.

---

### Post by QIII on 2014-04-05
"Suspend" preserves the state of the memory *in situ *by making sure a small amount of current is delivered to the memory modules despite the fact that the computer seems like it is turned off.  Suspend will eventually run down your battery on a laptop.

"Hibernate", which some call "suspend to disk", physically copies the contents of the memory to disk and then fully shuts down the computer.  To be sure that everything in memory can be preserved, the space on the disk reserved for that task should equal the size of the memory, which is why the swap partition should be at least the size of the memory.  I say give it an extra 10% for safety.  If you have a small amount of memory, say <= 2GB, and swappiness is high, it wouldn't hurt to go with a swap partition double the size of the memory.

Windows dynamically adjusts the amount of disk space available to hold the state of the memory when you hibernate.  Linux does not.

---

### Post by anaconda on 2014-04-06
You have so much memory, that I don't think you would really need a swap partition.

And since you have already partitioned your HD it is too much work.

If I was you I would make a 1-2GB Swapfile, which works just as well as a swap-partition, except that hibernate wont work as well on it. (Needs tweaking) And then you would have to make a 16GB Swap file (or partition) which would be just too big.
Advantage of swapfile is that if you later need the space on your HD you can just delete the swapfile 

And I read that someone tried the hibernate on his laptop with a SSD and resuming from hibernate wasn't much faster than shutdown/restarting the machine. So not much point in hibernate for you....

---

### Post by monkeybrain20122 on 2014-04-06
> **anaconda said:**
> 

And I read that someone tried the hibernate on his laptop with a SSD and resuming from hibernate wasn't much faster than shutdown/restarting the machine. So not much point in hibernate for you....

Hibernation is never about speed, it is about wanting to preserve your session.  Reboot is always a lot faster, SSD or no SSD. But you lose your session upon reboot so that misses the point.

Waking up from suspension is fast and it restores sessions but as Qill pointed out it drains your battery, even though slowly.

---

### Post by mastablasta on 2014-04-07
> **monkeybrain20122 said:**
> Hibernation is never about speed, it is about wanting to preserve your session. Reboot is always a lot faster, SSD or no SSD. But you lose your session upon reboot so that misses the point.
.


in KDE the session is stored on reboot by default setting ;-)

---

### Post by monkeybrain20122 on 2014-04-07
> **mastablasta said:**
> in KDE the session is stored on reboot by default setting ;-)

I know, but I don't like saving session by default. And to add to that, in xfce it is almost impossible to make it not to save session! I consider it a handicap to not be able to save sessions in gnome (hence unity)

---

### Post by philinux on 2014-04-07
OP not posted for two days.
For others finding this thread see link below.
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by thevypr on 2014-04-07
Swap is only necessary if you have low amounts of RAM (<4GB), I'm not using a swap partition and I have 6GB of RAM.

---

