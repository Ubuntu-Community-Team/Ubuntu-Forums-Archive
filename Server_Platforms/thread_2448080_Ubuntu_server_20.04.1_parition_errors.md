---
title: "Ubuntu server 20.04.1 parition errors"
date: 2020-08-01
forum: Server Platforms
---

### Post by Parth_Maniar on 2020-08-01
HI, I have installed Ubuntu 20.04.1 on VMWare ESXi. It has 2 disks - one HDD of 100 GB and one SSD of 360 GB. I am able to see the SSD correctly.

However, for the HDD I am able to see the following:
```

sda                         8:0    0   100G  0 disk
&#9500;&#9472;sda1                      8:1    0   512M  0 part /boot/efi
&#9500;&#9472;sda2                      8:2    0     1G  0 part /boot
&#9492;&#9472;sda3                      8:3    0  98.5G  0 part
  &#9492;&#9472;ubuntu--vg-ubuntu--lv 253:0    0  49.3G  0 lvm  /

```


I am also getting following errors in syslog:


```
Aug  1 09:33:34 hostname multipathd[799]: sdb: failed to get sgio uid: No such file or directory
Aug  1 09:33:38 hostname multipathd[799]: sda: add missing path
Aug  1 09:33:38 hostname multipathd[799]: sda: failed to get udev uid: Invalid argument
Aug  1 09:33:38 hostname multipathd[799]: sda: failed to get sysfs uid: Invalid argument
Aug  1 09:33:38 hostname multipathd[799]: sda: failed to get sgio uid: No such file or directory
Aug  1 09:33:39 hostname multipathd[799]: sdb: add missing path
Aug  1 09:33:39 hostname multipathd[799]: sdb: failed to get udev uid: Invalid argument
Aug  1 09:33:39 hostname multipathd[799]: sdb: failed to get sysfs uid: Invalid argument
Aug  1 09:33:39 hostname multipathd[799]: sdb: failed to get sgio uid: No such file or directory
Aug  1 09:33:43 hostname multipathd[799]: sda: add missing path
Aug  1 09:33:43 hostname multipathd[799]: sda: failed to get udev uid: Invalid argument
Aug  1 09:33:43 hostname multipathd[799]: sda: failed to get sysfs uid: Invalid argument
Aug  1 09:33:43 hostname multipathd[799]: sda: failed to get sgio uid: No such file or directory
Aug  1 09:33:44 hostname multipathd[799]: sdb: add missing path
Aug  1 09:33:44 hostname multipathd[799]: sdb: failed to get udev uid: Invalid argument
Aug  1 09:33:44 hostname multipathd[799]: sdb: failed to get sysfs uid: Invalid argument
Aug  1 09:33:44 hostname multipathd[799]: sdb: failed to get sgio uid: No such file or directory
Aug  1 09:33:48 hostname multipathd[799]: sda: add missing path
Aug  1 09:33:48 hostname multipathd[799]: sda: failed to get udev uid: Invalid argument
Aug  1 09:33:48 hostname multipathd[799]: sda: failed to get sysfs uid: Invalid argument
Aug  1 09:33:48 hostname multipathd[799]: sda: failed to get sgio uid: No such file or directory
```


What am I doing wrong? How do I resolve this?

Thank you.

---

### Post by darkod on 2020-08-01
It looks like it is complaining about multipath setup or paths. I assume this is related to multipath in VMware where you can have redundancy to reach the datastores through different paths and that way allow the VMs to continue working if one path goes down.

Have you googled those messages from the syslog? Anything interesting in the search results?

On the HDD partition layout I see nothing strange. I don't know if it is what you expected though. You have a EFI partition and what looks like bios_grub partitions. The rest of the 100GB is one single VG which is normal for a guided setup using LVM.

---

### Post by TheFu on 2020-08-01
Which disk controller does the VM present to Ubuntu?  For most VMs today, using the virtio controller is the best choice - fastest and with the lowest overhead.  Alas, we dropped all ESX stuff around 2011 due to VMware management decisions that we and our clients couldn't take, so my VMware knowledge is dated.

BTW, would help to make output more readable if enclosed in "code tags" when posting here.  Especially the **lsblk** and **df -Th** output normally needed to troubleshoot storage stuff.

I've never used efi booting with any virtual machine. For a long time, efi support wasn't very good, so I just never got into the habit.

Looks like [https://bugs.launchpad.net/ubuntu/+source/multipath-tools/+bug/1875594](https://bugs.launchpad.net/ubuntu/+source/multipath-tools/+bug/1875594) is related and there is a proposed fix in a PPA. Post #17 suggests blacklisting the VMware disk drivers - some issue with the VMware SCSI vdisk stuff.

---

### Post by Parth_Maniar on 2020-08-01
> **TheFu said:**
> Which disk controller does the VM present to Ubuntu?  For most VMs today, using the virtio controller is the best choice - fastest and with the lowest overhead.  Alas, we dropped all ESX stuff around 2011 due to VMware management decisions that we and our clients couldn't take, so my VMware knowledge is dated.

BTW, would help to make output more readable if enclosed in "code tags" when posting here.  Especially the **lsblk** and **df -Th** output normally needed to troubleshoot storage stuff.

I've never used efi booting with any virtual machine. For a long time, efi support wasn't very good, so I just never got into the habit.

Looks like [https://bugs.launchpad.net/ubuntu/+source/multipath-tools/+bug/1875594](https://bugs.launchpad.net/ubuntu/+source/multipath-tools/+bug/1875594) is related and there is a proposed fix in a PPA. Post #17 suggests blacklisting the VMware disk drivers - some issue with the VMware SCSI vdisk stuff.

Hi, thank you very much for your reply.

Please find the required logs.

```
NAME                      MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
loop0                       7:0    0   9.1M  1 loop /snap/canonical-livepatch/95
loop1                       7:1    0    15M  1 loop /snap/aws-cli/130
loop2                       7:2    0 118.7M  1 loop /snap/google-cloud-sdk/143
loop3                       7:3    0  59.6M  1 loop /snap/powershell/137
loop4                       7:4    0    55M  1 loop /snap/core18/1880
loop5                       7:5    0  71.3M  1 loop /snap/lxd/16100
loop6                       7:6    0    97M  1 loop /snap/core/9665
loop7                       7:7    0   3.5M  1 loop /snap/stress-ng/4462
loop8                       7:8    0  27.1M  1 loop /snap/snapd/7264
loop9                       7:9    0    55M  1 loop /snap/core18/1705
loop10                      7:10   0    69M  1 loop /snap/lxd/14804
loop11                      7:11   0  29.9M  1 loop /snap/snapd/8542
sda                         8:0    0   100G  0 disk
&#9500;&#9472;sda1                      8:1    0   512M  0 part /boot/efi
&#9500;&#9472;sda2                      8:2    0     1G  0 part /boot
&#9492;&#9472;sda3                      8:3    0  98.5G  0 part
  &#9492;&#9472;ubuntu--vg-ubuntu--lv 253:0    0  49.3G  0 lvm  /
sdb                         8:16   0   360G  0 disk /mnt/ssd

```

and 


```
Filesystem                        Type      Size  Used Avail Use% Mounted on
udev                              devtmpfs  2.9G     0  2.9G   0% /dev
tmpfs                             tmpfs     595M  1.3M  594M   1% /run
/dev/mapper/ubuntu--vg-ubuntu--lv ext4       49G   11G   36G  22% /
tmpfs                             tmpfs     3.0G     0  3.0G   0% /dev/shm
tmpfs                             tmpfs     5.0M     0  5.0M   0% /run/lock
tmpfs                             tmpfs     3.0G     0  3.0G   0% /sys/fs/cgroup
/dev/sdb                          ext4      354G  5.4G  330G   2% /mnt/ssd
/dev/sda2                         ext4      976M  104M  805M  12% /boot
/dev/loop1                        squashfs   15M   15M     0 100% /snap/aws-cli/130
/dev/loop2                        squashfs  119M  119M     0 100% /snap/google-cloud-sdk/143
/dev/loop0                        squashfs  9.2M  9.2M     0 100% /snap/canonical-livepatch/95
/dev/loop3                        squashfs   60M   60M     0 100% /snap/powershell/137
/dev/loop4                        squashfs   55M   55M     0 100% /snap/core18/1880
/dev/loop7                        squashfs  3.7M  3.7M     0 100% /snap/stress-ng/4462
/dev/loop8                        squashfs   28M   28M     0 100% /snap/snapd/7264
/dev/loop11                       squashfs   30M   30M     0 100% /snap/snapd/8542
/dev/sda1                         vfat      511M  7.8M  504M   2% /boot/efi
/dev/loop5                        squashfs   72M   72M     0 100% /snap/lxd/16100
/dev/loop9                        squashfs   55M   55M     0 100% /snap/core18/1705
/dev/loop6                        squashfs   97M   97M     0 100% /snap/core/9665
/dev/loop10                       squashfs   69M   69M     0 100% /snap/lxd/14804
tmpfs                             tmpfs     595M     0  595M   0% /run/user/1000
```


I hope this helps. I am concerned that the disk provisioned is 100 GB but I am only able to see 49 GB for / . I am unsure where the remaining 50 GB is.

---

### Post by TheFu on 2020-08-01
code tags?

Did you follow that link and do what they say?

---

### Post by Parth_Maniar on 2020-08-01
> **darkod said:**
> It looks like it is complaining about multipath setup or paths. I assume this is related to multipath in VMware where you can have redundancy to reach the datastores through different paths and that way allow the VMs to continue working if one path goes down.

Have you googled those messages from the syslog? Anything interesting in the search results?

On the HDD partition layout I see nothing strange. I don't know if it is what you expected though. You have a EFI partition and what looks like bios_grub partitions. The rest of the 100GB is one single VG which is normal for a guided setup using LVM.


Hi, thank you very much for you reply.


 I found 4 threads with same error and I have tried their solutions but in my case the error doesn't stop. I am worried about the logs filling up to be honest. 

[https://askubuntu.com/questions/1242731/ubuntu-20-04-multipath-configuration](https://askubuntu.com/questions/1242731/ubuntu-20-04-multipath-configuration)
[https://ubuntuforums.org/showthread.php?t=2441797](https://ubuntuforums.org/showthread.php?t=2441797)
[https://www.suse.com/support/kb/doc/?id=000016951](https://www.suse.com/support/kb/doc/?id=000016951)
[https://internet-lab.ru/vmware_linux_multipathd_failed_to_get_udev_uid](https://internet-lab.ru/vmware_linux_multipathd_failed_to_get_udev_uid) (russian)


:(

---

### Post by Parth_Maniar on 2020-08-01
> **TheFu said:**
> code tags?

Did you follow that link and do what they say?


Hi, sorry I did not do this yet. Let me do this and reply. Could you tell me how to best deal with expanding the disk size too? In case I need to reboot or take downtime for the VM. Why is the HDD size 50 GB instead of 100 GB?

Thank you.

---

### Post by darkod on 2020-08-01
With LVM you probably have the remaining free space inside the VG but not assigned to any LV yet. If you don't know what LVM is I wouldn't install a production server/VM before reading up on it.

You can see the VG assigned/free space with:
```
sudo vgdisplay
```

When posting output results please include them inside [code] tags like TheFu mentioned already. It keeps the formatting and makes the output easily readable.

---

### Post by TheFu on 2020-08-01
Hopefully, the OP knows all about LVM.  The current commands we like are
```
sudo pvs
sudo vgs
sudo lvs
```

The output from the older lv/vg/pv-display commands is seldom needed unless there is a deep issue.  

The issue here is at a lower level, well below LVM. Unless the OP tried to resize the LV, the first "root" LV should take up the entire VG and PV.  Personally, I think that is a huge mistake and I always resize my root LV to be 25G so it isn't wasted on useless stuff and for security. But everyone is different.  For people really new to Linux and LVM and volume management, non-trivial storage setups are usually fine, until they learn more and *understand* why those are a bad idea.

IMHO.

---

### Post by Parth_Maniar on 2020-08-05
Hi, I apologise for not formatting earlier posts. I have edited the one allowed by the system.

```
  --- Volume group ---
  VG Name               ubuntu-vg
  System ID
  Format                lvm2
  Metadata Areas        1
  Metadata Sequence No  2
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                1
  Open LV               1
  Max PV                0
  Cur PV                1
  Act PV                1
  VG Size               <98.50 GiB
  PE Size               4.00 MiB
  Total PE              25215
  Alloc PE / Size       12608 / 49.25 GiB
  Free  PE / Size       12607 / <49.25 GiB
  VG UUID               ji4eP9-Wal5-BQRo-Qijk-wIIi-LcHt-pqkDej


```


I am not an administrator for Ubuntu and my knowledge is limited when deploying Ubuntu server of ESXi. This is not in production for a company. This is part of my final year project in university where I'm trying to capture logs using ELK stack and map cyberattack patterns around the world. :) 

I have deployed VMs using VMWare workstation and never faced issue even when thin provisioning a disk.

Continuous error logs have stopped after following guide here [https://www.suse.com/support/kb/doc/?id=000016951](https://www.suse.com/support/kb/doc/?id=000016951) and settings within comments here: [https://askubuntu.com/questions/1242731/ubuntu-20-04-multipath-configuration](https://askubuntu.com/questions/1242731/ubuntu-20-04-multipath-configuration)

```
after I added "blacklist { devnode "sda" }"  to /etc/multipath.conf the entries in syslog disapeared. I am still  wondering why multipath is enabled by default.
```

Reboot of the VM is required. 

Thank you for everyone's assistance.

---

### Post by Parth_Maniar on 2020-08-05
Hi thank you for your reply. You are right that during initial installation, I did not pay attention to Ubuntu only formatting 50% of the drive. I did change setting wherein I mounted SSD volume allocated to the VM (since I need IOPs for collection, parsing and analytics.) However that SSD is also thin provisioned but entire 360 GB is visible.

The disk is thin provisioned in ESXi. Is there a way to claim the free space or will I need to rebuild?[B]


sudo pvs
[/B]```

  PV         VG        Fmt  Attr PSize   PFree
  /dev/sda3  ubuntu-vg lvm2 a--  <98.50g <49.25g
```

**sudo vgs**
```
  VG        #PV #LV #SN Attr   VSize   VFree
  ubuntu-vg   1   1   0 wz--n- <98.50g <49.25g
```

**sudo lvs**
```
  LV        VG        Attr       LSize  Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  ubuntu-lv ubuntu-vg -wi-ao---- 49.25g
```

---

### Post by TheFu on 2020-08-05
The output above shows that Ubuntu doesn't know anything about thin provisioning. Appears that during the installation, sda3 only had about 50G, which it used for the PV.  I've never seen that before, but we don't use thin provisioning for VMs, just containers.

If you understand LVM, it looks like resizing the different logical parts should be easy and not need downtime. If it was me, I'd try this:
[LIST=1]
[*]Use pvresize to increase the PV size.
[*]Use vgextend to increase the VG size. (may not be needed; pvresize may automatically vgextend too)
[*]Use lvresize to shrink the current LV to 25G or less - the size depends on how much you want to waste with the OS and file-based swap.
[*]Use lvcreate to make another LV to be used for /home and all data, sized to use the amount needed for the next 3 months.
[/LIST]

Whenever using lvresize or lvcreate, I use the -r option so the file system gets handled automatically. Forget to do that and you'll need another step.

I'd leave at least 20% of the VG free for future needs and to be used for swap.
Never allocate the entire disk to LVs.  We need to leave some space to extend storage where it is needed later, some for snapshots so our backups can be clean, and perhaps some for swap, which it seems the system doesn't have.  Normally, there should be a swap LV on a system like this.
I'm not a fan of using file-based swap. LVs are much cleaner and avoid certain issues.

To give you an idea about different LVM:```

regulus:~$ sudo lvs
  LV     VG            Attr       LSize  Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  root   vgubuntu-mate -wi-ao---- 17.00g                                                    
  home   vgubuntu-mate -wi-ao---- 12.00g                                                    
  swap_1 vgubuntu-mate -wi-ao----  4.10g                                                    
regulus:~$ sudo vgs 
  VG            #PV #LV #SN Attr   VSize  VFree
  vgubuntu-mate   2   3   0 wz--n- 39.49g 6.39g
regulus:~$ sudo pvs
  PV         VG            Fmt  Attr PSize   PFree
  /dev/vda5  vgubuntu-mate lvm2 a--  <29.50g    0 
  /dev/vdb1  vgubuntu-mate lvm2 a--  <10.00g 6.39g
```
That's on my main desktop. I screwed up during the install and only gave the VM 30G because the prior desktop VM was using only 25G total. 20.04 is bloated.  Anyway, I added a new 10G physical disk (as far as the VM was installed knew), vdb. then I made that new disk part of the VG and gave some of the storage to the root LV.
```
regulus:~$ lsblk -e 7 -o name,size,type,fstype,mountpoint
NAME                       SIZE TYPE FSTYPE      MOUNTPOINT
sr0                       1024M rom              
vda                         30G disk             
&#9500;&#9472;vda1                     512M part vfat        /boot/efi
&#9500;&#9472;vda2                       1K part             
&#9492;&#9472;vda5                    29.5G part LVM2_member 
  &#9500;&#9472;vgubuntu--mate-root     17G lvm  ext4        /
  &#9500;&#9472;vgubuntu--mate-swap_1  4.1G lvm  swap        [SWAP]
  &#9492;&#9472;vgubuntu--mate-home     12G lvm  ext4        /home
vdb                         10G disk             
&#9492;&#9472;vdb1                      10G part LVM2_member 
  &#9492;&#9472;vgubuntu--mate-root     17G lvm  ext4        /
```
All this work was done while the VM kept running. No downtime needed.  These were the commands: [https://ubuntuforums.org/showthread.php?t=2444855&p=13963156#post13963156](https://ubuntuforums.org/showthread.php?t=2444855&p=13963156#post13963156)

Notice how I left 6G free?  This gets used for nightly backups as snapshot storage.  At some point in the future, I may clean this up by extending the vda allocation to the VM - really doesn't matter.  On the VM host, vda and vdb are just LVs presented to the VM, regulus, as block devices. See:
```
$ sudo lvs
  LV                VG       Attr       LSize   Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  lv-regulus        hadar-vg -wi-ao----  30.00g                                                    
  lv-regulus-2      hadar-vg -wi-ao----  10.00g           
```

A little "Inception" loop here. Like that movie. ;)

---

### Post by Parth_Maniar on 2020-08-05
> **TheFu said:**
> The output above shows that Ubuntu doesn't know anything about thin provisioning. Appears that during the installation, sda3 only had about 50G, which it used for the PV.  I've never seen that before, but we don't use thin provisioning for VMs, just containers.

If you understand LVM, it looks like resizing the different logical parts should be easy and not need downtime. If it was me, I'd try this:
[LIST=1]
[*]Use pvresize to increase the PV size. 
[*]Use vgextend to increase the VG size. (may not be needed; pvresize may automatically vgextend too) 
[*]Use lvresize to shrink the current LV to 25G or less - the size depends on how much you want to waste with the OS and file-based swap. 
[*]Use lvcreate to make another LV to be used for /home and all data, sized to use the amount needed for the next 3 months. 
[/LIST]

Whenever using lvresize or lvcreate, I use the -r option so the file system gets handled automatically. Forget to do that and you'll need another step.

I'd leave at least 20% of the VG free for future needs and to be used for swap.
Never allocate the entire disk to LVs.  We need to leave some space to extend storage where it is needed later, some for snapshots so our backups can be clean, and perhaps some for swap, which it seems the system doesn't have.  Normally, there should be a swap LV on a system like this.
I'm not a fan of using file-based swap. LVs are much cleaner and avoid certain issues.

To give you an idea about different LVM:```

regulus:~$ sudo lvs
  LV     VG            Attr       LSize  Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  root   vgubuntu-mate -wi-ao---- 17.00g                                                    
  home   vgubuntu-mate -wi-ao---- 12.00g                                                    
  swap_1 vgubuntu-mate -wi-ao----  4.10g                                                    
regulus:~$ sudo vgs 
  VG            #PV #LV #SN Attr   VSize  VFree
  vgubuntu-mate   2   3   0 wz--n- 39.49g 6.39g
regulus:~$ sudo pvs
  PV         VG            Fmt  Attr PSize   PFree
  /dev/vda5  vgubuntu-mate lvm2 a--  <29.50g    0 
  /dev/vdb1  vgubuntu-mate lvm2 a--  <10.00g 6.39g
```
That's on my main desktop. I screwed up during the install and only gave the VM 30G because the prior desktop VM was using only 25G total. 20.04 is bloated.  Anyway, I added a new 10G physical disk (as far as the VM was installed knew), vdb. then I made that new disk part of the VG and gave some of the storage to the root LV.
```
regulus:~$ lsblk -e 7 -o name,size,type,fstype,mountpoint
NAME                       SIZE TYPE FSTYPE      MOUNTPOINT
sr0                       1024M rom              
vda                         30G disk             
&#9500;&#9472;vda1                     512M part vfat        /boot/efi
&#9500;&#9472;vda2                       1K part             
&#9492;&#9472;vda5                    29.5G part LVM2_member 
  &#9500;&#9472;vgubuntu--mate-root     17G lvm  ext4        /
  &#9500;&#9472;vgubuntu--mate-swap_1  4.1G lvm  swap        [SWAP]
  &#9492;&#9472;vgubuntu--mate-home     12G lvm  ext4        /home
vdb                         10G disk             
&#9492;&#9472;vdb1                      10G part LVM2_member 
  &#9492;&#9472;vgubuntu--mate-root     17G lvm  ext4        /
```
All this work was done while the VM kept running. No downtime needed.  These were the commands: [https://ubuntuforums.org/showthread.php?t=2444855&p=13963156#post13963156](https://ubuntuforums.org/showthread.php?t=2444855&p=13963156#post13963156)

Notice how I left 6G free?  This gets used for nightly backups as snapshot storage.  At some point in the future, I may clean this up by extending the vda allocation to the VM - really doesn't matter.  On the VM host, vda and vdb are just LVs presented to the VM, regulus, as block devices. See:
```
$ sudo lvs
  LV                VG       Attr       LSize   Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  lv-regulus        hadar-vg -wi-ao----  30.00g                                                    
  lv-regulus-2      hadar-vg -wi-ao----  10.00g           
```

A little "Inception" loop here. Like that movie. ;)




Thank you very much for the detailed explanation. Given that I am a novice I will need sometime before I go through the commands man pages and carry out the change.

Thank you very much once again.

---

### Post by TheFu on 2020-08-05
If you aren't 100% certain about each command, it is best to create another VM just with tiny LVMs to do the testing.  For testing out LVM commands, it doesn't matter if 100G or 100M are used.

---

### Post by Parth_Maniar on 2020-08-05
I think I have already screwed up.

**lsblk**

```
NAME                      MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
loop0                       7:0    0    15M  1 loop /snap/aws-cli/130
loop1                       7:1    0    97M  1 loop /snap/core/9665
loop2                       7:2    0   9.1M  1 loop /snap/canonical-livepatch/95
loop3                       7:3    0    55M  1 loop /snap/core18/1880
loop4                       7:4    0 118.7M  1 loop /snap/google-cloud-sdk/143
loop5                       7:5    0  71.3M  1 loop /snap/lxd/16100
loop6                       7:6    0  71.5M  1 loop /snap/lxd/16530
loop7                       7:7    0  59.6M  1 loop /snap/powershell/137
loop8                       7:8    0  29.9M  1 loop /snap/snapd/8542
loop9                       7:9    0    55M  1 loop /snap/core18/1705
loop10                      7:10   0  27.1M  1 loop /snap/snapd/7264
loop11                      7:11   0   3.5M  1 loop /snap/stress-ng/4462
loop12                      7:12   0 118.9M  1 loop /snap/google-cloud-sdk/144
sda                         8:0    0   100G  0 disk
&#9500;&#9472;sda1                      8:1    0   512M  0 part /boot/efi
&#9500;&#9472;sda2                      8:2    0     1G  0 part /boot
&#9492;&#9472;sda3                      8:3    0  98.5G  0 part
  &#9492;&#9472;ubuntu--vg-ubuntu--lv 253:0    0  49.3G  0 lvm  /
sdb                         8:16   0   360G  0 disk /mnt/ssd
```



Then I ran:


**pvresize --setphysicalvolumesize 75G /dev/sda3**


```
/dev/sda3: Requested size 75.00 GiB is less than real size <98.50 GiB. Proceed?  [y/n]: y
  WARNING: /dev/sda3: Pretending size is 157286400 not 206565376 sectors.
  Physical volume "/dev/sda3" changed
  1 physical volume(s) resized or updated / 0 physical volume(s) not resized
```


Re-ran

lsblk

```
NAME                      MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
loop0                       7:0    0    15M  1 loop /snap/aws-cli/130
loop1                       7:1    0    97M  1 loop /snap/core/9665
loop2                       7:2    0   9.1M  1 loop /snap/canonical-livepatch/95
loop3                       7:3    0    55M  1 loop /snap/core18/1880
loop4                       7:4    0 118.7M  1 loop /snap/google-cloud-sdk/143
loop5                       7:5    0  71.3M  1 loop /snap/lxd/16100
loop6                       7:6    0  71.5M  1 loop /snap/lxd/16530
loop7                       7:7    0  59.6M  1 loop /snap/powershell/137
loop8                       7:8    0  29.9M  1 loop /snap/snapd/8542
loop9                       7:9    0    55M  1 loop /snap/core18/1705
loop10                      7:10   0  27.1M  1 loop /snap/snapd/7264
loop11                      7:11   0   3.5M  1 loop /snap/stress-ng/4462
loop12                      7:12   0 118.9M  1 loop /snap/google-cloud-sdk/144
sda                         8:0    0   100G  0 disk
&#9500;&#9472;sda1                      8:1    0   512M  0 part /boot/efi
&#9500;&#9472;sda2                      8:2    0     1G  0 part /boot
&#9492;&#9472;sda3                      8:3    0  98.5G  0 part
  &#9492;&#9472;ubuntu--vg-ubuntu--lv 253:0    0  49.3G  0 lvm  /
sdb                         8:16   0   360G  0 disk /mnt/ssd
root@inmum-i-ssslp01:~# pvresize --setphysicalvolumesize 75G /dev/sda3

```


I may need hand holding. I have to submit my last year project and hence the rush.

---

### Post by darkod on 2020-08-05
I don't understand what is happening here and in your place I would STOP, until we clarify few things.

And lets go back to basics, yes/no questions to keep it simple.

1) The root LV according to the first posts here is only 22% full. You don't even need to expand it. I know it has 50GB out of 100GB but that is not an issue. So, do you want to extend root LV to have more than 50GB size? Yes/No? If yes, to which size you want to expand it?

2) I see you tried to shrink the PV using pvresize. Is there a reason you really need to do this?

TheFu gave you a lot of detailed information and he is respected forum contributor but in this case with a LVM novice all that info might be counter-productive. You see, he clearly said "use pvresize to increase PV size" and you tried to shrink your PV. Wihtout detailing a valid reason before doing it. If you continue hacking commands like that without understanding what they do, and without needing to run them at all in the first place, that is an excellent recipe for disaster.

Also, the thin in VMware has no influence. We can talk about that too but I don't see how it is related here. Please elaborate. The thin disks are no different from VM and OS side. They are important from VMware side because using thin you can overprovision your datastore and fill it up and crash it.

If you answer the above questions we can tell you how to extend your root LV in 5mins. But again, it is only 22% full and I don't even see a need to extend it. I think that not knowing what LVM is you just got "scared" seeing you have 50GB instead of the expected 100GB.

---

### Post by TheFu on 2020-08-05
Darknod - 
I think the OP thin provisioned on the VMware side, starting with 50G.  The installation saw that and used 50G for the PV - as seen by the output commands pvs, vgs, lvs, in post #11 above.  Then VMware thin provisioning appears to have resized the storage behind the scenes.  This surprised the OP and it surprised me, but I know thin provisioning can do that, if setup in that manner.

I don't think the pvresize command did anything bad.  Seeing the pvs, vgs, and lvs output again, now, would be useful.

The plain lsblk command isn't as useful as this alias: **alias lsb-no-loop='lsblk -e 7 -o name,size,type,fstype,mountpoint' ** This version doesn't show any loop storage and does show the file systems for each. Not seeing cruft helps for understanding.

---

### Post by darkod on 2020-08-05
> I think the OP thin provisioned on the VMware side, starting with 50G. The installation saw that and used 50G for the PV

I have to disagree on this. The very first post shows lsblk output which clearly states sda as 100GB (in line with having 100GB VHDD in VMware, thin or thick provisioned doesn't matter). And it also states the LV is only 50GB. The latter might be due to selection during installation, or due to the guided LVM method not using 100% of the available disk, not sure.

Anyway, to me it looked pretty clear. 100GB disk with 50GB LV which you can extend if needed. No messing with PV and stuff necessary, not that I can see.

I think the only OP confusion here was seeing 50GB for / after giving the VM a 100GB disk in VMware. Because of not understanding of how LVM works and that you can easily extend the / to 100GB if you wanted.

---

### Post by TheFu on 2020-08-05
How would someone end up with a PV of 50G doing a simple server install with 100G partition?  When I've tried to have a root LV of 25G setup during the installer, I've never been successful. It always takes the entire partition for the PV, VG and root LV. Drives me crazy, but fortunately, for someone experienced, reducing the root LV to the size I want and adding the other LVs in the desired sizes isn't THAT difficult, just a hassle. At install time, really miss the CentOS disk/LVM tools.

Completely unrelated, but this is bad:
```
sdb                         8:16   0   360G  0 disk /mnt/ssd
```

Really, the /dev/sdb disk should have been partitioned, then a file system placed onto that partition ... or better, use LVM, so the storage can be better managed on the ssd with PVs, VGs and LVs.  Normally, people make this mistake with RAID setups.
The diagram here: [https://www.brainupdaters.net/ca/brief-introduction-logical-volumes-lv-concept-example-application/](https://www.brainupdaters.net/ca/brief-introduction-logical-volumes-lv-concept-example-application/) should help understand the relationship between 
[LIST]
[*]whole drives
[*]Partition tables (msdos or GPT)
[*]partitions
[*]PVs
[*]VGs
[*]LVs and 
[*]File systems
[/LIST]
With LVM, we almost always work from the VG, LV and file system levels after a disk is added to a system. LVM is more complex, but provides crazy flexibility, especially for storage that will be used over multiple years.

But new-to-Unix users are seldom ready for LVM's complexities/capabilities and are often better off NOT using LVM.

---

### Post by darkod on 2020-08-05
> How would someone end up with a PV of 50G doing a simple server install with 100G partition?

That is the thing bugging me. But since I still haven't done a new clean install of 20.04 my first assumption was that the installer "helps" you by not using the whole VG for only one LV right from the start.

I have used plenty thin disks in VMware and that shouldn't have created this situation because from VM and OS side, the disk is seen as whole 100GB size. The only difference is on VMware side where thick disk would grab the whole 100GB right away, while a thin disk would only use amount of space in the datastore related to how full the disk is in the OS. And with the usage in the OS growing, the VHDD file in the datastore grows too up to 100GB.

But anyway going into too much VMware details can also add to confusion here. :)

---

### Post by TheFu on 2020-08-05
> **darkod said:**
> That is the thing bugging me. But since I still haven't done a new clean install of 20.04 my first assumption was that the installer "helps" you by not using the whole VG for only one LV right from the start.

I have used plenty thin disks in VMware and that shouldn't have created this situation because from VM and OS side, the disk is seen as whole 100GB size. The only difference is on VMware side where thick disk would grab the whole 100GB right away, while a thin disk would only use amount of space in the datastore related to how full the disk is in the OS. And with the usage in the OS growing, the VHDD file in the datastore grows too up to 100GB.

But anyway going into too much VMware details can also add to confusion here. :)

I've done an LVM install of 20.04 into a VM.  It still takes the entire partition. Guess we have 2 possible answer for what happened to the OP's VM. Can't wait to learn what the truth is.

---

### Post by Parth_Maniar on 2020-08-06
Hello @Darkod and @TheFu, sorry I was asleep when you both were discussing. I have created a new VM and the same problem persists. Following are the details:

[FONT=&amp]I am using ESXi 7.0b Dell customised image with updated custom network drivers (Intel l219.) Base (host) system hardware has 2 disks - 1 HDD and 1 SSD.


ESXi storage configuration:

[IMG]http://users.ox.ac.uk/~kell4724/Ubuntu_prod.png[/IMG]


1. I updated the installer during installation. (I am using 20.04 ISO from Ubuntu.com which I have verified using file hash.)

[IMG]http://users.ox.ac.uk/~kell4724/Ubuntu_2.png[/IMG]



2. [/FONT][FONT=&amp][FONT=&amp]I selected entire disk during installation:


[IMG]http://users.ox.ac.uk/~kell4724/Ubuntu_3.png[/IMG]



3. Following screen shows / partition as being 49 GB as opposed to 100 GB.

[IMG]http://users.ox.ac.uk/~kell4724/Ubuntu_4.png[/IMG]



4. Following are the changes I made and the final settings that i used.

[IMG]http://users.ox.ac.uk/~kell4724/Ubuntu_5.png[/IMG]



[IMG]http://users.ox.ac.uk/~kell4724/Ubuntu_6.png[/IMG]


I hope this helps. [/FONT]

I am using UFI with secureboot during VM creation, just in case that matters.


[/FONT]

---

### Post by darkod on 2020-08-06
Well, it does look to me like the new installer is trying to leave you some free space in the VG so it creates the root LV only to take 50%. Like I said, this is not an issue. On the contrary, it is good.

About sdb you are still making the same mistake TheFu mentioned. And the installer is warning you about it too. You are selecting the disk to be mounted at /mnt/ssd. You should first create partition on it (which will be /dev/sdb1) and then use that to mount at /mnt/ssd.

But the secondary disk you can ignore during installation. It would be much easier to do that later once you have the VM running. Assuming you know at least the basics about disk management and mounting in ubuntu.

---

### Post by Parth_Maniar on 2020-08-06
> **darkod said:**
> Well, it does look to me like the new installer is trying to leave you some free space in the VG so it creates the root LV only to take 50%. Like I said, this is not an issue. On the contrary, it is good.

About sdb you are still making the same mistake TheFu mentioned. And the installer is warning you about it too. You are selecting the disk to be mounted at /mnt/ssd. You should first create partition on it (which will be /dev/sdb1) and then use that to mount at /mnt/ssd.

But the secondary disk you can ignore during installation. It would be much easier to do that later once you have the VM running. Assuming you know at least the basics about disk management and mounting in ubuntu.

Hi, I am aware of basic formatting & mounting of the disk. [B]Would you recommend rebuilding the VM, as in can the current configuration cause problems later on? 

[/B]
Thank you for your guidance.

PS: I did not create a new VM but just took printscreens to see what happens. :)

---

### Post by darkod on 2020-08-06
Actually right now I don't see big problems here, to need rebuild.

However, I would like to see how the PV is right now after you tried to shrink it with pvresize. I like the older type commands even though TheFu doesn't like them :)
```
sudo pvdisplay
sudo vgdisplay
sudo lvdisplay
```

That will give you good info about all three components of LVM. I want to see if the PV now is 75GB or 100GB. And subsequently how is the VG.

And for sdb if you still don't have any data on it, I would unmount it, create new msdos or gpt table on it (that will destroy the current ext4 formatting on sdb), then create one new partition sdb1 and then format that partition as ext4. After that you mount and use that partition. If you need help with commands about this part, let us know.

---

### Post by Parth_Maniar on 2020-08-06
> **darkod said:**
> Actually right now I don't see big problems here, to need rebuild.

However, I would like to see how the PV is right now after you tried to shrink it with pvresize. I like the older type commands even though TheFu doesn't like them :)
```
sudo pvdisplay
sudo vgdisplay
sudo lvdisplay
```

That will give you good info about all three components of LVM. I want to see if the PV now is 75GB or 100GB. And subsequently how is the VG.

And for sdb if you still don't have any data on it, I would unmount it, create new msdos or gpt table on it (that will destroy the current ext4 formatting on sdb), then create one new partition sdb1 and then format that partition as ext4. After that you mount and use that partition. If you need help with commands about this part, let us know.




Hi Please find the output:

[B]sudo pvdisplay
[/B]```
  --- Physical volume ---
  PV Name               /dev/sda3
  VG Name               ubuntu-vg
  PV Size               <98.40 GiB / not usable 410.00 KiB
  Allocatable           yes
  PE Size               4.00 MiB
  Total PE              25190
  Free PE               12582
  Allocated PE          12608
  PV UUID               dzJeHH-oEOD-6Wfi-2QzN-1Jsk-mblK-rEbqRD

```
[B]
sudo vgdisplay
[/B]
```
  --- Volume group ---
  VG Name               ubuntu-vg
  System ID
  Format                lvm2
  Metadata Areas        1
  Metadata Sequence No  5
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                1
  Open LV               1
  Max PV                0
  Cur PV                1
  Act PV                1
  VG Size               <98.40 GiB
  PE Size               4.00 MiB
  Total PE              25190
  Alloc PE / Size       12608 / 49.25 GiB
  Free  PE / Size       12582 / <49.15 GiB
  VG UUID               ji4eP9-Wal5-BQRo-Qijk-wIIi-LcHt-pqkDej

```
[B]
sudo lvdisplay
[/B]```
  --- Logical volume ---
  LV Path                /dev/ubuntu-vg/ubuntu-lv
  LV Name                ubuntu-lv
  VG Name                ubuntu-vg
  LV UUID                BEhVeI-mjth-dMLm-4s2f-08NX-hpAh-dSnqTa
  LV Write Access        read/write
  LV Creation host, time ubuntu-server, 2020-07-31 21:19:28 +0000
  LV Status              available
  # open                 1
  LV Size                49.25 GiB
  Current LE             12608
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           253:0

```


The SSD has data but I can take 2 days off work and rebuild the system. This is part of my final year project and will be ingesting data at around 2 GB/day. If you do forsee problems do let me know. I want to get a distinction :) :D

---

### Post by darkod on 2020-08-06
OK, the LVM part looks good. Both the PV and the VG are 100GB, and the LV is 50GB.

If you wanna practice how easy it is to add more space to root LV lets make it exactly 55GB:
```
sudo lvextend -L +5.75G /dev/ubuntu-vg/ubuntu-lv
```

That will make it go from 49.25 to 55.00GB.

But that only extends the LV. The filesystem size you adjust with:
```
sudo resize2fs /dev/ubuntu-vg/ubuntu-lv
```

Now you have root of 55GB.

I would rearrange sdb. Without rebuilding the whole system. But you would need to temporarily move the data from sdb unless you have a backup or second location with that data. Because rearranging sdb will destroy the data currently on it.

---

### Post by TheFu on 2020-08-06
Or to it in 1 command:
```
sudo lvextend **-r** -L +5.75G /dev/ubuntu-vg/ubuntu-lv
```
That will handle the resize2fs for us with just 1 added switch.

Guess we will never know how the first time only saw a 50G PV.
I do like that the root LV is not using all the storage.

If you use LVM for the OS, why not use it for the data SSD too? Is there a reason?

BTW, I've not performed an install using the 20.04.1 installers, yet.

---

