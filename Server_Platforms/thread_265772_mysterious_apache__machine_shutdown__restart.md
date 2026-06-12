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

### Post by fstab on 2006-09-26
In my experience, spontaneous restarts or shutdowns tend to be related to the power supply.  If your power supply isn't strong enough, it could shutdown as if someone had plugged the plug.  If your power supply is flaky it could restart spontaneously.

---

### Post by psyncho on 2006-09-26
Well, I had thought of that, but I figured a flaky power supply restart wouldn't give the server enough time to write log messages saying that it was shutting down.

---

### Post by sonic2000gr on 2006-09-29
The messages you are getting from apache all come at 6:25 in the morning. This is a scheduled restart for apache. It is initiated from the cron job that rotates the logs. You can verify it by looking at the file /etc/crontab  (You will notice the daily cron job executes at 6.25) and looking at the the /etc/cron.daily folder you will find a link to the logrotate script.
Check your server uptime with the uptime command to see if it actually restarts at any time. I wouldn't look at apache though.

---

### Post by psyncho on 2006-09-29
> **sonic2000gr said:**
> The messages you are getting from apache all come at 6:25 in the morning. This is a scheduled restart for apache. It is initiated from the cron job that rotates the logs. You can verify it by looking at the file /etc/crontab  (You will notice the daily cron job executes at 6.25) and looking at the the /etc/cron.daily folder you will find a link to the logrotate script.
Check your server uptime with the uptime command to see if it actually restarts at any time. I wouldn't look at apache though.

Yep, I had figured a lot of that out, though I didn't know which script in cron.daily was actually doing it.  From other logs it looked like the entire machine had actually restarted (e.g. syslog got the "delphi exiting on signal 15" entry.  Would that be created by restarting the apache server?  I wouldn't think so.

I also found no references to reboot, halt, or poweroff in any of the cron.daily scripts.  

I'll take a closer look at the logrotate script.  Let me know if you have any more ideas or more info of specifically what to look for there since, like I said, I didn't see any reboot-like commands.

thanks, 
psyncho

---

### Post by sonic2000gr on 2006-09-29
Yes you will not find any reference to a reboot or shutdown in a cron script, cause there shouldn't be any! A server is supposed to be up all the time. Since the time on the delphi message is also 6.25 my guess is this is again from a cron script and possibly logrotate.
For apache, the actual logrotation comes from the apache2 script in /etc/logrotate.d

The logrotation configuration file /etc/logrotate.conf contains a reference to run all scripts in /etc/logrotate.d 

The apache2 script has a 

  ```
if [ -f /var/run/apache2.pid ]; then
        /etc/init.d/apache2 restart > /dev/null
        fi
```

which restarts apache just after the rotation
So you should be getting an apache restart message in your logs just after the apache exiting message.
It should look something like:

```
[Sun Sep 03 06:25:50 2006] [notice] caught SIGTERM, shutting down [Sun Sep 03 06:25:51 2006] [notice] suEXEC mechanism enabled (wrapper: /usr/lib/apache2/suexec2)
[Sun Sep 03 06:25:51 2006] [notice] mod_security/1.9.4 configured [Sun Sep 03 06:25:52 2006] [notice] Apache/2.0.54 (Debian GNU/Linux) PHP/5.1.4-1.dotdeb.2 mod_ssl/2.0.54 OpenSSL/0.9.7e mod_perl/1.999.21 Perl/v5.8.4 configured -- resuming normal operations
```

If you don't have a restart, and assuming the shutdown comes from the logrotate as it looks, then it  would be just weird...

I would be tempted to run the logrotate script "by hand" and see what happens:
```

sudo /etc/cron.daily/logrotate
```

Manolis

P.S. I am actually using a debian server, but there is little difference here I believe.

---

### Post by jgeewax on 2006-10-27
I have been having a similar problem. I think it has to do with syslogd?

Every morning near 10 past 2, there is an entry in my syslog:
Oct 27 02:07:19 localhost syslogd 1.4.1#17ubuntu7: restart.

And the PC does a full system restart (actually power down, etc)

I cannot figure out why this is happening, and as a test I sudo ran all the files in /etc/cron.daily, and none of them restarted the machine.

Are there any other things I could do to test if the problem is with a script?

---

### Post by psyncho on 2006-10-27
Well, the first thing is to figure out what's executing the command.  You could try iterating through all of your logs (that's what I did) to see what events were correlated with the syslog entry.

Going through cron.daily was a great idea, too bad it didn't show up.

The PHP association seems like it might be good to look at web logs and whatever you've got going on with php.

Another thing to do is figure out what user or daemon is running the command.  I don't know of many things that would actually have permission to restart the machine other than root. You can look at the last root commands in bash_history in the root user directory.

Are there any emails sent reporting what happened? In that case, is the mail server setup correctly, one of my problems is I was changing the mail server to be sql based mailboxes and I hadn't set one up for root so I didn't get important system messages which made it even harder to track down my bug.

Is the computer exposed to the internet? Could it have been compromized and php code inserted somewhere that is restarting the machine? I don't know what this association is with php...but have you tried just uninstalling php5?  Look for all php files on your system and make sure you know what they are and how they got there and what they're doing.

if you think you got compromized you could also look at security postings to see about running a rootkit or other tools that look for things that are awry.

So really its about narrowing down what is actually restarting the machine, and then figuring out why.

And, there are a whole lot of people more knowledgable than me around this forum.  Keep searching here and on google for machine restarts and even things that don't seem completely related may lead you to things that are.

good luck,
John

---

