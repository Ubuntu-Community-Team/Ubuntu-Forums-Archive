---
title: "Postfix error: private/smtp No such file or directory"
date: 2011-12-28
forum: Server Platforms
---

### Post by sohmc on 2011-12-28
Good afternoon and happy new year!

I'm in the process of moving to a new server and am running Ubuntu 11.10.  It looks like dovecot was upgraded to 2.0, which is a major revision to what was there before (1.something).

In the process, it looks like my old config files no longer work so I'm down to starting from scratch.  I'm racking my brain with an issue.  I can receive mail fine but cannot send mail out:

```
Dec 27 08:43:17 helo postfix/anvil[21959]: statistics: max connection rate 1/60s for (smtp:117.201.49.196) at Dec 27 08:39:55
Dec 27 08:43:17 helo postfix/anvil[21959]: statistics: max connection count 1 for (smtp:117.201.49.196) at Dec 27 08:39:55
Dec 27 08:43:17 helo postfix/anvil[21959]: statistics: max cache size 1 at Dec 27 08:39:55
Dec 27 08:43:47 helo postfix/qmgr[56377]: 400B263200CC: from=<someaddress@helo.mikesoh.com>, size=2389, nrcpt=1 (queue active)
Dec 27 08:43:47 helo postfix/qmgr[56377]: warning: connect to transport private/smtp: No such file or directory
Dec 27 08:43:47 helo postfix/error[36098]: 400B263200CC: to=<someaddress@gmail.com>, relay=none, delay=315493, delays=315493/0.01/0/0.02, dsn=4.3.0, status=deferred (mail transport unavailable)
```

Now, upon inspection, it looks like the socket to the smtp service does not exist on /var/spool/postfix/private

How do I create this?  I've set up dovecot to create the SASL authentication correctly (at least I think so) since I can log into the server.  Mail within the system seems fine (outside the fact that spamassassin is logging it as spam, but that's a whole other issue).

---

### Post by collisionystm on 2011-12-28
Not sure what you did as far as moving config files, but did you try to copy the entire folder from /etc/dovecot or did you just copy the 1 or 2 config files

---

### Post by sohmc on 2011-12-28
Since dovecot drastically changed their config files, copying the entire directory was out of the question.  I modified the files as needed by following their wiki.

---

### Post by collisionystm on 2011-12-28
in your main.cf 

do you have mynetworks defined? You need this to allow relay to you mail system from clients

I.E. Mine is


mynetworks = 127.0.0.0/8 172.16.128.0/19 192.168.16.0/24 192.168.7.0/24 172.16.32.0/19 172.16.64.0/19 172.16.192.0/19

---

### Post by sohmc on 2011-12-29
mynetworks isn't the issue, but I'll post it here anyway:
```
mynetworks = 127.0.0.0/8, [::ffff:127.0.0.0]/104, [::1]/128,    205.251.65.0/24

```

I'm sending mail directly on the server to offsite.

---

### Post by sohmc on 2011-12-29
I decided to start postfix from scratch, just like dovecot and I'm now one step closer.  Now when I try to send mail I get:

```
Dec 29 09:18:32 helo postfix/pickup[12071]: 2DF4A63200D0: uid=0 from=<root>
Dec 29 09:18:32 helo postfix/cleanup[13698]: 2DF4A63200D0: message-id=<20111229141832.2DF4A63200D0@helo.mikesoh.com>
Dec 29 09:18:32 helo postfix/qmgr[12070]: 2DF4A63200D0: from=<root@helo.mikesoh.com>, size=600, nrcpt=1 (queue active)
Dec 29 09:18:32 helo postfix/qmgr[12070]: warning: connect to transport private/smtp: Connection refused
Dec 29 09:18:32 helo postfix/error[13700]: 2DF4A63200D0: to=<someaddress@gmail.com>, relay=none, delay=43, delays=43/0/0/0.01, dsn=4.3.0, status=deferred (mail transport unavailable)
```

So now, private/smtp exists, but localhost is getting connection refused.  I'm looking on google for some help, but wanted to update the thread.

---
EDIT:

It looks like there was a problem with my master.cf configuration.  Even though I copied the proper entries for [SASL from dovecot](http://wiki2.dovecot.org/HowTo/PostfixAndDovecotSASL?action=show&redirect=PostfixAndDovecotSASL), it looks like the Ubuntu distro didn't like them.  The Ubuntu distro came with a "submission" entry within master.cf and when uncommented, it provided the appropriate information.

For the curious, the submission entry should look like this:
```
submission inet n       -       -       -       -       smtpd
  -o smtpd_tls_security_level=encrypt
  -o smtpd_sasl_auth_enable=yes
  -o smtpd_client_restrictions=permit_sasl_authenticated,reject
  -o milter_macro_daemon_name=ORIGINATING
```

---

