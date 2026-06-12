---
title: "NFS share between VM Debian Etch,XP and Ubuntu"
date: 2009-01-15
forum: Server Platforms
---

### Post by tigga on 2009-01-15
Hello ,
I have 2 virtual machines on ubuntu created by VMware.
The firt is windows XP and the other is debian etch.

The problem is ,
I want to create NFS partition and i want that the three machines(ubuntu,XP,debian) to be able to acces to this partition.

can anyone help me

---

### Post by koenn on 2009-01-15
Here's how to set up NFS on Debian or Ubuntu. It's pretty straightforward. [http://users.telenet.be/mydotcom/howto/linuxsbs/linuxnetworking.htm](http://users.telenet.be/mydotcom/howto/linuxsbs/linuxnetworking.htm)

If you set up your VM's with bridged networking, the VM's and the host system will be able to see each other 

But I doubt Win XP can do NFS.

---

### Post by HermanAB on 2009-01-15
For Windows, to get NFS support, you have to go to the Microsoft web site and download "Services for UNIX" for your version of Windows.  It is free and it works well.

Cheers,

Herman

---

