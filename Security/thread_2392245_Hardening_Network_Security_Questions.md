---
title: "Hardening Network Security Questions"
date: 2018-05-18
forum: Security
---

### Post by sniper8752 on 2018-05-18
I was reading a post by the user, TheFu, and a few things I was curious about that was mentioned:
```
Always have both a hardware AND software firewall.
Don't trust other computers on the same LAN implicitly. One of them may have been hacked and is being used to attack all other systems.
```

1. I am running iptables on my server.  Is this not enough?  Is a hardware device recommended?  
2. How is this acted upon?  How do I protect myself internally, from these types of attacks?

---

### Post by oldos2er on 2018-05-18
This doesn't directly answer your question, but there is a mailing list devoted to this very subject: [https://lists.ubuntu.com/mailman/listinfo/ubuntu-hardened](https://lists.ubuntu.com/mailman/listinfo/ubuntu-hardened)

---

### Post by sniper8752 on 2018-05-18
> **oldos2er said:**
> This doesn't directly answer your question, but there is a mailing list devoted to this very subject: [https://lists.ubuntu.com/mailman/listinfo/ubuntu-hardened](https://lists.ubuntu.com/mailman/listinfo/ubuntu-hardened)

Awesome, thanks for sharing this!  :)

---

### Post by oldos2er on 2018-05-18
Welcome! If you learn the answer to your question, I hope you will share it here.

---

### Post by TheFu on 2018-05-24
> **sniper8752 said:**
> I was reading a post by the user, TheFu, and a few things I was curious about that was mentioned:
```
Always have both a hardware AND software firewall.
Don't trust other computers on the same LAN implicitly. One of them may have been hacked and is being used to attack all other systems.
```

1. I am running iptables on my server.  Is this not enough?  Is a hardware device recommended?  
2. How is this acted upon?  How do I protect myself internally, from these types of attacks?

I don't exactly recall the thread, but the HW firewall is a first layer to protect systems from WAN attacks.  When hardware systems fail, they fail closed. Having a separate device for that purpose adds another layer of protection to your important data.  The chances of misconfiguration for a single device is much higher than 2 systems having that failure, especially when the 2 firewalls are running different OSes with different control interfaces.  My WAN firewall is BSD-based. Most of my internal systems run Linux and either use ufw or iptables to manage firewall rules.  Just depends on the complexity needed.  All my systems use fail2ban for ssh protection to prevent brute force attacks.  Last time I checked, there were about 6500 blocked subnets for my WAN router due to past bad behavior. 
```
$ grep -c DROP foo 
6815
```

Web servers also protect what gets through against bad requests.  Same for email servers and other internal systems providing services.  Nothing I control uses default passwords, unlike the ISP's router.  Thanks to Javascript in browsers, attacks from inside can be launched by bad-actors outside just by tricking most average users into loading a webpage.  Network scanning has been seen in the wild from javascript loaded pages.  Same for UPnP enabled routers.  

For example, I bring a travel router with me when I travel to use in hotel rooms.  This adds a layer between my systems and the hotel insecurity.  I'd do the same in a dorm or any other hostile environment.  It also means I don't have to setup wifi over and over against, since the SSID/passphrase in the travel router are under my control.

When it comes to security, I want both a belt and suspenders to keep my pants up.

In general, if you don't run the network, then the organization who does can completely own your system, traffic, data. Extra steps are needed to undermine those attempts. 

Times I don't have the travel router, I use a full VPN.  For example, when I visit a restaurant and use their free wifi or when I'm doing any non-trivial data use over a cellular data connection, a full VPN is uses. Don't trust the weenie encryption that cellular providers claim, it isn't very secure.

Heck, in my house, my wifi connections are all considered "guests" and connected through the ISPs router, which is untrusted. My wifi clients use a full vpn to gain access through my router (inside the ISPs router) to my internal subnets.  Wifi protocols have enough security issues they shouldn't be trusted. The ISPs router is in bridge mode and provides my public /29 subnet to my router for use by the server network. Typical desktop systems are on a different LAN from the servers. That is also to protect them from being trivially hacked should any of the servers become compromised.

Clear as mud?

---

### Post by mohicann on 2018-06-03
May I add my 2 cents only for information. I'm very fond of all that leaked stuff concerning NSA or CIA tools that we've been overwhelmed for the last years with Snowden's, the shadow brokers' or the "vault" things. From anything I had a glance at, I couldn't find something that would make a hardware firewall over a Linux desktop one worth the pain. I may be wrong, of course, and never happened doesn't mean won't happen ever, but at least, based on the exploits I've read from these sources, the built-in Linux firewall has never been an attack surface. Hardware firewalls are otherwise, at least for older generations.

 Same as Windows, and eternelblue was a good example.

Just my 2 cents.

---

