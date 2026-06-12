---
title: "Need help with firewall (iptables)"
date: 2007-05-01
forum: Server Platforms
---

### Post by anil_robo on 2007-05-01
Despite being technologically challenged, I'm running Ubuntu on a server with apache and SSH. I'm behind a home router, and have opened port 22 (ssh) to allow incoming connections from outside for remote management of my server.  I was reading the server logs recently (for the first time) and I saw many failed password attempts via ssh2 in the file /var/log/auth.log (***dictionary-based ssh attacks?***) . I'm afraid someone might crack my password one day, so I want to fortify my Ubuntu server with a firewall besides the router firewall.  I followed many tutorials from the internet, but they are deficient in some way or another, and that's why I am writing to the Ubuntu community once again.

Here's what I'd like to do:[LIST]
[*]The firewall should start at bootup, and I should not be required to enter a password
[*]The firewall should recognize three failed login attempts within three minutes via ssh, and should ban that IP address for three hours
[*]In addition to banning that IP for three hours, the firewall should also append that IP address to hosts.deny, AND a text-file called badguys.txt so that I can conveniently view that file later
[*]Which ports to open: http(80), https(443) and ssh(22) for sure. Don't know if I'm using any other ports.[/LIST]Thanks for your help in advance :popcorn:

---

### Post by twistedtwig on 2007-05-03
have not yet installed it but I would think this is at least part of your solution "fail2ban"  blocks IPs after bad attempts I blieve.

---

### Post by anil_robo on 2007-05-03
I now have [denyhosts]("http://denyhosts.sourceforge.net/") running on my server, and it has started catching the culprits already! I'll write a detailed how-to for this soon and share with ubuntu community. Thanks! :)

---

