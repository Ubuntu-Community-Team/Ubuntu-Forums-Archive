---
title: "Block multiple ssh login attempts"
date: 2011-03-22
forum: Security
---

### Post by pcarlos853 on 2011-03-22
Hello, I am running a ubuntu server 10.10 with SSH, and OpenVPN. I use it mainly for the VPN, but I have seen log in attempts such as: > Mar 22 14:52:53 UbuntuSvr sshd[2397]: Invalid user support from 85.217.190.69
Mar 22 14:52:55 UbuntuSvr sshd[2399]: Invalid user student from 85.217.190.69
Mar 22 14:52:57 UbuntuSvr sshd[2401]: Invalid user transfer from 85.217.190.69
Mar 22 14:52:59 UbuntuSvr sshd[2403]: Invalid user user from 85.217.190.69
Mar 22 14:53:00 UbuntuSvr sshd[2405]: Invalid user public from 85.217.190.69
Mar 22 14:53:02 UbuntuSvr sshd[2407]: Invalid user info from 85.217.190.69
Mar 22 14:53:05 UbuntuSvr sshd[2409]: Invalid user oscar from 85.217.190.69
Mar 22 14:53:09 UbuntuSvr sshd[2411]: Invalid user record from 85.217.190.69
Is it possible to make it so when some one has tried logging in 5 times with an invalid user/pass that the ip is banned for 10 minutes? I have password auth set to no and am using keys.

Thanks!

---

### Post by BkkBonanza on 2011-03-22
You may want to look at [fail2ban]("https://help.ubuntu.com/community/Fail2ban") which is quite popular. It can scan log files and apply ip blocks.

Another common tactic is to change ssh to a random high port instead of 22. While this is just making it more obscure it does generally get rid of all these noisy login attempts as it's too much work for most hackers to scan all ports to find out where to attempt login.

---

### Post by pcarlos853 on 2011-03-23
That worked perfectly! Thanks for you assistance!

---

### Post by Lars Noodén on 2011-03-23
Another way besides [fail2ban](http://packages.ubuntu.com/maverick/fail2ban) would be to use [iptables](http://www.debian-administration.org/articles/187) to limit the connections.

---

### Post by bodhi.zazen on 2011-03-23
> **Lars Noodén said:**
> Another way besides [fail2ban](http://packages.ubuntu.com/maverick/fail2ban) would be to use [iptables](http://www.debian-administration.org/articles/187) to limit the connections.

fail2ban works well, but has it's own set of problems and can introduce vulnerabilities.

Learning iptables takes a little time, but so does learning fail2ban ;)

In general if you use keys, and disable password, you can ignore these things, and turn off logging of these attempts. 

If you really feel the need you can add a few "simple" rules to iptables.

---

### Post by pcarlos853 on 2011-03-23
The reason I wanted to do this was to make my server more secure, if it can introduce vulnerabilities then I will have to rethink using it. I do use keys and have disabled password auth.

Thanks

---

### Post by bodhi.zazen on 2011-03-23
> **pcarlos853 said:**
> The reason I wanted to do this was to make my server more secure, if it can introduce vulnerabilities then I will have to rethink using it. I do use keys and have disabled password auth.

Thanks

IMO, after running ssh servers for many years, keys + disable password authentication is all you need.

What you are seeing in the logs are so called "script kiddies" and as :

1. Most of those users probably do not exist on your system.
2. You disabled passwords.
3. The do not have a key ...

fail2ban does not, IMO, does not significantly increase security.

Blocking these attempts will quiet the logs (so will disabling logging).

As I said, if you wish, simply add a few rules for iptables.

I would use fail2ban only if you had to use password authentication (for ssh or ftp or http) for some reason. In that event, it may help, but keep in mind:

fail2ban and denyhosts introduce their own vulnerabilities, including dos (if your ip is spoofed your server will block legitimate traffic).

---

### Post by njdove on 2011-03-23
> **pcarlos853 said:**
> The reason I wanted to do this was to make my server more secure, if it can introduce vulnerabilities then I will have to rethink using it. I do use keys and have disabled password auth.

Thanks


That mitigates brute force attempts.

Depending on the nature of the server, a firewall may be good practice any how. "ufw" creates iptables rules but has a lower bar to entry. To enable ufw run "[FONT=Courier New]sudo ufw enable[/FONT]". To rate-limit SSH, run "[FONT=Courier New]sudo ufw limit ssh/tcp[/FONT]". Note that ufw defaults to denying incoming traffic so you'll need to explicitly allow ports that your server requires (e.g. "[FONT=Courier New]sudo ufw allow in 'Apache Full'[/FONT]"). See also: man ufw, [https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)

---

