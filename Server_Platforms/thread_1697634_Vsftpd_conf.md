---
title: "Vsftpd conf"
date: 2011-03-01
forum: Server Platforms
---

### Post by gasuco on 2011-03-01
Hi forum,

Im new to this forum ;)  Im trying to make a vsftpd server accept connections through port 21.

Everything works ok when i connect through port 22 but when it comes to connections through por 21 it doesnt allow them.

I have listened to por 21 connections with tcmdump and i cant see the traffic.  On my iptables config i allow all traffic.

Can anyone help me?

This is what i get when i ftp myself:

> 
ftp localhost
Connected to localhost.localdomain.
220 Bienvenido al servidor FTP de Gasuco.
Name (localhost:root): root
331 Please specify the password.
Password:
530 Login incorrect.
Login failed.

Thanks before hand.

gasuco

---

### Post by artheus on 2011-03-01
By default in Vsftpd the root user is unable to connect.
It is considered a security hole to allow the root user to connect through regular ftp as the password will be sent in plain text over the network.
But if you want to allow the root user either way. This thread might help you.

[http://ubuntuforums.org/showthread.php?t=577112](http://ubuntuforums.org/showthread.php?t=577112)

Cheers,
Artheus

---

### Post by gasuco on 2011-03-01
The problem was that use have to delete the users that you need connecting via ftp (port 21) from the /etc/ftpusers list.

I have checked many forums and no one gives a clear solution to this problem.

I ho pe this helps to other vsftpd installers.

Thanks for the reply artheus.

gasuco

---

