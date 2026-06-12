---
title: "Failed SSH Key Exchange"
date: 2008-08-21
forum: Server Platforms
---

### Post by voteforpedro on 2008-08-21
I'm trying to SFTP to my server using WS_FTP Pro 8; I can connect to it just fine using PuTTY.

But when I try with WS_FTP I get:

> 
[2008.08.21 13:56:29.453] Connecting to xxx.xxx.xxx.xxx:22
[2008.08.21 13:56:29.531] Connected to xxx.xxx.xxx.xxx:22 in 0.078125 seconds, Waiting for Server Response
[2008.08.21 13:56:29.578] Server Welcome: SSH-2.0-OpenSSH_4.7p1 Debian-8ubuntu1.2
[2008.08.21 13:56:29.578] Client Version: SSH-2.0-WS_FTP-8.0-2003.05.23
[2008.08.21 13:56:29.593] [COLOR="Red"]Failure to agree with SSH server[/COLOR] on compatible algorithms
[2008.08.21 13:56:29.593] SSH Transport agreed algorithms
[2008.08.21 13:56:29.593]      Purpose: key agreement  		Algo: diffie-hellman-group-exchange-sha1
[2008.08.21 13:56:29.593]      Purpose: server host key		Algo: ssh-dss
[2008.08.21 13:56:29.593]      Purpose: encryption cs  		Algo: 3des-cbc
[2008.08.21 13:56:29.593]      Purpose: encryption sc  		Algo: 3des-cbc
[2008.08.21 13:56:29.593]      Purpose: MAC cs         		Algo: hmac-md5
[2008.08.21 13:56:29.593]      Purpose: MAC sc         		Algo: hmac-md5
[2008.08.21 13:56:29.593]      Purpose: compression cs 		Algo: invalid
[2008.08.21 13:56:29.593]      Purpose: compression sc 		Algo: invalid
[2008.08.21 13:56:29.593] [COLOR="Red"]Failed SSH Key Exchange[/COLOR]
[2008.08.21 13:56:29.593] [COLOR="Red"]SSH Transport closed.[/COLOR]


Any thoughts? I have reinstalled Ubuntu Server so it must have a new key but I haven't tried to connect via WS_FTP before so it wouldn't have the key logged anywhere.

---

### Post by windependence on 2008-08-21
Yes, but the key is per IP address so you will have to remove the key in the known hosts file (/etc/ssh/ssh_known_hosts )

-Tim

---

### Post by voteforpedro on 2008-08-21
> **windependence said:**
> Yes, but the key is per IP address so you will have to remove the key in the known hosts file (/etc/ssh/ssh_known_hosts )

-Tim

I don't have an ssh_known_hosts in /etc/ssh. :(

---

### Post by windependence on 2008-08-21
Ooops! Sorry, in Ubuntu it's at:

/home/username/.ssh/known_hosts

Just remove the offending key that is the same as the IP of the client you are trying to connect from.

-Tim

---

### Post by vmashburn on 2009-06-03
I am having the same issue, but the /.ssh is not in my username directory.  I have installed the openssh-server under my account though.  Any ideas?

---

