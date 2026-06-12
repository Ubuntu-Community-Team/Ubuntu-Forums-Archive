---
title: "sftp logon attempts worry?"
date: 2010-02-02
forum: Security
---

### Post by MonkeyZiggurat on 2010-02-02
I have just started running an ssh server, and I was looking through the log file after having the server running for a few days, and I noticed a lot of connection attempts by unknown users. Every day for a few hours, I'm getting hundreds of attempts to connect to my server each with a different username, all from the same IP address. Here is a short example of what I'm talking about.

<snip>-
02-02-2010 13:24:31 IP 123.30.98.50 SSH library: user unknown.
02-02-2010 13:24:31 IP 123.30.98.50 SSH library disconnected.
02-02-2010 13:24:31 IP 123.30.98.50 SSH connection attempt.
02-02-2010 13:24:35 IP 123.30.98.50 SSH appserver: user unknown.
02-02-2010 13:24:35 IP 123.30.98.50 SSH appserver disconnected.
02-02-2010 13:24:36 IP 123.30.98.50 SSH connection attempt.
02-02-2010 13:24:39 IP 123.30.98.50 SSH windowserver: user unknown.
02-02-2010 13:24:39 IP 123.30.98.50 SSH windowserver disconnected.
02-02-2010 13:24:40 IP 123.30.98.50 SSH connection attempt.
02-02-2010 13:24:43 IP 123.30.98.50 SSH enemser: user unknown.
02-02-2010 13:24:43 IP 123.30.98.50 SSH enemser disconnected.
02-02-2010 13:24:44 IP 123.30.98.50 SSH connection attempt.
02-02-2010 13:24:47 IP 123.30.98.50 SSH tkallas: user unknown.
02-02-2010 13:24:47 IP 123.30.98.50 SSH tkallas disconnected.
02-02-2010 13:24:48 IP 123.30.98.50 SSH connection attempt.
02-02-2010 13:24:51 IP 123.30.98.50 SSH gmorris: user unknown.
02-02-2010 13:24:51 IP 123.30.98.50 SSH gmorris disconnected.
02-02-2010 13:24:52 IP 123.30.98.50 SSH connection attempt.
02-02-2010 13:24:55 IP 123.30.98.50 SSH gm: user unknown.
02-02-2010 13:24:56 IP 123.30.98.50 SSH gm disconnected.
02-02-2010 13:24:56 IP 123.30.98.50 SSH connection attempt.
02-02-2010 13:24:59 IP 123.30.98.50 SSH multimedia: user unknown.
02-02-2010 13:25:00 IP 123.30.98.50 SSH multimedia disconnected.
-<snip>

My question is, should I be worried about this? I check the log every night now, and I'm adding the IPs that crop up like this to the blacklist, but this is a work fileserver, and I guess I'll need to do something if there is someone out there trying to break into a client's sftp space. What do you guys think about this?

---

### Post by FuturePilot on 2010-02-02
Setup denyhosts or fail2ban. It will automatically ban the IP after a configurable number of failed login attempts.

---

### Post by bodhi.zazen on 2010-02-02
Or learn how to use iptables or iplist ...

---

### Post by bbourdet on 2010-02-03
Hello,

I am having the same problem. I have an SSH port open for use for a few people, and I have recently seen lots of login attempts from this one address. I do not have enough knowledge about iptables to know how to block this ip address. I have disabled remote root and only have three users, and their user names are unique, they are not something like "admin" or "sales".
This person was unable to get in. Here are some of my /var/log/auth.log

```
Failed password for root from 190.7.199.58 port 8484 ssh2
Feb  3 03:39:00  sshd[12375]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=190.7.199.58  user=root
Feb  3 03:39:02  sshd[12375]: Failed password for root from 190.7.199.58 port 3490 ssh2
Feb  3 03:39:09  sshd[12377]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=190.7.199.58  user=root
Feb  3 03:39:10  sshd[12377]: Failed password for root from 190.7.199.58 port 4353 ssh2
Feb  3 03:39:17  sshd[12379]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=190.7.199.58  user=root
Feb  3 03:39:19  sshd[12379]: Failed password for root from 190.7.199.58 port 5177 ssh2
Feb  3 03:39:25  sshd[12381]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=190.7.199.58  user=root
Feb  3 03:39:26  sshd[12381]: Failed password for root from 190.7.199.58 port 6046 ssh2
Feb  3 03:39:33  sshd[12383]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=190.7.199.58  user=root
Feb  3 03:39:35  sshd[12383]: Failed password for root from 190.7.199.58 port 6855 ssh2
Feb  3 03:39:41  sshd[12386]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=190.7.199.58  user=root
Feb  3 03:39:43  sshd[12386]: Failed password for root from 190.7.199.58 port 7743 ssh2
Feb  3 03:39:50  sshd[12388]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=190.7.199.58  user=root
Feb  3 03:39:52  sshd[12388]: Failed password for root from 190.7.199.58 port 8652 ssh2
Feb  3 03:39:58  sshd[12390]: Invalid user oracle from 190.7.199.58
Feb  3 03:39:58  sshd[12390]: pam_unix(sshd:auth): check pass; user unknown
Feb  3 03:39:58  sshd[12390]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=190.7.199.58 
Feb  3 03:40:00  sshd[12390]: Failed password for invalid user oracle from 190.7.199.58 port 3706 ssh2
Feb  3 03:40:06  sshd[12392]: Invalid user test from 190.7.199.58
Feb  3 03:40:06  sshd[12392]: pam_unix(sshd:auth): check pass; user unknown
Feb  3 03:40:06  sshd[12392]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=190.7.199.58 
Feb  3 03:40:08  sshd[12392]: Failed password for invalid user test from 190.7.199.58 port 4621 ssh2
Feb  3 03:40:15  sshd[12394]: Invalid user staff from 190.7.199.58
Feb  3 03:40:15  sshd[12394]: pam_unix(sshd:auth): check pass; user unknown
Feb  3 03:40:15  sshd[12394]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=190.7.199.58 
Feb  3 03:40:17  sshd[12394]: Failed password for invalid user staff from 190.7.199.58 port 5523 ssh2
Feb  3 03:40:23  sshd[12396]: Invalid user staff from 190.7.199.58
Feb  3 03:40:23  sshd[12396]: pam_unix(sshd:auth): check pass; user unknown
Feb  3 03:40:23  sshd[12396]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=190.7.199.58 
Feb  3 03:40:26  sshd[12396]: Failed password for invalid user staff from 190.7.199.58 port 6401 ssh2
Feb  3 03:40:32  sshd[12398]: Invalid user staff from 190.7.199.58
Feb  3 03:40:32  sshd[12398]: pam_unix(sshd:auth): check pass; user unknown
Feb  3 03:40:32  sshd[12398]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=190.7.199.58 
Feb  3 03:40:34  sshd[12398]: Failed password for invalid user staff from 190.7.199.58 port 7367 ssh2
Feb  3 03:40:40  sshd[12402]: Invalid user staff from 190.7.199.58
Feb  3 03:40:40  sshd[12402]: pam_unix(sshd:auth): check pass; user unknown
Feb  3 03:40:40  sshd[12402]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=190.7.199.58 
Feb  3 03:40:42  sshd[12402]: Failed password for invalid user staff from 190.7.199.58 port 8260 ssh2
Feb  3 03:40:48  sshd[12404]: Invalid user sales from 190.7.199.58
Feb  3 03:40:48  sshd[12404]: pam_unix(sshd:auth): check pass; user unknown
Feb  3 03:40:48  sshd[12404]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=190.7.199.58 
Feb  3 03:40:50  sshd[12404]: Failed password for invalid user sales from 190.7.199.58 port 3335 ssh2
Feb  3 03:40:57  sshd[12406]: Invalid user sales from 190.7.199.58
Feb  3 03:40:57  sshd[12406]: pam_unix(sshd:auth): check pass; user unknown
Feb  3 03:40:57  sshd[12406]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=190.7.199.58 
Feb  3 03:40:59  sshd[12406]: Failed password for invalid user sales from 190.7.199.58 port 4304 ssh2
Feb  3 03:41:05  sshd[12408]: Invalid user sales from 190.7.199.58
Feb  3 03:41:05  sshd[12408]: pam_unix(sshd:auth): check pass; user unknown
Feb  3 03:41:05  sshd[12408]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=190.7.199.58 
Feb  3 03:41:07  sshd[12408]: Failed password for invalid user sales from 190.7.199.58 port 5144 ssh2
Feb  3 03:41:13  sshd[12410]: Invalid user sales from 190.7.199.58
Feb  3 03:41:13  sshd[12410]: pam_unix(sshd:auth): check pass; user unknown
Feb  3 03:41:13  sshd[12410]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=190.7.199.58 
Feb  3 03:41:16  sshd[12410]: Failed password for invalid user sales from 190.7.199.58 port 6015 ssh2
Feb  3 03:41:22  sshd[12412]: Invalid user student from 190.7.199.58
Feb  3 03:41:22  sshd[12412]: pam_unix(sshd:auth): check pass; user unknown
Feb  3 03:41:22  sshd[12412]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=190.7.199.58 
Feb  3 03:41:24  sshd[12412]: Failed password for invalid user student from 190.7.199.58 port 6878 ssh2
Feb  3 03:41:30  sshd[12414]: Invalid user student from 190.7.199.58
Feb  3 03:41:30  sshd[12414]: pam_unix(sshd:auth): check pass; user unknown
Feb  3 03:41:30  sshd[12414]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=190.7.199.58 
Feb  3 03:41:33  sshd[12414]: Failed password for invalid user student from 190.7.199.58 port 7764 ssh2
Feb  3 03:41:39  sshd[12417]: Invalid user student from 190.7.199.58
Feb  3 03:41:39  sshd[12417]: pam_unix(sshd:auth): check pass; user unknown
Feb  3 03:41:39  sshd[12417]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=190.7.199.58 
Feb  3 03:41:41  sshd[12417]: Failed password for invalid user student from 190.7.199.58 port 8664 ssh2
Feb  3 03:41:47  sshd[12419]: Invalid user student from 190.7.199.58
Feb  3 03:41:47  sshd[12419]: pam_unix(sshd:auth): check pass; user unknown
Feb  3 03:41:47  sshd[12419]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=190.7.199.58 
Feb  3 03:41:49  sshd[12419]: Failed password for invalid user student from 190.7.199.58 port 3675 ssh2
Feb  3 03:41:56  sshd[12421]: Invalid user knoppix from 190.7.199.58
Feb  3 03:41:56  sshd[12421]: pam_unix(sshd:auth): check pass; user unknown
Feb  3 03:41:56  sshd[12421]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=190.7.199.58 
Feb  3 03:41:58  sshd[12421]: Failed password for invalid user knoppix from 190.7.199.58 port 4553 ssh2
Feb  3 03:42:04  sshd[12424]: Invalid user knoppix from 190.7.199.58
Feb  3 03:42:04  sshd[12424]: pam_unix(sshd:auth): check pass; user unknown
Feb  3 03:42:04  sshd[12424]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=190.7.199.58 
Feb  3 03:42:06  sshd[12424]: Failed password for invalid user knoppix from 190.7.199.58 port 5358 ssh2
Feb  3 03:42:13  sshd[12426]: Invalid user webadmin from 190.7.199.58
Feb  3 03:42:13  sshd[12426]: pam_unix(sshd:auth): check pass; user unknown
Feb  3 03:42:13  sshd[12426]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=190.7.199.58 
Feb  3 03:42:14  sshd[12426]: Failed password for invalid user webadmin from 190.7.199.58 port 6200 ssh2
Feb  3 03:42:20  sshd[12428]: Invalid user webadmin from 190.7.199.58
Feb  3 03:42:20  sshd[12428]: pam_unix(sshd:auth): check pass; user unknown
Feb  3 03:42:20  sshd[12428]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=190.7.199.58 
Feb  3 03:42:22  sshd[12428]: Failed password for invalid user webadmin from 190.7.199.58 port 6955 ssh2
Feb  3 03:42:29  sshd[12430]: Invalid user webadmin from 190.7.199.58
Feb  3 03:42:29  sshd[12430]: pam_unix(sshd:auth): check pass; user unknown
Feb  3 03:42:29  sshd[12430]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=190.7.199.58 
Feb  3 03:42:31  sshd[12430]: Failed password for invalid user webadmin from 190.7.199.58 port 7774 ssh2
Feb  3 03:42:37  sshd[12433]: Invalid user zabbix from 190.7.199.58
Feb  3 03:42:37  sshd[12433]: pam_unix(sshd:auth): check pass; user unknown
Feb  3 03:42:37  sshd[12433]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=190.7.199.58 
Feb  3 03:42:39  sshd[12433]: Failed password for invalid user zabbix from 190.7.199.58 port 8612 ssh2
Feb  3 03:42:45  sshd[12435]: Invalid user zabbix from 190.7.199.58
Feb  3 03:42:45  sshd[12435]: pam_unix(sshd:auth): check pass; user unknown
Feb  3 03:42:45  sshd[12435]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=190.7.199.58 
Feb  3 03:42:47  sshd[12435]: Failed password for invalid user zabbix from 190.7.199.58 port 3583 ssh2
Feb  3 03:42:54  sshd[12437]: Invalid user zabbix from 190.7.199.58
Feb  3 03:42:54  sshd[12437]: pam_unix(sshd:auth): check pass; user unknown
Feb  3 03:42:54  sshd[12437]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=190.7.199.58 
Feb  3 03:42:56  sshd[12437]: Failed password for invalid user zabbix from 190.7.199.58 port 4428 ssh2
Feb  3 03:43:02  sshd[12439]: Invalid user nagios from 190.7.199.58
Feb  3 03:43:02  sshd[12439]: pam_unix(sshd:auth): check pass; user unknown
Feb  3 03:43:02  sshd[12439]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=190.7.199.58 
Feb  3 03:43:04  sshd[12439]: Failed password for invalid user nagios from 190.7.199.58 port 5289 ssh2
Feb  3 03:43:10  sshd[12441]: Invalid user nagios from 190.7.199.58
Feb  3 03:43:10  sshd[12441]: pam_unix(sshd:auth): check pass; user unknown
Feb  3 03:43:10  sshd[12441]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=190.7.199.58 
Feb  3 03:43:12  sshd[12441]: Failed password for invalid user nagios from 190.7.199.58 port 6043 ssh2
Feb  3 03:43:18  sshd[12443]: Invalid user nagios from 190.7.199.58
Feb  3 03:43:18  sshd[12443]: pam_unix(sshd:auth): check pass; user unknown
Feb  3 03:43:18  sshd[12443]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=190.7.199.58 
Feb  3 03:43:20  sshd[12443]: Failed password for invalid user nagios from 190.7.199.58 port 6828 ssh2
Feb  3 03:43:27  sshd[12445]: Invalid user nagios from 190.7.199.58
Feb  3 03:43:27  sshd[12445]: pam_unix(sshd:auth): check pass; user unknown
Feb  3 03:43:27 sshd[12445]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=190.7.199.58 
Feb  3 03:43:29  sshd[12445]: Failed password for invalid user nagios from 190.7.199.58 port 7652 ssh2
Feb  3 03:43:36  sshd[12448]: Invalid user oracle from 190.7.199.58
Feb  3 03:43:36  sshd[12448]: pam_unix(sshd:auth): check pass; user unknown
Feb  3 03:43:36  sshd[12448]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=190.7.199.58 
Feb  3 03:43:38  sshd[12448]: Failed password for invalid user oracle from 190.7.199.58 port 8509 ssh2
Feb  3 03:43:44  sshd[12450]: Invalid user oracle from 190.7.199.58
Feb  3 03:43:44  sshd[12450]: pam_unix(sshd:auth): check pass; user unknown
Feb  3 03:43:44 sshd[12450]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=190.7.199.58 
Feb  3 03:43:45 sshd[12450]: Failed password for invalid user oracle from 190.7.199.58 port 3481 ssh2
Feb  3 03:43:52  sshd[12452]: Invalid user oracle from 190.7.199.58
Feb  3 03:43:52  sshd[12452]: pam_unix(sshd:auth): check pass; user unknown
Feb  3 03:43:52  sshd[12452]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=190.7.199.58 

```

---

### Post by bodhi.zazen on 2010-02-03
If you do not know how to use iptables, and the only server you are running is ssh :

1. Disable password logins and use ssh keys.
2. Install denyhosts or fail to ban.

If you wish to learn to use a firewall, I suggest you start with ufw and progress to iptables.

[http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/](http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/)
    [http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/](http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/)
    [http://blog.bodhizazen.net/linux/firewall-ubuntu-servers/](http://blog.bodhizazen.net/linux/firewall-ubuntu-servers/)

[http://bodhizazen.net/Tutorials/iptables/](http://bodhizazen.net/Tutorials/iptables/)


If you just want a simple application to block IP addresses, look at iplist

[http://ubuntuforums.org/showthread.php?t=530183](http://ubuntuforums.org/showthread.php?t=530183)

---

### Post by JSeymour on 2010-02-03
It's a problem only if your sshd config is poor, your server or users have poor security, or your sshd has a vulnerability.  IOW: It depends.

I make a habit of listing any IP, or IP range, if necessary, that proves itself to be a pest.

I am sometimes tempted to blocklist entirely a Certain Continent and all of Two Certain Countries.  That would probably eliminate 80% or better of the knob-twisting I see on my servers.  Probably a goodly portion of the spam I receive, too.

Jim

---

### Post by bbourdet on 2010-02-03
> **bodhi.zazen said:**
> 
2. Install denyhosts or fail to ban.



Thanks! I did that, and then I tried to log in with some bogus usernames from a local machine, and it blocked it after 5 attempts. Denyhosts is really nice! Thank you so much! This is why I love linux! The community!


Tarken

---

### Post by MonkeyZiggurat on 2010-02-10
Yes, thanks for the suggestions, fail2ban works nicely.

---

