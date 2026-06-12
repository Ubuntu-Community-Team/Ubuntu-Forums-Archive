---
title: "Passwords are horrifically slow"
date: 2011-07-04
forum: Server Platforms
---

### Post by Jagoly on 2011-07-04
Hello. I recently built a small server for my dad, to host a business website aswell as manage storage of important documents (raid 1).

Yesterday I thought I would try out zentyal. I got it working, mostly. It seemed very useful.

However, ANY password authentication; including login, sudo, ssh, was extremely laggy. Were talking a minute after entering the password.

I have done
```
sudo apt-get purge zentyal zentyal-samba
```
And
```
sudo apt-get autoremove --purge
```
And rebooted, but the problem persists.

The server won't go into the office for a few weeks yet, but I will need to set up a static ip eventually. But I cannot yet, if that matters.

Ubuntu server 11.04 64bit

---

### Post by dapperdanny77 on 2011-07-04
you have to get an idea what's going on on your system - have a look at the log files in /var/log - maybe you can find valuable info there

/var/log/syslog
/var/log/auth.log
/var/log/kern.log
.
.
.

---

### Post by Jagoly on 2011-07-05
thanks.

auth.log just tells me that authentication was verified 24 seconds after the event prior;

kern.log doesn't really apply for this problem;

syslog probably holds the key, but I can't make much sense of it. I'll try and get the contents on here soon (currently sshing and already packed away keyboard/screen).

---

### Post by Jagoly on 2011-07-06
sorry for slow reply...

this is syslog.1 which is more relevent.

```
Jul  5 14:17:53 AGA-SERVER rsyslogd: [origin software="rsyslogd" swVersion="4.6.4" x-pid="657" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.
Jul  5 14:17:59 AGA-SERVER anacron[746]: Job `cron.daily' terminated
Jul  5 14:17:59 AGA-SERVER anacron[746]: Normal exit (1 job run)
Jul  5 14:39:01 AGA-SERVER CRON[1592]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) -delete)
Jul  5 15:01:01 AGA-SERVER CRON[1664]: (root) CMD (/usr/share/zentyal-network/bandwidth-test.pl >> /dev/null 2>&1)
Jul  5 15:01:01 AGA-SERVER CRON[1662]: (CRON) error (grandchild #1664 failed with exit status 127)
Jul  5 15:09:01 AGA-SERVER CRON[1690]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) -delete)
Jul  5 15:17:01 AGA-SERVER CRON[1722]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul  5 15:39:01 AGA-SERVER CRON[1790]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) -delete)
Jul  5 16:09:01 AGA-SERVER CRON[1887]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) -delete)
Jul  5 16:17:01 AGA-SERVER CRON[1919]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul  5 16:39:01 AGA-SERVER CRON[1989]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) -delete)
Jul  5 17:09:01 AGA-SERVER CRON[2086]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) -delete)
Jul  5 17:17:01 AGA-SERVER CRON[2118]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul  5 17:39:01 AGA-SERVER CRON[2186]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) -delete)
Jul  5 18:09:01 AGA-SERVER CRON[2281]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) -delete)
Jul  5 18:17:01 AGA-SERVER CRON[2312]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul  5 18:39:01 AGA-SERVER CRON[2380]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) -delete)
Jul  5 19:09:01 AGA-SERVER CRON[2474]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) -delete)
Jul  5 19:17:01 AGA-SERVER CRON[2505]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul  5 19:39:01 AGA-SERVER CRON[2573]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) -delete)
Jul  5 20:01:01 AGA-SERVER CRON[2646]: (root) CMD (/usr/share/zentyal-network/bandwidth-test.pl >> /dev/null 2>&1)
Jul  5 20:01:01 AGA-SERVER CRON[2644]: (CRON) error (grandchild #2646 failed with exit status 127)
Jul  5 20:09:01 AGA-SERVER CRON[2673]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) -delete)
Jul  5 20:17:01 AGA-SERVER CRON[2705]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul  5 20:39:01 AGA-SERVER CRON[2773]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) -delete)
Jul  5 21:09:01 AGA-SERVER CRON[2869]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) -delete)
Jul  5 21:17:01 AGA-SERVER CRON[2901]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul  5 21:39:01 AGA-SERVER CRON[2970]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) -delete)
Jul  5 22:09:01 AGA-SERVER CRON[3067]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) -delete)
Jul  5 22:17:01 AGA-SERVER CRON[3099]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul  5 22:39:01 AGA-SERVER CRON[3165]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) -delete)
Jul  5 23:09:01 AGA-SERVER CRON[3261]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) -delete)
Jul  5 23:17:01 AGA-SERVER CRON[3293]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul  5 23:39:01 AGA-SERVER CRON[3360]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) -delete)
Jul  6 00:01:01 AGA-SERVER CRON[3433]: (root) CMD (/usr/share/zentyal-network/bandwidth-test.pl >> /dev/null 2>&1)
Jul  6 00:01:01 AGA-SERVER CRON[3431]: (CRON) error (grandchild #3433 failed with exit status 127)
Jul  6 00:09:01 AGA-SERVER CRON[3461]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) -delete)
Jul  6 00:17:01 AGA-SERVER CRON[3492]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul  6 00:39:01 AGA-SERVER CRON[3561]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) -delete)
Jul  6 01:09:01 AGA-SERVER CRON[3658]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) -delete)
Jul  6 01:12:57 AGA-SERVER dhclient: DHCPREQUEST of 10.0.0.5 on eth0 to 10.0.0.138 port 67
Jul  6 01:12:57 AGA-SERVER dhclient: DHCPACK of 10.0.0.5 from 10.0.0.138
Jul  6 01:12:57 AGA-SERVER dhclient: can't create /var/lib/dhcp3/dhclient.eth0.leases: No such file or directory
Jul  6 01:12:57 AGA-SERVER dhclient: bound to 10.0.0.5 -- renewal in 42550 seconds.
Jul  6 01:17:01 AGA-SERVER CRON[3700]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul  6 01:39:01 AGA-SERVER CRON[3769]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) -delete)
Jul  6 02:09:01 AGA-SERVER CRON[3866]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) -delete)
Jul  6 02:17:01 AGA-SERVER CRON[3897]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul  6 02:39:01 AGA-SERVER CRON[3966]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) -delete)
Jul  6 03:09:01 AGA-SERVER CRON[4063]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) -delete)
Jul  6 03:17:01 AGA-SERVER CRON[4095]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul  6 03:39:01 AGA-SERVER CRON[4164]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) -delete)
Jul  6 04:09:01 AGA-SERVER CRON[4261]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) -delete)
Jul  6 04:17:01 AGA-SERVER CRON[4293]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul  6 04:39:01 AGA-SERVER CRON[4362]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) -delete)
Jul  6 05:01:01 AGA-SERVER CRON[4435]: (root) CMD (/usr/share/zentyal-network/bandwidth-test.pl >> /dev/null 2>&1)
Jul  6 05:01:01 AGA-SERVER CRON[4433]: (CRON) error (grandchild #4435 failed with exit status 127)
Jul  6 05:09:01 AGA-SERVER CRON[4463]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) -delete)
Jul  6 05:17:01 AGA-SERVER CRON[4495]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul  6 05:39:01 AGA-SERVER CRON[4564]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) -delete)
Jul  6 06:09:01 AGA-SERVER CRON[4661]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) -delete)
Jul  6 06:17:01 AGA-SERVER CRON[4692]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul  6 06:25:01 AGA-SERVER CRON[4719]: (root) CMD (test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily ))
Jul  6 06:39:01 AGA-SERVER CRON[4764]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) -delete)
Jul  6 07:09:01 AGA-SERVER CRON[4861]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) -delete)
Jul  6 07:17:01 AGA-SERVER CRON[4893]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul  6 07:30:01 AGA-SERVER CRON[4936]: (root) CMD (start -q anacron || :)
Jul  6 07:30:01 AGA-SERVER anacron[4939]: Anacron 2.3 started on 2011-07-06
Jul  6 07:30:01 AGA-SERVER anacron[4939]: Will run job `cron.daily' in 5 min.
Jul  6 07:30:01 AGA-SERVER anacron[4939]: Jobs will be executed sequentially
Jul  6 07:35:01 AGA-SERVER anacron[4939]: Job `cron.daily' started
Jul  6 07:35:01 AGA-SERVER anacron[4959]: Updated timestamp for job `cron.daily' to 2011-07-06
Jul  6 07:39:01 AGA-SERVER CRON[5010]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) -delete)
```

---

### Post by dapperdanny77 on 2011-07-06
hi,

as far as i understood - zentyal is a web based application - right?
is your web based access slow too?

you can run the following commands to identify possible resource eaters 

```

## top shows the resource consumtion of processes near realtime
>top

## by pressing shift+m top is sorting processes in order of their memory usage

## vmstat shows you several aspects of resource consumption - below vmstat is printing a line every 10 seconds

>vmstat 10

#if the values in the columns si/so are high then your system is swapping which could decrease your systems performance dramatically - maybe you can post some lines

```

There are no obvious findings in your syslog (from my point of view)

---

### Post by Jagoly on 2011-07-06
No, web acces speed is perfectly fine; except ssh passwords. But this problem occurs for purely local passwords too.

Actually, why are there still entrys for zentyal in syslog? I purged it and it's dependencies on the third.

---

### Post by headvampyre@hotmail.co.uk on 2011-07-07
Is there any chance these packages modify any files in /etc/pam.d ? I've found that some modifications (Especially logging in to samba4 DC using the domain the DC is hosting)

---

