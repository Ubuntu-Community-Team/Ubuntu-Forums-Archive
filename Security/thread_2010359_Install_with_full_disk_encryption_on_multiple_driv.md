---
title: "Install with full disk encryption on multiple drives?"
date: 2012-06-25
forum: Security
---

### Post by Cheesemill on 2012-06-25
I'm about to re-install my OS and have thought of something I don't have the answer to.

I have plenty of experience installing systems using dm-crypt and LVM but these have all been systems with only one drive. My current setup has an SSD for /boot, / and /home and then an HD for /data and swap.

Is it possible to have both drives encrypted in such a way that I will only be asked for a decryption passphrase once upon boot (obviously the same passphrase will be used for both drives)? As far as I can work out I can set up two encrypted LVM's but don't know how to unlock them both with a single passphrase request.

Does anyone have any experience with such a setup?

---

### Post by [o_0] Rob on 2012-07-20
I'm also interested in this question.

---

### Post by Cheesemill on 2012-07-31
Time for a bump, up you go :)

---

### Post by Blackbird_13 on 2012-08-01
Not sure how helpful I can be, but this is my experience.

I have a desktop and a laptop that each have 2 hard discs.  I used the 12.04 alternative install CD and encrypted partitions on both hard drives. I then created LV Groups and LV's. The net result is, on each pc, I only need one pass-phrase to unlock both hard discs.

My approach on the two hard discs was slightly different.

DESKTOP
I created separate LVG's for the 2 hard discs (used logical partitions on each) I also had a separate encrypted fat32 primary partition on sdb3. On the first boot I had to enter 3 pass-phrases. I then created luks keys for sda5 and the fat32 partition and stored them on my root system on sdb5. I manually edited /etc/crypttab to reflect the change to keys. Now I just need to use one pass-phrase to unlock my root system and the keys unlock my remaining encrypted partitions on sda and sdb.

LAPTOP
This is a little harder to explain, but the net result is the same (i.e. I just need one pass-phrase).

I created one LVG for the 2 hard discs (used logical partitions on each). I also had a separate encrypted fat32 primary partition on sdb. On the first boot I had to enter 3 pass-phrases. I then created keys for sda5 and the fat32 partition and stored them on my root system on sdb5. 

This is where it gets tricky. Initially, I was prompted for two pass-phrases (for sda5 and sdb5) which was a real pain and not something I was expecting. I experimented with using compbiniations of keys/pass-phrases for both sda5 and sdb5 with no success.

After a week(?) it suddenly self-corrected. The only thing I can think of is I had a new kernel update and the "update-initramfs" sorted it out for me. 

Now I just need to use one pass-phrase to unlock my root system and the keys unlock my remaining encrypted partitions on sda and sdb. Interestingly, the pass-phrase I use is for sda5 which does not contain my root system (that's's on sdb5).  

There is one other complication and unfortunately my memory on this is a little vague.  After the initial install I played about with some of the partitions on both pc's and installed other encrypted OS's on unused partitions. I think the problem arose on the laptop but it may have been the desktop. In any case, whichever pc it was, I had a failed update-initramfs after a kernel upgrade. The failure related to not recognising a specific luks encrypted partition. This meant I could not boot the new kernel. My solution was to manually amend the new initrd.

Both pc's now seem fine booting with one pass-phrase and no problem with subsequent update-initramfs.

Until March of this year I had not used luks/lvm so I've really got here by trial and error. If you want any more info let me know.

---

