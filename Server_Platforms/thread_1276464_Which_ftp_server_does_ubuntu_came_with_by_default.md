---
title: "Which ftp server does ubuntu came with by default?"
date: 2009-09-27
forum: Server Platforms
---

### Post by cpthk on 2009-09-27
I was wondering which ftp server does ubuntu came with by default? vsftpd or proftpd?

Which is recommended?

Thanks.

---

### Post by ainsworth_t on 2009-09-27
There is no default, though both are in the repositories. I'm not sure if one is recommended over the other, but the Ubuntu Server Guide covers configuring VSFTPD: [https://help.ubuntu.com/9.04/serverguide/C/ftp-server.html](https://help.ubuntu.com/9.04/serverguide/C/ftp-server.html)

---

### Post by jocampo on 2009-09-27
> **cpthk said:**
> I was wondering which ftp server does ubuntu came with by default? vsftpd or proftpd?

Which is recommended?

Thanks.

Do not use ftp, use ssh and its secure way to transfer files instead. FTP is an insecure protocol.

---

### Post by Bachstelze on 2009-09-27
> **jocampo said:**
> Do not use ftp, use ssh and its secure way to transfer files instead. FTP is an insecure protocol.

You can encrypt FTP traffic with SSL.

---

### Post by cpthk on 2009-09-27
I really have to use ftp due to company requirement. If I install ubuntu server edition, and choose to install ftp service during installation, which ftp server does it installed?

---

### Post by Bachstelze on 2009-09-27
> **cpthk said:**
> I really have to use ftp due to company requirement. If I install ubuntu server edition, and choose to install ftp service during installation, which ftp server does it installed?

Why does it matter? Just don't select it, and install the FTP server of your choice afterwards. It will be the same in the end.

---

### Post by scorp123 on 2009-09-27
> **Bachstelze said:**
> You can encrypt FTP traffic with SSL. That's a royal PITA. And not every client program supports that properly. And having that stuff pass properly through corporate firewalls is yet another story.

SFTP/SCP is so much better in many ways.

---

### Post by Bachstelze on 2009-09-27
> **scorp123 said:**
> That's a royal PITA.

Is not.

> **scorp123 said:**
> And not every client program supports that properly.

Of course, if a program does not support a protocol properly, it's the fault of the protocol...

> **scorp123 said:**
> And having that stuff pass properly through corporate firewalls is yet another story.

SFTP/SCP is so much better in many ways.

If your corporate firewall blocks FTPS, chances are very high it will block SSH too.

---

### Post by cpthk on 2009-09-27
I prefer to use the default ftp server, which has better support. So I would like to know which one is installed by default.

---

### Post by Bachstelze on 2009-09-27
> **cpthk said:**
> I prefer to use the default ftp server, which has better support.

How do you know? Anyway, vsftpd is in the main repository, as opposed to all other ftpd's who are in universe.

---

### Post by cpthk on 2009-09-27
Thanks. If it's by default, then the users on the forums should mostly use that, since many people install it during installation of ubuntu. So if I ask any question, more people could answer my question. On top of that, ubuntu only provide documentation for vsftpd, which is already an extra support.
On the other hand, it's just like doing service for your car. Many people would prefer to do the service at your car brand dealership service instead of other 3rd party store. Dealership usually cost way more, but some people only trust them.

Thanks for your help.

---

### Post by ainsworth_t on 2009-09-29
> If it's by default, then the users on the forums should mostly use that, since many people install it during installation of ubuntu.
This is not true for a couple of reasons:
1) Some people, as previously mentioned, choose not to install FTP as a service since it is an insecure protocol, and choose to go the route of SCP/SFTP. 
2) There is no FTP server installed by default during a basic installation of Ubuntu Server. Because there is no "default", the choice is up to the end user to install ProFTPD, VSFTPD, SCP/SFTP, or whatever other service/server they feel more comfortable with.

However, the server that would probably closest fit your criteria would be VSFTPD since it's 1) documented in the Ubuntu Server Guide, and 2) It's in the Main repository which means it's free software and it's supported (Updates come from Canonical, not from the community).

---

### Post by scorp123 on 2009-09-29
> **Bachstelze said:**
>  If your corporate firewall blocks FTPS, chances are very high it will block SSH too. That's not what I meant. Please lookup how FTP works and what ports and in which direction it involves. Then lookup the same for FTPS, which is FTP + SSL on top. Summa summarum: One rigged protocol (FTP) yet gets another rig on top. That's also why not all FTPS clients work exactly the same.

And then lookup what port SSH involves? ONE. Only ONE. 22/tcp. And that's it. From a firewall point of view making sure SSH/SCP/SFTP can pass through and get where they need to is _EASY_ compared to making sure FTPS can pass through.

---

### Post by Iowan on 2009-09-29
I suppose you're gonna make me do a fresh server install - just to find out... ;)

---

