---
title: "Samba Help - worked fine and then went belly up"
date: 2021-05-12
forum: Server Platforms
---

### Post by peeweejd on 2021-05-12
ubuntu 20.04.2
samba 4.11.6-Ubuntu

Can anyone offer any advice to fix my Samba share problem?

I run this computer as a Plex server.  It has a SSD that runs the OS and such, and a HDD that has all my Plex media files on it.  I run the server headless and use a Samba share to manage files on the HDD (add/change/delete) from various Windows 10 PCs and Android devices on the local network.  One evening last week I added some files using the Samba share, and the next morning I tried again and could not connect to the Samba share.

[LIST]
[*]The Plex server is running fine and can access the media files on the HDD
[*]I can see the server on my Windows machine and Android devices.
[*]sudo ufw status gives Status: inactive
[*]I have stopped and started the Samba service using sudo service smbd stop and sudo service smbd start.  Both commands ran with no errors.
[*]I updated everything and have restarted the server multiple times.
[*]I uninstalled and re-installed Samba (including a fresh smb.conf file)
[/LIST]

Sudo smbstatus gives the result below (no shares are listed)
```
Samba version 4.11.6-Ubuntu
PID     Username     Group        Machine                                   Protocol Version  Encryption           Signing
----------------------------------------------------------------------------------------------------------------------------------------

Service      pid     Machine       Connected at                     Encryption   Signing
---------------------------------------------------------------------------------------------

No locked files
```

This is the share listed in my /etc/samba/smb.conf file
```
[hda]
   path = /media/hda/sharehda
   read only = no
   browsable = yes
   public = yes

```

---

### Post by slickymaster on 2021-05-12
*Thread moved to **Server Platforms**.*

---

### Post by LHammonds on 2021-05-12
Have you run this command yet to verify the syntax in your config file?
```
testparm
```

LHammonds

---

### Post by peeweejd on 2021-05-12
> **LHammonds said:**
> Have you run this command yet to verify the syntax in your config file?
```
testparm
```

LHammonds

```
Load smb config files from /etc/samba/smb.conf
Loaded services file OK.
Server role: ROLE_STANDALONE

Press enter to see a dump of your service definitions

# Global parameters
[global]
        log file = /var/log/samba/log.%m
        logging = file
        map to guest = Bad User
        max log size = 1000
        obey pam restrictions = Yes
        panic action = /usr/share/samba/panic-action %d
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:                                                                                                                     * %n\n *password\supdated\ssuccessfully* .
        passwd program = /usr/bin/passwd %u
        server role = standalone server
        server string = %h server (Samba, Ubuntu)
        usershare allow guests = Yes
        idmap config * : backend = tdb


[printers]
        browseable = No
        comment = All Printers
        create mask = 0700
        path = /var/spool/samba
        printable = Yes


[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers


[hda]
        guest ok = Yes
        path = /media/hda/sharehda
        read only = No

```

---

### Post by rsteinmetz70112 on 2021-05-12
Are you sure the path is correct? Shouldn't it be a partition rather than the whole disk?
What does lsblk show?

---

### Post by peeweejd on 2021-05-12
> **rsteinmetz70112 said:**
> Are you sure the path is correct? Shouldn't it be a partition rather than the whole disk?
What does lsblk show?

The drive only has one partition and I share the whole thing (it just holds media files for the Plex server).  The OS is installed on a solid state drive.

The path works
```
peeweejd@plexy:/$ cd /media/hda/sharehda
peeweejd@plexy:/media/hda/sharehda$ ls
DCIM  plexmedia

```

lsblk output
```
peeweejd@plexy:/$ lsblk
NAME                      MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
loop0                       7:0    0  67.6M  1 loop /snap/lxd/20326
loop1                       7:1    0  55.5M  1 loop /snap/core18/1988
loop2                       7:2    0  32.3M  1 loop /snap/snapd/11588
loop3                       7:3    0  55.5M  1 loop /snap/core18/1997
loop4                       7:4    0  32.3M  1 loop /snap/snapd/11402
loop5                       7:5    0  70.4M  1 loop /snap/lxd/19647
sda                         8:0    0 465.8G  0 disk
&#9492;&#9472;sda1                      8:1    0 465.8G  0 part /media/hda
sdb                         8:16   0 465.8G  0 disk
nvme0n1                   259:0    0 232.9G  0 disk
&#9500;&#9472;nvme0n1p1               259:1    0     1M  0 part
&#9500;&#9472;nvme0n1p2               259:2    0     1G  0 part /boot
&#9492;&#9472;nvme0n1p3               259:3    0 231.9G  0 part
  &#9492;&#9472;ubuntu--vg-ubuntu--lv 253:0    0   116G  0 lvm  /

```

---

### Post by Morbius1 on 2021-05-12
The local server user "nobody" has to have write access to sharehda and at least execute permissions on media and hda so what are the permissions on the tree:
```
ls -al /media/hda
```

---

### Post by peeweejd on 2021-05-12
> **Morbius1 said:**
> The local server user "nobody" has to have write access to sharehda and at least execute permissions on media and hda so what are the permissions on the tree:
```
ls -al /media/hda
```

I'm not good a permissions...

```
peeweejd@plexy:/$ ls -al /media/
total 16
drwxr-xr-x  4 root root 4096 Jan 15 17:48 .
drwxr-xr-x 20 root root 4096 Nov  7  2020 ..
drwxr-xr-x  4 root root 4096 Nov  7  2020 hda
drwxr-xr-x  2 root root 4096 Jan 15 17:48 hdb
```

```
peeweejd@plexy:/$ ls -al /media/hda
total 28
drwxr-xr-x 4 root   root     4096 Nov  7  2020 .
drwxr-xr-x 4 root   root     4096 Jan 15 17:48 ..
drwx------ 2 root   root    16384 Nov  6  2020 lost+found
drwxrwxrwx 4 nobody nogroup  4096 Apr 10 16:44 sharehda
```

```
peeweejd@plexy:/$ ls -al /media/hda/sharehda
total 16
drwxrwxrwx 4 nobody   nogroup  4096 Apr 10 16:44 .
drwxr-xr-x 4 root     root     4096 Nov  7  2020 ..
drwxrwxr-x 6 peeweejd peeweejd 4096 Apr 10 16:48 DCIM
drwxrwxr-x 9 peeweejd peeweejd 4096 Apr  1 20:25 plexmedia
```

---

### Post by Morbius1 on 2021-05-12
THe easiest way out of this is to edit your share definition to make all network connections - [COLOR=#ff0000]**at least to this share**[/COLOR] - as peeweejd:

> [hda]
   path = /media/hda/sharehda
   read only = no
   browsable = yes
   public = yes
   [COLOR=#ff0000]**force user = peeweejd**[/COLOR]
Then restart smbd:
```
sudo service smbd restart
```

Right now no one has write access to the plexmedia folder but peeweejd. The change above will ensure it.

---

### Post by peeweejd on 2021-05-12
> **Morbius1 said:**
> THe easiest way out of this is to edit your share definition to make all network connections - [COLOR=#ff0000]**at least to this share**[/COLOR] - as peeweejd:


Then restart smbd:
```
sudo service smbd restart
```

Right now no one has write access to the plexmedia folder but peeweejd. The change above will ensure it.

Thanks for helping so much.  I don't think it's working still.

testparm shows the same output as earlier (except the force user line I just added).

smbstatus does not show the share still.  I believe it should show the [hda] part in there, correct?
```
peeweejd@plexy:/$ sudo smbstatus

Samba version 4.11.6-Ubuntu
PID     Username     Group        Machine                                   Protocol Version  Encryption           Signing
----------------------------------------------------------------------------------------------------------------------------------------

Service      pid     Machine       Connected at                     Encryption   Signing
---------------------------------------------------------------------------------------------

No locked files
```

edit: I believe it's working again.  I restarted the client PC and I am able to connect.  I cannot connect on my android devices though.  I will look into this separately.

---

### Post by Morbius1 on 2021-05-12
smbstatus will only show something if someone accesses the server and it's share.

---

