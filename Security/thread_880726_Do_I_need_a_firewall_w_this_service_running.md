---
title: "Do I need a firewall w/ this service running?"
date: 2008-08-05
forum: Security
---

### Post by ZeldaFan on 2008-08-05
If I use bitorrents or other service that involve me opening up ports on my computer, do I or should I run a firewall? Right now my firewall is disabled (sudo ufw disable) but I'm not sure if I need to run it or not. Should I only run it when I have a bitorrent client open? Also, how do I configure the ports, it's kind of confusing. Right now, when I use azureus, I have no problems because all my ports are open I think. Can I allow for specific services to access ports as opposed to just opening ports?

---

### Post by hyper_ch on 2008-08-05
well, do you want to block certain ips that may access your torrent client or other services? If so, then you want to install a firewall... or are you behind a router already? If so, you shoule configure that one.

---

### Post by ZeldaFan on 2008-08-05
I am behind a router, so I guess I'll just configure its firewall instead. However, before when forwarding my ports for bitorrent, I had to constantly update my IP address because it was dynamic. However, now, I never have update my IP address in my router settings, even though I am still using DHCP. Why is that? Does that indicate that my firewall is ineffective?

---

### Post by hyper_ch on 2008-08-05
dunno... I operate with static ips only (or almost only)

---

### Post by molotov00 on 2008-08-05
"I had to constantly update my IP address because it was dynamic"

That makes no sense. Clarify.

---

### Post by ZeldaFan on 2008-08-05
On my router, when you forward a port, you need to specify the IP address to open the port on. Thus, because I have a dynamic IP address (using DHCP), I need to change the router settings for the forwarded port to the IP address my computer is using at that moment.

---

### Post by zo934 on 2008-08-06
HEy HOw do I put the firewall back to default, 
I was messing with it lastnight, trying to configure firewall in Ubuntu, 
I think I set it back to default but want to be positive. Now when I try and login, I can login, but all I get is a blank screen, and i have to power down my machine, could I have changed something in the firewall to cause this? Help please

---

### Post by hyper_ch on 2008-08-06
make iptable forget all rules ;) I'm sure google has an answer for that.

---

### Post by zo934 on 2008-08-06
I dont understand. I cant even login now, when I login I get a 
blank screen. I was trying to configure firewall lastnight.
Would denying a port have anything to do with loggin in

---

### Post by zeronothing on 2008-08-06
> **ZeldaFan said:**
> On my router, when you forward a port, you need to specify the IP address to open the port on. Thus, because I have a dynamic IP address (using DHCP), I need to change the router settings for the forwarded port to the IP address my computer is using at that moment.

all you would need to do is make your ip address on you machine static. if you are dealing with your own router, it would be better to (on you machine) set a ip static. this way you wouldn't have to keep changing the ip address within the router. depending on what brand of router you have, sometime you can set a ip address based on a MAC address. so whenever you request and IP address from your router (dhcp server I assume), based on you MAC address your router will hand you PC that specific IP address. I have this set on my router (netgear).

---

### Post by zo934 on 2008-08-06
Im new to this whole thing, dont understand much linux language.
I was testing out the firewall so I blocked a certain port then allowed it, then deleted the rule, it said rule added, does this mean my firewall went back to default, thats what I want cause I dont want to block or allow ports if I dont know what they are, Im reinstalling Ubuntu right now, should this make the firewall go back to default?

---

### Post by barney385 on 2008-08-06
> **zo934 said:**
> Im new to this whole thing, dont understand much linux language.
I was testing out the firewall so I blocked a certain port then allowed it, then deleted the rule, it said rule added, does this mean my firewall went back to default, thats what I want cause I dont want to block or allow ports if I dont know what they are, Im reinstalling Ubuntu right now, should this make the firewall go back to default?

I'd like to know how to default iptables also...


:)


good question

---

### Post by ZeldaFan on 2008-08-06
> all you would need to do is make your ip address on you machine static. if you are dealing with your own router, it would be better to (on you machine) set a ip static. this way you wouldn't have to keep changing the ip address within the router. depending on what brand of router you have, sometime you can set a ip address based on a MAC address. so whenever you request and IP address from your router (dhcp server I assume), based on you MAC address your router will hand you PC that specific IP address. I have this set on my router (netgear).

Is that necessarily legal? I've read some where in Comcast's terms contract that you are not allowed to change/control the IP address my computer uses. I've heard that this IP address is not the true IP address that I am using, just like one that my router gives me. I was always confused about this, so I never went the static IP route.

---

### Post by hyper_ch on 2008-08-06
zelda:

If you have a router then yuo obtain from comcast an IP address - the public one - and that one you cannot change. However as you use a router you have an internal network and in there you can assign IP addresses as you want.

192.168.0.x is a private net that's normally used for lans.
10.0.0.x is what I prefer. So my router has 10.0.0.1, my computer has statically assigned 10.0.0.5  and on my open wifi I let other join from 10.0.0.100 onwards by dhcp.

So all important services for me (like ssh) I route from the router to 10.0.0.5

---

