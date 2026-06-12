---
title: "Unable to use cd/dvd drive from cli"
date: 2011-02-21
forum: Server Platforms
---

### Post by gabriel403 on 2011-02-21
I'm trying to set up a script for weekly burning of some files to a cd,
however most of the time the system is unable to find the drive to burn

when I do 
```
wodim --devices
``` 

I get back 

```
wodim: Overview of accessible drives (0 found) :
-------------------------------------------------------------------------
-------------------------------------------------------------------------
```

But when I do lshw I find this entry

```
           *-cdrom
                description: DVD-RAM writer
                physical id: 1
                bus info: scsi@3:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                capabilities: audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: status=open
```

This is on lucid

```
root@machine:~# lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 10.04.1 LTS
Release:	10.04
Codename:	lucid
```

```
cat /proc/version
Linux version 2.6.32-27-server (buildd@crested) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #49-Ubuntu SMP Thu Dec 2 02:05:21 UTC 2010
```

---

### Post by cariboo on 2011-02-21
I don't have a cd drive connected on my server, as there isn't enough room in the case, but when I do, it is detected as /dev/sr0

You can see what device the cdrom is linked to by typing the following command:

```
ls -l /dev/cdrom
```

this is what I get:

```
ls -l /dev/cdrom
lrwxrwxrwx 1 root root 3 2011-02-21 10:54 /dev/cdrom -> sr0
```

---

### Post by gabriel403 on 2011-02-22
> **cariboo907 said:**
> I don't have a cd drive connected on my server, as there isn't enough room in the case, but when I do, it is detected as /dev/sr0

You can see what device the cdrom is linked to by typing the following command:

```
ls -l /dev/cdrom
```

this is what I get:

```
ls -l /dev/cdrom
lrwxrwxrwx 1 root root 3 2011-02-21 10:54 /dev/cdrom -> sr0
```

so even though wodim can't detect it I can still burn to it?

---

### Post by mciverza on 2011-02-22
According to "man wodim"
If a file /etc/wodim.conf exists, the parameter to the dev= option may also be a drive name label in that file (see FILES section).

And ...
"If no dev option is present, wodim will try to get the device from the CDR_DEVICE environment."

or you can pass the option dev=/dev/sr0 to wodim when you run it

---

