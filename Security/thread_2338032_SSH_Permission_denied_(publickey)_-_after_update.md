---
title: "SSH: Permission denied (publickey) - after update"
date: 2016-09-23
forum: Security
---

### Post by coryc on 2016-09-23
Issue: Permission denied (publickey)
[LIST]
[*]Client Ubuntu 16.04 on VirtualBox | Server Ubuntu 16.04
[*]Worked fine before installing updates on client, and VirtualBox
[*]Still able to connect to server with Putty (Win8) using same key
[/LIST]

Thanks in advance for any help you can provide.


ssh permissions
```

drwx------  2 cory cory 4096 Sep 23 20:37 .ssh
-rw-------  1 cory cory 1766 Aug 20 15:30 .ssh/id_rsa
-rw-------  1 cory cory  402 Aug 20 15:30 .ssh/id_rsa.pub
-rw-------  1 cory cory 1332 Sep 23 20:35 .ssh/known_hosts

```

server permissions
```

drwx------ 2 user user  4096 Sep 22 20:57 .ssh
-rw------- 1 user user  798 Sep 22 20:59 authorized_keys

```

ssh -vvv output
```

OpenSSH_7.2p2 Ubuntu-4ubuntu2.1, OpenSSL 1.0.2g  1 Mar 2016
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug2: resolving "server" port 22
debug2: ssh_connect_direct: needpriv 0
debug1: Connecting to server [192.168.x.x] port 22.
debug1: Connection established.
debug1: identity file /home/cory/.ssh/id_rsa type 1
debug1: key_load_public: No such file or directory
debug1: identity file /home/cory/.ssh/id_rsa-cert type -1
debug1: key_load_public: No such file or directory
debug1: identity file /home/cory/.ssh/id_dsa type -1
debug1: key_load_public: No such file or directory
debug1: identity file /home/cory/.ssh/id_dsa-cert type -1
debug1: key_load_public: No such file or directory
debug1: identity file /home/cory/.ssh/id_ecdsa type -1
debug1: key_load_public: No such file or directory
debug1: identity file /home/cory/.ssh/id_ecdsa-cert type -1
debug1: key_load_public: No such file or directory
debug1: identity file /home/cory/.ssh/id_ed25519 type -1
debug1: key_load_public: No such file or directory
debug1: identity file /home/cory/.ssh/id_ed25519-cert type -1
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_7.2p2 Ubuntu-4ubuntu2.1
debug1: Remote protocol version 2.0, remote software version OpenSSH_7.2p2 Ubuntu-4ubuntu2.1
debug1: match: OpenSSH_7.2p2 Ubuntu-4ubuntu2.1 pat OpenSSH* compat 0x04000000
debug2: fd 3 setting O_NONBLOCK
debug1: Authenticating to server:22 as 'user'
debug3: hostkeys_foreach: reading file "/home/cory/.ssh/known_hosts"
debug3: record_hostkey: found key type ECDSA in file /home/cory/.ssh/known_hosts:5
debug3: load_hostkeys: loaded 1 keys from server
debug3: order_hostkeyalgs: prefer hostkeyalgs: ecdsa-sha2-nistp256-cert-v01@openssh.com,ecdsa-sha2-nistp384-cert-v01@openssh.com,ecdsa-sha2-nistp521-cert-v01@openssh.com,ecdsa-sha2-nistp256,ecdsa-sha2-nistp384,ecdsa-sha2-nistp521
debug3: send packet: type 20
debug1: SSH2_MSG_KEXINIT sent
debug3: receive packet: type 20
debug1: SSH2_MSG_KEXINIT received
debug2: local client KEXINIT proposal
debug2: KEX algorithms: curve25519-sha256@libssh.org,ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,ext-info-c
debug2: host key algorithms: ecdsa-sha2-nistp256-cert-v01@openssh.com,ecdsa-sha2-nistp384-cert-v01@openssh.com,ecdsa-sha2-nistp521-cert-v01@openssh.com,ecdsa-sha2-nistp256,ecdsa-sha2-nistp384,ecdsa-sha2-nistp521,ssh-ed25519-cert-v01@openssh.com,ssh-rsa-cert-v01@openssh.com,ssh-ed25519,rsa-sha2-512,rsa-sha2-256,ssh-rsa
debug2: ciphers ctos: chacha20-poly1305@openssh.com,aes128-ctr,aes192-ctr,aes256-ctr,aes128-gcm@openssh.com,aes256-gcm@openssh.com,aes128-cbc,aes192-cbc,aes256-cbc,3des-cbc
debug2: ciphers stoc: chacha20-poly1305@openssh.com,aes128-ctr,aes192-ctr,aes256-ctr,aes128-gcm@openssh.com,aes256-gcm@openssh.com,aes128-cbc,aes192-cbc,aes256-cbc,3des-cbc
debug2: MACs ctos: umac-64-etm@openssh.com,umac-128-etm@openssh.com,hmac-sha2-256-etm@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-sha1-etm@openssh.com,umac-64@openssh.com,umac-128@openssh.com,hmac-sha2-256,hmac-sha2-512,hmac-sha1
debug2: MACs stoc: umac-64-etm@openssh.com,umac-128-etm@openssh.com,hmac-sha2-256-etm@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-sha1-etm@openssh.com,umac-64@openssh.com,umac-128@openssh.com,hmac-sha2-256,hmac-sha2-512,hmac-sha1
debug2: compression ctos: none,zlib@openssh.com,zlib
debug2: compression stoc: none,zlib@openssh.com,zlib
debug2: languages ctos: 
debug2: languages stoc: 
debug2: first_kex_follows 0 
debug2: reserved 0 
debug2: peer server KEXINIT proposal
debug2: KEX algorithms: curve25519-sha256@libssh.org,ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group14-sha1
debug2: host key algorithms: ssh-rsa,rsa-sha2-512,rsa-sha2-256,ecdsa-sha2-nistp256,ssh-ed25519
debug2: ciphers ctos: chacha20-poly1305@openssh.com,aes128-ctr,aes192-ctr,aes256-ctr,aes128-gcm@openssh.com,aes256-gcm@openssh.com
debug2: ciphers stoc: chacha20-poly1305@openssh.com,aes128-ctr,aes192-ctr,aes256-ctr,aes128-gcm@openssh.com,aes256-gcm@openssh.com
debug2: MACs ctos: umac-64-etm@openssh.com,umac-128-etm@openssh.com,hmac-sha2-256-etm@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-sha1-etm@openssh.com,umac-64@openssh.com,umac-128@openssh.com,hmac-sha2-256,hmac-sha2-512,hmac-sha1
debug2: MACs stoc: umac-64-etm@openssh.com,umac-128-etm@openssh.com,hmac-sha2-256-etm@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-sha1-etm@openssh.com,umac-64@openssh.com,umac-128@openssh.com,hmac-sha2-256,hmac-sha2-512,hmac-sha1
debug2: compression ctos: none,zlib@openssh.com
debug2: compression stoc: none,zlib@openssh.com
debug2: languages ctos: 
debug2: languages stoc: 
debug2: first_kex_follows 0 
debug2: reserved 0 
debug1: kex: algorithm: curve25519-sha256@libssh.org
debug1: kex: host key algorithm: ecdsa-sha2-nistp256
debug1: kex: server->client cipher: chacha20-poly1305@openssh.com MAC: <implicit> compression: none
debug1: kex: client->server cipher: chacha20-poly1305@openssh.com MAC: <implicit> compression: none
debug3: send packet: type 30
debug1: expecting SSH2_MSG_KEX_ECDH_REPLY
debug3: receive packet: type 31
debug1: Server host key: ecdsa-sha2-nistp256 SHA256:3uquOuzXcti2gQ184zV/ZhpPsBohdxluqYjgdho+iGA
debug3: hostkeys_foreach: reading file "/home/cory/.ssh/known_hosts"
debug3: record_hostkey: found key type ECDSA in file /home/cory/.ssh/known_hosts:5
debug3: load_hostkeys: loaded 1 keys from server
debug3: hostkeys_foreach: reading file "/home/cory/.ssh/known_hosts"
debug3: record_hostkey: found key type ECDSA in file /home/cory/.ssh/known_hosts:6
debug3: load_hostkeys: loaded 1 keys from 192.168.x.x
debug1: Host 'server' is known and matches the ECDSA host key.
debug1: Found key in /home/cory/.ssh/known_hosts:5
debug3: send packet: type 21
debug2: set_newkeys: mode 1
debug1: rekey after 134217728 blocks
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug3: receive packet: type 21
debug2: set_newkeys: mode 0
debug1: rekey after 134217728 blocks
debug1: SSH2_MSG_NEWKEYS received
debug2: key: /home/cory/.ssh/id_rsa (0x810d9e30), agent
debug2: key: /home/cory/.ssh/id_dsa ((nil))
debug2: key: /home/cory/.ssh/id_ecdsa ((nil))
debug2: key: /home/cory/.ssh/id_ed25519 ((nil))
debug3: send packet: type 5
debug3: receive packet: type 7
debug1: SSH2_MSG_EXT_INFO received
debug1: kex_input_ext_info: server-sig-algs=<rsa-sha2-256,rsa-sha2-512>
debug3: receive packet: type 6
debug2: service_accept: ssh-userauth
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug3: send packet: type 50
debug3: receive packet: type 51
debug1: Authentications that can continue: publickey
debug3: start over, passed a different list publickey
debug3: preferred gssapi-keyex,gssapi-with-mic,publickey,keyboard-interactive,password
debug3: authmethod_lookup publickey
debug3: remaining preferred: keyboard-interactive,password
debug3: authmethod_is_enabled publickey
debug1: Next authentication method: publickey
debug1: Offering RSA public key: /home/cory/.ssh/id_rsa
debug3: send_pubkey_test
debug3: send packet: type 50
debug2: we sent a publickey packet, wait for reply
debug3: receive packet: type 51
debug1: Authentications that can continue: publickey
debug1: Trying private key: /home/cory/.ssh/id_dsa
debug3: no such identity: /home/cory/.ssh/id_dsa: No such file or directory
debug1: Trying private key: /home/cory/.ssh/id_ecdsa
debug3: no such identity: /home/cory/.ssh/id_ecdsa: No such file or directory
debug1: Trying private key: /home/cory/.ssh/id_ed25519
debug3: no such identity: /home/cory/.ssh/id_ed25519: No such file or directory
debug2: we did not send a packet, disable method
debug1: No more authentication methods to try.
Permission denied (publickey).



```


server auth.log
```

Sep 23 19:41:29 server sshd[30283]: Connection from 192.168.0.215 port 63536 on 192.168.x.x port 22
Sep 23 19:41:29 server sshd[30283]: Failed publickey for user from 192.168.0.215 port 63536 ssh2: RSA SHA256:FuFBtfBJCoEjWzyGsYHLSl7n7notVtVxjTI51bIYvxU
Sep 23 19:41:29 server sshd[30283]: Connection closed by 192.168.0.215 port 63536 [preauth]



```

---

### Post by DuckHook on 2016-09-23
I'm no ssh expert so can be of only limited help, but perhaps the update replaced your customized config files in /etc/ssh/ with generic ones? You may want to check them again to see if they are pointing to the right key directories (for example).

---

### Post by DuckHook on 2016-09-23
> **coryc said:**
> ```
debug1: Trying private key: /home/cory/.ssh/i[COLOR="#FF0000"]d[/COLOR]_dsa
debug3: no such identity: /home/cory/.ssh/id_[COLOR="#FF0000"]d[/COLOR]sa: [COLOR="#FF0000"]No such file or directory[/COLOR]
debug1: Trying private key: /home/cory/.ssh/id_ec[COLOR="#FF0000"]d[/COLOR]sa
debug3: no such identity: /home/cory/.ssh/id_ec[COLOR="#FF0000"]d[/COLOR]sa: [COLOR="#FF0000"]No such file or directory[/COLOR]
debug1: Trying private key: /home/cory/.ssh/id_ed25519
debug3: no such identity: /home/cory/.ssh/id_ed25519: [COLOR="#FF0000"]No such file or directory[/COLOR]

```

I also call your attention to the above errors. Any time the "No such..." error shows up, it's usually a good clue as to where to look. A typo in some config file? To my knowledge, the "d" should be "r".

---

### Post by SeijiSensei on 2016-09-24
> drwx------ 2 user user  4096 Sep 22 20:57 .ssh
-rw------- 1 user user  798 Sep 22 20:59 authorized_keys
From the looks of that, authorized_keys resides in the directory above .ssh.  It needs to be in the .ssh directory.

---

### Post by coryc on 2016-09-24
I got it working by creating a new key and manually copying it to the server.  I also removed my old entry from authorized_keys.  I then had to use ssh-add on the client.  I still don't know why it happened, but glad to have it fixed.

---

