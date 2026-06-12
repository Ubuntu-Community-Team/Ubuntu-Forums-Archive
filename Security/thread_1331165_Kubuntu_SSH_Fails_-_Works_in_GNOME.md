---
title: "Kubuntu SSH Fails - Works in GNOME"
date: 2009-11-19
forum: Security
---

### Post by onyxrev on 2009-11-19
My employer has security set up via SSH public keys - no passwords.  I can sign into all of their systems just fine in Gnome but Kubuntu always returns 'Permission denied (publickey)'

Is there an agent/daemon I need to run to get Kubuntu aware of this key?  It's present in my .ssh as a file the same as my username.  They have my .pub file installed on their machines.

---

### Post by onyxrev on 2009-11-19
```
ssh -vvv foo@yadayada
OpenSSH_5.1p1 Debian-6ubuntu2, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to yadayada port 22.
debug1: Connection established.
debug1: identity file /home/foo/.ssh/identity type -1
debug1: identity file /home/foo/.ssh/id_rsa type -1
debug1: identity file /home/foo/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.1p1 Debian-5ubuntu1
debug1: match: OpenSSH_5.1p1 Debian-5ubuntu1 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.1p1 Debian-6ubuntu2
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
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
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
debug2: dh_gen_key: priv key bits set: 123/256
debug2: bits set: 510/1024
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug3: check_host_in_hostfile: filename /home/foo/.ssh/known_hosts
debug3: check_host_in_hostfile: match line 14
debug3: check_host_in_hostfile: filename /home/foo/.ssh/known_hosts
debug3: check_host_in_hostfile: match line 13
debug1: Host 'yadayada' is known and matches the RSA host key.
debug1: Found key in /home/foo/.ssh/known_hosts:14
debug2: bits set: 493/1024
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
debug2: key: /home/foo/.ssh/identity ((nil))
debug2: key: /home/foo/.ssh/id_rsa ((nil))
debug2: key: /home/foo/.ssh/id_dsa ((nil))
debug1: Authentications that can continue: publickey
debug3: start over, passed a different list publickey
debug3: preferred gssapi-keyex,gssapi-with-mic,gssapi,publickey,keyboard-interactive,password
debug3: authmethod_lookup publickey
debug3: remaining preferred: keyboard-interactive,password
debug3: authmethod_is_enabled publickey
debug1: Next authentication method: publickey
debug1: Trying private key: /home/foo/.ssh/identity
debug3: no such identity: /home/foo/.ssh/identity
debug1: Trying private key: /home/foo/.ssh/id_rsa
debug3: no such identity: /home/foo/.ssh/id_rsa
debug1: Trying private key: /home/foo/.ssh/id_dsa
debug3: no such identity: /home/foo/.ssh/id_dsa
debug2: we did not send a packet, disable method
debug1: No more authentication methods to try.
Permission denied (publickey).

```

---

### Post by onyxrev on 2009-11-19
Solution: 

ssh-add mykey

*type passphrase*
*try again*

worked!

---

### Post by Lars Noodén on 2009-11-19
> **onyxrev said:**
> Solution: 

ssh-add mykey

*type passphrase*
*try again*

worked!

Then there is a bug in how KDE was launched.  It should have been started using shh-agent like GNOME was.  It'd help others if you could [file the report](https://launchpad.net/ubuntu).  It'd very nice to have it fixed in LTS in April.

---

### Post by onyxrev on 2009-11-19
Hmmm.  Do you think it could be related to the fact that I use GDM instead of KDM to start the session?

---

### Post by onyxrev on 2009-11-19
Nope - launching with KDM has the same behavior.  I'll file a bug.

---

### Post by onyxrev on 2009-11-19
[https://bugs.launchpad.net/ubuntu/+source/kubuntu-default-settings/+bug/485403](https://bugs.launchpad.net/ubuntu/+source/kubuntu-default-settings/+bug/485403)

---

