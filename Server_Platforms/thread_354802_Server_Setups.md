---
title: "Server Setups"
date: 2007-02-06
forum: Server Platforms
---

### Post by DriverJC on 2007-02-06
A little background first:
I have 7 1tb servers that house my DVD Collection in AVI Format.  I can access these servers with NFS and Samba.  Everything is set up as follows.

Names
Server 1 - Gateway.example.com
Server 2 - DVD01.example.com
Server 3 - DVD02.example.com
Server 4 - DVD03.example.com
Server 5 - DVD04.example.com
Server 6 - DVD05.example.com
Server 7 - DVD06.example.com
Server 8 - DVD07.example.com

Servers 2 - 8 have a DVD directory in /media that is exported and mounted by Server 1 in the /media directory.
So the /media directory looks like this

/media/dvd01
/media/dvd02
/media/dvd03
/media/dvd04
/media/dvd05
/media/dvd06
/media/dvd07

the /media directory is shared via SAMBA and NFS to allow the Windows and Linux machines to view the files.

What I would like to know is:

Is it possible to automaticly combine all the /media/dvdXX directories into one LARGE directory. kinda like LVM does with Hard Disks?

Is it possible to use LVM accross a network? If so what would the performace be like?

I would want this to display the files as if they were in a single directory as well as allow me to save the files to the virtual directory and have the files automaticly directed to the server with the open space (i.e dvd07)

Any information you have will be helpfull.
Joel

---

### Post by Brazen on 2007-02-07
You can't do what you are asking with LVM.  The only way to do what you are asking is to use iSCSI.  Set up servers 2-8 as iSCSI targets and have server 1 attach to all those targets (that would be refered to as an iSCSI Initiator).  Each of the targets will look and act just like a physical harddrive so you can then add them all to a logical volume group.

My suggestion though, after setting up the iSCSI, combine those 7 targets into a Raid5 array.  That way you'll have a little redundancy in case a harddrive in one of your servers blows out, or if a server drops off completely then you will still be able to access all your files.  And with that much data, I think you will definately want some hard drive redundancy.

---

