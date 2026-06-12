---
title: "Mirror Ubuntu"
date: 2008-03-07
forum: Server Platforms
---

### Post by timteohkb2007 on 2008-03-07
Hi 

I just install an ununtu server and would like to know how can I do the following :-

1. Mirror the main server to another machine so the second machine can be used as a secondary server. Updates to the main server is also reflected in the second unit when changes are done. And when the main server fails all I need to do is to just inform the users to use the second server.

2. How do i add open ssh access to new users as currently only the user created during installation have access and new created users do not.

Thanks.

---

### Post by azadpanchi on 2008-03-07
I will try to address point 2.  If you want to learn add users here is a good how-to from the command line:
[http://www.howtogeek.com/howto/ubuntu/add-a-user-on-ubuntu-server/](http://www.howtogeek.com/howto/ubuntu/add-a-user-on-ubuntu-server/)

There is a lot of ways to try to achieve your first point, I am going to leave it for someone else to answer.  If you are looking to create redundancy maybe you should look to the same server with a RAID controller, multiple disks in a RAID 5 would be highly recommended.

---

### Post by koenn on 2008-03-08
> **timteohkb2007 said:**
> Hi 

I just install an ununtu server and would like to know how can I do the following :-

1. Mirror the main server to another machine so the second machine can be used as a secondary server. Updates to the main server is also reflected in the second unit when changes are done. And when the main server fails all I need to do is to just inform the users to use the second server.


You can write a small script around rsync, and use a cron job to execute it at an interval that suits you (seconds, minutes, hours, daily ... )

rsync is an intelligent remote 'copy' tool, i.e. it only copies changes and can be made to delete files on the remote machine if the corresponding files are deleted on the original machine : you can keep the two machines completely identical.

you need to work on it a bit to
- make sure not to rsync hardware-specific files (depends on how similar the hardware of both servers is).
- decide how to handle (rsync or not) files specific to processes running on the server (/tmp, /proc, log files, ...


[http://www.samba.org/ftp/rsync/rsync.html](http://www.samba.org/ftp/rsync/rsync.html)

you may also want a more elaborate sollution, i.e; a real "cluster"
[http://www.linuxjournal.com/article/5862](http://www.linuxjournal.com/article/5862)

---

### Post by jonabyte on 2008-03-08
Koenn,

I admit I am not up on rsync, should be, but anyways. Would you know if this could work with a server offsite.
My bosses want to backup our file server, but have the backup offsite.

---

### Post by koenn on 2008-03-08
sure it'd work. 
a network is a network, be it a LAN, a vpn tunnel or the internet.
rsync is unaware of this, it just knows hostname/ip address of the destination, and your network infrastructure will handle all the rest.

the only limiting factor is the network's properties (eg LAN bandwith, ISP speed and volume limits, ...), and things like that
This will affect* the time it takes* to rsync, but not whether rsync will work or not.

---

