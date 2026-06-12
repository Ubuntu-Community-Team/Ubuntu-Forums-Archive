---
title: "apt-cdrom and ISO image, no network"
date: 2013-01-27
forum: Server Platforms
---

### Post by Jonathan L on 2013-01-27
Hello

Anybody got a simple, definitive, procedure for using CD-ROM images to add packages when there's no network connection or CD-ROM drive?

Situation: fresh 12.04.1 server installation with just SSH server, and want to install packages with apt-get from the 12.04.1 installation CDROM ISO image.

```
user@gran:/$ sudo apt-cdrom -d /ubu-12.04.1 -m ident
[sudo] password for user: 
Using CD-ROM mount point /ubu-12.04.1/
Mounting CD-ROM
Identifying.. [af2d149f3414185ae5cb12b9b0c3cc0b-2]
Stored label: 
user@gran:/$ sudo apt-get install apache2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package apache2
```
... any other solution to the problem also gratefully received.

Thanks for any help.

Kind regards,
Jonathan.

PS.  the definitely mounts fine and is freshly downloaded 
3daaa312833a7da1e85e2a02787e4b66  ubuntu-12.04.1-server-i386.iso

---

### Post by Cheesehead on 2013-01-27
Archives on CD work best when actually using a CD drive.

If using USB sticks, try apt-zip or apt-offline.

apt-zip:
> Description-en: Update a non-networked computer using apt and removable media
 These scripts simplify the process of using dselect and apt on a
 non-networked Debian box, using removable media like ZIP floppies and
 USB keys.
 One generates a `fetch' script (supporting backends such as wget and
 lftp, in a modular, extensible way) to be run on a host with better
 connectivity, check space constraints of your removable media, and
 then install the package on your Debian box.



apt-offline:
> Description-en: offline APT package manager
 apt-offline is an Offline APT Package Manager.
 .
 apt-offline can fully update and upgrade an APT based distribution without
 connecting to the network, all of it transparent to APT.
 .
 apt-offline can be used to generate a signature on a machine (with no network).
 This signature contains all download information required for the APT database
 system. This signature file can be used on another machine connected to the
 internet (which need not be a Debian box and can even be running windows) to
 download the updates.
 The downloaded data will contain all updates in a format understood by APT and
 this data can be used by apt-offline to update the non-networked machine.
 .
 apt-offline can also fetch bug reports and make them available offline.


---

