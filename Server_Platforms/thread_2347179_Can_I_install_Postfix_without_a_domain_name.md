---
title: "Can I install Postfix without a domain name?"
date: 2016-12-22
forum: Server Platforms
---

### Post by agarwaldvk on 2016-12-22
Hi Everyone


I have done some reading and I believe that some sort of MTA need to be installed on the system for it to be able to send out email notifications to the administrator e.g completion and status notifications for cron jobs etc.

It appears that Postfix is among the easier of the various tools available for the purpose. But from what I have so far read, it appears that it needs a domain name for it to work. I was wondering if its at all possible to install and configure Postfix without a domain name - my server doesn't have one.

I have also heard that 'ssmtp' can also perform this job - send out application email notifications - using my existing gmail account - and I am more than happy to use it for this purpose. I don't intend to use this service to receive messages - sending out application messages is all I need this system for.

Any advice/suggestions as to whether I should try and install Postfix or 'ssmtp' should suffice would be greatly appreciated.


Edit
Just read about 'Mutt' as well - is this a good option to consider for the purpose?



Best regards


Deepak

---

### Post by SeijiSensei on 2016-12-22
By default Postfix comes configured to accept mail on the localhost address (127.0.01).  It doesn't "need" a domain name, but every computer should have a hostname.  What does the command "hostname" return?  If it's empty, create a name for the machine with "sudo hostname name_you_chose".  It need not by "fully-qualified" with a domain; something my "mypc" is fine.

---

### Post by agarwaldvk on 2016-12-22
Hi SeijiSensei 


Thanks for your response.


The hostname command with or without -f option comes up with 'MyHomeServer'. The 'domainname' command comes up with nothing as I don't have one.

So how do I then install Postfil - it asks for the domain name as an entry in the 'Mail System Name' - in most documentation that I have read they say use something like 'example.com' or 'linuxbabe.com' (for the documentation provided by them) etc.

What should I use or is there a get around to this? Or simply can I use the hostname for both the hostname and the domain names?


Best regards


Deepak

---

### Post by SeijiSensei on 2016-12-22
Try using "localdomain" for the domain name, and check /etc/hosts to see if that name is also used for the 127.0.0.1 interface.  If not, add it like this
```
127.0.0.1     localhost localhost.localdomain
```

---

### Post by agarwaldvk on 2016-12-22
Hi SeijiSensei 


Thanks again!

I will do that tonight and keep you posted.

What if that name ('localdomain') is already in that file (/etc/hosts), then do I do nothing and it should work, yeah?



Have a good and safe Christmas and New Year!


Best regards


Deepak

---

### Post by SeijiSensei on 2016-12-22
Yes, just leave it as it is.

---

### Post by agarwaldvk on 2016-12-22
Hi SeijiSensei 


Good-O, mate! Thanks!


Will try that tonight!


Best regards


Deepak

---

### Post by agarwaldvk on 2016-12-25
Hi All

I installed Postfix yesterday and did all the configurations as required - so I think - based on what I found on the net! But I tried to send a test mail - this is the output of the log

Can anyone suggest of the possible remedy?


```

Dec 26 09:29:07 MyHomeServer postfix/qmgr[7900]: warning: private/smtp socket: malformed response
Dec 26 09:29:07 MyHomeServer postfix/master[7898]: warning: process /usr/lib/postfix/sbin/smtp pid 29550 exit status 1
Dec 26 09:29:07 MyHomeServer postfix/master[7898]: warning: /usr/lib/postfix/sbin/smtp: bad command startup -- throttling
Dec 26 09:29:07 MyHomeServer postfix/qmgr[7900]: warning: transport smtp failure -- see a previous warning/fatal/panic logfile record for the problem description
Dec 26 09:29:07 MyHomeServer postfix/error[29553]: EE035601FA2: to=<deepakagarwalathome@gmail.com>, relay=none, delay=4.5, delays=0.04/4.4/0/0.02, dsn=4.3.0, status=deferred (unknown mail transport error)
Dec 26 09:30:05 MyHomeServer postfix/pickup[28736]: D5F09601FA6: uid=1000 from=<agarwaldvk@MyHomeServer>
Dec 26 09:30:05 MyHomeServer postfix/cleanup[29548]: D5F09601FA6: message-id=<20161225223005.D5F09601FA6@MyHomeServer.home.gateway>
Dec 26 09:30:05 MyHomeServer postfix/qmgr[7900]: D5F09601FA6: from=<agarwaldvk@MyHomeServer>, size=395, nrcpt=1 (queue active)
Dec 26 09:30:05 MyHomeServer postfix/error[29553]: D5F09601FA6: to=<deepakagarwalathome@gmail.com>, relay=none, delay=0.05, delays=0.03/0/0/0.01, dsn=4.3.0, status=deferred (unknown mail transport error)
Dec 26 09:34:18 MyHomeServer postfix/qmgr[7900]: EE035601FA2: from=<agarwaldvk@MyHomeServer>, size=395, nrcpt=1 (queue active)
Dec 26 09:34:18 MyHomeServer postfix/qmgr[7900]: 0625D601E17: from=<agarwaldvk@MyHomeServer>, size=395, nrcpt=1 (queue active)
Dec 26 09:34:18 MyHomeServer postfix/smtp[29672]: error: open database /etc/postfix/generic.db: No such file or directory
Dec 26 09:34:19 MyHomeServer postfix/smtp[29673]: error: open database /etc/postfix/generic.db: No such file or directory
Dec 26 09:34:22 MyHomeServer postfix/smtp[29672]: warning: hash:/etc/postfix/generic is unavailable. open database /etc/postfix/generic.db: No such file or directory
Dec 26 09:34:22 MyHomeServer postfix/smtp[29672]: warning: hash:/etc/postfix/generic lookup error for "agarwaldvk@MyHomeServer"
Dec 26 09:34:22 MyHomeServer postfix/smtp[29672]: fatal: smtp_generic_maps map lookup problem for agarwaldvk@MyHomeServer
Dec 26 09:34:22 MyHomeServer postfix/smtp[29673]: warning: hash:/etc/postfix/generic is unavailable. open database /etc/postfix/generic.db: No such file or directory
Dec 26 09:34:22 MyHomeServer postfix/smtp[29673]: warning: hash:/etc/postfix/generic lookup error for "agarwaldvk@MyHomeServer"
Dec 26 09:34:22 MyHomeServer postfix/smtp[29673]: fatal: smtp_generic_maps map lookup problem for agarwaldvk@MyHomeServer
Dec 26 09:34:23 MyHomeServer postfix/qmgr[7900]: warning: private/smtp socket: malformed response
Dec 26 09:34:23 MyHomeServer postfix/master[7898]: warning: process /usr/lib/postfix/sbin/smtp pid 29672 exit status 1
Dec 26 09:34:23 MyHomeServer postfix/master[7898]: warning: /usr/lib/postfix/sbin/smtp: bad command startup -- throttling
Dec 26 09:34:23 MyHomeServer postfix/qmgr[7900]: warning: transport smtp failure -- see a previous warning/fatal/panic logfile record for the problem description
Dec 26 09:34:23 MyHomeServer postfix/qmgr[7900]: warning: private/smtp socket: malformed response
Dec 26 09:34:23 MyHomeServer postfix/master[7898]: warning: process /usr/lib/postfix/sbin/smtp pid 29673 exit status 1
Dec 26 09:34:23 MyHomeServer postfix/qmgr[7900]: warning: transport smtp failure -- see a previous warning/fatal/panic logfile record for the problem description
Dec 26 09:34:23 MyHomeServer postfix/error[29674]: EE035601FA2: to=<deepakagarwalathome@gmail.com>, relay=none, delay=320, delays=316/4.1/0/0.01, dsn=4.3.0, status=deferred (unknown mail transport error)
Dec 26 09:34:23 MyHomeServer postfix/error[29675]: 0625D601E17: to=<deepakagarwalathome@gmail.com>, relay=none, delay=975, delays=971/4.1/0/0.02, dsn=4.3.0, status=deferred (unknown mail transport error)

```


Further, it appears that for some reason its not able to find the 'generic.db' file - where is this file normally supposed to reside?


Best regards


Deepak

---

### Post by agarwaldvk on 2016-12-26
Hi  All


This now works. A big thanks to everyone who helped me get this going!

I am marking this as Solved.


Best regards


Deepak

---

