---
title: "Fresh install with btrfs, full encryption"
date: 2017-04-08
forum: Ubuntu Development Version
---

### Post by izznogooood on 2017-04-08
Is this possible in an easy way?

---

### Post by ventrical on 2017-04-08
> **izznogooood said:**
> Is this possible in an easy way?

Good luck , have fun! :)

Not easy.

Works for a while then breaks.

---

### Post by izznogooood on 2017-04-08
Well, thank you for that insightful  knowledge :). Anyone else?

---

### Post by grahammechanical on 2017-04-08
> As of 11.04, it is possible to use only btrfs file systems with the caveat that grub **'MUST NOT**' be installed to the boot sector of the btrfs volume containing /boot.  See also [Ubuntu Grub2 Bug 757446]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/757446") and [Ubuntu Grub2 Bug 759772]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/759772"). You must install it to either the parent (sda rather than sda1; MBR/Reserved Sectors) **'OR**' use a dedicated /boot partition as described in the forum post below. 


When  installing Ubuntu in one large btrfs-Partition without an extra  boot-partition, take care to keep about 1 Mib space free at the  beginning of the disk. This is possible using the partition manager in  the Ubuntu installer. When there is not this space, the installer fails  at the end when trying to install Grub!

[https://help.ubuntu.com/community/btrfs](https://help.ubuntu.com/community/btrfs)

I will +1 to that 1MB free space at the front of the drive. The last time I tested BTRFS it lacked a snapshot management utilty but if we install something called apt-snapshot that utility will create a snapshot  every time you update. Also Friendly recovery will give you an apt-snapshot - revert to old snapshot & reboot option.

Regards

---

### Post by ventrical on 2017-04-08
> **grahammechanical said:**
> [https://help.ubuntu.com/community/btrfs](https://help.ubuntu.com/community/btrfs)

I will +1 to that 1MB free space at the front of the drive. The last time I tested BTRFS it lacked a snapshot management utilty but if we install something called apt-snapshot that utility will create a snapshot  every time you update. Also Friendly recovery will give you an apt-snapshot - revert to old snapshot & reboot option.

Regards

Hey .. thanks for pulling up the slack :)

Regards..

---

### Post by ventrical on 2017-04-08
> **izznogooood said:**
> Well, thank you for that insightful  knowledge :). Anyone else?

My apologies. I wasn't trying to be sarcastic. I really worked that  program hard . I was very unique for some test cases. It had a property, as Graham had mentioned , that would allow for a snapshot and you could roll back to working image if you borked the current one, lets say, with an update. 

regards..

---

### Post by izznogooood on 2017-04-09
Not to worry, I was the sarcastic one. I've had btrfs running on my home server for 1,5 years now and the performance with VM's / containers are better then EXT4 (or at least i feel it is). I'm well aware of its reputation, but my data is stored on a nas with EXT4 and Raid5. Not taking any chances.

Now I want it on my lap top but there's no choice when installing with full disk encryption, it automatically uses EXT4.

---

### Post by izznogooood on 2017-11-13
> **ventrical said:**
> Good luck , have fun! :)

Not easy.

Works for a while then breaks.

I definitively have to eat my words here ](*,). 

I came over this post again and since then I had 2 crashes on my disk which both resulted in complete loss of data! I took the second crash for me to in depth research the problem. It was related to write loss on the btrfs partition. Examining logs seeing warnings for weeks before total failure. 

The only differential "diagnosis" could be a loos wire (or faulty controller). How ever this is highly doubtful as the server have bean running on EXT4 without ANY issues for months now... (Same HW)

---

### Post by ventrical on 2017-11-13
> **izznogooood said:**
> I definitively have to eat my words here ](*,). 

I came over this post again and since then I had 2 crashes on my disk which both resulted in complete loss of data! I took the second crash for me to in depth research the problem. It was related to write loss on the btrfs partition. Examining logs seeing warnings for weeks before total failure. 

The only differential "diagnosis" could be a loos wire (or faulty controller). How ever this is highly doubtful as the server have bean running on EXT4 without ANY issues for months now... (Same HW)


When I tested it I thought it was the cure-all-app for broken systems caused by update/upgrades  but the  fs itself could not seem to manage itself after a while. But it was fun testing.

---

### Post by izznogooood on 2017-11-13
> **ventrical said:**
> but the  fs itself could not seem to manage itself after a while.

You hit the nail on the head there.

---

