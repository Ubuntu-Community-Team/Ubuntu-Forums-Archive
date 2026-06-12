---
title: "Can ClamAV Scan inside VirtualBox Folder?"
date: 2019-07-10
forum: Security
---

### Post by Rick St. George on 2019-07-10
Running WinXP inside VirtualBox because of proprietary Trading Software. After downloading quotes, which only takes a few seconds, I close the Network connection with ZoneAlarm, or Close the connection in VM. Nevertheless, I'm curious if ClamAV will scan the VM folder? I tried running AV inside WinXP/VM but it would not get updates online. Don't know why!

Anyone have a suggestion? 
Thanks!

Rick
:guitar:

---

### Post by kpatz on 2019-07-10
Virtualbox volumes are files* but a virus scanner on the host OS won't know how to open them as a file system.  Your best bet is to run an AV inside the VM.  It should be able to update provided the network connection is enabled and ZoneAlarm isn't blocking access.

* When I say files, there's one big file that contains the entire contents of the virtual drive.  In other words, that C: drive in your VM is housed in one big file on the host (or multiple big files if you use snapshots).  A virus scanner running on the host won't know how to extract files within that VM image to scan them.

There are ways to mount a Virtualbox volume in Linux provided it's a fixed size volume and not a dynamic one and there's no snapshots, but it gets a bit involved especially if there's partitions in the volume.

---

### Post by #&amp;thj^% on 2019-07-10
Why not install it on your windows VM
Or even malware-bytes
Ninja'd by kpatz

---

### Post by Rick St. George on 2019-07-10
> **kpatz said:**
> 
There are ways to mount a Virtualbox volume in Linux provided it's a fixed size volume and not a dynamic one and there's no snapshots, but it gets a bit involved especially if there's partitions in the volume.


Thanks, but Yes I'm using Snapshots as it is so much easier to just copy that snapshot over to my Backup HD once / month.
Guess I'll try another program and install inside the VM/WinXP.

):P

---

