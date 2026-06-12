---
title: "Hey, did I screw up acer eRecovery by installing ubuntu?"
date: 2008-07-27
forum: Windows
---

### Post by nerd0795 on 2008-07-27
At a curiosity since, my computer was acting a bit weird lately and I don't have an install disk with my computer.  I actually found while installing Ubuntu (I was editing the partitions and I found 3 Windows Partitions 1) 6GB 2) 90GB and 3) 90GB  I recently figured out that the 6GB partition was an restore partition.  while installing I only repartitioned the second partiton (with 90GB) and split it into 2 45GB partitions.  Not touching the 6GB.  Now the thing is did I screw it by installing Ubuntu?  I did make a factory default disk too...  but nobody was watching it and it could of crashed while doing so or something.  If I needed to restore Windows Vista do I need to delete the Ubuntu partition first?

I'm not planning on doing this anytime soon but since that's my only computer other then an old dusty Windows Mistake Edition computer.

EDIT:  I searched about the issue and get different responses.   Some say you can't do it because the bootloader is changed.  Some say you can.  Some say you need to clear all partitions first.  THE CONFUSION!!!

---

### Post by mikazo on 2008-07-27
I had the very same worries when I first tried installing Ubuntu on my HP laptop, which also has a small recovery partition. I have successfully re-installed Windows Vista after having installed Ubuntu on the main partition. The Grub boot loader was installed at the time, but before the boot loader screen appeared, there were still options to press function keys to access BIOS, and accessing the recovery partition was one of the options. Once you have access to recovery, it will re-partition and re-format your other drives as you see fit.

I don't know if you have the exact same situation, as yours is an Acer laptop, but my best guess is that you will still be able to restore Windows, should you need to.

---

### Post by zipperback on 2008-07-27
If you created the restore disk as per the Acer Laptop documentation PRIOR to installing Ubuntu you should be fine.

I have an Acer Aspire 5050-3371 and it gave me the option of creating the restore cd, but since I don't run windows I have long since done a full format and got rid of the hidden Acer Restore partitions.

- zipperback
:popcorn:

---

### Post by RheaHS on 2008-07-31
Is there any way of accessing the recovery partition to make the CDs without Windows installed? I have an Acer Extensa 5620z.

---

### Post by zipperback on 2008-07-31
> **RheaHS said:**
> Is there any way of accessing the recovery partition to make the CDs without Windows installed? I have an Acer Extensa 5620z.


"IF" you didn't wipe out the recovery partition you might be able to access it by rebooting your laptop and pressing the F12 key to access the recovery system. You might need to turn that on in the BIOS someplace, so boot the laptop and press F2 at the Acer boot screen. Look around for something that relates to the recovery boot key, it might be disabled on your system, or it might be a different key than F12.

If that doesn't seem to work, you "might" be able to boot your system up with the Ubuntu LiveCD and then use gparted to set the recovery partition to bootable and just boot into it. I didn't test that idea, but it might work for you. **[COLOR="Red"]Proceed with caution however and make sure you backup all your important files FIRST, because the windows recovery system might wipe your Linux data. BE CAREFUL![/COLOR]**

If that doesn't work, you'll need to set your Linux partition back to bootable again using gparted.

PROCEED WITH CAUTION. BACKUP YOUR DATA BEFORE YOU DO ANY OF THIS.

I accept no responsibility if you wipe your data doing this stuff.

MAKE A BACKUP FIRST.

Good luck. And let me know if it works for you.

- zipperback

---

### Post by dracule on 2008-07-31
I know for HP's recovery, it

erases C:/ and doesnt touch any other partitions
destorys MBR and replaces it w/ microsofts
will downgrade from vista to xp

---

### Post by nerd0795 on 2008-07-31
I forgot to mention I have the desktop Acer Aspire.

---

### Post by dca on 2008-08-01
Most newer computers from big box guys like Dell, HP, Acer, etc no longer ship optical disks with images on them or Windows complete OEM OS' and separate disk w/ drivers.  Everyone has migrated to separate partition on same HDD.  When in XP or Windows in general, you'll see C:\ having a ton of gigs and D:\ or something similar will be labeled as recovery or 'HP' or whatever and only be a 6 - 12 gig partition.  Most (okay 90%) of the Linux distro(s) I've messed about with all successfully listed the partition.  I'd leave it alone and wipe what consisted of C:\ and installed there...
 
Now, don't quote me on this but I'm almost positive the Dell laptop I had prior to being blasted into space prompted during Dell splash right after POST if I wanted to enter BIOS, boot into recovery, and one other option...

---

