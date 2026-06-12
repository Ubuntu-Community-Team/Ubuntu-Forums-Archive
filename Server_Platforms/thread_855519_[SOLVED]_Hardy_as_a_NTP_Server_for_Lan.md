---
title: "[SOLVED] Hardy as a NTP Server for Lan"
date: 2008-07-10
forum: Server Platforms
---

### Post by trmentry on 2008-07-10
I'm having a bit of an issue that I can't seem to find the right answer for.

I have a Hardy 64 bit server that I'm working on configuring.  

I have a pretty generic ntp.conf file (see below)   The problem is that Windows clients give the following error.

"An error occurred while Windows was synchronizing with 10.3.7.54.  the time sample was rejected because: The peer's stratum is less than the host's stratum."

I Googled around for an answer and saw the stuff about putting in the 127.127.0.1 info at the bottom of the ntp.conf file.  But that doesn't appear to work. (yes, restarted the service)


Does anyone have any ideas on what I can do to get this server to sync to us.pool.ntp.org and then allow others to query it for their time?

Thanks


```

root@chi-webuntu01:~# more /etc/ntp.conf
# /etc/ntp.conf, configuration for ntpd; see ntp.conf(5) for help

restrict default ignore

driftfile /var/lib/ntp/ntp.drift


# Enable this if you want statistics to be logged.
#statsdir /var/log/ntpstats/

statistics loopstats peerstats clockstats
filegen loopstats file loopstats type day enable
filegen peerstats file peerstats type day enable
filegen clockstats file clockstats type day enable


# You do need to talk to an NTP server or two (or three).
server us.pool.ntp.org
server ntp.ubuntu.com

# By default, exchange time with everybody, but don't allow configuration.
restrict -4 default kod notrap nomodify nopeer noquery
restrict -6 default kod notrap nomodify nopeer noquery

# Local users may interrogate the ntp server more closely.
restrict 127.0.0.1
restrict ::1

# Allow local lans to sync
restrict 10.0.0.0 mask 255.0.0.0 nomodify notrap


#server 127.127.1.0
#fudge 127.127.1.0 stratum 10

```

---

### Post by k_grdn on 2008-07-10
Hi,

Can you actually poll those ntp servers?

Does your server hold the correct time zone.

What time zone are you in?


Stop ntp daemon and try ntpdate to your ntp servers.


Regards,

k_grdn

---

### Post by Fire_Chief on 2008-07-10
Yes, do make sure your NTP server is properly syncing with it's parents. Once the NTP server has sync'd, it will auto adjust its own stratum setting and then your clients will use it properly. See the thread here: [http://forums.whirlpool.net.au/forum-replies-archive.cfm/680604.html]("http://forums.whirlpool.net.au/forum-replies-archive.cfm/680604.html")
About 3/4 of the way down the page, a suggestion to remove the "restrict default ignore" line may have contributed to fixing the issue. But ultimately, the sync to the parents is of primary concern.

Check the status using ntptrace

Cheers!

---

### Post by trmentry on 2008-07-11
The machine can sync to the pool fine.

```

root@chi-webuntu01:~# /etc/init.d/ntp stop
 * Stopping NTP server ntpd
  ...done.
root@chi-webuntu01:~# ntpdate us.pool.ntp.org
11 Jul 13:16:46 ntpdate[4671]: adjust time server 204.15.208.61 offset
0.000817 sec
root@chi-webuntu01:~# /etc/init.d/ntp start
 * Starting NTP server ntpd
  ...done.
root@chi-webuntu01:~#
root@chi-webuntu01:~#
root@chi-webuntu01:~# ntptrace
localhost: stratum 16, offset 0.000000, synch distance 0.000060
root@chi-webuntu01:~#
root@chi-webuntu01:~#
root@chi-webuntu01:~# ntpq -p
    remote           refid      st t when poll reach   delay   offset  jitter
==============================================================================
 nick125.com     192.43.244.18    2 u    6   64    1   82.513    0.465   0.001

```

But I still show up as 16.   I'm not sure why.

I did remove the restrict default ignore line, still no joy.

---

### Post by Fire_Chief on 2008-07-11
Can you see any info in the /var/log/ntp.log file regarding successful sync by the ntp daemon? Manual syncing does not move the service to a lower stratum.

From the Gentoo Wiki NTP page:
```
Checking ntp

It may take up to 4 hours of semi-continuous reachability to calibrate the clock before you achieve stratum 3 status. If the stratum status hasn't changed in a few hours, your synchronization is definitely failing. It should settle at 3, from synchronization with stratum 2 servers.

ntpq -c readvar | grep stratum   # Using full name of option
ntpq -c rv | grep stratum        # Using abbreviation

You can check what peers you are connected to (and in turn what they are connected to):

ntpq -c pe

For some more information:

ntpq -c rv
```

---

### Post by trmentry on 2008-07-11
Yup... I needed to be a bit more patient.   I waited for like an hour and viola.


root@ns2:~# ntpq -p
     remote           refid      st t when poll reach   delay   offset  jitter
==============================================================================
+caesar.cs.wisc. 128.105.201.11   2 u   60   64  177   20.814   15.848   9.432
+ns1.usg.edu     65.212.71.103    2 u   54   64  177   45.672   34.724  15.065
*time.nist.gov   .ACTS.           1 u  181   64  174   37.712    3.189  14.324
root@ns2:~#
root@ns2:~#
root@ns2:~# ntptrace
localhost: stratum 2, offset 0.019031, synch distance 0.992595
time.nist.gov: stratum 1, offset 0.000000, synch distance 0.002650, refid 'ACTS'



Windows clients happy too.

Thanks for all the help.

---

### Post by Fire_Chief on 2008-07-11
No problem. :) Glad it is working for you. Please mark the thread as [SOLVED] for others.

Cheers!

---

