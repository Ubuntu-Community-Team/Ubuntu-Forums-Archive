---
title: "Getting sshd to work my computer or how do I open up a port?"
date: 2005-10-16
forum: Server Platforms
---

### Post by shodekiagari on 2005-10-16
All right. I've spent a few hours on this, I've reconfigured things, I'm at my wits end. I seriously don't feel like re-installing to get ssh working properly but I do need it...

So, what's my problem? I've got the sshd server running, it's got a pid, it works when I use the ip "localhost" when running on the computer sshd is running on, but all other ip's fail (192.168.0.5 & it's external ip). Other computers, even ones on my same network can't access it. Nmap shows the only port open to the world is ftp. I need to open another port... I removed iptables and I didn't install any other firewall. So, yeah, how do I get it to open up that darn port 22 or 443 in my case...

Anybody know? One last note: the current ListenAddress is 0.0.0.0

Thank you so much for your help.

shodekiagari

edit: sorry for the typo in the title

---

### Post by joelito on 2005-10-16
I suppose that what's happening is that traffic from sshd is going trough the loopback (lo), maybee you need to grab firestarter from universe and use the policy editor in it to set it up (well, at least I do that with vsftpd on my local network)

---

