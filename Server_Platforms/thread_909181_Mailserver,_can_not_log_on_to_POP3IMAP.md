---
title: "Mailserver, can not log on to POP3/IMAP"
date: 2008-09-03
forum: Server Platforms
---

### Post by LarsEriksson on 2008-09-03
I have installed Ubuntu Server 8.04.1 64-bit, and installed mail software according to the guide at: 
[https://help.ubuntu.com/community/PostfixCompleteVirtualMailSystemHowto](https://help.ubuntu.com/community/PostfixCompleteVirtualMailSystemHowto)
Everything seems to have gone well with the installation, i have installed postfixadmin and can create accounts through it(directory is created under /home/vmail and login information is added to MySQL), the problem is when I log in with either POP3 or IMAP. 
I get the following message in the log when I try to log in: 
```
Sep  3 13:29:39 web pop3d: Connection, ip=[::ffff:192.168.1.210]
Sep  3 13:29:43 web pop3d: LOGIN FAILED, user=laeri, ip=[::ffff:192.168.1.210]
Sep  3 13:29:56 web pop3d: Disconnected, ip=[::ffff:192.168.1.210]
Sep  3 13:36:53 web imapd: Connection, ip=[::ffff:127.0.0.1]
Sep  3 13:36:53 web imapd: LOGIN FAILED, method=CRAM-MD5, ip=[::ffff:127.0.0.1]
Sep  3 13:36:58 web imapd: LOGIN FAILED, user=test@wintech.se, ip=[::ffff:127.0.0.1]
Sep  3 13:37:03 web imapd: Disconnected, ip=[::ffff:127.0.0.1], time=10
```

I have been troubleshooting and looking for solutions to the problem for 4-5 hours now, but come nowhere at all.
Is there anyone who knows what I can do?
MySQL log files are empty, so I do not know if the mail server even ask the MySQL server at login, how can I check it?

---

### Post by HermanAB on 2008-09-03
Hmm, unless you have to support millions of users, or is doing this as a learning exercise, there are better solutions for email.

I have quit the Postfix battle a couple of years ago and now use Citadel.  Citadel can be set up in about 20 minutes and just works, with zero maintenance.  A comparible Postfix/Apache/Squirrel/MySQL/Dovecot system could take a week to set up (if you know what you are doing - a month if not).

To come back to your question, first verify that the servers are actually running with 'ps -e' and 'telnet'.  For example, the following commands should elicit a response:
# telnet localhost 110
# telnet localhost 25

Put a tail on the log files to see what is going on:
# tail -f /var/log/messages
(or whatever log file is appropriate)

Cheers,

Herman

---

### Post by LarsEriksson on 2008-09-03
ok, i followed your advice and installed Citadel, however now i have a new problem, where can i set a smtp relay server? Since my ISP has closed port 25 i need to configure this.
According to the documentation on citadel.org there should be a setting like that on Admin -> Network, but its not there in my config.

---

### Post by HermanAB on 2008-09-03
It is called something else - Smart Host?  Just click around the menus, it is there somewhere.  If you can't find it send me a message and I'll have a look tonight.

Cheers,

H.

---

