---
title: "How can I detect or see if there is an intruder currently logged onto my server?"
date: 2014-05-23
forum: Security
---

### Post by vRanger on 2014-05-23
I'm using Ubuntu 14.04 for an email server.  (Does it make any difference if is command line only or not?)  Anyway, here are my questions, all related:
1) Is there a fool proof way that cannot be defeated by crafty intruder that will show the open connections to the server, whether it is ssh, or telnet, or html.
2) What are the connection types that would allow crafty intruder to make changes to my server that normally only root user can make.  e.g. ssh for sure, but html, others?
3) For ways that crafty intruder might have modified my system, using commands like below or other suggested commands, how can I tell if they (the commands themselves) have been modified?

So far I use:
:~$ sudo netstat -taupen
```
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       User       Inode       PID/Program name
tcp        0      0 0.0.0.0:587             0.0.0.0:*               LISTEN      0          11743       2251/master
tcp        0      0 127.0.0.1:9998          0.0.0.0:*               LISTEN      111        10116       1472/amavisd (maste
tcp        0      0 0.0.0.0:110             0.0.0.0:*               LISTEN      0          9891        1233/dovecot
tcp        0      0 127.0.0.1:10031         0.0.0.0:*               LISTEN      106        11825       2277/perl
tcp        0      0 0.0.0.0:143             0.0.0.0:*               LISTEN      0          9899        1233/dovecot
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      0          11864       2344/apache2
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      0          9159        1070/sshd
tcp        0      0 0.0.0.0:25              0.0.0.0:*               LISTEN      0          11655       2251/master
tcp        0      0 0.0.0.0:443             0.0.0.0:*               LISTEN      0          11867       2344/apache2
tcp        0      0 0.0.0.0:4190            0.0.0.0:*               LISTEN      0          9884        1233/dovecot
tcp        0      0 127.0.0.1:7777          0.0.0.0:*               LISTEN      0          302173      14797/python
tcp        0      0 0.0.0.0:993             0.0.0.0:*               LISTEN      0          9900        1233/dovecot
tcp        0      0 0.0.0.0:995             0.0.0.0:*               LISTEN      0          9892        1233/dovecot
tcp        0      0 127.0.0.1:10024         0.0.0.0:*               LISTEN      111        10115       1472/amavisd (maste
tcp        0      0 127.0.0.1:10025         0.0.0.0:*               LISTEN      0          11753       2251/master
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      105        10079       1280/mysqld
tcp        0      0 192.168.x.x:443         192.168.x.x:63477       TIME_WAIT   0          0           -
tcp        0      0 127.0.0.1:59309         127.0.0.1:3306          ESTABLISHED 0          909458      5833/auth
tcp        0      0 127.0.0.1:3306          127.0.0.1:36726         ESTABLISHED 105        1252074     1280/mysqld
tcp        0      0 127.0.0.1:3306          127.0.0.1:36965         TIME_WAIT   0          0           -
tcp        0      0 127.0.0.1:143           127.0.0.1:36943         TIME_WAIT   0          0           -
tcp        0      0 127.0.0.1:3306          127.0.0.1:36719         ESTABLISHED 105        1252061     1280/mysqld
tcp        0    280 10.x.x.x:22             10.x.x.x:60252          ESTABLISHED 0          1264577     18807/sshd: x
tcp        0      0 127.0.0.1:36719         127.0.0.1:3306          ESTABLISHED 106        1252060     4917/perl
tcp        0      0 127.0.0.1:3306          127.0.0.1:59309         ESTABLISHED 105        909459      1280/mysqld
tcp        0      0 127.0.0.1:36726         127.0.0.1:3306          ESTABLISHED 106        1252388     4966/perl
tcp6       0      0 :::22                   :::*                    LISTEN      0          9161        1070/sshd
udp        0      0 0.0.0.0:68              0.0.0.0:*                           0          9440        1038/dhclient3

```

:~$ w
```
 10:47:58 up 6 days, 18:58,  2 users,  load average: 0.06, 0.03, 0.05
USER     TTY      FROM              LOGIN@   IDLE   JCPU   PCPU WHAT
testuser pts/0    10.x.x.x          10:40    6.00s  0.24s  0.00s w

```

:~$ sudo lsof -i | grep -i established
```
COMMAND     PID        USER   FD   TYPE  DEVICE SIZE/OFF NODE NAME
mysqld     1280       mysql   37u  IPv4  909459      0t0  TCP ip6-localhost:mysql->ip6-localhost:59309 (ESTABLISHED)
mysqld     1280       mysql  166u  IPv4 1252061      0t0  TCP ip6-localhost:mysql->ip6-localhost:36719 (ESTABLISHED)
mysqld     1280       mysql  172u  IPv4 1252074      0t0  TCP ip6-localhost:mysql->ip6-localhost:36726 (ESTABLISHED)
cbpolicyd  4917 cluebringer   10u  IPv4 1252060      0t0  TCP ip6-localhost:36719->ip6-localhost:mysql (ESTABLISHED)
cbpolicyd  4966 cluebringer   10u  IPv4 1252388      0t0  TCP ip6-localhost:36726->ip6-localhost:mysql (ESTABLISHED)
auth       5833        root   12u  IPv4  909458      0t0  TCP ip6-localhost:59309->ip6-localhost:mysql (ESTABLISHED)
sshd      18807        root    3u  IPv4 1264577      0t0  TCP 10.x.x.x:ssh->10.x.x.x:60252 (ESTABLISHED)
sshd      18977           x    3u  IPv4 1264577      0t0  TCP 10.x.x.x:ssh->10.x.x.x:60252 (ESTABLISHED)

```

---

### Post by cariboo on 2014-05-23
The easiest way to check if there is anyone logged into your system is to use:

```
who
```

on my file server the output from the command looks like this:

```
who
cariboo  pts/0        2014-05-23 18:52 (192.168.0.108)
```

I access the server via ssh.

---

### Post by vRanger on 2014-05-24
Thanks.  "w" and "who" are not dissimilar functions.  Any additional comment on point 2 and 3?

---

### Post by unspawn on 2014-05-24
> **vRanger said:**
> Any additional comment on point 2 and 3? 2) Like I already said *elsewhere*: basically *any your machine provides, or whatever else means a perp is allowed to inject after gaining a foothold*.  3) The default Debian(-like) way of using debsums unfortunately requires you to modify apt-related configuration files before the event. So a distro-agnostic way could be to download a copy of any suspect package onto a known clean machine, generate a list of hashes (see md5sum or md5deep) and compare hashes ('md5sum -c') with the "victim" system. Also, if a perp doesn't clean up afterwards, there may be (logged connections in routers and switches,) entries in service and system log files, user login records, shell history, left uploads and changed ownership, hashes and MAC times of files and odd traffic behaviour as possible signs of an intrusion.

---

### Post by vRanger on 2014-05-24
unspawn, thank you for your thoughtful responses, in this thread, and here
> [http://www.linuxquestions.org/questions/linux-security-4/how-can-i-detect-or-see-if-there-is-an-intruder-currently-logged-onto-my-server-4175505944/](http://www.linuxquestions.org/questions/linux-security-4/how-can-i-detect-or-see-if-there-is-an-intruder-currently-logged-onto-my-server-4175505944/)
and here
> [https://www.linuxquestions.org/questions/linux-security-4/suspect-sever-break-in-with-user-%27sshd%27-on-ubuntu-12-04-ebury-4175505281/#post5174247](https://www.linuxquestions.org/questions/linux-security-4/suspect-sever-break-in-with-user-%27sshd%27-on-ubuntu-12-04-ebury-4175505281/#post5174247)

And just to follow up on our question, and understandable confusion, I first asked about a server I suspected had been compromised.  Now I'm starting again, and trying to gain a better understanding about how to determine where my vulnerabilities are and how to shore them up.  There are some fundamentals of the way ports work, and how they relate to services, that I do not quite understand yet.  Thanks again for taking the time to help out, it has been very useful!

---

### Post by TheFu on 2014-06-04
I have no perfect or "foolproof" answers for you.
Security is hard.  The most secure system is never connected to any network, but that usually isn't all that usable for us.

The more services that a server provides, each is now an attack vector.  Running multiple services on a single server introduces lots of server management complexities.  I prefer to limit the types of services that run on any single OS installation.  Email stuff for email servers. Web stuff on web servers. MySQL - that runs on 1 server NOWHERE NEAR THE INTERNET!!!  DNS - well, DNS gets hacked all the time - I pay a professional to run my internet-facing DNS.  In 2002, a server I ran was hacked through DNS.

Every service is locked down to which external connections are allowed.  That means the DBMS server cannot be accessed from any machine that isn't supposed to. This is all firewall rules.  Every system runs a firewall and uses fail2ban to dynamically block unwanted hack attempts quickly.  Some countries are completely blocked at the edge  - that is the nature of my clients. We don't make any money from Russia - why allow any Russian IPs access to our servers?

Plus, by moving the public port for ssh from 22 to ... er ... anything else, 99% of those attempts are stopped. No need to change the default port in the sshd config file - let the router handle the port-translations. That way it is clear when you use external or internal connections - they are on different ports.  Learn, know, love the ~/.ssh/config file sooner than later. It is amazing.

Telnet? Seriously?  Nobody should be running telnetd on any server these days. It is asking to be hacked. The same applies to plain FTP. Both of those services shouldn't have been used since about 1997.  sftp and ssh should be used.

Good, versioned backups are security tool #1. These are the most important things for security.  Why versioned? How else will you tell when a specific file was modified on a pwoned server?

Monitoring for config changes and performance changes - systems have a normal usage pattern. When that pattern changes and we don't know why, that often means something new is happening. Perhaps a hacker got in?  There are lots of monitoring tools. If you get the logs off the server ASAP, it is hard for the attacker to hide his system modifications.

So ... foolproof - no.  Every service needs to be reviewed for security considerations. Mitigation methods should be taken on a per-service basis.  Some things shouldn't ever be put on the internet. If remote users still need access, then setup a strong VPN, like openVPN. Avoid the weak/broken VPNs like PPTP.

So ... 
* block unwanted connections
* limit services
* stay current on system/application patches
* NEVER run an unsupported OS on the internet
* Monitor the logs and system performance
* Keep being paranoid. I assume every system I run can/will be hacked. People who have never been hacked don't think security is hard ... until they get hacked even when doing everything they know to protect a system.
* Backup, test restore process BEFORE YOU NEED IT!

Oh - any don't allow password-based logins for ssh - only use key-based logins except on the local network.

Here's a [story for fun about someone who wanted to have his box hacked and what the attacker did]("http://draios.com/fishing-for-hackers/") with it. Enjoy.

---

### Post by Habitual on 2014-06-04
> **TheFu said:**
> Here's a [story for fun about someone who wanted to have his box hacked and what the attacker did]("http://draios.com/fishing-for-hackers/") with it. Enjoy.

Great Stuff! and current too.
It's like Christmas every time I read one of your posts.

Thanks!

---

### Post by vRanger on 2014-06-04
Great post Fu, and thanks all!

---

