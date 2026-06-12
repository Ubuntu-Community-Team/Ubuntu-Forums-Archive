---
title: "problem ssh access macbook -&gt; ubuntu server"
date: 2014-04-29
forum: Server Platforms
---

### Post by benoit5 on 2014-04-29
Hello everyone

I have been some issues to connect by ssh to my server. In fact I have changed internet connection (new box etc...) and access by ssh is impossible.
```
ssh benoit@192.168.1.12
```
give
```
[FONT=Menlo]OpenSSH_6.2p2, OSSLShim 0.9.8r 8 Dec 2011[/FONT][FONT=Menlo]debug2: ssh_connect: needpriv 0[/FONT]
[FONT=Menlo]debug1: Connecting to 192.168.1.12 [192.168.1.12] port 22.[/FONT]
[FONT=Menlo]debug1: Connection established.[/FONT]
[FONT=Menlo]debug3: Incorrect RSA1 identifier[/FONT]
[FONT=Menlo]debug3: Could not load "/Users/maths/.ssh/id_rsa" as a RSA1 public key[/FONT]
[FONT=Menlo]debug1: identity file /Users/maths/.ssh/id_rsa type 1[/FONT]
[FONT=Menlo]debug1: identity file /Users/maths/.ssh/id_rsa-cert type -1[/FONT]
[FONT=Menlo]debug1: identity file /Users/maths/.ssh/id_dsa type -1[/FONT]
[FONT=Menlo]debug1: identity file /Users/maths/.ssh/id_dsa-cert type -1[/FONT]
[FONT=Menlo]debug1: Enabling compatibility mode for protocol 2.0[/FONT]
[FONT=Menlo]debug1: Local version string SSH-2.0-OpenSSH_6.2[/FONT]
[FONT=Menlo]debug1: Remote protocol version 2.0, remote software version OpenSSH_5.9p1 Debian-5ubuntu1.3[/FONT]
[FONT=Menlo]debug1: match: OpenSSH_5.9p1 Debian-5ubuntu1.3 pat OpenSSH_5*[/FONT]
[FONT=Menlo]debug2: fd 3 setting O_NONBLOCK[/FONT]
[FONT=Menlo]debug3: load_hostkeys: loading entries for host "192.168.1.12" from file "/Users/maths/.ssh/known_hosts"[/FONT]
[FONT=Menlo]debug3: load_hostkeys: found key type DSA in file /Users/maths/.ssh/known_hosts:1[/FONT]
[FONT=Menlo]debug3: load_hostkeys: loaded 1 keys[/FONT]
[FONT=Menlo]debug3: order_hostkeyalgs: prefer hostkeyalgs: ssh-dss-cert-v01@openssh.com,ssh-dss-cert-v00@openssh.com,ssh-dss[/FONT]
[FONT=Menlo]debug1: SSH2_MSG_KEXINIT sent[/FONT]
[FONT=Menlo]debug1: SSH2_MSG_KEXINIT received[/FONT]
[FONT=Menlo]debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1[/FONT]
[FONT=Menlo]debug2: kex_parse_kexinit: ssh-dss-cert-v01@openssh.com,ssh-dss-cert-v00@openssh.com,ssh-dss,ssh-rsa-cert-v01@openssh.com,ssh-rsa-cert-v00@openssh.com,ssh-rsa[/FONT]
[FONT=Menlo]debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-gcm@openssh.com,aes256-gcm@openssh.com,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se[/FONT]
[FONT=Menlo]debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-gcm@openssh.com,aes256-gcm@openssh.com,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se[/FONT]
[FONT=Menlo]debug2: kex_parse_kexinit: hmac-md5-etm@openssh.com,hmac-sha1-etm@openssh.com,umac-64-etm@openssh.com,umac-128-etm@openssh.com,hmac-sha2-256-etm@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-ripemd160-etm@openssh.com,hmac-sha1-96-etm@openssh.com,hmac-md5-96-etm@openssh.com,hmac-md5,hmac-sha1,umac-64@openssh.com,umac-128@openssh.com,hmac-sha2-256,hmac-sha2-512,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96[/FONT]
[FONT=Menlo]debug2: kex_parse_kexinit: hmac-md5-etm@openssh.com,hmac-sha1-etm@openssh.com,umac-64-etm@openssh.com,umac-128-etm@openssh.com,hmac-sha2-256-etm@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-ripemd160-etm@openssh.com,hmac-sha1-96-etm@openssh.com,hmac-md5-96-etm@openssh.com,hmac-md5,hmac-sha1,umac-64@openssh.com,umac-128@openssh.com,hmac-sha2-256,hmac-sha2-512,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96[/FONT]
[FONT=Menlo]debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib[/FONT]
[FONT=Menlo]debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib[/FONT]
[FONT=Menlo]debug2: kex_parse_kexinit: [/FONT]
[FONT=Menlo]debug2: kex_parse_kexinit: [/FONT]
[FONT=Menlo]debug2: kex_parse_kexinit: first_kex_follows 0 [/FONT]
[FONT=Menlo]debug2: kex_parse_kexinit: reserved 0 [/FONT]
[FONT=Menlo]debug2: kex_parse_kexinit: ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1[/FONT]
[FONT=Menlo]debug2: kex_parse_kexinit: ssh-dss,ssh-dss[/FONT]
[FONT=Menlo]debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se[/FONT]
[FONT=Menlo]debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se[/FONT]
[FONT=Menlo]debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-sha2-256,hmac-sha2-256-96,hmac-sha2-512,hmac-sha2-512-96,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96[/FONT]
[FONT=Menlo]debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-sha2-256,hmac-sha2-256-96,hmac-sha2-512,hmac-sha2-512-96,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96[/FONT]
[FONT=Menlo]debug2: kex_parse_kexinit: none,zlib@openssh.com[/FONT]
[FONT=Menlo]debug2: kex_parse_kexinit: none,zlib@openssh.com[/FONT]
[FONT=Menlo]debug2: kex_parse_kexinit: [/FONT]
[FONT=Menlo]debug2: kex_parse_kexinit: [/FONT]
[FONT=Menlo]debug2: kex_parse_kexinit: first_kex_follows 0 [/FONT]
[FONT=Menlo]debug2: kex_parse_kexinit: reserved 0 [/FONT]
[FONT=Menlo]debug2: mac_setup: found hmac-md5[/FONT]
[FONT=Menlo]debug1: kex: server->client aes128-ctr hmac-md5 none[/FONT]
[FONT=Menlo]debug2: mac_setup: found hmac-md5[/FONT]
[FONT=Menlo]debug1: kex: client->server aes128-ctr hmac-md5 none[/FONT]
[FONT=Menlo]debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent[/FONT]
[FONT=Menlo]debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP[/FONT]
[FONT=Menlo]debug2: dh_gen_key: priv key bits set: 123/256[/FONT]
[FONT=Menlo]debug2: bits set: 1027/2048[/FONT]
[FONT=Menlo]debug1: SSH2_MSG_KEX_DH_GEX_INIT sent[/FONT]
[FONT=Menlo]debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY[/FONT]
[FONT=Menlo]debug1: Server host key: DSA 94:eb:8f:ba:8c:44:d2:e2:aa:c4:1a:c2:22:a5:7f:5a[/FONT]
[FONT=Menlo]debug3: load_hostkeys: loading entries for host "192.168.1.12" from file "/Users/maths/.ssh/known_hosts"[/FONT]
[FONT=Menlo]debug3: load_hostkeys: found key type DSA in file /Users/maths/.ssh/known_hosts:1[/FONT]
[FONT=Menlo]debug3: load_hostkeys: loaded 1 keys[/FONT]
[FONT=Menlo]debug1: Host '192.168.1.12' is known and matches the DSA host key.[/FONT]
[FONT=Menlo]debug1: Found key in /Users/maths/.ssh/known_hosts:1[/FONT]
[FONT=Menlo]debug2: bits set: 1051/2048[/FONT]
[FONT=Menlo]debug1: ssh_dss_verify: signature correct[/FONT]
[FONT=Menlo]debug2: kex_derive_keys[/FONT]
[FONT=Menlo]debug2: set_newkeys: mode 1[/FONT]
[FONT=Menlo]debug1: SSH2_MSG_NEWKEYS sent[/FONT]
[FONT=Menlo]debug1: expecting SSH2_MSG_NEWKEYS[/FONT]
[FONT=Menlo]debug2: set_newkeys: mode 0[/FONT]
[FONT=Menlo]debug1: SSH2_MSG_NEWKEYS received[/FONT]
[FONT=Menlo]debug1: Roaming not allowed by server[/FONT]
[FONT=Menlo]debug1: SSH2_MSG_SERVICE_REQUEST sent[/FONT]
[FONT=Menlo]debug2: service_accept: ssh-userauth[/FONT]
[FONT=Menlo]debug1: SSH2_MSG_SERVICE_ACCEPT received[/FONT]
[FONT=Menlo]debug2: key: /Users/maths/.ssh/id_rsa (0x7fa68240b7e0),[/FONT]
[FONT=Menlo]debug2: key: /Users/maths/.ssh/id_dsa (0x0),[/FONT]
[FONT=Menlo]debug1: Authentications that can continue: publickey[/FONT]
[FONT=Menlo]debug3: start over, passed a different list publickey[/FONT]
[FONT=Menlo]debug3: preferred publickey,keyboard-interactive,password[/FONT]
[FONT=Menlo]debug3: authmethod_lookup publickey[/FONT]
[FONT=Menlo]debug3: remaining preferred: keyboard-interactive,password[/FONT]
[FONT=Menlo]debug3: authmethod_is_enabled publickey[/FONT]
[FONT=Menlo]debug1: Next authentication method: publickey[/FONT]
[FONT=Menlo]debug1: Offering RSA public key: /Users/maths/.ssh/id_rsa[/FONT]
[FONT=Menlo]debug3: send_pubkey_test[/FONT]
[FONT=Menlo]debug2: we sent a publickey packet, wait for reply[/FONT]
[FONT=Menlo]debug1: Authentications that can continue: publickey[/FONT]
[FONT=Menlo]debug1: Trying private key: /Users/maths/.ssh/id_dsa[/FONT]
[FONT=Menlo]debug3: no such identity: /Users/maths/.ssh/id_dsa: No such file or directory[/FONT]
[FONT=Menlo]debug2: we did not send a packet, disable method[/FONT]
[FONT=Menlo]debug1: No more authentication methods to try.[/FONT]
[FONT=Menlo]Permission denied (publickey).[/FONT]
```

Anyone has a idea, I disable the firewall.

In other way server => macbook no pb by ssh

Thanks you in advance

---

### Post by volkswagner on 2014-04-29
Does your public key in /Users/maths/.ssh/id_rsa.pub match on the server
/home/user/.ssh/authorized_keys?

Perhaps there is a mismatch in /Users/maths/.ssh/.know_hosts, but I suspect you'd get a different error.
You can try deleting lines pertaining to "192.168.1.12" in /Users/maths/.ssh/.known_hosts and try again.

---

### Post by benoit5 on 2014-04-29
Thanks you, indeed my public key was not the same so I change in authorized_keys and now it's work ! thank you ;)

---

