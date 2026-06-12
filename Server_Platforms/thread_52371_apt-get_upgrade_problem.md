---
title: "apt-get upgrade problem"
date: 2005-07-27
forum: Server Platforms
---

### Post by dallypost on 2005-07-27
While upgrading my server, I got the following. It paused for a long time at "Searching for GRUB installation directory ...", then closed the connection and restarted the server. The server is working again but things like this make me uneasy. Does anyone have an idea about what happened?

Lance Earl

Setting up linux-image-2.6.10-5-386 (2.6.10-34.3) ...
Not touching initrd symlinks since we are being reinstalled (2.6.10-34.2)
Not updating image symbolic links since we are being updated (2.6.10-34.2)
Searching for GRUB installation directory ... Read from remote host [www.dallypost.com:](www.dallypost.com:) Connection reset by peer
Connection to [www.dallypost.com](www.dallypost.com) closed.

---

### Post by Mr Frosti on 2005-07-27
Were you updating the server locally, or were you using another machine to run the updates? I am assuming when you restarted the machine, that is when you saw the GRUB message, since it only executes during the initial boot. 

I have not had GRUB pause here before, however if you have a SCSI or RAID controller, it is possible that locating all the hard drives is taking a second.

---

