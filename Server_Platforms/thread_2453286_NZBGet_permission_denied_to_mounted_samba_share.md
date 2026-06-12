---
title: "NZBGet permission denied to mounted samba share"
date: 2020-11-06
forum: Server Platforms
---

### Post by bert-jan54 on 2020-11-06
I've installed Ubuntu server 20.04 as a VM on a Proxmox server. I then installed samba and mounted a couple of Samba shares (on a NAS) via fstab. I mounted one of those shares to /mnt/Downloads
This works fine, as fare as I can see (I'm no expert), I can access everything in that mount and can read write and create files. 
The /mnt/Downloads folder has all the subfolders I need for NZBGet: 'nzb', 'complete' 'incomplete' etc. 

I then installed Docker, and NZBGet in Docker. NZBGet is up and running. As the MainDir in NZBGet I put /mnt/Downloads. This does not work; I get a couple of errors for the NzbDir, the QueueDir and the TempDit. All simillar: Permission denied

**nzbget.conf(46): Invalid value for option "NzbDir"  (/mnt/Downloads/NZBGet/nzb): could not create directory /mnt/Downloads:  Permission denied**

I came from Windows and am relatively new in Linux, I do not understand how to give NZBGet the permissions needed to access /mnt/Downloads. I tried ```
sudo chmod a+rwx /mnt/Downloads
``` but that did not solve the issue. 

Any help very much appreciated!

---

### Post by Frogs Hair on 2020-11-06
Moved to *Sever Platforms*.

---

