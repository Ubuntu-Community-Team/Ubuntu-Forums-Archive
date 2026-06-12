---
title: "[Beginner Question - KVM Guest Machines] Unable to start Guest VM"
date: 2021-07-23
forum: Virtualisation
---

### Post by sheenlim08 on 2021-07-23
Hello and Good Day,

I am setting up a home lab using KVM. I have 3 physical driver representing 3 volumes.
```
/mnt/110GB-SSD
/mnt/2TB-HDD
/mnt/500GB-SSD
```

My root drive is only 64GB.

```
user@srv01:~$ df -h
Filesystem                    Size  Used Avail Use% Mounted on
udev                           63G     0   63G   0% /dev
tmpfs                          13G  2.0M   13G   1% /run
/dev/mapper/ubuntu--vg-lv--0   63G   11G   50G  18% /
tmpfs                          63G     0   63G   0% /dev/shm
tmpfs                         5.0M     0  5.0M   0% /run/lock
tmpfs                          63G     0   63G   0% /sys/fs/cgroup
/dev/mapper/ubuntu--vg-lv--2  4.9G   23M  4.6G   1% /home
/dev/sda1                     511M  7.9M  504M   2% /boot/efi
/dev/mapper/ubuntu--vg-lv--1  4.9G  610M  4.0G  13% /var
/dev/sdc                      477G  3.4G  474G   1% /mnt/500GB-SSD
/dev/mapper/ubuntu--vg-lv--3  110G  818M  110G   1% /mnt/110GB-SSD
/dev/loop1                     56M   56M     0 100% /snap/core18/1944
/dev/loop0                     56M   56M     0 100% /snap/core18/2074
/dev/loop2                     32M   32M     0 100% /snap/snapd/10707
/dev/loop3                     70M   70M     0 100% /snap/lxd/19188
/dev/sdb                      1.9T   35G  1.8T   2% /mnt/2TB-HDD
/dev/loop4                     33M   33M     0 100% /snap/snapd/12398
/dev/loop5                     71M   71M     0 100% /snap/lxd/21029
tmpfs                          13G     0   13G   0% /run/user/1000
```

I have installed KVM and all of its requirements on the server. However my ISO files are located on /mnt/2TB-HDD
```
sheenlim08@srv01:~$ ls /mnt/2TB-HDD/ftp_root/ISO -l
total 22572480
-rwxrwxr-x 1 sheenlim08   sheenlim08 7135559680 Jul 22 12:53 CentOS-8-x86_64-1905-dvd1.iso
-rw-rw-r-- 1 sheenlim08   sheenlim08 4056940544 Jul 22 12:54 openSUSE-Leap-15.1-DVD-x86_64.iso
-rwxrwxr-x 1 libvirt-qemu kvm        2785017856 Jul 22 12:29 ubuntu-20.04.1-desktop-amd64.iso
-rw-rw-r-- 1 sheenlim08   sheenlim08 1215168512 Jul 22 12:20 ubuntu-20.04.2-live-server-amd64.iso
-rw-rw-r-- 1 sheenlim08   sheenlim08 7921532928 Jul 22 12:42 Windows21H1.iso
```

I created a Ubuntu VM with its virtual cd-rom targeting "/mnt/2TB-HDD/ftp_root/ISO/ubuntu-20.04.1-desktop-amd64.iso"

I then monitor the /var/log/syslog file then start the VM. 
The syslog file shows.
```
Jul 23 23:01:09 srv01 kernel: [ 2056.644781] audit: type=1400 audit(1627081269.900:41): apparmor="STATUS" operation="profile_load" profile="unconfined" name="libvirt-29e30561-c068-44c4-8d6b-d674728d683f" pid=2127 comm="apparmor_parser"
Jul 23 23:01:10 srv01 kernel: [ 2056.892720] audit: type=1400 audit(1627081270.148:42): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="libvirt-29e30561-c068-44c4-8d6b-d674728d683f" pid=2130 comm="apparmor_parser"
Jul 23 23:01:10 srv01 kernel: [ 2057.143155] audit: type=1400 audit(1627081270.396:43): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="libvirt-29e30561-c068-44c4-8d6b-d674728d683f" pid=2134 comm="apparmor_parser"
Jul 23 23:01:10 srv01 kernel: [ 2057.392757] audit: type=1400 audit(1627081270.648:44): apparmor="STATUS" operation="profile_replace" info="same as current profile, skipping" profile="unconfined" name="libvirt-29e30561-c068-44c4-8d6b-d674728d683f" pid=2138 comm="apparmor_parser"
Jul 23 23:01:10 srv01 kernel: [ 2057.405749] virbr0: port 2(vnet0) entered blocking state
Jul 23 23:01:10 srv01 kernel: [ 2057.405752] virbr0: port 2(vnet0) entered disabled state
Jul 23 23:01:10 srv01 kernel: [ 2057.405845] device vnet0 entered promiscuous mode
Jul 23 23:01:10 srv01 kernel: [ 2057.406044] virbr0: port 2(vnet0) entered blocking state
Jul 23 23:01:10 srv01 kernel: [ 2057.406046] virbr0: port 2(vnet0) entered listening state
Jul 23 23:01:10 srv01 networkd-dispatcher[1230]: WARNING:Unknown index 7 seen, reloading interface list
Jul 23 23:01:10 srv01 systemd-networkd[1202]: vnet0: Link UP
Jul 23 23:01:10 srv01 systemd-networkd[1202]: vnet0: Gained carrier
Jul 23 23:01:10 srv01 systemd-udevd[2141]: Using default interface naming scheme 'v245'.
Jul 23 23:01:10 srv01 systemd-udevd[2141]: ethtool: autonegotiation is unset or enabled, the speed and duplex are not writable.
Jul 23 23:01:10 srv01 kernel: [ 2057.652331] audit: type=1400 audit(1627081270.908:45): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="libvirt-29e30561-c068-44c4-8d6b-d674728d683f" pid=2149 comm="apparmor_parser"
Jul 23 23:01:10 srv01 systemd[1]: Started Virtual Machine qemu-2-ubuntu20.04.
Jul 23 23:01:11 srv01 systemd-networkd[1202]: vnet0: Link DOWN
Jul 23 23:01:11 srv01 systemd-networkd[1202]: vnet0: Lost carrier
Jul 23 23:01:11 srv01 kernel: [ 2057.754350] virbr0: port 2(vnet0) entered disabled state
Jul 23 23:01:11 srv01 kernel: [ 2057.758430] device vnet0 left promiscuous mode
Jul 23 23:01:11 srv01 kernel: [ 2057.758441] virbr0: port 2(vnet0) entered disabled state
Jul 23 23:01:11 srv01 systemd-networkd[1202]: rtnl: received neighbor for link '7' we don't know about, ignoring.
Jul 23 23:01:11 srv01 systemd-networkd[1202]: rtnl: received neighbor for link '7' we don't know about, ignoring.
Jul 23 23:01:11 srv01 libvirtd[1302]: Unable to read from monitor: Connection reset by peer
Jul 23 23:01:11 srv01 libvirtd[1302]: internal error: qemu unexpectedly closed the monitor: 2021-07-23T23:01:11.010860Z qemu-system-x86_64: -blockdev {"driver":"file","filename":"/mnt/2TB-HDD/ftp_root/ISO/ubuntu-20.04.1-desktop-amd64.iso","node-name":"libvirt-1-storage","auto-read-only":true,"discard":"unmap"}: Could not open '/mnt/2TB-HDD/ftp_root/ISO/ubuntu-20.04.1-desktop-amd64.iso': Permission denied
Jul 23 23:01:11 srv01 systemd[1]: machine-qemu\x2d2\x2dubuntu20.04.scope: Succeeded.
Jul 23 23:01:11 srv01 libvirtd[1302]: internal error: process exited while connecting to monitor: 2021-07-23T23:01:11.010860Z qemu-system-x86_64: -blockdev {"driver":"file","filename":"/mnt/2TB-HDD/ftp_root/ISO/ubuntu-20.04.1-desktop-amd64.iso","node-name":"libvirt-1-storage","auto-read-only":true,"discard":"unmap"}: Could not open '/mnt/2TB-HDD/ftp_root/ISO/ubuntu-20.04.1-desktop-amd64.iso': Permission denied
Jul 23 23:01:11 srv01 kernel: [ 2058.037661] audit: type=1400 audit(1627081271.292:46): apparmor="STATUS" operation="profile_remove" profile="unconfined" name="libvirt-29e30561-c068-44c4-8d6b-d674728d683f" pid=2163 comm="apparmor_parser"
```

Whie the virt manager shows the prompt.
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=288867&stc=1[/IMG]

I cannot see any permission issues on the file, can anyone guide me to the correct troubleshooting steps?

---

### Post by MAFoElffen on 2021-07-23
The post format is a mess and I can hardly look at it. You might go back and edit your post, wrapping any formatted text within [ c o d e } and [ / c o d e } tags (without the sapces I put there just to show you what they look like)... That will reformat that in a form that will be easier to read.

- What is the host system OS and version of?

- I i know you have limited space, but... Why the temporary mounts of the USB Drives? Is this a laptop or notebook? (Where the drives are not there all the time?)

Even though I haven't read through that in detail, and can hardly make that all out yet... I can tell you right off that it is how you have it mounted, and the read write permission to where it is trying to write to...  You need to back up a little bit and prep it to be used by KVM... It's not just that You don'. The libvert-qemu and kvm groups don't either.

---

### Post by sheenlim08 on 2021-07-24
Thanks** MAFoElffen, **the mounds /mnt are static, they are mapped from my fstab file.

```

sheenlim08@srv01:/mnt/2TB-HDD/ftp_root/ISO$ cat /etc/fstab 
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/ubuntu-vg/lv-0 during curtin installation
/dev/disk/by-id/dm-uuid-LVM-UkeuXncB9ODHc4slo6yR0ntB72Ue2NrocljWYS1Lx0VCVtZOVgDi318vxbtKI6X4 / ext4 defaults 0 0
# /var was on /dev/ubuntu-vg/lv-1 during curtin installation
/dev/disk/by-id/dm-uuid-LVM-UkeuXncB9ODHc4slo6yR0ntB72Ue2NrogRFt6cSbzi6HrPKYsOORw5mpCTlz41Wf /var ext4 defaults 0 0
# /home was on /dev/ubuntu-vg/lv-2 during curtin installation
/dev/disk/by-id/dm-uuid-LVM-UkeuXncB9ODHc4slo6yR0ntB72Ue2NrofFlRaAqsnUJ4vyk10S0B2MjImjCyWWT7 /home ext4 defaults 0 0
# /mnt/110GB-SSD was on /dev/ubuntu-vg/lv-3 during curtin installation
/dev/disk/by-id/dm-uuid-LVM-UkeuXncB9ODHc4slo6yR0ntB72Ue2Nro34xWDiTD8BBpYb5Lo2U7MD1fr9h7i9dm /mnt/110GB-SSD xfs defaults 0 0
# /boot/efi was on /dev/sdc1 during curtin installation
/dev/disk/by-uuid/A670-88C4 /boot/efi vfat defaults 0 0
# /mnt/500GB-SSD was on /dev/sde during curtin installation
/dev/disk/by-uuid/0d084e9e-264d-41f8-8b59-a4acb50ccbf6 /mnt/500GB-SSD xfs defaults 0 0
# /mnt/2TB-HDD was on /dev/sdd during curtin installation
/dev/disk/by-uuid/3facc172-3966-4549-b160-36d6bdc68118 /mnt/2TB-HDD xfs defaults 0 0
/swap.img    none    swap    sw    0    0

```

My OS information are:
```

sheenlim08@srv01:/mnt/2TB-HDD/ftp_root/ISO$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 20.04.2 LTS
Release:    20.04
Codename:    focal

sheenlim08@srv01:/mnt/2TB-HDD/ftp_root/ISO$ uname -a
Linux srv01 5.8.0-63-generic #71~20.04.1-Ubuntu SMP Thu Jul 15 17:46:08 UTC 2021 x86_64 x86_64 x86_64 GNU/Linux

```

How do i prepare a directory for KVM use? Can you point me to wiki page for it? i tried googling it but could not find any reference for it.

---

### Post by sheenlim08 on 2021-07-24
I have tried to remove the "defaults" column on my /etc/fstab, so that line now looks
/dev/disk/by-uuid/3facc172-3966-4549-b160-36d6bdc68118 /mnt/2TB-HDD xfs 0 0

did a reboot and that seem to fix the issue, I don't know why. 
If someone that is an expert in Linux and KVM, feel free to explain, i'd be interested on learning why.

---

### Post by The Cog on 2021-07-24
Lets start by double-checking the permissions:
```
ls -ld /mnt
ls -ld /mnt/110GB-SSD
ls -ld /mnt/110GB-SSD/ftp_root
ls -ld /mnt/110GB-SSD/ftp_root/ISO
ls -l /mnt/110GB-SSD/ftp_root/ISO/ubuntu-20.04.1-desktop-amd64.iso
```
And remember that the VM runs under its own account name (kvm or libvirt or similar, I can't remember). It will need **r**ead and e**x**ecute on all the directories, and **r**ead on the file.

Oops, didn't notice it was solved - never mind.

---

### Post by MAFoElffen on 2021-07-24
The directory that KVM cares about and is picky about is wherever you are pointing the storage pool for your VM disks Which if you are using Virt-Manager, you can easily set any directory that you have access to, as the default directory for those disk images... But then, if the permissions are not right, then it complains or fails on those.

What I do, is setup a directory for it somewhere that has room, whether that directory is locally mounted somewhere, a network share (SMB or NSF), an iSCSI storage or NAS..... Whatever, of any filesystem type... And set it "Owned/Created" by 'virt-qemu",and the setuid bit set, 4. The user set to rwx, 7. the group set to "kvm", and be able to at least rx, 5. Public set, to at least r, 4. So the permissions I set on that Directory, recursively is 4754.

Since you and other's seems to be having permissions problems with things about security, permissions, how selinux and apparmor tie into that, here is more detailed info:
 - [https://libvirt.org/drvqemu.html]("https://libvirt.org/drvqemu.html#securityselinux")

---

### Post by TheFu on 2021-07-24
Just trying to clear up something that isn't clear above.  The ISO files aren't meant to be available post-install into a VM.
In using virt-manager, which used libvirt, by default the location for virtual machines that use "file-based" backed storage is  /var/lib/libvirt/images/.  You can add other "storage pools" if you like. Those storage pools can be file-based or use other storage backends supported by libvirt and KVM - like ZFS, LVM, Sheepdog, or about 10 other options.  For file-based VM storage, all the popular types can be used.  It is generally not the situation that storage connected via USB is used for VM storage. There are many reasons for this.

I mount extra storage to 
```
Filesystem                        Type  Size  Used Avail Use% Mounted on
/dev/mapper/hadar--vg-libvirt--lv ext4  173G  127G   37G  78% /var/lib/libvirt
```
For quick file-based VMs.  My production VMs all use LVM-LV storage.

BTW, /mnt/ is supposed to be used for admin temporary work areas according to the Linux File System Standards.

virt-manager has a VM setup wizard, where it asks questions to generate a VM config file. One of the questions is what's the installation ISO and the other question is what storage do you want to install into?

Perhaps all of that is already clear and I missed it.

After installing kvm/virt-manager and the pulled in dependencies, the sudo-userid used will be added to the libvirtd group.  To make that active, you can either use newgrp or logout and login again.  If you are going to manage the KVM host from a different workstation using either virt-manager or virsh, then on that other workstation, being a member of the libvirtd group is also required.  This matters so that there aren't any permission issues. Check the group using the 'id' command.

---

### Post by sheenlim08 on 2021-07-24
Hi TheFu,

Thanks for Clarifying, but I am still confused.

I am using 2 Dir (File System) Storage Pools, 1 Pool for my baseline VMs and 1 for the ISO folder which is a ftp root for the FTP service that is running on the host. Both DIR are hosted in that 2TB-HDD storage.
If I remove the 4th column for the fstab entry of the 2TB-HDD device KVM and qemu can access that drive, however the FTP service can only read to it. If I put the defaults on the fstab, vsftpd can write/delete, the VM's can then start (for those that are already created) but they boot to EUFI (I set them on secureboot on the VM's BIOS).

For new VM's I cannot create them because I am getting that error message i posted on the first post.

So technically, my configs are ok but I am not sure what mount option I should put on the fstab.

---

### Post by MAFoElffen on 2021-07-24
It's yours with no other users, right?
 - After the mount point and filesystem helper, for options, use:  defaults,users 0 0

Then anyone (you) can do anything on it. You can then limit with permissions from there. You can add limitations to permission and access, but you can't add access to something you can't get to or see (behind a locked door). Does that logic make sense?

You could limit that more... by after users, adding uid=xxxx,gid=xxx,dmask=xxx,fmask=xxx options.

```
uid = user identifier, which 1000 is the first normal user. if you installed, that's you.
gid = group identifier, which 100 is safe...

umask=value; Set the umask (the bitmask of the permissions that are not present). The default is the umask of the current process. The value is given in octal. 

dmask=value;  Set the umask applied to directories only. The default is the umask of the current process. The value is given in octal.

fmask=value; Set the umask applied to regular files only. The default is the umask of the current process. The value is given in octal.
```
Note that umask is both directoriy and file permissions. Use either umask... or split permissions up into dmask and fmask.

That's probably more than you need, but you asked.

---

### Post by TheFu on 2021-07-24
Attempting to use plain FTP and have VMs running from the same directory is asking for problems.  Plain FTP should have died in 2002. Use sftp instead.  Then normal Unix groups can be used and you can make all the files use libvirtd for the group, which would allow both your userid and the KVM process total access.

In an fstab, the options cannot have any spaces, so
```
 defaults, users
```
is wrong.
```
 default[COLOR="#008000"]s,u[/COLOR]sers
```
could work, assuming a native Linux file system underneath.  I removed the space between the 2 options.  If the drive is NTFS, then the userid, groupid, and permissions can only be set through mount options.  It is too late here to head down that rabbit hole.

---

### Post by sheenlim08 on 2021-07-25
i tried the defaults,users thing in my fstab but it still behaves the same way. I am actually using SFTP.
As i have posted above, the 2 dir storage pool is hosted on the same disk but the FTP root and where virtual disks are not located in the same directory.

---

### Post by sheenlim08 on 2021-07-25
> **TheFu said:**
> Attempting to use plain FTP and have VMs running  from the same directory is asking for problems.  Plain FTP should have  died in 2002. Use sftp instead.  Then normal Unix groups can be used and  you can make all the files use libvirtd for the group, which would  allow both your userid and the KVM process total access.

In an fstab, the options cannot have any spaces, so
```
 defaults, users
```
is wrong.
```
 defaults,users
```
could work, assuming a native Linux file system underneath.  I removed  the space between the 2 options.  If the drive is NTFS, then the userid,  groupid, and permissions can only be set through mount options.  It is  too late here to head down that rabbit hole.

i tried the defaults,users thing in my fstab but it still behaves the same way. I am actually using SFTP.
As i have posted above, the 2 dir storage pool is hosted on the same disk but the FTP root and where virtual disks are not located in the same directory.

---

### Post by MAFoElffen on 2021-07-25
Well, This is what I have...My Ubuntu root is on SSD, my pools for ISO and KVM-VM (where my VM Disks are) are on a 4TB SATA that is NTFS... which I mount into my own Home directory so it's easy for me to navigate to... I could have just as easisly had the VAR directory split out and the Permissions and setting for it would have just been default... (Which some people do.)
```
afoelffen@Opti-Ubuntu-Main:~$ kvm --version
QEMU emulator version 4.2.1 (Debian 1:4.2-3ubuntu6.17)
Copyright (c) 2003-2019 Fabrice Bellard and the QEMU Project developers
mafoelffen@Opti-Ubuntu-Main:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdb5 during installation
UUID=d6eb6bcf-c93a-46d5-b7e0-25dd73eec384 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda4 during installation
UUID=a5c5987f-82ab-4e16-a39f-aa5564a0a2ef /home           ext4    defaults        0       2
# swap was on /dev/sda3 during installation
UUID=f7db5bcd-8019-46a1-abe9-44d99c84d0e7 none            swap    sw              0       0
[COLOR=#ff0000]UUID=0A24D9F224D9E0AD             /home/mafoelffen/WIN_G  ntfs    defaults        0       0 [/COLOR]

```
Then I set the permissions in the two directories/files recursively there for owned by virt-qemu, kvm group, permissions 4754, and it's works. I still had to set the permssion and ownership for those two for it to work. Just doing the mount doesn't do that. Especially since "mine" is not a Linux Filesystem on that disk.. 

I did that on that Filesystem. because that machine is a Multi-boot, and I can copy over ISO to that, from whatever OS I am running. And I have access to it from my Local LAN, from my Pi4... So I can copy ISO's from it.

On my Raspberry Pi4 running Ubuntu and Qemu/KVM, I just created my directories in the Public's Home folder, and all the permissions were already set fine to be used by any user on that. Because that home folder is shared.

Just techniques...

---

