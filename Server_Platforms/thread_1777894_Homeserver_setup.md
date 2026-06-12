---
title: "Homeserver setup"
date: 2011-06-08
forum: Server Platforms
---

### Post by Captaincrash on 2011-06-08
So I finally got my server install up and running but now I want to be able to use it!

The plans are,

2x2TB raid1, sorted but unable to check it don't know how!

Samaba for file management, so far I have been umable to mount it in windows my conf file passes the check but I cant get it to work.

Squeezebox, install went fine runs but I have no music on my server.

DLNA, media tomb is installed but I am unable to see it from my tv on windows it works fine.

SVN, not attempted to setup yet.

The server is up and running in headless mode with ssh access but I have no actual functionality if anyone can help I will be most appreciative.

---

### Post by blind2314 on 2011-06-08
> **Captaincrash said:**
> So I finally got my server install up and running but now I want to be able to use it!
 
The plans are,
 
2x2TB raid1, sorted but unable to check it don't know how!
 
Samaba for file management, so far I have been umable to mount it in windows my conf file passes the check but I cant get it to work.
 
Squeezebox, install went fine runs but I have no music on my server.
 
DLNA, media tomb is installed but I am unable to see it from my tv on windows it works fine.
 
SVN, not attempted to setup yet.
 
The server is up and running in headless mode with ssh access but I have no actual functionality if anyone can help I will be most appreciative.
 
So the raid is setup but you can't check to see that it's setup? How do you know it's setup? Also, post your smb.conf file (using code tags please) so we can take a look. When you try to access it from the windows side, do you get a generic "network resource not found" error?
 
As for setting up a versioning utility, subversion and git both have very thorough tutorials available through Google. I'd suggest starting there and coming back with specific questions.

---

### Post by a2j on 2011-06-08
> **Captaincrash said:**
> 

2x2TB raid1, sorted but unable to check it don't know how!

Samaba for file management, so far I have been umable to mount it in windows my conf file passes the check but I cant get it to work.


RAID10 is better, I've heard.

Can you be more specific on the samba issue?

---

### Post by spynappels on 2011-06-08
> **a2j said:**
> RAID10 is better, I've heard.

But impossible with only 2 disks....

---

### Post by a2j on 2011-06-08
> **spynappels said:**
> But impossible with only 2 disks....

I guess I have some magic on my server and laptop.... cuz it works for me just fine...  :)

---

### Post by spynappels on 2011-06-08
> **a2j said:**
> I guess I have some magic on my server and laptop.... cuz it works for me just fine...  :)

Very interesting, as the minimum number of disks for a RAID 10 array is 4. To be more precise, you need 4 RAID partitions, but even if you use 2 partitions per disk, at best you end up with the exact same as RAID 1 and at worst you have no redundancy at all.

I'd be very interested in seeing what magic happens on your server....:)

---

### Post by Captaincrash on 2011-06-08
Here is the output from fdisk

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      243202  1953514583+  ee  GPT

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      243202  1953514583+  ee  GPT

Disk /dev/sdc: 16.0 GB, 16000221184 bytes
255 heads, 63 sectors/track, 1945 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000235ec

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        1832    14707712   83  Linux
/dev/sdc2            1832        1946      914433    5  Extended
/dev/sdc5            1832        1946      914432   82  Linux swap / Solaris

Disk /dev/md0: 2000.4 GB, 2000397703168 bytes
2 heads, 4 sectors/track, 488378345 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table

And the samba.conf

[global]
    ; General server settings
    netbios name = GANDALF
    server string =
    workgroup = HOME
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_$

    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = yes

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
;[homes]
    ;valid users = %S
    ;create mode = 0600
    ;directory mode = 0755
    ;browseable = no
    ;read only = no
    ;veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
    ;path = /var/lib/samba/netlogon
    ;admin users = Administrator
    ;valid users = %U
    ;read only = no

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
    ;path = /var/lib/samba/profiles
    ;valid users = %U
    ;create mode = 0600
    ;directory mode = 0700
    ;writeable = yes
    ;browseable = no

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
[print$]
    path = /var/lib/samba/printers
    browseable = yes
    guest ok = yes
    read only = yes
    write list = root
    create mask = 0664
    directory mask = 0775

[printers]
    path = /tmp
    printable = yes
    guest ok = yes
    browseable = no

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
    ;path = /media/cdrom
    ;browseable = yes
    ;browseable = yes
    ;read only = yes
    ;guest ok = yes

[MyFiles]
    path = /media/samba/
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = neil
    force group = HOME

I have followed the instructions online how to setup the windows machine registry to get things going.

---

### Post by a2j on 2011-06-08
> **spynappels said:**
> Very interesting, as the minimum number of disks for a RAID 10 array is 4. To be more precise, you need 4 RAID partitions, but even if you use 2 partitions per disk, at best you end up with the exact same as RAID 1 and at worst you have no redundancy at all.

I'd be very interested in seeing what magic happens on your server....:)


just two 1.5T green wd hdds with single partition on each of them. pretty good speeds. iirc, it works like RAID0 when reading data, and RAID1 when writing. software raid, btw. about to expend to 4 drives and have "true" RAID10.

---

### Post by collisionystm on 2011-06-08
> A nonstandard definition of "RAID 10" was created for the Linux MD driver[[4]]("http://en.wikipedia.org/wiki/Nested_RAID_levels#cite_note-brown-neil-3") ; RAID 10 as recognized by the storage industry association and as generally implemented by RAID controllers is a **RAID 0 array of mirrors (which may be two way or three way mirrors)** [[5]]("http://en.wikipedia.org/wiki/Nested_RAID_levels#cite_note-4") and requires a minimum of 4 drives. Linux "RAID 10" can be implemented with as few as two disks. 

[B][http://en.wikipedia.org/wiki/Nested_RAID_levels#RAID_10_.28RAID_1.2B0.29](http://en.wikipedia.org/wiki/Nested_RAID_levels#RAID_10_.28RAID_1.2B0.29)

[/B]But I will still stick with my 4 Drive Raid 1+0   =)

---

### Post by chadhs on 2011-06-20
I'm going to resist joining in on the RAID discussion as that appears to be settled.
As far as your subversion (SVN) setup goes, there is good documentation in the official server guide on ubuntu.com.
I did write a very simple step by step blog entry on how to set up SVN as well here -> [http://www.chadstovern.com/how-to-set-up-a-basic-subversion-svn-server-on-ubuntu](http://www.chadstovern.com/how-to-set-up-a-basic-subversion-svn-server-on-ubuntu)

---

