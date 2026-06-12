---
title: "Large btmp file in /var/logs"
date: 2015-06-25
forum: Security
---

### Post by Aucun.AuServ on 2015-06-25
I've looked at the log and I see a ton of failed logins. IPs are from US and China mostly, the US ones seem like bots trying common account names and passwords; however, the ones from China are all focused on the root account with massive amount of tries. I have basic firewall rules disallowing every port but the ones I use for teamspeak and ssh. What is the best actions to take here? I was thinking on limiting ssh access to a specific IP starting number, but I'm not sure if that is good enough.

---

### Post by Lars Noodén on 2015-06-25
Welcome.

Make sure that you have **PermitRootLogin** set to "no" in your SSH server's configuration, and requiring keys for the other accounts is highly recommended.  You could also try rate limiting in iptables / UFW  for the connections that you do allow, but if the attacks are distributed among several hosts then that won't help much.  If the brunt of the attacks are from one or two networks, and you don't need those networks yourself, then block them. e.g.120.0.0.0/8  On my router, I blocked several whole Chinese networks that were the sources of the attacks and things quieted down for me for the most part.

---

### Post by Aucun.AuServ on 2015-06-25
I set rootlogin to no in the config and restarted ssh, and I can't login as root with the correct password, that's good. I also added the common IPs to ufw deny over port 22 so hopefully it calms down. The only problem I have now is that I can't clean the 200mb log file. using "sudo > btmp.1" gives me permission denied and so does "sudo cat /dev/null > btmp.1", any ideas?

---

