---
title: "Cannot ssh onto server with key file"
date: 2014-12-23
forum: Ubuntu Cloud and Juju
---

### Post by anonymouschief on 2014-12-23
Hello Ubuntu Gurus,

Whenever I try to connect to an Ubuntu Server, I get the following:

```

localuser@LocalMachine:~$ ssh -i ~/.ssh/myprivate.key -vvv user@domain.com
OpenSSH_6.6.1, OpenSSL 1.0.1f 6 Jan 2014
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to domain.com [X.X.X.X] port 22.
debug1: Connection established.
debug3: Incorrect RSA1 identifier
debug3: Could not load "/home/localuser/.ssh/myprivate.key" as a RSA1 public key
debug1: identity file /home/localuser/.ssh/myprivate.key type -1
debug1: identity file /home/localuser/.ssh/myprivate.key-cert type -1
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_6.6.1p1 Ubuntu-2ubuntu2
debug1: Remote protocol version 2.0, remote software version OpenSSH_6.7p1 Ubuntu-3
debug1: match: OpenSSH_6.7p1 Ubuntu-3 pat OpenSSH* compat 0x04000000
debug2: fd 3 setting O_NONBLOCK
debug3: load_hostkeys: loading entries for host "domain.com" from file "/home/localuser/.ssh/known_hosts"
debug3: load_hostkeys: found key type ECDSA in file /home/localuser/.ssh/known_hosts:1
debug3: load_hostkeys: loaded 1 keys
debug3: order_hostkeyalgs: prefer hostkeyalgs: ecdsa-sha2-nistp256-cert-v01@openssh.com,ecdsa-sha2-nistp384-cert-v01@openssh.com,ecdsa-sha2-nistp521-cert-v01@openssh.com,ecdsa-sha2-nistp256,ecdsa-sha2-nistp384,ecdsa-sha2-nistp521
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug2: kex_parse_kexinit: curve25519-sha256@libssh.org,ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ecdsa-sha2-nistp256-cert-v01@openssh.com,ecdsa-sha2-nistp384-cert-v01@openssh.com,ecdsa-sha2-nistp521-cert-v01@openssh.com,ecdsa-sha2-nistp256,ecdsa-sha2-nistp384,ecdsa-sha2-nistp521,ssh-ed25519-cert-v01@openssh.com,ssh-rsa-cert-v01@openssh.com,ssh-dss-cert-v01@openssh.com,ssh-rsa-cert-v00@openssh.com,ssh-dss-cert-v00@openssh.com,ssh-ed25519,ssh-rsa,ssh-dss
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-gcm@openssh.com,aes256-gcm@openssh.com,chacha20-poly1305@openssh.com,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-gcm@openssh.com,aes256-gcm@openssh.com,chacha20-poly1305@openssh.com,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: hmac-md5-etm@openssh.com,hmac-sha1-etm@openssh.com,umac-64-etm@openssh.com,umac-128-etm@openssh.com,hmac-sha2-256-etm@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-ripemd160-etm@openssh.com,hmac-sha1-96-etm@openssh.com,hmac-md5-96-etm@openssh.com,hmac-md5,hmac-sha1,umac-64@openssh.com,umac-128@openssh.com,hmac-sha2-256,hmac-sha2-512,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5-etm@openssh.com,hmac-sha1-etm@openssh.com,umac-64-etm@openssh.com,umac-128-etm@openssh.com,hmac-sha2-256-etm@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-ripemd160-etm@openssh.com,hmac-sha1-96-etm@openssh.com,hmac-md5-96-etm@openssh.com,hmac-md5,hmac-sha1,umac-64@openssh.com,umac-128@openssh.com,hmac-sha2-256,hmac-sha2-512,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: first_kex_follows 0 
debug2: kex_parse_kexinit: reserved 0 
debug2: kex_parse_kexinit: curve25519-sha256@libssh.org,ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group14-sha1
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss,ecdsa-sha2-nistp256
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,aes128-gcm@openssh.com,aes256-gcm@openssh.com,chacha20-poly1305@openssh.com
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,aes128-gcm@openssh.com,aes256-gcm@openssh.com,chacha20-poly1305@openssh.com
debug2: kex_parse_kexinit: umac-64-etm@openssh.com,umac-128-etm@openssh.com,hmac-sha2-256-etm@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-sha1-etm@openssh.com,umac-64@openssh.com,umac-128@openssh.com,hmac-sha2-256,hmac-sha2-512,hmac-sha1
debug2: kex_parse_kexinit: umac-64-etm@openssh.com,umac-128-etm@openssh.com,hmac-sha2-256-etm@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-sha1-etm@openssh.com,umac-64@openssh.com,umac-128@openssh.com,hmac-sha2-256,hmac-sha2-512,hmac-sha1
debug2: kex_parse_kexinit: none,zlib@openssh.com
debug2: kex_parse_kexinit: none,zlib@openssh.com
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: first_kex_follows 0 
debug2: kex_parse_kexinit: reserved 0 
debug2: mac_setup: setup hmac-sha1-etm@openssh.com
debug1: kex: server->client aes128-ctr hmac-sha1-etm@openssh.com none
debug2: mac_setup: setup hmac-sha1-etm@openssh.com
debug1: kex: client->server aes128-ctr hmac-sha1-etm@openssh.com none
debug1: sending SSH2_MSG_KEX_ECDH_INIT
debug1: expecting SSH2_MSG_KEX_ECDH_REPLY
debug1: Server host key: ECDSA a1:a1:a1:a1:a1:a1:a1:a1:a1:a1:a1:a1:a1:a1:a1:a1
debug3: load_hostkeys: loading entries for host "domain.com" from file "/home/localuser/.ssh/known_hosts"
debug3: load_hostkeys: found key type ECDSA in file /home/localuser/.ssh/known_hosts:1
debug3: load_hostkeys: loaded 1 keys
debug3: load_hostkeys: loading entries for host "X.X.X.X" from file "/home/localuser/.ssh/known_hosts"
debug3: load_hostkeys: found key type ECDSA in file /home/localuser/.ssh/known_hosts:2
debug3: load_hostkeys: loaded 1 keys
debug1: Host 'domain.com' is known and matches the ECDSA host key.
debug1: Found key in /home/localuser/.ssh/known_hosts:1
debug1: ssh_ecdsa_verify: signature correct
debug2: kex_derive_keys
debug2: set_newkeys: mode 1
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug2: set_newkeys: mode 0
debug1: SSH2_MSG_NEWKEYS received
debug1: Roaming not allowed by server
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug2: service_accept: ssh-userauth
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug2: key: /home/localuser/.ssh/myprivate.key ((nil)), explicit
debug1: Authentications that can continue: publickey,password
debug3: start over, passed a different list publickey,password
debug3: preferred gssapi-keyex,gssapi-with-mic,publickey,keyboard-interactive,password
debug3: authmethod_lookup publickey
debug3: remaining preferred: keyboard-interactive,password
debug3: authmethod_is_enabled publickey
debug1: Next authentication method: publickey
debug1: Trying private key: /home/localuser/.ssh/myprivate.key
debug1: key_parse_private2: missing begin marker
debug1: read PEM private key done: type RSA
debug3: sign_and_send_pubkey: RSA a2:a2:a2:a2:a2:a2:a2:a2:a2:a2:a2:a2:a2:a2:a2:a2
debug2: we sent a publickey packet, wait for reply
debug1: Authentications that can continue: publickey,password
debug2: we did not send a packet, disable method
debug3: authmethod_lookup password
debug3: remaining preferred: ,password
debug3: authmethod_is_enabled password
debug1: Next authentication method: password
user@domain.com's password: 

```

I am trying to run Snappy Ubuntu Core on Azure, as per [http://www.ubuntu.com/cloud/tools/snappy#snappy-azure](http://www.ubuntu.com/cloud/tools/snappy#snappy-azure)
I am connecting from an Ubuntu 14.04 desktop.
Thanks.

---

### Post by steeldriver on 2014-12-23
How exactly did you generate / install the key pair?

---

### Post by Lars Noodén on 2014-12-23
How did you generate the "~/.ssh/myprivate.key" and "~/.ssh/myprivate.key.pub" key pair?  It looks like there may be something wrong with it.  RSA1 is long since deprecated.  You might consider ed25519.

Edit: oops, too slow :)

---

### Post by anonymouschief on 2014-12-23
openssl req -x509 -nodes -days 365 -newkey rsa:2048 \
-keyout azure.key -out azure_pub.pem -subj "/CN=${USER}/"

---

### Post by Lars Noodén on 2014-12-23
I can't speak to use of certificates with openssh, there is a way to do it but I am unfamiliar with them.  With regards to keys, they are usually made with [ssh-keygen](http://manpages.ubuntu.com/manpages/trusty/en/man1/ssh-keygen.1.html)

```

ssh-keygen -t ed25519 -f azure.key -C 'Azure Key'

```

---

### Post by anonymouschief on 2014-12-23
ssh-keygen keys will not work with Azure. They require openssl-generated ones. See :[http://www.ubuntu.com/cloud/tools/snappy](http://www.ubuntu.com/cloud/tools/snappy)
Thanks.

---

### Post by anonymouschief on 2014-12-23
I'm in. The mistake was in the certificate creation. The following is what I used, and it worked:
```

openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout azure.key -out azure_pub.pem -subj "/CN=serveruser/"

```

---

