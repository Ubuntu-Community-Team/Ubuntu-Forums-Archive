---
title: "Another GRUB error"
date: 2012-04-03
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by scradock on 2012-04-03
My latest and greatest Precise (installed just before Beta2) is on sdb2, which is formatted btrfs, just to try it out. Worked fine until today. This is the GRUB-master for my second drive, sdb, so the grub-install command is grub-install /dev/sdb. This now fails, even when I re-reun with --recheck as advised in the error message.

The error message goes on to suggest running grub-probe, which gives both an info and an error message:

info: cannot open `/boot/grub/device.map' (which is not surprising, as the file does not exist);

and error: cannot find a GRUB drive for /dev/sdb2.  Check your device.map.

The grub-probe command suggested actually specifies the device-map location, so it should be trivial to change - if I knew where the device-map file should be.

Anyone know?

---

### Post by oldfred on 2012-04-03
device.map has been obsoleted.

See post #9 which repeats the grub 1.99 update log.

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/972250](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/972250)

> Don't generate device.map during grub-install or grub-mkconfig.

---

### Post by scradock on 2012-04-03
OK, so th error message is also out-dated.

I updated the grub programs today, of course. The update showed an error in debconf, so I tried to update manually to be sure not to upset my booting. update-grub ran fine, but grub-install failed with the error messages I mentioned.

Now I don't know if I need to fix something before re-booting. Do you have any idea what might have gone wrong? I don't have any GPT or EFI disks, but the laptop itself won't boot into any install on the second (USB) drive (a 2TB external) so I'm using PLOP as a workaround - I need it to get the second drive recognized at boot.

---

### Post by LostFarmer on 2012-04-03
I use 'PLOP' in the MBR of my boot hdd and it has the ability to change the partition table as I want.  Run 'fdisk-l'  does it look the way it should ?  

Depending on how you have 'plop' set up and if it is a old version, running any GUI partition program can mess up the logical partitions.  Or if you did not heed a PLOP error message when you booted.

---

### Post by scradock on 2012-04-03
> **LostFarmer said:**
> I use 'PLOP' in the MBR of my boot hdd and it has the ability to change the partition table as I want.  Run 'fdisk-l'  does it look the way it should ?  

Depending on how you have 'plop' set up and if it is a old version, running any GUI partition program can mess up the logical partitions.  Or if you did not heed a PLOP error message when you booted.

No, no PLOP errors on boot, except "error - sparse file not allowed". But that has been there since I installed to btrfs, and the boot always completes correctly after a time-out.

But at least the failure didn't ruin the boot of sdb2 (btrfs) from the second HD. It still boots up, and all my installs are listed. Looks as if the MBR on sdb still points to sdb2, and the grub.cfg on sdb2 is correct.

NOW, however, running update-grub in any OTHER install on sdb doesn't see sdb2 as bootable, despite having all the files needed to boot. sdb2 just doesn't come up on the list. So I can't switch to another install as GRUB-master, as I would lose the ability to boot into Precise on sdb2.

I'm guessing that the latest GRUB has not "liked" something about the btrfs partition. Any ideas anyone?

---

