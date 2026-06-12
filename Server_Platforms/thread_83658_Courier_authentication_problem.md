---
title: "Courier authentication problem"
date: 2005-10-29
forum: Server Platforms
---

### Post by Raffe on 2005-10-29
Hi
I'm setting up Postfix and courier-pop servers. Got Postfix working but courier is giving me headaches. I'm stuck on the authentication. trying to make it use the /etc/courier/userdb.dat. Tried getting som usefull debug outputs and made syslog.conf produce a /var/log/mail.debug file for me.
In this file I get messages like

Oct 29 12:34:55 consoftix authdaemond.plain: modules="authuserdb authpam authcram", daemons=5
Oct 29 12:34:57 consoftix postfix/master[4258]: daemon started -- version 2.1.5
Oct 29 12:39:04 consoftix courierpop3login: Connection, ip=[::ffff:127.0.0.1]
Oct 29 12:39:19 consoftix courierpop3login: LOGIN: DEBUG: ip=[::ffff:127.0.0.1], command=USER
Oct 29 12:39:26 consoftix courierpop3login: LOGIN: DEBUG: ip=[::ffff:127.0.0.1], command=PASS
Oct 29 12:39:26 consoftix courierpop3login: LOGIN: DEBUG: ip=[::ffff:127.0.0.1], username=mupp
Oct 29 12:39:26 consoftix courierpop3login: LOGIN: DEBUG: ip=[::ffff:127.0.0.1], password=mypwd
Oct 29 12:39:26 consoftix courierpop3login: authdaemon: starting client module
Oct 29 12:39:26 consoftix courierpop3login: authdaemon: REJECT
Oct 29 12:39:31 consoftix courierpop3login: LOGIN FAILED, ip=[::ffff:127.0.0.1]
Oct 29 12:39:32 consoftix courierpop3login: LOGIN: DEBUG: ip=[::ffff:127.0.0.1], command=QUIT
Oct 29 12:39:32 consoftix courierpop3login: LOGOUT, ip=[::ffff:127.0.0.1]

In /etc/courier/authdaemnonrc I have set:
authmodulelist="authuserdb authpam authcram"

And in /etc/courier/pop3d I have set:
DEBUG_LOGIN=2

in userdb I generated an encrypted password using "userdbpw -md5".

When testing it I use "telnet localhost 110". But I can't login to the pop server using USER and PASS.

It worries me that I cant se the authdaemon call authuserdb or any of the other modules. Have I missed some configuration here? or I'm I perhaps using the wrong password generation? How do one know which password encryption to use?

/Raffe

---

### Post by Frank-Hamersley on 2006-12-20
G'day - 2 years later and I have the same problem...

... getting authdaemon to authenticate a virtual user session for my courier-pop service.  There is not much useful diagnostic info in the logs except a terse message that the logon is being rejected (LOGIN FAILED).

I have tried using the fully qualified email address and then "admin" alone but no joy.  I have used debug level 2 and confirmed that the expected password was being passed correctly.  I have tried userdbpw -md5 as well as clear text passwords.  Should I be using the systempw field name?

From the various FAQ sources I have googled it remains unclear to me as to which elements of the userdb fields actually need to be supplied.  I presumed initially that interaction with the file system would simply use the daemon profile (hence no uid or gid was required as long as permissions allowed access) but after running pw2userdb I modeled my later attempts on the more explicit form.  Still no progress!

The other aspects of the mail system appear to be functioning correctly.  I have successfully sent mail to "admin" and can see the message has arrived in the mailbox but can not retrieve it.

Any one have tips on fixing this?

Regards, Frank.


Sanitised userdb is ...

# /etc/courier/userdb - virtual POP3 accounts for courier-pop
#
#admin@gvmp.com.au	mail=/var/spool/mail/admin|pop3pw=password

admin	uid=2000|gid=1000|mail=/var/spool/mail/admin|pop3pw=password
2000=	admin

#
#EOF

---

