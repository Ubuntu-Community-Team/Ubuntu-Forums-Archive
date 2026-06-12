---
title: "problems with ufw"
date: 2010-01-28
forum: Server Platforms
---

### Post by Ju1es on 2010-01-28
Hey guys,

I have set up a Ubuntu-9.10-Server which has two network interface cards and should route packages from network 192.168.0.0/24 (eth0) to 192.168.1.0/24 (eth1) and the other way around. 

I did this with ufw and the package routing works perfectly so that pings from all clients in one network reach clients in the other, also every host has a working connection to the internet. Now I wanted to set some rules i.e. blocking some port for specific clients and block some specific IPs, so that they can't reach the other network.

But the problem is: the rules I set in ufw actually don't cause any effect. For test purpose I set a rule: deny from anywhere to anywhere (just right before I entered the sudo ufw default deny command which already should do the same thing) but still every hosts ping passes through the router. 

So I really was wondering how this can happen that the ufw blocks nothing? I've already done a similar project and there it worked properly?


//I used the search function, and found nothing. Sorry if I missed a thread already dealing with this problem.



thank you[B]


Ju1es[/B]

---

### Post by cdenley on 2010-01-28
[https://answers.launchpad.net/ufw/+question/26585](https://answers.launchpad.net/ufw/+question/26585)

---

### Post by Ju1es on 2010-01-28
Thanks but didn't work. Sorry I should have said that every package passes the ufw although it is denied, not only the icmp packages.

What has changed now is that pings to the server (192.168.0.250, 192.168.1.250) itself fail, so there must be a working rule? But i.e. I try to reach the gateway 192.168.0.254 from the client 192.168.1.30 it still works although I  can't reach the server at its eth0 address 192.168.0.250. I actually have a rule: sudo ufw deny from 192.168.1.30 to 192.168.0.254 but I can definetly reach it on every port...

I don't get it :( its strange.


**Ju1es**

---

### Post by cdenley on 2010-01-28
```

sudo ufw status

```

---

### Post by Ju1es on 2010-01-28
[FONT=Courier New]Status: active

To              [/FONT][FONT=Courier New]Action [/FONT][FONT=Courier New]            From
Anywhere        [/FONT][FONT=Courier New]Deny              [/FONT][FONT=Courier New]Anywhere
192.168.0.254[/FONT][FONT=Courier New]   Deny              [/FONT][FONT=Courier New]192.168.1.30[/FONT][FONT=Courier New]



[/FONT]**Ju1es**

---

### Post by cdenley on 2010-01-28
> **Ju1es said:**
> 
What has changed now is that pings to the server (192.168.0.250, 192.168.1.250) itself fail, so there must be a working rule? But i.e. I try to reach the gateway 192.168.0.254 from the client 192.168.1.30 it still works although I  can't reach the server at its eth0 address 192.168.0.250. I actually have a rule: sudo ufw deny from 192.168.1.30 to 192.168.0.254 but I can definetly reach it on every port...

I don't understand. The server with the firewall is 192.168.0.250. You configure UFW to filter traffic coming to 192.168.0.250. Traffic sent to 192.168.0.254 would not be filtered by UFW on 192.168.0.250. Even if the traffic was being routed through the server, the traffic would be forwarded and the INPUT chain would not be processed, so it wouldn't be filtered.

UFW filters inbound traffic to the server.

---

### Post by Ju1es on 2010-01-28
thank you very much so far but what does it mean, the input chain wouldn't be processed? Do you mean the traffic to 192.168.0.250 is filtered but if I try to acces 192.168.0.254 its only forwarded through 192.168.0.250 and NOT filtered in any way?

So how do realise that some clients in 192.168.1.0/24 are NOT allowed to send ANY traffic to the 192.168.0.0/24 network then?


**Ju1es**

---

### Post by cdenley on 2010-01-28
> **Ju1es said:**
> thank you very much so far but what does it mean, the input chain wouldn't be processed? Do you mean the traffic to 192.168.0.250 is filtered but if I try to acces 192.168.0.254 its only forwarded through 192.168.0.250 and NOT filtered in any way?

So how do realise that some clients in 192.168.1.0/24 are NOT allowed to send ANY traffic to the 192.168.0.0/24 network then?


**Ju1es**

UFW is not for configuring your network. It is for configuring your server. If you are currently using ubuntu to route traffic for an entire network, I suggest you configure iptables directly by manipulating the NAT table. If it is not being routed through your ubuntu server, then of course you can't filter it from the server.

---

### Post by Ju1es on 2010-01-28
Ok I understand! Thank you! And I guess this is also the reason why it worked on the previous project I used it, there I had a virtual machine with only ONE physical network interface card and everything ran over only one physical network. Nevermind.


I heard it is quite hard to get familiar with iptables/NAT table... Is there any tutorial you could recommend me?? Or could you tell me basic commands?

Thanks again for your excellent help.



Ju1es

---

### Post by cdenley on 2010-01-28
[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)
```

man iptables

```

---

