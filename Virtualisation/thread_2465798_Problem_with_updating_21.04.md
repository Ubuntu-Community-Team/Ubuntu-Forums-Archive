---
title: "Problem with updating 21.04"
date: 2021-08-11
forum: Virtualisation
---

### Post by xbingx on 2021-08-11
Hello, I've been running 21.04 for 5 or 6 weeks and finally did an 'apt update' and 'apt upgrade' today...

Unfortunately I see some errors around initramfs at the end of the process and now I'm worried about restarting the server.

 This is running with ZFS as a Proxmox VM with a qcow2 virtual disk (if that matters.) 

Let me know if you need any further details, glad to provide them. Here  are the last snippets of the process, I can add more if needed. Thanks.

```
...
Setting up zfsutils-linux (2.0.2-1ubuntu5.1) ...
zfs-import-scan.service is a disabled or a static unit, not starting it.
Setting up libegl-mesa0:amd64 (21.0.3-0ubuntu0.2) ...
Setting up zfs-initramfs (2.0.2-1ubuntu5.1) ...
Setting up libglx-mesa0:amd64 (21.0.3-0ubuntu0.2) ...
Setting up zfs-zed (2.0.2-1ubuntu5.1) ...
Processing triggers for mailcap (3.68ubuntu1) ...
Processing triggers for fontconfig (2.13.1-4.2ubuntu3) ...
Processing triggers for desktop-file-utils (0.26-1ubuntu1) ...
Processing triggers for initramfs-tools (0.139ubuntu3) ...
update-initramfs: Generating /boot/initrd.img-5.11.0-25-generic
I: The initramfs will attempt to resume from /dev/sda3
I: (UUID=d333af31-1b7b-47ac-befe-5076439d4ba)
I: Set the RESUME variable to override this.
Error 24 : Write error : cannot write compressed block 
E: mkinitramfs failure cpio 141 lz4 -9 -l 24
update-initramfs: failed for /boot/initrd.img-5.11.0-25-generic with 1.
dpkg: error processing package initramfs-tools (--configure):
 installed initramfs-tools package post-installation script subprocess returned error exit status 1
Processing triggers for hicolor-icon-theme (0.17-2) ...
Processing triggers for gnome-menus (3.36.0-1ubuntu1) ...
Processing triggers for libglib2.0-0:amd64 (2.68.1-1~ubuntu21.04.1) ...
Processing triggers for libc-bin (2.33-0ubuntu5) ...
Processing triggers for man-db (2.9.4-2) ...
Processing triggers for dbus (1.12.20-1ubuntu3) ...
Setting up libedataserver-1.2-26:amd64 (3.40.0-1ubuntu1.1) ...
Setting up libecal-2.0-1:amd64 (3.40.0-1ubuntu1.1) ...
Setting up libebook-contacts-1.2-3:amd64 (3.40.0-1ubuntu1.1) ...
Setting up libedataserverui-1.2-3:amd64 (3.40.0-1ubuntu1.1) ...
Setting up gnome-settings-daemon (3.38.1-3ubuntu3.1) ...
Setting up libebackend-1.2-10:amd64 (3.40.0-1ubuntu1.1) ...
Setting up libedata-cal-2.0-1:amd64 (3.40.0-1ubuntu1.1) ...
Setting up libedata-book-1.2-26:amd64 (3.40.0-1ubuntu1.1) ...
Setting up libebook-1.2-20:amd64 (3.40.0-1ubuntu1.1) ...
Setting up evolution-data-server (3.40.0-1ubuntu1.1) ...
Setting up gnome-shell (3.38.4-1ubuntu3~21.04.1) ...
Setting up update-notifier (3.192.40.3) ...
Setting up gnome-shell-extension-prefs (3.38.4-1ubuntu3~21.04.1) ...
Processing triggers for libc-bin (2.33-0ubuntu5) ...
Errors were encountered while processing:
 initramfs-tools
ZSys is adding automatic system snapshot to GRUB menu
E: Sub-process /usr/bin/dpkg returned an error code (1)
(end)

```

---

### Post by QIII on 2021-08-11
Moved to Virtualisation.

---

### Post by xbingx on 2021-08-11
Ok, after a lot of googling I think the problem is a full /boot partition.

First path I went down was cleaning up old kernels, but I only have two installed...
[URL="https://help.ubuntu.com/community/RemoveOldKernels"]https://help.ubuntu.com/community/RemoveOldKernels

[/URL]```
root@xxh:~# dpkg -l | tail -n +6 | grep -E 'linux-image-[0-9]+'
rc  linux-image-5.11.0-16-generic              5.11.0-16.17              amd64              Signed kernel image generic
rc  linux-image-5.11.0-18-generic              5.11.0-18.19              amd64              Signed kernel image generic
ii  linux-image-5.11.0-22-generic              5.11.0-22.23              amd64              Signed kernel image generic
ii  linux-image-5.11.0-25-generic              5.11.0-25.27              amd64              Signed kernel image generic

  
```
Second  path was figuring a combination of the installer creating a much  too  small /boot partition by default and zsys creating too many boot   snapshots by default.
[https://github.com/ubuntu/zsys/issues/155](https://github.com/ubuntu/zsys/issues/155)

```

root@xxh:~# df -h
Filesystem                                        Size  Used Avail Use% Mounted on
bpool/BOOT/ubuntu_b0qbet                          280M  242M   39M  87% /boot
/dev/sda2                                         512M   16M  497M   4% /boot/efi
...

```

```

root@xxh:~# du -h /boot
2.5M    /boot/grub/i386-pc
2.3M    /boot/grub/fonts
3.4M    /boot/grub/x86_64-efi
11M     /boot/grub
2.5M    /boot/efi/grub/i386-pc
2.3M    /boot/efi/grub/fonts
3.4M    /boot/efi/grub/x86_64-efi
11M     /boot/efi/grub
3.4M    /boot/efi/EFI/ubuntu
1.9M    /boot/efi/EFI/BOOT
5.3M    /boot/efi/EFI
16M     /boot/efi
268M    /boot


```

```
root@xxh:~# fdisk -l /dev/sda
Disk /dev/sda: 125 GiB, 134217728000 bytes, 262144000 sectors
Disk model: QEMU HARDDISK   
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 874D579B-A4D9-4435-BDBC-E873E058ADFE

Device       Start       End   Sectors   Size Type
/dev/sda1     2048      4095      2048     1M BIOS boot
/dev/sda2     4096   1054719   1050624   513M EFI System
/dev/sda3  1054720   2945023   1890304   923M Linux swap
/dev/sda4  2945024   4988927   2043904  ** 998M Solaris boot**
/dev/sda5  4988928 261718750 256729823 122.4G Solaris root


```
```

root@xxh:~# zfs list 
NAME                                               USED  AVAIL     REFER  MOUNTPOINT
bpool                                              793M  38.5M       96K  /boot
bpool/BOOT                                         790M  38.5M       96K  none
bpool/BOOT/ubuntu_b0qbet                           790M  38.5M      241M  /boot
...

```

```

root@xxh:~# zfs list -t all -r bpool -o space,creation
NAME                                      AVAIL   USED  USEDSNAP  USEDDS  USEDREFRESERV  USEDCHILD  CREATION
bpool                                     38.5M   793M        0B     96K             0B       793M  Tue Jun  1 13:35 2021
bpool/BOOT                                38.5M   790M        0B     96K             0B       790M  Tue Jun  1 13:35 2021
bpool/BOOT/ubuntu_b0qbet                  38.5M   790M      **549M**    241M             0B         0B  Tue Jun  1 13:35 2021
bpool/BOOT/ubuntu_b0qbet@autozsys_jkr5cz      -    56K         -       -              -          -  Wed Jun  2 16:42 2021
bpool/BOOT/ubuntu_b0qbet@autozsys_vgaman      -     8K         -       -              -          -  Wed Jun  2 16:46 2021
bpool/BOOT/ubuntu_b0qbet@autozsys_piwclj      -     8K         -       -              -          -  Thu Jun  3  6:25 2021
bpool/BOOT/ubuntu_b0qbet@autozsys_01udkk      -    64K         -       -              -          -  Sat Jun  5 18:04 2021
bpool/BOOT/ubuntu_b0qbet@autozsys_jh63cm      -    48K         -       -              -          -  Sun Jun  6 11:34 2021
bpool/BOOT/ubuntu_b0qbet@autozsys_4i8obj      -    56K         -       -              -          -  Tue Jun  8  6:45 2021
bpool/BOOT/ubuntu_b0qbet@autozsys_lj631p      -    72K         -       -              -          -  Thu Jun 10  6:05 2021
bpool/BOOT/ubuntu_b0qbet@autozsys_ykd4ub      -     8K         -       -              -          -  Sat Jun 12 10:36 2021
bpool/BOOT/ubuntu_b0qbet@autozsys_ocpwcl      -     8K         -       -              -          -  Sat Jun 12 20:50 2021
bpool/BOOT/ubuntu_b0qbet@autozsys_ut3emy      -    56K         -       -              -          -  Sun Jun 13 18:02 2021
bpool/BOOT/ubuntu_b0qbet@autozsys_f1wse7      -    48K         -       -              -          -  Sun Jun 13 21:34 2021
bpool/BOOT/ubuntu_b0qbet@MySystemSave         -     0B         -       -              -          -  Mon Jun 14 12:58 2021
bpool/BOOT/ubuntu_b0qbet@autozsys_y3o9vy      -     0B         -       -              -          -  Thu Jun 17  6:13 2021
bpool/BOOT/ubuntu_b0qbet@autozsys_5gvr43      -    80K         -       -              -          -  Fri Jun 18  6:28 2021
bpool/BOOT/ubuntu_b0qbet@autozsys_34v890      -    80K         -       -              -          -  Wed Jun 23  6:46 2021
bpool/BOOT/ubuntu_b0qbet@autozsys_zlh40i      -    64K         -       -              -          -  Tue Jun 29  6:57 2021
bpool/BOOT/ubuntu_b0qbet@autozsys_en9a8m      -    64K         -       -              -          -  Fri Jul  2  3:10 2021
bpool/BOOT/ubuntu_b0qbet@autozsys_n5axu2      -    72K         -       -              -          -  Thu Jul  8  6:27 2021
bpool/BOOT/ubuntu_b0qbet@autozsys_lglvhi      -    72K         -       -              -          -  Fri Jul 16  6:39 2021
bpool/BOOT/ubuntu_b0qbet@autozsys_nx9b9a      -    72K         -       -              -          -  Fri Jul 16 20:56 2021


```

I don't understand enough yet to know if the system will reboot Ok in the current state. How can I check this?

So I made a live snapshot backup of the VM in Proxmox (why didn't I do this before upgrading is a very good question.)

I think my solution is to delete the old boot snapshots until there's some free space.

After that I don't know...

Just reboot

or... run 'update-initramfs' (to finalize the steps that 'apt upgrade' error'd on?) and then reboot

or... run some combination of the following commands and then reboot
'apt -f install' (to clean up the upgrade?)
'apt autoremove' (to free-up any additional space that's available?)
'update-initramfs' (to finalize the steps that 'apt upgrade' error'd on?)

Found the above in various posts around the internet on this sort of topic, but not sure which steps are needed at this point. Thanks.

---

### Post by CharlesA on 2021-08-12
Thanks for that. I've run into that with my install of proxmox. I think it's got like a 1GB /boot partition that fills up quite fast.

Please be sure to mark the thread as [SOLVED] from the Thread Tools menu.

---

### Post by xbingx on 2021-08-13
Got this resolved...

I had to delete more than a few boot snapshots to make any room.

Once I got some space free I ran update-initramfs but it required options that I wasn't sure of. I was tempted to use the "-k all" option but...

I then ran 'apt autoremove' and it ran update-initramfs as part of it's process.

```
root@xxh:~# apt autoremove
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following packages will be REMOVED:
  libllvm11
0 upgraded, 0 newly installed, 1 to remove and 6 not upgraded.
1 not fully installed or removed.
After this operation, 83.4 MB disk space will be freed.
Do you want to continue? [Y/n] y
Requesting to save current system state
ERROR couldn't save system state: Minimum free space to take a snapshot and preserve ZFS performance is 20%.
Free space on pool "rpool" is 16%.
Please remove some states manually to free up space. 
(Reading database ... 185361 files and directories currently installed.)
Removing libllvm11:amd64 (1:11.0.1-2ubuntu4) ...
Setting up initramfs-tools (0.139ubuntu3) ...
update-initramfs: deferring update (trigger activated)
Processing triggers for libc-bin (2.33-0ubuntu5) ...
Processing triggers for initramfs-tools (0.139ubuntu3) ...
update-initramfs: Generating /boot/initrd.img-5.11.0-25-generic
I: The initramfs will attempt to resume from /dev/sda3
I: (UUID=d333af31-1b7b-47ac-befe-5076439d4ba)
I: Set the RESUME variable to override this.
ZSys is adding automatic system snapshot to GRUB menu
```

After that I rebooted without issue.

At some point I will move/resize the boot & root partitions to make more room. I think I'll need to boot off a gparted thumb drive (or similar) to move the partitions.

 [https://gparted.org/livecd.php](https://gparted.org/livecd.php)

I have already extended the root pool/partition in the past with this VM (again, because of zsys' snapshots taking up so much space so often.) For resizing a ZFS pool on a single VM disk this works (as long as it's the last partition on the disk):
[https://www.kringles.org/linux/zfs/vmware/2015/02/10/linux-zfs-resize.html](https://www.kringles.org/linux/zfs/vmware/2015/02/10/linux-zfs-resize.html)

---

