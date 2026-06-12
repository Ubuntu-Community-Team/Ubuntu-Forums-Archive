---
title: "postfix mail install headache's"
date: 2007-10-31
forum: Server Platforms
---

### Post by buddajah on 2007-10-31
i do not know if this is the right area to post this in, feel free to move it to the right area. 

i am trying to set up postfix, mysql, courier pop, sasl mail server. mind you this was not my idea but some how fell to me to get done.

currently i am using ubuntu 6 and the guide by flurdy found at [http://flurdy.com/docs/postfix/#test_sasl](http://flurdy.com/docs/postfix/#test_sasl)

right now i cannot telnet to localhost 25, authentication is failing and local delivery is bouncing back. can some one help. let me know what you need and i can post it here. thank you

---

### Post by HermanAB on 2007-10-31
Here, this will make your head-ache go away: [http://www.citadel.org](http://www.citadel.org)

It only takes about 20 minutes to install, is zero maintenance, provides all features and protocols that you can think of, plus a few more and can handle up to 256 Terrabytes of mail.  That should be enough for anybody.

Postfix is the new sendmail and is strictly for masochists...
;)

Herman

---

### Post by buddajah on 2007-10-31
another staff member and i both suggested this to "the Man" and wasn't having it. i like citidel and may run it at home soon. but for now "the man" would like us to "find a way to make it work". thank for posting i appreciate it.

---

### Post by buddajah on 2007-10-31
here are the tails of the current logs:

**_mail.err :_**

Oct 29 19:28:24 pill courierpop3login: LOGIN FAILED, ip=[::ffff:127.0.0.1]

Oct 29 19:31:08 pill amavis[3608]: TROUBLE in pre_loop_hook: db_home directory is not writable: /var/lib/amavis/db at /usr/sbin/amavisd-new line 6451.

**_mail.err.0 :_**

Oct 16 22:47:12 pill postfix/pipe[29567]: fatal: get_service_attr: unknown username: vmail

Oct 16 23:47:36 pill courierpop3login: LOGIN FAILED, ip=[::ffff:127.0.0.1]


**_mail.info :_**

Oct 30 19:05:04 pill authdaemond.mysql: modules="authmysql", daemons=5

Oct 30 19:05:10 pill postfix/master[4017]: daemon started -- version 2.2.10, configuration /etc/postfix

Oct 30 21:18:03 pill postfix/pickup[4295]: 3A4B4BA0DB: uid=106 from=<amavis>
Oct 30 21:18:03 pill postfix/cleanup[4321]: 3A4B4BA0DB: message-id=<20071031011803.3A4B4BA0DB@pill.fubar.com>

Oct 30 21:18:03 pill postfix/qmgr[4021]: 3A4B4BA0DB: from=<amavis@pill.fubar.com>, size=747, nrcpt=1 (queue active)

Oct 30 21:18:03 pill postfix/local[4328]: 3A4B4BA0DB: to=<amavis@pill.fubar.com>, orig_to=<amavis>, relay=local, delay=0, status=sent (delivered to
 mailbox)
Oct 30 21:18:03 pill postfix/qmgr[4021]: 3A4B4BA0DB: removed

**_mail.log :_**

Oct 28 06:18:51 pill postfix/virtual[17663]: 44EB8BA00B: to=<user@fubar.com>, relay=virtual, delay=447152, status=deferred (mailbox /var/spool/ma
il/virtual/Mail: cannot open file: Permission denied)

 **_mail.warn :_**

Oct 23 02:08:25 pill postfix/trivial-rewrite[12340]: warning: do not list domain localhost in BOTH mydestination and virtual_mailbox_domains

if there is anything i can post that would help please let me know. any help or suggestions are appreciated as well as ways to test/confirm things. thank you.

---

### Post by buddajah on 2007-10-31
ok, i was able to send mail using mutt to accounts setup for postfix when ssh'ed into the server. but i cannot telnet to localhost 25 and i cannot authenticate to the mail server via thunder bird or outlook express. can anyone help me out. i can post the text of the files you request. thank you

---

### Post by buddajah on 2007-10-31
i fixed the telnet issues :

root@pill:/etc/postfix# telnet localhost 25
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
220 pill.fubar.com ESMTP Postfix (Ubuntu)
ehlo pill.fubar.com
250-pill.fubar.com
250-PIPELINING
250-SIZE 10240000
250-ETRN
250-STARTTLS
250-AUTH LOGIN PLAIN
250-AUTH=LOGIN PLAIN
250 8BITMIME

i am unable to authenticate in any manner remotely.

---

### Post by buddajah on 2007-10-31
i guess i some how i never updated postgrey whitelist file. i was able to sent an email from a mail client. but not receive mail from the pop server, the error i am getting is : 

There was a problem logging onto your mail server. Your Password was rejected. Account: 'pill', Server: '192.168.1.26', Protocol: POP3, Server Response: '-ERR Login failed.', Port: 110, Secure(SSL): No, Server Error: 0x800CCC90, Error Number: 0x800CCC92

any idea's on how to fix this with courier-pop ?

---

