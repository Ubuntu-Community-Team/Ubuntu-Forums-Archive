---
title: "Remote login prevention"
date: 2006-08-30
forum: Server Platforms
---

### Post by bPawn on 2006-08-30
I am looking for something that will prevent outgoing connection attempts from my server to the port 22 (or other remote login ports)  of other machines. However, I would like to be able to connect to my server using ssh (incoming). Moreover a way to reverse it if necessary.

The deal is that my network adminstrator disabled my network access because "My machine massivly attempted to connect to other machines at port 22 using random 'high' ports" He instructed me to look for suspicious daemons running, however I found nothing of "interest".

any ideas?

---

### Post by frodon on 2006-08-30
To limit outgoing traffic on port 22, use these iptables rules (you can cut and paste them in a terminal to set it) :```
iptables -A OUTPUT -p tcp -m tcp --dport 22 -j DROP
iptables -A OUTPUT -p udp -m udp --dport 22 -j DROP
```However there a problem somewhere, your computer is not supposed act like that.

---

### Post by bPawn on 2006-08-30
That was quick, thanks

It complained about -J (not such option) so I put -j:-k

---

### Post by frodon on 2006-08-30
Sorry it was a typo, indeed it's "-j" and not "-J"

---

### Post by sktx on 2006-09-16
> **bPawn said:**
> The deal is that my network adminstrator disabled my network access because "My machine massivly attempted to connect to other machines at port 22 using random 'high' ports" He instructed me to look for suspicious daemons running, however I found nothing of "interest".

Wow.  If you can't find any reason why your box should be scanning other machines for open ports, then iptables isn't a solution.  Granted, it might function as a bandaid, but if your machine's been compromised... If, on the chance that someone's gotten a login to your box,  you can't reasonably trust any of your programs, security software especially, to function as it should.  You can rip through your logs, keep an eye on netstat, tweak around with snort, etc... but I would recommend a wipe-and-reinstall.

---

### Post by MrHorus on 2006-09-16
> **frodon said:**
> To limit outgoing traffic on port 22, use these iptables rules (you can cut and paste them in a terminal to set it) :```
iptables -A OUTPUT -p tcp -m tcp --dport 22 -j DROP
iptables -A OUTPUT -p udp -m udp --dport 22 -j DROP
```However there a problem somewhere, your computer is not supposed act like that.

And why not?

The computer will do whatever you want it to do and it's extremely common for corporate firewalls to limit outgoing connections on ports like that for security and polity reasons.

---

### Post by sktx on 2006-09-16
> **MrHorus said:**
> The computer will do whatever you want it to do and it's extremely common for corporate firewalls to limit outgoing connections on ports like that for security and polity reasons.

"Whatever you want it to do," as in randomly scanning remote hosts without your prior knowledge?

---

