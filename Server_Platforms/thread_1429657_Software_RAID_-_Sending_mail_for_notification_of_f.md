---
title: "Software RAID - Sending mail for notification of failure"
date: 2010-03-14
forum: Server Platforms
---

### Post by urobb on 2010-03-14
Hi,

I am having troubles sending mail from my server, that is, getting my  mail accepted by the recipient.

I just want to be sure that I'm going to get an email when a disk fails  in my file server!

I have a fresh install of 9.10.. This is just a test installation (I  won't disable the root account on the real server)

Can anyone kindly give me any insight on this?  (I replaced my email  address with a dummy address)

root@ubuntu:~# echo 'hey buddy' | sendmail [email]me@example.com[/email]
root@ubuntu:~# tail /var/log/syslog
Mar 14 08:41:23 ubuntu postfix/pickup[957]: CF48937E5C: uid=0  from=<root>
Mar 14 08:41:23 ubuntu postfix/cleanup[1280]: CF48937E5C:  message-id=<20100314154123.CF48937E5C@ubuntu>
Mar 14 08:41:23 ubuntu postfix/qmgr[958]: CF48937E5C:  from=<root@ubuntu>, size=263, nrcpt=1 (queue active)
Mar 14 08:41:24 ubuntu postfix/smtp[1283]: CF48937E5C:  to=<me@example.com>,  relay=fltr-in2.mail.dreamhost.com[208.97.132.72]:25, delay=0.27,  delays=0.03/0.01/0.18/0.04, dsn=5.5.2, status=bounced (host  fltr-in2.mail.dreamhost.com[208.97.132.72] said: 504 5.5.2  <root@ubuntu>: Sender address rejected: need fully-qualified  address (in reply to RCPT TO command))
Mar 14 08:41:24 ubuntu postfix/cleanup[1280]: 1AA0837E5D:  message-id=<20100314154124.1AA0837E5D@ubuntu>
Mar 14 08:41:24 ubuntu postfix/qmgr[958]: 1AA0837E5D: from=<>,  size=2109, nrcpt=1 (queue active)
Mar 14 08:41:24 ubuntu postfix/bounce[1284]: CF48937E5C: sender  non-delivery notification: 1AA0837E5D
Mar 14 08:41:24 ubuntu postfix/qmgr[958]: CF48937E5C: removed
Mar 14 08:41:24 ubuntu postfix/local[1285]: 1AA0837E5D:  to=<root@ubuntu>, relay=local, delay=0.03, delays=0/0.01/0/0.01,  dsn=2.0.0, status=sent (delivered to command: procmail -a "$EXTENSION")
Mar 14 08:41:24 ubuntu postfix/qmgr[958]: 1AA0837E5D: removed

---

### Post by solar george on 2010-03-14
The problem you're seing is that the email doesn't come from a valid internet email address but from a local @ubuntu (i assume thats the hostname of your server).
I believe you can edit a file called /etc/mailname and set it to your fqdn (fully qualified domain name) i.e. including the .com or .co.uk

---

