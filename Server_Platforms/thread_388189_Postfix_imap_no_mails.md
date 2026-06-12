---
title: "Postfix imap no mails"
date: 2007-03-19
forum: Server Platforms
---

### Post by sjaakmans on 2007-03-19
Hello,

I have postfix installed with courier. Last week everything worked fine but know i cant get any mails in my inbox. When i send a mail in the mail log stands that i received it.

Is any one familiar with this problem?

Greetings,

Sjaakmans

---

### Post by astrogazer on 2007-03-19
What do your logs say?

---

### Post by sjaakmans on 2007-03-19
This sais my log: 
> Mar 19 13:11:26 sjaakmansserver imapd: LOGIN, user=sjaakmans, ip=[::ffff:127.0.0.1], protocol=IMAP
Mar 19 13:11:26 sjaakmansserver imapd: LOGOUT, user=sjaakmans, ip=[::ffff:127.0.0.1], headers=0, body=0, rcvd=25, sent=180, $
Mar 19 13:11:45 sjaakmansserver postfix/smtpd[3791]: connect from smtp19.wxs.nl[195.121.247.10]
Mar 19 13:11:45 sjaakmansserver postfix/smtpd[3791]: 238203409D: client=smtp19.wxs.nl[195.121.247.10]
Mar 19 13:11:45 sjaakmansserver postfix/cleanup[3796]: 238203409D: message-id=<393e4dc393c976.393c976393e4dc@planet.nl>
Mar 19 13:11:45 sjaakmansserver postfix/qmgr[3573]: 238203409D: from=<dam02249@planet.nl>, size=1438, nrcpt=1 (queue active)
Mar 19 13:11:45 sjaakmansserver postfix/smtpd[3791]: disconnect from smtp19.wxs.nl[195.121.247.10]
Mar 19 13:11:45 sjaakmansserver postfix/local[3797]: 238203409D: to=<sjaakmans@jacobvandam.nl>, relay=local, delay=0.15, del$
Mar 19 13:11:45 sjaakmansserver postfix/qmgr[3573]: 238203409D: removed
Mar 19 13:11:49 sjaakmansserver imapd: Connection, ip=[::ffff:127.0.0.1]
Mar 19 13:11:49 sjaakmansserver imapd: LOGIN, user=sjaakmans, ip=[::ffff:127.0.0.1], protocol=IMAP
Mar 19 13:11:49 sjaakmansserver imapd: LOGOUT, user=sjaakmans, ip=[::ffff:127.0.0.1], headers=302, body=0, rcvd=247, sent=10$


---

### Post by astrogazer on 2007-03-19
Provide full length log entries, important information might be there

---

### Post by sjaakmans on 2007-03-19
Do you want my mail.log and mail.log.0? i have ubuntu 6.10 server i forget to say that

---

### Post by astrogazer on 2007-03-19
The portion of the log you have previously posted is suffice, but, you are missing some chars at the end of some crucial lines.

---

### Post by sjaakmans on 2007-03-19
Ohw yes i see may bad sorry

Here it is
> Mar 19 13:11:26 sjaakmansserver imapd: Connection, ip=[::ffff:127.0.0.1]
Mar 19 13:11:26 sjaakmansserver imapd: LOGIN, user=sjaakmans, ip=[::ffff:127.0.0.1], protocol=IMAP
Mar 19 13:11:26 sjaakmansserver imapd: LOGOUT, user=sjaakmans, ip=[::ffff:127.0.0.1], headers=0, body=0, rcvd=25, sent=180, time=0
Mar 19 13:11:45 sjaakmansserver postfix/smtpd[3791]: connect from smtp19.wxs.nl[195.121.247.10]
Mar 19 13:11:45 sjaakmansserver postfix/smtpd[3791]: 238203409D: client=smtp19.wxs.nl[195.121.247.10]
Mar 19 13:11:45 sjaakmansserver postfix/cleanup[3796]: 238203409D: message-id=<393e4dc393c976.393c976393e4dc@planet.nl>
Mar 19 13:11:45 sjaakmansserver postfix/qmgr[3573]: 238203409D: from=<dam02249@planet.nl>, size=1438, nrcpt=1 (queue active)
Mar 19 13:11:45 sjaakmansserver postfix/smtpd[3791]: disconnect from smtp19.wxs.nl[195.121.247.10]
Mar 19 13:11:45 sjaakmansserver postfix/local[3797]: 238203409D: to=<sjaakmans@jacobvandam.nl>, relay=local, delay=0.15, delays=0.03/0/0/0.12, dsn=2.0.0, status=sent (delivered to command: procmail -a "$EXTENSION")
Mar 19 13:11:45 sjaakmansserver postfix/qmgr[3573]: 238203409D: removed
Mar 19 13:11:49 sjaakmansserver imapd: Connection, ip=[::ffff:127.0.0.1]
Mar 19 13:11:49 sjaakmansserver imapd: LOGIN, user=sjaakmans, ip=[::ffff:127.0.0.1], protocol=IMAP
Mar 19 13:11:49 sjaakmansserver imapd: LOGOUT, user=sjaakmans, ip=[::ffff:127.0.0.1], headers=302, body=0, rcvd=247, sent=1072, time=0


---

### Post by Mr. C. on 2007-03-19
The mail is being delivered to procmail.  Perhaps you have the same issue as this poster:

[http://tinyurl.com/ypclm7](http://tinyurl.com/ypclm7)

MrC

---

### Post by sjaakmans on 2007-03-19
No, i did not update my postfix. But once i changed  /etc/aliases since i did that i get this error... maybe i should remove postfix and everything what comes whit it so i can do a clean install.

How can i do a clean install i mean that also all the config files will be removed and everything what comes with it

---

### Post by Mr. C. on 2007-03-19
You want to throw the baby out with the bathwater ?

The problem is in your /etc/aliases file.  You made a change, and don't understand why the alias no longer works.  It would certainly be better to understand what procmail is receiving, and see what EXTENSION is evaluating to.

I can't tell you how to remove postfix, since you've not indicated how you installed it in the first place.

MrC

---

### Post by sjaakmans on 2007-03-19
I have installed it with this tutorial:

[http://www.howtoforge.com/perfect_setup_ubuntu_6.10](http://www.howtoforge.com/perfect_setup_ubuntu_6.10)

---

### Post by Mr. C. on 2007-03-19
I'm not going to chase down tutorials to find how you installed it.  Sorry.

If you're going to blindly follow someone's cookbook recipe, be prepared for trouble.

Why not *learn* how and why it is not working?

MrC

---

### Post by sjaakmans on 2007-03-19
Problem solved.. 

> postconf -e 'home_mailbox = Maildir/'
postconf -e 'mailbox_command ='
/etc/init.d/postfix restart did have to do this...

---

