---
title: "auth.log CRON spam"
date: 2010-07-24
forum: Server Platforms
---

### Post by ubila on 2010-07-24
Hey all, 
Im getting ALOT of spam in my auth.log from CRONTAB's run by root user.
I only have 2 known CRONTABs setup for root user and they run at around 10pm at night.... Can anyone explain what this activity means??
 

Jul 25 07:20:01 server1 CRON[19547]: pam_unix(cron:session): session opened for user root by (uid=0)
Jul 25 07:20:02 server1 CRON[19547]: pam_unix(cron:session): session closed for user root
Jul 25 07:30:01 server1 CRON[19655]: pam_unix(cron:session): session opened for user root by (uid=0)
Jul 25 07:30:01 server1 CRON[19655]: pam_unix(cron:session): session closed for user root
Jul 25 07:39:01 server1 CRON[19761]: pam_unix(cron:session): session opened for user root by (uid=0)
Jul 25 07:39:01 server1 CRON[19761]: pam_unix(cron:session): session closed for user root
Jul 25 07:40:01 server1 CRON[19839]: pam_unix(cron:session): session opened for user root by (uid=0)
Jul 25 07:40:01 server1 CRON[19839]: pam_unix(cron:session): session closed for user root
Jul 25 07:50:01 server1 CRON[19948]: pam_unix(cron:session): session opened for user root by (uid=0)
Jul 25 07:50:01 server1 CRON[19948]: pam_unix(cron:session): session closed for user root
Jul 25 08:00:01 server1 CRON[20058]: pam_unix(cron:session): session opened for user root by (uid=0)
Jul 25 08:00:02 server1 CRON[20058]: pam_unix(cron:session): session closed for user root
Jul 25 08:09:01 server1 CRON[20164]: pam_unix(cron:session): session opened for user root by (uid=0)
Jul 25 08:09:01 server1 CRON[20164]: pam_unix(cron:session): session closed for user root

 
Has someone gained access to my root account and added a bunch of Crontabs?
How can i check this?
 
Cheers

---

### Post by ubila on 2010-07-24
Im also getting a bunch of failed password attempts
 
Jul 25 10:49:45 server1 sshd[22550]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=b156232.ppp.asahi-net.or.jp  user=root
Jul 25 10:49:47 server1 sshd[22550]: Failed password for root from 202.213.156.232 port 48278 ssh2
Jul 25 10:49:49 server1 sshd[22552]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=b156232.ppp.asahi-net.or.jp  user=root
Jul 25 10:49:51 server1 sshd[22552]: Failed password for root from 202.213.156.232 port 48559 ssh2
Jul 25 10:49:53 server1 sshd[22554]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=b156232.ppp.asahi-net.or.jp  user=root
Jul 25 10:49:55 server1 sshd[22554]: Failed password for root from 202.213.156.232 port 48731 ssh2
Jul 25 10:49:57 server1 sshd[22556]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=b156232.ppp.asahi-net.or.jp  user=root
Jul 25 10:49:59 server1 sshd[22556]: Failed password for root from 202.213.156.232 port 48885 ssh2
Jul 25 10:50:01 server1 CRON[22561]: pam_unix(cron:session): session opened for user root by (uid=0)
Jul 25 10:50:01 server1 CRON[22561]: pam_unix(cron:session): session closed for user root
Jul 25 10:50:01 server1 sshd[22559]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=b156232.ppp.asahi-net.or.jp  user=root
Jul 25 10:50:03 server1 sshd[22559]: Failed password for root from 202.213.156.232 port 49020 ssh2
Jul 25 10:50:05 server1 sshd[22640]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=b156232.ppp.asahi-net.or.jp  user=root
Jul 25 10:50:07 server1 sshd[22640]: Failed password for root from 202.213.156.232 port 49137 ssh2
Jul 25 10:50:09 server1 sshd[22642]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=b156232.ppp.asahi-net.or.jp  user=root
Jul 25 10:50:11 server1 sshd[22642]: Failed password for root from 202.213.156.232 port 50056 ssh2
Jul 25 10:50:13 server1 sshd[22644]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=b156232.ppp.asahi-net.or.jp  user=root
Jul 25 10:50:14 server1 sshd[22644]: Failed password for root from 202.213.156.232 port 50978 ssh2
Jul 25 10:50:16 server1 sshd[22646]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=b156232.ppp.asahi-net.or.jp  user=root
Jul 25 10:50:18 server1 sshd[22646]: Failed password for root from 202.213.156.232 port 51881 ssh2
Jul 25 10:50:20 server1 sshd[22648]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=b156232.ppp.asahi-net.or.jp  user=root
Jul 25 10:50:22 server1 sshd[22648]: Failed password for root from 202.213.156.232 port 52772 ssh2
Jul 25 10:50:23 server1 sshd[22650]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=b156232.ppp.asahi-net.or.jp  user=root
Jul 25 10:50:25 server1 sshd[22650]: Failed password for root from 202.213.156.232 port 53669 ssh2
Jul 25 10:50:27 server1 sshd[22653]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=b156232.ppp.asahi-net.or.jp  user=root
Jul 25 10:50:29 server1 sshd[22653]: Failed password for root from 202.213.156.232 port 54566 ssh2

 
How come they are able to ssh on port 54566 (the last one attempted) when i only have port 22 open?

---

### Post by lykwydchykyn on 2010-07-24
> **ubila said:**
> 
How come they are able to ssh on port 54566 (the last one attempted) when i only have port 22 open?

That port number is the remote port, i.e. the port on the other machine that the ssh client is using.  It's not really significant info.

Failed ssh login attempts are just a reality if you have an ssh server open to the web.  I'd recommend implementing key-only authentication and installing something like fail2ban if you want to keep it secure and cut down on the logging.

---

### Post by lykwydchykyn on 2010-07-24
> **ubila said:**
> Hey all, 
Im getting ALOT of spam in my auth.log from CRONTAB's run by root user.
I only have 2 known CRONTABs setup for root user and they run at around 10pm at night.... Can anyone explain what this activity means??
 

Jul 25 07:20:01 server1 CRON[19547]: pam_unix(cron:session): session opened for user root by (uid=0)
Jul 25 07:20:02 server1 CRON[19547]: pam_unix(cron:session): session closed for user root
Jul 25 07:30:01 server1 CRON[19655]: pam_unix(cron:session): session opened for user root by (uid=0)
Jul 25 07:30:01 server1 CRON[19655]: pam_unix(cron:session): session closed for user root
Jul 25 07:39:01 server1 CRON[19761]: pam_unix(cron:session): session opened for user root by (uid=0)
Jul 25 07:39:01 server1 CRON[19761]: pam_unix(cron:session): session closed for user root
Jul 25 07:40:01 server1 CRON[19839]: pam_unix(cron:session): session opened for user root by (uid=0)
Jul 25 07:40:01 server1 CRON[19839]: pam_unix(cron:session): session closed for user root
Jul 25 07:50:01 server1 CRON[19948]: pam_unix(cron:session): session opened for user root by (uid=0)
Jul 25 07:50:01 server1 CRON[19948]: pam_unix(cron:session): session closed for user root
Jul 25 08:00:01 server1 CRON[20058]: pam_unix(cron:session): session opened for user root by (uid=0)
Jul 25 08:00:02 server1 CRON[20058]: pam_unix(cron:session): session closed for user root
Jul 25 08:09:01 server1 CRON[20164]: pam_unix(cron:session): session opened for user root by (uid=0)
Jul 25 08:09:01 server1 CRON[20164]: pam_unix(cron:session): session closed for user root

 
Has someone gained access to my root account and added a bunch of Crontabs?
How can i check this?
 
Cheers

I couldn't tell you what this is, but it's consistent with the auth log on every Linux machine I've ever administered.  I think it might be php5.  Do you have php5 installed?

EDIT: the ones at x:39 and x:09 are probably php5.  It creates a cron job in /etc/cron.d when installed that does some cleanup at those minutes every hour.  The other logs are probably similar services, just examine files in /etc/cron.d.

---

### Post by CharlesA on 2010-07-24
I don't have PHP installed and my auth.log looks like that with cronjobs (only difference is that mine are every hour). It's just how it is.

As for the failed login attempts, it looks like you've got a bot trying to bruteforce yer ssh credentials.

---

### Post by ubila on 2010-07-24
Thanks for the fast replys guys.
For now ive just dissabled port 22 on my router, as at this point, its not essentail that its turned on, i dont do any remote admin work atm.
 
But i will definatly be looking into fail2ban, thanks for that suggestion.

---

### Post by lykwydchykyn on 2010-07-24
> **CharlesA said:**
> I don't have PHP installed and my auth.log looks like that with cronjobs (only difference is that mine are every hour). It's just how it is.

As for the failed login attempts, it looks like you've got a bot trying to bruteforce yer ssh credentials.

They're not ALL php5, just the ones at x:09 and x:39.  Basically, when php5 is installed it creates a cron job that looks like this:
```


09,39 *     * * *     root   [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm

```

It's just a cleanup process that runs twice an hour at those times.

Other services set up similar things.  They'd likely be under /etc/cron.d; or, since yours are on the hour, check /etc/cron.hourly.

---

### Post by DaithiF on 2010-07-25
Hi, to suppress the pam messages in auth.log everytime a root cron job is run see
```
http://ubuntuforums.org/showthread.php?t=1256801
```

---

