---
title: "Losing connection with imap when during login [courier]"
date: 2012-06-20
forum: Server Platforms
---

### Post by markvalley on 2012-06-20
Hello,

I am installing a fresh webmail server. We decided to try Ubuntu this time (our current server is using Debian 5).

Basically we are using courier, postfix and roundcube as the front end. 

After the boot, i can use the webmail very well for about 10 minutes. After that, it seems that i lose connection with imap everytime during login operation. Restarting services will not solve the problem and i need to reboot the machine. All logs seem to be clean.

A telnet session gives me the following:

[INDENT]telnet localhost 143
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
* OK [CAPABILITY IMAP4rev1 UIDPLUS CHILDREN NAMESPACE THREAD=ORDEREDSUBJECT THREAD=REFERENCES SORT QUOTA IDLE ACL ACL2=UNION STARTTLS] Courier-IMAP ready. Copyright 1998-2011 Double Precision, Inc.  See COPYING for distribution information.
. login [email]user.name@mydomain.com[/email] mypassword
Connection closed by foreign host.[/INDENT]

At the last line the connection is closed. The normal answer should be ". OK LOGIN Ok.".


The mail.log has the following (i have enabled the log to show passwords too): 

[INDENT]Jun 20 09:35:35 virgo imapd: Connection, ip=[::ffff:127.0.0.1]
Jun 20 09:35:35 virgo authdaemond: received auth request, service=imap, authtype=login
Jun 20 09:35:35 virgo authdaemond: authpgsql: trying this module
Jun 20 09:35:35 virgo authdaemond: SQL query: SELECT username, password, '', '5000', '5000', '/home/vmail', maildir, quota, name, '' FROM mailbox WHERE username = 'user.name@mydomain.com'
Jun 20 09:35:35 virgo authdaemond: password matches successfully
Jun 20 09:35:35 virgo authdaemond: authpgsql: sysusername=<null>, sysuserid=5000, sysgroupid=5000, homedir=/home/vmail, address=user.name@mydomain.com, fullname=USER NAME, maildir=mydomain.com/user.name/, quota=0, options=<null>
Jun 20 09:35:35 virgo authdaemond: authpgsql: clearpasswd=<null>, passwd=$1$fc67c87a$ZymLVBprZ/CsR6OjrPG6j.
Jun 20 09:35:35 virgo authdaemond: Authenticated: sysusername=<null>, sysuserid=5000, sysgroupid=5000, homedir=/home/vmail, address=user.name@mydomain.com, fullname=USER NAME, maildir=mydomain.com/user.name/, quota=0, options=<null>
Jun 20 09:35:35 virgo authdaemond: Authenticated: clearpasswd=mypassword, passwd=$1$wc67787a$ZymLVBprZ/CiR6OjrPG6j.
[/INDENT]

On normal situatons (during the "10 minute window" , for example) the last line should be imapd confirming the login.

Other logs are clean and i can't figure out where to look. Does anyone have a clue about what is going on?

Thanks in advance!

Ps: Sorry, revised the body text but forgot the title.

---

### Post by [S2] on 2012-06-21
i have your exact same problem and no idea how to further debug this. did you happen to fix this?

---

### Post by [S2] on 2012-06-21
this
[http://ubuntuforums.org/showpost.php?p=11902102&postcount=16]("http://ubuntuforums.org/showpost.php?p=11902102&postcount=16")
fixed it for me

---

### Post by markvalley on 2012-06-21
I didn't work for me.

I found that setting IMAPDEBUGFILE=debug.txt at /etc/courier/imapd would create a file with all the imap conversation. The file will be created at the user maildir. But, unfortunally this log shows nothing too.

Yesterday night i decided to install the server again. It seems i don't have the problem anymore. I will do some other tests before setting it to production.

---

### Post by markvalley on 2012-06-26
Well, after a few days the problem is back. The only change now was the installation of Amavis. I will give some more trys and will be back to debian if dont have success... :(

---

