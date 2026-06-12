---
title: "Cannot ssh over pptp after upgrade to Ubuntu 15.10"
date: 2015-11-04
forum: Server Platforms
---

### Post by radoslav2 on 2015-11-04
Hello guys,
After i upgraded to ubuntu 15.10 i cannot establish ssh connection to my server over pptp but i can ssh from my server to the upgraded pc. In local network ssh works fine. Also my nfs mounts hangs after some time which are also over pptp mounted. I can connect with samba, ftp to my server, i have ping to the server.
This is output when i try ssh over pptp:
 ```
 debug1: Reading configuration data /etc/ssh/ssh_configdebug1: /etc/ssh/ssh_config line 19: Applying options for *
debug1: Connecting to 192.168.88.100 [192.168.88.100] port 22.
debug1: Connection established.
debug1: identity file /home/rpr/.ssh/id_rsa type 1
debug1: key_load_public: No such file or directory
debug1: identity file /home/rpr/.ssh/id_rsa-cert type -1
debug1: key_load_public: No such file or directory
debug1: identity file /home/rpr/.ssh/id_dsa type -1
debug1: key_load_public: No such file or directory
debug1: identity file /home/rpr/.ssh/id_dsa-cert type -1
debug1: key_load_public: No such file or directory
debug1: identity file /home/rpr/.ssh/id_ecdsa type -1
debug1: key_load_public: No such file or directory
debug1: identity file /home/rpr/.ssh/id_ecdsa-cert type -1
debug1: key_load_public: No such file or directory
debug1: identity file /home/rpr/.ssh/id_ed25519 type -1
debug1: key_load_public: No such file or directory
debug1: identity file /home/rpr/.ssh/id_ed25519-cert type -1
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_6.9p1 Ubuntu-2
debug1: Remote protocol version 2.0, remote software version OpenSSH_6.2_hpn13v11 FreeBSD-20130515
debug1: match: OpenSSH_6.2_hpn13v11 FreeBSD-20130515 pat OpenSSH* compat 0x04000000
debug1: Authenticating to 192.168.88.100:22 as 'rpr'
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-ctr umac-64-etm@openssh.com none
debug1: kex: client->server aes128-ctr umac-64-etm@openssh.com none
debug1: sending SSH2_MSG_KEX_ECDH_INIT
debug1: expecting SSH2_MSG_KEX_ECDH_REPLY



```

Any suggestions

---

### Post by QIII on 2015-11-04
*Moved to **Server Platforms***

---

### Post by radoslav2 on 2015-11-05
I don't understand why this thread is moved to server Platforms, the problem is on the client side.

---

### Post by radoslav2 on 2015-11-06
It turns the problem seems to be in pptp configuration. When i do it from network manager everything works but i am loosing connection or it is very slow. Thats why i did configuration manualy in the begining. I checked pptp configuration files and ntohing seems to be changed but still it does'n work.

---

### Post by andydread on 2015-11-11
> **radoslav2 said:**
> It turns the problem seems to be in pptp configuration. When i do it from network manager everything works but i am loosing connection or it is very slow. Thats why i did configuration manualy in the begining. I checked pptp configuration files and ntohing seems to be changed but still it does'n work.


Try lowering the mtu down to something like 1392. You can test this by typing:
```
ifconfig ppp0 mtu 1392
``` 
or another value below 1492 once you find a value that works then to make it permanent edit the /etc/ppp/peers/ and add
```
mtu <value>
```
eg. mtu 1392

---

