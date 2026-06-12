---
title: "Problems connecting to SMB share from android"
date: 2015-09-30
forum: Server Platforms
---

### Post by promufa on 2015-09-30
Hi all, I am rather new to Linux and SMB so I would appreciate any help.

I have a machine running Ubuntu 12.04 and smb 3.6.3
The samba shares from this machine are 3 folders each on a separate external drive and one partition of the internal drive (sda3).

From my windows PC I can automatically mount all 3 external drives (mapped drives). sda3 cannot be accessed as a mapped drive unless I first browse the network and explore the ubuntu machine. After doing this I can either browse to sda3 or access it from the mapped shortcut. After this sda3 remains accessible until the windows pc is restarted.

From android I can again access all 3 external drives just fine. sda3 is visible through ES file explorer but cannot open it. If I have already connected to sda3 from the windows pc, sda3 is accessible via android as well (again until windows pc is restarted).
I 've attached the smb.conf and fstab. I had to modify fstab to get sda3 share to work at all.

Any advice would be appreciated

Thanks :)

[B]

 smb.conf :
[/B]

#======================Global Settings========================
[global]
    workgroup = workgroup
    server string = Samba Server %v
    netbios name = Samba
    security = user
    guest ok = yes
    dns proxy = no
    username level = 3
    force user = promufa
    username map = /etc/samba/smbusers
;    encrypt passwords = yes
;    guest account = nobody


#======================Shares===================================


[Store]
    path = '/media/sda3'
;    browsable = yes
    writable = yes
    guest ok = yes
    username = promufa


[Expansion]
    path = /media/Expansion Drive/Expansion
    writeable = yes
;    browseable = yes
    guest ok = yes


[Darkness]
    path = /media/Darkness/Darkness
    writeable = yes
;    browseable = yes
    guest ok = yes


[Seagate]
    path = /media/Seagate Expansion Drive/-=STORAGE=-
    writeable = yes
;    browseable = yes
    guest ok = yes


**fstab:**

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc        proc  nodev,noexec,nosuid                                   0  0  
# / was on /dev/sda1 during installation
UUID=5f6f11d7-0eeb-490f-a051-7ffe988021d3  /            ext4  errors=remount-ro                                     0  1  
# swap was on /dev/sda5 during installation
UUID=e3e8025e-f834-439c-8224-4c242354e7fd  none         swap  defaults                                              0  0  
/dev/sda3                                  /media/sda3  ntfs  defaults                                              0  0

---

