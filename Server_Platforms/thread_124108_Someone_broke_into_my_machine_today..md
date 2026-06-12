---
title: "Someone broke into my machine today."
date: 2006-01-31
forum: Server Platforms
---

### Post by TheSqueak on 2006-01-31
Short story:

I have a visitor account on my home PC as we have a house guest, and I foolishly had a week password on it.

Earlier today someone accessed this account from Romania and downloaded what appears to me to be some sort of bot used to connect to an IRC server.

I first noticed this when I was looking at my router logs to see why a laptop MSN connection wasn't working properly and a bit of further investigation showed:

3 Connections to irc servers:

```
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 192.168.10.2:32826      undernet.xs4all.nl:ircd ESTABLISHED-
tcp        0      0 192.168.10.2:32822      irc2.saunalahti.fi:6666 ESTABLISHED-
tcp        0      0 192.168.10.2:32800      unknown.easynews.c:ircd ESTABLISHED-

```

Something called "checka" being run by the visitor account,  even though they weren't logged on at the time.

The following new files:

```
james@Fluoroalien (/var/tmp) $ ls -l checka*
-rw-r--r--  1 visitor visitor 289343 2006-01-05 08:33 checka.tgz

checka:
total 828
-rwxr-xr-x  1 visitor visitor    242 2006-01-31 22:45 1
-rwxr-xr-x  1 visitor visitor    242 2006-01-31 22:45 2
-rwxr-xr-x  1 visitor visitor    242 2006-01-31 22:45 3
-rwxr-xr-x  1 visitor visitor     14 2006-01-05 08:08 a
-rwx--x--x  1 visitor visitor 578551 2005-02-05 13:17 checka
-rw-r--r--  1 visitor visitor  13066 2006-01-31 22:45 checka.seen
-rw-r--r--  1 visitor visitor    843 2006-01-31 21:58 LinkEvents
-rwxr-xr-x  1 visitor visitor 167964 2001-03-16 16:47 pico
drwxr-xr-x  2 visitor visitor   4096 2005-09-10 22:46 rand
-rwxr-xr-x  1 visitor visitor  22465 2005-02-05 13:17 raw.help
-rwxr-xr-x  1 visitor visitor   1022 2006-01-31 22:45 raw.levels
-rw-------  1 visitor visitor      5 2006-01-31 15:16 raw.pid
-rw-r--r--  1 visitor visitor   1377 2006-01-31 22:45 raw.session
-rwxr-xr-x  1 visitor visitor   4438 2006-01-05 08:07 raw.set
```

And the following long list of entries in /var/log/auth.log

```
Jan 31 15:02:16 localhost sshd[9851]: Did not receive identification string from 85.46.96.5
Jan 31 15:13:38 localhost sshd[9852]: Invalid user staff from 85.46.96.5
Jan 31 15:13:38 localhost sshd[9852]: (pam_unix) check pass; user unknown
Jan 31 15:13:38 localhost sshd[9852]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=host5-96.pool8546.interbusiness.it
Jan 31 15:13:40 localhost sshd[9852]: Failed password for invalid user staff from 85.46.96.5 port 1351 ssh2
Jan 31 15:13:40 localhost sshd[9854]: Invalid user sales from 85.46.96.5
Jan 31 15:13:40 localhost sshd[9854]: (pam_unix) check pass; user unknown
Jan 31 15:13:40 localhost sshd[9854]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=host5-96.pool8546.interbusiness.it
Jan 31 15:13:42 localhost sshd[9854]: Failed password for invalid user sales from 85.46.96.5 port 1685 ssh2
Jan 31 15:13:43 localhost sshd[9856]: Invalid user recruit from 85.46.96.5
Jan 31 15:13:43 localhost sshd[9856]: (pam_unix) check pass; user unknown
Jan 31 15:13:43 localhost sshd[9856]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=host5-96.pool8546.interbusiness.it
Jan 31 15:13:45 localhost sshd[9856]: Failed password for invalid user recruit from 85.46.96.5 port 1894 ssh2
Jan 31 15:13:46 localhost sshd[9858]: Invalid user alias from 85.46.96.5
Jan 31 15:13:46 localhost sshd[9858]: (pam_unix) check pass; user unknown
Jan 31 15:13:46 localhost sshd[9858]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=host5-96.pool8546.interbusiness.it
Jan 31 15:13:48 localhost sshd[9858]: Failed password for invalid user alias from 85.46.96.5 port 2381 ssh2
Jan 31 15:13:49 localhost sshd[9860]: Invalid user office from 85.46.96.5
Jan 31 15:13:49 localhost sshd[9860]: (pam_unix) check pass; user unknown
Jan 31 15:13:49 localhost sshd[9860]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=host5-96.pool8546.interbusiness.it
Jan 31 15:13:51 localhost sshd[9860]: Failed password for invalid user office from 85.46.96.5 port 2524 ssh2
Jan 31 15:13:52 localhost sshd[9862]: Invalid user samba from 85.46.96.5
Jan 31 15:13:52 localhost sshd[9862]: (pam_unix) check pass; user unknown
Jan 31 15:13:52 localhost sshd[9862]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=host5-96.pool8546.interbusiness.it
Jan 31 15:13:53 localhost sshd[9862]: Failed password for invalid user samba from 85.46.96.5 port 2919 ssh2
Jan 31 15:13:57 localhost sshd[9864]: Invalid user tomcat from 85.46.96.5
Jan 31 15:13:57 localhost sshd[9864]: (pam_unix) check pass; user unknown
Jan 31 15:13:57 localhost sshd[9864]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=host5-96.pool8546.interbusiness.it
Jan 31 15:13:59 localhost sshd[9864]: Failed password for invalid user tomcat from 85.46.96.5 port 3128 ssh2
Jan 31 15:14:00 localhost sshd[9866]: Invalid user webadmin from 85.46.96.5
Jan 31 15:14:00 localhost sshd[9866]: (pam_unix) check pass; user unknown
Jan 31 15:14:00 localhost sshd[9866]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=host5-96.pool8546.interbusiness.it
Jan 31 15:14:02 localhost sshd[9866]: Failed password for invalid user webadmin from 85.46.96.5 port 3696 ssh2
Jan 31 15:14:02 localhost sshd[9868]: Invalid user spam from 85.46.96.5
Jan 31 15:14:02 localhost sshd[9868]: (pam_unix) check pass; user unknown
Jan 31 15:14:02 localhost sshd[9868]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=host5-96.pool8546.interbusiness.it
Jan 31 15:14:04 localhost sshd[9868]: Failed password for invalid user spam from 85.46.96.5 port 4249 ssh2
Jan 31 15:14:05 localhost sshd[9870]: Invalid user virus from 85.46.96.5
Jan 31 15:14:05 localhost sshd[9870]: (pam_unix) check pass; user unknown
Jan 31 15:14:05 localhost sshd[9870]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=host5-96.pool8546.interbusiness.it
Jan 31 15:14:07 localhost sshd[9870]: Failed password for invalid user virus from 85.46.96.5 port 4431 ssh2
Jan 31 15:14:08 localhost sshd[9872]: Invalid user cyrus from 85.46.96.5
Jan 31 15:14:08 localhost sshd[9872]: (pam_unix) check pass; user unknown
Jan 31 15:14:08 localhost sshd[9872]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=host5-96.pool8546.interbusiness.it
Jan 31 15:14:10 localhost sshd[9872]: Failed password for invalid user cyrus from 85.46.96.5 port 4814 ssh2
Jan 31 15:14:10 localhost sshd[9874]: Invalid user oracle from 85.46.96.5
Jan 31 15:14:10 localhost sshd[9874]: (pam_unix) check pass; user unknown
Jan 31 15:14:10 localhost sshd[9874]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=host5-96.pool8546.interbusiness.it
Jan 31 15:14:12 localhost sshd[9874]: Failed password for invalid user oracle from 85.46.96.5 port 1137 ssh2
Jan 31 15:14:13 localhost sshd[9876]: Invalid user michael from 85.46.96.5
Jan 31 15:14:13 localhost sshd[9876]: (pam_unix) check pass; user unknown
Jan 31 15:14:13 localhost sshd[9876]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=host5-96.pool8546.interbusiness.it
Jan 31 15:14:15 localhost sshd[9876]: Failed password for invalid user michael from 85.46.96.5 port 1392 ssh2
Jan 31 15:14:15 localhost sshd[9878]: Invalid user ftp from 85.46.96.5
Jan 31 15:14:15 localhost sshd[9878]: (pam_unix) check pass; user unknown
Jan 31 15:14:15 localhost sshd[9878]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=host5-96.pool8546.interbusiness.it
Jan 31 15:14:17 localhost sshd[9878]: Failed password for invalid user ftp from 85.46.96.5 port 1681 ssh2
Jan 31 15:14:18 localhost sshd[9880]: Invalid user test from 85.46.96.5
Jan 31 15:14:18 localhost sshd[9880]: (pam_unix) check pass; user unknown
Jan 31 15:14:18 localhost sshd[9880]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=host5-96.pool8546.interbusiness.it
Jan 31 15:14:20 localhost sshd[9880]: Failed password for invalid user test from 85.46.96.5 port 1903 ssh2
Jan 31 15:14:21 localhost sshd[9882]: Invalid user webmaster from 85.46.96.5
Jan 31 15:14:21 localhost sshd[9882]: (pam_unix) check pass; user unknown
Jan 31 15:14:21 localhost sshd[9882]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=host5-96.pool8546.interbusiness.it
Jan 31 15:14:23 localhost sshd[9882]: Failed password for invalid user webmaster from 85.46.96.5 port 2215 ssh2
Jan 31 15:14:24 localhost sshd[9884]: Invalid user postmaster from 85.46.96.5
Jan 31 15:14:24 localhost sshd[9884]: (pam_unix) check pass; user unknown
Jan 31 15:14:24 localhost sshd[9884]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=host5-96.pool8546.interbusiness.it
Jan 31 15:14:25 localhost sshd[9884]: Failed password for invalid user postmaster from 85.46.96.5 port 2925 ssh2
Jan 31 15:14:26 localhost sshd[9886]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=host5-96.pool8546.interbusiness.it  user=postfix
Jan 31 15:14:28 localhost sshd[9886]: Failed password for postfix from 85.46.96.5 port 3589 ssh2
Jan 31 15:14:30 localhost sshd[9888]: Invalid user postgres from 85.46.96.5
Jan 31 15:14:30 localhost sshd[9888]: (pam_unix) check pass; user unknown
Jan 31 15:14:30 localhost sshd[9888]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=host5-96.pool8546.interbusiness.it
Jan 31 15:14:32 localhost sshd[9888]: Failed password for invalid user postgres from 85.46.96.5 port 4770 ssh2
Jan 31 15:14:32 localhost sshd[9890]: Invalid user paul from 85.46.96.5
Jan 31 15:14:32 localhost sshd[9890]: (pam_unix) check pass; user unknown
Jan 31 15:14:32 localhost sshd[9890]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=host5-96.pool8546.interbusiness.it
Jan 31 15:14:34 localhost sshd[9890]: Failed password for invalid user paul from 85.46.96.5 port 1763 ssh2
Jan 31 15:14:35 localhost sshd[9892]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=host5-96.pool8546.interbusiness.it  user=root
Jan 31 15:14:36 localhost sshd[9892]: Failed password for root from 85.46.96.5 port 2374 ssh2
Jan 31 15:14:37 localhost sshd[9894]: Invalid user guest from 85.46.96.5
Jan 31 15:14:37 localhost sshd[9894]: (pam_unix) check pass; user unknown
Jan 31 15:14:37 localhost sshd[9894]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=host5-96.pool8546.interbusiness.it
Jan 31 15:14:40 localhost sshd[9894]: Failed password for invalid user guest from 85.46.96.5 port 3117 ssh2
Jan 31 15:14:40 localhost sshd[9896]: Invalid user admin from 85.46.96.5
Jan 31 15:14:40 localhost sshd[9896]: (pam_unix) check pass; user unknown
Jan 31 15:14:40 localhost sshd[9896]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=host5-96.pool8546.interbusiness.it
Jan 31 15:14:43 localhost sshd[9896]: Failed password for invalid user admin from 85.46.96.5 port 3769 ssh2
Jan 31 15:14:44 localhost sshd[9898]: Invalid user linux from 85.46.96.5
Jan 31 15:14:44 localhost sshd[9898]: (pam_unix) check pass; user unknown
Jan 31 15:14:44 localhost sshd[9898]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=host5-96.pool8546.interbusiness.it
Jan 31 15:14:45 localhost sshd[9898]: Failed password for invalid user linux from 85.46.96.5 port 4610 ssh2
Jan 31 15:14:46 localhost sshd[9900]: Invalid user user from 85.46.96.5
Jan 31 15:14:46 localhost sshd[9900]: (pam_unix) check pass; user unknown
Jan 31 15:14:46 localhost sshd[9900]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=host5-96.pool8546.interbusiness.it
Jan 31 15:14:48 localhost sshd[9900]: Failed password for invalid user user from 85.46.96.5 port 1363 ssh2
Jan 31 15:14:49 localhost sshd[9902]: Invalid user david from 85.46.96.5
Jan 31 15:14:49 localhost sshd[9902]: (pam_unix) check pass; user unknown
Jan 31 15:14:49 localhost sshd[9902]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=host5-96.pool8546.interbusiness.it
Jan 31 15:14:52 localhost sshd[9902]: Failed password for invalid user david from 85.46.96.5 port 2441 ssh2
Jan 31 15:14:52 localhost sshd[9904]: Invalid user web from 85.46.96.5
Jan 31 15:14:53 localhost sshd[9904]: (pam_unix) check pass; user unknown
Jan 31 15:14:53 localhost sshd[9904]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=host5-96.pool8546.interbusiness.it
Jan 31 15:14:54 localhost sshd[9904]: Failed password for invalid user web from 85.46.96.5 port 3452 ssh2
Jan 31 15:14:55 localhost sshd[9906]: Invalid user apache from 85.46.96.5
Jan 31 15:14:55 localhost sshd[9906]: (pam_unix) check pass; user unknown
Jan 31 15:14:55 localhost sshd[9906]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=host5-96.pool8546.interbusiness.it
Jan 31 15:14:57 localhost sshd[9906]: Failed password for invalid user apache from 85.46.96.5 port 4104 ssh2
Jan 31 15:14:58 localhost sshd[9908]: Invalid user pgsql from 85.46.96.5
Jan 31 15:14:58 localhost sshd[9908]: (pam_unix) check pass; user unknown
Jan 31 15:14:58 localhost sshd[9908]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=host5-96.pool8546.interbusiness.it
Jan 31 15:14:59 localhost sshd[9908]: Failed password for invalid user pgsql from 85.46.96.5 port 4867 ssh2
Jan 31 15:15:00 localhost sshd[9910]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=host5-96.pool8546.interbusiness.it  user=mysql
Jan 31 15:15:03 localhost sshd[9910]: Failed password for mysql from 85.46.96.5 port 1539 ssh2
Jan 31 15:15:07 localhost sshd[9912]: Invalid user info from 85.46.96.5
Jan 31 15:15:07 localhost sshd[9912]: (pam_unix) check pass; user unknown
Jan 31 15:15:07 localhost sshd[9912]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=host5-96.pool8546.interbusiness.it
Jan 31 15:15:09 localhost sshd[9912]: Failed password for invalid user info from 85.46.96.5 port 2316 ssh2
Jan 31 15:15:13 localhost sshd[9914]: Invalid user tony from 85.46.96.5
Jan 31 15:15:13 localhost sshd[9914]: (pam_unix) check pass; user unknown
Jan 31 15:15:13 localhost sshd[9914]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=host5-96.pool8546.interbusiness.it
Jan 31 15:15:16 localhost sshd[9914]: Failed password for invalid user tony from 85.46.96.5 port 4033 ssh2
Jan 31 15:15:17 localhost sshd[9916]: Invalid user core from 85.46.96.5
Jan 31 15:15:17 localhost sshd[9916]: (pam_unix) check pass; user unknown
Jan 31 15:15:17 localhost sshd[9916]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=host5-96.pool8546.interbusiness.it
Jan 31 15:15:19 localhost sshd[9916]: Failed password for invalid user core from 85.46.96.5 port 1776 ssh2
Jan 31 15:15:19 localhost sshd[9918]: Invalid user newsletter from 85.46.96.5
Jan 31 15:15:19 localhost sshd[9918]: (pam_unix) check pass; user unknown
Jan 31 15:15:19 localhost sshd[9918]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=host5-96.pool8546.interbusiness.it
Jan 31 15:15:22 localhost sshd[9918]: Failed password for invalid user newsletter from 85.46.96.5 port 2733 ssh2
Jan 31 15:15:23 localhost sshd[9920]: Invalid user named from 85.46.96.5
Jan 31 15:15:23 localhost sshd[9920]: (pam_unix) check pass; user unknown
Jan 31 15:15:23 localhost sshd[9920]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=host5-96.pool8546.interbusiness.it
Jan 31 15:15:25 localhost sshd[9920]: Failed password for invalid user named from 85.46.96.5 port 3615 ssh2
Jan 31 15:15:26 localhost sshd[9922]: Accepted password for visitor from 85.46.96.5 port 4482 ssh2
Jan 31 15:15:26 localhost sshd[9924]: (pam_unix) session opened for user visitor by (uid=0)
Jan 31 15:15:33 localhost sshd[9936]: Invalid user ftpuser from 85.46.96.5
Jan 31 15:15:33 localhost sshd[9936]: (pam_unix) check pass; user unknown
Jan 31 15:15:33 localhost sshd[9936]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=host5-96.pool8546.interbusiness.it
Jan 31 15:15:35 localhost sshd[9936]: Failed password for invalid user ftpuser from 85.46.96.5 port 2618 ssh2
Jan 31 15:15:36 localhost sshd[9938]: Invalid user username from 85.46.96.5
Jan 31 15:15:36 localhost sshd[9938]: (pam_unix) check pass; user unknown
Jan 31 15:15:36 localhost sshd[9938]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=host5-96.pool8546.interbusiness.it
Jan 31 15:15:38 localhost sshd[9938]: Failed password for invalid user username from 85.46.96.5 port 3343 ssh2
Jan 31 15:16:10 localhost sshd[9943]: Accepted password for visitor from 85.186.211.144 port 2833 ssh2
Jan 31 15:16:11 localhost sshd[9945]: (pam_unix) session opened for user visitor by (uid=0)
Jan 31 15:16:22 localhost passwd[9959]: (pam_unix) password changed for visitor
Jan 31 15:16:22 localhost passwd[9959]: (pam_unix) Password for visitor was changed
Jan 31 15:17:01 localhost CRON[9970]: (pam_unix) session opened for user root by (uid=0)
Jan 31 15:16:46 localhost CRON[9970]: (pam_unix) session closed for user root
Jan 31 15:17:01 localhost CRON[9985]: (pam_unix) session opened for user root by (uid=0)
Jan 31 15:17:01 localhost CRON[9985]: (pam_unix) session closed for user root
Jan 31 15:17:23 localhost sshd[9940]: fatal: Timeout before authentication for 85.46.96.5
Jan 31 15:17:44 localhost sshd[9942]: fatal: Timeout before authentication for 86.120.5.172
Jan 31 15:17:45 localhost sshd[9945]: (pam_unix) session closed for user visitor
```

As far as I can tell, this looks like I had a long string of failed attempts to log in on common user names from 85.46.96.5 (which is, according to whois, in Italy), immediately followed by a successful login as visitor from 85.186.211.144 (the Romania one)

I've killed off the checka process, deleted the visitor account (mea culpa, I was a fool), disabled ssh (as I don't use it much anyway), checked that there are no unknown network connections and made sure that visitor has no crontab.

I'm about to bail and get some sleep as i've got an early start in the morning, but I have a couple of questions I wonder if folks could shed some light on ...

1. What is it with the long string of failed connections from one IP immediately followed by the successful entry from a different one in another country?

2. Has anyone heard of "checka" before, i'm not a programmer in any way so I can't really dig through it to work out what it does - but the files are still there if anyone is interested.

3. Are the CRON entries about root sessions coincidental (there are others of these in other parts of the log totally unrelated to this afternoon)

4. There doesn't appear to have been any attempt to break the root account, and the visitor account was reasonably locked down, but am I still right in thinking I should really reinstall my O/S after something like this?

Cheers for any help, and apologies for the length of this post.

---

### Post by saubz on 2006-01-31
> 

1. What is it with the long string of failed connections from one IP immediately followed by the successful entry from a different one in another country?



I'm not positive, but this would seem to indicate the person is using a proxy server, or a series of proxies to mask his actual IP.  Any smart hacker will do something similar to hide their identity.

---

### Post by Alpha_toxic on 2006-01-31
The above looks very possible...
Anyway this is way I have disabled remote login for all users, including root. I'd advice anyone to do so if he doesn't actually need it.

---

### Post by r4ik on 2006-01-31
[QUOTE=Alpha_toxic]The above looks very possible...
Anyway this is way I have disabled remote login for all users, including root. I'd advice anyone to do so if he doesn't actually need it.[/QUOTE]

How do i disable remote login can you enyone tell me that please?
When i do a  /var/log/auth.log i get a acces denied as root also.

---

### Post by Peter76 on 2006-02-01
Could you post checka.tgz here? I wouldn't mind having a look at it.

---

### Post by TheSqueak on 2006-02-01
I've renamed it to .tar.gz so that the forums would take it, but it's otherwise unchanged and attached to this post.

---

### Post by void_false on 2006-02-01
read files in checka\rand 
15 minutes of laugh guaranteed!:mrgreen: :twisted:

---

### Post by kruz on 2006-02-01
opened tar file, opened rand files with gedit
LAUGHED FOR 15 MINUTES STRAIT!!!!
i dont think u have anything to worry about
if i had to guess
i would most DEFFINITLY say that this
is for someone who is using u as a bot, or host in an irc room
and those are its away messages, etc, go into a room that it logs in, and check

sounds like someone is making a botnet, and using u to distribute files


but i dont think their very sucessful

---

### Post by christhemonkey on 2006-02-01
LMAO! thats funny!

---

### Post by invalid on 2006-02-01
I might suggest that you install DenyHosts. I don't think it's available as a .deb package, but I know for a fact that it can be installed from source. It will set a limit on the amount of times a host can attempt to access your ssh. After this has been exceeded, the host will be banned from your system.

I had (still do) problems with people trying to access my system, and never had a clue. I installed DenyHosts, and regularly catch 5-10 hosts a day (mostly proxies, probably the same person).

Cheers,
Cb

---

### Post by krusbjorn on 2006-02-01
[QUOTE=invalid]I might suggest that you install DenyHosts. I don't think it's available as a .deb package, but I know for a fact that it can be installed from source. It will set a limit on the amount of times a host can attempt to access your ssh. After this has been exceeded, the host will be banned from your system.

I had (still do) problems with people trying to access my system, and never had a clue. I installed DenyHosts, and regularly catch 5-10 hosts a day (mostly proxies, probably the same person).

Cheers,
Cb[/QUOTE]

Thanks a lot, invalid. I am definitely gonna check this out.

Edit: Got it up and running. It was a breeze to configure, even for a newbie like me. I greatly appreciate that you mentioned it here.

---

### Post by souki on 2006-02-01
the checka file is the EnergyMech irc bot [http://www.energymech.net/](http://www.energymech.net/)   :

```
strings checka | grep -i start
__libc_start_main
__gmon_start__
EnergyMech started...
 -d          start mech in debug mode
Started             %s
```

I don't want to be alarmist but:
I would not trust a computer like yours, you can do a lot of things with an irc bot : trojan, distributed attacks, mass mailer, etc... the main purpose of the irc part is to give remote access to your computer even if it is behind a firewall

it can be easy to gain root access from a shell (there is a lot of exploit code to use), and it is very easy to install a root kit

if your computer was updated with last security fix, don't worry much about that. If not, disconnect the computer, save your work, and reinstall

for the ssh part, you can use a ssh key and disable password authentication in /etc/ssh/sshd_config

good luck :p

---

### Post by LordHunter317 on 2006-02-02
Your computer was compromised.

Everything on it is now suspect.  Disconnect it now, wipe and reinstall.  The box shouldn't be online any longer.

At a very minimum, virus scan all your data files before using them again.  Any code you wrote needs to be manually audited.

---

### Post by TheSqueak on 2006-02-02
I was kind of hoping that I wouldn't have to reinstall everything, as it looked pretty much like it was just a script kiddy getting lucky through my stupidity (easy password on the account), rather than a decent hacker, but I realise that's probably being a bit too optimistic :(

I have at least

a) Shutdown the SSH server, as I don't use it much
b) Deleted the visitor account that was connected to
c) Changed my passwords
d) Booted from a LiveCD and run chkrootkit from that (nothing showed up)
e) Actually installed a firewall rather than just relying on the NAT router I was behind

---

### Post by BLTicklemonster on 2006-02-02
Very scary stuff. How does one fix this? Someone asked, but no one really gave an answer.

---

### Post by newuser111 on 2006-02-02
the hacker used a bruteforce type attack, which is a wordlist of common usernames and passwords and tries them on the ssh login, and by luck succeeded

running any server on your computer is a security risk

at least use uncommon usernames and passwords with numbers and mixed case

btw ubuntu isnt installed with an ssh server by default

---

### Post by BLTicklemonster on 2006-02-02
Welll, it just figures, because I have a spare box, and was going to ask around on how to set it up with the ability to be used as a router and a server. I have a 4 port dlink router at present, and this box would leave someone out in the cold, so I was thinking of putting some of the Nics I have laying around to good use along with that box.

---

### Post by cilynx on 2006-05-08
A little advice on DenyHosts:

First off, I have to say that this is a great little prog.  Before DenyHost, I was getting about 2 attempts per second on my server.  After DenyHosts, I get about 1 attempt per week that squeeks through before DenyHosts quashes that as well.  I use the "crappy ip distribution" feature of DenyHosts and the imported bad guy list pretty much takes care of things.  Also, by default DenyHosts only blocks SSH for your bad guys.  I edited the config such that it blocks all services.  Why would I want some script kiddie in Italy having any access to my box at all?

---

### Post by Chris Tucker on 2008-01-23
Noticed this in netstat just now. searched the foreign address.. very nice. 

have to admit didnt think id become part of something like this. From what im seeing definatly a botnet. still trying to locate where it installed itself to. caught me by a username "display" password "display" that i used to display things on my server's monitor.

should be more careful with my passwords.

changed the user's password and killed the processes simotaniously. connections were back 3 min later. had to delete the user completely. 

thankfully safe. cant find it's files yet but i know that user never has had access to replace anything in one of my executable directories and i never run something with a different path. was scared for a second though when i noticed here it had a copy of pico thats infected in it though>_>

Only thing i find strange is according to auth logs this user has had access to my system for possibly months. but another scan was done to find open usernames/passwords that shows yesterday? either another person using the same rootkit or someone is really greedy and wants more UIDs on the same systems >_>

---

### Post by ssam on 2008-01-23
just to note. this can only happen if you have a ssh server installed. you allow logins from any IP address. you allow password logon (search for ssh key login). you dont have a brute force stopper (look up denyhost or fail2ban).

---

### Post by smileypaul on 2008-01-23
Why not just set up IP tables to permanently ban the ip after say 3 tries in one minute?

It certainly keeps the riff-raff out..


another method i used was just changing the ssh port to something other than 22 ..

---

### Post by ssam on 2008-01-23
> **smileypaul said:**
> Why not just set up IP tables to permanently ban the ip after say 3 tries in one minute?


denyhost and fail2ban basically do that, but they only care about failed loggin attempts. they can also get lists of bad IPs from somewhere else. let sucsessful logins reset the fail counts etc.

maybe you can do this with IP tables (i am not an expert), but it is very easy to do it with these tools.

---

