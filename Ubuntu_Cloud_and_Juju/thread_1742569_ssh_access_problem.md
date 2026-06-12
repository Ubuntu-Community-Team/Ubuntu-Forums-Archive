---
title: "ssh access problem"
date: 2011-04-29
forum: Ubuntu Cloud and Juju
---

### Post by viswacse02 on 2011-04-29
[email]cloud@node:~/.ssh[/email]$ ssh -v -i mykey.priv ubuntu@10.1.1.106
OpenSSH_5.3p1 Debian-3ubuntu6, OpenSSL 0.9.8k 25 Mar 2009
Warning: Identity file mykey.priv not accessible: No such file or directory.
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to 10.1.1.106 [10.1.1.106] port 22.
debug1: Connection established.
debug1: identity file /home/cloud/.ssh/identity type -1
debug1: identity file /home/cloud/.ssh/id_rsa type -1
debug1: identity file /home/cloud/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.3p1 Debian-3ubuntu6
debug1: match: OpenSSH_5.3p1 Debian-3ubuntu6 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.3p1 Debian-3ubuntu6
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-ctr hmac-md5 none
debug1: kex: client->server aes128-ctr hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
The authenticity of host '10.1.1.106 (10.1.1.106)' can't be established.
RSA key fingerprint is 0d:5d:c9:b4:74:c5:5d:22:48:45:8a:6e:ac:f8:f3:6e.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added '10.1.1.106' (RSA) to the list of known hosts.
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey
debug1: Next authentication method: publickey
debug1: Trying private key: /home/cloud/.ssh/identity
debug1: Trying private key: /home/cloud/.ssh/id_rsa
debug1: Trying private key: /home/cloud/.ssh/id_dsa
debug1: No more authentication methods to try.
Permission denied (publickey).
[email]cloud@node:~/.ssh[/email]$ 

How to troubleshoot this problem?

---

### Post by dverebe on 2011-05-02
The first error code suggests that the key file hasn't been found - perhaps try to use a full path.

---

### Post by kim0 on 2011-05-03
also please make sure you used euca-add-keypair to register your keys are found in the UEC documentation

---

### Post by viswacse02 on 2011-05-04
still i could not solve the problem

---

