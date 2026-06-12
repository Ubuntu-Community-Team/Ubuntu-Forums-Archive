---
title: "ssh Security"
date: 2006-11-01
forum: Server Platforms
---

### Post by kverde on 2006-11-01
After reading [these tips]("http://thinkhole.org/wp/2006/10/30/five-steps-to-a-more-secure-ssh/"), I decided to think about security a bit.  I access my machine via ssh at times, but I never checked the logs.  I looked at /var/logs/auth.log and found MANY access attempts.  

I tried the #5 tip (change the port), but when I do, I get the following message when trying to log in via my new port: 
ssh_exchange_indentification: Connection closed by remote host

Any thoughts on how to change the port???

Also, any HOW TO on how to setup fail2ban on Ubuntu?  

A general look at security, and making maintaining a secure desktop easy is definitely needed.

---

### Post by Joe_CoT on 2006-11-01
> Also, any HOW TO on how to setup fail2ban on Ubuntu?

No how to, but fail2ban is available in the universe repositories, and by default blocks ssh logins after 5 attempts once installed.

> I tried the #5 tip (change the port), but when I do, I get the following message when trying to log in via my new port:
ssh_exchange_indentification: Connection closed by remote host

Odds are this means one of your firewall settings is blocking the port. You probably enabled 22 when you set up ssh, and it's blocking the new port. Check your hosts.deny, or however you decided to set it up.

---

