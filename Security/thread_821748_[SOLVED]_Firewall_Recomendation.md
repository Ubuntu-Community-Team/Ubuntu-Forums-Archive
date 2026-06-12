---
title: "[SOLVED] Firewall Recomendation?"
date: 2008-06-07
forum: Security
---

### Post by Roj on 2008-06-07
Hey everyone. I've been using Linux for a while now and have worked with iptables before. I am curious, however about whether anyone can recommend a good front-end to iptables that will allow me to do the following:

[LIST=1]
[*]Switch between using my wireless and Ethernet cards to access the internet.
[*]Use a variety of networks without having to restart/reconfigure my firewall each time (school, work, home, etc.).
[/LIST]

The reason I want to have the above two features in a firewall is I have a laptop with both a wireless and Ethernet card that I use at school, work and home. Because of this, I end up jumping from network to network throughout the day, and while I use wireless most the time, I sometimes need to connect to the ethernet instead. In each of these situations, I use DHCP to receive an IP address, so I can't just specify a specific address in iptables that I want to allow traffic into and block all others. I've worked with shorewall, firestarter, and guarddog in the past, but none of these have been able to meet my two needs listed above. Does anyone know of a front-end to iptables that will function in this type of environment without needing to be reconfigured or started and stopped each time? I know that Linux is fairly secure even without a firewall as long as its set up correctly, keep it up-to-date, and you don't leave unused ports open, but "the Penguin" isn't perfect and I feel better about having the extra layer of security.

---

### Post by Monicker on 2008-06-07
You might want to read Section 2 of this post:

[http://ubuntuforums.org/showthread.php?t=765421](http://ubuntuforums.org/showthread.php?t=765421)

---

### Post by bwhite82 on 2008-06-08
Do you have an old, spare computer laying around? It needn't have to have good specs. You could turn it into a stand-alone firewall (using Smoothwall) software and voila, problem solved.

---

### Post by Dr Small on 2008-06-08
> **Soldierboy said:**
> Do you have an old, spare computer laying around? It needn't have to have good specs. You could turn it into a stand-alone firewall (using Smoothwall) software and voila, problem solved.
If I had one, that's what I would do... and I would have it monitor bandwidth, also. ;)

---

### Post by Roj on 2008-06-08
Thanks everyone for posting so quickly, its a big help. 

> Firewall

Discussions about firewalls often are passionate (just search the Ubuntu forums). By default, Ubuntu includes a firewall, iptables, but by default nothing is engaged. This is reasonable as a default Ubuntu install opens zero ports to the outside world, so a firewall is redundant. However, installing "server software" will cause ports to open, so some people like to use a firewall as a catch-all layer to find mistakes in their configuration.

I was already aware of this, but like I said, I like the additional security of a firewall.

> A source of confusion sometimes occurs when users feel the need to be running firestarter/Guarddog for their firewall to be active. This is untrue ! Keep in mind that these applications are not firewalls, but rather configuration tools for ip tables. These applications should be run only to configure your firewall. Once configured, IP tables (the actual firewall) is active (at boot) without having to run firestarter/guarddog. firestarter will monitor traffic, but it runs as root and there are better monitoring programs, so configure you firewall, shut down firestarter/grauddog, and let IP tables do the rest . 

While I have used these tools to configure iptables for me, I have had to run them each time I connect to a different network because they each have different IP ranges. Is there any way to use one of these tools (such as firestarter) to work for both network cards on multiple networks?


> Do you have an old, spare computer laying around? It needn't have to have good specs. You could turn it into a stand-alone firewall (using Smoothwall) software and voila, problem solved.

I've also thought of this approach, and actually do have a firewall on my home network, so I'm not too worried about there. The main places I worry about is on my school and work networks.

---

### Post by Pjotr123 on 2008-06-10
You could use ufw:
[http://ubuntutip.googlepages.com/security](http://ubuntutip.googlepages.com/security)

---

### Post by Roj on 2008-06-10
> **Pjotr123 said:**
> You could use ufw:
[http://ubuntutip.googlepages.com/security](http://ubuntutip.googlepages.com/security)

I've heard of ufw and wondered if it would be a good option, but I don't know much about it. From what I can see, it looks like a short-hand way of editing iptables from the command line. Is it easy to configure and implement? Do you have to have it running all the time, or can you simply apply the rules to iptables and then not worry about it? Do you know of a wiki or tutorial on how to use ufw?

---

### Post by Roj on 2008-06-15
[Here's]("http://www.ubuntugeek.com/ufw-uncomplicated-firewall-for-ubuntu-hardy.html") a link to a page I found that explains a bit about ufw and how the rules system works in case anyone else is interested. I think this is the iptables front-end I'm going to use for my laptop. Thanks for all your help guys! :)

---

