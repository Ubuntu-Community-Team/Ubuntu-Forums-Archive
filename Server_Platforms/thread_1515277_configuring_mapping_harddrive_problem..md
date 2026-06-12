---
title: "configuring mapping harddrive problem."
date: 2010-06-22
forum: Server Platforms
---

### Post by kanolsen on 2010-06-22
I have problems configuring fstab and samba to work after reinstall of ubuntu 10.04.

I have managed to get it to work before, in this [post.]("http://ubuntuforums.org/showthread.php?t=1379235")

What I want to do is get my ntfs formatted drive (sdb1) and home folder to be mapped from my other computers, but I can't get it to work, I get the following error when starting ubuntu: 
an error occurred while mapping /media/1TBsamsung og /media/store

And samba doesn't seem to be running.

**root@ubuntu:/home/kanolsen# service samba status**
samba: unrecognized service


**root@ubuntu:/home/kanolsen# fdisk -l**

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b987c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *           1      121601   976759009+   5  Extended
/dev/sda5          121039      121601     4522266   82  Linux swap /
Solaris
/dev/sda6               1        2433    19534848   83  Linux
/dev/sda7            2433      121038   952699904   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x31f4aa6f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121602   976759808    7  HPFS/NTFS
root@ubuntu:/home/kanolsen# nano /etc/samba/smb.conf

**root@ubuntu:/home/kanolsen# testparm -s**
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[ntfs]"
Loaded services file OK.
ERROR: lock directory /var/run/samba does not exist
ERROR: pid directory /var/run/samba does not exist
Server role: ROLE_STANDALONE
[global]
        workgroup = HJEMME
        server string = %h server (Samba, Ubuntu)
        map to guest = Bad User
        obey pam restrictions = Yes
        pam password change = Yes
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\s*\spassword:* %n\n
        *Retype\snew\s*\spassword:* %n\n
        *password\supdated\ssuccessfully* .
        unix password sync = Yes
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        dns proxy = No
        usershare allow guests = Yes
        panic action = /usr/share/samba/panic-action %d

[printers]
        comment = All Printers
        path = /var/spool/samba
        create mask = 0700
        printable = Yes
        browseable = No
        browsable = No

[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers

[ntfs]
        comment = Public Folder
        path = /media/ntfs
        force user = nobody
        force group = nogroup
        read only = No
        create mask = 0777
        directory mask = 0777
        guest ok = Yes

**root@ubuntu:/home/kanolsen# cat /etc/fstab**
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique
identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=69e2c58b-3c9c-4dd7-a117-d4599d2322c6 /               ext4   
errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=44bb1e07-d555-4a06-b11e-d632a9ee255b /home           ext4   
defaults        0       2
# swap was on /dev/sda5 during installation
UUID=35bcfb82-911f-42ad-8637-e35355bf9611 none            swap    sw    
         0       0
/dev/sda  /media/store  ext3  user,suid,dev,exec  0  0
/dev/sdb1 /media/1TBsamsung ntfs-3G defaults 0 0
root@ubuntu:/home/kanolsen# blkid -c /dev/null
/dev/sda5: UUID="35bcfb82-911f-42ad-8637-e35355bf9611" TYPE="swap" 
/dev/sda6: UUID="69e2c58b-3c9c-4dd7-a117-d4599d2322c6" TYPE="ext4" 
/dev/sda7: UUID="44bb1e07-d555-4a06-b11e-d632a9ee255b" TYPE="ext4" 
/dev/sdb1: LABEL="1TBsamsung" UUID="7C209AF2209AB31E" TYPE="ntfs" 
root@ubuntu:/home/kanolsen#

---

### Post by Ryan Dwyer on 2010-06-22
Why are you trying to mount sda into /media/store? Is that a mistake?

---

### Post by kanolsen on 2010-06-22
I thought I had to to get it to work, that's what the[ manual ]("http://www.howtoforge.com/ubuntu-home-fileserver-p3")stated to do.

---

### Post by Ryan Dwyer on 2010-06-22
I don't see where you copied that line from.

For starters, your fstab line should be something like sda6 rather than just sda. You also chose ext3, but none of your partitions from your fdisk are using ext3.

You need to decide what you're actually trying to do. Are you trying to mount two partitions or just one? If it's just one, remove the sda line from your fstab.

---

### Post by kanolsen on 2010-06-22
I have realised I'm out of my depth here, so I clearly need help digging myself out of this mess I've created.

I read it in point 8 Install The Second Hard Disk. 

But I see I just can't copy/paste it, I have to modify it correctly. 

But what I try to do is:
1. get the NTFS formatted drive sdb1 to be mounted in fstab, so I can mapp it up from my other computers. How do I do that?
2. get my /home directory to be mapped up from my other computers as well.

Could you give me any tips on where I go wrong in my setup?

Thanks in advance
Kanolsen

---

### Post by Ryan Dwyer on 2010-06-22
I think their tutorial is wrong. I think the part that says mount /dev/hda /media/store should be hda1, not hda.

Anyway, your home directory is already mounted automatically. I can see that because one of the lines in your fstab has /home in it.

Remove the /dev/sda /media/store line from your fstab. On the /dev/sdb1 line, change ntfs-3G to ntfs-3g (not sure if it's case sensitive, but doesn't hurt to make it lowercase). When you reboot, your Samsung disk should be mounted to /media/1TBsamsung automatically.

In your smb.conf, change the [ntfs] path from /media/ntfs to /media/1TBsamsung. Then run sudo /etc/init.d/smbd restart (you can probably use service start smb or service start smbd as well).

---

### Post by kanolsen on 2010-06-22
Thanks, I almost got it to work now.
I managed to map up my NTFS drive correctly. The relevant files are now as:
I did: **mkdir /media/store**

**root@ubuntu:/home/kanolsen# sudo nano /etc/fstab**
.
.
# /home was on /dev/sda7 during installation
UUID=44bb1e07-d555-4a06-b11e-d632a9ee255b /home           ext4    defaults     $
.
.
/dev/sdb1 /media/store ntfs-3g defaults 0 0

**root@ubuntu:/home/kanolsen# nano /etc/samba/smb.conf**
The relevant changes are as following:
[global]
.
   workgroup = HJEMME
.
[homes]
   comment = Home Directories
   browseable = yes
.
   read only = NO
.
   create mask = 0700
.
   directory mask = 0700
.
#   valid users = %S

[ntfs]
comment = Public Folder
path = /media/store
# path = /media/ntfs
public = yes
guest ok = yes
writable = yes
create mask = 0777
directory mask = 0777
force user = nobody
force group = nogroup

The odd thing is that from windows I mount it with \\servername\ntfs I can't understand why I can that. By my logic I would assume \\servername\store.

And I can't map my homefolder from windows by \\servername\kanolsen it prompts me for a username/password and when I enter, it claim it's already in use.

Sorry for bothering you so much, but I really want to finally understand how this works, once and for all. 

Kanolsen

---

### Post by Ryan Dwyer on 2010-06-22
The share is called ntfs because you have [ntfs] in your smb.conf. That's the share name.

Have a look at the log files in /var/log/samba/ to see what's going on with the username and password issue.

---

