---
title: "pre-encryption disk randomization"
date: 2008-06-05
forum: Security
---

### Post by mepic on 2008-06-05
Hi,
I have been following the tutorial at [Ubuntu Tutorials: 7 Steps To An Encrypted Partition (local or removable disk)]("http://ubuntu-tutorials.com/2007/08/17/7-steps-to-an-encrypted-partition-local-or-removable-disk/") by [Christer Edwards]("https://wiki.ubuntu.com/ChristerEdwards").
From Step 4:
[INDENT]We’ll write data over the newly created partition to help aid in the encryption process. By writing data to the partition prior to encryption it helps protect against data attacks, finding patterns on the block-level, etc. You can use one of the following three commands:
...
sudo dd if=/dev/urandom of=/dev/sda bs=4K
[/INDENT]

On my system [1.8GHz Pentiuim 4/512Mb RAM/750Gb (New) HDD/8.10 Live CD] this will produce 1.8Mb of data per second - which will take 5 days to complete! :popcorn: Reading from /dev/zero procudes 67Mb/s transfer.

Would like to know:
[LIST]
[*]Relative benefit of this process on a new hard drive (compare ubuntu encrypted install does not randomize disk)?
[*]Would I expect better performance if the process was run on a proper install and not a Live CD? 
[*]Would performance improve if some music played in the background to seed urandom?
[/LIST]
Thanks in advance

---

### Post by hyper_ch on 2008-06-05
if it's a new disk, then you don't really need to delete evidence that's on there...

if you use the alternate installer, you can fully encrypt your system from installation, it will then also randomize the data on there but it will take a lot less time.

---

### Post by Biochem on 2008-06-05
> **hyper_ch said:**
> if it's a new disk, then you don't really need to delete evidence that's on there...

if you use the alternate installer, you can fully encrypt your system from installation, it will then also randomize the data on there but it will take a lot less time.

My experience with the randomization of the HD in the alternate installer is different. It stalled after a while, probably due to a lack on entropy. the dd if=/dev/urandom was way faster.

If the HD is new then it is true that there is no data to erase so writing random data seems superfluous. However, if after encryption the empty sectors are still 00 then it would give some information to a potential attacker on what could possibly be on the drive. Depending on your paranoia level (IMHO, aluminium foil hat or higher), this is something bad

---

### Post by hyper_ch on 2008-06-05
dd /dev/urandom takes on my 500 GB disk about 2 1/2 days... the installer takes about 2h

---

### Post by HermanAB on 2008-06-05
If the encryption is any good, then the pre-writing won't make any difference.  If the encryption is not any good, then don't use it...

---

