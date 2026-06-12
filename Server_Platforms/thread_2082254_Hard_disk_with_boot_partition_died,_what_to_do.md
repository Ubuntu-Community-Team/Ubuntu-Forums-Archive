---
title: "Hard disk with /boot partition died, what to do?"
date: 2012-11-08
forum: Server Platforms
---

### Post by X1R1 on 2012-11-08
Post title explains it all, here is more info.

I have a server with 3 hard disks, here is the layout:

hard disk 1: /boot and swap partition (DEAD)
hard disk 2: raid1 member
hard disk 3: raid1 member

I installed the boot parition on a separate hard disk because I read somewhere that it was not advised to put the /boot partition inside a software RAID array (which is what I am currently using).

Tried to recover the files inside the boot partition to copy them to a new drive, but no luck, what can I do? can I just pop in a new drive and make a new boot partition with another disk and install grub on it? is the fix that simple?

Thanks for the help!

---

### Post by darkod on 2012-11-09
Installing grub2 is simple, but I am not sure what can be done about the missing kernels which are inside /boot also. Especially since the system "thinks" they are already installed so not sure apt-get install can install them. But you can try.

And for future reference, you definitely took some bad advice about /boot. The thing is that /boot can't be inside raid0 mdadm array since with raid0 you split the data and I guess the boot files don't tolerate to be split in two.

But for raid1 on the contrary, it's recommended to keep /boot on the array because even with one disk dead the system goes on and gives you a chance to replace the failed disk. You can have /boot as separate mdX raid1 device, or inside your / mdX device, doesn't matter. Sometimes it's better to have it separate at the start of the disks to make sure the boot files are not too far from the beginning of the disk on large disks. Some older machines can't use boot files if beyond the 137GB mark on the disk.

Having said the above, you don't even need a new disk to try and save this, and later keep /boot inside /.

Boot the server with the live cd, add the mdadm package since it's not in the live cd, and if needed reassemble the array (make SURE you do NOT use --create, use --assemble like):
sudo mdadm --assemble --scan

After that mount the root mdX device on /mtn for example (temporary mount point). Open /mnt/etc/fstab (your server fstab) and comment the /boot line adding # at the beginning. That will make it ignore looking for the /boot partition on the dead disk.

After that create a boot folder inside root which in this case would be:
sudo mkdir /mnt/boot

Since there is no separate entry for /boot in fstab, the OS will try to use the boot folder inside /.

Then all you need to do is chroot into /mnt and try installing the latest kernel and grub2. If you need more detailed help with that, ask. I think the above general ideas should be the correct way to go.

---

### Post by X1R1 on 2012-11-09
thanks! trying this now, will come back later with the results!

---

### Post by X1R1 on 2012-11-09
So, if my RAID device is /dev/md0, while chrooted, I just do:

grub-install /dev/md0

and then try to install the kernel packages (I am guessing this would be a good time to use apt force option?? since the package is marked as installed but some files are missing now).

A little more details would be awesome, since the RAID array contains pretty critical info (about 350 GB of work files) and I would hate to mess up the array and need to do a full restore.

thanks a lot for the help!

EDIT: According to this help page: [https://help.ubuntu.com/community/Grub2/Installing]("https://help.ubuntu.com/community/Grub2/Installing")[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing) point 10 says:

> Reinstall GRUB 2 (substitute the correct device with sda, sdb, etc. Do not specify a partition number):

grub-install --recheck /dev/sdX
If the system partitions are on a software RAID install GRUB 2 on all disks in the RAID. Example (software RAID using /dev/sda and /dev/sdb):

grub-install /dev/sda
grub-install /dev/sdb

So its not on the RAID array itself but on the RAID member disks.

Would this measure cause my array to get out of sync?

---

### Post by darkod on 2012-11-09
No, software raid is done on the OS level, it's not like hardware raid or fakeraid. So the grub is installed to the MBRs of the disks belonging to the raid, not to /dev/md0.

For example, if md0 is made from partitions on sda and sdb, it would be:
grub-install /dev/sda /dev/sdb

That way both disks have the bootloader and it can boot if one dies.

As for forcing the kernel installs, I never needed to do that but I would say it sounds right to use the force option. Don't forget that grub files will be missing too since they are in /boot also, so you might need to recreate some config files with:
grub-mkconfig
update-grub

Run the grub-install after that.

---

### Post by darkod on 2012-11-09
> **X1R1 said:**
> 


So its not on the RAID array itself but on the RAID member disks.

Would this measure cause my array to get out of sync?

I don't think so. We are talking about bootloader installation on the MBR which is not part of the raided partitions. It doesn't relate to the sync I think.

---

### Post by X1R1 on 2012-11-09
VICTORY!!!

I ended up using this to fix grub:

[http://sourceforge.net/p/ubuntu-secured/home/Home/](http://sourceforge.net/p/ubuntu-secured/home/Home/)

Its compatible with raid arrays so no problems :D

for replacing the kernels, I just did:

sudo apt-get install linux-image-server

and that pulled the latest kernel (which I have never installed), and copied the required files.

For this to work you need to chroot and also specify /dev/pts, and /dev mountpoints, I was going to post how I did it here but I lost the link :D (will come back and edit when I find it)

everything is back to normal! thanks a lot for the help!

---

