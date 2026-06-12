---
title: "HowTo: Setup OpenVPN on Amazon EC2 service"
date: 2010-12-27
forum: Ubuntu Cloud and Juju
---

### Post by Dukeswharf on 2010-12-27
Hi,
I am completely new to the Linux world, but would like to setup:

1. An AWS EC2 server running an Linux 10.x instance (64 or 32 bit?)
2. OpenVPN server

and how to 

1. Start/stop an EC2/OpenVPN service from an Ubuntu 10.10 Desktop client 

Can anyone put me in the direction of step by step instructions to set this up?

Many thanks in advance
Duke

---

### Post by raymdt on 2010-12-27
```

ssh -i mykeypriv  ubuntu@<myip>

/etc/init.d/openvpn stop or start


```

to install

[https://help.ubuntu.com/10.04/serverguide/C/openvpn.html](https://help.ubuntu.com/10.04/serverguide/C/openvpn.html)

---

