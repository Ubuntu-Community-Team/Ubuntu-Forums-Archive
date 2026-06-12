---
title: "Hacked?  Or just misconfigured?"
date: 2007-01-29
forum: Server Platforms
---

### Post by va3uxb on 2007-01-29
Yesterday (Sunday) morning around 6:40 my Apache2 server at work stopped serving web pages.  I found out about 3 hours later when I got the phone call asking if something was broken.  I was able to access the system and found that Apache2 was down, and the apache error logs looked like the server was restarted.  We have SSL set up and a restart requires a pasword, and it looks like that's where the restart failed.  

Looking around I noticed that syslogd also restarted about the same time.  My first panic was someone compromised the system and was mucking about.  Then I realized that syslogd restarts that time every Sunday morning, it's in the cron.weekly.  I can't see anything though that would restart Apache2 at that time.

My concern is this - this server just went 'live' exactly a week before.  It's Ubuntu 6.06 LTS, server configuration, with absolutely nothing installed other than Apache2, SSL, and Perl.  Just a barebones Ubuntu, that serves webpages.  The only open ports are 80, 443, and a high-number unpublished port I use for ssh.  Prior to Ubuntu we were using RHEL and we made the switch because I said Ubuntu was easier to maintain and friendlier to use.  I've been running a 6.06 webserver personally since last July without a single problem.  

Any suggestions or advice would be most welcome.  I'm no Linux guru, I'm self taught, and some aspects leave me completely befuddled.  Unfortunately we're a small business and I've got the system-admin responsibilities, without all the training and resources.

Thanks very much.

-Stephanie

---

### Post by kerry_s on 2007-01-29
Any power outages? Could it have got to hot? Did you check the auth.log to see if any one accessed root besides you?

---

### Post by va3uxb on 2007-01-29
Thanks for the reply.

The physical server itself didn't shut down, it was just apache2.  The log /var/log/apache2/error.log shows a sigTerm at 06.25 which coincides with the time that cron.daily is supposed to run, which is why I'm not sure what's going on.  The lines from error.log:
```
[Sun Jan 28 06:25:04 2007] [notice] caught SIGTERM, shutting down
[Sun Jan 28 06:25:05 2007] [error] Init: Unable to read pass phrase [Hint: key introduced or changed before restart?]
[Sun Jan 28 06:25:05 2007] [error] SSL Library Error: 218710120 error:0D094068:asn1 encoding routines:d2i_ASN1_SET:bad tag
[Sun Jan 28 06:25:05 2007] [error] SSL Library Error: 218529960 error:0D0680A8:asn1 encoding routines:ASN1_CHECK_TLEN:wrong tag
[Sun Jan 28 06:25:05 2007] [error] SSL Library Error: 218595386 error:0D07803A:asn1 encoding routines:ASN1_ITEM_EX_D2I:nested asn1 error
[Sun Jan 28 06:25:05 2007] [error] SSL Library Error: 218734605 error:0D09A00D:asn1 encoding routines:d2i_PrivateKey:ASN1 lib
```

auth.log shows at 06.25.01 a CRON session opened for user root, and at 06.25.02 it shows an su by root:nobody which is adding to my confusion.  Here's the lines from auth.log:
```
Jan 28 06:25:01 webster CRON[15278]: (pam_unix) session opened for user root by (uid=0)
Jan 28 06:25:02 webster su[15309]: + ??? root:nobody
Jan 28 06:25:02 webster su[15309]: (pam_unix) session opened for user nobody by (uid=0)
Jan 28 06:25:02 webster su[15309]: (pam_unix) session closed for user nobody
Jan 28 06:25:02 webster su[15311]: + ??? root:nobody
Jan 28 06:25:02 webster su[15311]: (pam_unix) session opened for user nobody by (uid=0)
Jan 28 06:25:02 webster su[15311]: (pam_unix) session closed for user nobody
Jan 28 06:25:02 webster su[15313]: + ??? root:nobody
Jan 28 06:25:02 webster su[15313]: (pam_unix) session opened for user nobody by (uid=0)
Jan 28 06:25:02 webster su[15313]: (pam_unix) session closed for user nobody
```

The fact that it all seems to coincide with the timing of cron.daily is making me think there's something going on there.  Except that the first 6 days, apache did not stop.  Just sunday.  Cron.weekly doesn't run till 6.47 but apache was already down by then.

This was a clean install of Ubuntu 6.06 LTS server by the way, installed in an off-line environment in December, put live on Jan 21st, and fully up to date with apt.

Thanks again!

-Stephanie

---

### Post by MJN on 2007-01-30
The daily/weekly log rotations often restart services in order to free up the existing logfile - after all you can't rotate (or doing anything involving writing to) a logfile whilst it's still in use as a race condition could occur where Apache is trying to write to a log whilst syslogd is trying to perform log rotatation (or whatever).
 
However, as Apache is not a service logged by syslog I'd suspect logrotate - check /etc/logrotate.d/apache and see if it is set to reload Apache (it should do) then check when logrotate is being executed by cron.
 
If you're after reassurance I can dig out the relevent portions of the config which prove one way or another if/when this is the case (I'm at work right now and don't have access to my machine).
 
This is all perfectly normal behaviour - I am surprised you haven't seen it before or has the passphrase-protected SSL certificate only recently been loaded? (Edit: Just noticed the Jan 21st date... no wonder! You'd better get used to this, or a) stop logrotate working on Apache files, b) increase the rotation period to something much less frequent, or c) remove the certificate passphrase. Other solutions may also exist.)
 
Mathew
 
P.S. Hopefully now you can relax! ;)

---

### Post by va3uxb on 2007-01-30
Thank you so much!  Logrotate was indeed to blame.  The logs rotated again this moring and apache went down again.  I found the command in /etc/logrotate.d/apache2, it was issuing the restart to apache.

The thing that seems wierd to me is we never had this problem on RHEL.  We've had the password on our SSL thing for 2 or 3 years, and logrotate on RHEL never restarted apache.

I don't understand why logrotate has to restart apache now...I sort of get what you're saying, but also don't.  If it's just writing to a log file, why would have to be affected or even notice if the log file was suddenly empty?

I've disabled the part of logrotate that restarts apache just to see what happens.

Thanks again - I do feel much better knowing what the cause is! 

-Stephanie

---

### Post by MJN on 2007-01-30
It's not so much that the logfile is suddenly empty (it wouldn't know as it's only adding to the end of it) but rather the fact that the logfile doesn't even exist given that logrotate has rotated (moved) it into <logfile>.0(or .1.gz,.2.gz etc).
 
Hence the reason for the restart - it creates a new logfile if one doesn't exist as a matter of course without hesitation.
 
Given your Apache won't be restarted it will suddenly find itself without a logfile. I have no idea how it will react when this happens - easy to test of course (I'll keep an eye out for your post at ~7am next Sunday! ;) - it could fall over depending on the native error handling of this case.
 
From what I understand the logrotate config files are provided by the application developer, i.e. Apache in this case - if they want the server restarting every log rotate then that's what they want. Of course it doesn't mean it's necessarilly the best for your particular circumstances.
 
However, as mentioned, you would be far better off sticking with the intended function of logrotate (i.e. a restart of Apache every rotation) and removing the passphrase from the server key. If the key is only readable by root then you should have little qualms about doing this. See [http://httpd.apache.org/docs/2.0/ssl/ssl_faq.html#removepassphrase](http://httpd.apache.org/docs/2.0/ssl/ssl_faq.html#removepassphrase) for details of how to do this (it's really very simple).
 
What's more, if the passphrase is removed from the key then you can also take advantage of automatic reboots following power failures etc.
 
Mathew

---

### Post by va3uxb on 2007-01-30
Thanks for the clarification Mathew.

I've bookmarked that link re. the SSL password.  After a few years of it, I'm kind of fond of it, knowing nobody can start apache other than those with the password.  Maybe its false security but it 'feels good' :-)

I'm going to let it go for a week with the restarts disabled and see what happens.  I have the logrotate config set up to create a new log file, so there shouldn't be a problem of apache not finding the file, it'll just be an empty one all of a sudden.  

It's good knowing though of the alternative, if this breaks then I'll follow your full advice and remove the ssl password then let logrotate do what it wants.

Cheers!

-Stephanie

---

### Post by MJN on 2007-01-30
> **va3uxb said:**
> Thanks for the clarification Mathew.
 
I've bookmarked that link re. the SSL password. After a few years of it, I'm kind of fond of it, knowing nobody can start apache other than those with the password. Maybe its false security but it 'feels good'
 
I understand. However just for the record it is indeed false security... ;)
 
Nobody but root can start Apache. If someone has root access then they've also got Apache config access. If they've got Apache config access they can remove/change the SSL etc etc... Heck, they can even replace your private key with their own!
 
Don't say I didn't warn you when you're called out at 4am just because a power line spike rebooted the machine - the filesystem is fine, all other services have happily restarted, yet Apache is sat around waiting for the passphrase...! :D 
 
All the best,
 
Mathew
 
P.S. Note that that link is to the official Apache docs, hence not some misguided HowTo!

---

### Post by va3uxb on 2007-02-07
Well I had to see how it worked for myself but you were right it did bite me in the behind...

Without restarting Apache, it doesn't acknowledge the new log files, and so even though the new error.log exists, Apache continues writing to the former log - even after it was renamed error.log.1

So the restart is required, so I've removed the pass phrase and set the logrotate.d file back to its original configuration.

Just figured I'd post the outcome here incase anyone else was interested or had a similar situation.

Thanks again for the help!

-Stephanie

---

### Post by MJN on 2007-02-07
Goot to hear you're sorted, and thanks for posting the result back. At least now we know for certain what happens in these circumstances!
 
Mathew

---

