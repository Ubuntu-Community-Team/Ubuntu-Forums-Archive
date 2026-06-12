---
title: "New rsa keys not working since patch"
date: 2008-05-22
forum: Security
---

### Post by russpadd on 2008-05-22
I recently applied the ssh patch to my 2 ubuntu systems and now rsa keys no longer work, it always prompts for the regular password.


I tried generating all new keys and followed all the instructions at [https://help.ubuntu.com/community/AdvancedOpenSSH#head-f06532af79917a251e68c7ccf567cb5c399e0aba](https://help.ubuntu.com/community/AdvancedOpenSSH#head-f06532af79917a251e68c7ccf567cb5c399e0aba)

I've checked my sshd_config and restarted the server, making sure that:
RSAAuthentication yes
PubkeyAuthentication yes
are both included.


I've generated new keys, made sure they were in the proper ~/.ssh/id_rsa and id_rsa.pub files and made sure to add them to .ssh/authorized_keys on the remote user account.  I've double-checked them and the values are the exact same on both machines.


ssh-copy-id -i ~/.ssh/id_rsa.pub reports:
```
/usr/bin/ssh-copy-id: ERROR: No identities found
```


ssh says:
```
ssh -v -pXXXX russ@XXX.XXX.XXX.XXX
OpenSSH_4.2p1 Debian-7ubuntu3.4, OpenSSL 0.9.8a 11 Oct 2005
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to XXX.XXX.XXX.XXX [XXX.XXX.XXX.XXX] port XXXX.
debug1: Connection established.
debug1: identity file /home/russ/.ssh/identity type -1
debug1: identity file /home/russ/.ssh/id_rsa type 1
debug1: identity file /home/russ/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_4.3p2 Debian-8ubuntu1.4
debug1: match: OpenSSH_4.3p2 Debian-8ubuntu1.4 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_4.2p1 Debian-7ubuntu3.4
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-cbc hmac-md5 none
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host 'XXX.XXX.XXX.XXX' is known and matches the RSA host key.
debug1: Found key in /home/russ/.ssh/known_hosts:4
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Trying private key: /home/russ/.ssh/identity
debug1: Offering public key: /home/russ/.ssh/id_rsa
debug1: Authentications that can continue: publickey,password
debug1: Trying private key: /home/russ/.ssh/id_dsa
debug1: Next authentication method: password
russ@XXX.XXX.XXX.XXX's password:
```

Any idea what's going on?

---

### Post by movieman on 2008-05-22
In my experience, public keys randomly not working is usually due to file permissions on the key files or directories. If the permissions are wrong (e.g. keys are world-writeable) and strict key checks are enabled in the sshd config file, then the keys will be ignored.

---

### Post by russpadd on 2008-05-22
Ah, bingo.


The key files were locked, but the remote user's home directory was set group writable.  As soon as I changed that it all started working again.


Thanks!

---

