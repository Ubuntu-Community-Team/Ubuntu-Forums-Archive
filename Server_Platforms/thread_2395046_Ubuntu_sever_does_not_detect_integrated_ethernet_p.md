---
title: "Ubuntu sever does not detect integrated ethernet ports on DL180 SE HP Pavilion G6"
date: 2018-06-25
forum: Server Platforms
---

### Post by hmmmmmmmmmmm on 2018-06-25
When i tried to install Ubuntu sever on my  DL180 SE HP Pavilion G6 it could  not detect any interface is. So i cant install it how could i fix this problem

---

### Post by volkswagner on 2018-06-26
can you post output of:
```
lspci | grep Ethernet
```

---

### Post by hmmmmmmmmmmm on 2018-07-20
sorry for the long reply .but it does it when i try to install it

---

### Post by hmmmmmmmmmmm on 2018-07-26
how  do i do that when i am in the installer

---

### Post by hmmmmmmmmmmm on 2018-07-26
> **volkswagner said:**
> can you post output of:
```
lspci | grep Ethernet
```

how do i do that when i am in the installer

---

### Post by darkod on 2018-07-26
Create the live cd/usb with the desktop version that has live mode. Then boot it into live mode (Try Ubuntu), open terminal and you can run commands to get more HW info.

---

### Post by hmmmmmmmmmmm on 2018-08-15
do i do it like this [COLOR=#000000][FONT=&quot]lspci | grep Ethernet or [/FONT][/COLOR][COLOR=#000000][FONT=&quot]lspci grep Ethernet

[/FONT][/COLOR]

---

### Post by darkod on 2018-08-15
Just like he wrote. Including the vertical line.

---

### Post by hmmmmmmmmmmm on 2018-08-15
it came up with nothing ?

---

### Post by CharlesA on 2018-08-15
> **hmmmmmmmmmmm said:**
> it came up with nothing ?

Found some information about the NIC in that server.
[http://h20628.www2.hp.com/km-ext/kmcsdirect/emr_na-c01727924-8.pdf](http://h20628.www2.hp.com/km-ext/kmcsdirect/emr_na-c01727924-8.pdf)
[https://serverfault.com/questions/181508/dual-port-server-nic-question](https://serverfault.com/questions/181508/dual-port-server-nic-question)

Try this instead.

```
sudo lshw | grep Ethernet
```

This might help as well..
[https://wiki.debian.org/HP/ProLiant](https://wiki.debian.org/HP/ProLiant)

---

### Post by hmmmmmmmmmmm on 2018-08-27
ok
ubuntu@ubuntu:~$ sudo lshw | grep Ethernet

PCI (sysfs)

---

