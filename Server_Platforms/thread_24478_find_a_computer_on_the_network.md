---
title: "find a computer on the network"
date: 2005-04-07
forum: Server Platforms
---

### Post by chz on 2005-04-07
how do you find an ip address of a computer on the network. i am able to connect through its name through samba, but some applications require strictly just the IP address. i've tried random methods like pinging and smbclient, but that doesnt work. any ideas?

---

### Post by fjleal on 2005-04-08
nmap -sP 10.0.0.0/24

See "nmap --help".

---

### Post by yvesvanbelle on 2005-04-08
just ping the name of the machine and you will get the ip-address

ex. ping -c 5 server

Best regards
Yves

---

