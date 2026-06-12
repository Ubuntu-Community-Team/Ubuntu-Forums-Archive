---
title: "SSH Problem"
date: 2008-06-13
forum: Server Platforms
---

### Post by JeffElkins on 2008-06-13
I've been using passwordless ssh on my home network for ages. Suddenly, one particular system (ubuntu server 7.10) is suddenly requiring a password for incoming connections. From that machine, you can ssh w/o password to other machines on the network. I did regen the system's ssh_host keys w/o effect. Root's .ssh authorized_keys2,id_dsa and id_dsa.pub files are present and unchanged.I'm stymied. Where do I start looking to debug this problem?

---

### Post by HermanAB on 2008-06-13
On the server, the public keys are kept in ~/.ssh/authorized_keys.  This is a text file.  Look at it with 'less' or something and see which public keys are in there.  If it doesn't have a public key for each of your other machines, then add them.

To debug the issue enable verbose errors with:
$ ssh -vvv user@server

Cheers,

Herman

---

### Post by JeffElkins on 2008-06-13
```

OpenSSH_4.7p1 Debian-8ubuntu1.2, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to kmac [192.168.0.10] port 22.
debug1: Connection established.
debug1: permanently_set_uid: 0/0
debug1: identity file /root/.ssh/identity type -1
debug1: identity file /root/.ssh/id_rsa type -1
debug3: Not a RSA1 key file /root/.ssh/id_dsa.
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
debug2: key_type_from_name: unknown key type '-----END'
debug3: key_read: missing keytype
debug1: identity file /root/.ssh/id_dsa type 2
debug1: Remote protocol version 2.0, remote software version OpenSSH_4.6p1 Debian-5ubuntu0.5
debug1: match: OpenSSH_4.6p1 Debian-5ubuntu0.5 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_4.7p1 Debian-8ubuntu1.2
debug2: fd 3 setting O_NONBLOCK
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib
debug2: kex_parse_kexinit:
debug2: kex_parse_kexinit:
debug2: kex_parse_kexinit: first_kex_follows 0
debug2: kex_parse_kexinit: reserved 0
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib@openssh.com
debug2: kex_parse_kexinit: none,zlib@openssh.com
debug2: kex_parse_kexinit:
debug2: kex_parse_kexinit:
debug2: kex_parse_kexinit: first_kex_follows 0
debug2: kex_parse_kexinit: reserved 0
debug2: mac_setup: found hmac-md5
debug1: kex: server->client aes128-cbc hmac-md5 none
debug2: mac_setup: found hmac-md5
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug2: dh_gen_key: priv key bits set: 131/256
debug2: bits set: 511/1024
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug3: check_host_in_hostfile: filename /root/.ssh/known_hosts
debug3: check_host_in_hostfile: match line 1
debug3: check_host_in_hostfile: filename /root/.ssh/known_hosts
debug3: check_host_in_hostfile: match line 2
debug1: Host 'kmac' is known and matches the RSA host key.
debug1: Found key in /root/.ssh/known_hosts:1
debug2: bits set: 503/1024
debug1: ssh_rsa_verify: signature correct
debug2: kex_derive_keys
debug2: set_newkeys: mode 1
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug2: set_newkeys: mode 0
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug2: service_accept: ssh-userauth
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug2: key: /root/.ssh/identity ((nil))
debug2: key: /root/.ssh/id_rsa ((nil))
debug2: key: /root/.ssh/id_dsa (0xb7fbc600)
debug1: Authentications that can continue: publickey,password
debug3: start over, passed a different list publickey,password
debug3: preferred gssapi-keyex,gssapi-with-mic,gssapi,publickey,keyboard-interactive,password
debug3: authmethod_lookup publickey
debug3: remaining preferred: keyboard-interactive,password
debug3: authmethod_is_enabled publickey
debug1: Next authentication method: publickey
debug1: Trying private key: /root/.ssh/identity
debug3: no such identity: /root/.ssh/identity
debug1: Trying private key: /root/.ssh/id_rsa
debug3: no such identity: /root/.ssh/id_rsa
debug1: Offering public key: /root/.ssh/id_dsa
debug3: send_pubkey_test
debug2: we sent a publickey packet, wait for reply
debug1: Authentications that can continue: publickey,password
debug2: we did not send a packet, disable method
debug3: authmethod_lookup password
debug3: remaining preferred: ,password
debug3: authmethod_is_enabled password
debug1: Next authentication method: password

```

Thanks for the reply. All of my machines have the same exact authorized_keys2 file located in /root/.ssh. It contains one entry only. The /root/.ssh directory also contains the same exact (contents the same) id_dsa* files for each machine on the network. Is this secure? Beats me, but I've been using this system for several years: I add a machine to my home network and copy /root/.ssh from an existing box to the new box and happily ssh in from other boxes on the home network. My problem is that this has suddenly failed for one box only. All other boxes on this home network continue to function as they have for the past several years.

I've posted the console output from ssh -vvv root@problemserver above.

---

### Post by JeffElkins on 2008-06-13
```

-rw-r--r-- 1 root root  600 2008-05-21 02:21 authorized_keys2
-rw------- 1 root root  668 2008-05-21 02:21 id_dsa
-rw-r--r-- 1 root root  600 2008-05-21 02:21 id_dsa.pub
-rw-r--r-- 1 root root 3200 2008-06-13 13:08 known_hosts

```

Just for chuckles, I checked the permissions for the malfunctioning box and they match the rest...

---

### Post by tr333 on 2008-06-14
The file should be called 'authorized_keys' not 'authorized_keys2'.  Try renaming this file and see if that fixes your problem.

---

### Post by JeffElkins on 2008-06-14
> **tr333 said:**
> The file should be called 'authorized_keys' not 'authorized_keys2'.  Try renaming this file and see if that fixes your problem.

> 
For backward compatibility ~/.ssh/authorized_keys2 will still used for
   authentication and hostkeys are still read from the known_hosts2.


authorized_keys2 is depreciated, but still works. All my machines still use it. I did make the change though, w/o effect.

---

