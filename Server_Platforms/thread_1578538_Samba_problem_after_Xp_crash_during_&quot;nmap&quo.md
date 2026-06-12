---
title: "Samba problem after Xp crash during &quot;nmap&quot; instalation"
date: 2010-09-20
forum: Server Platforms
---

### Post by Irvine_himself on 2010-09-20
Over the weekend, I networked my Ubuntu box with an old Xp laptop. I have had it working perfectly a couple of times, but it seems to be pretty fragile and falls over frequently. Up until now I have been able to recover, but....

Being paranoid,  I installed "nmap" on both Xp and Ubuntu to check the port security. The first installation attempt of "nmap" caused Xp to crash. After re-booting Xp, strange things had happened, most noticeable the task bar was all messed up and the Samba connection had fallen over again, (in both directions.)

After some tweaking, I am now able to add and remove files from the Xp laptop using the Ubuntu end of the Samba. However the Xp end of things can no longer see Samba!

I finally got "nmap" working on Xp and it basically says that the only open port on Ubuntu is port 25, (email I think,) in other words, the Samba port is no longer open on Ubuntu?

```

From Ubuntu:
135/tcp open  msrpc       Microsoft Windows RPC
139/tcp open  netbios-ssn
445/tcp open  netbios-ssn

From Xp:
25/tcp open  smtp    Postfix smtpd
```I am not sure if that is normal for Ubuntu, since by default it should not respond and, (I have got to admit,) am out of my depth and need help. 

Please!
.

---

### Post by Irvine_himself on 2010-09-21
Okay, I have finally figured out a solution:

First, I did a system restore on Xp. It did not solve anything, (the problem was with Ubuntu/Samba,) but it did get my laptop  working in its normal barely tolerable Xp fashion. I then had to redo the network settings on Xp

Second, I tried re-installing Samba, but that did no good so I completely removed it and then re-installed. 

The visible Samba permissions were unchanged, but what ever was blocking the connection was fixed. I have no idea what it was, but I now have two way control of my network.

PS

If anyone is looking for a good "Idiot Guide" to setting up a Ubuntu/Xp LAN with Samba, I would recommend [URL="http://www.liberiangeek.net/2010/05/share-filesfolders-between-windows-xp-vista-7-and-ubuntu-10-04-lucid-lynx-via-samba/"]this here.
[/URL] 
.

---

