---
title: "ntpd not working/strange"
date: 2009-12-28
forum: Server Platforms
---

### Post by AnrDaemon on 2009-12-28
I've a primary accounting server that doing all authentification for my network, and I have a ntp server running on it.
But for all I can see, it does not work in any way to correct system time - it runs forward by about 9 seconds per day. In 2 weeks, drift exceed 120 seconds.
The ntp daemon starts normally
```
Dec 29 03:31:32 user ntpd[4718]: ntpd 4.2.4p4@1.1520-o Fri Dec  4 18:18:33 UTC 2009 (1)
Dec 29 03:31:32 user ntpd[4719]: precision = 1.000 usec
Dec 29 03:31:33 user ntpd[4719]: Listening on interface #0 wildcard, 0.0.0.0#123 Disabled
Dec 29 03:31:33 user ntpd[4719]: Listening on interface #1 lo, 127.0.0.1#123 Enabled
Dec 29 03:31:33 user ntpd[4719]: Listening on interface #2 eth0, 192.168.1.1#123 Enabled
Dec 29 03:31:33 user ntpd[4719]: Listening on interface #3 eth0:1, 192.168.10.2#123 Enabled
Dec 29 03:31:33 user ntpd[4719]: kernel time sync status 0040
```
It starts before webmin (that also installed), even if not, it does not appears to have any conflicts.

Now, if i stop ntp and do a manual update...
```
root@user ~
$ invoke-rc.d ntp stop
 * Stopping NTP server ntpd                                                                                      [ OK ]
root@user ~
$ ntpdate -q  fartein.ifi.uio.no info.cyf-kr.edu.pl ntp.cs.strath.ac.uk
server 129.240.64.3, stratum 2, offset -1.977842, delay 0.05746
server 149.156.4.11, stratum 2, offset -1.978373, delay 0.09290
server 130.159.196.118, stratum 2, offset -1.980362, delay 0.08786
29 Dec 04:25:11 ntpdate[7518]: step time server 129.240.64.3 offset -1.977842 sec
root@user ~
$ ntpdate fartein.ifi.uio.no info.cyf-kr.edu.pl ntp.cs.strath.ac.uk
29 Dec 04:25:19 ntpdate[7521]: no server suitable for synchronization found
root@user ~
$ ntpdate -u fartein.ifi.uio.no info.cyf-kr.edu.pl ntp.cs.strath.ac.uk
29 Dec 04:25:30 ntpdate[7524]: step time server 129.240.64.3 offset -1.979683 sec
root@user ~
$
```

This, I do not understand the following:
a) 2 seconds drift from manual clock set 4 hours ago.
b) Why the hell it can't syncronize with given servers withous -u argument?
c) What the hell ntpd doing in system, if it does not keep time in sync? I could as well use cron, but then I'll have to restart dovecot every time clock sync occur.

---

### Post by mhanson on 2009-12-30
Post the contents of your "/etc/ntp.conf" file.

Also from the man page:
>        -u     Direct  ntpdate  to use an unprivileged port for outgoing packets.  This is most useful when behind a firewall that blocks incoming traffic to privileged ports, and you want to synchronise with hosts beyond the fire&#8208;wall. Note that the -d option always uses unprivileged ports.


and:
>         -q     Query only - don’t set the clock.

---

### Post by AnrDaemon on 2009-12-30
> $ grep -Ev "^(#|$)" /etc/ntp.conf
driftfile /var/lib/ntp/ntp.drift
statistics loopstats peerstats clockstats
filegen loopstats file loopstats type day enable
filegen peerstats file peerstats type day enable
filegen clockstats file clockstats type day enable
server fartein.ifi.uio.no
server info.cyf-kr.edu.pl
server ntp.cs.strath.ac.uk
restrict -4 default kod notrap nomodify nopeer noquery
restrict 127.0.0.1
broadcast 192.168.1.255
enable ntp kernel


Thanks, I can read the man page.

P.S.
$ uptime && ntpdate -q  fartein.ifi.uio.no info.cyf-kr.edu.pl ntp.cs.strath.ac.uk
 00:38:12 up 1 day, 21:07,  1 user,  load average: 0.00, 0.00, 0.00
server 129.240.64.3, stratum 2, offset -16.036764, delay 0.05751
server 149.156.4.11, stratum 2, offset -16.027426, delay 0.09822
server 130.159.196.118, stratum 2, offset -16.037550, delay 0.08806
31 Dec 00:34:09 ntpdate[21486]: step time server 129.240.64.3 offset -16.036764 sec

P.P.S.
Is there a way to enable more detailed logging?
Or to gather ntpd status info in any way?

---

### Post by AnrDaemon on 2010-01-04
Hm. Could ntpd be unable to syncronize time due to the fact that I have an intermediate router, and it doing a time syncronizaton for itself?

---

### Post by AnrDaemon on 2010-02-11
```
$ uptime && ntpdate -q fartein.ifi.uio.no info.cyf-kr.edu.pl ntp.cs.strath.ac.uk
 20:59:48 up 24 days, 11:18,  1 user,  load average: 0.05, 0.03, 0.00
server 129.240.64.3, stratum 2, offset -197.346346, delay 0.05528
server 149.156.4.11, stratum 2, offset -197.345439, delay 0.08835
server 130.159.196.118, stratum 2, offset -197.347498, delay 0.09171
11 Feb 20:59:38 ntpdate[468]: step time server 129.240.64.3 offset -197.346346 sec
```
Not enjoyable, if you ask me. Anyone have any slightest idea, what's going on?

---

### Post by gmargo on 2010-02-11
A couple of random but likely useless thoughts:

The firewall port is open?  Must be if ntpdate works.

To see how the ntp daemon is doing and who it's talking to, and synchronized with, run "ntpdc -c peers".

My /etc/default/ntp file has "NTPD_OPTS='-g'" which allows a big step.  That's probably Ubuntu default.

Use multiple servers in /etc/ntp.conf, which you are doing, plus use the "iburst" option.

Here's the "server" section from my /etc/ntp.conf:
server 0.pool.ntp.org iburst
server 1.pool.ntp.org iburst
server 2.pool.ntp.org iburst
server pool.ntp.org iburst
server ntp.ubuntu.com iburst

---

### Post by AnrDaemon on 2012-02-20
I've finally managed to solve it long time ago. Just forgot to update the thread.
What has been done:
1. REMOVE/DISABLE THE /etc/network/if-up.d/ntpdate LINK FFS!!!!
It will disrupt the ntpd server function.

2. Edit your ntp.conf and add all the servers you want to rely upon.
3. Restart ntpd. Wait a few minutes.
4. Run "ntpq -p" and make sure it recognize servers. Most of them will have refid of .INIT. and strata (st) of 16, this should change with time.
5. If after hours (days) of operation, server do not change .INIT. to something more meaningful, or server's strata didn't changed - remove it from the list, and seek for replacement. If all servers stay in that state for days, you probably have issues with blocked packets, or your network misbehaving greatly.

---

