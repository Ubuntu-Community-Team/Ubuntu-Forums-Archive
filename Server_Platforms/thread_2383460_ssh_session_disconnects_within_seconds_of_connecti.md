---
title: "ssh session disconnects within seconds of connecting, if it connects"
date: 2018-01-25
forum: Server Platforms
---

### Post by NotQuiteSU on 2018-01-25
I set up a new Ubuntu 16.04.3 LTS server host on an older optiplex.  After doing some set up  and ids, (nothing that should impact SSH), I rebooted and changed the IP reservation on my DHCP server. It is currently pinging consistently with no issues.

Everytime I use putty to connect, it either hangs, or as soon as it connects and I put my password in, I'll get disconnected either after a couple seconds or a command or 2. (eg - view /var/log/syslog) or even hitting enter a few times. Most times, my connection doesn't even succeed.

It's not rebooting or a connectivity issue, as I have pings working, It's not putty since I tried from another ubuntu server and had hangs as well.  It doesn't disconnect, but has long intervals of being frozen. While I would prefer not to rebuild, I would if needed. But I'd love to be able to troubleshoot this

---

### Post by wildmanne39 on 2018-01-25
*Thread moved to **Server Platforms, a more appropriate forum**.*

---

### Post by darkod on 2018-01-25
I don't like the fact that you "changed IP reservation". Depending of the local network, devices might actually remain confused after an IP change. And it will also remain a mistery if your router is to blame here too. Can you guarantee how it handles reservation changes???

1. Server should have static IP outside of any dhcp range. Period.
2. Decide on an IP before you install the server, and stick to it. Period.

Having said that, changing the IP should be OK after a while even if there are some remains and conflicts initially.

Are you sure there isn't another device using the same IP?

SSH is designed to be very safe protocol and basically anything it considers even little suspicious, any inconsistency, it will kick you out... :)

Try connecting again from any linux machine, and raise the verbocity to have more data (not sure how many Vs are enough). Something like:
```
ssh -vvv user@host
```

Not sure if you can do some similar logging from putty, maybe yes but never needed to look for it. More verbocity will give you more info what is going on...

---

### Post by NotQuiteSU on 2018-01-25
The reservation is outside the DHCP scope. No worries there. And it seems connectivity is working fine.
When building the new system, i copied over the .ssh contents, but I don't see how that would impact things, so it should impact outgoing connections.

```

adminaccount@mars:~$ ssh -vvv adminaccount@192.168.5.21
OpenSSH_7.2p2 Ubuntu-4ubuntu2.4, OpenSSL 1.0.2g  1 Mar 2016
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug2: resolving "192.168.5.21" port 22
debug2: ssh_connect_direct: needpriv 0
debug1: Connecting to 192.168.5.21 [192.168.5.21] port 22.
debug1: connect to address 192.168.5.21 port 22: Connection timed out
ssh: connect to host 192.168.5.21 port 22: Connection timed out
adminaccount@mars:~$ ssh -vvv adminaccount@192.168.5.21
OpenSSH_7.2p2 Ubuntu-4ubuntu2.4, OpenSSL 1.0.2g  1 Mar 2016
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug2: resolving "192.168.5.21" port 22
debug2: ssh_connect_direct: needpriv 0
debug1: Connecting to 192.168.5.21 [192.168.5.21] port 22.
debug1: Connection established.
debug1: key_load_public: No such file or directory
debug1: identity file /home/adminaccount/.ssh/id_rsa type -1
debug1: key_load_public: No such file or directory
debug1: identity file /home/adminaccount/.ssh/id_rsa-cert type -1
debug1: key_load_public: No such file or directory
debug1: identity file /home/adminaccount/.ssh/id_dsa type -1
debug1: key_load_public: No such file or directory
debug1: identity file /home/adminaccount/.ssh/id_dsa-cert type -1
debug1: key_load_public: No such file or directory
debug1: identity file /home/adminaccount/.ssh/id_ecdsa type -1
debug1: key_load_public: No such file or directory
debug1: identity file /home/adminaccount/.ssh/id_ecdsa-cert type -1
debug1: key_load_public: No such file or directory
debug1: identity file /home/adminaccount/.ssh/id_ed25519 type -1
debug1: key_load_public: No such file or directory
debug1: identity file /home/adminaccount/.ssh/id_ed25519-cert type -1
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_7.2p2 Ubuntu-4ubuntu2.4
debug1: Remote protocol version 2.0, remote software version OpenSSH_7.2p2 Ubuntu-4ubuntu2.4
debug1: match: OpenSSH_7.2p2 Ubuntu-4ubuntu2.4 pat OpenSSH* compat 0x04000000
debug2: fd 3 setting O_NONBLOCK
debug1: Authenticating to 192.168.5.21:22 as 'adminaccount'
debug3: hostkeys_foreach: reading file "/home/adminaccount/.ssh/known_hosts"
debug3: record_hostkey: found key type ECDSA in file /home/adminaccount/.ssh/known_hosts:1
debug3: load_hostkeys: loaded 1 keys from 192.168.5.21
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
debug1: Server host key: ecdsa-sha2-nistp256 SHA256:o/CbAt6hvjJPVqEAMZXfz8KJZth0gbT3XL/6BUTTtJ8
debug3: hostkeys_foreach: reading file "/home/adminaccount/.ssh/known_hosts"
debug3: record_hostkey: found key type ECDSA in file /home/adminaccount/.ssh/known_hosts:1
debug3: load_hostkeys: loaded 1 keys from 192.168.5.21
debug1: Host '192.168.5.21' is known and matches the ECDSA host key.
debug1: Found key in /home/adminaccount/.ssh/known_hosts:1
debug3: send packet: type 21
debug2: set_newkeys: mode 1
debug1: rekey after 134217728 blocks
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug3: receive packet: type 21
debug2: set_newkeys: mode 0
debug1: rekey after 134217728 blocks
debug1: SSH2_MSG_NEWKEYS received
debug2: key: /home/adminaccount/.ssh/id_rsa ((nil))
debug2: key: /home/adminaccount/.ssh/id_dsa ((nil))
debug2: key: /home/adminaccount/.ssh/id_ecdsa ((nil))
debug2: key: /home/adminaccount/.ssh/id_ed25519 ((nil))
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
debug3: preferred gssapi-keyex,gssapi-with-mic,publickey,keyboard-interactive,password
debug3: authmethod_lookup publickey
debug3: remaining preferred: keyboard-interactive,password
debug3: authmethod_is_enabled publickey
debug1: Next authentication method: publickey
debug1: Trying private key: /home/adminaccount/.ssh/id_rsa
debug3: no such identity: /home/adminaccount/.ssh/id_rsa: No such file or directory
debug1: Trying private key: /home/adminaccount/.ssh/id_dsa
debug3: no such identity: /home/adminaccount/.ssh/id_dsa: No such file or directory
debug1: Trying private key: /home/adminaccount/.ssh/id_ecdsa
debug3: no such identity: /home/adminaccount/.ssh/id_ecdsa: No such file or directory
debug1: Trying private key: /home/adminaccount/.ssh/id_ed25519
debug3: no such identity: /home/adminaccount/.ssh/id_ed25519: No such file or directory
debug2: we did not send a packet, disable method
debug3: authmethod_lookup password
debug3: remaining preferred: ,password
debug3: authmethod_is_enabled password
debug1: Next authentication method: password
adminaccount@192.168.5.21's password:
debug3: send packet: type 50
debug2: we sent a password packet, wait for reply
debug1: Authentication succeeded (password).
Authenticated to 192.168.5.21 ([192.168.5.21]:22).
debug1: channel 0: new [client-session]
debug3: ssh_session2_open: channel_new: 0
debug2: channel 0: send open
debug3: send packet: type 90
debug1: Requesting no-more-sessions@openssh.com
debug3: send packet: type 80
debug1: Entering interactive session.
debug1: pledge: network
debug3: send packet: type 1
debug1: channel 0: free: client-session, nchannels 1
debug3: channel 0: status: The following connections are open:
  #0 client-session (t3 r-1 i0/0 o0/0 fd 4/5 cc -1)

Connection to 192.168.5.21 closed by remote host.
Connection to 192.168.5.21 closed.
Transferred: sent 1736, received 1388 bytes, in 0.0 seconds
Bytes per second: sent 6027575.9, received 4819283.1
debug1: Exit status -1
adminaccount@mars:~$
adminaccount@mars:~$
adminaccount@mars:~$ ssh -vvv adminaccount@192.168.5.21
OpenSSH_7.2p2 Ubuntu-4ubuntu2.4, OpenSSL 1.0.2g  1 Mar 2016
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug2: resolving "192.168.5.21" port 22
debug2: ssh_connect_direct: needpriv 0
debug1: Connecting to 192.168.5.21 [192.168.5.21] port 22.
debug1: connect to address 192.168.5.21 port 22: Connection timed out
ssh: connect to host 192.168.5.21 port 22: Connection timed out
adminaccount@mars:~$
adminaccount@mars:~$
adminaccount@mars:~$ ssh -vvv adminaccount@192.168.5.21
OpenSSH_7.2p2 Ubuntu-4ubuntu2.4, OpenSSL 1.0.2g  1 Mar 2016
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug2: resolving "192.168.5.21" port 22
debug2: ssh_connect_direct: needpriv 0
debug1: Connecting to 192.168.5.21 [192.168.5.21] port 22.


debug1: connect to address 192.168.5.21 port 22: Connection timed out
ssh: connect to host 192.168.5.21 port 22: Connection timed out
adminaccount@mars:~$
adminaccount@mars:~$
adminaccount@mars:~$ ssh -vvv adminaccount@192.168.5.21
OpenSSH_7.2p2 Ubuntu-4ubuntu2.4, OpenSSL 1.0.2g  1 Mar 2016
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug2: resolving "192.168.5.21" port 22
debug2: ssh_connect_direct: needpriv 0
debug1: Connecting to 192.168.5.21 [192.168.5.21] port 22.


```

---

### Post by darkod on 2018-01-25
Actually I'm not convinced connectivity os working fine. I think these connection timed out message are actually because it is not working correctly.

I am also confused by the reservation outside the dhcp scope thing. The IP reservations are precisely made so that IPs inside the scope get assigned to specific machines using the unique MAC address. Outside the scope there is no way for an IP to be assigned automatically to any device, so reservations are not needed. You set up manual, static IPs and you make sure you don't assign the same one twice (IP conflict).

If you are really using a static IP outside the dhcp scope, I would remove the reservation, just in case it creates any issues. And then try it like that...

To double check connectivity again you can also try ping the destination and traceroute (tracert in windows).

And it goes without saying, you don't have any firewall active on the destination server, right?

---

### Post by NotQuiteSU on 2018-01-25
With regards to the DHCP - You have a subnet, lets say 10.10.10.0/24, which is 0-255 for the last octet. Then you can have a DHCP range, for example, 100 - 250, which would dole out 10.10.10.100- 10.10.10.250. Static IPs are within the /24 range, but not distributed by DHCP. Reservations are done on the DHCP range, but are designed that when a host requests an address, it gets the same one every time.

Anyway..I've had a constant ping running, with no hiccups. I've also done a traceroute which hits my gateway then the host.

I will remove the reservation, and reboot again in a few hours.

I wonder if its CPU exhaustion from something misconfigured. perhaps my FSTAB

---

### Post by NotQuiteSU on 2018-01-25
so some odd behavior. I got home and was able to comment out everything I added to /etc/fstab. rebooted and all is right, save for my mounts.

I added back 2 mounts:
```

//192.168.5.20/media/tvshows /mnt/tvshows cifs credentials=/root/.creds,uid=1000,gid=130,iocharset=utf8,file_mode=0555,dir_mode=0555
//192.168.5.20/media2/movies /mnt/movies cifs credentials=/root/.creds,uid=1000,gid=130,iocharset=utf8,file_mode=0555,dir_mode=0555

```

I copied it literally from my old host which I'm replacing. The uid and gid are correct.

When I tab into /mnt to list the shares, it hangs everything. But I wonder if it is related to the permissions of the mount points...they're root:root on my new server, not that on my old one..

---

### Post by darkod on 2018-01-26
One question, are those cifs shares on a windows server or on linux?

---

### Post by NotQuiteSU on 2018-01-26
linux. and the issue persists when correcting the shares.

I think I'm gonna wipe and start over

---

### Post by darkod on 2018-01-26
If the source is linux use NFS. Don't complicate it with CIFS. I would only use CIFS if windows clients need to use the share too.

In fact, unless I am wrong you can share the same folder by samba for CIFS clients and by NFS for linux clients.

---

### Post by NotQuiteSU on 2018-01-26
You are spot on actually. But I do have some windows clients accessing it. It's been working fine previously.

I just wiped the host and rebuilt. Time to redo the mounts and see if I run into the same problem.

I was seeing a message that said "CIFS VFS: Server <IP> has not responded in 120 seconds, Reconnecting..."

Now I suspect something totally different. I rebuilt, reinstalled, and only after doing all updates (including dist updates) does the system start to lock up from ssh attempts.

I'm going to start over without dist updates.

---

