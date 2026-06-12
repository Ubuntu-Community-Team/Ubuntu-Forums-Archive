---
title: "Command-line backup CD burning not cooperating!"
date: 2006-12-15
forum: Server Platforms
---

### Post by kenquad on 2006-12-15
Hi all:

Tried tacking this onto a previous thread in Desktop but I guess it didn't really belong there anyway.  The problem is that my CD burned, an older Sony, is not fully recognized by cdrecord.
 ```
sudo cdrecord -scanbus
```
returns
```
cdrecord: Warning: Running on Linux-2.6.15-23-server
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
cdrecord: No such file or directory. Cannot open '/dev/pg*'. Cannot open SCSI driver.
cdrecord: For possible targets try 'cdrecord -scanbus'.
cdrecord: For possible transport specifiers try 'cdrecord dev=help'.
cdrecord: 
cdrecord: For more information, install the cdrtools-doc
cdrecord: package and read /usr/share/doc/cdrecord/README.ATAPI.setup .
Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.
```

I also ran
```
sudo cdrecord dev=/dev/hdc -checkdrive
```
with the following result:
```
cdrecord: Warning: Running on Linux-2.6.15-23-server
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: '/dev/hdc'
devname: '/dev/hdc'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
cdrecord: Warning: using inofficial version of libscg (debian-0.8debian2 '@(#)scsitransp.c	1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

Using libscg version 'debian-0.8debian2'.
Device type    : Removable CD-ROM
Version        : 0
Response Format: 1
Vendor_info    : 'SONY    '
Identifikation : 'CD-RW  CRX140E  '
Revision       : '1.0n'
Device seems to be: Generic mmc CD-RW.
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-2 SWABAUDIO 
Supported modes: TAO PACKET SAO SAO/R96R RAW/R96R

```

It looks to me like cdrecord can see my drive and even tell it's a burner.  Maybe the problem is with SCSI vs. IDE.  I don't really know how the program addresses that.  Any help would be appreciated!

Merry Christmas!

Kenquad

---

### Post by tturrisi on 2006-12-15
try dpkg-reconfigure cdrecord
There may be options set that prevent it from being used, such as requiring root or is not configured for all users.

---

### Post by kenquad on 2006-12-22
Thanks for the thought, but running that (and selecting to "install" with suid) doesn't change the results.

---

