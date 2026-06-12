---
title: "Ufw and iptables"
date: 2010-08-05
forum: Server Platforms
---

### Post by dragos2 on 2010-08-05
In Lucid I have some ufw rules but I figured that I need to limit the ICMP messages that the box responds to and also limit their number. 

There are iptables rules to accomplish this but since I already have ufw rules it is safe to use iptables only for ICMP rules ?

What is the recommended solution ?

---

### Post by stlsaint on 2010-08-05
Since you are already using ufw than stick with it. Mixing rules between iptables/ufw can get confusing. Especially considering that ufw is just a frontend for iptables.

---

### Post by pipemartinm on 2010-08-05
I'd just block it with UFW. UFW has a tendency to overwrite rules you add directly using iptables. If you absolutely have to you can add the iptables statements to /etc/rc.local so they'll be applied at boot time but that can get nasty.

---

### Post by dragos2 on 2010-08-06
And how do I limit the number of ICMP's per second/minute with ufw ? From what I have
seen ufw can only block or allow ICMP's.

And as a second question: does it indirectly handle ICMP over IPV6 ?

---

### Post by kevin11951 on 2010-08-06
I don't know if anyone knows this, but you can use iptables rules in ufw...  see here:  [https://help.ubuntu.com/8.04/serverguide/C/firewall.html](https://help.ubuntu.com/8.04/serverguide/C/firewall.html)

Scroll down to *"ufw Masquerading"* to see what I mean.

---

