---
title: "Need Help- Ubuntu Server"
date: 2009-09-16
forum: Server Platforms
---

### Post by pampersdry on 2009-09-16
hi all.....im new here....im sorry if the question had already asked by someone....

i've install ubuntu server on my hp proliant...the problem is my box have no conn to the internet or network...i use 2 net interface

this is my ip setting

******eth0
address 192.168.1.10
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1


when i ping google.com, the server say "unknown host google.com"... and i cannot ping my gateway...."destination host unreachable"....

i dont know what the real problem is.... :(

---

### Post by KiLaHuRtZ on 2009-09-16
Make sure you have DNS setup in '/etc/resolv.conf'.

```
domain [YOUR DOMAIN] # (optional)
search [YOUR DOMAIN] # (optional)
nameserver [A.A.A.A]
nameserver [B.B.B.B]
[...]
nameserver [Z.Z.Z.Z]
```

Also, have you restarted networking?

```
sudo /etc/init.d/networking restart
```

One last thing, are you using the correct NIC?

---

### Post by PilotJLR on 2009-09-16
Please post:

```

ifconfig -a

route

cat /etc/resolv.conf

```

---

### Post by Udayakiran on 2009-09-17
have you tried this:
```
sudo dmesg | less
```most of the time it shows what the problem is.

maybe the network interface has not been initialized.

also try ```
ifconfig -a
``` to see if it is eth0 or something else. at times it initializes to eth1.

---

