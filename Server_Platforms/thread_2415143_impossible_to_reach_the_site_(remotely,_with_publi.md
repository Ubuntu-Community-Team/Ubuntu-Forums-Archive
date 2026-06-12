---
title: "impossible to reach the site (remotely, with public IP)"
date: 2019-03-21
forum: Server Platforms
---

### Post by danilo-rosso-it on 2019-03-21
Hello,
I set up an Ubuntu 18.04.2 server in my home network, and set a static IP.
Everything works fine locally, but if I try to reach my server from a PC outside my LAN using a public IP (provided by NOIP), I can't.
I tried to install an Ubuntu 16.04 server on another PC on the same LAN, assigning it the same static IP, and this is reachable from the remote PC.


this is my configuration:

```

danilo@ubuntuservertwr:~$ cat /etc/netplan/01-netcfg.yaml


# This file describes the network interfaces available on your system
# For more information, see netplan(5).
network:
  version: 2
  renderer: networkd
  ethernets:
    enp2s0:
     dhcp4: no
     dhcp6: no
     addresses: [192.168.1.24/24]
     gateway4: 192.168.1.1
     nameservers:
       addresses: [8.8.8.8,8.8.4.4] 
             
danilo@ubuntuservertwr:~$ 



```

netplan apply does not report errors:

```

danilo@ubuntuservertwr:~$ sudo netplan apply
[sudo] password di danilo: 
danilo@ubuntuservertwr:~$ 



```

this is netplan --debug apply instead

```

danilo@ubuntuservertwr:~$ sudo netplan --debug apply
[sudo] password di danilo: 
** (generate:4628): DEBUG: 08:03:52.864: Processing input file /etc/netplan/01-netcfg.yaml..
** (generate:4628): DEBUG: 08:03:52.864: starting new processing pass
** (generate:4628): DEBUG: 08:03:52.864: enp2s0: setting default backend to 1
** (generate:4628): DEBUG: 08:03:52.864: Generating output files..
** (generate:4628): DEBUG: 08:03:52.864: NetworkManager: definition enp2s0 is not for us (backend 1)
DEBUG:netplan generated networkd configuration exists, restarting networkd
DEBUG:no netplan generated NM configuration exists
DEBUG:enp2s0 not found in {}
DEBUG:Merged config:
network:
  bonds: {}
  bridges: {}
  ethernets:
    enp2s0:
      addresses:
      - 192.168.1.24/24
      dhcp4: false
      dhcp6: false
      gateway4: 192.168.1.1
      nameservers:
        addresses:
        - 8.8.8.8
        - 8.8.4.4
  vlans: {}
  wifis: {}


DEBUG:Skipping non-physical interface: lo
DEBUG:device enp2s0 operstate is up, not changing
DEBUG:{}
DEBUG:netplan triggering .link rules for lo
DEBUG:netplan triggering .link rules for enp2s0
danilo@ubuntuservertwr:~$ 



```

this is ip addr:

```

danilo@ubuntuservertwr:~$ ip addr
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp2s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 00:1d:60:79:9c:d8 brd ff:ff:ff:ff:ff:ff
    inet 192.168.1.24/24 brd 192.168.1.255 scope global enp2s0
       valid_lft forever preferred_lft forever
    inet6 fe80::21d:60ff:fe79:9cd8/64 scope link 
       valid_lft forever preferred_lft forever
danilo@ubuntuservertwr:~$ 



```


this is ip link:

```

danilo@ubuntuservertwr:~$ ip link
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN mode DEFAULT group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: enp2s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP mode DEFAULT group default qlen 1000
    link/ether 00:1d:60:79:9c:d8 brd ff:ff:ff:ff:ff:ff
danilo@ubuntuservertwr:~$ 



```

this is ip route show:

```

danilo@ubuntuservertwr:~$ ip route show
default via 192.168.1.1 dev enp2s0 proto static 
192.168.1.0/24 dev enp2s0 proto kernel scope link src 192.168.1.24 
danilo@ubuntuservertwr:~$ 



```




Where am I wrong? how to solve?
thank you

---

### Post by TheFu on 2019-03-21
Firewall and port forwarding correct?
Web server blocking non-LAN requests?

What do the log files show on the router and on the server?  Check the firewall logs (router and server) AND the web server logs.

---

### Post by danilo-rosso-it on 2019-03-22
thank you:
I have no firewall;
it is from ubuntu 12.04 that I use an ubuntu server with the same static ip and that it is contacted remotely with the public IP, without any problem. Only the 18.nn does not work. not bad, back to 17.04.

---

### Post by glen88 on 2019-04-03
Sudo ufw status...? upgrade update reboot..[COLOR=#333333][FONT=monospace]sudo netplan try  --try the new netplan [/FONT][/COLOR][COLOR=#333333][FONT=monospace]sudo netplan apply --apply the new configuration
[/FONT][/COLOR][https://www.linux.com/learn/intro-to-linux/2018/9/how-use-netplan-network-configuration-tool-linux](https://www.linux.com/learn/intro-to-linux/2018/9/how-use-netplan-network-configuration-tool-linux)
[https://websiteforstudents.com/configure-static-ip-addresses-on-ubuntu-18-04-beta/](https://websiteforstudents.com/configure-static-ip-addresses-on-ubuntu-18-04-beta/)

---

### Post by TheFu on 2019-04-03
Support for 12.04 and 17.xx ended long ago.
Today, I'd only use 18.04 or 16.04 LTS releases.

I don't have any 18.04 in production today, mainly due to networking considerations. My network needs are non-trivial for many systems.

---

