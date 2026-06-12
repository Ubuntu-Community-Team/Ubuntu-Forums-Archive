---
title: "Windows Programs on Ubuntu Server"
date: 2011-08-24
forum: Server Platforms
---

### Post by ostrowlaw on 2011-08-24
Hi,

I have been administering Novell Netware servers for years for my small law office, but I am not a "tech" type, just a country lawyer.  However, I always found Novell servers to be relatively easy to administer without much technical expertise.

Now, I find out that Novell has discontinued Netware, and my choice is continuing with Novell on its Linux server, or other choices.  I do have several of my home computers running Ubuntu, so I thought I would give the Ubuntu server a first crack.

I have several old DOS programs that actually operate off the server, i.e., Wordstar 7.0 LAN and Borland Sprint.  I guess I could just move them over the workstations, and just store the data files on the server.

Did I answer my own question?  I am really interested in knowing whether programs themselves which are stored on the Linux server will run on Windows machines, or do the programs need to be stored locally?  Otherwise, is the use of the server simply as a remote storage medium?

I know that files, in whatever format, can be stored on Linux machines and accessed by Windows.  So am I on the right track here?

I am really concerned about storing some Windows data files and accessing them on the server.  For example, we heavily use several databases that use MS Foxpro.  The data files reside on the server,and are accessed by several users.  Would this operate the same or would there be more difficulty (like needing to use Wine on the server??).  I have had very little success actually running Foxpro under Wine, much less in a multi-user environment.  I would feel much more comfortable simply accessing forms and date (like under MS Word for example) stored on the Linux server.

Thanks,
Alan

---

### Post by Lars Noodén on 2011-08-24
The server is just remote storage.  The programs that you store on the server will be accessible just as if they were on a disk drive. If they are Windows programs then they will be runable on Windows machines or, with the help of WINE, on Linux, too.

Samba is probably the service that you would need to look at first.

---

### Post by lykwydchykyn on 2011-08-24
I'll second Lars.

If they worked from a Netware server, they should work just as well from a Linux server.  Sounds like the netware server is only sharing files, not running services for these applications.

Are you using NDS/eDirectory for authentication?

---

### Post by ostrowlaw on 2011-08-24
Thanks.  Not really using NDS for authentication.

I am just a little concerned about accessing the files for multi-use, i.e., Foxpro and Quickbooks.  But, if they are read just like disk drives (and I am sure I can set up the shares so they are accessed by drive letters) it should be good.

Just need to put a big chunk of time together to get this project started.

I have the Linux Administration Handbook and I think I can get going.. . .

Lots to learn.

---

### Post by lykwydchykyn on 2011-08-24
> **ostrowlaw said:**
> 
I am just a little concerned about accessing the files for multi-use, i.e., Foxpro and Quickbooks.  But, if they are read just like disk drives (and I am sure I can set up the shares so they are accessed by drive letters) it should be good.



Not for certain about those programs, but typically programs that use shared data files like that will create a "lock file" in the share to determine who has which records locked for editing.  That's the (client) application's responsibility, so it's just a file sharing thing.

---

