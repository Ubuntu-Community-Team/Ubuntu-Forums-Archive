---
title: "Unable to connect to a localhost Ubuntu server with OSX"
date: 2017-10-28
forum: Server Platforms
---

### Post by rdkings on 2017-10-28
Hey guys and gals,

I am novice Linux user trying to set up a ssh server to my laptop, so I can program my server easier. I got it running once, but when I rebooted my Ubuntu was unable to reboot, mind you I wrote the partition on a USB drive. Here's what I'm getting kicked back from the server 

```
~ rdkingsland$ ssh -vvv rdkingsland@10.0.0.102
OpenSSH_7.4p1, LibreSSL 2.5.0
debug1: Reading configuration data /etc/ssh/ssh_config
debug2: resolving "10.0.0.102" port 22
debug2: ssh_connect_direct: needpriv 0
debug1: Connecting to 10.0.0.102 [10.0.0.102] port 22.
debug1: Connection established.
debug1: identity file /Users/rdkingsland/.ssh/id_rsa type 1
debug1: key_load_public: No such file or directory
debug1: identity file /Users/rdkingsland/.ssh/id_rsa-cert type -1
debug1: identity file /Users/rdkingsland/.ssh/id_dsa type 2
debug1: key_load_public: No such file or directory
debug1: identity file /Users/rdkingsland/.ssh/id_dsa-cert type -1
debug1: key_load_public: No such file or directory
debug1: identity file /Users/rdkingsland/.ssh/id_ecdsa type -1
debug1: key_load_public: No such file or directory
debug1: identity file /Users/rdkingsland/.ssh/id_ecdsa-cert type -1
debug1: key_load_public: No such file or directory
debug1: identity file /Users/rdkingsland/.ssh/id_ed25519 type -1
debug1: key_load_public: No such file or directory
debug1: identity file /Users/rdkingsland/.ssh/id_ed25519-cert type -1
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_7.4
debug1: Remote protocol version 2.0, remote software version OpenSSH_7.2p2 Ubuntu-4ubuntu2.2
debug1: match: OpenSSH_7.2p2 Ubuntu-4ubuntu2.2 pat OpenSSH* compat 0x04000000
debug2: fd 3 setting O_NONBLOCK
debug1: Authenticating to 10.0.0.102:22 as 'rdkingsland'
debug3: hostkeys_foreach: reading file "/Users/rdkingsland/.ssh/known_hosts"
debug3: record_hostkey: found key type ECDSA in file /Users/rdkingsland/.ssh/known_hosts:1
debug3: load_hostkeys: loaded 1 keys from 10.0.0.102
debug3: order_hostkeyalgs: prefer hostkeyalgs: [email]ecdsa-sha2-nistp256-cert-v01@openssh.com,ecdsa-sha2-nistp384-cert-v01@openssh.com,ecdsa-sha2-nistp521-cert-v01@openssh.com[/email],ecdsa-sha2-nistp256,ecdsa-sha2-nistp384,ecdsa-sha2-nistp521
debug3: send packet: type 20
debug1: SSH2_MSG_KEXINIT sent
debug3: receive packet: type 20
debug1: SSH2_MSG_KEXINIT received
debug2: local client KEXINIT proposal
debug2: KEX algorithms: curve25519-sha256,curve25519-sha256@libssh.org,ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group16-sha512,diffie-hellman-group18-sha512,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha256,diffie-hellman-group14-sha1,ext-info-c
debug2: host key algorithms: [email]ecdsa-sha2-nistp256-cert-v01@openssh.com,ecdsa-sha2-nistp384-cert-v01@openssh.com,ecdsa-sha2-nistp521-cert-v01@openssh.com,ecdsa-sha2-nistp256,ecdsa-sha2-nistp384,ecdsa-sha2-nistp521,ssh-ed25519-cert-v01@openssh.com,ssh-rsa-cert-v01@openssh.com[/email],ssh-ed25519,rsa-sha2-512,rsa-sha2-256,ssh-rsa
debug2: ciphers ctos: [email]chacha20-poly1305@openssh.com,aes128-ctr,aes192-ctr,aes256-ctr,aes128-gcm@openssh.com,aes256-gcm@openssh.com[/email],aes128-cbc,aes192-cbc,aes256-cbc
debug2: ciphers stoc: [email]chacha20-poly1305@openssh.com,aes128-ctr,aes192-ctr,aes256-ctr,aes128-gcm@openssh.com,aes256-gcm@openssh.com[/email],aes128-cbc,aes192-cbc,aes256-cbc
debug2: MACs ctos: [email]umac-64-etm@openssh.com,umac-128-etm@openssh.com,hmac-sha2-256-etm@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-sha1-etm@openssh.com,umac-64@openssh.com,umac-128@openssh.com[/email],hmac-sha2-256,hmac-sha2-512,hmac-sha1
debug2: MACs stoc: [email]umac-64-etm@openssh.com,umac-128-etm@openssh.com,hmac-sha2-256-etm@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-sha1-etm@openssh.com,umac-64@openssh.com,umac-128@openssh.com[/email],hmac-sha2-256,hmac-sha2-512,hmac-sha1
debug2: compression ctos: none,zlib@openssh.com,zlib
debug2: compression stoc: none,zlib@openssh.com,zlib
debug2: languages ctos: 
debug2: languages stoc: 
debug2: first_kex_follows 0 
debug2: reserved 0 
debug2: peer server KEXINIT proposal
debug2: KEX algorithms: [email]curve25519-sha256@libssh.org[/email],ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group14-sha1
debug2: host key algorithms: ssh-rsa,rsa-sha2-512,rsa-sha2-256,ecdsa-sha2-nistp256,ssh-ed25519
debug2: ciphers ctos: [email]chacha20-poly1305@openssh.com,aes128-ctr,aes192-ctr,aes256-ctr,aes128-gcm@openssh.com,aes256-gcm@openssh.com[/email]
debug2: ciphers stoc: [email]chacha20-poly1305@openssh.com,aes128-ctr,aes192-ctr,aes256-ctr,aes128-gcm@openssh.com,aes256-gcm@openssh.com[/email]
debug2: MACs ctos: [email]umac-64-etm@openssh.com,umac-128-etm@openssh.com,hmac-sha2-256-etm@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-sha1-etm@openssh.com,umac-64@openssh.com,umac-128@openssh.com[/email],hmac-sha2-256,hmac-sha2-512,hmac-sha1
debug2: MACs stoc: [email]umac-64-etm@openssh.com,umac-128-etm@openssh.com,hmac-sha2-256-etm@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-sha1-etm@openssh.com,umac-64@openssh.com,umac-128@openssh.com[/email],hmac-sha2-256,hmac-sha2-512,hmac-sha1
debug2: compression ctos: none,zlib@openssh.com
debug2: compression stoc: none,zlib@openssh.com
debug2: languages ctos: 
debug2: languages stoc: 
debug2: first_kex_follows 0 
debug2: reserved 0 
debug1: kex: algorithm: [email]curve25519-sha256@libssh.org[/email]
debug1: kex: host key algorithm: ecdsa-sha2-nistp256
debug1: kex: server->client cipher: [email]chacha20-poly1305@openssh.com[/email] MAC: <implicit> compression: none
debug1: kex: client->server cipher: [email]chacha20-poly1305@openssh.com[/email] MAC: <implicit> compression: none
debug3: send packet: type 30
debug1: expecting SSH2_MSG_KEX_ECDH_REPLY
debug3: receive packet: type 31
debug1: Server host key: ecdsa-sha2-nistp256 SHA256:sWzwF/7la+I047Lum+4C0Gk8Uq29M3kKUvJpW4WUCYA
debug3: hostkeys_foreach: reading file "/Users/rdkingsland/.ssh/known_hosts"
debug3: record_hostkey: found key type ECDSA in file /Users/rdkingsland/.ssh/known_hosts:1
debug3: load_hostkeys: loaded 1 keys from 10.0.0.102
debug1: Host '10.0.0.102' is known and matches the ECDSA host key.
debug1: Found key in /Users/rdkingsland/.ssh/known_hosts:1
debug3: send packet: type 21
debug2: set_newkeys: mode 1
debug1: rekey after 134217728 blocks
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug3: receive packet: type 21
debug1: SSH2_MSG_NEWKEYS received
debug2: set_newkeys: mode 0
debug1: rekey after 134217728 blocks
debug2: key: /Users/rdkingsland/.ssh/id_rsa (0x7fa964e056c0)
debug1: Skipping ssh-dss key /Users/rdkingsland/.ssh/id_dsa - not in PubkeyAcceptedKeyTypes
debug2: key: /Users/rdkingsland/.ssh/id_ecdsa (0x0)
debug2: key: /Users/rdkingsland/.ssh/id_ed25519 (0x0)
debug3: send packet: type 5
debug3: receive packet: type 7
debug1: SSH2_MSG_EXT_INFO received
debug1: kex_input_ext_info: server-sig-algs=<rsa-sha2-256,rsa-sha2-512>
debug3: receive packet: type 6
debug2: service_accept: ssh-userauth
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug3: send packet: type 50
debug3: receive packet: type 51
debug1: Authentications that can continue: publickey,password
debug3: start over, passed a different list publickey,password
debug3: preferred publickey,keyboard-interactive,password
debug3: authmethod_lookup publickey
debug3: remaining preferred: keyboard-interactive,password
debug3: authmethod_is_enabled publickey
debug1: Next authentication method: publickey
debug1: Offering RSA public key: /Users/rdkingsland/.ssh/id_rsa
debug3: send_pubkey_test
debug3: send packet: type 50
debug2: we sent a publickey packet, wait for reply
debug3: receive packet: type 51
debug1: Authentications that can continue: publickey,password
debug1: Trying private key: /Users/rdkingsland/.ssh/id_ecdsa
debug3: no such identity: /Users/rdkingsland/.ssh/id_ecdsa: No such file or directory
debug1: Trying private key: /Users/rdkingsland/.ssh/id_ed25519
debug3: no such identity: /Users/rdkingsland/.ssh/id_ed25519: No such file or directory
debug2: we did not send a packet, disable method
debug3: authmethod_lookup password
debug3: remaining preferred: ,password
debug3: authmethod_is_enabled password
debug1: Next authentication method: password
``` 
Could anyone shed light on whats going wrong? I have a id_rsa.pub key in my /ssh/authorized_keys that I extracted and uploaded to my server. Again, any help would be appreciated.

---

### Post by wildmanne39 on 2017-10-28
*Thread moved to **Server Platforms for better a better fit **.*

Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by darkod on 2017-10-29
I'm confused.

1. You say you are setting up ssh server on your laptop to control your server? The ssh server needs to be on the server only, the laptop will use ssh client to connect, not server. And if I'm not mistaken OSX supports ssh by default so you don't need to install anything on it to open ssh sessions.

2. According to that ssh output, there is no local key it can find and use on the client, so it can only try connecting to the server using password authentication. If you planned to use keys, double check where is your key located and how you have it declared suring opening the session (it needs to know where to find it).

---

