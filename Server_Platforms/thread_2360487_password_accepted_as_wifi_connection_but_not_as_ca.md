---
title: "password accepted as wifi connection but not as cable connection: Ubuntu 16.04 Server"
date: 2017-05-05
forum: Server Platforms
---

### Post by marco910 on 2017-05-05
Hi,
in the last two days I connected to mu Ubuntu 16.04 Server via ssh through only wifi connection.
Today I can use my desk and I tried to connect, as I did till two days ago, to my Ubuntu 16.04 Server via cable.
But exactly the same password used for the wifi connection doesn't allow to me to access my Ubuntu 16.04 Server via cable:

via wifi:
login as: marco
Server refused our key
marco@192.168.1.8's password:
Welcome to Ubuntu 16.04.2 LTS (GNU/Linux 4.4.0-75-generic x86_64)

 * Documentation:  [https://help.ubuntu.com](https://help.ubuntu.com)
 * Management:     [https://landscape.canonical.com](https://landscape.canonical.com)
 * Support:        [https://ubuntu.com/advantage](https://ubuntu.com/advantage)

38 packages can be updated.
0 updates are security updates.


Last login: Thu May  4 09:22:23 2017 from 192.168.1.3
marco@PC:~$


via cable:
login as: marco
Server refused our key
marco@192.168.1.7's password:
Access denied
marco@192.168.1.7's password:


I didn't touch any of the two files /etc/network/interfaces and /etc/wpa_supplicant.conf

Any suggestions about what happened and how to solve it?
Looking forward to your kind help.
Marco

---

### Post by cariboo on 2017-05-05
Could you post the output of:
```
ssh -vvv marco@192.168.1.7
```

---

### Post by darkod on 2017-05-06
Why are you accessing it by different IPs? Your ubuntu server has both wired and wireless connection with different IP?

Usually you would have only single connection to your LAN and whether you connect with wired or wireless connection your router (or wifi access point) takes care of that.

In theory it sould work with both connections because ssh by default listens on all. But unless you really need it, don't connect your server by two connections to the LAN.

---

### Post by volkswagner on 2017-05-07
Fingerprint mismatch, is likely because you connected to a different server or you made changes to current sever and saved fingerprint in ~/.ssh/known_hosts.

You'll need to delete the entry wit same IP. In the above file, then reconnect.

---

