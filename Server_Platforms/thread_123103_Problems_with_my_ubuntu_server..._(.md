---
title: "Problems with my ubuntu server... :("
date: 2006-01-29
forum: Server Platforms
---

### Post by monotux on 2006-01-29
Hello everyone!

I reinstalled my home server yesterday (from debian to ubuntu), but it didn't take long before I ran into some strange problems.

The install went great, but for some reason, my ubuntu server doesn't answer to any other of my computers in my private network.
I have 2 ports forwarded from my router to my server, ssh and http, and if I try to ssh to my external DNS, I can log on to my server, visit it's webpages etc, but if I try the same thing using it's internal IP-address, I usually get something like "no route to host".

I tried to check my /etc/hosts{.deny,.allow}, but they are very sane (deny and allow doesn't contain anything), I don't have any firewall running that could screw things up...and I'm out of ideas.

Anyone with any ideas on how to resolv this? :(

---

### Post by alamba on 2006-01-29
Are you able to ping the internal IP? 

Akshay

---

### Post by monotux on 2006-01-29
[QUOTE=alamba]Are you able to ping the internal IP? 

Akshay[/QUOTE]
Not from my laptop :/
But from another computer I can even connect using samba, but not look up the name with nmblookup.

---

### Post by alamba on 2006-01-30
What's your IP address scheme in your internal network? Post your ifconfig and netstat -rn from your laptop. Are you running a firewall on the ubuntu box?

Akshay

---

### Post by monotux on 2006-01-30
[QUOTE=alamba]What's your IP address scheme in your internal network? Post your ifconfig and netstat -rn from your laptop. Are you running a firewall on the ubuntu box?

Akshay[/QUOTE]

My router uses this as it's scheme: 192.168.1.0 (and I'm not sure whever the subnet mask is /24 or /32, I never understood that part).
My laptop has a static DHCP-address of .13, and the server .12 (but I'm using the static method)

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
10.0.0.1        0.0.0.0         255.255.255.255 UH        0 0          0 tun0
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 ath0
0.0.0.0         192.168.1.1     0.0.0.0         UG        0 0          0 ath0

```

10.0.0.1 is the servers address on it's virtual interface (all access I have to the server atm is through openvpn, and I use it's external DNS to reach it).

I'm not running any firewall on the machine either.

---

### Post by alamba on 2006-01-30
This is a mind boggler. I'm assuming you have both the server and the laptop on the same hub/switch. Both have the same IP range and with no firewall on the server or the laptop you should atleast be able to ping it. 

Sorry buddy i'm all out of idea's here unless anything I've stated above is not the correct picture in your setup. Correct me if i've gotten a part wrong then maybe I'll be able to figure it out.

Akshay

---

