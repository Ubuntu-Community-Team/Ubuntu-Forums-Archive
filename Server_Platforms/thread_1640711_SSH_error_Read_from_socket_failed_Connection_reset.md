---
title: "SSH error: Read from socket failed: Connection reset by peer"
date: 2010-12-08
forum: Server Platforms
---

### Post by kradalby on 2010-12-08
Hi

Can someone help me figure out this error?

```
kradalby@hpcompaq6530b-laptop ~/.ssh $ ssh -vvv -p 110 kradalby@dfekt.no
OpenSSH_5.5p1 Debian-5+b1, OpenSSL 0.9.8o 01 Jun 2010
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to dfekt.no [81.167.61.169] port 110.
debug1: Connection established.
debug3: Not a RSA1 key file /home/kradalby/.ssh/id_rsa.
debug2: key_type_from_name: unknown key type '-----BEGIN'
debug3: key_read: missing keytype
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug2: key_type_from_name: unknown key type '-----END'
debug3: key_read: missing keytype
debug1: identity file /home/kradalby/.ssh/id_rsa type 1
debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-2048
debug1: Checking blacklist file /etc/ssh/blacklist.RSA-2048
debug1: identity file /home/kradalby/.ssh/id_rsa-cert type -1
debug1: identity file /home/kradalby/.ssh/id_dsa type -1
debug1: identity file /home/kradalby/.ssh/id_dsa-cert type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.3p1 Debian-3ubuntu4
debug1: match: OpenSSH_5.3p1 Debian-3ubuntu4 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.5p1 Debian-5+b1
debug2: fd 3 setting O_NONBLOCK
debug1: SSH2_MSG_KEXINIT sent
Read from socket failed: Connection reset by peer

```

Information:
Im trying to connect from my schools network.
Doesnt this mean that it actually does get trough the server?
```
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.3p1 Debian-3ubuntu4
```
The server is Ubuntu server 10.04 LTS up to date.
The client is Linux Mint Debian up to date.
The server runs on port 22 and 110, 22 is blocked by the school and the 110 is a mail port that is open.

Is it possible that the school has blocked the whole ssh protocol? 

Port 22 error:
ssh_exchange_identification: read: Connection reset by peer


Hope someone can help :)

.kradalby

---

### Post by chrislynch8 on 2010-12-08
You've answered your own question - if your trying to access on port 22 and its blocked how do you expect to access it?

port 110 is in use for mail as you've said so I can't see a ssh server accepting connections over port 110.

Is it your ssh server your are trying to acces?

Chris

---

### Post by sag47 on 2011-08-09
Your theory of the port being blocked is wrong.  I don't know what it is but I know the port isn't blocked.

I have two Linux machines.

KUbuntu 10.04 LTS
Ubuntu 11.04

The K machine can connect to ssh just fine.

The U machine can't connect throwing the error:
```
Read from socket failed: Connection reset by peer
```

Does anyone who knows about this error have a solution?  This is obviously an Ubuntu problem and not a blocked port problem.

---

### Post by hawkmage on 2011-08-09
The error is exactly what it says.  The peer, the system you are connecting to, closed the TCP connection.  in the case of the port 110 I would make sure that sshd is listening on port 110 on that system, it is normally the port that the POP service listens on.  

Can you log into the system you are logging into and run the command:
```
sudo lsof -i -nP
```
and look for what is binding to the port you are trying to ssh into.

If it is not there the sshd is not binding to that port or if it is something other than sshd that is binding to the port then your sshd and the other service are not configured to allow you to ssh into that port.  Also if the IP address listed for the listening address is 127.0.0.1 then the service is binding to the loop backhand you can not get to that from a remote system.

---

### Post by hamadazein84 on 2013-03-09
Hi,
I have similar problem.


I am trying to connect to my Linux machine using SSH but I get this error:
Read from socket failed: Connection reset by peer


this the the debug info when I am trying to run this command: ssh -v localhost


OpenSSH_5.9p1 Debian-5ubuntu1, OpenSSL 1.0.1 14 Mar 2012
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug1: Connecting to localhost [127.0.0.1] port 22.
debug1: Connection established.
debug1: identity file /home/hamada/.ssh/id_rsa type -1
debug1: identity file /home/hamada/.ssh/id_rsa-cert type -1
debug1: identity file /home/hamada/.ssh/id_dsa type -1
debug1: identity file /home/hamada/.ssh/id_dsa-cert type -1
debug1: identity file /home/hamada/.ssh/id_ecdsa type -1
debug1: identity file /home/hamada/.ssh/id_ecdsa-cert type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.9p1 Debian-5ubuntu1
debug1: match: OpenSSH_5.9p1 Debian-5ubuntu1 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.9p1 Debian-5ubuntu1
debug1: SSH2_MSG_KEXINIT sent
Read from socket failed: Connection reset by peer

---

