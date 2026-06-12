---
title: "HTB traffic shaping - working, but need more customisation"
date: 2011-09-19
forum: Server Platforms
---

### Post by wall_e on 2011-09-19
Hello all.

I've tried my best before asking.

My server is running 10.04 server and it has a fast-ish 8 drive Raid5 array, which is home to a number of samba share points.

I use this box at home, it only gets used as a samba file server.

My aim is to stop each _individual client_ from using more than 200mbps of the gigabit pipe to the switch.

So far I've managed to do this with HTB, but I've hit a brick wall.

Using the commands below I am able to throttle traffic leaving the interface, but I want to carve individual 200mbit pipes per client, not limit the overall traffic for the interface to 200mbit. 

```
sudo /sbin/tc qdisc del dev eth1 root

sudo /sbin/tc qdisc add dev eth1 root handle 1:0 htb default 10

sudo /sbin/tc class add dev eth1 parent 1:0 classid 1:10 htb rate 200mbps ceil 200mbps prio 0

sudo tc filter add dev eth1 parent 1:0 prio 0 protocol ip handle 10 fw flowid 1:10
```

Can anybody help with this?

I read that there is a way to do this with Shorewall per IP, but the kernel extension required is not present in the standard kernel - and I can't find any information about patching to achieve what is required.

Any ideas?

---

