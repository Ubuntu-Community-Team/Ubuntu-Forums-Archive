---
title: "[SOLVED] WAN access problem [Vista host Vmware Ubuntu 8.1 server]"
date: 2008-11-08
forum: Virtualisation
---

### Post by dkwolf on 2008-11-08
Hi there :) 

Been searching for stuff for days now and now (still kinda newb, but learning fast) i just got tired of it. Been rechearching stuff for my NAS server i am going to build. So i am trying alot of stuff. Buut now i have run into a very strange problem.

Here is what i have

Host: Vista Ultimate 64bit (IP 192.168.1.34 - MAC adress locked in my router)
Client: Ubuntu Server 8.10 64bit (IP 192.168.1.33 - MAC adress locked in my router)
Software: VMware 6.5 build 118166
Network type: vmware bridged

I have gotten everything i wanted to work over my LAN (apache, php,mysql,samba, ssh). But i wanted to be sure that my apache would work over WAN. So i set it up to run on port 8088 (i hate port 80) and it works just fine over LAN. 
I have set up a port forward in my router so port 8088 is forwarded to 192.168.1.33, but i just get a "Could not connect" message.

I have another Ubuntu desktop in my VMware and if i boot it up and make sure it gets the same IP as my Server version. There i can see that the port is open (used the test on [http://www.canyouseeme.org](http://www.canyouseeme.org)). So i am guessing that the problem lies in my Ubuntu Server, but i have no idea where....

there is the output of some commands

netstat -rn
```
Destination     Gateway     Genmask     Flags     MSS  Window  irtt Ifase
192.168.1.0      0.0.0.0    255.255.255.0  U      0    0         0   eth0
0.0.0.0        192.168.1.1   0.0.0.0      UG      0    0         0   eth0
```

netstats -ltn | grep 8088
```
tcp      0    0.0.0.0:8088       0.0.0.0:*    LISTEN
```

Hope some one can give me a pointer to what is wrong

---

### Post by dkwolf on 2008-11-08
well got it working... 

crappy router does not want to port forward 8088 but moved it to 80 and everything works... stupid router

---

