---
title: "how to forward ports to virtualbox ?"
date: 2008-09-26
forum: Virtualisation
---

### Post by tjwoosta on 2008-09-26
i have installed windows xp as a virtualbox guest

i want to be able to use utorrent on the virtualbox

but my router has a firewall (requiring me to forward the desired ports to the desired machines)


so how do i forward the utorrent ports to my windows xp guest?

---

### Post by veloce on 2008-09-27
Assuming that you are using bridged networking ...

Find out the ip address of the vm (use ipconfig)

On the firewall, forward the appropriate port to the ip address of the vm.

---

### Post by bob_hilton on 2008-09-29
im trying to do the same but ipconfig show my ip address as
```
fe80::a00:27ff:feec:e956%5
```

---

### Post by Delvien on 2008-09-30
> **bob_hilton said:**
> im trying to do the same but ipconfig show my ip address as
```
fe80::a00:27ff:feec:e956%5
```


?


Do this...

Start>Run> type in "cmd" and hit enter>in the command line type 

```
ipconfig /all
```

Then look for your ip address, and write it down.

Go into your router settings, find the option for port forwarding. Fill out the spaces, plop the IP address where it asks you, and the port you wanted it to forward.

---

### Post by tjwoosta on 2008-09-30
> 
Find out the ip address of the vm (use ipconfig)

On the firewall, forward the appropriate port to the ip address of the vm.

yea i tried that but i get an error message from my router that says i cant forward the ports because the address is not part of the private subnet

---

### Post by veloce on 2008-09-30
> **tjwoosta said:**
> yea i tried that but i get an error message from my router that says i cant forward the ports because the address is not part of the private subnet

Not knowing what address spaces you are using makes it difficult to give any meaningful advice here.

However, if you are using NAT to provide internet access to your vm then it will be on a different subnet. 

Alternatively, your vm may not be connected to the network at all.  Did you try the "ipconfig /all" suggestion?

---

### Post by tjwoosta on 2008-09-30
the vm is definatly connected because i can browse on firefox

all of the other computers on my network have adresses like 192.168.1.XX

but the vm has 10.0.2.x

---

### Post by veloce on 2008-10-01
> **tjwoosta said:**
> the vm is definatly connected because i can browse on firefox

all of the other computers on my network have adresses like 192.168.1.XX

but the vm has 10.0.2.x

Ah, that makes sense.  Your virtualbox is set up to use NAT for your vm to access the network (and internet). 

To forward a port to your vm, you have two choices:

[LIST=1]
[*]Get Virtualbox to use bridged networking rather than NAT. I don't actually know if that's possible but then I don't use virtualbox. This would result in your vm having an address in the 192.168.1.xx space.

[*]Forward the port to your host and then setup a "firewall" on the host to forward it again to the virtualbox virtual network (10.0.2.x).  This is also beyond my experience.  You can see if it is feasible by pinging the vm from the host: ping 10.0.2.x
[/LIST]

I know that option 1. is possible under vmware so expect it is under virtualbox.

---

