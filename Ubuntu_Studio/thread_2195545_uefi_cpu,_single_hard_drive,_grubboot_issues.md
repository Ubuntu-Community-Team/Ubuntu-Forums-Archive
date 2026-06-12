---
title: "uefi cpu, single hard drive, grub/boot issues"
date: 2013-12-24
forum: Ubuntu Studio
---

### Post by Zalethon on 2013-12-24
Hi! I installed Studio on my Toshiba Satellite C55-A laptop, and I have been having problems. At first it was alongside Windows 8, but this HD has been completely formatted, and now contains only Studio. (Three partitions, /boot / and swap)

So when I boot up, I'm dumped into a minimal shell from which I can manually load and boot linux, which I learned to do elsewhere:

```

> linux (hd0,gpt2)/boot/vmlinuz-[etc]-generic.efi.signed root=/dev/sda2
> initrd (hd0,gpt2)/boot/initrd.img-[etc]-generic
> boot

```

In an attempt to fix the overall issue, and have the OS boot on its own, I ran boot-repair. It didn't work. [http://paste.ubuntu.com/6631323/](http://paste.ubuntu.com/6631323/)

Any ideas? Thanks!!

---

### Post by oldfred on 2013-12-25
You show two kernels installed. I assume the low latency is for Studio.

 Standard boot
/boot/vmlinuz-3.11.0-14-lowlatency
secure boot version
/boot/vmlinuz-3.11.0-14-generic.efi.signed 

But if you can only boot the signed version then you must have secure boot on? 
Or there is some difference in the versions otherwise. 

When you have secure boot on, only secure boot systems will boot. So with secure boot you cannot boot lowlatency or the Studio version.

---

### Post by Zalethon on 2013-12-25
Thank you for your response! I can boot into whichever kernel I choose, I'd just been using the one someone else used. I just verified this, in fact, and am responding from within the lowlatency kernel... Turning secure boot off has no effect. Everything seems to work fine except that it just doesn't boot automatically or show me a menu like I'm used to.

Two lines in my boot-repair log stuck out to me just now, at the very top of the log:
```

    Boot sector info:  According to the info in the boot sector, sda1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda1 starts at sector 2048.

```

And at the very bottom of the log as well:

```
The boot files of [The OS now in use - Ubuntu 13.10] are far from the start of the disk. Your BIOS may not detect them. You may want to retry after creating a /boot partition (EXT4, >200MB, start of the disk). This can be performed via tools such as gParted. Then select this partition via the [Separate /boot partition:] option of [Boot Repair]. (https://help.ubuntu.com/community/BootPartition)
```

Could this be the problem? I don't know how to transpose partitions and make room for a partition to mount at /boot in front. I also don't know if this will mess up the EFI partition that seems to mount at /boot/efi ?

ETA Or perhaps I should have marked the EFI parition as a separate boot partition for boot-repair?
ETA (removed a response I made to your signature.. I thought it was part of your response)

---

### Post by oldfred on 2013-12-25
I have not seen a new UEFI system where we had to move boot files. But some BIOS and particularly USB external drives seem to have that issue. Boot-Repair is just reporting it.

The efi partition is not a separate /boot. Some have said you can do a lot inside the efi partition but do not know details.

A work around posted and used by several others. I am not sure if there is a bug or some other issue.

Create a grub.cfg file in /efi/ubuntu folder in efi partition.
And just add this one entry. Or you can add all the lines you use to manually boot. The gpt2 entry must be the partition with your /boot/grub folder.

 configfile (hd0,gpt2)/boot/grub/grub.cfg

The efi boot will find the grub and use it to redirect to the actual grub file in your install.

I normally suggest smaller / (root) partitions and separte data or /home partition(s). Then most of the system files are closer together on the drive and the less used data files may then be scattered across drive. Usually Boot-Repair shows locations of boot files, line 426 in your current report, but it did not. That may be related to the issue you are having, but not sure what that could be.

---

### Post by Zalethon on 2013-12-25
The workaround didn't work: grub doesn't seem to want to load the config file from the efi partition either. But I can manually load the config file, so I know that much works. (And at least it's cut down on the steps I needed to boot)

Do you suppose it will help (or at least not hurt) to reinstall with a new partition scheme? ( 275MiB fat32 /boot/efi boot partition ; 30GiB ext4 / ; 6GiB swap ; remainder /home )

---

### Post by oldfred on 2013-12-25
That would be close to what I suggest as a partition scheme, but I am not sure if that will help your issue or not.
It is more if something is wrong in the grub install. You can try the full purge and reinstall of grub with Boot-Repair.

---

### Post by Zalethon on 2013-12-26
It has been fixed! I ran boot-repair once, purging and reinstalling grub like you suggested, and it didn't help. [http://paste.ubuntu.com/6640260/](http://paste.ubuntu.com/6640260/)

But there was a little message that piqued my interest, which hadn't been there before.

```
Please do not forget to make your BIOS boot on sda1/EFI/ubuntustudio/shimx64.efi file!
```

I looked around for a few minutes in the BIOS settings for a way to do that, and couldn't find one, so I did a little bit of research.
The answer I found didn't say to do it, but I turned secureboot off again--I can't remember why I wanted to, or if I unchecked the 'secureboot' box in boot-repair--and I checked the box that said 'Backup and rename Windows EFI files'.
I thought that the hard drive being completely formatted would have removed those, but apparently not. (Indeed, there was a 'Microsoft' folder in the EFI folder when I looked) I also purged and re-installed grub a second time. Now it works as expected; here's my nice, 'healthy' log file: [http://paste.ubuntu.com/6640345/](http://paste.ubuntu.com/6640345/)

I think that what did it was renaming the Windows EFI files, but I really see no need to turn secureboot back on. (If I turned it on and ran boot-repair again with the secureboot box checked, it might work fine, but why?)

Thank you for your help!!

---

### Post by oldfred on 2013-12-26
Boot-Repair does several things.
If you have secure boot on or check it, then it installs the secure boot versions of shim, grub, kernel so you can boot with secure boot on. Not sure it then it still works well with secure boot off.

Some systems will only boot the Windows efi file. They modify UEFI code to only see bootmgfw.efi. So Boot-Repair offers to back up that file and rename shim to be that file. Since shim has same Microsoft secure boot key UEFI will still boot that thinking it is booting Windows, but it boots grub and from grub you then can boot the backed up/ renamed Windows file.    
If your system boots an Ubuntu entry from UEFI menu then you do not need the rename and can undo it with Boot-Repair.
The main entry in UEFI will just be ubuntu or whatever version of ubuntu you have. But details will be the exact file.

UEFI memory saves old entries, which you can houseclean with efibootmgr.
       sudo efibootmgr -v

 The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:
[http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)

---

