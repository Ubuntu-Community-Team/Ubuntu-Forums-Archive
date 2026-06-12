---
title: "needrestart skipped, dkpg failed"
date: 2022-12-01
forum: Server Platforms
---

### Post by audiodef2 on 2022-12-01
For the past month or so, I've been seeing messages like these after upgrades:

```

Errors were encountered while processing:
 grub-efi-amd64-signed
 shim-signed
needrestart is being skipped since dpkg has failed

```

What causes this and how do I fix it?

---

### Post by audiodef2 on 2022-12-01
Here's more output after another update:

```

Preparing to unpack .../libtiff5_4.3.0-6ubuntu0.3_amd64.deb ...
Unpacking libtiff5:amd64 (4.3.0-6ubuntu0.3) over (4.3.0-6ubuntu0.2) ...
Setting up grub-efi-amd64-signed (1.182~22.04.1+2.06-2ubuntu10) ...
mount: /var/lib/grub/esp: special device /dev/sda15 does not exist.
dpkg: error processing package grub-efi-amd64-signed (--configure):
 installed grub-efi-amd64-signed package post-installation script subprocess returned error exit status 32
dpkg: dependency problems prevent configuration of shim-signed:
 shim-signed depends on grub-efi-amd64-signed | grub-efi-arm64-signed; however:
  Package grub-efi-amd64-signed is not configured yet.
  Package grub-efi-arm64-signed is not installed.

dpkg: error processing package shim-signed (--configure):
 dependency problems - leaving unconfigured
Setting up libtiff5:amd64 (4.3.0-6ubuntu0.3) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                           Processing triggers for libc-bin (2.35-0ubuntu3.1) ...
Errors were encountered while processing:
 grub-efi-amd64-signed
 shim-signed
needrestart is being skipped since dpkg has failed


```

PS The forum's software wouldn't let me edit my post, complaining that my post was too short and I should lengthen it to "at least 1 characters." Just putting that out there in case it's something an admin wants to look into.

---

### Post by Bashing-om on 2022-12-01
audiodef2; Hello :D

I'll start this ball rolling >>

> 
mount: /var/lib/grub/esp: special device /dev/sda15 does not exist.


makes one wonder what is defined and the where.
Please - as a place to start the hunt - post back the results of terminal commands:
```

sudo fdisk -lu
cat /etc/fstab

```

see where we go from here.

[INDENT]there is a process
[/INDENT]

---

### Post by audiodef2 on 2022-12-02
fdisk -lu:
```

Disk /dev/loop0: 237.56 MiB, 249102336 bytes, 486528 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop1: 4 KiB, 4096 bytes, 8 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop2: 63.24 MiB, 66314240 bytes, 129520 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop3: 237.51 MiB, 249049088 bytes, 486424 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop4: 346.33 MiB, 363151360 bytes, 709280 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop5: 91.69 MiB, 96141312 bytes, 187776 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop6: 49.62 MiB, 52031488 bytes, 101624 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Disk /dev/sda: 1.82 TiB, 2000398934016 bytes, 3907029168 sectors
Disk model: ST2000NM0033-9ZM
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x6212759a

Device     Boot    Start        End    Sectors  Size Id Type
/dev/sda1           2048   16779263   16777216    8G fd Linux raid autodetect
/dev/sda2       16779264   18876415    2097152    1G fd Linux raid autodetect
/dev/sda3       18876416 3907027119 3888150704  1.8T fd Linux raid autodetect


Disk /dev/sdb: 1.82 TiB, 2000398934016 bytes, 3907029168 sectors
Disk model: ST2000NM0033-9ZM
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xce9d205e

Device     Boot    Start        End    Sectors  Size Id Type
/dev/sdb1           2048   16779263   16777216    8G fd Linux raid autodetect
/dev/sdb2       16779264   18876415    2097152    1G fd Linux raid autodetect
/dev/sdb3       18876416 3907027119 3888150704  1.8T fd Linux raid autodetect


Disk /dev/md2: 3.62 TiB, 3981195608064 bytes, 7775772672 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 524288 bytes / 1048576 bytes


Disk /dev/md1: 1022 MiB, 1071644672 bytes, 2093056 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/md0: 15.98 GiB, 17160994816 bytes, 33517568 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 524288 bytes / 1048576 bytes

```

/etc/fstab:
```

proc /proc proc defaults 0 0
# /dev/md/0
UUID=35297a77-7fa7-4df0-9c13-480ef88516b0 none swap sw 0 0
# /dev/md/1
UUID=7c0a9251-95ea-46bb-85b3-851874884a09 /boot ext3 defaults 0 0
# /dev/md/2
UUID=052438c2-04ac-4730-9f28-295d9266111f / ext4 defaults 0 0

```

---

### Post by bluexmas on 2022-12-03
is this a Hetzner server? If yes, I had the same problem.

The solution was pretty simple, but please make sure you don't have an UEFi system before trying this.

You need to remove these to fix the issue:
[COLOR=#747474][FONT=&amp]
[/FONT][/COLOR]```
apt remove shim-signed grub-efi-amd64-bin –allow-remove-essential
```[COLOR=#747474][FONT=&amp]
[/FONT][/COLOR]

---

### Post by audiodef2 on 2022-12-03
I guess this is a known issue with Hetzner servers, maybe something to do with their install images? Anyway, that did the trick. Thanks, blue!

---

### Post by bluexmas on 2022-12-03
No worries. Yes, it is a known issue, I asked their support and they also sent this solution, to uninstall those packages. Indeed, something to do with their installimage script, an old issue that they say it's fixed in the newer versions of it. It took me a while to figure it out, especially since it's quite stressful to mess around with bare metal containers boot, on production environments.

If you google for the command above, there is a more in depth discussion on a blog called "sindastra" about this (I don't think I am allowed to post urls here).

---

### Post by audiodef2 on 2022-12-03
My next stop was going to be reaching out to Hetzner, good to know they respond pretty well. :)

---

### Post by mbc0 on 2023-01-05
> **bluexmas said:**
> is this a Hetzner server? If yes, I had the same problem.

The solution was pretty simple, but please make sure you don't have an UEFi system before trying this.

You need to remove these to fix the issue:
[COLOR=#747474][FONT=&amp]
[/FONT][/COLOR]```
apt remove shim-signed grub-efi-amd64-bin –allow-remove-essential
```[COLOR=#747474][FONT=&amp]
[/FONT][/COLOR]

Hi!

I have a Hetzner server with the same problem but get this error when trying the command you gave? any ideas?



# apt remove shim-signed grub-efi-amd64-bin –allow-remove-essential
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
E: Unable to locate package –allow-remove-essential
root@Ubuntu-2204-jammy-amd64-base ~ #

Thank you!

---

### Post by graitsol on 2023-01-05
I have the same problem with Hetzner server.

[FONT=monospace][COLOR=#000000]The following packages will be REMOVED:[/COLOR]
  grub-efi-amd64 grub-efi-amd64-bin grub-efi-amd64-signed shim-signed
WARNING: The following essential packages will be removed.
This should NOT be done unless you know exactly what you are doing!
  shim-signed grub-efi-amd64-signed (due to shim-signed)
0 upgraded, 0 newly installed, 4 to remove and 6 not upgraded.
1 not fully installed or removed.
After this operation, 16.6 MB disk space will be freed.
[COLOR=#FF5454]**E: **[/COLOR][COLOR=#000000]Removing essential system-critical packages is not permitted. This might break the system

===

But i have laptop with Kubuntu [/COLOR][/FONT][FONT=monospace]shim-signed [/FONT]is installed in the desktop system and there are no problems when updating. 
I can remove those packages! But will the system boot without these packages?
[FONT=monospace][COLOR=#000000]
[/COLOR]
[/FONT]

---

### Post by PePas on 2023-07-18
This needs to be: ```
--allow-remove-essential
``` (start with double-dash) and then it works beautifully.

---

### Post by giakka on 2023-08-22
Same problem on [COLOR=#000000]Hetzner server
[/COLOR]

dpkg: error processing package grub-efi-amd64-signed (--configure):
 installed grub-efi-amd64-signed package post-installation script subprocess returned error exit status 32
dpkg: dependency problems prevent configuration of shim-signed:
 shim-signed depends on grub-efi-amd64-signed (>= 1.187.2~) | grub-efi-arm64-signed (>= 1.187.2~); however:
  Package grub-efi-amd64-signed is not configured yet.
  Package grub-efi-arm64-signed is not installed.


dpkg: error processing package shim-signed (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Processing triggers for libc-bin (2.35-0ubuntu3.1) ...
Errors were encountered while processing:
 grub-efi-amd64-signed
 shim-signed
needrestart is being skipped since dpkg has failed
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

