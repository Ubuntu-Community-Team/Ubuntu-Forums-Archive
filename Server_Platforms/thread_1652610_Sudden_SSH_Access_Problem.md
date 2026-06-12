---
title: "Sudden SSH Access Problem"
date: 2010-12-25
forum: Server Platforms
---

### Post by clev on 2010-12-25
While away over the Christmas, I've lost remote access to my Ubuntu 10.04 server box. It worked previously this week, but not today.

Here's the log from my SSH client:

```

debug2: ssh_connect: needpriv 0
debug1: Connecting to abc.xyz.com [xxx.xxx.xxx.xxx] port 7219.
debug2: fd 16 setting O_NONBLOCK
debug1: fd 16 clearing O_NONBLOCK
debug1: Connection established.
debug3: timeout: 29116 ms remain after connect
debug3: Not a RSA1 key file
/var/mobile/Applications/6BB893C4-1EA0-41DB-940B-B3CD6CE2C368/Documents/keys/iphone.
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
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug2: key_type_from_name: unknown key type '-----END'
debug3: key_read: missing keytype
debug1: identity file
/var/mobile/Applications/6BB893C4-1EA0-41DB-940B-B3CD6CE2C368/Documents/keys/iphone
type 1
debug1: Remote protocol version 2.0, remote software version
OpenSSH_5.3p1 Debian-3ubuntu4
debug1: match: OpenSSH_5.3p1 Debian-3ubuntu4 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.1
debug2: fd 16 setting O_NONBLOCK
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug2: kex_parse_kexinit:
diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss
debug2: kex_parse_kexinit:
aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit:
aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit:
hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit:
hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib
debug2: kex_parse_kexinit:
debug2: kex_parse_kexinit:
debug2: kex_parse_kexinit: first_kex_follows 0
debug2: kex_parse_kexinit: reserved 0
debug2: kex_parse_kexinit:
diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss
debug2: kex_parse_kexinit:
aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit:
aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit:
hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit:
hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
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
debug2: dh_gen_key: priv key bits set: 117/256
debug2: bits set: 1010/2048
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug3: put_host_port: [xxx.xxx.xxx.xxx]:7219
debug3: put_host_port: [abc.xyz.com]:7219
debug3: check_host_in_hostfile: filename
/var/mobile/Applications/6BB893C4-1EA0-41DB-940B-B3CD6CE2C368/Documents/keys/.ssh/known_hosts
debug3: check_host_in_hostfile: match line 3
debug3: check_host_in_hostfile: filename
/var/mobile/Applications/6BB893C4-1EA0-41DB-940B-B3CD6CE2C368/Documents/keys/.ssh/known_hosts
debug3: check_host_in_hostfile: match line 3
debug1: Host '[abc.xyz.com]:7219' is known and matches the
RSA host key.
debug1: Found key in
/var/mobile/Applications/6BB893C4-1EA0-41DB-940B-B3CD6CE2C368/Documents/keys/.ssh/known_hosts:3
debug2: bits set: 1018/2048
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
debug2: key: /var/mobile/Applications/6BB893C4-1EA0-41DB-940B-B3CD6CE2C368/Documents/keys/iphone
(0x20d850)
debug1: Authentications that can continue: publickey
debug3: start over, passed a different list publickey
debug3: preferred publickey,keyboard-interactive,password
debug3: authmethod_lookup publickey
debug3: remaining preferred: keyboard-interactive,password
debug3: authmethod_is_enabled publickey
debug1: Next authentication method: publickey
debug1: Offering public key:
/var/mobile/Applications/6BB893C4-1EA0-41DB-940B-B3CD6CE2C368/Documents/keys/iphone
debug3: send_pubkey_test
debug2: we sent a publickey packet, wait for reply
debug1: Authentications that can continue: publickey
debug2: we did not send a packet, disable method
debug1: No more authentication methods to try.
debug1: Authentication succeeded (publickey).

```

Note that this is from my iphone using TouchTerm SSH client, the only computing device I have with me at the moment.

I'm confused by the "authentication suceeded" log entry, but it still doesn't seem to open a session.

The server setup is fairly standard with public key authentication enabled, and password auth disabled.

The server (and client) setup has not been touched since it was last working. The only things that could have changed are those out of my control, i.e. power interrupt and reboot, router messing up somehow, etc. But I can't make the link between these potential events and the above log, and lack of access.

Any ideas gratefully appreciated?

C

---

### Post by aceofspades686 on 2010-12-25
I'm not an expert, but this line:

```

debug3: Not a RSA1 key file
/var/mobile/Applications/6BB893C4-1EA0-41DB-940B-B3CD6CE2C368/Documents/keys/iphone.

```

Seems to indicate to me a problem with the ssh key stored on your phone.

---

### Post by clev on 2010-12-26
Thanks for the suggestion aceofspades. Accessing a test server from the phone using the same key works, so its safe to assume the problem is server side.

Additionally, I've found TouchTerm ssh on the iPhone confusingly seems to generate a debug message "Authentication succeeded (publickey)" even when authentication was *not* successful. Copying the key pair from phone to a PC (OpenSSH client), and attempting access resulting in a very similar set of debug messages except it ended in "Permission denied (publickey)".

So it looks like the server has just stopped accepting my keys for some reason. I guess I'll find out what's broken when I get (physical) access to the box.

Cheers for the suggestion.

---

### Post by HermanAB on 2010-12-26
To see what is going on during login:
$ ssh -vvv user@server

---

### Post by karesmakro on 2010-12-26
> debug2: key_type_from_name: unknown key type '-----BEGIN'

Are you sure, you are using the right key for authentication?
This no ssh server related problem.

Make sure, taking the right key and try again!

---

