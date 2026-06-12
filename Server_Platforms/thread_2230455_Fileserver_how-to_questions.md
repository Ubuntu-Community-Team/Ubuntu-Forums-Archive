---
title: "Fileserver how-to questions"
date: 2014-06-19
forum: Server Platforms
---

### Post by harphauler on 2014-06-19
I would like to set up a small office LAN fileserver.  The how-to articles and threads don't quite fit what I would like to do and most seem to be a long, complicated process with lots of fine detail in editing config files, installing and modifying packages and so on.  Here's the situation:

There are approximately 15 individual workstations on the LAN; Mac, Windows, Linux.

I think I need to use Ubuntu Server; assuming that, will use 14.04.

I would like to use the fileserver mainly for backup of the individual workstations in individual password protected home directories.

I need one - four directories that can be shared by some individual workstations and one directory that can be shared by all users.

I plan to use RAID in the LAN server and do a remote backup of it.

This is the basic concept I'm looking at.  Can this be answered here or in a how-to somewhere?

Thanks!

---

### Post by Tadaen_Sylvermane on 2014-06-19
Samba best bet. Getting some folders shared by only certain workstations might be a bit of a pain but everything can be done with samba.

[http://www.spuddogg.com/how-to/how-to-part-3-linux-file-server-on-windows-network/](http://www.spuddogg.com/how-to/how-to-part-3-linux-file-server-on-windows-network/) is where I started. Separate /home/$USER directories isn't a huge leap from this.

---

### Post by harphauler on 2014-06-19
Now that's what I'm looking for!  Thanks!

---

