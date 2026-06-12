---
title: "[SOLVED] SSH security"
date: 2008-07-31
forum: Security
---

### Post by jerome1232 on 2008-07-31
so I ran this today
```
cat /var/log/auth.log | grep fail | cat >auth
```
now looking at my file I have 300 KB file mostly made up of entires like this:
> Jul 31 12:53:23 lampserver sshd[5619]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=host226-148-static.34-88-b.business.telecomitalia.it 
Jul 31 12:53:27 lampserver sshd[5621]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=host226-148-static.34-88-b.business.telecomitalia.it 
Jul 31 12:53:32 lampserver sshd[5623]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=host226-148-static.34-88-b.business.telecomitalia.it 
Jul 31 12:53:36 lampserver sshd[5625]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=host226-148-static.34-88-b.business.telecomitalia.it 
Jul 31 12:53:40 lampserver sshd[5627]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=host226-148-static.34-88-b.business.telecomitalia.it 

and this:
> Jul 22 22:18:39 lampserver sshd[11599]: reverse mapping checking getaddrinfo for abts-ncr-static-050.225.160.122.airtelbroadband.in [122.160.225.50] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul 22 22:18:39 lampserver sshd[11599]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=122.160.225.50 
Jul 22 22:18:44 lampserver sshd[11601]: reverse mapping checking getaddrinfo for abts-ncr-static-050.225.160.122.airtelbroadband.in [122.160.225.50] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul 22 22:18:44 lampserver sshd[11601]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=122.160.225.50 
Jul 22 22:18:48 lampserver sshd[11603]: reverse mapping checking getaddrinfo for abts-ncr-static-050.225.160.122.airtelbroadband.in [122.160.225.50] failed - POSSIBLE BREAK-IN ATTEMPT!
Jul 22 22:18:48 lampserver sshd[11603]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=122.160.225.50 

I think I need to switch to a non standard port and disable password authentication. But before I do all that do those look like bot/malicious hits, 'cuz they do to me. (I don't recognize those ip's)

---

### Post by Joeb454 on 2008-07-31
Moved to security discussions

---

### Post by kevdog on 2008-07-31
Definitely switch to a different port to cut down on script kiddie attacks.

---

### Post by jerome1232 on 2008-07-31
Yeah I just ended up telling iptables to only allow computers on the lan connect to port 22 (I hate adding that extra -p blah) and for access outside of the lan it's my very special secret port lol.

I also turned off password authentication, must be done by a public key.

---

### Post by jerome1232 on 2008-07-31
Is there a way to config sshd_config to ban ip's for a set amount of time if it gets multiple authentication attempts like that?

---

### Post by Traumadog on 2008-08-01
You might consider running a program such as "DenyHosts" which will lockout IP addresses with excessive log in failures. If you're interested you can get more information about "DenyHosts" from their website at [http://denyhosts.sourceforge.net/](http://denyhosts.sourceforge.net/)

Best wishes, :)

Traumadog.

---

### Post by Oldsoldier2003 on 2008-08-01
Denyhosts is also available in the universe repository, use apt/aptitude/synaptic to install it.

---

### Post by hyper_ch on 2008-08-01
denyhosts will be sufficient... no need to switch port.

---

### Post by kevdog on 2008-08-01
You might find this article interesting:

[http://www.linux.com/articles/61061](http://www.linux.com/articles/61061)

and this artile:

[http://www.la-samhna.de/library/brutessh.html](http://www.la-samhna.de/library/brutessh.html)

Iptables in conjunction with the recent/update statements (ipt-recent module) works very well for most situations if you are interested in an iptables solution.

---

### Post by jerome1232 on 2008-08-01
Good reading thanks for those links, I think I will set sshd to listen on 2 ports, implement denyhosts immediately, modify Iptables to start dropping connections to one of those ports for all hosts but my desktop, and to drop packets to the second port if it starts getting hit with connections, and set my router to only forward the second port.

this is what deny hosts shows as blocked now.
> 88.79.127.99 (dialbs-088-079-127-099.static.arcor-ip.net)
60.56.225.152 (unknown)
216.53.199.228 (unknown)
200.170.203.131 (200-170-203-131.core01.spo.ifx.net.br)
218.7.13.215 (unknown)
122.160.225.50 (ABTS-NCR-Static-050.225.160.122.airtelbroadband.in)
64.22.91.225 (countryclub-investment.com)
202.104.183.2 (unknown)
219.138.207.34 (unknown)
61.25.213.198 (61-25-213-198.rev.home.ne.jp)
88.34.148.226 (host226-148-static.34-88-b.business.telecomitalia.it)
190.139.106.194 (relay.aper.net)

---

### Post by jerome1232 on 2008-08-01
Wow they missed a login by 1 character, admin1, i've been wanting to delete that account 'cuz I thought it was a bad name :)
> Jul 22 22:02:36 lampserver sshd[11217]: Invalid user admin from 122.160.225.50
Jul 22 22:02:36 lampserver sshd[11217]: pam_unix(sshd:auth): check pass; user un
known
Jul 22 22:02:37 lampserver sshd[11217]: pam_unix(sshd:auth): authentication fail
ure; logname= uid=0 euid=0 tty=ssh ruser= rhost=122.160.225.50 
Jul 22 22:02:39 lampserver sshd[11217]: Failed password for invalid user admin f
rom 122.160.225.50 port 58730 ssh2
Jul 22 22:02:42 lampserver sshd[11219]: reverse mapping checking getaddrinfo for abts-ncr-static-050.225.160.122.airtelbroadband.in [122.160.225.50] failed - POSSIBLE BREAK-IN ATTEMPT!

that address also tried rebootera and riconta, I wonder where these names come from

edit: I think some1 misstyped their ip? I just tried to ssh back to that address and it accepted alot of those names that were tried.

---

