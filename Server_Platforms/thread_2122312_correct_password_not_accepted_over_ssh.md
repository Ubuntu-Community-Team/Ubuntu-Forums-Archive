---
title: "correct password not accepted over ssh"
date: 2013-03-04
forum: Server Platforms
---

### Post by wlraider70 on 2013-03-04
I'm trying to ssh in which I've done many times now the pw is not being excepted.

The password works at the box.  I think the problem started when I was using a two factor with Pam. Even with just password it still fails.

---

### Post by kevdog on 2013-03-04
Its probably something to do with your sshd_config file.  Did you mess something up?

What happens when you try to connect with the -vvv option on the client?

---

### Post by wlraider70 on 2013-03-04
I very well may have messed up the config. However, I did successfully log on with the pam settings. numerous times. 
I also recall that I had several failed log in attempts then success. At the time I thought it was me. Maybe it wasn't


hers the -vvv

```

debug1: Connecting to 10.10.11.2 [10.10.11.2] port 2222.
debug1: Connection established.
debug1: identity file /home/WCA/.ssh/id_rsa type -1
debug1: identity file /home/WCA/.ssh/id_rsa-cert type -1
debug1: identity file /home/WCA/.ssh/id_dsa type -1
debug1: identity file /home/WCA/.ssh/id_dsa-cert type -1
debug1: identity file /home/WCA/.ssh/id_ecdsa type -1
debug1: identity file /home/WCA/.ssh/id_ecdsa-cert type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.3p1 Debian-3ubuntu7
debug1: match: OpenSSH_5.3p1 Debian-3ubuntu7 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.9
debug2: fd 3 setting O_NONBLOCK
debug3: put_host_port: [10.10.11.2]:2222
debug3: load_hostkeys: loading entries for host "[10.10.11.2]:2222" from file "/home/WCA/.ssh/known_hosts"
debug3: load_hostkeys: found key type RSA in file /home/WCA/.ssh/known_hosts:4
debug3: load_hostkeys: loaded 1 keys
debug3: order_hostkeyalgs: prefer hostkeyalgs: ssh-rsa-cert-v01@openssh.com,ssh-rsa-cert-v00@openssh.com,ssh-rsa
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug2: kex_parse_kexinit: ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa-cert-v01@openssh.com,ssh-rsa-cert-v00@openssh.com,ssh-rsa,ecdsa-sha2-nistp256-cert-v01@openssh.com,ecdsa-sha2-nistp384-cert-v01@openssh.com,ecdsa-sha2-nistp521-cert-v01@openssh.com,ssh-dss-cert-v01@openssh.com,ssh-dss-cert-v00@openssh.com,ecdsa-sha2-nistp256,ecdsa-sha2-nistp384,ecdsa-sha2-nistp521,ssh-dss
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-sha2-256,hmac-sha2-256-96,hmac-sha2-512,hmac-sha2-512-96,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-sha2-256,hmac-sha2-256-96,hmac-sha2-512,hmac-sha2-512-96,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib
debug2: kex_parse_kexinit:
debug2: kex_parse_kexinit:
debug2: kex_parse_kexinit: first_kex_follows 0
debug2: kex_parse_kexinit: reserved 0
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib@openssh.com
debug2: kex_parse_kexinit: none,zlib@openssh.com
debug2: kex_parse_kexinit:
debug2: kex_parse_kexinit:
debug2: kex_parse_kexinit: first_kex_follows 0
debug2: kex_parse_kexinit: reserved 0
debug2: mac_setup: found hmac-md5
debug1: kex: server->client aes128-ctr hmac-md5 none
debug2: mac_setup: found hmac-md5
debug1: kex: client->server aes128-ctr hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug2: dh_gen_key: priv key bits set: 110/256
debug2: bits set: 511/1024
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Server host key: RSA c7:39:9b:17:ec:2d:75:88:6f:58:29:dd:ac:80:ea:76
debug3: put_host_port: [10.10.11.2]:2222
debug3: put_host_port: [10.10.11.2]:2222
debug3: load_hostkeys: loading entries for host "[10.10.11.2]:2222" from file "/home/WCA/.ssh/known_hosts"
debug3: load_hostkeys: found key type RSA in file /home/WCA/.ssh/known_hosts:4
debug3: load_hostkeys: loaded 1 keys
debug3: load_hostkeys: loading entries for host "[10.10.11.2]:2222" from file "/home/WCA/.ssh/known_hosts"
debug3: load_hostkeys: found key type RSA in file /home/WCA/.ssh/known_hosts:4
debug3: load_hostkeys: loaded 1 keys
debug1: Host '[10.10.11.2]:2222' is known and matches the RSA host key.
debug1: Found key in /home/WCA/.ssh/known_hosts:4
debug2: bits set: 498/1024
debug1: ssh_rsa_verify: signature correct
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
debug2: key: /home/WCA/.ssh/id_rsa (0x0)
debug2: key: /home/WCA/.ssh/id_dsa (0x0)
debug2: key: /home/WCA/.ssh/id_ecdsa (0x0)
debug1: Authentications that can continue: password
debug3: start over, passed a different list password
debug3: preferred publickey,keyboard-interactive,password
debug3: authmethod_lookup password
debug3: remaining preferred: ,keyboard-interactive,password
debug3: authmethod_is_enabled password
debug1: Next authentication method: password
server@10.10.11.2's password:
debug3: packet_send2: adding 64 (len 60 padlen 4 extra_pad 64)
debug2: we sent a password packet, wait for reply
debug1: Authentications that can continue: password
Permission denied, please try again.
server@10.10.11.2's password:
debug3: packet_send2: adding 64 (len 60 padlen 4 extra_pad 64)
debug2: we sent a password packet, wait for reply
debug1: Authentications that can continue: password
Permission denied, please try again.
server@10.10.11.2's password:
debug3: packet_send2: adding 64 (len 60 padlen 4 extra_pad 64)
debug2: we sent a password packet, wait for reply
debug1: Authentications that can continue: password
debug2: we did not send a packet, disable method
debug1: No more authentication methods to try.
Permission denied (password).



```

---

### Post by kevdog on 2013-03-05
Doesn't seem like its accepting the password. The output doesn't suggest its a PAM problem rather an ssh authentication problem

---

### Post by wlraider70 on 2013-03-07
I ended up saying no to plaintext, yes to pam, yes to challenge authentication.
It seems to be working now. 
I out the pam code in then the user password.

---

