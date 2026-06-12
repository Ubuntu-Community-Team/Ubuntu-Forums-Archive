---
title: "File Server Setup (for windows clients)"
date: 2006-07-05
forum: Server Platforms
---

### Post by Zyzzyva100 on 2006-07-05
I have a few questions about how to setup Ubuntu as a file server.  I have been using Ubuntu on my laptop for about a year, and gentoo on my desktop a bit longer, but have never really configured a linux server.

The server in question is a dell precision that my lab inherited.  Its a P4 with 2 gigs of RDRAM, so this doesn't have to be a terribly lean install.  My plan is to do the basic Ubuntu install so that I at least have a graphical environment to work with if I need it.  (And just remove things that aren't needed after the fact, like multimedia players, etc).  Previously this machine was a domain controller, but after crashing twice in 6 months, and refusing to restore active directory from backups, I am done.  The domain was nice for configuration, but all the server really needs to do is easily serve files for windows, mac and linux machines.  (Its a backup server for all our lab data).

All the data is currently on 2 300 gig SATA drives, which are formatted as NTFS.  The drives are not close to being full, so I plan ot move everything to one drive, format the other, and then rinse and repeat.  What would be the best filesystem to go for, fat32?  Or if I format ext3, will the the partitions be read and writeable via samba?  That is my main concern, since I haven't really played with having file shares be writeable via samba across different file systems.

If anyone has any other tips, I am open to ideas.

---

### Post by Iowan on 2006-07-05
Your choice, but is it easier to do a basic install and remove the stuff you don't want, or do a server install and add the stuff you do want?  IMHO, ext3/Samba should work - others might recommend other filesystems.

---

### Post by Randomskk on 2006-07-05
I'd definitely go for ext3, so long as the SERVER is running linux it'l be fine, samba serves up files, not access to the disk directly.
I'd also suggest doing a server install, then just installing the things you need - you may find you don't want X anyway, and I'd go for openssh-server for remote control.
However, you could just install the core X stuff, and maybe a light window manager, if you want the graphical interface, something like sudo apt-get install xserver-core might get you the base X (can't remember for sure).

If it's a backup server for files only, you may want to look into just using FTP instead of samba, as it's much easier to setup, and can still be browsed with the native file manager for windows, mac and linux.

---

### Post by Zyzzyva100 on 2006-07-05
Thanks for the input.  I assumed correctly then as to how Samba works, I just wanted to make sure that the writes would work.

Yea, it would probably be easier to just do the server install, and add what I need, but the boot drive is 80 gigs, and nothing else will even be stored on it.  Since storage and memory aren't really limiting anything, I figure a basic Gnome install should be just fine.

As for FTP, I thought about that, and may still play with it, but people tend to backup more if the drive is mapped via 'My computer', and so that is probably the route I will go using Samba.

---

### Post by Randomskk on 2006-07-06
I believe you can actually map an FTP account to a "My Computer" drive; at least, I've seen it done without any extra plugins or such.
Samba is probably easier, I guess - could always get both.

Also, if you do really want a nice GUI, how about XFCE? install xubuntu-desktop via apt-get, it's nice and light and won't suck up much CPU at all.

---

### Post by harisund on 2006-07-06
Yes, you can do everything you want to do. 

Once you have rinsed and repeatedly cleaned, you can install samba and Windows users can just map into it. 

FTP can be installed, and is not a big deal either.

---

