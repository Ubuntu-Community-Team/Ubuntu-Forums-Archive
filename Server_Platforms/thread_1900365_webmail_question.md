---
title: "webmail question"
date: 2011-12-26
forum: Server Platforms
---

### Post by johnno40 on 2011-12-26
Hi All,
Running a mailserver with virtual users, postfix and imap/pop.
Since 4th december, after reboot I can not login to my webmail client(s) from externally, but from my internal network no problems at all?!?

Closer looks at logs gave me a hint SSL was not working so I followed [http://ubuntuforums.org/showthread.php?t=1859667&page=2](http://ubuntuforums.org/showthread.php?t=1859667&page=2) and solved the problem (thanks!).

So I tried several solutions, changed my IMAP/POP client from dovecot to courier. Rebuild php5, gave write permissions to the session directory (as squirrel suggests at their site). Changed squirrel for Roundcube. But all with no result. Rebuild postfix and put any debug option to log errors. Rebooted/reloaded every step.

In my mail.log I see a direct login/logout from IMAP. I'm sure I overlook something, any help would be great!

John.

Running Ubuntu 10.04.3 LTS, 
- postfix 2.8.5 compiled with TLS/SSL
- mysql virtual users
- postfixadmin
- courier imap,pop (and the ssl packages)
- lighttpd/1.4.26 (ssl)
- roundcube /squirrelmail
- PHP 5.3.2-1ubuntu4.11 with Suhosin-Patch (cli)

---

### Post by lisati on 2011-12-26
Have you changed anything in your hostname settings? I recently tinkered with mine, with a view to changing the primary domain name that my email system uses, and found that I couldn't login via roundcube. Changing it back got things working again.

---

### Post by johnno40 on 2011-12-26
Hi Lisati,

As good practice I backup my /etc and /var every month.
Back-uped the /etc did not help.

This is what I see when I log in:

> Dec 26 12:17:40 webserver roundcube: query(1): SELECT vars, ip, changed FROM session WHERE sess_id = 'oi6dcndntolqdhfirquvqb67i1';
Dec 26 12:17:40 webserver roundcube: query(1): DELETE FROM session WHERE sess_id = '********tolqdhfirquvqb67i1';
Dec 26 12:17:40 webserver roundcube: query(1): INSERT INTO session (sess_id, vars, ip, created, changed) VALUES ('********tolqdhfirquvqb67i1', '********2V8czo1OiJubF9OTCI7dGVtcHxiOjE7', '159.253.0.74', '2011-12-26 12:1

When I try to login from a website outside my network with anomynous proxy.

This is how it looks like when I enter from internal:
> Dec 26 12:21:28 webserver roundcube: query(1): SELECT vars, ip, changed FROM session WHERE sess_id = '*******cl1gma0p6ccstfib31';
Dec 26 12:21:28 webserver roundcube: query(1): UPDATE session SET changed='2011-12-26 12:21:28' WHERE sess_id='********cl1gma0p6ccstfib31';
Dec 26 12:21:36 webserver roundcube: query(1): SELECT vars, ip, changed FROM session WHERE sess_id = '*******1gma0p6ccstfib31';
Dec 26 12:21:36 webserver roundcube: query(1): DELETE FROM session WHERE sess_id = '********cl1gma0p6ccstfib31';
Dec 26 12:21:36 webserver roundcube: query(1): SELECT * FROM users WHERE mail_host = '192.168.1.**' AND username = BINARY 'XXXXXXXXXX@droppert.net';
Dec 26 12:21:36 webserver imapd: Connection, ip=[::ffff:192.168.1.46]
Dec 26 12:21:36 webserver roundcube: [8D09] S: * OK [CAPABILITY IMAP4rev1 UIDPLUS CHILDREN NAMESPACE THREAD=ORDEREDSUBJECT THREAD=REFERENCES SORT QUOTA IDLE ACL ACL2=UNION STARTTLS] Courier-IMAP ready. Copyright 1998-2008 Double Precision, Inc.  See COPYING for distribution information.
Dec 26 12:21:36 webserver roundcube: [8D09] C: A0001 LOGIN [email]XXXXXXXXX@droppert.net[/email] XXXXXXXXX


Any clue?

Thanks already!

---

### Post by johnno40 on 2011-12-29
Still looking for an answer.
I changed back from roundcube to squirrelmail.
Still no login from external.

I tried with mutt.
mutt -f imap://my.ip.add.ress/

and login to IMAP was permitted.
So defenitally a login or security error?

What options can I check more :confused: ??

Any clue would be appriciated.

---

### Post by johnno40 on 2011-12-29
In the php.ini I changed session.use_cookies from 1 to 0 and the option to save the sessions into the /tmp directory.

webmail options from internal do have a value of about 1.800 bytes, external have 66 bytes or less. This is the content:

> session_expired_post|a:0:{}session_expired_location|s:7:"webmail";

Thanks again.

John.

---

