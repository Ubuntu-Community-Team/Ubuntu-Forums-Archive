---
title: "Can't mount drive to samba share folder."
date: 2019-09-29
forum: Server Platforms
---

### Post by trexxit on 2019-09-29
I have access to my samba share after setting it up, great! I go to configure my 1tb drive to mount in samba via /etc/fstab, emergency mode, double checked, all looks good, well nope!
I delete that line, reboot all is well, but I can't manually mount the drive after booting in my samba share folder(/samba/public)
I also cannot mount it anywhere else, which is odd, whats going on here?
Followed this guide to get it set up in general, as I'm new to the server side of things:[https://websiteforstudents.com/samba-setup-on-ubuntu-16-04-17-10-18-04-with-windows-systems/](https://websiteforstudents.com/samba-setup-on-ubuntu-16-04-17-10-18-04-with-windows-systems/)
Output of fdisk.
```
Disk /dev/sdb: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors                                                                                                                                                                                                                                                                      
Units: sectors of 1 * 512 = 512 bytes                                                                                                                                                                                                                                                                                                  
Sector size (logical/physical): 512 bytes / 4096 bytes                                                                                                                                                                                                                                                                                 
I/O size (minimum/optimal): 4096 bytes / 4096 bytes                                                                                                                                                                                                                                                                                    

Disklabel type: dos                                                                                                                                                                                                                                                                                                                    
Disk identifier: 0x52d8a984                                                                                                                                                                                                                                                                                                            
                                                                                                                                                                                                                                                                                                                                       
Device     Boot Start        End    Sectors   Size Id Type                                                                                                                                                                                                                                                                             
/dev/sdb1        2048 1757812735 1757810688 838.2G 83 Linux 
```
output of lsh -c disk
```
  *-disk                                                                                                                                                                                                                                                                                                                               
       description: ATA Disk                                                                                                                                                                                                                                                                                                           
       product: ST1000DM003-1CH1                                                                                                                                                                                                                                                                                                       
       vendor: Seagate                                                                                                                                                                                                                                                                                                                 
       physical id: 0.0.0                                                                                                                                                                                                                                                                                                              
       bus info: scsi@2:0.0.0                                                                                                                                                                                                                                                                                                          
       logical name: /dev/sdb                                                                                                                                                                                                                                                                                                          
       version: CC46                                                                                                                                                                                                                                                                                                                   
       serial: S1DBM9RC                                                                                                                                                                                                                                                                                                                
       size: 931GiB (1TB)                                                                                                                                                                                                                                                                                                              
       capabilities: partitioned partitioned:dos                                                                                                                                                                                                                                                                                       
       configuration: ansiversion=5 logicalsectorsize=512 sectorsize=4096 signature=52d8a984
```
My smb.conf config for my public share:```
[Public]                                                                                                                                                                                                                                                                                                                               
   path = /samba/public                                                                                                                                                                                                                                                                                                                
   writeable = yes                                                                                                                                                                                                                                                                                                                     
   guest ok = yes                                                                                                                                                                                                                                                                                                                      
   guest only = yes                                                                                                                                                                                                                                                                                                                    
   read only = no                                                                                                                                                                                                                                                                                                                      
   create mode = 0777                                                                                                                                                                                                                                                                                                                  
   directory mode = 0777                                                                                                                                                                                                                                                                                                               
   force user = nobody 
```

---

### Post by darkod on 2019-09-29
1. Is /samba/public emptry folder? You should only use empty folders as mount points.

2. Does it give you any error when trying to mount manually? Post the output of:
```
sudo mount -v /dev/sdb1 /samba/public
```

---

### Post by TheFu on 2019-09-29
And what about the fstab entry?
I'm confused as to how samba would care about mounting a disk.

Also, ```
lsblk -o name,size,type,fstype,mountpoint
```
would be helpful. When pasting output, please include a copy/paste for the exact command used.  Typos here are killers for understanding. There is a typo in the OP, clearly. Accuracy matters.

---

### Post by trexxit on 2019-09-29
output:```
rootbox@homeserver:~$ sudo mount -v /dev/sdb1 /samba/public                                                                                     

mount: /samba/public: wrong fs type, bad option, bad superblock on /dev/sdb1, missing codepage or helper program, or other error. 
```
Also```
rootbox@homeserver:~$ lsblk -o  name,type,fstype,mountpoint                                                                                     
NAME   TYPE FSTYPE   MOUNTPOINT                                                                                                                 
loop0  loop squashfs /snap/core/7270                                                                                                            
loop1  loop squashfs /snap/core/7713                                                                                                            
sda    disk                                                                                                                                     
&#9500;&#9472;sda1 part vfat     /boot/efi                                                                                                                  
&#9492;&#9472;sda2 part ext4     /                                                                                                                          
sdb    disk                                                                                                                                     
&#9492;&#9472;sdb1 part ext4    

```
I know commands and typos are important, forgive me, 5:30 am locally and was tired, the commands i entered (way earlier in the day)were checked for typos, but i still may have missed something.Will be sure to post commands from now on
The folder is empty for now, but I did want to mount the drive to /samba/public ( a separate drive,not my boot drive) so I guess it would then not be empty. I'm also guessing fstab was throwing me into emergency mode because of some formatting error, or something along those lines, as its still throwing the error when I try to mount it manually. using mount elsewhere```
rootbox@homeserver:/media$ ls                                                                                                                   
rootbox@homeserver:/media$ sudo mount -v /dev/sdb1 /media                                                                                       
mount: /media: wrong fs type, bad option, bad superblock on /dev/sdb1, missing codepage or helper program, or other error.                      
rootbox@homeserver:/media$ sudo mount -v /dev/sdb1 /mnt                                                                                         
mount: /mnt: wrong fs type, bad option, bad superblock on /dev/sdb1, missing codepage or helper program, or other error.                        
rootbox@homeserver:/media$  
```

---

### Post by trexxit on 2019-09-29
Reformatted and overwrote existing data with zeros, seems to have solved my silly problem, I tried this already, but I'm guessing my fdisk fu isn't quite up to par, thanks guys

---

