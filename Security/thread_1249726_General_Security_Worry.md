---
title: "General Security Worry"
date: 2009-08-25
forum: Security
---

### Post by kempy1000 on 2009-08-25
Hi

Just a general security worry, im just curious how do i know if someone is attempting to get onto my system?

I noticed the log below by accident while looking at some logs on my server and got a bit conerned.

(Last 100 Lines of auth.log)

```

Aug 25 22:24:10 chimera sshd[19536]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=190.82.64.149  user=root
Aug 25 22:24:11 chimera sshd[19536]: Failed password for root from 190.82.64.149 port 54728 ssh2
Aug 25 22:24:13 chimera sshd[19538]: Invalid user music from 190.82.64.149
Aug 25 22:24:13 chimera sshd[19538]: pam_unix(sshd:auth): check pass; user unknown
Aug 25 22:24:13 chimera sshd[19538]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=190.82.64.149 
Aug 25 22:24:15 chimera sshd[19538]: Failed password for invalid user music from 190.82.64.149 port 55042 ssh2
Aug 25 22:24:17 chimera sshd[19540]: Invalid user jessie from 190.82.64.149
Aug 25 22:24:17 chimera sshd[19540]: pam_unix(sshd:auth): check pass; user unknown
Aug 25 22:24:17 chimera sshd[19540]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=190.82.64.149 
Aug 25 22:24:19 chimera sshd[19540]: Failed password for invalid user jessie from 190.82.64.149 port 55304 ssh2
Aug 25 22:24:21 chimera sshd[19542]: Invalid user notes from 190.82.64.149
Aug 25 22:24:21 chimera sshd[19542]: pam_unix(sshd:auth): check pass; user unknown
Aug 25 22:24:21 chimera sshd[19542]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=190.82.64.149 
Aug 25 22:24:23 chimera sshd[19542]: Failed password for invalid user notes from 190.82.64.149 port 55631 ssh2
Aug 25 22:24:25 chimera sshd[19544]: Invalid user turbo from 190.82.64.149
Aug 25 22:24:25 chimera sshd[19544]: pam_unix(sshd:auth): check pass; user unknown
Aug 25 22:24:25 chimera sshd[19544]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=190.82.64.149 
Aug 25 22:24:26 chimera sshd[19544]: Failed password for invalid user turbo from 190.82.64.149 port 55931 ssh2
Aug 25 22:24:29 chimera sshd[19546]: Invalid user usuario from 190.82.64.149
Aug 25 22:24:29 chimera sshd[19546]: pam_unix(sshd:auth): check pass; user unknown
Aug 25 22:24:29 chimera sshd[19546]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=190.82.64.149 
Aug 25 22:24:30 chimera sshd[19546]: Failed password for invalid user usuario from 190.82.64.149 port 56202 ssh2
Aug 25 22:24:32 chimera sshd[19548]: Invalid user spamfiltrer from 190.82.64.149
Aug 25 22:24:32 chimera sshd[19548]: pam_unix(sshd:auth): check pass; user unknown
Aug 25 22:24:32 chimera sshd[19548]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=190.82.64.149 
Aug 25 22:24:34 chimera sshd[19548]: Failed password for invalid user spamfiltrer from 190.82.64.149 port 56522 ssh2
Aug 25 22:24:36 chimera sshd[19550]: Invalid user elite from 190.82.64.149
Aug 25 22:24:36 chimera sshd[19550]: pam_unix(sshd:auth): check pass; user unknown
Aug 25 22:24:36 chimera sshd[19550]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=190.82.64.149 
Aug 25 22:24:39 chimera sshd[19550]: Failed password for invalid user elite from 190.82.64.149 port 56797 ssh2
Aug 25 22:24:41 chimera sshd[19552]: Invalid user ftpuser from 190.82.64.149
Aug 25 22:24:41 chimera sshd[19552]: pam_unix(sshd:auth): check pass; user unknown
Aug 25 22:24:41 chimera sshd[19552]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=190.82.64.149 
Aug 25 22:24:43 chimera sshd[19552]: Failed password for invalid user ftpuser from 190.82.64.149 port 57150 ssh2
Aug 25 22:24:45 chimera sshd[19554]: Invalid user radmin from 190.82.64.149
Aug 25 22:24:45 chimera sshd[19554]: pam_unix(sshd:auth): check pass; user unknown
Aug 25 22:24:45 chimera sshd[19554]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=190.82.64.149 
Aug 25 22:24:47 chimera sshd[19554]: Failed password for invalid user radmin from 190.82.64.149 port 57461 ssh2
Aug 25 22:24:49 chimera sshd[19556]: Invalid user portal from 190.82.64.149
Aug 25 22:24:49 chimera sshd[19556]: pam_unix(sshd:auth): check pass; user unknown
Aug 25 22:24:49 chimera sshd[19556]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=190.82.64.149 
Aug 25 22:24:50 chimera sshd[19556]: Failed password for invalid user portal from 190.82.64.149 port 57777 ssh2
Aug 25 22:24:52 chimera sshd[19558]: Invalid user master from 190.82.64.149
Aug 25 22:24:52 chimera sshd[19558]: pam_unix(sshd:auth): check pass; user unknown
Aug 25 22:24:52 chimera sshd[19558]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=190.82.64.149 
Aug 25 22:24:54 chimera sshd[19558]: Failed password for invalid user master from 190.82.64.149 port 58049 ssh2
Aug 25 22:24:57 chimera sshd[19560]: Invalid user sales from 190.82.64.149
Aug 25 22:24:57 chimera sshd[19560]: pam_unix(sshd:auth): check pass; user unknown
Aug 25 22:24:57 chimera sshd[19560]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=190.82.64.149 
Aug 25 22:24:59 chimera sshd[19560]: Failed password for invalid user sales from 190.82.64.149 port 58376 ssh2
Aug 25 22:25:01 chimera sshd[19562]: Invalid user util1 from 190.82.64.149
Aug 25 22:25:01 chimera sshd[19562]: pam_unix(sshd:auth): check pass; user unknown
Aug 25 22:25:01 chimera sshd[19562]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=190.82.64.149 
Aug 25 22:25:03 chimera sshd[19562]: Failed password for invalid user util1 from 190.82.64.149 port 58696 ssh2
Aug 25 22:25:05 chimera sshd[19564]: Invalid user anthony from 190.82.64.149
Aug 25 22:25:05 chimera sshd[19564]: pam_unix(sshd:auth): check pass; user unknown
Aug 25 22:25:05 chimera sshd[19564]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=190.82.64.149 
Aug 25 22:25:07 chimera sshd[19564]: Failed password for invalid user anthony from 190.82.64.149 port 59012 ssh2
Aug 25 22:25:09 chimera sshd[19566]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=190.82.64.149  user=root
Aug 25 22:25:11 chimera sshd[19566]: Failed password for root from 190.82.64.149 port 59310 ssh2
Aug 25 22:29:21 chimera sshd[19573]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=218.108.230.100  user=root
Aug 25 22:29:22 chimera sshd[19573]: Failed password for root from 218.108.230.100 port 39999 ssh2
Aug 25 22:29:25 chimera sshd[19575]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=218.108.230.100  user=root
Aug 25 22:29:28 chimera sshd[19575]: Failed password for root from 218.108.230.100 port 40249 ssh2
Aug 25 22:29:31 chimera sshd[19577]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=218.108.230.100  user=root
Aug 25 22:29:33 chimera sshd[19577]: Failed password for root from 218.108.230.100 port 40569 ssh2
Aug 25 22:29:36 chimera sshd[19579]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=218.108.230.100  user=root
Aug 25 22:29:38 chimera sshd[19579]: Failed password for root from 218.108.230.100 port 40881 ssh2
Aug 25 22:29:41 chimera sshd[19581]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=218.108.230.100  user=root
Aug 25 22:29:43 chimera sshd[19581]: Failed password for root from 218.108.230.100 port 41193 ssh2
Aug 25 22:29:46 chimera sshd[19583]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=218.108.230.100  user=root
Aug 25 22:29:48 chimera sshd[19583]: Failed password for root from 218.108.230.100 port 41481 ssh2
Aug 25 22:29:51 chimera sshd[19585]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=218.108.230.100  user=root
Aug 25 22:29:53 chimera sshd[19585]: Failed password for root from 218.108.230.100 port 41788 ssh2
Aug 25 22:29:56 chimera sshd[19587]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=218.108.230.100  user=root
Aug 25 22:29:58 chimera sshd[19587]: Failed password for root from 218.108.230.100 port 42070 ssh2
Aug 25 22:30:01 chimera sshd[19589]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=218.108.230.100  user=root
Aug 25 22:30:01 chimera CRON[19591]: pam_unix(cron:session): session opened for user root by (uid=0)
Aug 25 22:30:02 chimera CRON[19591]: pam_unix(cron:session): session closed for user root
Aug 25 22:30:03 chimera sshd[19589]: Failed password for root from 218.108.230.100 port 42357 ssh2
Aug 25 22:30:06 chimera sshd[19781]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=218.108.230.100  user=root
Aug 25 22:30:08 chimera sshd[19781]: Failed password for root from 218.108.230.100 port 42684 ssh2
Aug 25 22:30:12 chimera sshd[19783]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=218.108.230.100  user=root
Aug 25 22:30:14 chimera sshd[19783]: Failed password for root from 218.108.230.100 port 42990 ssh2
Aug 25 22:30:17 chimera sshd[19785]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=218.108.230.100  user=root
Aug 25 22:30:19 chimera sshd[19785]: Failed password for root from 218.108.230.100 port 43289 ssh2
Aug 25 22:30:22 chimera sshd[19787]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=218.108.230.100  user=root
Aug 25 22:30:24 chimera sshd[19787]: Failed password for root from 218.108.230.100 port 43588 ssh2
Aug 25 22:30:27 chimera sshd[19789]: Invalid user oracle from 218.108.230.100
Aug 25 22:30:27 chimera sshd[19789]: pam_unix(sshd:auth): check pass; user unknown
Aug 25 22:30:27 chimera sshd[19789]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=218.108.230.100 
Aug 25 22:30:28 chimera sshd[19789]: Failed password for invalid user oracle from 218.108.230.100 port 43884 ssh2
Aug 25 22:30:31 chimera sshd[19791]: Invalid user test from 218.108.230.100
Aug 25 22:30:31 chimera sshd[19791]: pam_unix(sshd:auth): check pass; user unknown
Aug 25 22:30:31 chimera sshd[19791]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=218.108.230.100 
Aug 25 22:30:34 chimera sshd[19791]: Failed password for invalid user test from 218.108.230.100 port 44155 ssh2
Aug 25 22:39:01 chimera CRON[19856]: pam_unix(cron:session): session opened for user root by (uid=0)
Aug 25 22:39:01 chimera CRON[19856]: pam_unix(cron:session): session closed for user root
Aug 25 22:40:01 chimera CRON[19931]: pam_unix(cron:session): session opened for user root by (uid=0)
Aug 25 22:40:02 chimera CRON[19931]:

```

Thanks
Chris

---

### Post by bodhi.zazen on 2009-08-25
You will find your ssh server gets hammered.

I assume you do not have the root account enabled ? I also assume you use a strong password ? keys ?

If these logs bother you , configure iptables or install denyhosts or fail2ban.

[http://bodhizazen.net/Tutorials/iptables/](http://bodhizazen.net/Tutorials/iptables/)

---

### Post by munky99999 on 2009-08-25
Looks like someone has indeed been trying to test common logins and common passwords.

I'm wondering why you have this server exposed to the net? Firewall what you dont need exposed.

---

### Post by kempy1000 on 2009-08-26
> **bodhi.zazen said:**
> You will find your ssh server gets hammered.

I assume you do not have the root account enabled ? I also assume you use a strong password ? keys ?

If these logs bother you , configure iptables or install denyhosts or fail2ban.

[http://bodhizazen.net/Tutorials/iptables/](http://bodhizazen.net/Tutorials/iptables/)

Root is disabled and my password is very complex.

> **munky99999 said:**
> Looks like someone has indeed been trying to test common logins and common passwords.

I'm wondering why you have this server exposed to the net? Firewall what you dont need exposed.

The server is exposed so that i can login via ssh from work.

I have an iptables configuration running blocking all ports I dont want open.

Thanks
Chris

---

### Post by XCan on 2009-08-26
Change the ssh port and you should notice the hammering dropping tremendously. Actually, I haven't had even one single bruteforce attempt since I change the port to a high number. You can do it by editing /etc/ssh/sshd.conf , look for the line stating the Port at the beginning of the file.

---

### Post by kempy1000 on 2009-08-26
> **XCan said:**
> Change the ssh port and you should notice the hammering dropping tremendously. Actually, I haven't had even one single bruteforce attempt since I change the port to a high number. You can do it by editing /etc/ssh/sshd.conf , look for the line stating the Port at the beginning of the file.

Thanks for the advice.

I have changed the ssh port to a random number, opened that port in my firewall and now sealed shut port 22.

Thanks
Chris

---

### Post by dfreer on 2009-08-27
Couple other things you can do:
Switch to using a private key instead password login.
Install fail2ban or something similar that bans IP's after X amount of failed logins.

---

### Post by john6of6 on 2009-10-01
Or... you can put the following lines in one of your startup scripts.

iptables -A INPUT -i eth0 -p tcp -m tcp --dport 22 -m conntrack --ctstate NEW -m recent --set --name sshscans --rsource
iptables -A INPUT -m recent --rcheck --seconds 50 --hitcount 7 --name sshscans --rsource -j DROP

After 7 failed login attempts within 50 seconds IPTABLES bans the offending IPAddress.  Course you can customize it to.  Three attempts in 2 minutes... whatever.

---

### Post by undecim on 2009-10-02
Some routers also allow you to route an external port to a different internal port. Saves you the extra command line option when using it from home

---

### Post by kevdog on 2009-10-02
Or install a port knocker that will then dynamically uncloak your port in response to single encrypted non-replayable packet.

---

