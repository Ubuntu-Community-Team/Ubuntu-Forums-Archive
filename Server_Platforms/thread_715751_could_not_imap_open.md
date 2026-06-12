---
title: "could not imap_open"
date: 2008-03-05
forum: Server Platforms
---

### Post by yanny on 2008-03-05
```

Warning: imap_open() [function.imap-open]: Couldn't open stream localhost:143/imap}INBOX in /var/www/mail/testimap.php on line 6
Connection to server failed
Array ( [0] => Can't open mailbox localhost:143/imap}INBOX: no such mailbox )

```

The above error I get when I go to the page testimap.php to test.


This is my script:

[PHP]
<?php
if (imap_open("localhost:25/imap}INBOX",'sandra','sandra')) {
	die("succesful!");
} else {
	echo "Connection to server failed<br />";
	print_r(imap_errors());
}
?>
[/PHP]


I use Postfix as mailserver and Courier-imap as IMAP server.

How can I fix this?

Tx very much!

---

### Post by Alekc on 2008-03-05
some more details? 
(and maybe a bit more precise question?)

---

### Post by yanny on 2008-03-05
^ See my first post, I've added some more details... :-k

---

### Post by faulkes on 2008-03-05
While this is more a php question than a server related question, I will answer it anyways
as there is at least some server component involved.

The imap_open function is being used improperly, you are specifying the SMTP
port (localhost:25) rather than the imap port 143.

Faulkes

---

### Post by yanny on 2008-03-05
Even though I use 143 it does not work too. ](*,)

But thanks for telling that I need to use port 143. I will change my first post now.

---

### Post by Alekc on 2008-03-05
Are you sure that there is some service configured for imap?
Try to exec "telnet localhost 143". If you are able to access port 143 with telnet but not with php, check the logs of Courier-imap for the reasons.

---

### Post by yanny on 2008-03-05
Yes I can telnet localhost 143, but after while (I don't know how long) the connection is broken. It says "Connection closed by foreign host".
:neutral:

Where are the logs of courier-imap?:confused:

---

### Post by faulkes on 2008-03-05
> **yanny said:**
> Yes I can telnet localhost 143, but after while (I don't know how long) the connection is broken. It says Connection closed by foreign host.
:neutral:

Where are the logs of courier-imap?:confused:

/var/log/mail.* {warn, err, crit, etc}
/var/log/syslog
/var/log/messages
/var/log/daemon.log

All of those can contain possible entries for typical system activities.  I'm not
sure if courier sets up it's own logging, however if it does, it should reside
within /var/log as well.

Faulkes

---

### Post by yanny on 2008-03-05
I see the messages but did not understand, I paste them here, maybe you guys see something that's wrong... :shock:

From another website I read: > Note that you can find log file messages from Postfix in /var/log/maillog (Courier-IMAP places log messages here as well).

So I believe the following code is the message log for Courier-IMAP too.

**/var/log/mail.log**
```

Mar  5 08:22:46 localhost postfix/smtpd[9512]: connect from localhost.localdomain[127.0.0.1]
Mar  5 08:27:46 localhost postfix/smtpd[9512]: timeout after CONNECT from localhost.localdomain[127.0.0.1]
Mar  5 08:27:46 localhost postfix/smtpd[9512]: disconnect from localhost.localdomain[127.0.0.1]
Mar  5 08:37:10 localhost imapd: Connection, ip=[::ffff:127.0.0.1]
Mar  5 08:53:28 localhost imapd: Connection, ip=[::ffff:127.0.0.1]

```

---

### Post by yanny on 2008-03-05
I have an idea that it is because Courier-IMAP itself is something not correct.

When I exec "telnet localhost 143" I surely get connected, but then when I do:

AB LOGIN "sandra" "sandra"


I get: 

* BYE Temporary problem, please try again later
Connection closed by foreign host.


Even without typing the connection closed after one minute or so...

---

### Post by yanny on 2008-03-05
I get this error now:

```

Certificate failure for localhost: self signed certificate: /C=US/ST=NY/L=New York/O=Courier Mail Server/OU=Automatically-generated IMAP SSL key/CN=localhost/emailAddress=postmaster@example.com

```


**The error messages are: **

```
Mar  5 09:37:14 localhost imapd: Connection, ip=[::ffff:127.0.0.1]
Mar  5 09:37:27 localhost authdaemond: failed to connect to mysql server (server=yanling.nl, userid=yanling): Can't connect to MySQL server on 'ya$
Mar  5 09:37:27 localhost imapd: LOGIN FAILED, user=sandra, ip=[::ffff:127.0.0.1]
Mar  5 09:37:27 localhost imapd: authentication error: Input/output error

```

](*,) I'm getting crazy

---

### Post by faulkes on 2008-03-05
Yes, it would appear that your courier-imap setup is not correct.

It appears to be trying to connect to mysql to authenticate the user and failing.

I would review your courier-imap setup and how you have told it to authenticate
users.

Note that this was originally a php question, which is now more on the server topic
of configuring a system service (courier-imap).  The more information you provide
about what you are trying to achieve and your current setup, the more helpful
we can be.

Faulkes

---

### Post by yanny on 2008-03-05
**The situation now is: **

root@ubuntu:/home/ubuntu# tail /var/log/mail.log
Mar  5 13:35:29 localhost imapd: Disconnected, ip=[::ffff:127.0.0.1], time=0, starttls=1
Mar  5 13:35:30 localhost imapd: Connection, ip=[::ffff:127.0.0.1]
Mar  5 13:35:30 localhost imapd: couriertls: connect: error:14094418:SSL routines:SSL3_READ_BYTES:tlsv1 alert unknown ca
Mar  5 13:35:30 localhost imapd: Disconnected, ip=[::ffff:127.0.0.1], time=0, starttls=1
Mar  5 13:35:30 localhost imapd: Connection, ip=[::ffff:127.0.0.1]
Mar  5 13:35:30 localhost imapd: couriertls: connect: error:14094418:SSL routines:SSL3_READ_BYTES:tlsv1 alert unknown ca
Mar  5 13:35:30 localhost imapd: Disconnected, ip=[::ffff:127.0.0.1], time=0, starttls=1
Mar  5 13:35:31 localhost imapd: Connection, ip=[::ffff:127.0.0.1]
Mar  5 13:35:31 localhost imapd: couriertls: connect: error:14094418:SSL routines:SSL3_READ_BYTES:tlsv1 alert unknown ca
Mar  5 13:35:31 localhost imapd: Disconnected, ip=[::ffff:127.0.0.1], time=0, starttls=1

I followed this tutorial: [http://www.howtoforge.com/virtual-users-and-domains-with-postfix-ubuntu-7.10](http://www.howtoforge.com/virtual-users-and-domains-with-postfix-ubuntu-7.10)

---

### Post by yanny on 2008-03-05
By the way I can login to pop3 server with no problem. The messages in mail.log are positive for telnet localhost pop3

---

### Post by faulkes on 2008-03-05
> **yanny said:**
> By the way I can login to pop3 server with no problem. The messages in mail.log are positive for telnet localhost pop3

You may wish to follow the install procedure located at 

[https://help.ubuntu.com/community/Courier](https://help.ubuntu.com/community/Courier)

which is the community based documentation.  

From the logfiles you have posted, currently, the issue appears to be that it
doesn't like the certificate and it is attempting to access mysql to authenticate
the user (for imap).  It is certainly possible that the pop3 configuration is
setup differently.

I would suggest you look through the configuration files in /etc/courier/imapd
and /etc/courier/imapd-ssl

Faulkes

---

### Post by yanny on 2008-03-06
I don't know what I've done, but today there is no error with IMAP...:)
What I did yesterday was the certificate again. 

From the messages I see no more error problem.. 

```

Mar  6 08:56:38 localhost authdaemond: Installing libauthmysql
Mar  6 08:56:38 localhost authdaemond: Installation complete: authmysql
Mar  6 08:56:41 localhost postfix/master[7011]: daemon started -- version 2.4.5, configuration /etc/postfix
Mar  6 08:57:02 localhost postfix/master[7011]: reload configuration /etc/postfix
Mar  6 09:23:03 localhost imapd: Connection, ip=[::ffff:127.0.0.1]
Mar  6 09:23:16 localhost imapd: LOGIN FAILED, user=yanling, ip=[::ffff:127.0.0.1]
Mar  6 11:31:25 localhost imapd: Connection, ip=[::ffff:127.0.0.1]
Mar  6 11:31:51 localhost imapd: LOGIN FAILED, user=mail_admin, ip=[::ffff:127.0.0.1]
Mar  6 11:32:09 localhost imapd: LOGIN, user=yanling@yanling.nl, ip=[::ffff:127.0.0.1], protocol=IMAP
Mar  6 11:33:25 localhost imapd: DISCONNECTED, user=yanling@yanling.nl, ip=[::ffff:127.0.0.1], headers=0, body=0, rcvd=11, sent=70, time=75

```

I even succeed in login in IMAP!!!:lol:

Thanks for the link anyway, because there it says:

"IMAP login username password"

I thought "AB login username password" is the command to login.. 

Also, they use the mysql table to authenticate so I completed with the emailaddress which is good! :D

Also the connection does not broke suddenly which is positive! =;

---

### Post by yanny on 2008-03-06
](*,)](*,)](*,)

I can connect to the IMAP server and open an emailaccount via the **terminal ** but still not via php script >.<

---

### Post by faulkes on 2008-03-06
> **yanny said:**
> ](*,)](*,)](*,)

I can connect to the IMAP server and open an emailaccount via the **terminal ** but still not via php script >.<

If courier is now working via terminal and not php, we would need to see the
errors that are coming out and the code which is being called.

Faulkes

---

### Post by yanny on 2008-03-06
**This is my code for php script:**

[PHP]<?php
if (imap_open("{localhost:143}INBOX","yanling@yanling.nl","test")) {
	die("succesful!");
} else {
	echo "Connection to server failed<br />";
	print_r(imap_errors());
}
?>[/PHP]


**This is the error via screen:**

Warning: imap_open() [function.imap-open]: Couldn't open stream {localhost:143}INBOX in /var/www/mail/testimap.php on line 6
Connection to server failed
Array ( [0] => Certificate failure for localhost: self signed certificate: /C=US/ST=NY/L=New York/O=Courier Mail Server/OU=Automatically-generated IMAP SSL key/CN=localhost/emailAddress=postmaster@example.com )


**In mail.err there is only this:**
Mar  6 08:56:25 localhost dccproc[5360]: no working DCC servers dcc1.dcc-servers.net dcc2.dcc-servers.net dcc3.dcc-servers.net ... at 127.0.0.1
Mar  6 12:48:28 localhost dccproc[5360]: no working DCC servers dcc1.dcc-servers.net dcc2.dcc-servers.net dcc3.dcc-servers.net ... at 127.0.0.1

---

### Post by yanny on 2008-03-06
Wooow I can't believe I have solved it!!!!!!!!!!!!!!!!!!!=D>

I will tell what I have done. :lol:

I googled like mad and came to this site: [http://www.phpfreakz.nl/forum.php?forum=10&iid=1099569](http://www.phpfreakz.nl/forum.php?forum=10&iid=1099569)

So, yeah it's a php issue rather than a server-sided, but still first I had server problems. :-)

The solution is to put "novalidate-cert" behind, see code below:

[PHP]<?php
if (imap_open("{localhost:143/imap/novalidate-cert}INBOX","yanling@yanling.nl","test")) {
	die("succesful!");
} else {
	echo "Connection to server failed<br />";
	print_r(imap_errors());
}
?>[/PHP]

The problem was the certificate is self-signed. I know this is not a solution for the certificate, but I can finally login!!! :guitar:

---

