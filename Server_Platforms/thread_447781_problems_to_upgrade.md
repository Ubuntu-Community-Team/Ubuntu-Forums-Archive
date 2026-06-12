---
title: "problems to upgrade"
date: 2007-05-18
forum: Server Platforms
---

### Post by lvamb on 2007-05-18
HI,
I have a ubuntu production server and today I upgrade from edgy to feisty. The problem was that a reboot I've got the following error:

```

[/dev/sda10] unknown operand

```

with my customized kernel. Then I reinstalled my deb kernel packages and everything was solved.
But now I have discovered that the /proc/sys/net/ipv4/ip_forward was come back to 0 then my vpn connection was broken... so my question is .. why upgrade ubuntu server have so much problems   ?

---

