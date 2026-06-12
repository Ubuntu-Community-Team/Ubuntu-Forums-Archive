---
title: "Postfix - Recieving but can't POP! :)"
date: 2007-06-18
forum: Server Platforms
---

### Post by nigelicious on 2007-06-18
Hey all, I've setup Postfix using [http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/) . 

Recieving mail now to the virtual folders okay, and can deliver mail but cannot access mail via POP. When I try telnet to 110, i get the following:

nigelicious@vmlicious:~$ telnet localhost 110
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
+OK Hello there.
user nigelicious
+OK Password required.
pass mypass
-ERR Temporary problem, please try again later
Connection closed by foreign host.

I have tried starting all of the services I can think of saslauthd, courier-authdaemon, courier-imap-ssl, courier-imap, courier-pop. But no joy. I have all the ports open but just cant seem to auth. If there's anything I can provide to assist, let me know!

---

### Post by bmathis on 2007-06-19
can you post some logs so we can see any errors that might be showing up.

---

### Post by bikeboy on 2007-06-19
To start, you could check that something is actually listening on port 110. That might provide some guidance for where the problem exists.
```
netstat -l | grep tcp
```

---

### Post by nigelicious on 2007-06-19
sorry, i was a bit overwhelmed and not sure what to provide

mail.log
----
Jun 19 23:30:32 vmlicious courierpop3login: Connection, ip=[::ffff:x.x.x.x]
Jun 19 23:30:32 vmlicious authdaemond: authmysql: MYSQL_CRYPT_PWFIELD and MYSQL_CLEAR_PWFIELD not set in /etc/courier/authmysqlrc.
Jun 19 23:30:32 vmlicious courierpop3login: LOGIN FAILED, user=nigelicious, ip=[::ffff:x.x.x.x]
Jun 19 23:30:32 vmlicious courierpop3login: authentication error: Input/output error
Jun 19 23:31:32 vmlicious courierpop3login: Connection, ip=[::ffff:x.x.x.x]
Jun 19 23:31:32 vmlicious authdaemond: authmysql: MYSQL_CRYPT_PWFIELD and MYSQL_CLEAR_PWFIELD not set in /etc/courier/authmysqlrc.
Jun 19 23:31:32 vmlicious courierpop3login: LOGIN FAILED, user=nigelicious, ip=[::ffff:x.x.x.x]
Jun 19 23:31:32 vmlicious courierpop3login: authentication error: Input/output error

 MYSQL_CRYPT_PWFIELD was commented out as per tutorial, so after uncommenting it, I stop recieving that error but now just recieve login failed. I have looked at my SQL database and the username and password I am using match what I have in the table.

Jun 19 23:51:52 vmlicious courierpop3login: LOGIN FAILED, user=nigelicious, ip=[::ffff:x.x.x.x]
Jun 19 23:51:57 vmlicious courierpop3login: Disconnected, ip=[::ffff:x.x.x.x]
Jun 19 23:52:03 vmlicious courierpop3login: Connection, ip=[::ffff:x.x.x.x]
Jun 19 23:52:03 vmlicious courierpop3login: LOGIN FAILED, user=nigelicious, ip=[::ffff:x.x.x.x]
Jun 19 23:52:08 vmlicious courierpop3login: Disconnected, ip=[::ffff:x.x.x.x]

---

### Post by nigelicious on 2007-06-19
I have been able to connect to 110,25, and 143 when testing... 

output of netstat :
nigelicious@mymachine:/var/log$ netstat -l | grep tcp
tcp        0      0 localhost:2208          *:*                     LISTEN
tcp        0      0 localhost:mysql         *:*                     LISTEN
tcp        0      0 *:netbios-ssn           *:*                     LISTEN
tcp        0      0 *:webmin                *:*                     LISTEN
tcp        0      0 *:www                   *:*                     LISTEN
tcp        0      0 localhost:ipp           *:*                     LISTEN
tcp        0      0 *:smtp                  *:*                     LISTEN
tcp        0      0 *:microsoft-ds          *:*                     LISTEN
tcp        0      0 localhost:2207          *:*                     LISTEN
tcp6       0      0 *:imaps                 *:*                     LISTEN
tcp6       0      0 *: pop3                  *:*                     LISTEN
tcp6       0      0 *:imap2                 *:*                     LISTEN
tcp6       0      0 *:ssh                   *:*                     LISTEN
tcp6       0      0 *:1982                  *:*                     LISTEN

---

### Post by Mr. C. on 2007-06-19
It's clear your POP port is listening, as your first post showed you communicating with the pop server.

What authentication modules are listed in your authdaemonrc file ?   Use "locate authdaemonrc" of you don't know how to find it, and the grep authmodulelist from that file.

MrC

---

### Post by bikeboy on 2007-06-19
Ah yes, I misread one part of the OP.

---

### Post by nigelicious on 2007-06-19
nigelicious@vmlicious:/var/log$ sudo cat /etc/courier/authdaemonrc | grep authmodulelist
##NAME: authmodulelist:2
authmodulelist="authmysql"
##NAME: authmodulelistorig:3
authmodulelistorig="authuserdb authpam authpgsql authldap authmysql authcustom authpipe"

---

### Post by Mr. C. on 2007-06-19
Ok, so you are using mysql for authentication.

Your error showed that both MYSQL_CRYPT_PWFIELD and MYSQL_CLEAR_PWFIELD were missing:

```
authdaemond: authmysql: MYSQL_CRYPT_PWFIELD and MYSQL_CLEAR_PWFIELD not set in /etc/courier/authmysqlrc.
```

You said you uncommented out MYSQL_CRYPT_PWFIELD; have you tried MYSQL_CLEAR_PWFIELD being uncommented, but MYSQL_CRYPT_PWFIELD commented as per the tutorial?

You can set DEBUG_LOGIN=2 in your authdaemonrc file, and the restart courier.  You'll need debug level logging in syslog too to get the debug log messages.  Check your /etc/syslog.conf file for current settings.

Also check for those empty spaces at the end of the lines in authdaemonrc.

MrC

---

### Post by nigelicious on 2007-06-19
Thanks for sticking with me through this. I tried commenting only MYSQL_CRYPT_PWFIELD to no change. Also checked for those empty spaces at the end of the lines in authdaemonrc, but there werent any.

Changed to DEBUG_LOGIN=2 but wasnt sure on debug level logging (sorry if i am missing something basic here) .. but couldnt see any change on output through the various logs after restarting postfix..

mail.log 
-------
Same as before.


tail /var/log/mysql/mysql.log
------------
070620  1:57:33     333 Connect     mail@localhost on
                    333 Init DB     maildb
                    333 Query       SELECT id, "", clear, uid, gid, home, "", "", name, "" FROM users WHERE id = "nigelicious"
070620  1:58:47     333 Query       SELECT id, "", clear, uid, gid, home, "", "", name, "" FROM users WHERE id = "nigelicious"
070620  1:59:54     333 Query       SELECT id, "", clear, uid, gid, home, "", "", name, "" FROM users WHERE id = "nigelicious"
070620  2:00:54     333 Query       SELECT id, "", clear, uid, gid, home, "", "", name, "" FROM users WHERE id = "nigelicious"
070620  2:01:33     332 Quit

---

### Post by nigelicious on 2007-06-19
any ideas? :)

---

### Post by Mr. C. on 2007-06-19
I've been meaning to suggest you change the title of this thread to:

COURIER- POP password failure

as this has thread has nothing to do with postfix.

Restarting postfix will have no affect; the courier authdaemon is the process that needs restarting.

You will see no additional output until:
a) you restart courier authdaemon
b) modify your /etc/syslog.conf to output debug-level messages for the appropriate service.

Your log shows that the mysql query being made is for "clear" text password.  Run your own query and ensure the password stored in that table is indeed a clear-text password.

MrC

---

### Post by nigelicious on 2007-06-19
of course. I just got caught up on postfix being the issue.

after restarting the courier services and attempting to connect via POP, I get in mail.log
---------
Jun 20 12:59:55 vmlicious courierpop3login: Connection, ip=[::ffff:x.x.x.x]
Jun 20 12:59:55 vmlicious authdaemond: received auth request, service=pop3, authtype=login
Jun 20 12:59:55 vmlicious authdaemond: authmysql: trying this module
Jun 20 12:59:55 vmlicious authdaemond: SQL query: SELECT id, "", clear, uid, gid, home, "", "", name, "" FROM users WHERE id = "nigelicious"
Jun 20 12:59:55 vmlicious authdaemond: zero rows returned
Jun 20 12:59:55 vmlicious authdaemond: no password available to compare
Jun 20 12:59:55 vmlicious authdaemond: authmysql: REJECT - try next module
Jun 20 12:59:55 vmlicious authdaemond: FAIL, all modules rejected
Jun 20 12:59:55 vmlicious courierpop3login: LOGIN FAILED, user=nigelicious, ip=[::ffff:x.x.x.x]
Jun 20 13:00:00 vmlicious courierpop3login: Disconnected, ip=[::ffff:x.x.x.x

so i realised... stupidly, i had trying to connect with 'nigelicious' rather than 'nigelicious@mydomain.com'. So i changed it.

Jun 20 13:03:57 vmlicious courierpop3login: Connection, ip=[::ffff:x.x.x.x]
Jun 20 13:03:57 vmlicious authdaemond: received auth request, service=pop3, authtype=login
Jun 20 13:03:57 vmlicious authdaemond: authmysql: trying this module
Jun 20 13:03:57 vmlicious authdaemond: SQL query: SELECT id, "", clear, uid, gid, home, "", "", name, "" FROM users WHERE id = "nigelicious@thedomain.com"
Jun 20 13:03:57 vmlicious authdaemond: authmysql: sysusername=<null>, sysuserid=5000, sysgroupid=5000, homedir=/var/spool/mail/virtual, address=nigelicious@thedomain.com, fullname=nigelicious, maildir=<null>, quota=<null>, options=<null>
Jun 20 13:03:57 vmlicious authdaemond: authmysql: clearpasswd=thepassword, passwd=<null>
Jun 20 13:03:57 vmlicious authdaemond: Authenticated: sysusername=<null>, sysuserid=5000, sysgroupid=5000, homedir=/var/spool/mail/virtual, address=nigelicious@thedomain.com, fullname=nigelicious, maildir=<null>, quota=<null>, options=<null>
Jun 20 13:03:57 vmlicious authdaemond: Authenticated: clearpasswd=thepassword, passwd=<null>
Jun 20 13:03:57 vmlicious courierpop3login: chdir Maildir: No such file or directory
]

the output from the users table database seemed right, i.e. home is /var/spool/mail/virtual  and maildir is	nigel/. 
so i went to check authmysqlrc and make sure the line "MYSQL_MAILDIR_FIELD     concat(home,'/',maildir)" was correct
and thats when I noticed when i took out the # in front of  "MYSQL_MAILDIR_FIELD     concat(home,'/',maildir)" , i had a space where the # was, so i removed that and it worked! i checked for spaces at the ends of the lines as you suggested, but didnt notice, or think to check the front.

It's always this kind of stuff when you have a problem.. I need an editor to go through my config files after i've touched them. 
Thanks very much :)

---

