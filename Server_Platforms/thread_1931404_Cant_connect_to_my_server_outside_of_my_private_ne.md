---
title: "Cant connect to my server outside of my private network"
date: 2012-02-25
forum: Server Platforms
---

### Post by glogo on 2012-02-25
Hi,
I have problem connecting to my server outside of my private network, but I can connect FROM it to internet and I can connect TO my server (via ssh or just ping it...) within my local network.

my configuration:
**/etc/network/interfaces**
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

**/etc/resolv.conf**
nameserver 10.42.43.1

//***

I believe I am missing something, so I would appreciate any help, Thanks!

---

### Post by WasMeHere on 2012-02-25
I guess you and/or your internet provider have a firewall somewhere, that does not allow incoming traffic. This is the default. If you want to open your firewall(s) you must know what you are doing, otherwise your computer will be an easy target for some intruder.

If you have a router, it has probably a firewall to protect your LAN. These things are tricky, so I suggest that you

1. have a look at [[COLOR="RoyalBlue"]_https://wiki.ubuntu.com/BasicSecurity_[/COLOR]]("https://wiki.ubuntu.com/BasicSecurity") which gives a good introduction although it states that it is not for servers.

2. wait for help from some guys that really know about security issues (I am not one of them).

Have fun finding out :-)
Olle

---

### Post by Iowan on 2012-02-25
What do you have for port-forwarding on the router?
Do you have a static IP address from your ISP - or are you using a service like **no-ip.com**.
Does your DHCP server issue a static lease  - otherwise, that server is going to be a moving target.

---

### Post by glogo on 2012-02-25
For port forwarding I have:

```
start	end	protocol	IP		enable
**************************************************************
80	80    	both		192.168.1.4	true
80	80    	both		192.168.1.9	true
80	80    	both		192.168.1.5	true
```


and I have a static IP (well I whink)

> **Iowan said:**
> What do you have for port-forwarding on the router?
Do you have a static IP address from your ISP - or are you using a service like **no-ip.com**.

I guess there could be problem with my **/etc/network/interfaces** configuration... but when I tried following cofiguration:...
I wasnt able to connect to internet from my server or to my server from local computer

```

auto eth0
iface eth0 inet static
  address 192.168.1.9
  gateway 192.168.1.1
  netmask 255.255.255.0
  network 192.168.1.0
  broadcast 192.168.1.255

```

---

### Post by Doug S on 2012-02-25
Please tell us more about your network environment. One reason that I ask is that your name server is listed as 10.42.43.1, which is in itself a private network address. So I guess my related question: Is your private network a sub-net of another private network?
I do not think that what you listed as port forwarding is. It looks to me as though it is a list of enabled outgoing ports for computers on your private network.

---

### Post by glogo on 2012-02-25
Just few seconds before you replied I realized that problem was between the keyboard and chair...

You are right I am (or I was) having a sub net... I realized that from that strange IP just like you have. I am connected to this router with my laptop via wifi and I was sharing internet connection from my laptop to this server via short ethernet cable, because wifi router is in next room. 
Now I managed to find a long ethernet cable so I think this part of problem is fixed...

so server now have static IP...

Now the question is, how to make my server become visible online... when I put my static ip 192.168.1.9 into browser (from PC in home network) I could connect, but when I write my public IP into browser nothing is happening... just long delay.
What else I do need to configure please.
Thanks much

---

### Post by glogo on 2012-02-25
Okay, I feel bit awkward.. solving my problems and realizing that Im missing the obvious things...

I just had to correct now port triggering to accept my static 192.168.1.9  on port 80
I thought I set it that but I was playing with that and something went wrong...
I hope this could help somebody someday :)

thanks for your time

---

### Post by WasMeHere on 2012-02-25
Congratulations :KS

I hope you will enjoy your networking. And don't wait too long to have a look at that wiki page about security issues ;-)

---

### Post by glogo on 2012-02-25
> **Olle Wiklund said:**
> Congratulations :KS

I hope you will enjoy your networking. And don't wait too long to have a look at that wiki page about security issues ;-)

OK, I will tottaly do that :)
thanks again for your cooperation!

---

