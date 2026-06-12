---
title: "SSH Fails - Permission denied (publickey)"
date: 2011-02-17
forum: Server Platforms
---

### Post by AndF0 on 2011-02-17
Hi guys, 
for some reason I can't ssh into my cloud instance.
I also deleted the file "known_hosts" but that didn't change anything. 
I get the following error: 

```

$ ssh -i adminkey.private root@XX.XX.XX.9 -v
OpenSSH_5.5p1 Debian-4ubuntu5, OpenSSL 0.9.8o 01 Jun 2010
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to XX.XX.XX.98 [XX.XX.XX.9] port 22.
debug1: Connection established.
debug1: identity file adminkey.private type -1
debug1: identity file adminkey.private-cert type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.1p1 Debian-6ubuntu2
debug1: match: OpenSSH_5.1p1 Debian-6ubuntu2 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.5p1 Debian-4ubuntu5
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-ctr hmac-md5 none
debug1: kex: client->server aes128-ctr hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host 'XX.XX.XX.98' is known and matches the RSA host key.
debug1: Found key in /home/af/.ssh/known_hosts:1
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: Roaming not allowed by server
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey
debug1: Next authentication method: publickey
debug1: Trying private key: adminkey.private
debug1: read PEM private key done: type RSA
debug1: Authentications that can continue: publickey
debug1: No more authentication methods to try.
Permission denied (publickey).


```
THX!!

---

### Post by Neo@Matrix on 2011-02-17
By my opinion U have to re-config UR server , as it states: 
Roaming not allowed by server

---

