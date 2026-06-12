---
title: "vmware port forwarding"
date: 2010-03-25
forum: Virtualisation
---

### Post by halfdead on 2010-03-25
Hello, since a few days im runnign an VMware server on my rootserver (running windows server 2003 as guest), tbh host is CentOS, although i guess my problem aint no kernel problem so i figured i could post it over here too

Ive been googling alot to fix my problems, got several fixed but got 1 big problem with vmware port forwarding with NAT network card setup..

First question : Can i forward more then 1 port using [incomingxxx] in the nat.conf?

Lets go futher with my story,,

On several links i found u have to set [incomingtcp] in nat.conf, so i did
Ive changed it into this : 
```
[incomingtcp]
# Use these with care - anyone can enter into your VM through these...
1434 = 192.168.165.128:1434
1433 = 192.168.165.128:1433
3389 = 192.126.165.128:3389
```When i restart network / vmware i only got access with the 1434 port, after doing ipconfig /renew in windows server i only got access from 3389 ( remote desktop )

When i put 3389 in the middle of them it connects fine, although it fails at configuring..

so other words : it only reads one port / line

i got linux iptables accepting 1434, 1433 and 3389.. got no other firewall running

So the questions :

Is this normal in vmware Server ?
if no.: how can i fix my problem so i can access it using these ports ( remote desktop and sql server )

---

