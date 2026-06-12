---
title: "Ubuntu Server 18.04 seeing more disk space than physically present"
date: 2019-09-23
forum: Server Platforms
---

### Post by elzilcho2 on 2019-09-23
I'm trying to install Ubuntu 18.04 on a server with a 18T raid5 virtual disk.  The raid controller reports there is only 18T of space.  Other OS'es report the same, but when I try to install 18.04 and 19.04 it fails.  Setup is reporting the virtual disk is 139.639T.  If I manually create partitions and keep them below the 18T size, it will install.  If I use the entire disk and LVM, it states an error has occurred and the install fails.  How can I figure out why the installer is incorrectly reporting the virtual disk size?

The error in the installer output is:

curtin.util.ProcessExecutionError:  Unexpected error while running command,
Command:  ['sgdisk', '--new', '3:393472:37484265215', '--typecode=3:8300', '/dev/sda']
Exit code:  4
Reason: -
Stdout:  ''
Stderr:  Could not create partition 3 from 393472 to 37484265215
            Could not change partition 3's type code to 8300!
            Error encountered; no saving changes

Unexpected error while running command.
Command:  ['sgdisk',  '--new', '3:393472:37484265215',  '--typecode=3:8300', '/dev/sda']
Exit code:  4
Reason: -
Stdout: ''
Stderr:  Could not create partition 3 from 393472 to 37484265215
            Could not change partition 3's type code to 8300!
            Error encountered; no saving changes


Stderr: ''

---

### Post by Skaperen on 2019-09-24
can you boot up the live ubuntu (the "try ubuntu" option)?  then try to start up a terminal session.  from there, some special commands can be used to examine the virtual disk and related information.  the first command to do is "[COLOR=#0000cd][FONT=courier new]**cat /proc/partitions**[/FONT][/COLOR]".  please post the output between code tags.

---

### Post by elzilcho2 on 2019-09-24
output from "cat /proc/partitions"

```

major minor  #blocks  name

   7             0       1860396 loop0
   7             1           93172 loop1
   7             2           35368 loop2
   8             0 18742132736 sda
   8             1         524288 sda1
   8             2       1048576 sda2
 11             0       1949696 sr0
 11             1       1048575 sr1
 11             2       1048575 sr2
 11             3       1048575 sr3

```

---

### Post by darkod on 2019-09-25
You could also check things with:
```
lsblk
sudo parted /dev/sda unit GiB print
```

At the end of the day, I know you want to discover why this happens, but if it works with precreated partitions then simply create the partitions before hand and install.

My biggest worry would be if the size mismatch means that maybe it is not reading your raid controller correctly. Is the controller doing real HW raid or some sort of SW fakeraid?

Maybe driver issue? Have you confirmed the controller is supported in the ubuntu version you are trying to use?

---

### Post by LHammonds on 2019-09-27
I assume you are using the alternative (aka traditional) installer ISO "ubuntu-18.04.3-server-amd64.iso" because of RAID instead of the default installer ISO "ubuntu-18.04.3-live-server-amd64.iso"

[Reference link](https://ubuntuforums.org/showthread.php?t=2390785)

LHammonds

---

