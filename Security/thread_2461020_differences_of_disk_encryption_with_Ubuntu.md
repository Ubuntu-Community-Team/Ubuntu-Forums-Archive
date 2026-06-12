---
title: "differences of disk encryption with Ubuntu"
date: 2021-04-22
forum: Security
---

### Post by Skaperen on 2021-04-22
what are the pluses and minuses of letting the installer encrypt your  hard drive vs. doing it yourself?  i have multiple drives and intend to  have **/dev/sdc** be entirely encrypted at the block level  below the file system(s) on it.  i prefer encrypting everything  including the partition table.  but **/dev/sda** will not  be encrypted.  i want this laptop to boot up to a running Xubuntu system  without entering a pass phrase.  so /dev/sda will have a bbotable and  runable system on it.  i don't know what kind of **encryption configuration** or **encryption arrangement** i can get from the installer.

---

### Post by TheFu on 2021-04-24
So, you want the storage encrypted, but don't want to be bothered for a passphrase to unlock it?

There are a number of ways to unlock storage access with LUKS. There are 8 slots. I'd encourage you to read the **cryptsetup** manpage to understand how those options can be used.  A tightly coupled keyfile stored on a USB flash drive might the solution. Of course, there are caveats, since anyone with that keyfile would be able to unlock the storage and have free reign over it.  If the goal is only to protect the data during warranty returns of the HDD, then that keyfile isn't a real problem. But if you want security when traveling and have to provide there's an OS on the machine for a border customs agent, then the keyfile would become compromised.

The main reason I use the installer encryption setup, as un-perfect as that is, is because it is easy and fast. I wish they'd stop using MSDOS partition tables already and use GPT.  I like that they use LVM, but dislike that they make the root LV much too large.  LVM's power/flexibility comes from increasing the size as needed, not allocating it all at once. The first things I do post-install are to drastically reduce the root LV size, create a new Home LV and a new swap LV.  Then make those available for use as expected. I do this before there are any files on the system to make my life easier.  The install takes about 10 minutes. Fixing the LVM setup takes about 5 more.  How long does it take to manually do everything? Is it complex for someone like you or intuitively obvious?

---

### Post by Skaperen on 2021-04-24
> So, you want the storage encrypted, but don't want to be bothered for a passphrase to unlock it?

i didn't say that.  i *don't* want to mount the encrypted disk *automatically* (thus, it won't prompt me for the passphrase at that time),  the OS on /dev/sda will come up without any encryption active.  at this point a thief or border agent booting it will see a normal Ubuntu or Xubuntu system come up.  it may be configured to look like some widespread commercial OS.  at this point i can go to the admin user a via sudo i run a secret script that silently prompts me for the passphrase while it gives the illusion that i am playing hangman.  then it proceeds to let LUKS set up the decrypting mount.  it will then run a fully linked binary from the encrypted disk (does not use any libs from the unsafe disk, at least).  that binary checks to see if certain files on /dev/sda have been changed (especially the boot loader and kernel and modules).  then it proceeds to pivot the root point to the encrypted disk.

there are still ways to overcome this but it would be more effort and thus narrow the range of actors wanting to go further without me noticing.

i don't really know if i want to use LVM.  i want to first understand how it maps sector/block/page locations to understand what kind of performance loses i may have.  i can live with MBR.  i have MBR now.  what i usually do is partition the disk ahead of the install and use that.  i will be re-doing that even if i don't do any whole disk encryption because i need to increase the root partition, move the swap space, and shrink /home by 16G.

here is my bash script that generates my partition table:  [http://ipal.net/u/20210424/partition.bash](http://ipal.net/u/20210424/partition.bash)

i am OK with doing a manual setup though i do like to understand what i'm doing.  the script above calculates and shows my partition setup and outputs a full *sgdisk* command line to set it up.

---

