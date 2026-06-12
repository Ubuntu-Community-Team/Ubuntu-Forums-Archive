---
title: "Multiple SSH attacks from one IP ..."
date: 2008-07-16
forum: Security
---

### Post by whitegourd on 2008-07-16
Hello.  Need some understanding of what had happend on my system.  I was checking my /var/log/auth.log file as I do on a daily basis and noticed that I've received multiple attacks from one specific IP address (from Northeastern University, China).

I am running fail2ban on Dapper 6.06.2 and have it configured so that IPs get banned after three failed attempts/time out.  It has worked w/o any problems so far.  Fail2ban is watching over ports 21,22,80.  Through the log files, it doesn't show fail2ban being shutdown during these attacks.

So my question I guess would be, "Why would more than three attacks from one IP show up while fail2ban is running".  I thought maybe the attacker sent multiple SSH requests at the same time, but then again my system should have banned the IP at the third failed request/time out.  It did finally ban it after a couple of minutes (attacks kept going till it eventually got banned).  Can someone clarify what might have happend?  Thanks.

auth.log
```

Jul 15 23:25:10 system1 sshd[4671]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=202.118.6.228  user=root
Jul 15 23:25:11 system1 sshd[4671]: fatal: Timeout before authentication for 202.118.6.228
Jul 15 23:25:15 system1 sshd[4673]: User root from 202.118.6.228 not allowed because not listed in AllowUsers
Jul 15 23:25:15 system1 sshd[4673]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=202.118.6.228  user=root
Jul 15 23:25:17 system1 sshd[4673]: fatal: Timeout before authentication for 202.118.6.228
Jul 15 23:25:20 system1 sshd[4675]: User root from 202.118.6.228 not allowed because not listed in AllowUsers
Jul 15 23:25:20 system1 sshd[4675]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=202.118.6.228  user=root
Jul 15 23:25:22 system1 sshd[4675]: Failed password for invalid user root from 202.118.6.228 port 41453 ssh2
Jul 15 23:25:22 system1 sshd[4675]: fatal: Timeout before authentication for 202.118.6.228
Jul 15 23:25:26 system1 sshd[4677]: User root from 202.118.6.228 not allowed because not listed in AllowUsers
Jul 15 23:25:26 system1 sshd[4677]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=202.118.6.228  user=root
Jul 15 23:25:27 system1 sshd[4677]: fatal: Timeout before authentication for 202.118.6.228
Jul 15 23:25:32 system1 sshd[4679]: User root from 202.118.6.228 not allowed because not listed in AllowUsers
Jul 15 23:25:32 system1 sshd[4679]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=202.118.6.228  user=root
Jul 15 23:25:33 system1 sshd[4679]: fatal: Timeout before authentication for 202.118.6.228
Jul 15 23:25:37 system1 sshd[4681]: User root from 202.118.6.228 not allowed because not listed in AllowUsers
Jul 15 23:25:37 system1 sshd[4681]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=202.118.6.228  user=root
Jul 15 23:25:39 system1 sshd[4681]: fatal: Timeout before authentication for 202.118.6.228
Jul 15 23:25:43 system1 sshd[4683]: User root from 202.118.6.228 not allowed because not listed in AllowUsers
Jul 15 23:25:43 system1 sshd[4683]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=202.118.6.228  user=root
Jul 15 23:25:44 system1 sshd[4683]: fatal: Timeout before authentication for 202.118.6.228
Jul 15 23:25:48 system1 sshd[4685]: User root from 202.118.6.228 not allowed because not listed in AllowUsers
Jul 15 23:25:48 system1 sshd[4685]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=202.118.6.228  user=root
Jul 15 23:25:50 system1 sshd[4685]: fatal: Timeout before authentication for 202.118.6.228
Jul 15 23:25:54 system1 sshd[4687]: User root from 202.118.6.228 not allowed because not listed in AllowUsers
Jul 15 23:25:54 system1 sshd[4687]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=202.118.6.228  user=root
Jul 15 23:25:55 system1 sshd[4687]: fatal: Timeout before authentication for 202.118.6.228

```

fail2ban.log
```

2008-07-15 23:27:03,391 INFO: SSH: 202.118.6.228 has 3 login failure(s). Banned.
2008-07-15 23:27:03,393 WARNING: SSH: Ban 202.118.6.228
2008-07-15 23:37:03,517 WARNING: SSH: Unban 202.118.6.228

```

---

### Post by moonpup on 2008-07-16
From your log snippets I really don't see anything wrong. It looks as though it banned the ip about 2 mins after the attempts and unbanned the ip 10 mins later.

So it must be set to parse your log file every 2 mins and automatically unban after 10 mins. I happen to use denyhosts and am not familiar with fail2ban, but based on what you provided it appears to be working fine.

Just check your fail2ban config file to see what you actually have set.

---

### Post by kevdog on 2008-07-16
If you know it to be a specific ip address every time, why dont you just insert a rule into iptables directly to block that ip address permanently?  Wouldn't that be the most direct way to deal with this problem?

---

### Post by whitegourd on 2008-07-16
Moonpup,

Fail2ban did successfully ban the offending IP, but it should have done it almost instantly right after the third failed attempt, not a couple of minutes later.  I see attacks from other offending IPs after this particular one and they do get banned right away after the third attempt (like they're suppose to), so fail2ban must be working properly here, but there has got to be a reason as to why this particular attack was delayed the instant ban.  The system is pretty much idle during this time frame and there is nothing in the cron.  I doubled checked the .conf file and it is configured correctly.

----------

Kevdog,

You're correct, I could deal with it just by adding them directly to the iptables, but I don't want to spend the time having to manually build up a list of random IP address within iptables each time I get an attack.  Most of the attacks that I get are almost always brute force attacks, so to me it's easier to run fail2ban to temporarily ban and unband the offending IP after 10 minutes.

The attacks from this IP already stopped after it got banned.  Most of the attacks that I get move on after they get banned and not get a response from my system.  I'd like to find out why this one particular attack is so different from all the other typical brute force attacks that I normally get.

---

### Post by Keeters on 2008-07-17
That is odd, I don't see any reason why it should have done that. I would offer another possible solution that i have quite a bit of experience with and never had an issue.

The following is another option right inside of iptables. It dynamically builds a list of IPs that access port 22 and then runs a check to see how many times that IP has accessed that port. If the remote host stops trying to connect for a full 10 min (600 seconds) then it removes the ban on their ip. Then the whole process starts all over again. Just make sure that you white list required IPs so they can't DOS you by spoofing their address to something important. But then again it looks like you would run into that same problem with your current set up. Anyhow, enjoy.

iptables -N SSH_BLACKLIST 
iptables -A INPUT -m state --state NEW -p tcp --dport 22 -j SSH_BLACKLIST
iptables -A SSH_BLACKLIST -m recent --set --name SSH
iptables -A SSH_BLACKLIST -m recent --update --seconds 600 --hitcount 3 --name SSH -j DROP

---

