---
title: "Cisco Call Manager and SFTP backup"
date: 2009-10-06
forum: Security
---

### Post by dcamp25 on 2009-10-06
All,

I am able to log into my ubuntu 9.04 system and download files and upload files.  I can transfer files and so on.


When I try to backup a Cisco Call manager to my ubuntu machine with SFTP I get nowhere.  I have verified my config and all other SFTP functions work.  A friend of mine told me that Cisco call manager does not accept encrypted streams.  Any cisco guys out the with this problem.  I will post any config asked.  I am new to Ubuntu so be kind.


Thanks

Doug

---

### Post by The Cog on 2009-10-07
Is the call manager trying to make an stfp connection to the Ubuntu server, or is the Ubuntu server trying to connect to the call manager?

When you say you get nowhere, do you get any error message from the machine that's trying to make the connection?

I'm not familiar with call manager, but if it has an option to send backups, via sftp then by definition it is able to handle encrypted streams.

---

### Post by Lars Noodén on 2009-10-08
Does the Cisco Call Manager even have port 22 open and accept SSH and SFTP connections?

```

# assuming call manager has IPv4 192.168.0.25 and login user is dcamp25  
**sudo scanssh -n 22 -s ssh 192.168.0.25**
192.168.0.25:22 SSH-2.0-OpenSSH_5.3
Effective host scan rate: 1.01 hosts/s

```

What messages do you see when you increase the verbosity of the client using -v, -vv, or -vvv

```

** sftp -v dcamp25@192.168.0.25**
Connecting to 192.168.0.25...
OpenSSH_5.1p1 Debian-6ubuntu1, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to 192.168.0.25 [192.168.0.25] port 22.
debug1: Connection established.
debug1: permanently_set_uid: 0/0
debug1: identity file /dcamp25/.ssh/id_rsa type -1
debug1: identity file /dcamp25/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.3
debug1: match: OpenSSH_5.3 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.1p1 Debian-6ubuntu1
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-cbc hmac-md5 none
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
The authenticity of host 'callmgr.dcamp25.com (192.168.0.25)' can't be established.
RSA key fingerprint is 29:54:11:7d:79:3c:d9:14:a6:e8:96:09:c7:c0:61:4b.
Are you sure you want to continue connecting (yes/no)

```

---

