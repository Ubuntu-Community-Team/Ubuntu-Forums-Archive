---
title: "Need advice on file system options for HUGE storage server"
date: 2008-07-22
forum: Server Platforms
---

### Post by rockfx01 on 2008-07-22
Hello,

We are investigating options for a NAS server with a capacity of 100TB+.  I am pretty new to Linux and haven't built a system this large before, so I was hoping someone could offer suggestions on what file system to use and any possible limitations that Ubuntu may present.

We were initially looking at RHEL with GFS, but from my experience, RHEL support is not very good (compared to Ubuntu) and from our initial discussions with them, their implementation of GFS requires a $2k+ license for Cluster Suite, which is out of the question.

The NAS we are looking to build would be a system with a single head behind it with lots of storage.  We are thinking upwards of 100TB, possibly more.

The storage will be mounted via NFS to another Linux server and via Samba to Windows clients.

[LIST]
[*]It needs to be reliable enough to put in a production environment.
[*]It needs to be FAST.
[*]It needs to support large files, although I doubt they will surpass 1TB/file anytime soon (if ever).
[*]It must support ACLs.
[/LIST]

From my research thus far, it seems that XFS, JFS, or GFS would be desirable.  So far XFS seems to be the best option, but I have no actual experience with any of the three, so any suggestions you have would be greatly appreciated.

Can anyone tell me how well these file systems are supported by Ubuntu and whether or not they will serve our needs?

Thanks!

---

### Post by Titan8990 on 2008-07-22
Just out of curiosity how do you plan to get 100 hard drives in one system? 

I can't imagine the wattage + the space + the stress on the boards soutbridge.

Do you realize how bad it is to invest in storage? Think about how big hard drives were 5years ago and how much they cost. As time goes on storage gets remarkably cheaper. In other words I would get as much storage as you need for the next few years and then plan to get more then as you will be able to get much more for a cheaper price.

---

### Post by rockfx01 on 2008-07-22
After a little more reading, it sounds like JFS might be the better option.  It seems to be more reliable and about as fast as XFS.  There is a smaller file system size than XFS, but I doubt we will need to build a file system larger than 32PB anytime soon.

Suggestions?

---

### Post by windependence on 2008-07-22
This is definitely enterprise class. 

Should be done in RAID cabinets with SCSI drives, that's how you manage power, it's built into the RAID cabinet. I have one here with 12 drives. You would need quite a few controllers for that though. Probably better off just getting an EMC or other proprietary solution.

As to the OS if you indeed find a way to do it, CentOS is an exact copy of Redhat EL. They have great forum support too. I have also had good luck with SuSE. 

If you don't care if you use Linux, you would be good to try something more geared toward the enterprise like FreeBSD or OpenSolaris. There are tons of different file systems out there and even someting like EXT3 could be tuned to perform well if you know what you are doing. I really can't give you a recommendation on that one because it depends on what is important to you. If you go for speed, you generally sacrifice relaiblility, and vice versa. It can be a tough call sometimes.

-Tim

---

### Post by rockfx01 on 2008-07-22
> **Titan8990 said:**
> Just out of curiosity how do you plan to get 100 hard drives in one system? 

I can't imagine the wattage + the space + the stress on the boards soutbridge.

Do you realize how bad it is to invest in storage? Think about how big hard drives were 5years ago and how much they cost. As time goes on storage gets remarkably cheaper. In other words I would get as much storage as you need for the next few years and then plan to get more then as you will be able to get much more for a cheaper price.

As far as I understand it, the storage server connects via Infiniband to a "head" which controls several banks of hard drives in our server racks.  I'm not sure what the hard drive limitations are on the system or how it works.  We have someone else for that.  My job is just to find out what file system supports our needs and implement the file sharing mechanism between the clients and the server.

The storage servers are going to be supplied along with another server product we are developing, so file system size for the storage is up to the client.  There will be a LOT of high resolution media files being stored, so the storage capacity needs to be big enough and fast enough to handle it.  We're not talking your typical MS Word/Excel/etc files being used by a typical office.  The storage server will be doing *nothing* but serving files to clients.

It seems that our customers want storage solutions bigger than RHEL's ~25TB limit (without Cluster Suite/GFS or other solutions which RedHat doesn't really offer much support for).  Even RHEL's basic GFS support is limited to around 25TB, and higher capacity solutions you're supposed to "call for support" on.  I.E. they don't want to deal with supporting file systems that large.  Several customers wanted to use a Windows based storage solution, but there are serious problems with Windows Services for NFS and international character support between Linux/Windows clients, so we are looking at Linux as a storage solution because we know int'l support works.

---

### Post by Titan8990 on 2008-07-22
I will be interest in keeping up with this thread. I work for a small business of around 15 employees and I just couldn't imagine that many drives. We just spent $1000 on 6TB and I thought that was nuts...

---

### Post by scorp123 on 2008-07-23
> **Titan8990 said:**
>  Just out of curiosity how do you plan to get 100 hard drives in one system?  

[http://www.sun.com/servers/x64/x4540/](http://www.sun.com/servers/x64/x4540/)
Two of these (48 SATA disks per system) and you're almost there. :)

---

### Post by scorp123 on 2008-07-23
> **rockfx01 said:**
>  We are investigating options for a NAS server with a capacity of 100TB+.  I am pretty new to Linux and haven't built a system this large before, so I was hoping someone could offer suggestions on what file system to use and any possible limitations that Ubuntu may present.  We use SUN storage servers and expansions and we use Ubuntu (64-bit) as OS. Works tip top.

e.g.
[http://www.sun.com/servers/x64/x4540/](http://www.sun.com/servers/x64/x4540/)


> **rockfx01 said:**
>  The storage will be mounted via NFS to another Linux server and via Samba to Windows clients.  Bingo, same here. All our $HOME directories live on the storage, and regardless where our users log in they always get their home directory and therefore all their settings, data, mails, and what not.

> **rockfx01 said:**
>  [*]It needs to be reliable enough to put in a production environment.
[*]It needs to be FAST.
[*]It needs to support large files, although I doubt they will surpass 1TB/file anytime soon (if ever).
[*]It must support ACLs.
[/LIST]  We use XFS. That's pretty much a "tested and tried" filesystem (first released in 1993). XFS was the default on SGI's UNIX / 3D rendering boxes in the mid-90's and did very well there and since it was ported over to Linux early 2000 many people have used it on Linux too. I've always had good experience with it, especially when it comes to really large files (4 GB and beyond), that's where XFS really shines.

Recently I have started to look at JFS too ... so far I can't see any major differences between JFS and XFS, both "behave well" on our servers. It's just that I am more familiar with XFS at the moment.

> **rockfx01 said:**
>  Can anyone tell me how well these file systems are supported by Ubuntu and whether or not they will serve our needs? I have no experience or knowledge about GFS ... sorry. But XFS and JFS are both easily available on Ubuntu and work tip top.

---

