---
title: "How to secure open port for a particular program?"
date: 2014-03-06
forum: Security
---

### Post by Kestreln8144 on 2014-03-06
Hello everyone. I'm learning my way around network and Linux security, and I would like advice for this situation:

I'm setting up my iptables firewall, and there is a particular application I run that needs to accept incoming tcp connections as well as udp. I've read that allowing incoming connections for tcp is an insecurity (possibly udp too, but I still don't know much about udp). I know I can restrict incoming requests to certain IPs, but unfortunately in this situation I won't be able to know what they are.

The only idea I have is: I could open a particular port for this program *only,* restrict the usage of this port to this program, then secure the program with AppArmor. This way, any incoming connection would only be able to connect to that program, and even if it's insecure AppArmor should limit any damage.

But I've yet to learn how to do this. Is it possible to restrict the usage of a port to a particular program?

What are your thoughts? You security gurus no doubt know a lot more than I do. How can I go about securing an open port that accepts incoming connections?

---

### Post by CharlesA on 2014-03-06
What program?

See here:
[http://bodhizazen.net/Tutorials/iptables](http://bodhizazen.net/Tutorials/iptables)

---

### Post by Empire-Phoenix on 2014-03-07
Well if you need access from the internet to a potentially unsecure application, the usual way is to use a vpn, then allow only from the vpn access to the unsecure application. That way if the vpn is secure there are no open vulnerabilities to the internet.

---

### Post by 3rdalbum on 2014-03-07
> **Kestreln8144 said:**
> 
I'm setting up my iptables firewall, and there is a particular application I run that needs to accept incoming tcp connections as well as udp. I've read that allowing incoming connections for tcp is an insecurity

It's not really an "insecurity", it's a risk. An insecurity is an insecurity, a risk can be managed.

> The only idea I have is: I could open a particular port for this program *only,* restrict the usage of this port to this program, then secure the program with AppArmor. This way, any incoming connection would only be able to connect to that program, and even if it's insecure AppArmor should limit any damage.

If the program is the only program listening for incoming connections on that port, then it will be the only one receiving the data. If the program is not running, then no incoming connection will ever be answered and you will receive no data. Even if you have programs listening on port 502, 503, 504, 506 and 507; they will still not receive any data destined for port 505. Do you understand what I mean? If you want to restrict incoming connections on that port to one particular program, then simply don't have any other programs listening on that port.

Securing the service with AppArmour is a great way of limiting risk. You do need to know exactly what that program does, however, otherwise you'll either make the AppArmour profile too loose or so restrictive that the program won't work properly.

---

### Post by Kestreln8144 on 2014-03-07
> **CharlesA said:**
> What program?
Retroshare: [http://retroshare.sourceforge.net/](http://retroshare.sourceforge.net/)
Wiki (needs work): [http://retroshare.sourceforge.net/wiki/index.php/Main_Page](http://retroshare.sourceforge.net/wiki/index.php/Main_Page)

> **Empire-Phoenix said:**
> Well if you need access from the internet to a potentially unsecure application, the usual way is to use a vpn, then allow only from the vpn access to the unsecure application. That way if the vpn is secure there are no open vulnerabilities to the internet.
I am not the one who will be connecting to this program. It will be accepting connects to addresses that I cannot know beforehand. The risk here is that this program may have flaws, and an unknown attacker might utilize vulnerabilities to access my PC or otherwise cause problems. I want to secure the program from the rest of my system (with AA), and restrict the use of the port to that program alone.

> **3rdalbum said:**
> Do you understand what I mean? If you want to restrict incoming connections on that port to one particular program, then simply don't have any other programs listening on that port.
Yes, I understand this. But what worries me—and maybe I just don't understand enough about all of this—is that other applications on my system might utilize that port without my knowing (unless I look). I guess a better question is how can I know what programs are using what ports, and make sure this doesn't happen?

> **3rdalbum said:**
> Securing the service with AppArmour is a great way of limiting risk. You do need to know exactly what that program does, however, otherwise you'll either make the AppArmour profile too loose or so restrictive that the program won't work properly.
Yeah, I've begun reading AA's documentation, and it looks like quite the learning curve. I'm not expecting to learn this overnight, but hopefully I can work something out that will work well enough.

---

### Post by ant2ne on 2014-03-10
open the port on your server but only when the source is your workstations IP.

something like
iptables -A INPUT -s YOURIP -p tcp --dport 22 -j ACCEPT

---

