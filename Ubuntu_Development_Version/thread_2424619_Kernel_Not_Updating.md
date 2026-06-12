---
title: "Kernel Not Updating"
date: 2019-08-12
forum: Ubuntu Development Version
---

### Post by PJs Ronin on 2019-08-12
I run a couple of Ubuntu partitions, one is an LTS with Bionic and the other is a 'development' install currently on Eoan ('cloned' from my Bionic install), both with xfce as the DE.   I don't use the Eoan partition a lot; just continue to update and watch for breakage. Eoan is progressing smoothly so I haven't really paid attention till today when I noticed that the kernel appears stuck on 5.0.0-13.
```
wayne@x-core:~$ dpkg --get-selections | grep linux-image
linux-image-5.0.0-13-generic            deinstall
linux-image-5.2.0-10-generic            install
linux-image-5.2.0-8-generic            install
linux-image-generic                install
wayne@x-core:~$ uname -r
5.0.0-13-generic
wayne@x-core:~$ 
```I haven't posted this in the 'Ubuntu Development Version' support forum as I really don't think this is an Eoan problem.   I'd appreciate some advice on how to get things moving to update the kernel.

Regards

---

### Post by Bashing-om on 2019-08-12
PJs Ronin; Hey hey :)

Show us:
```

dpkg -l | grep linux-

```
see here about "linux-image-generic" 

[INDENT][INDENT]or else
[/INDENT][/INDENT]

---

### Post by PJs Ronin on 2019-08-12
Greeting Sir, and thanks for the assist, although there appears to be some missing links in your post :)

As requested, ```
ii  binutils-x86-64-linux-gnu            2.32.51.20190727-1ubuntu1         amd64        GNU binary utilities, for x86-64-linux-gnu target
ii  linux-base                           4.5ubuntu2                        all          Linux image base package
ii  linux-firmware                       1.181                             all          Firmware for Linux kernel drivers
ii  linux-generic                        5.2.0.10.11                       amd64        Complete Generic Linux kernel and headers
ii  linux-headers-5.0.0-13               5.0.0-13.14                       all          Header files related to Linux kernel version 5.0.0
ii  linux-headers-5.0.0-13-generic       5.0.0-13.14                       amd64        Linux kernel headers for version 5.0.0 on 64 bit x86 SMP
ii  linux-headers-5.2.0-10               5.2.0-10.11                       all          Header files related to Linux kernel version 5.2.0
ii  linux-headers-5.2.0-10-generic       5.2.0-10.11                       amd64        Linux kernel headers for version 5.2.0 on 64 bit x86 SMP
ii  linux-headers-5.2.0-8                5.2.0-8.9                         all          Header files related to Linux kernel version 5.2.0
ii  linux-headers-5.2.0-8-generic        5.2.0-8.9                         amd64        Linux kernel headers for version 5.2.0 on 64 bit x86 SMP
ii  linux-headers-generic                5.2.0.10.11                       amd64        Generic Linux kernel headers
rF  linux-image-5.0.0-13-generic         5.0.0-13.14                       amd64        Signed kernel image generic
ii  linux-image-5.2.0-10-generic         5.2.0-10.11                       amd64        Signed kernel image generic
ii  linux-image-5.2.0-8-generic          5.2.0-8.9                         amd64        Signed kernel image generic
ii  linux-image-generic                  5.2.0.10.11                       amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                 5.2.0-10.11                       amd64        Linux Kernel Headers for development
ii  linux-modules-4.15.0-20-generic      4.15.0-20.21                      amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
ii  linux-modules-4.15.0-24-generic      4.15.0-24.26                      amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
ii  linux-modules-4.15.0-29-generic      4.15.0-29.31                      amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
ii  linux-modules-4.15.0-30-generic      4.15.0-30.32                      amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
ii  linux-modules-4.15.0-32-generic      4.15.0-32.35                      amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
ii  linux-modules-4.15.0-36-generic      4.15.0-36.39                      amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
ii  linux-modules-5.0.0-13-generic       5.0.0-13.14                       amd64        Linux kernel extra modules for version 5.0.0 on 64 bit x86 SMP
ii  linux-modules-5.2.0-10-generic       5.2.0-10.11                       amd64        Linux kernel extra modules for version 5.2.0 on 64 bit x86 SMP
ii  linux-modules-5.2.0-8-generic        5.2.0-8.9                         amd64        Linux kernel extra modules for version 5.2.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.0.0-13-generic 5.0.0-13.14                       amd64        Linux kernel extra modules for version 5.0.0 on 64 bit x86 SMP
ii  linux-modules-extra-5.2.0-10-generic 5.2.0-10.11                       amd64        Linux kernel extra modules for version 5.2.0 on 64 bit x86 SMP
ii  linux-modules-extra-5.2.0-8-generic  5.2.0-8.9                         amd64        Linux kernel extra modules for version 5.2.0 on 64 bit x86 SMP
ii  linux-sound-base                     1.0.25+dfsg-0ubuntu5              all          base package for ALSA and OSS sound systems
```
Can I safely assume my kernel mess is more substantial than originally thought?

Regards

---

### Post by cruzer001 on 2019-08-12
I think your /boot is full. 
```
df -h
```
Should confirm that.

---

### Post by PJs Ronin on 2019-08-12
Greetings cruzer,```

wayne@x-core:/boot$ df -h
Filesystem                    Size  Used Avail Use% Mounted on
udev                          7.8G     0  7.8G   0% /dev
tmpfs                         1.6G  1.2M  1.6G   1% /run
/dev/sda8                     9.6G  6.9G  2.3G  76% /
tmpfs                         7.9G     0  7.9G   0% /dev/shm
tmpfs                         5.0M     0  5.0M   0% /run/lock
tmpfs                         7.9G     0  7.9G   0% /sys/fs/cgroup
/dev/sdc1                     3.6T  2.2T  1.3T  65% /media/data
/dev/mapper/lvmbackup-backup  3.6T  2.2T  1.3T  64% /media/backup
tmpfs                         1.6G   20K  1.6G   1% /run/user/1000
wayne@x-core:/boot$
```All my partitions (2 x Arch and 2 x Ubu) are about the same size (10gb) and run the same DE's and packages.   The 'consumption' of space on the Eoan is about 250mb greater than my Bionic partition but not at such a level that has caused concern in the past on any partition.

Regards

---

### Post by cruzer001 on 2019-08-12
Have you tried manually installing the the latest kernel.  Are the kernel metapacks still installed?  I would remove them if they are not.

linux-generic
linux-headers-generic
linux-image-generic

These packages update the 4.15 kernel and not used with the 5.xx.

---

### Post by PJs Ronin on 2019-08-12
> **cruzer001 said:**
> Have you tried manually installing the the latest kernel.  Are the kernel metapacks still installed?  I would remove them if they are not.

linux-generic
linux-headers-generic
linux-image-generic

These packages update the 4.15 kernel and not used with the 5.xx.

a.   Am currently researching how to manually install the latest kernel, not having much luck.
b.   Metapacks?   Not sure, how would I find out?

Just had a look at the Ubuntu mainline kernel site and there does not appear to be a 5.2.0-10 even though my system appears to have tried to install it.

---

### Post by QIII on 2019-08-12
What makes you think that this is not Eoan?

Moved to development version.

When was the last time you fully shut down your Eoan partition and fully rebooted it?  Which distro is on the default boot device?  Have you updated GRUB from there?

It appears that get-selections is identifying more recent kernels to reinstall.

---

### Post by PJs Ronin on 2019-08-12
> **QIII said:**
> What makes you think that this is not Eoan?

Moved to development version.

When was the last time you fully shut down your Eoan partition and fully rebooted it?  Which distro is on the default boot device?  Have you updated GRUB from there?

It appears that get-selections is identifying more recent kernels to reinstall.

Ty QIII

a.  'gut feel'... is that a legitimate reason?   I guess because Eoan has not presented any problems for me and I do recall it updating the kernel early on in the piece.   Perhaps I'm a tad naive.

b.   I always reboot Eoan after updating to test all is ok (couple of times a week) and may not open it again for a couple of days.   It's not a VM, it's on metal.

c/d.   The default boot device is my sda6 which is a rolling Arch distro.   The GRUB is updated from a Bionic partition and based on cavsfan's wonder grub (my name for it).   Grub was updated about 4 days ago, iirc... I shall hasten to update and report back.

For info:
sda5 - Arch LTS
sda6 - Arch rolling - default boot partition
sda7 - Bionic - grub updated from here
sda8 - Eoan

Regards

Edit:
updated GRUB from the Bionic partition... no problem.   Rebooted into Eoan```
wayne@x-core:~$ dpkg --get-selections | grep linux-image
linux-image-5.0.0-13-generic            install
linux-image-5.2.0-10-generic            install
linux-image-5.2.0-8-generic            install
linux-image-generic                install
wayne@x-core:~$ 
```

---

### Post by deadflowr on 2019-08-12
> The GRUB is updated from a Bionic partition and based on cavsfan's wonder grub 
I noticed they've changed the symlinks from the root to boot.
Now there /boot/vmlinuz and /boot/initrd.img which link to the latest kernel.
(Instead of the old /vmlinuz and /initrd.img symlinks)

So /boot/vmlinuz should be linked to /boot/vmlinuz-5.2.0-10-generic
and /boot/initrd.img linked to /boot/initrd.img-5.2.0-10-generic.

So just edit your custom grub files to reflect that change.

---

### Post by PJs Ronin on 2019-08-12
> **deadflowr said:**
> I noticed they've changed the symlinks from the root to boot.
<snip> 
So just edit your custom grub files to reflect that change.
Bingo!   Ty deadflower.   As can be seen in the screenshot I'm now booting off the 5.2.0-10 kernel, although the nVidia graphics system has taken a pounding but that's normal.

Thanks to all who offered advice.   Now, my next task is to remember how to mark a thread as 'solved'.

---

