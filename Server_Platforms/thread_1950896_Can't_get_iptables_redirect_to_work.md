---
title: "Can't get iptables redirect to work"
date: 2012-04-01
forum: Server Platforms
---

### Post by ilyail3 on 2012-04-01
Hi

I have a short snippet

```
CHAIN_NAME="RED$dest"

sudo iptables -t nat -L $CHAIN_NAME &> /dev/null

if [[ $? != 0 ]];
then
	echo "create $CHAIN_NAME"
	iptables -t nat -N $CHAIN_NAME
	iptables -t nat -A PREROUTING -p tcp --dport $dest -j $CHAIN_NAME
fi


iptables -t nat -F $CHAIN_NAME
iptables -t nat -A $CHAIN_NAME -p tcp -j REDIRECT --dport $dest --to-port $source
```

Which should allow multiple instances of a service to run at the same time, redirecting to the newest on and gracefully shutting down the old one without causeing downtime. Well, at least that's the theory.

In practice, I couldn't get it to work on my development environment , ubutntu 11.10 64bit desktop.

I tried using ```
sudo sysctl -w net.ipv4.ip_forward=1
``` , Masquerading, allowing forward(which is allowed anyway). And still couldn't get it to work. 

I used similar script on server and it worked like a charm, why is Desktop different?

---

### Post by ilyail3 on 2012-04-01
Found something running
```
sudo iptables -t nat -v -x -n -L
Chain PREROUTING (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 4 

Chain INPUT (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 222 packets, 14344 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain POSTROUTING (policy ACCEPT 222 packets, 14344 bytes)
    pkts      bytes target     prot opt in     out     source               destination
```

why I don't have and prerouting packets, is there something I forgot to enable?

---

