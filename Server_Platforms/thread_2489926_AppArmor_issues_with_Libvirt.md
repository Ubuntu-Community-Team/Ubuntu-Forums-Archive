---
title: "AppArmor issues with Libvirt"
date: 2023-08-15
forum: Server Platforms
---

### Post by johannes1985 on 2023-08-15
I have a fresh Ubuntu Server 22.04.3 and Debian 12.1.0 installed and updated. Along with Cockpit and Cockpit virtual machines on both tests machines.


I am getting the following errors and warning when looking at the log section in Cockpit:




```
Failed to read AppArmor profiles list '/sys/kernel/security/apparmor/profiles': Permission denied libvirtd






Failed to open file '/sys/kernel/security/apparmor/profiles': Permission denied libvirtd






Failed to read AppArmor profiles list '/sys/kernel/security/apparmor/profiles': Permission denied libvirtd






Failed to open file '/sys/kernel/security/apparmor/profiles': Permission denied libvirtd
```






The virtual machines start up and has no issues. However, the errors pop up after every reboot once I click the virtual machines section on Cockpit. These errors only show then, and not when I do NOT go to virtual machines section in Cockpit. So it seems to only start once you go to that section in Cockpit.


The /etc/apparmor.d/usr.sbin.libvirtd does have the line:


```

/sys/kernel/security/apparmor/profiles r,

```


My user has also been added to groups libvirt, kvm and sudo.


Also, when running the following command without sudo and not as root on the terminal, then I also get a permission denied. I checked the folder permissions and it does have read permissions and belong to the group root:


```

cat /sys/kernel/security/apparmor/profiles

```


Has anyone else experience this issue? Any solution to get it fixed with or without disabling AppArmor for KVM? or can the errors be safely ignored?




Thank you to the person who has a solution to this.

---

### Post by MAFoElffen on 2023-08-15
You also asked here: [https://askubuntu.com/questions/1482332/apparmor-issues-with-libvirt](https://askubuntu.com/questions/1482332/apparmor-issues-with-libvirt)

You have both Debian and Ubuntu Server installed how? On the same machine as dualboot? And then, where are the VM domains stored between the OS'es? And you are using cockpit on which OS installation, accessing VM Domains to where?

When you get those errors, it is a permissions problem. I often mount my pieces of KVM QEMU into the filesystem, so that it can be used by other than one OS, and easily be migrated. I mount the storage pools, my ISO directory, and /etc/libvirt/ from outside of the OS root partition.  

For example, here images in one of the staorage pools on one of my KVM servers:
```

mafoelffen@Mikes-B460M:~$ ls -l /data/KVM-VM/
total 548830355
-rwxrwxrwx 1 libvirt-qemu kvm  32217432064 May 30 01:12 console01.qcow2
-rwxrwxrwx 1 libvirt-qemu kvm  32217432064 Nov 24  2022 fedora37.qcow2
-rwxrwxrwx 1 libvirt-qemu kvm  13000179712 Jul 26 01:03 fedora38.qcow2
-rw------- 1 root         root 53695545344 Jul  7 19:59 freebsd13.1.qcow2
-rw------- 1 libvirt-qemu kvm  32217432064 Dec 27  2022 iso-tester-01.qcow2
-rw------- 1 root         root 42956488704 Jun 21 14:54 kaisenrollingrino22.04-1.qcow2
-rw------- 1 libvirt-qemu kvm  32217432064 Dec 14  2022 linux2020-2.qcow2
-rw------- 1 root         root  4294967296 Aug 14 20:18 luks-key-usb-01.img
-rw------- 1 libvirt-qemu kvm  26847870976 Dec  3  2022 lunar23.04-2.qcow2
-rw------- 1 libvirt-qemu kvm  42956488704 Feb 23 12:51 lunar-lander-04.qcow2
-rw------- 1 libvirt-qemu kvm  10739318784 Apr 12 01:33 lunar-lander-05-1.qcow2
-rw------- 1 libvirt-qemu kvm  21478375424 Apr 12 01:35 lunar-lander-05.qcow2
-rw------- 1 libvirt-qemu kvm  22554476544 Jan 27  2023 lunar-lander-8_5.qcow2
-rw------- 1 libvirt-qemu kvm  42956488704 Feb 23 13:23 lunar-laner-04.qcow2
-rw------- 1 libvirt-qemu kvm  32217432064 Mar  1 07:06 lunar-server-01.qcow2
-rw------- 1 libvirt-qemu kvm  10739318784 Dec 15  2022 lunar-server-03-1.qcow2
-rw------- 1 libvirt-qemu kvm  10739318784 Dec 15  2022 lunar-server-03.qcow2
-rw------- 1 libvirt-qemu kvm  10739318784 Apr 12 13:11 lunar-server-04-1.qcow2
-rw------- 1 libvirt-qemu kvm  10739318784 Apr 12 13:11 lunar-server-04-2.qcow2
-rw------- 1 libvirt-qemu kvm  10739318784 Apr 12 13:11 lunar-server-04.qcow2
-rw------- 1 libvirt-qemu kvm  21478375424 Dec 16  2022 lunar-server-06.qcow2
-rw------- 1 libvirt-qemu kvm  10743054336 Jul  3 05:45 lunar-server-22.04-zfs.qcow2
-rw-rw-r-- 1 libvirt-qemu kvm   2463498240 Jan 25  2023 lunar-server-cloudimg-amd64.img
-rw-rw-r-- 1 libvirt-qemu kvm    724238336 Dec 27  2022 lunar-server-cloudimg-amd64.img.1
-rw-rw-r-- 1 libvirt-qemu kvm    724238336 Dec 27  2022 lunar-server-cloudimg-amd64.img.2
-rw-rw-r-- 1 libvirt-qemu kvm    724238336 Dec 27  2022 lunar-server-cloudimg-amd64.img.3
-rw------- 1 libvirt-qemu kvm  11667570688 May 26 09:57 lunar-server-lightvnc.qcow2
-rw------- 1 libvirt-qemu kvm  16108814336 Dec 18  2022 lunar-server-template.qcow2
-rw------- 1 libvirt-qemu kvm  11541217280 Jul  3 05:30 lunar-server-zfs-23.04.qcow2
-rw------- 1 libvirt-qemu kvm  10739318784 Aug 15 00:31 lvm2-xrdp-01.qcow2
-rw------- 1 libvirt-qemu kvm  21478375424 Aug 15 14:30 lvm2-xrdp-02.qcow2
-rw------- 1 libvirt-qemu kvm  21478375424 Aug 15 14:30 lvm2-xrdp-03.qcow2
-rw------- 1 libvirt-qemu kvm  10739318784 Aug 15 00:40 lvm2-xrdp-04.qcow2
-rw------- 1 libvirt-qemu kvm  10739318784 Aug 15 00:40 lvm2-xrdp-05.qcow2
-rw------- 1 libvirt-qemu kvm  10739318784 Aug 15 00:40 lvm2-xrdp-06.qcow2
-rw------- 1 libvirt-qemu kvm  10739318784 Aug 15 00:40 lvm2-xrdp-07.qcow2
-rw------- 1 root         root  1074135040 Jun 12 13:23 lvm-data-01.qcow2
-rw------- 1 root         root  1074135040 Jun 12 13:23 lvm-data-2.qcow2
-rw------- 1 root         root  1074135040 Jun 12 13:23 lvm-data--3.qcow2
-rw------- 1 root         root  1074135040 Jun 12 13:23 lvm-data-4.qcow2
-rw------- 1 root         root  2148073472 Jul 21 23:42 lvm-data-5.qcow2
-rw------- 1 root         root  2148073472 Jul 17 11:45 lvm-data-6.qcow2
-rw------- 1 root         root  2148073472 Jun 12 13:15 lvm-data-7.qcow2
-rw------- 1 root         root  2148073472 Jun 12 13:15 lvm-data-8.qcow2
-rwxrwxrwx 1 libvirt-qemu kvm    314572800 Nov 20  2022 openwrt-22.03.2-x86-64-generic-ext4-combined-efi.img
-rw------- 1 libvirt-qemu kvm  26847870976 Mar 22 01:23 penryn-01.qcow2
-rw------- 1 libvirt-qemu kvm  32217432064 Mar 21 16:47 proxmox-7.3-1.qcow2
-rw------- 1 libvirt-qemu kvm    670105600 Apr 23 11:59 prt-001-02-clone.qcow2
-rw-r--r-- 1 libvirt-qemu kvm    907214848 Apr 21 14:16 prt-001-02.qcow2
-rw------- 1 libvirt-qemu kvm  16109404160 May  3 20:40 prt_001.qcow2
-rw------- 1 libvirt-qemu kvm   2366570496 Apr 30 19:39 prt_002.qcow2
-rw------- 1 libvirt-qemu kvm  26922516480 May  4 09:18 prt-gpt-efi-01-clone-clone-clone.qcow2
-rw------- 1 libvirt-qemu kvm   3361669120 May  3 22:43 prt-gpt-efi-01-clone-clone.qcow2
-rw------- 1 libvirt-qemu kvm   2559770624 Apr 28 08:53 prt-gpt-efi-01-clone.qcow2
-rw-r--r-- 1 libvirt-qemu kvm   3456172032 Apr 28 09:47 prt-gpt-efi-01.qcow2
-rw------- 1 libvirt-qemu kvm  32217432064 Jun 20 22:55 rollingrino22.04-1.qcow2
-rwxrwxrwx 1 libvirt-qemu kvm   8641576960 Nov 21  2022 sol-11_4disk001.qcow2
-rw------- 1 libvirt-qemu kvm  21478506496 Jun 10 04:13 test.qcow2
-rw------- 1 libvirt-qemu kvm  42956619776 Mar 28 19:09 tiny11-01.qcow2
-rw------- 1 libvirt-qemu kvm  16108814336 Apr 25 10:12 ubuntu14.04-2.qcow2
-rw------- 1 libvirt-qemu kvm  16108814336 Apr 13 00:40 ubuntu14.04.qcow2
-rw------- 1 libvirt-qemu kvm  16108814336 Jan 18  2023 ubuntu16.04.qcow2
-rw------- 1 libvirt-qemu kvm  20174798848 Mar 16 14:59 ubuntu18.04.qcow2
-rw------- 1 root         root 42956488704 Jul 14 03:45 ubuntu20.04-2-1.qcow2
-rw------- 1 root         root 37586927616 Jun 15 01:04 ubuntu20.04-2.qcow2
-rw------- 1 root         root 42956488704 Jul 21 11:36 ubuntu20.04-3.qcow2
-rw------- 1 libvirt-qemu kvm  26847870976 Mar  1 23:20 ubuntu20.04.qcow2
-rwxrwxrwx 1 libvirt-qemu kvm  32212254720 Jul 26 00:15 ubuntu20.04-s390x-2
-rw------- 1 libvirt-qemu kvm  26847870976 Jan 28  2023 ubuntu22.04-10-1.qcow2
-rw------- 1 libvirt-qemu kvm  26847870976 Jun  6 09:10 ubuntu22.04-10-2.qcow2
-rw------- 1 libvirt-qemu kvm  19597099008 Mar  7 13:33 ubuntu22.04-10-clone-1.qcow2
-rw------- 1 libvirt-qemu kvm  23678222336 Jan 27  2023 ubuntu22.04-10-clone.qcow2
-rw------- 1 libvirt-qemu kvm  53695545344 Jan 18  2023 ubuntu22.04-10.qcow2
-rw------- 1 libvirt-qemu kvm  27873968128 Mar 16 00:33 ubuntu22.04-11.qcow2
-rw------- 1 libvirt-qemu kvm  26847870976 Feb 28 13:18 ubuntu22.04-12.qcow2
-rw------- 1 libvirt-qemu kvm  26847870976 Aug  4 10:18 ubuntu22.04-13.qcow2
-rw------- 1 root         root 53695545344 Aug 14 20:18 ubuntu22.04-15-1.qcow2
-rw------- 1 root         root 42956488704 Jun 21 15:04 ubuntu22.04-15.qcow2
-rw-rw-r-- 1 libvirt-qemu kvm   3371171840 Feb 21 08:01 ubuntu-22.04.2-live-server-riscv64.img
-rwxrwxrwx 1 libvirt-qemu kvm  32217432064 Nov 27  2022 ubuntu22.04-2.qcow2
-rw-r--r-- 1 libvirt-qemu kvm   9300017152 Jun 29 10:23 ubuntu-22.04.2-server-riscv64-01.qcow2
-rw------- 1 libvirt-qemu kvm  17394302976 Jul  5 05:22 ubuntu22.04-3-1-clone.qcow2
-rw------- 1 libvirt-qemu kvm  42956488704 Dec  3  2022 ubuntu22.04-3-1.qcow2
-rw------- 1 libvirt-qemu kvm  32217432064 Feb 15 13:52 ubuntu22.04-3.qcow2
-rw------- 1 libvirt-qemu kvm  42956488704 Feb 25 02:22 ubuntu22.04-4.qcow2
-rw------- 1 libvirt-qemu kvm  42956488704 Dec 18  2022 ubuntu22.04-5.qcow2
-rw------- 1 libvirt-qemu kvm  21478375424 Apr 12 13:11 ubuntu22.04-6-1.qcow2
-rw------- 1 libvirt-qemu kvm  26847870976 Mar 16 15:34 ubuntu22.04-6-2.qcow2
-rw------- 1 libvirt-qemu kvm  32217432064 Dec 16  2022 ubuntu22.04-7-1.qcow2
-rw------- 1 libvirt-qemu kvm  26847870976 Dec 16  2022 ubuntu22.04-7-2.qcow2
-rw------- 1 libvirt-qemu kvm  16108814336 Jun 10 03:20 ubuntu22.04-7-3.qcow2
-rw------- 1 libvirt-qemu kvm  16108814336 Dec 13  2022 ubuntu22.04-7.qcow2
-rw------- 1 libvirt-qemu kvm  42956488704 May 18 11:46 ubuntu22.04-8.qcow2
-rw------- 1 libvirt-qemu kvm  32217432064 Dec 29  2022 ubuntu22.04-9-1.qcow2
-rw------- 1 libvirt-qemu kvm  22523674624 Jul 25 23:05 ubuntu22.04-9-clone.qcow2
-rw------- 1 libvirt-qemu kvm  26847870976 Jul 25 22:14 ubuntu22.04-9.qcow2
-rwxrwxrwx 1 libvirt-qemu kvm  32217432064 Jul 26 01:27 ubuntu22.04.qcow2
-rw------- 1 root         root 26847870976 Aug  4 10:18 ubuntu23.04-1.qcow2
-rw------- 1 root         root 42956488704 Jun 21 21:44 ubuntu23.04.qcow2
-rw-rw-r-- 1 libvirt-qemu kvm   3879731200 Dec 18  2022 ubuntu-core-22-20221218-amd64.img
-rw------- 1 libvirt-qemu kvm  21478375424 Mar 21 21:59 ubuntu-core22-20221218.qcow2
-rw------- 1 libvirt-qemu kvm   9917235200 Mar 22 13:14 ubuntu-server-22.04.2.qcow2
-rw-rw-r-- 1 libvirt-qemu kvm           77 Dec 30  2022 user-data.img
-rw------- 1 libvirt-qemu kvm  42956488704 Aug 15 14:30 win10.qcow2
-rw------- 1 libvirt-qemu kvm  85912715264 Jul  5 05:24 win2k22.qcow2
-rw------- 1 libvirt-qemu kvm  26847870976 Feb  2  2023 xubuntu22.04-01.qcow2
-rw------- 1 root         root  9873719296 Jul 14 05:30 Zentyal-22.04-test.qcow2

```
These are actually within complex mounts from ZFS RAIDz2 pools
```

mafoelffen@Mikes-B460M:~$ sudo zfs list | grep 'KVM-VM'
datapool/DATA/ubuntu_2cwpns/KVM-VM                 523G  3.81T      523G  /data/KVM-VM
mafoelffen@Mikes-B460M:~$ sudo zpool status -v datapool
  pool: datapool
 state: ONLINE
  scan: scrub repaired 0B in 00:16:02 with 0 errors on Sun Aug 13 00:40:03 2023
config:

    NAME                                                   STATE     READ WRITE CKSUM
    datapool                                               ONLINE       0     0     0
      raidz2-0                                             ONLINE       0     0     0
        ata-Samsung_SSD_870_EVO_2TB_S6PNNM0TA09560A-part1  ONLINE       0     0     0
        ata-Samsung_SSD_870_EVO_2TB_S6PNNM0TA11601H-part1  ONLINE       0     0     0
        ata-Samsung_SSD_870_EVO_2TB_S6PNNM0TA47393M-part1  ONLINE       0     0     0
        ata-Samsung_SSD_870_EVO_2TB_S6PNNS0W330507J-part1  ONLINE       0     0     0
        ata-Samsung_SSD_870_EVO_2TB_S6PNNM0TB08933B-part1  ONLINE       0     0     0
    logs    
      nvme-Samsung_SSD_970_EVO_2TB_S464NB0KB10521K-part2   ONLINE       0     0     0
    cache
      nvme-Samsung_SSD_970_EVO_2TB_S464NB0KB10521K-part1   ONLINE       0     0     0

errors: No known data errors

```
I occasionally reset all my images as owned by livbirt-qemu:kvm and reset the permissions of them to 664, via
```

sudo chown -R libvirt-qemu:kvm /path/to/images/*
sudo chmod -R 664 /path/to/images/*

```

---

### Post by johannes1985 on 2023-08-16
Hi,

The setups are tested first on Virtual box, each in their own vm before it is installed on a physical server.

The issue is only with cockpit-machines. If I install the minimal kvm tools as below on Ubuntu 22.04.3 server:

```

sudo apt install bridge-utils libvirt-clients libvirt-daemon-system qemu-system-x86


sudo systemctl status libvirtd


sudo systemctl stop libvirtd


sudo groupadd kvm
sudo groupadd libvirt


sudo usermod -aG kvm $USER
sudo usermod -aG libvirt $USER


sudo chown :kvm /var/lib/libvirt/images
sudo chmod g+rw /var/lib/libvirt/images


sudo systemctl start libvirtd
sudo systemctl status libvirtd

```

and have another PC running either Ubuntu or anything with Virt Manager:

```

sudo apt install ssh-askpass virt-manager


sudo chown root:kvm /var/lib/libvirt/images/ISO
sudo chmod g+rw /var/lib/libvirt/images/ISO

```

Then these errors do not occur.


Even on a fresh install, there are no VMs setup or created yet on Cockpit Machines, it still gave that permission error. I just have to click on the Virtual Machines link on Cockpit, then the logs show that permission error. So, it is not a VM on cockpit machines causing this issue. I also tested it last night on a physical server and the results are the same.

A fresh install of Ubuntu 22.04.3, updated, cockpit and cockpit-machines installed from backports. Logging in, clicking on Virtual Machines and the log shows these errors:

```

[COLOR=#000000][FONT=&quot]Failed to read AppArmor profiles list '/sys/kernel/security/apparmor/profiles': Permission denied libvirtd
[/FONT][/COLOR][COLOR=#000000][FONT=&quot]Failed to open file '/sys/kernel/security/apparmor/profiles': Permission denied libvirtd
[/FONT][/COLOR][COLOR=#000000][FONT=&quot]Failed to read AppArmor profiles list '/sys/kernel/security/apparmor/profiles': Permission denied libvirtd
[/FONT][/COLOR][COLOR=#000000][FONT=&quot]Failed to open file '/sys/kernel/security/apparmor/profiles': Permission denied libvirtd
[/FONT][/COLOR]
```

Even with these 4 permission errors, I am still able to create VMs in Cockpit, they work. The issue is mainly, I like an error free system and I am hopelessly unable to resolve this issue.

The Cockpit and Cockpit Machines web gui is a nice to have, it makes working on the server much more convenient, but if I can't get this resolved, then I am fine just using the command line.

A user from Debian forums, advise I should just ignore these errors:
[https://forums.debian.net/viewtopic.php?t=155689](https://forums.debian.net/viewtopic.php?t=155689)


--- 
Also:

As per the minimal kvm install, and I install cockpit-machines afterwards and creating a vm in virt manager, running the following to check:

```

sudo aa-logprof

```

Gives an error that it can't find the profile for the VM, which is fine I guess. Libvirt create these profiles automatically every time. This just occurs, if the VM was created on Virt Manager and I installed Cockpit Machines afterwards on the test server.

---

### Post by MAFoElffen on 2023-08-16
So this bug seems to be with cockpit-machines...

I wonder. this was 20.04, but seems real similar: [https://bugs.launchpad.net/ubuntu/+source/cockpit/+bug/1891092](https://bugs.launchpad.net/ubuntu/+source/cockpit/+bug/1891092)

I read more about profile permission errors using cockpit-machines with libvirtd (KVM) and found an interesting work-around for someone who was getting the same errors as you... This is the apparmor profile template file for lxc:
```

mafoelffen@msi-ubuntu:~$ grep . /etc/apparmor.d/libvirt/TEMPLATE.lxc
#
# This profile is for the domain whose UUID matches this file.
#
#include <tunables/global>
profile LIBVIRT_TEMPLATE flags=(attach_disconnected) {
  #include <abstractions/libvirt-lxc>
  # Globally allows everything to run under this profile
  # These can be narrowed depending on the container's use.
  file,
  capability,
  network,
}

```
This is the apparmor profile template file for KVM
```

mafoelffen@msi-ubuntu:~$ grep . /etc/apparmor.d/libvirt/TEMPLATE.qemu
#
# This profile is for the domain whose UUID matches this file.
#
#include <tunables/global>
profile LIBVIRT_TEMPLATE flags=(attach_disconnected) {
  #include <abstractions/libvirt-qemu>
}

```
What they did was to add "file," to the KVM profile template, which opened the security up just a smiggen, and then it started working for him without errors, so something like this
```

#
# This profile is for the domain whose UUID matches this file.
#
#include <tunables/global>
profile LIBVIRT_TEMPLATE flags=(attach_disconnected) {
  #include <abstractions/libvirt-qemu>
  [COLOR=#ff0000]file,[/COLOR]
}

```
Could you make that edit and test if it helps you?

---

### Post by MAFoElffen on 2023-08-16
I do a lot of testing. <-- Not just using KVM, but in how I use it. I have used KVM & QEMU for over 13 years now. I have installed and used various VM tools to see if they fit into my workflows, or helped in differing ways. One of those was cockpit-machines. I am still on that journey, and search... 

Are you interested in my review of cockpit-machines and why I opt not to use it? I am hesitant in sharing that if you are 'invested' in using it. I understand that your personal preferences may not match my own, and I wouldn't want to impose mine, if it were not welcomed...

---

### Post by MAFoElffen on 2023-08-16
That last post reminded me that I still have cockpit-machines installed... See attached.

Seems that I get the same error message while starting/using cockpit-machines. But nothing is wrong and everything still works.

---

### Post by TheFu on 2023-08-16
I didn't read the entire thread, but a few months ago I saw a similar error.  The root cause was that the libvirt VM storage area was above the mandated free blocks for the storage device I'd put there which was just large enough to hold the only VM I planned to have in a .qcow2 file.  I added a few GB more storage to that area and QEMU/KVM started working.  LVM made adding a tiny bit to that logical volume trivial.

It presented as "permission denied" and the logs were full of apparmor warnings/errors.

I assume Cockpit uses libvirt and that normal libvirt areas in /var/lib/libvirt are used?  Check that area isn't full and that the mandated root-reserved storage limit hasn't been hit.
Here's mine:
```
$ df -Th  /var/lib/libvirt
Filesystem                   Type  Size  Used Avail Use% Mounted on
/dev/mapper/vg01-libvirt--01 ext4  134G  131G  2.8G  98% /var/lib/libvirt
```

To see what the limit is on an ext2/3/4 file system, use
```
$ sudo tune2fs -l /dev/mapper/vg01-libvirt--01
...
Filesystem OS type:       Linux
Inode count:              8978432
Block count:              35913728
**Reserved block count:     0**
Overhead blocks:          841118
Free blocks:              735564
...

```

As you can see, I set it to zero. Don't do that if you don't know what this does. It is a terrible idea if this is the OS storage.

Of course, I could be completely wrong.  This may not be the issue for the OP.

Typically, I use LVM LVs for my VM storage, so that directory will never be used for any other VM needs.

---

### Post by MAFoElffen on 2023-08-16
@TheFu

IDK. Reproducible on mine, but mine is this:
```

mafoelffen@Mikes-ThinkPad-T520:~$ zfs list | grep -e 'NAME' -e 'images '
NAME                                               USED  AVAIL     REFER  MOUNTPOINT
kpool/QEMU-KVM/ubuntu_2204/images                  224G   552G      224G  /var/lib/libvirt/images

```
I have plenty of space available there, but mine is in ZFS pools.

And I do not have any quotas set on that dataset:
```

mafoelffen@Mikes-ThinkPad-T520:~$ sudo zfs get refquota,quota kpool/QEMU-KVM/ubuntu_2204/images
NAME                               PROPERTY  VALUE     SOURCE
kpool/QEMU-KVM/ubuntu_2204/images  refquota  none      default
kpool/QEMU-KVM/ubuntu_2204/images  quota     none      default

```
I think it might just be a Cockpit quark. I see no profiles in apparmor set for cockpit to access "things", and libvirt only has a single rule defined. The permissions of Cockpit use itself, are of the user that is logged into cockpit, unless you press the "Elevate Permissions" button in the upper right of the panel...

---

### Post by TheFu on 2023-08-17
Webapps for system management make me a bit nervous.  Millions of crackers work to learn how to attack and penetrate webservers/webapps. It is a "target rich area" of server computing.  I feel for organizations that need something like this.  At least with virt-manager, ssh authentication and security are required to remotely manage VMs. Alas, many organizations feel that virt-manager doesn't scale well and they have a point.  Xen made a pretty webapp for their VM management. Same for Proxmox.  With all the pretty graphs, managers are easily impressed and that's what sells software.  

I have stories where the company I worked at added some completely useless "features" just to add graphs that were of ZERO use.  Sales jumped.  We called it "spreading the cheese".  You know how almost anything tastes better with enough cheese on it?


johannes1985, you don't have to use shell commands to manage VMs.  virt-manager is a nice little GUI that uses libvirt and makes creating and managing VMs almost like a desktop program VMware Workstation or Virtualbox, but with the stability and speed of KVM/QEMU.  Setup a VM host, connect to it from any workstation using virt-manager.  The connection URL is like this: qemu+ssh://username@remote-vm-server-dns-name/system

Just setup ssh-key connections for username@remote-vm-server-dns-name and it is like working locally. Once the storage pools have been added, pick the type you want, it is pretty easy. 

The default will use a directory on the file system, usually /var/lib/libvirt/images, but you can add or change that to point anywhere.  I added an LVM volume group and whenever a VM is created, tell it to make an LV just for that VM.  No local mounts.  Pure block storage added to the VM. Plus all the LVM capabilities.  There are 12 backend storage options, including NFS and iSCSI, and multiple cluster storage tools like Gluster and Sheepdog.  Of course, the host system can use tools like snapshots to create perfect backups for every VM too, if the volume manager provides that capability (ZFS/LVM do).   These storage options are part of the reason why VMware Player/Workstation and Virtualbox are toys in comparison.

---

