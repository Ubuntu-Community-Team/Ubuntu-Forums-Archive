---
title: "[Samba] Change location of /var/lib/samba/secrets.tdb"
date: 2009-11-30
forum: Server Platforms
---

### Post by eremos on 2009-11-30
Hi all,

I've got my media center PC running off a USB drive and as such want to minimize writes to the boot disk.

I've moved all the oft-written bits to tmpfs or to physical disks, but samba is giving me trouble.

I've changed my samba settings as follows:

from:
state directory = /var/lib/samba
usershare path = /var/lib/samba/usershares

to:
state directory = /mnt/tank/home/samba
usershare path = /mnt/tank/home/samba/usershares

..and copied all the data across.

But Samba fails to start and according to the log is still looking for /var/lib/samba/secrets.tdb

So, does anyone know where I can change the location of the secrets file?

As a workaround for now I've just created a symlink in /var/lib to point towards the actual data location.

Thanks

---

### Post by capscrew on 2009-11-30
> **eremos said:**
> Hi all,

I've got my media center PC running off a USB drive and as such want to minimize writes to the boot disk.

I've moved all the oft-written bits to tmpfs or to physical disks, but samba is giving me trouble.

I've changed my samba settings as follows:

from:
state directory = /var/lib/samba
usershare path = /var/lib/samba/usershares

to:
state directory = /mnt/tank/home/samba
usershare path = /mnt/tank/home/samba/usershares

..and copied all the data across.

But Samba fails to start and according to the log is still looking for /var/lib/samba/secrets.tdb

So, does anyone know where I can change the location of the secrets file?

As a workaround for now I've just created a symlink in /var/lib to point towards the actual data location.

Thanks

Just a guess here; you have configured Samba via Nautilus and not via the /etc/samba/smb.conf file.  Use the smb.conf file to configure your global settings and shares.  There is a line to configure .tdb files to be placed in non standard places in the file system.

I believe the smb.conf file has precedence over the /var/lib/samba files.  You might try just configuring the .tdb location.

---

### Post by eremos on 2009-11-30
> **capscrew said:**
> Just a guess here; you have configured Samba via Nautilus and not via the /etc/samba/smb.conf file.  Use the smb.conf file to configure your global settings and shares.  There is a line to configure .tdb files to be placed in non standard places in the file system.

I believe the smb.conf file has precedence over the /var/lib/samba files.  You might try just configuring the .tdb location.

I have actually edited /etc/samba/smb.conf directly. Here's the whole global section:

```
[global]
   workgroup = WORKGROUP
   log file = /var/log/samba/log.%m
   max log size = 1000
   syslog = 0
   panic action = /usr/share/samba/panic-action %d
   map to guest = bad user
   guest account = media
   state directory = /mnt/tank/home/samba
   usershare path = /mnt/tank/home/samba/usershares

```

I used testparm -v to find all the parameters that default to something in /var/lib/samba and changed them.

Thanks
Henning

---

### Post by capscrew on 2009-11-30
Did that solve your issue?

---

### Post by eremos on 2009-11-30
Nope, this is what I'd done before which results in samba failing to start.

Thanks

---

### Post by capscrew on 2009-11-30
Is /mnt/tank mounted *_locally_*?  By that I mean either through a mount command or fstab.   Sometimes things are not Nautilus aware.

---

### Post by eremos on 2009-11-30
Yep, mounted locally.

Not sure where Nautilus comes in? Here's my samba log.

```
  smbd version 3.4.0 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2009
[2009/11/30 18:53:31,  0] printing/print_cups.c:103(cups_connect)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2009/11/30 18:53:31,  0] printing/print_cups.c:103(cups_connect)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2009/11/30 18:53:31,  0] passdb/secrets.c:71(secrets_init)
  Failed to open /var/lib/samba/secrets.tdb
[2009/11/30 18:53:31,  0] passdb/secrets.c:71(secrets_init)
  Failed to open /var/lib/samba/secrets.tdb
[2009/11/30 18:53:31,  0] smbd/server.c:1168(main)
  ERROR: smbd can not open secrets.tdb

```

I want it to be looking at /mnt/tank/home/samba/secrets.tdb

Henning

---

### Post by capscrew on 2009-11-30
> Not sure where Nautilus comes in?

You did configure the shares via the GUI; correct?

Samba and Gnome (Nautilus) do things slightly different.

What is the output from the CLI of the command:```
mount
```

Edit: Samba itself puts nothing at /var/lib/samba.  That is the home of Gnome created configs.

---

### Post by eremos on 2009-11-30
Nopes, shares all configured directly in file:

/etc/samba/smbd.conf:```

[global]
   workgroup = WORKGROUP
   log file = /var/log/samba/log.%m
   max log size = 1000
   syslog = 0
   panic action = /usr/share/samba/panic-action %d
   map to guest = bad user
   guest account = media

[media]
   path = /mnt/tank/media
   guest ok = yes
   read only = no

[home]
path = /mnt/tank/home/media
guest ok = yes
read only = no
browseable = no

[drop]
path = /mnt/tank/home/media/drop
guest ok = yes
read only = no
browseable = yes

[logs]
path = /var/log/
guest ok = yes
read only = yes
browseable = yes

```

```
media@htpc:~$ mount
/dev/sde1 on / type ext4 (rw,noatime,nodiratime,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /tmp type tmpfs (rw,noatime)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/dev/md0 on /mnt/tank type ext3 (rw,noatime)
none on /var/log type tmpfs (rw,noatime)
none on /var/tmp type tmpfs (rw,noatime)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/sdd1 on /mnt/old type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)

```

---

### Post by capscrew on 2009-11-30
Very strange.

How did the original```
state directory = /var/lib/samba
usershare path = /var/lib/samba/usershares

```
get to this location?

I have Samba running on 2 hosts and there is nothing in my /var/lib/samba.  I configured everything manually.

As I said Gnome (GIO specifically) Nautilus uses that location.

I'm stumped   :-(

---

### Post by eremos on 2009-11-30
Hmm. /var/lib/samba is the samba default as far as I can tell. Weird that yours is empty. What does ```
testparm -v | grep "/var"
``` give you?

I should have mentioned before - this is on 9.10.

It's probably better to just keep it as a symlink then, as it is now, since clearly things other than samba expect these files to be in this dir.

Thanks for the help.

---

### Post by capscrew on 2009-11-30
> **eremos said:**
> Hmm. /var/lib/samba is the samba default as far as I can tell. Weird that yours is empty. What does ```
testparm -v | grep "/var"
``` give you?

I should have mentioned before - this is on 9.10.

It's probably better to just keep it as a symlink then, as it is now, since clearly things other than samba expect these files to be in this dir.

Thanks for the help.

I'm using 8.04 (Hardy), but I have kept up on the latest stuff.  I can see you have a setting for *_usershares_*.  This can only be for GUI use.  it allows for users to create their own shares.

I think you are right; the symlinks are the way for right now.

Sorry I could not help more.

Edit:  I don't have any references to /var from testparm

---

### Post by capscrew on 2009-11-30
> [2009/11/30 18:53:31,  0] passdb/secrets.c:71(secrets_init)
  Failed to open /var/lib/samba/secrets.tdb


just a thought here. The log says it couldn't *open */var/lib/samba/secrets.tdb.  I wonder if this is a permissions issue.

---

### Post by eremos on 2009-11-30
Nah, the file doesn't exist at all in that location (moved away).

---

### Post by capscrew on 2009-11-30
> **eremos said:**
> Nah, the file doesn't exist at all in that location (moved away).

Right, my confusion.  

I just read the Samba section of the Ubuntu server guide.  The author uses symlinks to move the location of the secrets.tdb file.

---

### Post by cur8or on 2012-09-10
Sorry to resurrect an old thread, but I needed to move all Samba tdb data to shared storage so I can use VCS HA with Samba configured with AD/RID backend. Here is what I had to add to smb.conf to do this, in case anyone is trying to do the same:

        username map = /samba/smb1/samba/username.map
        smb passwd file = /samba/smb1/locks/private/smbpasswd
        private dir = /samba/smb1/locks/private/
        usershare path = /samba/smb1/locks/usershares
        log file = /samba/smb1/logs/log.%m
        pid directory = /samba/smb1/locks/
        lock directory = /samba/smb1/locks/
        cache directory = /samba/smb1/locks/
        state directory = /samba/smb1/locks/

Change directories to what you need.

---

