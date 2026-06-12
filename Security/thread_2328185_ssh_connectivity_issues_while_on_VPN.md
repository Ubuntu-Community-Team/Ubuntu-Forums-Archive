---
title: "ssh connectivity issues while on VPN"
date: 2016-06-18
forum: Security
---

### Post by vicmorrowshead on 2016-06-18
Hello,

I am experiencing issues connecting to ssh under certain conditions.

If the client is physically plugged into the same LAN as the ssh server (not on VPN), no issues. Connection is instant.

If the client is not on the LAN but is VPN'd in, here are the results:

```
# ssh me@192.168.1.182 -v
OpenSSH_7.2p2 Ubuntu-4ubuntu1, OpenSSL 1.0.2g-fips  1 Mar 2016
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug1: Connecting to 192.168.1.182 [192.168.1.182] port 22.
debug1: Connection established.
### (a bunch of identity lines here)
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_7.2p2 Ubuntu-4ubuntu1
debug1: Remote protocol version 2.0, remote software version OpenSSH_7.2p2 Ubuntu-4ubuntu1
debug1: match: OpenSSH_7.2p2 Ubuntu-4ubuntu1 pat OpenSSH* compat 0x04000000
debug1: Authenticating to 192.168.1.182:22 as '<my account name here>'
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: algorithm: curve25519-sha256@libssh.org
debug1: kex: host key algorithm: ecdsa-sha2-nistp256
debug1: kex: server->client cipher: chacha20-poly1305@openssh.com MAC: <implicit> compression: none
debug1: kex: client->server cipher: chacha20-poly1305@openssh.com MAC: <implicit> compression: none
debug1: expecting SSH2_MSG_KEX_ECDH_REPLY
### --> (big delay here: > 1min)
Connection closed by 192.168.1.182 port 22
```

Some points:

[LIST]
[*]The ssh server I am trying to connect to is the same server that hosts the OpenVPN server.
[*]Please note that everything above (the -v on ssh) is how it appears when connecting while plugged directly into the LAN except that it finishes immediately AND successfully.
[*]While VPN'd in, ping works to this server instantly and without any issues.
[*]There are other "IoT's" on this LAN (part of the 192.168.1.0/24 subnet) that I can access without any issues: no communication issues, no delays while connected via VPN from outside.
[/LIST]

Thanks for your help.

---

### Post by vicmorrowshead on 2016-06-19
MTU size is the issue. Depending on certain firewalls and routers in between to server and client, fragmentation could occur. Reducing the MTU size on the server's tun interface seems to have solved the problem.

---

