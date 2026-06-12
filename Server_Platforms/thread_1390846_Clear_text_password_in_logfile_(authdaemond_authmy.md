---
title: "Clear text password in logfile (authdaemond: authmysql)"
date: 2010-01-26
forum: Server Platforms
---

### Post by LarsEriksson on 2010-01-26
Using postfix/courier/amavis etc with virtual users(MySQL).

When a user logs in, the following lines is created in /var/log/syslog:
```
Jan 26 10:23:58 servername imapd: Connection, ip=[::ffff:1.2.3.4]
Jan 26 10:23:59 servername authdaemond: received auth request, service=imap, authtype=login
Jan 26 10:23:59 servername authdaemond: authmysql: trying this module
Jan 26 10:23:59 servername authdaemond: SQL query: SELECT username, password, "", 5000, 5000, '/home/vmail', maildir, concat(quota,'S'), name, "" FROM mailbox WHERE username = 'USER@DOMAIN.com' 
Jan 26 10:23:59 servername authdaemond: password matches successfully
Jan 26 10:23:59 servername authdaemond: authmysql: sysusername=<null>, sysuserid=5000, sysgroupid=5000, homedir=/home/vmail, address=USER@DOMAIN.com, fullname=Lars Eriksson, maildir=USER@DOMAIN.com/, quota=0S, options=<null>
Jan 26 10:23:59 servername authdaemond: authmysql: clearpasswd=<null>, passwd=ENCRPYTED_PW
Jan 26 10:23:59 servername authdaemond: Authenticated: sysusername=<null>, sysuserid=5000, sysgroupid=5000, homedir=/home/vmail, address=USER@DOMAIN.com, fullname=Lars Eriksson, maildir=USER@DOMAIN.com/, quota=0S, options=<null>
Jan 26 10:23:59 servername authdaemond: Authenticated: clearpasswd=MY_PASSWD_AS_CLEAR_TEXT , passwd=ENCRPYTED_PW
Jan 26 10:23:59 servername imapd: LOGIN, user=USER@DOMAIN.com, ip=[::ffff:1.2.3.4], port=[15594], protocol=IMAP
```

In line 9, the line above the last, my password is logged in clear text. How can i set up the logging to not include clear text passwords?

---

### Post by daniel_c on 2010-04-08
1. Go to /etc/courier/
2. open file authdaemonrc
3. search for string DEBUG_LOGIN and set it to "0" instead of "2"
4. save the file
5. restart authdaemond : /etc/init.d/courier-authdaemon restart

This procedure works at least on debian system and I'm pretty sure your ubuntu will work as well ... 

Dan.

---

### Post by LarsEriksson on 2010-06-14
Worked perfectly. Thanks for the answer :)

---

