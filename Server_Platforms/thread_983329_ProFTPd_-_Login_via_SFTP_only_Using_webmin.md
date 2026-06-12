---
title: "ProFTPd - Login via SFTP only? Using webmin"
date: 2008-11-15
forum: Server Platforms
---

### Post by Swerve1000 on 2008-11-15
Hello everyone

I have installed ProFTPd through Webmin onto Ubuntu 8.10 Server edition.

I can connect to ProFTPd via FTP on Port 21 no problem, but currently am unable to via SFTP (using WinSCP).

I would like to block all FTP access on Port 21 and only make it only possible to connect via SFTP/SSH on Port 22.

How would I do this? I'm pretty new to all this, so please be gentle

Many thanks! Any help is greatly appreciated!

---

### Post by hictio on 2008-11-15
> **Swerve1000 said:**
> Hello everyone

I have installed ProFTPd through Webmin onto Ubuntu 8.10 Server edition.

I can connect to ProFTPd via FTP on Port 21 no problem, but currently am unable to via SFTP (using WinSCP).

I would like to block all FTP access on Port 21 and only make it only possible to connect via SFTP/SSH on Port 22.

How would I do this? I'm pretty new to all this, so please be gentle

Many thanks! Any help is greatly appreciated!

You don't need ProFTPD if you want to use SFTP.
SFTP is part of SSH, and having the sshd server up & running is enough.

If you have the SSH server running on your Ubuntu Server, you can shutdown ProFTPD; as ssh uses port 22 TCP, that has to be open on your server, and/ or redirected from any router in-between your server and the internet (or the clients that have to connect to your server).

---

### Post by Swerve1000 on 2008-11-15
Oh really, well thank you hictio for explaining it all.

The services I chose to install during Ubuntu's installation was LAMP and OpenSSH.

I will reformat now to be safe.

Seems I have do to a bit more research before simply diving in.

Appreciated :)

---

### Post by hictio on 2008-11-15
> **Swerve1000 said:**
> Oh really, well thank you hictio for explaining it all.

The services I chose to install during Ubuntu's installation was LAMP and OpenSSH.

I will reformat now to be safe.

Seems I have do to a bit more research before simply diving in.

Appreciated :)

Don't mention :)
Take a look at this link first:

[ssh suite: Sftp, scp and ssh-agent](http://linuxgazette.net/issue64/dellomodarme.html)

and then, if you want to, this one might come handy, specially if you are setting up that service to have sort of "public" acess (SORT OF!)

[SFTP For Business Use](http://freshmeat.net/articles/view/1576/)

---

