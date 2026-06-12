---
title: "Fail to send mail"
date: 2012-01-31
forum: Server Platforms
---

### Post by satimis on 2012-01-31
Hi all,

VM - ubuntu1010 server 64bit
host - ubuntu1104 desktop 64bit
Orcle VirtualBox

On router
Port 25 pointing VM Ip(local)

Just finished building a mail server

$ telnet localhost smtp
Trying ::1...
Connected to localhost.
Escape character is '^]'.
220 server1.domain.com ESMTP Postfix (Ubuntu)

ehlo server1.domain.com
250-server1.domain.comm
250-PIPELINING
250-SIZE 10240000
250-VRFY
250-ETRN
250-STARTTLS
250-AUTH PLAIN LOGIN
250-AUTH=PLAIN LOGIN
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN

mail from:<user@server1.domain.com>
250 2.1.0 Ok

rcpt to:<someone@yahoo.com>
554 5.7.1 <someone@yahoo.com>: Relay access denied

I have been googling a while unable to find a solution.  Please help.  TIA

B.R.
satimis

---

### Post by SeijiSensei on 2012-01-31
First try "telnet mta5.am0.yahoodns.net 25" to see if you can actually connect to that server.  Your ISP could block outbound port 25 connections, Yahoo could be refusing traffic from your IP address (common if you're on a residential connection), or Postfix could be misconfigured.  Let's start by first seeing if you can actually send mail to a Yahoo SMTP server.

---

### Post by satimis on 2012-01-31
> **SeijiSensei said:**
> First try "telnet mta5.am0.yahoodns.net 25" to see if you can actually connect to that server.  Your ISP could block outbound port 25 connections, Yahoo could be refusing traffic from your IP address (common if you're on a residential connection), or Postfix could be misconfigured.  Let's start by first seeing if you can actually send mail to a Yahoo SMTP server.

Hi,

$ telnet mta5.am0.yahoodns.net 25```

Trying 209.191.88.254...
Connected to mta5.am0.yahoodns.net.
Escape character is '^]'.
220 mta1008.mail.mud.yahoo.com ESMTP YSmtp service ready
Connection closed by foreign host.

```
My ISP won't block port 25 because I'm subscribing fixed IP plan.

I was following;

The Perfect Server - Ubuntu 10.10 [ISPConfig 3]
[http://www.howtoforge.com/perfect-server-ubuntu-10.10-maverick-meerkat-ispconfig-3-p4](http://www.howtoforge.com/perfect-server-ubuntu-10.10-maverick-meerkat-ispconfig-3-p4)

to build this server running on a VM of Oracle VirtualBox.  Then I followed;
Postfix Complete VirtualMail System Howto
[https://help.ubuntu.com/community/PostfixCompleteVirtualMailSystemHowto](https://help.ubuntu.com/community/PostfixCompleteVirtualMailSystemHowto)

further configuring postfix.

After encountering problem I followed the advice on #2
Setup mailaccount 
[http://www.howtoforge.com/forums/showthread.php?t=2](http://www.howtoforge.com/forums/showthread.php?t=2)

trying to solve it without result.

$ telnet localhost smtp
Trying ::1...
Connected to localhost.
Escape character is '^]'.
220 mail.server1.domain.com ESMTP Postfix (Ubuntu)

ehlo server1.domain.com
250-mail.server1.domain.com
250-PIPELINING
250-SIZE 10240000
250-VRFY
250-ETRN
250-STARTTLS
250-AUTH PLAIN LOGIN
250-AUTH=PLAIN LOGIN
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN

mail from:<user@server1.domain.com>                 
250 2.1.0 Ok

rcpt to:<somebody@yahoo.com>
554 5.7.1 <somebody@yahoo.com>: Relay access denied

rcpt to:<stephen@server1.domain.com>
250 2.1.5 Ok

stephen is the new user created on following;
Setup mailaccount 
[http://www.howtoforge.com/forums/showthread.php?t=2](http://www.howtoforge.com/forums/showthread.php?t=2)

$ ls /home/```

other_users

```
stephen a/c couldn't be found

$ su stephen
sh-4.1$ls```

smtpd.crt smtpd.key web

```

it works but I couldn't find the mail.  I don't know why.

B.R.
satimis

---

### Post by lisati on 2012-01-31
Have you set up the server to require authentication by any chance?

---

### Post by satimis on 2012-01-31
> **lisati said:**
> Have you set up the server to require authentication by any chance?
Could you please explain in more detail?  Thanks

B.R.
satimis

---

### Post by SeijiSensei on 2012-01-31
> **satimis said:**
> Hi,

$ telnet mta5.am0.yahoodns.net 25```

Trying 209.191.88.254...
Connected to mta5.am0.yahoodns.net.
Escape character is '^]'.
220 mta1008.mail.mud.yahoo.com ESMTP YSmtp service ready
Connection closed by foreign host.

```

Did you disconnect from the remote server, or did it drop the connection on you? If the latter, then Yahoo doesn't like your IP address.  Are you on a residential connection?  Try checking your IP address against blacklists [here](http://www.mxtoolbox.com/).

---

### Post by lisati on 2012-01-31
> **satimis said:**
> Could you please explain in more detail?  Thanks

B.R.
satimis

My postfix server is set so that I have to access it using a valid user name and password, otherwise it returns "relay access denied."

---

### Post by satimis on 2012-02-01
> **SeijiSensei said:**
> Did you disconnect from the remote server, or did it drop the connection on you? If the latter, then Yahoo doesn't like your IP address.  Are you on a residential connection?  Try checking your IP address against blacklists [here](http://www.mxtoolbox.com/).
It dropped the connection after a while.

checked my fixed IP against blacklist:-
All "OK" without problem except follows```

CYBERLOGIC	 TIMEOUT	ERROR, Reponse code=2 		0
ivmSIP	 TIMEOUT			0
ivmSIP/24	 TIMEOUT			0
SPAMRBL	 TIMEOUT	ERROR, Reponse code=2 		0
TECHNOVISION	 TIMEOUT	ERROR, Reponse code=2 		0
Tiopan	 TIMEOUT	ERROR, Reponse code=2 

```

Edit:
$ tail /var/log/mail.log```

Feb  1 18:10:01 server1 postfix/smtpd[2873]: lost connection after CONNECT from unknown[::1]
Feb  1 18:10:01 server1 postfix/smtpd[2873]: disconnect from unknown[::1]
Feb  1 18:10:01 server1 postfix/pickup[1745]: A1B04141180: uid=33 from=<www-data>
Feb  1 18:10:01 server1 postfix/cleanup[2899]: A1B04141180: message-id=<20120201101001.A1B04141180@mail.server1.domain.com>
Feb  1 18:10:01 server1 postfix/qmgr[1746]: A1B04141180: from=<www-data@server1.domain.com>, size=908, nrcpt=1 (queue active)
Feb  1 18:10:01 server1 postfix/smtp[2838]: connect to 127.0.0.1[127.0.0.1]:10024: Connection refused
Feb  1 18:10:01 server1 postfix/smtp[2838]: A1B04141180: to=<www-data@server1.domain.com>, orig_to=<www-data>, relay=none, delay=0.02, delays=0.02/0/0/0, dsn=4.4.1, status=deferred (connect to 127.0.0.1[127.0.0.1]:10024: Connection refused)
Feb  1 18:11:18 server1 postfix/smtpd[2834]: warning: table "mysql:/etc/postfix/mysql-virtual_client.cf": empty query string -- ignored
Feb  1 18:11:18 server1 postfix/smtpd[2834]: NOQUEUE: reject: RCPT from unknown[::1]: 554 5.7.1 <somebody@yahoo.com>: Relay access denied; from=<user@server1.domain.com> to=<somebody@yahoo.com> proto=ESMTP helo=<server1.domain.com>
Feb  1 18:11:30 server1 postfix/smtpd[2834]: disconnect from unknown[::1]

```

B.R.
satimis

---

### Post by satimis on 2012-02-01
> **lisati said:**
> My postfix server is set so that I have to access it using a valid user name and password, otherwise it returns "relay access denied."
I sent a mail to an user on the server.  But it didn't arrive.

$ tail /var/log/mail.log ```

Feb  1 17:45:01 server1 postfix/smtpd[2368]: warning: TLS library problem: 2368:error:0B084002:x509 certificate routines:X509_load_cert_crl_file:system lib:by_file.c:274:
Feb  1 17:45:01 server1 postfix/smtpd[2368]: warning: ::1: address not listed for hostname localhost
Feb  1 17:45:01 server1 postfix/smtpd[2368]: connect from unknown[::1]
Feb  1 17:45:01 server1 postfix/smtpd[2368]: lost connection after CONNECT from unknown[::1]
Feb  1 17:45:01 server1 postfix/smtpd[2368]: disconnect from unknown[::1]
Feb  1 17:46:21 server1 postfix/smtpd[2368]: warning: ::1: address not listed for hostname localhost
Feb  1 17:46:21 server1 postfix/smtpd[2368]: connect from unknown[::1]
Feb  1 17:48:39 server1 postfix/smtpd[2368]: warning: table "mysql:/etc/postfix/mysql-virtual_client.cf": empty query string -- ignored
Feb  1 17:48:39 server1 postfix/smtpd[2368]: EE6BA14117B: client=unknown[::1]
Feb  1 17:48:45 server1 postfix/smtpd[2368]: disconnect from unknown[::1]

```

$ cat /etc/postfix/main.cf | grep authenticated```

smtpd_sasl_authenticated_header = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination

```


B.R.
satimis

---

