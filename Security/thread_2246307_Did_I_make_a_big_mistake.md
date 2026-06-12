---
title: "Did I make a big mistake?"
date: 2014-09-29
forum: Security
---

### Post by donsy on 2014-09-29
Uh-oh. I hope I didn't make a big security mistake with UFW. A while back I needed ssh access to a website, and since my first command to UFW is
```
sudo ufw default deny incoming && sudo ufw default deny outgoing
``` I had to open various outgoing ports manually. One of my rules was
```
sudo ufw allow out ssh
``` which opened port 22 for outgoing traffic. I have since deleted that rule. Did I make a big mistake by allowing port 22 to be opened out? My thinking was that if port 22 was denied incoming but allowed outgoing I would be OK. Was I wrong? I'm willing to do a fresh re-install if necessary.

---

### Post by Doug S on 2014-09-29
What you did should have been fine. I do not think you made any mistake.
Do you have a specific reason for your concern? Odd log entries or something?

Disclaimer: I am good at iptables, but do not actually use UFW (which is just a front end for iptables).

Edit: Additionally, if you are not running ssh server, there is even less to worry about, as probably nothing is even listening on port 22.

---

### Post by John_Ten on 2014-09-30
Well, it says you allowed ssh outgoing connections, basically ssh bruteforce scanners are trying passwords using incoming connections, so I think it will not affect you that much. Also, if you want ssh to be more secure you can change the default port from 22, most scanners only try 22, you can also login using a key and disable passwords, but anyway that's all done on "incoming" and not outgoing.

---

### Post by Lars Noodén on 2014-09-30
+1 for key use, should you start using an SSH server.

If you do decide to open an *incoming* port for a service, the scanners will find you regardless of which port.  So make your plans around being visible if you do open a port.  As an example, I've run SSH on non-standard ports before and seen both password guessers and other service-specific probes.  Though lately, it's been only the latter at least daily.

---

### Post by The Cog on 2014-09-30
> **Lars Noodén said:**
> +1 for key use, should you start using an SSH server.
+1 to this, except I would re-word it to make it clearer for people whos first language is not English.

It is not saying you should use an SSH server. 
It is saying that **if** you do decide to use an SSH server, then you should disable passwords and use keys instead.

There is no problem in allowing SSH outbound.

---

### Post by fugu2 on 2014-10-04
[https://en.wikipedia.org/wiki/Ingress_filtering](https://en.wikipedia.org/wiki/Ingress_filtering) vs. [https://en.wikipedia.org/wiki/Egress_filtering](https://en.wikipedia.org/wiki/Egress_filtering)

---

