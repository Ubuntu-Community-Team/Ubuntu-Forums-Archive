---
title: "SERVER help"
date: 2011-09-23
forum: Server Platforms
---

### Post by brent2151@ on 2011-09-23
Running ubuntu server 11.04 as a home media/ samba server everything was working for 2 weeks now its running but cant connect to any of the other devices. HELP

---

### Post by Dangertux on 2011-09-23
Have you verified the network connection is active , and properly working?

Also could you provide more information?

---

### Post by brent2151@ on 2011-09-23
getting ip address can see my router working....just cant see it on the network anymore im completely lost cant even remote login anymore no way to post results without typing it all out...grrr 
can still login on local keyboard...help...:)

---

### Post by brent2151@ on 2011-09-23
cant even ping the router 

ping 192.168.0.1

From 192.168.0.2 icmp_seq=100 Destination Host Unreachable
From 192.168.0.2 icmp_seq=101 Destination Host Unreachable
From 192.168.0.2 icmp_seq=102 Destination Host Unreachable
From 192.168.0.2 icmp_seq=103 Destination Host Unreachable

---

### Post by Dangertux on 2011-09-23
You should try restarting the network. 

```

sudo /etc/init.d/networking restart

```

See if that helps. If anything reboot the machine.

---

### Post by brent2151@ on 2011-09-23
was all my crappy shaw wireless router switched ports now mediaserver works, gotta figure out why samba is not

---

### Post by CharlesA on 2011-09-24
Post this please:

```
service smbd status
```
```
service nmbd status
```

---

### Post by kevinthecomputerguy on 2011-09-24
try this... [http://woodel.com](http://woodel.com)   (makes samba easy, you will be most interested in page 3, but read in order)

---

