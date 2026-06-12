---
title: "File and Backup Server"
date: 2009-10-31
forum: Server Platforms
---

### Post by Jukov on 2009-10-31
Hi there,

My question is pretty simple, I guess, but I haven't found a compelling answer, so bare with a noob, please.

I run a network of several PCs (with vista an win7) and a Mac. One of the PCs is a pretty old pentium 4 pc which servers as a file and backup server for all the others. Essentially I store all the work files, as well as the music, videos and personal photos on it. All the other PCs can access the files, view and edit them. The "oldie" is also running Acronis backup software and backs up all the other PCs via the network. All in all it's like running an external network drive, but on a PC.

I'm interested in switching this PC to Ubuntu or even Xubuntu and would like to know if such functionality can also be achieved under Linux and how. I'd also like to know if someone could point me to a tutorial for setting up such a fileserver over the internet as well.

Thanks in advance

---

### Post by TwiceOver on 2009-10-31
Samba - Look this up for your file sharing.  Easy enough to configure.

BackupPC - Look into this for doing your network backups.  It takes a little setup and you will need Apache web server running for the interface, but it works really well.

---

