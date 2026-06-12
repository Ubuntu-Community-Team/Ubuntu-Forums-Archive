---
title: "VMWare server - hard disk dize"
date: 2008-08-19
forum: Virtualisation
---

### Post by TheGameAh on 2008-08-19
Hey guys.

I have two servers.  Nothing really fancy.  One is a file/print server (100gigs about).  The other the same, although it also has a Solidworks vault on it, plus files  :)

Was thinking about consolidating both of these servers into one.  Was gonna build a RAID 10 box, (4) 250 gigabyte drives.  That would give me 500 gigabytes, some room to grow.

Was thinking about using VMWare Server, but has anyone ever created such a large disk with VMWare server (300 gigabyte +).  What exactly is the range where people stop using VMWare server, and move on to ESX or the paid products?

---

### Post by insane_alien on 2008-08-20
i think you can make 2TB drives with it. so i don't think you need to worry about it.

---

### Post by HermanAB on 2008-08-20
Linux can handle enormous disk drives so no problem there.  I usually keep the VMs smallish (8GB or less) and then use NFS to mount disk space from the host system for the data.  This simple trick makes it easier to manage the VMs since it keeps the data separated from the VM.

Cheers,

Herman

---

### Post by fjgaude on 2008-08-20
I do similarly here with a huge database raid5 array (about 1TB) but use Samba, not NFS, going from Windows to Linux and back. Works great. My Windows VM is only 10GBs.

---

### Post by TheGameAh on 2008-08-21
I love the samba and NFS ideas.  Unfortunately I know little about NFS, and I've had trouble mimicking Windows security permissions through samba.  Might have to investigate  :)

---

