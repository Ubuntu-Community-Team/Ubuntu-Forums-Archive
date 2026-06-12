---
title: "fail2ban trickery?"
date: 2012-04-06
forum: Server Platforms
---

### Post by webservervideos on 2012-04-06
I was interested in using fail2ban, never tried it. Interested in knowing if I can do some trickery to prevent hackers with it.  I use a non standard port for my ssh...and have port 22 closed.  I think it would be nice to have fail2ban listen at port 22 and any ip attempting a connection should be blocked.  but is that possible? I think fail2ban only looks at logs...perhaps open the port 22 and add logging of anyone attempting to reach it?  any ideas?

---

### Post by rubylaser on 2012-04-06
I'm not sure why you'd want to open a port if you're not using it.  Fail2ban's SSH rule will block offenders with too many failed SSH attempts. Just setup Fail2Ban on your non standard port instead.

---

### Post by webservervideos on 2012-04-06
> **rubylaser said:**
> I'm not sure why you'd want to open a port if you're not using it.  Fail2ban's SSH rule will block offenders with too many failed SSH attempts. Just setup Fail2Ban on your non standard port instead.

 because I want to get ips blocked from hackers. A non standard port has less hackers hitting it.  if someone comes to port 22 and I am using something else for ssh, then I know 100% that is a hacker and I can then prevent them from running scripts on any port, hitting my web apps, brute forcing, etc.  adding listening at ports or attempts at ports I am not using can prevent hacks elsewhere rather quickly. Script kiddies use standard ports a lot. I want to protect my server.  ignoring attempts does not help, I want to be proactive.  And on a virtual host machine I can immediately protect all server virtual machines from dns, mail, webservers, mysql, backup servers, etc..  a simple and elegant solution, just not sure if it can be done with fail2ban.

---

### Post by JohnMazurka on 2012-04-06
The above post is correct. Fail2ban monitors logs and runs every minute to look for defined dodgy occurrences. So it'll need logs to be written for it to read.
You could try portsentry, that monitors ports.

---

### Post by rubylaser on 2012-04-06
> **webservervideos said:**
> because I want to get ips blocked from hackers. A non standard port has less hackers hitting it.  if someone comes to port 22 and I am using something else for ssh, then I know 100% that is a hacker and I can then prevent them from running scripts on any port, hitting my web apps, brute forcing, etc.  adding listening at ports or attempts at ports I am not using can prevent hacks elsewhere rather quickly. Script kiddies use standard ports a lot. I want to protect my server.  ignoring attempts does not help, I want to be proactive.  And on a virtual host machine I can immediately protect all server virtual machines from dns, mail, webservers, mysql, backup servers, etc..  a simple and elegant solution, just not sure if it can be done with fail2ban.

Sounds like you've got a potential solution from JohnMazurkaidea. Opening unnecessary ports is not a good practice, and allows one more potential access point to your box.  I fail to see how not opening a port is not proactive, but sounds like you can script up PortSentry with iptables to do what you want. Personally, I don't ever expose SSH to the internet, it's only available via VPN connection, and I still run fail2ban on my SSH port on the LAN.

---

### Post by webservervideos on 2012-04-06
actually it was much easier than I thought...a simple drop port command with a log command in it..
boom...someone hits it, its logged, its picked up by fail2ban, done.

simple, elegant, works great.

---

