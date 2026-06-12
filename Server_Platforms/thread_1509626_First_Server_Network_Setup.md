---
title: "First Server: Network Setup?"
date: 2010-06-14
forum: Server Platforms
---

### Post by cwhiii on 2010-06-14
A little background: I am setting up my first server (which will be a file server when complete). I have some experience with a terminal, but not much. I'm not at all afraid of it, and want to learn more (one of the reasons I'm doing this project). 

At the moment I am trying to get the server to see my network. Using the info I found here: [https://help.ubuntu.com/10.04/serverguide/C/network-configuration.html](https://help.ubuntu.com/10.04/serverguide/C/network-configuration.html) I have been able to ping the router. I cannot, however, reach other computers on the network. Nor can other computers ping the server.

I am looking for a newbie guide on how to connect to my local network.

--
C.W.Holeman III
[http://www.cwholemaniii.com](http://www.cwholemaniii.com)

---

### Post by CharlesA on 2010-06-14
What OS is the network comprised of?

---

### Post by cwhiii on 2010-06-14
I have OS X, Windows XP and Ubuntu (Desktop) 10.04

---

### Post by arrrghhh on 2010-06-14
That's a pretty thorough guide, so can you give us more info?

Are you using a static IP for the server?  Can you ping anything outside of your router?  I know you said you couldn't ping any of the other machines, how about [www.google.com](www.google.com) or something?

---

### Post by cwhiii on 2010-06-14
The router does have a static IP, and I can only ping the router.

---

### Post by CharlesA on 2010-06-14
What does this return?

```
cat /etc/resolv.conf
```

---

### Post by cwhiii on 2010-06-14
search MathomGrove
nameserver 192.168.0.1

---

### Post by arrrghhh on 2010-06-14
> **cwhiii said:**
> The router does have a static IP, and I can only ping the router.

I meant does the server have a static IP...

---

### Post by CharlesA on 2010-06-14
Can you ping the others via IP address? If you can, then DNS isn't working correctly.

---

### Post by drdos2006 on 2010-06-14
I found this HOWTO very, very useful.
> 
Are you using the most current version of this how-to?
Version numbers are located @ top right of this page. Latest versions are available at my homepage [http://woodel.com](http://woodel.com)
Under the Solutions tab
Setting up a Linux Server, Start to Finish, using Webmin. By Kevin Elwood



regards

---

### Post by cwhiii on 2010-06-14
> **arrrghhh said:**
> I meant does the server have a static IP...


Oh, sorry. Yes the server has a IP (or at least. it's supposed to, and I believe it does.)

---

### Post by cwhiii on 2010-06-14
> **CharlesA said:**
> Can you ping the others via IP address? If you can, then DNS isn't working correctly.

I can ping any computer from any other except for the server, which nothing can ping, and which can only ping the router.

---

### Post by arrrghhh on 2010-06-14
> **cwhiii said:**
> Oh, sorry. Yes the server has a IP (or at least. it's supposed to, and I believe it does.)

Please post the results of 'ifconfig' in a [ code ] bracket.  Also, post your /etc/networking/interfaces in a separate [ code ] bracket.

---

### Post by cwhiii on 2010-06-14
> **CharlesA said:**
> Can you ping the others via IP address? If you can, then DNS isn't working correctly.

I can ping any computer from any other except for the server, which nothing can ping, and which can only ping the router.

---

### Post by cwhiii on 2010-06-14
> **arrrghhh said:**
> Please post the results of 'ifconfig' in a [ code ] bracket.  Also, post your /etc/networking/interfaces in a separate [ code ] bracket.

ifconfig:
```

eth0 
  Link encap:Ethernet   HWadder 00:22:15:a4:4e:b9
  inet addr: 192.168.0.1  Bcast 192.168.0.255 mask:255.255.255.0
  UP BROADCAST MULTICAST MTU:1500 Metric:1
  RX packets :0 errors:0 dropped:0 overruns:0 frame:0
  TX packets :0 errors:0 dropped:0 overruns:0 carrier:1
  collisions:0 txqueuelen:1000
  RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
  Memory:fbfc000-fc000000

lo 
  Link encap:Local Loopback
  inet addr:127.0.0.1 Mask 255.0.0.0
  inet6 addr: ::1/120 Scopre Host
  UP LOOPBACK RUNNING MTU:16436 Metric:1
  RX packets: 2204 errors:0 dropped:0 overruns:0 frame:0
  TX packets:  2204 errors:0 dropped:0 overruns:0 carrier:0
  collisions:0 txqueuelen: 0
  RX bytes:349555 (349.5 KB) TX bytes:349555 (349.5 KB)    
  
virbr0
  Link encap:Ethernet   HWadder 3a:46:ff:ca:94:c1
  inet addr: 192.168.122.1  Bcast 192.168.122.255 mask:255.255.255.0
  inet6 addr:fe80::3846:ffff:feca:94c1/64 Scope: Link
  UP BROADCAST MULTICAST MTU:1500 Metric:1
  RX packets :0 errors:0 dropped:0 overruns:0 frame:0
  TX packets :0 errors:0 dropped:0 overruns:0 carrier:0
  collisions:0 txqueuelen:0
  RX bytes:0 (0.0 B) TX bytes:29444 (29.4 KB)
  Memory:fbfc000-fc000000

```

I assume you meant cat of /etc/networking/interfaces (without comments)
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
  address 192.168.0.1
  netmask 255.255.255.0
  network 192.168.0.0
  broadcast 192.168.0.255
  gateway 192.168.0.1

dns-nameservers 192.168.0.1
dns-search MathomGrove

```

---

### Post by CharlesA on 2010-06-14
It looks like it has the same IP address as the router.

---

### Post by arrrghhh on 2010-06-15
> **CharlesA said:**
> It looks like it has the same IP address as the router.

I was going to say the same thing.  Change the IP in /etc/networking/interfaces, you can't have 192.168.0.1 - that looks like it's your gateway's address.  You *can* take that IP, but you'll need to change the IP of your gateway to something else.

---

### Post by cwhiii on 2010-06-15
> **arrrghhh said:**
> I was going to say the same thing.  Change the IP in /etc/networking/interfaces, you can't have 192.168.0.1 - that looks like it's your gateway's address.  You *can* take that IP, but you'll need to change the IP of your gateway to something else.

Oops. Copy and paste error. Actual file is: 
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
  **address 192.168.0.121**
  netmask 255.255.255.0
  network 192.168.0.0
  broadcast 192.168.0.255
  gateway 192.168.0.1

dns-nameservers 192.168.0.1
dns-search MathomGrove

```

---

### Post by arrrghhh on 2010-06-15
> **cwhiii said:**
> Oops. Copy and paste error. Actual file is:

```
eth0 
  Link encap:Ethernet   HWadder 00:22:15:a4:4e:b9
  inet addr: **192.168.0.1**  Bcast 192.168.0.255 mask:255.255.255.0
  UP BROADCAST MULTICAST MTU:1500 Metric:1
  RX packets :0 errors:0 dropped:0 overruns:0 frame:0
  TX packets :0 errors:0 dropped:0 overruns:0 carrier:1
  collisions:0 txqueuelen:1000
  RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
  Memory:fbfc000-fc000000
```

So was it a copy/paste error with your ifconfig as well?  Because your ifconfig agrees with your interfaces file from you other posts...

---

### Post by CharlesA on 2010-06-15
> **arrrghhh said:**
> ```
eth0 
  Link encap:Ethernet   HWadder 00:22:15:a4:4e:b9
  inet addr: **192.168.0.1**  Bcast 192.168.0.255 mask:255.255.255.0
  UP BROADCAST MULTICAST MTU:1500 Metric:1
  RX packets :0 errors:0 dropped:0 overruns:0 frame:0
  TX packets :0 errors:0 dropped:0 overruns:0 carrier:1
  collisions:0 txqueuelen:1000
  RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
  Memory:fbfc000-fc000000
```

So was it a copy/paste error with your ifconfig as well?  Because your ifconfig agrees with your interfaces file from you other posts...

I don't know how that one could have been a copy/paste error, but you never know.

---

### Post by arrrghhh on 2010-06-15
> **CharlesA said:**
> I don't know how that one could have been a copy/paste error, but you never know.

The fact that his interfaces file matched his ifconfig is suspect of any copy/paste error...

OP, what's the result?  I have a feeling the interfaces file is the culprit - a bad config will do exactly what you have described.

---

