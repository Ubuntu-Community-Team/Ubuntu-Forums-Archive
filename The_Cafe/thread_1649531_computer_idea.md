---
title: "computer idea"
date: 2010-12-20
forum: The Cafe
---

### Post by chris200x9 on 2010-12-20
I have a pipe dream of starting a business that builds laptops, what would be the problem of pre-installing a dual boot system. Then just mounting your windows home directory as /home in fstab? Then you could claim all of the benefits of both truthfully in commercials, i.e runs all your windows software, no viruses, has a microsoft compatible office suite, etc.

---

### Post by Spice Weasel on 2010-12-20
Ah... but there is a problem.

NTFS.

---

### Post by chris200x9 on 2010-12-20
I compiled a 2.6.37 kernel there was an option for ntfs write support so I'm assuming read and write is in kernel now...if I'm wrong why couldn't you mount it via fuse? It's not even root.

---

### Post by Barrucadu on 2010-12-20
NTFS doesn't support *nix permissions.

---

### Post by Spice Weasel on 2010-12-20
Since NTFS is reverse engineered there may be problems such as corruption, but I suppose as long as you back up it should be fine.

---

### Post by NCLI on 2010-12-20
> **Barrucadu said:**
> NTFS doesn't support *nix permissions.

This. That makes using it quite impossible.

---

### Post by chris200x9 on 2010-12-20
> **Barrucadu said:**
> NTFS doesn't support *nix permissions.

does that matter? The only problem with that I can see is from a security standpoint of a multiuser system?

---

### Post by Barrucadu on 2010-12-20
Yes, it does matter. A lot of things will break if they can't set permissions properly. The first example I can think of is SSH keys, which require your ~/.ssh directory to be readable only by you.

---

### Post by chris200x9 on 2010-12-20
oh that sucks, next idea why not just have a small native home and a "shared" or "data".

---

### Post by 3Miro on 2010-12-20
Create a dual-boot, but both systems should live on separate partitions. Then you can put a link in Linux to Windows home (MyWindowsFiles) and a link in Windows to Linux /home (MyLinuxFiles). This meas installing ext3/4 software under windows, but it should work.

>  runs all your windows software, no viruses, has a microsoft compatible office suite 

You cannot achieve that. Windows software (including Office) is accessible from Linux only after reboot. That is, download a .docx file, reboot and only then can I open it. Also, the windows part of the system will always be susceptible to windows viruses. There is simply no way of truly getting "the best of both".

---

### Post by warfacegod on 2010-12-20
Another potential major roadblock to this is that Windows is, for all intents and purposes, totally incapable of reading Linux filesystems such as ext3 and ext4.  Say one of your customers breaks their Linux install. They'll think, "Okay. I'll just boot into Windows and x,y,z the files to fix it". Oopsy! Windows can't read the filesystem and, in some cases, can't even see the partition.

---

### Post by warfacegod on 2010-12-20
I would offer your customers the option of either and offer free additional tech support if they opt for Linux.

---

### Post by oldsoundguy on 2010-12-20
Once MS found out you were setting up dual boots or similar to SELL, your OEM license would get pulled and you would have to pay retail for  Windows.

It is Windows ONLY on sales or it is Linux ONLY on sales.

What is done AFTER market is out of their control.

---

### Post by tgalati4 on 2010-12-20
That is why it is a pipe dream.

Having dual boot with a shared data partition (say FAT32) does expose the shared partition to all of Windows penchant for corrupting the partition.

Just setting up dual boot and training your customers how to pick out files from the Windows partition is a good compromise.  With no shared data partiton each OS can function normally, but the user has the option to pull files from Windows into Linux when booted into Linux.  To go the other way, pulling files from the linux partition into Windows requires installing an ext3 plug-in for Windows (don't know how well it works--never used it), or store data in the cloud or on a USB stick then pull it into Windows.  Both would require some hands on training for new users not familiar with dual boot.

---

### Post by chris200x9 on 2010-12-20
> **3Miro said:**
> Create a dual-boot, but both systems should live on separate partitions. Then you can put a link in Linux to Windows home (MyWindowsFiles) and a link in Windows to Linux /home (MyLinuxFiles). This meas installing ext3/4 software under windows, but it should work.



You cannot achieve that. Windows software (including Office) is accessible from Linux only after reboot. That is, download a .docx file, reboot and only then can I open it. Also, the windows part of the system will always be susceptible to windows viruses. There is simply no way of truly getting "the best of both".

couldn't you pre-install openoffice on both partitions? Of course the "best of both worlds" is a half truth, this is marketing isn't it?

> **tgalati4 said:**
> That is why it is a pipe dream.

Having dual boot with a shared data partition (say FAT32) does expose the shared partition to all of Windows penchant for corrupting the partition.

Just setting up dual boot and training your customers how to pick out files from the Windows partition is a good compromise.  With no shared data partiton each OS can function normally, but the user has the option to pull files from Windows into Linux when booted into Linux.  To go the other way, pulling files from the linux partition into Windows requires installing an ext3 plug-in for Windows (don't know how well it works--never used it), or store data in the cloud or on a USB stick then pull it into Windows.  Both would require some hands on training for new users not familiar with dual boot.

my whole thing I guess is why not pre-install an ext2/3/4 driver and then pre-install some open source software on both "root" (which has a small home) partitions that are cross platform. So you can seamlessly open document types created in either. Or can you not pre-install software with an OEM windows install? Lord knows enough crapware gets pre-installed, why not have something useful pre-installed?

Example: audacity comes pre-installed on windows and linux, you save a project to your shared folder/partition, open/change in either.

edit: this whole thing is most likely never going to be a reality, but I was thinking of having these choices: default: dual boot (with an advanced option to choose partition scheme), next option: windows only, next option: linux only, lastly: no os.

---

### Post by warfacegod on 2010-12-21
> **chris200x9 said:**
> 

my whole thing I guess is why not pre-install an ext2/3/4 driver 

If you mean in Windows they do exist but don't work very well, at best. Hence, my first post.

---

### Post by julio_cortez on 2010-12-22
> **chris200x9 said:**
> oh that sucks, next idea why not just have a small native home and a "shared" or "data".That's why I have set up my PC:

Ubuntu 10.04 with its own /home,
Mint 10 'Julia' with its own /home
Windows 7 with its own C:\Users

Then, an additional (large) NTFS data partition on sda which is mounted via fstab in /media/data for both Ubuntu and Mint, and is seen as D:\ in Windows.

If you mind a suggestion, I'd avoid mounting C:\ (in this case, C:\users) in Ubuntu (like it has been said before, NTFS support is there in Ubuntu but it's not proven 100% safe yet).

---

