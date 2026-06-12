---
title: "auth.log oddity"
date: 2012-10-14
forum: Security
---

### Post by Buckie_Bhoy on 2012-10-14
Not sure if this is the correct forum or not.
 
12.04 Server 64 Bit
 
logged into my server tonight via SSH (using keys not password), got message about having to restart system, so checked for any more updatesa nd upgraded, then rebooted server. I then checked my auth.log and noticed the following [note timestamps]:
 
```
Oct 14 17:17:01 HomeServer1 CRON[15132]: pam_unix(cron:session): session opened for user root by (uid=0)
Oct 14 17:17:01 HomeServer1 CRON[15132]: pam_unix(cron:session): session closed for user root
Oct 14 18:17:01 HomeServer1 CRON[15153]: pam_unix(cron:session): session opened for user root by (uid=0)
Oct 14 18:17:01 HomeServer1 CRON[15153]: pam_unix(cron:session): session closed for user root
Oct 14 19:09:27 HomeServer1 sshd[15210]: Accepted publickey for username from 192.168.0.7 port 49268 ssh2
Oct 14 19:09:27 HomeServer1 sshd[15210]: pam_unix(sshd:session): session opened for user username by (uid=0)
Oct 14 19:17:01 HomeServer1 CRON[15583]: pam_unix(cron:session): session opened for user root by (uid=0)
Oct 14 19:17:01 HomeServer1 CRON[15583]: pam_unix(cron:session): session closed for user root
Oct 14 19:20:19 HomeServer1 sudo: pam_unix(sudo:auth): authentication failure; logname=username uid=1000 euid=0 tty=/dev/pts/0 ruser=username rhost=  user=username
Oct 14 19:20:28 HomeServer1 sudo:    username : TTY=pts/0 ; PWD=/home/username ; USER=root ; COMMAND=/usr/bin/apt-get update
Oct 14 19:20:28 HomeServer1 sudo: pam_unix(sudo:session): session opened for user root by username(uid=1000)
Oct 14 19:20:41 HomeServer1 sudo: pam_unix(sudo:session): session closed for user root
Oct 14 19:21:24 HomeServer1 sudo:    username : TTY=pts/0 ; PWD=/home/username ; USER=root ; COMMAND=/usr/bin/apt-get upgrade
Oct 14 19:21:24 HomeServer1 sudo: pam_unix(sudo:session): session opened for user root by username(uid=1000)
Oct 14 19:21:46 HomeServer1 sudo: pam_unix(sudo:session): session closed for user root
Oct 14 19:21:53 HomeServer1 sudo:    username : TTY=pts/0 ; PWD=/home/username ; USER=root ; COMMAND=/usr/bin/apt-get update
Oct 14 19:21:53 HomeServer1 sudo: pam_unix(sudo:session): session opened for user root by username(uid=1000)
Oct 14 19:22:05 HomeServer1 sudo: pam_unix(sudo:session): session closed for user root
Oct 14 19:22:52 HomeServer1 sudo:    username : TTY=pts/0 ; PWD=/home/username ; USER=root ; COMMAND=/usr/bin/apt-get upgrade
Oct 14 19:22:52 HomeServer1 sudo: pam_unix(sudo:session): session opened for user root by username(uid=1000)
Oct 14 19:22:53 HomeServer1 sudo: pam_unix(sudo:session): session closed for user root
Oct 14 19:23:20 HomeServer1 sudo:    username : TTY=pts/0 ; PWD=/home/username ; USER=root ; COMMAND=/sbin/shutdown -P -r now
Oct 14 19:23:20 HomeServer1 sudo: pam_unix(sudo:session): session opened for user root by username(uid=1000)
Oct 14 19:23:20 HomeServer1 sudo: pam_unix(sudo:session): session closed for user root
Oct 14 18:55:27 HomeServer1 sshd[1012]: Received signal 15; terminating.
Oct 14 18:55:27 HomeServer1 sshd[1106]: Server listening on 0.0.0.0 port 22.
Oct 14 18:55:27 HomeServer1 sshd[1106]: Server listening on :: port 22.
Oct 14 19:25:42 HomeServer1 sshd[1763]: Accepted publickey for username from 192.168.0.7 port 49373 ssh2
Oct 14 19:25:42 HomeServer1 sshd[1763]: pam_unix(sshd:session): session opened for user username by (uid=0)
Oct 14 19:25:59 HomeServer1 sudo:    username : TTY=pts/0 ; PWD=/home/username ; USER=root ; COMMAND=/usr/bin/apt-get update
Oct 14 19:25:59 HomeServer1 sudo: pam_unix(sudo:session): session opened for user root by username(uid=1000)
Oct 14 19:26:13 HomeServer1 sudo: pam_unix(sudo:session): session closed for user root
Oct 14 19:26:38 HomeServer1 sudo:    username : TTY=pts/0 ; PWD=/home/username ; USER=root ; COMMAND=/usr/bin/apt-get upgrade
Oct 14 19:26:38 HomeServer1 sudo: pam_unix(sudo:session): session opened for user root by username(uid=1000)
Oct 14 19:26:39 HomeServer1 sudo: pam_unix(sudo:session): session closed for user root
```
 
Any ideas why the entries at 18:55, I was the user logging in at 19:09 and running the commands.

---

### Post by Doug S on 2012-10-14
I have seen two cases where time stamps in log files seem to be misaligned. There may be many others, this is just what I have seen.
 
One was due to downloading a huge file via the apache web server that took a very long time, due to my limited bandwidth. The time stamp is fetched at the start of the download, but only actually written to the log file at the end. Meanwhile other more normal, small "GET"s were done. The result was a significant jumping around of the time stamp:```
96.50.106.49 - - [28/Mar/2010:16:14:29 -0700] "GET /favicon.ico HTTP/1.1" 200 1150 "-" "Mozilla/4.0 (compatible; MSIE 8.0; Windows NT 6.0; Trident/4.0; GTB0.0; SLCC1; .NET CLR 2.0.50727; Media Center PC 5.0; .NET CLR 3.5.30729; .NET CLR 3.0.30729)"         
96.50.7.185 - - [28/Mar/2010:[COLOR=red]16:14:56[/COLOR] -0700] "GET /~doug/xxxxx/bla.zip HTTP/1.1" 206 87303579 "http://www.smythies.com/~doug/xxxxx/" "Mozilla/4.0 (compatible; MSIE 8.0; Windows NT 5.1; Trident/4.0; .NET CLR 1.1.4322; .NET CLR 2.0.50727; InfoPath.2; .$
207.46.12.165 - - [28/Mar/2010:[COLOR=red]16:53:20[/COLOR] -0700] "GET /index.html HTTP/1.1" 200 8711 "-" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.2;  SLCC1;  .NET CLR 1.1.4322)"
96.50.106.49 - - [28/Mar/2010:[COLOR=red]16:14:36[/COLOR] -0700] "GET /~doug/xxxxx/bla.zip HTTP/1.1" 200 93525412 "http://www.smythies.com/~doug/harrison/" "Mozilla/4.0 (compatible; MSIE 8.0; Windows NT 6.0; Trident/4.0; GTB0.0; SLCC1; .NET CLR 2.0.50727; Media Center PC $

```Also there is a time shift during boot when a NTP time server is checked and the local server clock is corrected:```
Oct 14 [COLOR=red]14:25:27[/COLOR] s15 postfix/master[2014]: daemon started -- version 2.9.3, configuration /etc/postfix
Oct 14 [COLOR=red]14:25:23[/COLOR] s15 ntpdate[1107]: step time server 91.189.94.4 offset [COLOR=red]-3.972526[/COLOR] sec
Oct 14 14:25:23 s15 kernel: [   27.685039] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
Oct 14 14:25:23 s15 dhcpd:
Oct 14 14:25:23 s15 dhcpd: No subnet declaration for eth0 (192.168.111.112).
Oct 14 14:25:23 s15 dhcpd: ** Ignoring requests on eth0.  If this is not what

```Check /var/log/syslog for the ntp entry and is it very large in your case ~~ 1920 seconds.

---

### Post by Buckie_Bhoy on 2012-10-15
Hi Doug,
 
Thanks for the info, have found the NTP in syslog which explains it.
 
```
Oct 14 18:55:35 HomeServer1 transmission-daemon[1691]: DHT Bootstrapping from 103 IPv4 nodes (tr-dht.c:153)
Oct 14 18:55:35 HomeServer1 transmission-daemon[1691]: Using settings from "/var/lib/transmission-daemon/info" (daemon.c:488)
Oct 14 18:55:35 HomeServer1 transmission-daemon[1691]: Saved "/etc/transmission-daemon/settings.json" (bencode.c:1731)
Oct 14 18:55:35 HomeServer1 transmission-daemon[1691]: transmission-daemon requiring authentication (daemon.c:508)
Oct 14 18:55:35 HomeServer1 transmission-daemon[1691]: Loaded 1 torrents (session.c:1937)
[COLOR=red]Oct 14 19:23:19 HomeServer1 ntpdate[1116]: step time server 91.189.94.4 offset 1663.072889 sec[/COLOR]
Oct 14 19:51:54 HomeServer1 transmission-daemon[1691]: Searching for web interface file "/home/debian-transmission/.local/share/transmission/web/index.html" (platform.$
Oct 14 19:51:54 HomeServer1 transmission-daemon[1691]: Searching for web interface file "/usr/share/transmission/web/index.html" (platform.c:540)

```

---

