---
title: "Help with Ubuntu server 12.04 for penetration testing"
date: 2013-10-22
forum: Security
---

### Post by skorpinok on 2013-10-22
Hi,  I've installed ubuntu 12.04 server on virtualbox,( during the install i chose openssh & lamp server & no updates. )i would like to know how to ill configure this server to do a penetration test against it ? like disabling all security feautures, keep all ports open. i've installed mutilidae a vunerable web app inside server & i use kali linux to conduct some test.  "not for illegal purposes but for practice ", if u got any suggestions please let me know.


Regards
Skorpinok

---

### Post by SeijiSensei on 2013-10-22
First, unless you're on a local network with a lot of competent hackers, I don't see much point to local penetration testing.  I'd be much more concerned with external threats.  If you have access to a remote computer running Linux outside your network, run your tests from there.  I recommend starting with **[nmap]("http://insecure.org/nmap")** which is available in every major distribution's repositories.  It's a highly sophisticated scanner with a lot of options.

---

### Post by Lars Noodén on 2013-10-22
I would have recommended "Damn Vulnerable Linux" instead but that is gone.  Instead you'll have to add and intentionally misconfigure services if you want to go that route.  I'd advise against it, especially if the machine is connected to the net in any way.  

+1 for nmap, if you want a GUI then there is Zenmap as a front-end

There is tcpdump to monitor traffic to and from the machine.  If you want a GUI for network monitoring, there is Wireshark.  

Rather than making a secure machine into an insecure one and risking a mess, maybe just put it out on the net in a secure state but with Snort or another IDS running.  Watch the fun.

---

### Post by skorpinok on 2013-10-22
> **Lars Noodén said:**
> I would have recommended "Damn Vulnerable Linux" instead but that is gone.  Instead you'll have to add and intentionally misconfigure services if you want to go that route.  I'd advise against it, especially if the machine is connected to the net in any way.  

+1 for nmap, if you want a GUI then there is Zenmap as a front-end

There is tcpdump to monitor traffic to and from the machine.  If you want a GUI for network monitoring, there is Wireshark.  

Rather than making a secure machine into an insecure one and risking a mess, maybe just put it out on the net in a secure state but with Snort or another IDS running.  Watch the fun.
 
Thanks. am not connected to net as its in **sandbox environment** I would like  to **add**  **intentionally misconfigure services** & i have kali linux as a attacker machine. 
apart from turning firewall off what else can be done..?

---

### Post by SeijiSensei on 2013-10-22
Run nmap against the machine's local address for starters.

---

