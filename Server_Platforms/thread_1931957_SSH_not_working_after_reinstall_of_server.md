---
title: "SSH not working after reinstall of server"
date: 2012-02-26
forum: Server Platforms
---

### Post by Terry Su on 2012-02-26
I've had to reinstall server after having problems created by installing EHCP Hosting Panel after installing Tikiwiki. Had ssh set up and  working well before reinstalling. Now I get the following when I try and connect with ssh.
> 

owner@Owners-Pangolin-Performance:~$ sudo ssh -v owners@192.168.1.104
[sudo] password for owner: 
OpenSSH_5.8p1 Debian-1ubuntu3, OpenSSL 0.9.8o 01 Jun 2010
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to 192.168.1.104 [192.168.1.104] port 22.
debug1: Connection established.
debug1: permanently_set_uid: 0/0
debug1: identity file /root/.ssh/id_rsa type -1
debug1: identity file /root/.ssh/id_rsa-cert type -1
debug1: identity file /root/.ssh/id_dsa type -1
debug1: identity file /root/.ssh/id_dsa-cert type -1
debug1: identity file /root/.ssh/id_ecdsa type -1
debug1: identity file /root/.ssh/id_ecdsa-cert type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.3p1 Debian-3ubuntu7
debug1: match: OpenSSH_5.3p1 Debian-3ubuntu7 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.8p1 Debian-1ubuntu3
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-ctr hmac-md5 none
debug1: kex: client->server aes128-ctr hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Server host key: RSA 4a:1d:41:d9:95:81:52:e7:5b:bf:67:39:7f:2d:d8:80
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that a host key has just been changed.
The fingerprint for the RSA key sent by the remote host is
4a:1d:41:d9:95:81:52:e7:5b:bf:67:39:7f:2d:d8:80.
Please contact your system administrator.
Add correct host key in /root/.ssh/known_hosts to get rid of this message.
Offending RSA key in /root/.ssh/known_hosts:3
  remove with: ssh-keygen -f "/root/.ssh/known_hosts" -R 192.168.1.104
RSA host key for 192.168.1.104 has changed and you have requested strict checking.
Host key verification failed.
owner@owners-Pangolin-Performance:~$ 

This has to be a trivial problem, but I've been searching Ubuntu Forums for a couple of days and read many man pages I've fooled with sshd_config and looked at associated files to no avail. Also looking in OpenSSH website email archives without finding references to my problem.

I'd be very grateful for any help.

---

### Post by CharlesA on 2012-02-26
When you reinstalled, the host key changed.

Run this:

```
sudo ssh-keygen -f "/root/.ssh/known_hosts" -R 192.168.1.104
```

Sidenote, you shouldn't have to run ssh with sudo because you are telling it which user to connect as.

---

### Post by Terry Su on 2012-02-26
I  am flabbergasted!!

I'd swear that I tried that command several times with no result.  I did copy and paste your code so maybe I was doing something stupid but....

Thank you so much.  Next time I'm in trouble I'll come to the 'Forum a little quicker although I did learn a lot.

---

### Post by Terry Su on 2012-02-26
OK.  I was putting a space between the / after root and the . ahead of ssh.  fun!!


sudo ssh-keygen -f "/root/.ssh/known_hosts" -R 192.168.1.104

---

