---
title: "Large file transfer on LAN"
date: 2010-11-11
forum: Server Platforms
---

### Post by jcolinger3 on 2010-11-11
Hello,

I'm trying to create an Ubuntu Server file server that will handle large file transfers (up to 50gb) from the LAN with Windows clients.  We've been using a Windows server on our LAN on the file transfers will occasionally fail... though the server is used for other services as well.

The files will be up to 50gb.  My thoughts are to create a VLAN (or separate physical switch) to ensure maximum bandwidth.  Ubuntu server will be 64bit with 4tb of storage in a RAID 5 config.

Does anyone have any feedback or suggestions on this type of a setup that may help?

John

---

### Post by PapaNerd on 2010-11-11
A server (Windows or Unix) failing on a transfer may have nothing to do with the server itself.

You probably should consider acquiring a network architect to work with your team to help you plan your I/O needs and evaluate your transfer problems.  A typical scenario in a data center, for example, would be to have web traffic I/O go through a NIC on a DMZ, and do backups and other large data transfers through a second NIC on a dedicated network configured with gigabit switches.

---

### Post by WinstonChurchill on 2010-11-11
Windows SMB file-transfer protocols have never worked very well, whether with Samba or with Windows machines - another good reason to ditch Microsoft. FTP is much faster and massively more reliable, in my experience; if your clients have the capability, I would use that.

I've moved very large archives (~40GB) back and forth across networks with vsftpd - I never have failures, and I consistently get speeds around ~100 MB/s (obviously limited by the HDD).

---

