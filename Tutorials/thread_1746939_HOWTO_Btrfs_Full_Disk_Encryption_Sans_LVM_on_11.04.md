---
title: "HOWTO: Btrfs Full Disk Encryption Sans LVM on 11.04"
date: 2011-05-02
forum: Tutorials
---

### Post by AlexEagar on 2011-05-02
The following tutorial demonstrates how to install Ubuntu 11.04 with btrfs and full disk encryption without LVM. I am using the amd64 alternate installation cd on a Dell laptop with 128 GB SSD hard drive, but the instructions should work for any single full disk setup.

Note: I just noticed [the following gotcha]("https://btrfs.wiki.kernel.org/index.php/Gotchas"): btrfs volumes on top of dm-crypt block devices (and possibly LVM) require write-caching to be turned off on the underlying HDD. Failing to do so, in the event of a power failure, may result in corruption not yet handled by btrfs code. (2.6.33)

I haven't looked into write-caching on my SSD but I've got a battery, so hopefully I don't lose power. :p

[Btrfs :popcorn:]("https://btrfs.wiki.kernel.org/index.php/Main_Page") is a revolutionary file system, but it's still being developed and a btrfsk fsck tool to fix file system corruptions, has not yet been written. It's supposed to be stable for everyday usage, so if you've got a computer without important data on it, try it out!

**Overwrite Disk with Random Data**
[LIST][*]When you get to the partitioning step, select Manual.
[*]Select your disk device, which is the selection above the individual partions.
[*]Create new empty partition table on this device? Yes
[*]Select pri/log # GB FREE SPACE.
[*]Select Create a new partition.
[*]Leave the maximum partition size and select Continue.
[*]Select Primary.
[*]The partition options are not important, but I set them to what my /boot is going to be.
[*]Select Use as: btrfs journalng file system.
[*]Select Mount point: /boot.
[*]Select Bootable flag: on.
[*]Select Done Setting up the partition.
[*]Before you can fill the drive with random data, you need to save the new partion.
[*]You're not setting up encrypted volumes yes, but in order to save the partition, select Configure encrypted volumes.
[*]Write the changes to disk and configure encrypted volumes? Yes
[*]At Encryption configuration actions, select Go Back.
[*]Select the partition that you created a moment ago.
[*]Select Erase data on this partition.
[*]Really erase the data on your disk, partition #1? Yes
[*]Wait for a while for your disk to be erased.
[*]Select Done setting up the partition.[/LIST]

**Default Swap Size**
[LIST][*]Swap space lets your computer cache RAM to your hard drive.
[*]Swap space can be allocated as a partition or as a file, but btrfs doesn't currently support swap files.
[*]To see the suggested swap partition size, select Guided partitioning, select Guided - use entire disk, then select your disk.
[*]As a personal preference I prefer primary partitions, so write down or remember your swap partition size.
[*]Highlight your disk device, which is the selection above the individual partions.
[*]Create new empty partition table on this device? Yes[/LIST]

**Create the Boot Partition**
[LIST][*]A small portion of your disk will not be encrypted so that the computer is able to load the encryption password prompt.
[*]Select pri/log # GB FREE SPACE.
[*]Select Create a new partition.
[*]Enter 268.9275 MB and select Continue.
[*]Select Primary.
[*]Select Beginning.
[*]Select Use as: btrfs journaling file system.
[*]Select Mount point: /boot.
[*]Select Bootable flag: on.
[*]Select Done Setting up the partition.
[*]At this point on my computer, the boot partition says that it is 268.4 MB.
[*]Verify that the boot partition is big enough by saving it to disk.
[*]You're not setting up encrypted volumes yes, but in order to save the partition, select Configure encrypted volumes.
[*]Write the changes to disk and configure encrypted volumes? Yes
[*]At Encryption configuration actions, select Go Back.
[*]If the screen turns red and says that there was an error, delete the partition and increase its size when you recreate it.[/LIST]

**Create the Root Partition**
[LIST][*]Select pri/log # GB FREE SPACE.
[*]Select Create a new partition.
[*]Enter the total size minus the default swap size.
[*]As a personal preference I prefer primary partitions, so select Primary.
[*]Select Beginning.
[*]Select Use as: physical volume for encryption.
[*]Select Done Setting up the partition.
[*]Select Configure encrypted volumes.
[*]Write the changes to disk and configure encrypted volumes? Yes
[*]Select Create encrypted volumes.
[*]Use space bar to select the second partition.
[*]Select Continue.
[*]Select Finish.
[*]Type your full disk encryption password.
[*]Select Continue.
[*]Type your full disk encryption password.
[*]Select Continue.
[*]Select the encrypted volume which was just created.
[*]Select Use as: btrfs journaling file system.
[*]Select Mount point: /.
[*]Select Done Setting up the partition.[/LIST]

**Create the Swap Partition**
[LIST][*]The swap partition will use a ramdom encryption key which is intentionally discarded each time you shut down your computer.
[*]Select pri/log # GB FREE SPACE.
[*]Select Create a new partition.
[*]Leave the maximum partition size and select Continue.
[*]Select Primary.
[*]As a personal preference I prefer primary partitions, so select Primary.
[*]Select Use as: physical volume for encryption.
[*]Select Encryption key: Random key.
[*]Select Done Setting up the partition.
[*]Select Configure encrypted volumes.
[*]Write the changes to disk and configure encrypted volumes? Yes
[*]Select Create encrypted volumes.
[*]Use space bar to select the third partition, which is the second partition listed.
[*]Select Finish.[/LIST]

**Installation and Configuration**
[LIST][*]Select Finish partitioning and write changes to disk.
[*]Write the changes to disks? Yes
[*]Install the GRUB boot loader to the master boot record? Yes
[*]Hold down the shift key as your computer starts up in order to enter the Grub2 menu.
[*]Highlight Ubuntu, with Linux 2..38-8-generic.
[*]Press e.
[*]Type rootflags=subvol=@ in the space between the ro and quiet.
[*]Press Ctrl-x or F10 to boot.
[*]Press Esc at the Press any key to continue... prompt.
[*]Press Esc to display the graphical framebuffer.
[*]Type your disk encryption password and press enter.
[*]Log in.
[*][Apply this workaround]("https://bugs.launchpad.net/ubuntu-release-notes/+bug/757631/comments/8"), which is described in the steps below.
[*]Verify that rootflags=subvol=@ would not be generated if you recreated /boot/grub/grub.cfg.
[*]Open a Terminal.
[*]sudo grub-mkconfig | grep " ro "
[*]If the output does not contain rootflags=subvol=@, then do the following.
[*]sudo nano -c /etc/grub.d/10_linux
[*]Replace line 59 from this: 
```
if [ "x`${grub_probe} --device ${GRUB_DEVICE} --target=fs 2>/dev/null || true`" = xbtrfs ]; then
```
with these two lines (Hint: Pressing Ctrl-k Ctrl-u Ctrl-u will duplicate the line.):
```
#if [ "x`${grub_probe} --device ${GRUB_DEVICE} --target=fs 2>/dev/null || true`" = xbtrfs ]; then
if [ "x`stat -f --printf=%T /`" = xbtrfs ]; then
```
[*]Save and close by pressing Ctrl-x then pressing y and then Enter. 
[*]Verify that rootflags=subvol=@ would be generated if you recreated /boot/grub/grub.cfg.
[*]sudo grub-mkconfig | grep " ro "
[*]If the output does contain rootflags=subvol=@, then recreate your /boot/grub/grub.cfg.
[*]sudo cp /boot/grub/grub.cfg /boot/grub/grub.cfg.backup
[*]sudo update-grub2[/LIST]

---

### Post by zerothink on 2011-06-07
Thanks for detailed guide!

One question - is it possible to use hibernation (considering swap uses random password) ?

---

### Post by tim001dev on 2011-10-14
> **zerothink said:**
> Thanks for detailed guide!

One question - is it possible to use hibernation (considering swap uses random password) ?

No you can't hibernate. I don't have a full disk encryption, just /home, swap and /tmp, but I certainly can't hibernate.
You can sleep though (suspend to ram) which is all I really need.

---

