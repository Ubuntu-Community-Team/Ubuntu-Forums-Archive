---
title: "ntp no longer picking a server"
date: 2010-02-08
forum: Server Platforms
---

### Post by r0k5t4r on 2010-02-08
Hi, 
 
I setup 2 ubuntu 9.04 servers to serv ntp to our clients. This was working fine till friday. All of a sudden both servers refuse to pick a ntp server:
 
root@gedail1:/var/yp# ntpq -p
remote refid st t when poll reach delay offset jitter
==============================================================================
gedacw3.vegagro 172.17.200.12 2 u 15 64 377 0.980 2980.80 3.705
10.1.0.2 172.20.200.18 3 u 62 64 377 0.218 2973.97 3.398
 
 
Stratum is fine so why doesn't it pick the server again? I don't think there have been any changes on our firewall that would cause this. 
 
Regards,
r0k5t4r

---

### Post by r0k5t4r on 2010-02-08
I commented out all the restricts. My config file is almost empty now but still it refuses to pick the server:
 
cat /etc/ntp.conf | grep -v ^#
driftfile /var/lib/ntp/ntp.drift

statsdir /var/log/ntpstats/
statistics loopstats peerstats clockstats
filegen loopstats file loopstats type day enable
filegen peerstats file peerstats type day enable
filegen clockstats file clockstats type day enable

server dantp
server dantp2

---

### Post by r0k5t4r on 2010-02-09
Ok, I investigated a little closer using tcpdump and it shows an upd chksum error:
 
[bad udp cksum 19ce!]
 
This is not the case for our solaris 8 ntp server. I will reboot the windows 2003 server that we use as an ntp source for the ubuntu machines. Hopefully that fixes the problem?

---

### Post by nutznboltz on 2010-02-09
ntpd works best when configured to use three servers.

There is a standard group of servers provided by
[http://www.pool.ntp.org/en/](http://www.pool.ntp.org/en/)

Also, using the "iburst" option argument to the "server" configuration option helps a lot.

If you are in the US try using this in your /etc/ntp.conf

server 0.us.pool.ntp.org iburst
server 1.us.pool.ntp.org iburst
server 2.us.pool.ntp.org iburst

Instead of any other "server" lines.

If you are not in the US you can instructions found here:
[http://www.pool.ntp.org/en/use.html](http://www.pool.ntp.org/en/use.html)

---

### Post by r0k5t4r on 2010-02-09
Hi,

thanks for your reply. The 2 ubuntu ntp servers are on a restricted network. I can't reach any server but a windows 2003 box. We have an old solaris 8 box that is able to sync it's time with this win2k3 box without any problems. The udp checksum error I mentioned above seems to be a problem of tcpdump not the ntp protocol. 

I believe it has something to do with the version of ntp that I'm currently using. I will try to upgrade my ubuntu 9.04 to 9.10 tomorrow and hopefully the ntp package will also be upgraded. I know that it was working some time ago. Security updates are installed automatically and I check every week for new updates.

---

### Post by nutznboltz on 2010-02-09
> **r0k5t4r said:**
> The 2 ubuntu ntp servers are on a restricted network. I can't reach any server but a windows 2003 box.

Heh, I'm posting about a similar situation but on a different level.

[http://ubuntuforums.org/showthread.php?t=1402791](http://ubuntuforums.org/showthread.php?t=1402791)

---

### Post by nutznboltz on 2010-02-09
I have a suspicion that this is the problem:

[https://bugs.launchpad.net/ubuntu/+source/ntp/+bug/229632](https://bugs.launchpad.net/ubuntu/+source/ntp/+bug/229632)

We are limited a single NTP upstream source due to political reasons outside our control and our Ubuntu ntpd loses sync periodically.

What if it's due to running ntpd without elevated priority on a busy server like that bug report points out?

The suggestions to use "renice" in that bug report are bogus.  Hack the startup script instead:

```
-- default-intrepid-ntp-init-script     2010-02-09 15:01:43.255277872 -0500
+++ /etc/init.d/ntp     2010-02-09 15:02:48.000000000 -0500
@@ -57,7 +57,7 @@
                        exit 1
                fi
                lock_ntpdate
-               start-stop-daemon --start --quiet --oknodo --pidfile $PIDFILE --startas $DAEMON -- -p $PIDFILE -u $UGID $NTPD_OPTS
+               start-stop-daemon --start --quiet --oknodo --pidfile $PIDFILE --startas $DAEMON --nicelevel -8 -- -p $PIDFILE -u $UGID $NTPD_OPTS
                status=$?
                unlock_ntpdate
                log_end_msg $status

```

---

### Post by nutznboltz on 2010-02-09
xxx

---

