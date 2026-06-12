---
title: "Partitioning a drive for the server"
date: 2008-08-26
forum: Server Platforms
---

### Post by brian77095 on 2008-08-26
Hi- I will be setting up a server for web hosting and network storage.

I would like to know what is the best way to set up the hard drive.

Should I just give it 100%?  I would like to store a fairly large number of pictures and music on the drive that will need to be accessed by a windows computer.

With that being said should I have two partitions?  One just for windows crap?

I also have an extra drive I could put in there would that be better?

Thanks for the help!!

---

### Post by flatline on 2008-08-26
I'm not really sure what you mean by "*Should I just give it 100%?*"  

On my server, I have a 1TB drive.  It has 50GB dedicated to / , 4GB of swap, and the remaining 900-odd GB as /home.   / includes the root filesystem, bootloader stuff, configuration files, applications, all that stuff. /home is shared with Samba and used for music/photos/torrents/backups.

Honestly, you can usually get away with a swap partition and one big / partition.  However, you may want to consider a separate /boot, /www, and/or /var.  This will provide some separation and might be more desirable since your server will be both internally and externally accessible.  You could use a /public partition for your windows share, depending on how you want to set that up, or go with /home as I did.

You will almost certainly be using Samba to share to Windows computers.  That means it doesn't really matter what your underlying filesystem is.  I would recommend ext3.

---

