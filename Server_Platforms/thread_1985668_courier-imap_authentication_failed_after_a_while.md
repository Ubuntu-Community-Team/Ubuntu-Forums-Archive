---
title: "courier-imap: authentication failed after a while"
date: 2012-05-23
forum: Server Platforms
---

### Post by clement.analogue on 2012-05-23
Hi,

Authentication failed for imapd and imapd-ssl after a while for some users, not always the same ones, at different times (between half an hour and few days). My MDA is courier-imap and courier-imap-ssl.

The logs (mails.log) using thunderbird with ssl:
```
May 21 17:47:03 clement-desktop imapd-ssl: Connection, ip=[::ffff:192.168.1.11]
```Same using roundcube without ssl:
```
May 21 17:48:09 clement-desktop imapd: Connection, ip=[::ffff:192.168.1.11]
```Same thing with ssl.

Roundcube logs:
```
[23-May-2012 19:38:27 +0200]: IMAP Error: Login failed for ****** from xx.xxx.xxx.xxx. AUTHENTICATE PLAIN:  in /usr/share/roundcube/program/include/rcube_imap.php on line 205 (POST /roundcube/?_task=login&_action=login)
```I tried to restart some service: courier-imap, courier-imap-ssl, courier-authdaemon, saslauthd. But still not working. The only way I found is to reboot the server :/
I'm not sure, but I think it's since I upgraded from 10.04 to 12.04. Before that, it worked fine.

Any idea ?
Thanks

Edit: This post solved my problem :
[http://ubuntuforums.org/showpost.php...2&postcount=16]("http://ubuntuforums.org/showpost.php?p=11902102&postcount=16")

---

### Post by rabbadabb on 2012-05-24
I have the same issue after updating to 12.04. Tried to restart saslauthd, postfix, courier-imap all of it. Nothing works, only reboot of the server.
To note is that the users look authenticated in the maillog, only error I can find is in auth.log:  postfix/smtpd[13906]: unable to dlopen /usr/lib/sasl2/libsql.so.2: libmysqlclient.so.16: cannot open shared object file: No such file or direct

Not sure if this is caused by the other bug my installation is suffering from.

---

### Post by clement.analogue on 2012-05-24
Nothing happened in the auth.log file.

---

### Post by clement.analogue on 2012-05-27
up

---

### Post by Migrus on 2012-06-04
Been having the same issue. telnet to the imap server simply disconnects when trying to login, eg:

```
$ telnet localhost imap
* OK [CAPABILITY IMAP4rev1 UIDPLUS CHILDREN NAMESPACE THREAD=ORDEREDSUBJECT THREAD=REFERENCES SORT QUOTA IDLE ACL ACL2=UNION] Courier-IMAP ready. Copyright 1998-2011 Double Precision, Inc.  See COPYING for distribution information. 
. login user correctpassword
Connection closed by foreign host.
```For me killing the gam_server process makes me able to connect to the imap server and access my emails.

See this thread and bugreport
[http://ubuntuforums.org/showthread.php?t=1970712](http://ubuntuforums.org/showthread.php?t=1970712)
[https://bugs.launchpad.net/ubuntu/+source/courier/+bug/890756](https://bugs.launchpad.net/ubuntu/+source/courier/+bug/890756)

---

### Post by clement.analogue on 2012-06-04
I saw the bug and the thread. This post solved my problem :
[http://ubuntuforums.org/showpost.php?p=11902102&postcount=16](http://ubuntuforums.org/showpost.php?p=11902102&postcount=16)

---

### Post by rabbadabb on 2012-06-05
Hoping for this to solve my problems! Thanks in advance!

---

### Post by cdean on 2012-06-10
Encountered this problem on a new 12.04 server after moving a configuration over from an old 8.04 server. Troubling and frustrating!

---

### Post by jongers on 2012-06-12
I had this problem during the Beta.
please check This [post]("http://ubuntuforums.org/showthread.php?t=1959912"), It seems like the same issue.

rgds
J

---

### Post by clement.analogue on 2012-06-12
I already solved the problem and the solution is in this thread. I edited the fisrt message to give the link which solved the issue.

---

### Post by lazloman on 2012-07-11
Rebooting worked for me as well, it seems. As some folks have noted, the issue came back after a while, in which case, I'll try the solution listed in another post. But I have to say this a red letter day for me. Never before in 12 years of linux have I ever had to reboot to fix a problem. Not a criticism, just a notable event.

---

