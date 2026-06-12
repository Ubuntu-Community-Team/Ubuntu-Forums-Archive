---
title: "stop bruteforcing"
date: 2006-01-27
forum: Server Platforms
---

### Post by Peter76 on 2006-01-27
Is there a way to blacklist the ip from someone bruteforcing you? This afternoon someone |( 213.50.3.6 ) was bruteforcing me for half an hour or so. I'm looking for something that grabs the ip after about say 5 login attempts and blocks it.

---

### Post by LordHunter317 on 2006-01-27
You can, but there's no point.  Set a strong password (or use keypairs if possible) and then ignore them.

---

### Post by az on 2006-01-27
because they will just change their ip?

---

### Post by LordHunter317 on 2006-01-27
Because the attacks are nieve and they're not going to go away, plus any other measure doesn't fix your real problem.

---

### Post by Horndog on 2006-01-27
I have no idea how this works but here is the link anyway

[http://fail2ban.sourceforge.net/]("http://fail2ban.sourceforge.net/")

---

### Post by Oceola on 2006-01-27
If you use nettools to see "who is" you may get a system address and an email or even phone in somecases. If it's continuous you may be able to write an email to the system administrator.
Also try a trace first to make sure the IP is actually the one you think it is.

---

### Post by Peter76 on 2006-01-27
Hey Horndog, thanks, that is exactly what I'm looking for

---

### Post by Horndog on 2006-01-27
[QUOTE=Peter76]Hey Horndog, thanks, that is exactly what I'm looking for[/QUOTE]

Glad to help. Please report back on how it works.

---

### Post by Peter76 on 2006-01-28
I will Horndog; but at the moment packages.debian is down:-( I'll post when I get it; Went through all the doc stuff; and it looks very good

---

### Post by curtis on 2006-01-28
APF and BFD may help good from Rfx-networks.
I know it is used by 95% of cPanel hosts.
APF == Active policy firewall
BFD == Brute force defender, it ties into APF
Hopefully they help as well :D

---

### Post by Peter76 on 2006-01-28
Hey Curtis, this looks good as well, I'll dive into it; although for me it needs to work with the ipmasq package which does my firewalling and routing now, but thanks for the tip and I think all these tips are very usefull for other ubuntu users as well.

website = [www.rfxnetworks.com](www.rfxnetworks.com)

---

### Post by anthro398 on 2006-02-01
I wrote some iptable firewall rules and use hosts.deny and hosts.allow as a second line of defense.  No one outside of the 10 or so ip addresses I've specified in my iptables should ever even get a response from my machine and if iptables somehow failed they'd still never get an ssh prompt if they aren't in my hosts.allow file.  Iptables isn't trivial but it was very interesting to work on. The hosts.allow and deny files are simple to use.  Just use a search engine and I'm sure you'll find the same resources I used.

---

### Post by devnulljp on 2006-09-06
Add their IP to /etc/hosts.deny
If you get lots of that kind of traffic (don't we all?)try denyhosts - it's not in the repositories so you'll have to grab source and install. It's a python app that runs as a daemon and adds IPs that try to get in but fail to hosts.deny automatically.
There's a good howto here: [http://www.howtoforge.com/preventing_ssh_dictionary_attacks_with_denyhosts](http://www.howtoforge.com/preventing_ssh_dictionary_attacks_with_denyhosts)
Latest version is on sourceforge.

> **Peter76 said:**
> Is there a way to blacklist the ip from someone bruteforcing you? This afternoon someone |( 213.50.3.6 ) was bruteforcing me for half an hour or so. I'm looking for something that grabs the ip after about say 5 login attempts and blocks it.

---

