---
title: "Remote Clone An Ubuntu Server Installation On A VM"
date: 2017-02-05
forum: Server Platforms
---

### Post by mpez on 2017-02-05
For research purposes, me and and few other colleagues have been granted a VM that is hosted by the University's cloud service program. After a few months of work we need to backup the whole Ubuntu Server installation. As you understand there is no physical machine thus no USB/Live CD or bootable programs are options here. The Backup should be made in real-time remotely while accessing the VM with a SSH client. 

The cloud service itself supports new installations of Linux on your VM (and a big variety of other OS to be precise) if you provide your own image , but it doesn't have a build-in program to clone the logical drive. The supported image formats are 
[LIST]
[*]extdump
[*]ntfsdump
[*]diskdump
[/LIST]

Is there a way to pull an Iso or something remotely this way? 
Any help is highly appreciated, Thanks in advance

---

### Post by Habitual on 2017-02-05
[https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)
[http://rsync.net/resources/howto/rsync.html](http://rsync.net/resources/howto/rsync.html)

Good luck.

---

### Post by mpez on 2017-02-07
> **Habitual said:**
> [https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)
[http://rsync.net/resources/howto/rsync.html](http://rsync.net/resources/howto/rsync.html)

Good luck.
thanks a lot for your reply

---

