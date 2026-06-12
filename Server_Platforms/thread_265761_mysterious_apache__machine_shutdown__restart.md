---
title: "mysterious apache / machine shutdown / restart"
date: 2006-09-26
forum: Server Platforms
---

### Post by psyncho on 2006-09-26
Hi, 

I have ubuntu dapper on an amd 64 and recently I've had apache go down twice for no reason.  Upon closer inspection of log files it appears that the entire machine may have restarted.  I'm configuring the machine in my spare time and constantly making changes so its hard to pinpoint if anything may have caused this, but my first thought was that someone may have hacked my webserver, got control of the www-data user, then shut it down.  The only other thing is I installed boinc shortly before these things happened.  However, I've only recently left the server running all the time...so the problem could have been there beforehand for all I know.

This is the output of logs I've thought to look at:
apache error:
[Sat Sep 23 22:13:26 2006] [error] [client 24.244.149.2] request failed: error reading the headers
[Sun Sep 24 06:25:09 2006] [notice] caught SIGTERM, shutting down



apache access:
24.98.49.155 - - [23/Sep/2006:19:23:36 -0400] "GET / HTTP/1.0" 200 599 "-" "-"
24.13.170.92 - - [23/Sep/2006:19:31:52 -0400] "GET / HTTP/1.0" 200 599 "-" "-"
24.8.118.213 - - [23/Sep/2006:21:19:08 -0400] "GET / HTTP/1.0" 200 599 "-" "-"
24.244.149.2 - - [23/Sep/2006:22:08:23 -0400] "GET / HTTP/1.0" 400 226 "-" "-"
24.129.121.9 - - [24/Sep/2006:05:54:29 -0400] "GET / HTTP/1.0" 200 599 "-" "-"


apache ssl-error.log
[Sun Sep 24 06:25:10 2006] [error] SSL Library Error: 218595386 error:0D07803A:asn1 encoding routines:ASN1_ITEM_EX_D2I:nested asn1 error
[Sun Sep 24 06:25:10 2006] [error] SSL Library Error: 218734605 error:0D09A00D:asn1 encoding routines:d2i_PrivateKey:ASN1 lib


apache ssl-access.log There is no record of an ssl access past 9/20

syslog:
Sep 24 06:09:01 delphi /USR/SBIN/CRON[13803]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Sep 24 06:09:01 delphi /USR/SBIN/CRON[13805]: (root) CMD (  [ -d /var/lib/php4 ] && find /var/lib/php4/ -type f -cmin +$(/usr/lib/php4/maxlifetime) -print0 | xargs -r -0 rm)
Sep 24 06:17:01 delphi /USR/SBIN/CRON[13827]: (root) CMD (   run-parts --report /etc/cron.hourly)
Sep 24 06:18:01 delphi /USR/SBIN/CRON[13829]: (amavis) CMD (test -e /usr/bin/sa-learn && test -e /usr/sbin/amavisd-new && /usr/bin/sa-learn --sync >/dev/null)
Sep 24 06:25:01 delphi /USR/SBIN/CRON[13832]: (root) CMD (test -x /usr/sbin/anacron || run-parts --report /etc/cron.daily)
Sep 24 06:25:11 delphi exiting on signal 15  

If anyone has any advice on what to look at or what this could have been I would greatly appreciate it.

thanks, 
John

---

### Post by Jussi Kukkonen on 2006-09-26
> [Sun Sep 24 06:25:09 2006] [notice] caught SIGTERM, shutting down

SIGTERM is the signal kill and killall use -- it seems someone/something with enough permissions deliberately killed apache?

---

### Post by psyncho on 2006-09-28
I found this in my /var/log/auth.log file

Sep 24 06:25:01 delphi su[13835]: + ??? root:amavis
Sep 24 06:25:01 delphi su[13835]: (pam_unix) session opened for user amavis by (uid=0)  
Sep 24 06:25:01 delphi su[13835]: (pam_unix) session closed for user amavis           
Sep 24 06:25:02 delphi su[13852]: + ??? root:www-data
Sep 24 06:25:02 delphi su[13852]: (pam_unix) session opened for user www-data by (uid=0)
Sep 24 06:25:02 delphi su[13852]: (pam_unix) session closed for user www-data           
Sep 24 06:25:02 delphi su[13857]: + ??? root:www-data
Sep 24 06:25:02 delphi su[13857]: (pam_unix) session opened for user www-data by (uid=0)
Sep 24 06:25:03 delphi su[13857]: (pam_unix) session closed for user www-data         
Sep 24 06:25:03 delphi su[13874]: + ??? root:nobody
Sep 24 06:25:03 delphi su[13874]: (pam_unix) session opened for user nobody by (uid=0)  
Sep 24 06:25:03 delphi su[13874]: (pam_unix) session closed for user nobody           
Sep 24 06:25:03 delphi su[13878]: + ??? root:nobody
Sep 24 06:25:03 delphi su[13878]: (pam_unix) session opened for user nobody by (uid=0)  
Sep 24 06:25:03 delphi su[13878]: (pam_unix) session closed for user nobody                    
Sep 24 06:25:03 delphi su[13880]: + ??? root:nobody
Sep 24 06:25:03 delphi su[13880]: (pam_unix) session opened for user nobody by (uid=0)  
Sep 24 06:25:04 delphi su[13880]: (pam_unix) session closed for user nobody


Does that look like someone compromised my system as a service?

---

### Post by jgeewax on 2006-10-26
Bump on this?

I have the same problem where the machine restarts every night (early morning) and I cannot figure out why.

system log output:
Oct 25 01:09:01 localhost /USR/SBIN/CRON[7023]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Oct 25 01:17:01 localhost /USR/SBIN/CRON[7241]: (root) CMD (   run-parts --report /etc/cron.hourly)
Oct 25 01:39:01 localhost /USR/SBIN/CRON[7826]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Oct 25 02:03:57 localhost -- MARK --
Oct 25 02:09:01 localhost /USR/SBIN/CRON[8627]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Oct 25 02:18:11 localhost syslogd 1.4.1#17ubuntu7: restart.

// apache error.log (only entry near 2am on oct 25
[Wed Oct 25 02:18:31 2006] [notice] Apache/2.0.55 (Ubuntu) PHP/5.1.2 configured -- resuming normal operations

// auth.log (entries near 2am oct 25)
Oct 25 02:09:01 localhost CRON[8626]: (pam_unix) session opened for user root by (uid=0)
Oct 25 02:09:01 localhost CRON[8626]: (pam_unix) session closed for user root
Oct 25 02:18:28 localhost sshd[4926]: Server listening on :: port 22.


I am not really sure what it could be, and I have nothing to do but wait until tonight to see if it dies again.... ](*,) 
I will play with some things, but if anyone has any ideas, please let me know!

---

### Post by psyncho on 2006-10-26
Hi, sorry for not updating this. 

I don't believe my server was actually restarting, just apache.

I had a certificate with apache running TLS, and it required a user password, to be more secure.  The logrotate script in cron of course didn't enter this password, so it would try to restart the server but fail since it couldn't enter the password for the certificate.  I just saw it as apache being shut off once a week with mysterious error messages that weren't too informative.

The auth.log entries were just cron scripts dropping to the propper user and rights to run various things.

psyncho

---

### Post by jgeewax on 2006-10-27
It just did it again!

I can't figure out what is happening. I have a complete system restart and it is not a crash. It is "sceduled" it seems. Cron runs something for PHP5, and then there is a "restart" command issued around 10 past 2 AM.

Anyone have an idea?

---

### Post by drakorg on 2006-11-25
check if there is any cron activity scheduled for 10 past 2.
i've read in another forum another user having trouble with log rotations, and if apache was up by the time, it just crashed.

he "solved" it by forcing apache to restart immediately after the log rotation.

hope it helps
drak

---

### Post by MJN on 2006-11-25
> **jgeewax said:**
> It just did it again!

I can't figure out what is happening. I have a complete system restart and it is not a crash. It is "sceduled" it seems. Cron runs something for PHP5, and then there is a "restart" command issued around 10 past 2 AM.

Anyone have an idea?

What makes you think the whole server is rebooting? The following line:

Oct 25 02:18:11 localhost syslogd 1.4.1#17ubuntu7: restart

does **not** tell you that (although I can see why you would think it doe). It's merely saying that syslogd is restarting, like it has to every day as part of the log rotations. This is necessary in order that the current log file can be 'released' and rolled over; the restart of syslogd can than take place with a fresh (empty) log file.

What's the contents of your /etc/crontab file? And do you have Anacron installed? (check for the existence of /usr/sbin/anacron)

Mathew

---

