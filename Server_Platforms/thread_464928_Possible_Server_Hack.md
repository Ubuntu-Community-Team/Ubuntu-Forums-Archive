---
title: "Possible Server Hack"
date: 2007-06-05
forum: Server Platforms
---

### Post by coxy on 2007-06-05
After reading the post [http://ubuntuforums.org/showthread.php?t=403383](http://ubuntuforums.org/showthread.php?t=403383) I thought it would be sensible to check my auth.log on my server. I found hundreds of login attempts from root (which is disabled) and Administrator (which doesn't exist) that had all failed. I guess the Administrator account is looking for a Windows box. I also found the following entries so used grep to filter them out; I am not to sure what they mean.

```

dancer:/home/chris# cat /var/log/auth.log | grep Successful
Jun  3 10:23:49 dancer su[2929]: Successful su for root by chris
Jun  4 06:25:02 dancer su[2704]: Successful su for nobody by root
Jun  4 06:25:02 dancer su[2708]: Successful su for nobody by root
Jun  4 06:25:02 dancer su[2710]: Successful su for nobody by root
Jun  4 20:02:08 dancer su[4717]: Successful su for root by chris
Jun  5 06:25:01 dancer su[5019]: Successful su for nobody by root
Jun  5 06:25:01 dancer su[5023]: Successful su for nobody by root
Jun  5 06:25:01 dancer su[5025]: Successful su for nobody by root
Jun  5 11:49:33 dancer su[5239]: Successful su for root by chris
Jun  5 12:03:43 dancer su[5279]: Successful su for root by chris

```

```

dancer:/home/chris# cat /var/log/auth.log | grep nobody
Jun  4 06:25:02 dancer su[2704]: Successful su for nobody by root
Jun  4 06:25:02 dancer su[2704]: + ??? root:nobody
Jun  4 06:25:02 dancer su[2704]: (pam_unix) session opened for user nobody by (uid=0)
Jun  4 06:25:02 dancer su[2704]: (pam_unix) session closed for user nobody
Jun  4 06:25:02 dancer su[2708]: Successful su for nobody by root
Jun  4 06:25:02 dancer su[2708]: + ??? root:nobody
Jun  4 06:25:02 dancer su[2708]: (pam_unix) session opened for user nobody by (uid=0)
Jun  4 06:25:02 dancer su[2708]: (pam_unix) session closed for user nobody
Jun  4 06:25:02 dancer su[2710]: Successful su for nobody by root
Jun  4 06:25:02 dancer su[2710]: + ??? root:nobody
Jun  4 06:25:02 dancer su[2710]: (pam_unix) session opened for user nobody by (uid=0)
Jun  4 06:25:23 dancer su[2710]: (pam_unix) session closed for user nobody
Jun  5 06:25:01 dancer su[5019]: Successful su for nobody by root
Jun  5 06:25:01 dancer su[5019]: + ??? root:nobody
Jun  5 06:25:01 dancer su[5019]: (pam_unix) session opened for user nobody by (uid=0)
Jun  5 06:25:01 dancer su[5019]: (pam_unix) session closed for user nobody
Jun  5 06:25:01 dancer su[5023]: Successful su for nobody by root
Jun  5 06:25:01 dancer su[5023]: + ??? root:nobody
Jun  5 06:25:01 dancer su[5023]: (pam_unix) session opened for user nobody by (uid=0)
Jun  5 06:25:01 dancer su[5023]: (pam_unix) session closed for user nobody
Jun  5 06:25:01 dancer su[5025]: Successful su for nobody by root
Jun  5 06:25:01 dancer su[5025]: + ??? root:nobody
Jun  5 06:25:01 dancer su[5025]: (pam_unix) session opened for user nobody by (uid=0)
Jun  5 06:25:01 dancer su[5025]: (pam_unix) session closed for user nobody
Jun  5 11:52:19 dancer sshd[5242]: User nobody from saturn.bt.com not allowed because not listed in AllowUsers
Jun  5 11:52:19 dancer sshd[5242]: Failed none for invalid user nobody from 193.113.57.20 port 29939 ssh2
Jun  5 11:52:21 dancer sshd[5242]: Failed password for invalid user nobody from 193.113.57.20 port 29939 ssh2
Jun  5 11:52:25 dancer sshd[5242]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=saturn.bt.com  user=nobody
Jun  5 11:52:27 dancer sshd[5242]: Failed password for invalid user nobody from 193.113.57.20 port 29939 ssh2

```

The worrying things are the nobody entries; I realise the nobody account will exist but I do not use it at all. Can someone advise if this is a concern or not? I intend to install fail2ban to block future attempts.

Thanks in advance.

---

### Post by ruy_lopez on 2007-06-05
the "su" lines are just cron jobs (the giveaway is the timestamps). 

As for the failed ssh attempts, do you have forwarding on port 22? It looks like attempts to try and guess your password. You should setup public keys for ssh, then disable password authentication. If public keys are infeasible (you remotely log in from public terminals) then make sure your password is strong.

Brute force attempts on ssh are a common problem.

---

### Post by coxy on 2007-06-05
Thanks for the response; I run SSH on port 23 due to the firewall setup at work, I have no choice. I will configure fail2ban to block anything over 3 attempts from an IP.

Thanks again.

---

