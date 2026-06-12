---
title: "Boot from a 3TB HDD?"
date: 2013-04-24
forum: Server Platforms
---

### Post by fkjensen on 2013-04-24
Hi guys,

I have just installed ubuntu server on a 3 TB HDD, but it will not boot.
I have red some stuff about GPT and efi boot, but I am a bit confused (and yes, I am new at this linux stuff).
Any guide on how to set up the partitions so it will work?

The motherboard is an Intel D845GSEJT. It should support UEFI boot, but according to this:
[http://www.intel.com/support/motherboards/desktop/sb/CS-010355.htm#2TB](http://www.intel.com/support/motherboards/desktop/sb/CS-010355.htm#2TB)
-----
Enabling support for 2 terabyte drives
If you are using a hard drive 2 terabytes or greater 
in capacity, you must enable UEFI (Unified Extended Firmware Interface) in order 
for your system to recognize the drive.
 
To enable UEFI:
 
1.During boot, enter the BIOS setup by pressing F2. 
2.Go to the Boot menu. 
3.Set UEFI Boot to Enable. 
4.Press F10 to Save and Exit.
-----

I should enable it in the bios, but the option is not there. I have updated to the latest bios version.

Any help?

Best regards,
Frank

---

### Post by darkod on 2013-04-24
It says you only need that to recognize the disk as 3TB. Does it recognize it as 3TB? If it does, forget about it. And it's best to use legacy boot anyway, forget about the uefi boot.

With windows, you would have to use uefi boot since it needs that for gpt tables (and it needs a gpt table for a disk above 2TB), but with linux you can use legacy boot with gpt.

The only thing you need to be careful about, is that on gpt disks grub2 needs a small 1MiB partition with no filesystem and with the bios_grub flag set. Grub2 will put part of it's code there. Note: it does it automatically, you still install grub2 to the MBR, not that small partition.

For a 3TB disk it would also be good to put the boot files at front. There are two ways to do this: making a small / partition at front, or if you want / to be big and include everything, make a small /boot partition in front.

So, the order would be:
1. Check that the bios recognizes the disk as 3TB. Very important thing!!! If bios doesn't see it right, it will not present it right to the OS.
2. Make a gpt table on the disk (in case you already don't have one).
3. Make small 1MiB partition with no filesystem (raw format, no fat, no ntfs, no ext4, nothing). DO NOT format it with a filesystem. Put a bios_grub flag on it.
4. Make a small 500MB-1GB ext4 /boot partition, if you decided to go for that option.
5. Make / taking the rest of the disk...

---

### Post by fkjensen on 2013-04-24
Thanks for the extremely fast reply :-)

The disk was recognized as 3TB during the install.
The rest of the stuff is where my linux skills fall a bit short (it seems I am always getting a bit confused, when it comes to partitioning in linux...)

How do I make a gpt table on the disk?

Once that is done, I guess I can maybe figure out the rest - maybe... :-)

I was thinking of making a smallish (~20GB) / partition and then use the rest for /home, but a 1GB /boot and the rest for / would also work. Or maybe 1GB for /boot, 20GB for / and then the rest for /home...
Any pros and cons?
What's the recommended file system for these partitions? ext4?

~Frank

---

### Post by darkod on 2013-04-24
If you plan to run some services, like mysql databases, etc, note that by default they don't put the data in /home. So having a small / can be bad. And if you make small / at start there is no need for separate /boot.

I prefer doing partitioning with parted in terminal in live mode. So, boot the server first with the desktop live cd in live mode and open terminal. If that hdd is the only one, it will be /dev/sda. If not, change the following commands accordingly.

Use parted to manipulate the partitions:
```
sudo parted /dev/sda
```

Once in the parted prompt:
```
mklabel gpt #(new blank gpt table)
unit MiB #(change the display units to MiB)
mkpart GRUB 1 2 #(make small 1MiB partition between 1 and 2 with label GRUB)
set 1 bios_grub on #(set the bios_grub flag to ON on that partition)
mkpart ROOT 2 20482 #(make partition for / with size 20480MiB=20GiB)
mkpart HOME 20482 xxxxx #(make partition for /home between 20482 and the total number of MiB on the disk minus few)
quit #(quit parted)
```

You can get the total numbers of MiB of the disk after you changed the unit with:
print

on the parted prompt. Using print you can view the current info at all times. The disk details shown will show the total size in MiB if the current unit is MiB.

That should get you going. When making the server install use the partitions 2 and 3 as ext4, with mount points / and /home respectively. Do NOT make any changes on partitions 1, leave it as it is.

---

### Post by fkjensen on 2013-04-27
Thanks for the guide.
I didn't do it yet, but when I check the partitions during the install, I get something similar:

[IMG]http://dodgethis.dk/files/20130427_083215.jpg[/IMG]

It isn't called bios_grub but biosgrub though. When I look at the details the boot flag is not set:

[IMG]http://dodgethis.dk/files/20130427_085951.jpg[/IMG]

I doesn't look like I can change it...

Also, why are there two unused parts (they are small, yes, but why?)
And what's the 2nd partition (ext2) for?

I have used LVM on the 3rd partition. Is that ok?

Best regards,
Frank

---

### Post by fkjensen on 2013-04-27
Btw, don't I need a swap partition as well?

Best regards,
Frank

---

### Post by darkod on 2013-04-27
The biosgrub is fine, that's how the server installer shows it. The bootable flag is not the same, you see it says Use As: Reserved BIOS boot area. That should be fine.

The small 250MB partition was probably prepared to be /boot, because often when using LVM you have separate /boot outside the LVM. But you need to select it with Enter, change the Use As to ext4, and select mount point /boot.

You also need to "use" both LVs you have at the top. Select the root LV and set it as ext4 with mount point /. Then select the swap LV (that will be the swap), and select the Use As to swap area. Swap doesn't use mount point.

That should be it.

But before you start you might consider deleting partitions #2 and #3 and making a bigger ext4 partition for /boot, and then the rest of the space for the LVM. It's best to have little bit more in /boot than 250MB. Something like 500MB or 1GB.

---

### Post by fkjensen on 2013-04-27
Thanks.

One more thing, I am asked if it should install GRUB to the master boot record. Should I?

Ok, one more thing, I have not set anything up regarding GPT. Should I have done that or is it using GPT as standard (could be, I am not really understanding this properly...)?

Best regards,
Frank

---

### Post by fkjensen on 2013-04-27
Well I did install grub to the MBR, but it didn't boot...
My partitions are set up as:
[IMG]http://dodgethis.dk/files/20130427_141212.jpg[/IMG]

What am I doing wrong? Is it the grub on the MBR or is it that I do not use GPT and if so, how do I set that up during the install? Or do I have to make a USB with the desktop version and do the "parted" suggestion above?

Best regards,
Frank

---

### Post by darkod on 2013-04-27
It looks good. Yes, the bootloader goes to the MBR. You are using gpt since partition #4 is 3TB. With msdos table the max partition size is around 2TB. So it can't be msdos.

You can also try this: Open the / partition and set the boot flag on it. Sometimes some motherboards need that even though ubuntu doesn't use it.

---

### Post by fkjensen on 2013-04-27
That didn't help.
I started up in rescue mode form the USB stick and used print in parted:

[IMG]http://dodgethis.dk/files/20130427_210314.jpg[/IMG]

Any ideas?

Best regards,
Frank

---

### Post by oldfred on 2013-04-27
I do not know servers like Darko does. And we have seen with Intel motherboards the issue of not booting anything unless a boot flag was present and even some gpt drives needing a boot flag.
But with the new UEFI the boot flag is only supposed to be on an efi partition and then UEFI looks for boot files. And some UEFI/BIOS switch automatically between UEFI and BIOS.

Or not sure if you should have boot flag on a partition or not. 
Per UEFI standard it should only be on an efi partition and UEFI needs gpt. 
Per Intel (who wrote original UEFI spec) some gpt drives need a boot flag even when BIOS booting.

---

### Post by darkod on 2013-04-27
It all looks good. Sorry, I have no clues right now. Does it show any message at all during boot?

It could be a video issue although that is rare with a server. Or the grub menu simply not showing up. If you wait longer, does it boot to the login screen maybe?

---

### Post by fkjensen on 2013-04-27
Right after the initial motherboard spash screen it just says:
"A bootable device has not been detected. Please refer to the Product Guide at <link to Intel product support>"
And then it just stops there.
I have also tried to set the bios to wait 15s before detecting the HDD (maybe it was slow to start up), but that didn't help either.

Btw, it boots just fine with my old 1.5TB HD running Ubuntu server 9.04.
The partition info for that is:

[IMG]http://dodgethis.dk/files/20130427_223651.jpg[/IMG]

Best regards,
Frank

---

### Post by oldfred on 2013-04-27
Server does not have live mode, so you would have to download a Desktop version to run this, but it may show something we have missed:

 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

### Post by Vegan on 2013-04-27
That old 865 chipset is not UEFI, its MBR only so 2TB is as big as the boot disk will go.

My new M5A99FX PRO R2.0 however can boot 5 TB disks as it has full UEFI boot capacity

---

### Post by fkjensen on 2013-04-28
I think the board uses Intels mobile 945GSE Express chipset. Still maybe that doesn't have UEFI, but do I need it for Linux (Ubuntu server 32 bit)?

I have downloaded the server version (ubuntu-12.04.2-server-i386.iso). I have put it on a USB stick with UNetbootin. When it boots I have several options. Some of them are:
- Default (will start the installation process, but will fail when it can't find the CDROM (duh, I am using USB!))
- Install (Works, but it looks like it is downloading the whole thing. At least I have to wait quite a while before it gets going with the actual install)
- Install server (looks like the same as default)
- Rescue mode (will let me choose a root partition and run a shell. That's how I got the "parted" info)

I have also tried to use Pendrivelinux, but here I also get the no-cdrom error.
When the install succeeds, with the above "Install" option, I have to chose what kind of server I want to install, so I think I am installing the server edition.

I will look at the boot-info/repair later today.

Best regards,
Frank

---

### Post by fkjensen on 2013-04-28
I just red this article: [http://www.ibm.com/developerworks/linux/library/l-gpt/](http://www.ibm.com/developerworks/linux/library/l-gpt/)
I looks like I should be using GRUB2 for GPT on a BIOS system (i.e. non-EFI).
How do I find out what's being installed? And if it is GRUB, how do I install GRUB2 instead?

Best regards,
Frank

---

### Post by darkod on 2013-04-28
Ubuntu since 9.10 comes with grub2 by default. So, any clean install of any recent version is using grub2.

It might be a BIOS limitation, or it might be that it really expect the boot flag to be on FAT32 partition like oldfred says, even when you are not using uefi boot. The problem is that most manufacturers still design with Microsoft in mind, and for windows you would have to use uefi boot with gpt. With linux, you can use both legacy and uefi boot with gpt disk.
Especially since it's Intel board, and they came up with uefi, I wouldn't be surprised it can't boot because it's detecting gpt disk with no uefi system partition.

What if you try creating small 200MB FAT32 partition and set the boot flag on it. But it has to be first on trhe disk.
After that create the bios_grub, because it doesn't need to be first.
Then create all your other partitions.

But use bios boot, not uefi. Just make the fat32 partition to see if that makes the board happy.

That error message "bootable device not detected" is from the board, not the OS.

---

### Post by fkjensen on 2013-04-28
BootInfo: [http://paste.ubuntu.com/5613542/](http://paste.ubuntu.com/5613542/)

Hope it helps :-)

Also, I tried to install 12.04 desktop 32bit but with the same result. This was before I did the BootInfo, so the partitions has changed a little, but the problem is probably the same.

Best regards,
Frank

---

### Post by darkod on 2013-04-28
It all look good, I can't notice anything at all wrong.

Again, if you are willing to do a test and create small 200MB fat32 partition as first one, in case this is what your board expects. Don't forget to put the boot flag on it (not the bios_grub). You should still have the bios_grub partition because grub2 will need it.
After those two partitions, you can create the other partitions as you want. It wouldn't hurt to have 20-25 GB root partition at front, or at least 1GB /boot partition. That will make sure the boot files are kept close to the start of the disk. You don't need to do both, either small / at front with larger /home on the rest of the disk, or if you expect to need big space for / for databases and such, simply put a small /boot at front and that's enough.

---

### Post by oldfred on 2013-04-28
Back to Darko's post #2. A smaller / (root) of 25GB or a separate /boot.
There used to be a bug which I thought they fixed where  grub got lost on very large / (root) partitions that were over 500GB. It may still apply for those over 2TB?

      ```
            GiB - GB             File                                 Fragment(s)

   1124.137115479 = 1207.033036800 boot/grub/grub.cfg                             1
 216.234535217 = 232.180064256  boot/grub/core.img                             1
1124.135375977 = 1207.031169024 boot/vmlinuz-3.5.0-23-generic                  1
1124.135375977 = 1207.031169024 vmlinuz                                        1
   1.561054230 = 1.676169216    boot/initrd.img-3.5.0-23-generic               2
   1.561054230 = 1.676169216    initrd.img                                     2

```    

You have some boot files at 1.67 and some at 1207 which is pretty far apart.

---

### Post by fkjensen on 2013-04-28
I tried (still with the 12.04 desktop version) to make a 200MB FAT32 partition with "boot" on as the first partition, but still no luck...
I couldn't find an option to set the boot flag during the install, so I booted in live mode and did it with parted. I used "boot", should I have used "legacy_boot"?

The partitions looked something like this:
1: 200 MB FAT32 boot
2: 1 MB bios_grub
3: 1 GB swap
4: 20 GB /
5: 3TB /home

Best regards,
Frank

---

### Post by fkjensen on 2013-04-28
> **oldfred said:**
> You have some boot files at 1.67 and some at 1207 which is pretty far apart.

Is this a problem and if so how do I change that?

Best regards,
Frank

---

### Post by darkod on 2013-04-28
> **fkjensen said:**
> Is this a problem and if so how do I change that?

Best regards,
Frank

With the setup you posted in post #23 that would be solved. The boot files will go into / and since root is small only 20GB and at the front of the disk, they will be there instead of way back on the disk.

Yeah, the boot flag on sda1 looks good, it's called boot. sda2 also looks good, it has the bios_grub flag and it has no filesystem, which is correct.

Try installing like that and let us know.

---

### Post by fkjensen on 2013-04-29
> **darkod said:**
> Try installing like that and let us know.

I did, still no luck :-/

Best regards,
Frank

---

### Post by oldfred on 2013-04-29
I really expected that to work.
Are you using the 64 bit version? And 12.04 or 12.04.2. Only difference is the kernel for 12.04.2 is a newer version.

Post a new link to a BootInfo report just to see if anything seems out of place, but at this point I am not sure.

---

### Post by fkjensen on 2013-04-29
> **oldfred said:**
> I really expected that to work.
Are you using the 64 bit version? And 12.04 or 12.04.2. Only difference is the kernel for 12.04.2 is a newer version.

Post a new link to a BootInfo report just to see if anything seems out of place, but at this point I am not sure.

I am using the 32 bit version as the Intel D945GSEJT is only 32 bit (I think).
ubuntu-12.04.2-server-i386.iso and ubuntu-12.04.2-desktop-i386.iso

I will post the BootInfo report later this evening.

Best regards,
Frank

---

### Post by oldfred on 2013-04-29
If you have Core2 Duo processor then it is 64 bit. Both my laptop & desktop are different versions of Duo processors from 6 to 7 years ago and both run 64 bit without issue.
What mode is BIOS in, you need to have AHCI not IDE for hard drive access.

       32-bit vs. 64-bit Ubuntu 13.04 Linux Performance with only 1GB of RAM & most tests better with 64bit
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_x86_1304&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_x86_1304&num=1)

---

### Post by fkjensen on 2013-04-29
> **oldfred said:**
> What mode is BIOS in, you need to have AHCI not IDE for hard drive access.

YES!!! I think that was it. I just booted the currently installed desktop version after I switched from IDE to AHCI :D

I will se if I can remove the FAT32 "boot" partition and install the server edition later.

> **oldfred said:**
> If you have Core2 Duo processor then it is 64 bit. Both my laptop & desktop are different versions of Duo processors from 6 to 7 years ago and both run 64 bit without issue.

       32-bit vs. 64-bit Ubuntu 13.04 Linux Performance with only 1GB of RAM & most tests better with 64bit
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_x86_1304&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_x86_1304&num=1)

The processor on the Intel D945GSEJT is an Atom N270. I think it is 32 bit, but should I still be able to run 64 bit? (I have been running 9.04 32 bit the last few years, and it has worked just fine.)


And lastly, many thanks for all you guys excellent support, quick response and patience!! :KS

Best regards,
Frank

---

### Post by darkod on 2013-04-29
If it's N270 that's 32bit only. If you intend to install 64bit version it should give you an error about wrong infrastructure I guess.

---

### Post by oldfred on 2013-04-29
I think a lot of Atom's are 32bit, but do not know details.

---

### Post by fkjensen on 2013-04-30
The server edition is now installed and booting without the ekstra FAT32 "boot" partition :-)

Once again thanks for your help :-)

Best regards,
Frank

---

