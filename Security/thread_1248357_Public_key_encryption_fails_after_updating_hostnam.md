---
title: "Public key encryption fails after updating hostname"
date: 2009-08-24
forum: Security
---

### Post by korin43 on 2009-08-24
So I have a server running Ubuntu 9.04 server, and a desktop computer running Ubuntu 9.04. Right after installing the server, the first thing I did was copy over public keys so I could ssh more quickly. It worked fine until I changed the hostname, and now it doesn't work anymore. Any ideas what happened? :(

I added the keys with scp *.pub server, then cat *.pub >> ./.ssh/authorized_keys
It worked perfectly until I changed my hostname.. And changing the hostname back doesn't help.

The permissions were set with:
```
chmod -R 700 .ssh
```
on both computers.

SSH:
```
brendan@brendan-desktop: $ ssh -v ###
OpenSSH_5.1p1 Debian-5ubuntu1, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to ### [###] port 22.
debug1: Connection established.
debug1: identity file /home/brendan/.ssh/identity type -1
debug1: identity file /home/brendan/.ssh/id_rsa type 1
debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-2048
debug1: Checking blacklist file /etc/ssh/blacklist.RSA-2048
debug1: identity file /home/brendan/.ssh/id_dsa type 2
debug1: Checking blacklist file /usr/share/ssh/blacklist.DSA-1024
debug1: Checking blacklist file /etc/ssh/blacklist.DSA-1024
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.1p1 Debian-5ubuntu1
debug1: match: OpenSSH_5.1p1 Debian-5ubuntu1 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.1p1 Debian-5ubuntu1
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-cbc hmac-md5 none
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host 'supremerule.net' is known and matches the RSA host key.
debug1: Found key in /home/brendan/.ssh/known_hosts:1
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Offering public key: /home/brendan/.ssh/id_dsa
debug1: Authentications that can continue: publickey,password
debug1: Offering public key: /home/brendan/.ssh/id_rsa
debug1: Authentications that can continue: publickey,password
debug1: Trying private key: /home/brendan/.ssh/identity
debug1: Next authentication method: password
```

SSHD:
```
brendan@###:~$ sudo /usr/sbin/sshd -d -p 22
debug1: sshd version OpenSSH_5.1p1 Debian-5ubuntu1
debug1: read PEM private key done: type RSA
debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-2048
debug1: Checking blacklist file /etc/ssh/blacklist.RSA-2048
debug1: private host key: #0 type 1 RSA
debug1: read PEM private key done: type DSA
debug1: Checking blacklist file /usr/share/ssh/blacklist.DSA-1024
debug1: Checking blacklist file /etc/ssh/blacklist.DSA-1024
debug1: private host key: #1 type 2 DSA
debug1: rexec_argv[0]='/usr/sbin/sshd'
debug1: rexec_argv[1]='-d'
debug1: rexec_argv[2]='-p'
debug1: rexec_argv[3]='22'
debug1: Bind to port 22 on 0.0.0.0.
Server listening on 0.0.0.0 port 22.
debug1: Bind to port 22 on ::.
Server listening on :: port 22.
debug1: Server will not fork when running in debugging mode.
debug1: rexec start in 5 out 5 newsock 5 pipe -1 sock 8
debug1: inetd sockets after dupping: 3, 3
Connection from ### port 49047
debug1: Client protocol version 2.0; client software version OpenSSH_5.1p1 Debian-5ubuntu1
debug1: match: OpenSSH_5.1p1 Debian-5ubuntu1 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.1p1 Debian-5ubuntu1
debug1: permanently_set_uid: 102/65534
debug1: list_hostkey_types: ssh-rsa,ssh-dss
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: kex: server->client aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST received
debug1: SSH2_MSG_KEX_DH_GEX_GROUP sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_INIT
debug1: SSH2_MSG_KEX_DH_GEX_REPLY sent
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: KEX done
debug1: userauth-request for user brendan service ssh-connection method none
debug1: attempt 0 failures 0
debug1: PAM: initializing for "brendan"
debug1: PAM: setting PAM_RHOST to "###"
debug1: PAM: setting PAM_TTY to "ssh"
Failed none for brendan from ### port 49047 ssh2
debug1: userauth-request for user brendan service ssh-connection method publickey
debug1: attempt 1 failures 0
debug1: test whether pkalg/pkblob are acceptable
debug1: Checking blacklist file /usr/share/ssh/blacklist.DSA-1024
debug1: Checking blacklist file /etc/ssh/blacklist.DSA-1024
debug1: temporarily_use_uid: 1000/1000 (e=0/0)
debug1: trying public key file /home/brendan/.ssh/authorized_keys
debug1: restore_uid: 0/0
debug1: temporarily_use_uid: 1000/1000 (e=0/0)
debug1: trying public key file /home/brendan/.ssh/authorized_keys2
debug1: restore_uid: 0/0
Failed publickey for brendan from ### port 49047 ssh2
debug1: userauth-request for user brendan service ssh-connection method publickey
debug1: attempt 2 failures 1
debug1: test whether pkalg/pkblob are acceptable
debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-2048
debug1: Checking blacklist file /etc/ssh/blacklist.RSA-2048
debug1: temporarily_use_uid: 1000/1000 (e=0/0)
debug1: trying public key file /home/brendan/.ssh/authorized_keys
debug1: restore_uid: 0/0
debug1: temporarily_use_uid: 1000/1000 (e=0/0)
debug1: trying public key file /home/brendan/.ssh/authorized_keys2
debug1: restore_uid: 0/0
Failed publickey for brendan from ### port 49047 ssh2
```

---

### Post by korin43 on 2009-08-24
This thread contains a workaround: [https://bugs.launchpad.net/ubuntu/+source/openssh/+bug/362427](https://bugs.launchpad.net/ubuntu/+source/openssh/+bug/362427)

It's strange though because I wasn't using encrypted home directories, but I did chmod my home directories to 770.

Anyway, if anyone else needs it, the workaround I used was to move my /home/me/.ssh/authorized_keys to /etc/ssh/me/authorized_keys and then change the AuthorizedKeysFile setting in /etc/ssh/ssh_config to /etc/ssh/%u/authorized_keys

---

### Post by kevdog on 2009-08-24
Why did you have to do that?  Change the directory?

---

