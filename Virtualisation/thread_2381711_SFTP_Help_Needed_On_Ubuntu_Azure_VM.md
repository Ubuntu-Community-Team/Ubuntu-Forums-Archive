---
title: "SFTP Help Needed On Ubuntu Azure VM"
date: 2018-01-04
forum: Virtualisation
---

### Post by waynem1966 on 2018-01-04
SFTP server works fine using Filezilla, but one of our vendors requires that FTP be functional from a DOS prompt. (I don't remember is this is passive or active FTP.)
Login works fine. ls command gives the following error: "500 Illegal PORT command. 425 Use PORT or PASV first."

---

### Post by TheFu on 2018-01-04
Welcome to the forums.

I can't tell if you want help with sftp or plain FTP.  Both are completely separate from each other.

---

### Post by waynem1966 on 2018-01-05
Sorry, I should have written VSFTP instead of SFTP.

---

### Post by TheFu on 2018-01-05
> **waynem1966 said:**
> Sorry, I should have written VSFTP instead of SFTP.

FTP is a protocol full of issues from a security and firewall standpoint.  There are lots of articles about all the reasons why we should NOT use it anymore. 

sftp is a completely different protocol, based on the ssh protocol. Firewall people like it, because it uses a known port and only that port.

If you run an sftp server, then you can use a compliant sftp client to connect.

vsftp is something I've never needed or wanted.  It has a less than great security history and the normal sftp-server that is provided with the ssh-server packages has been more than sufficient for our needs.

---

