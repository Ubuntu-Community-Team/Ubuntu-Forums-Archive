---
title: "Problem on dovecot"
date: 2008-05-22
forum: Server Platforms
---

### Post by satimis on 2008-05-22
Hi folks,


Ubuntu 6.05.3 drake amd64
Postfix 2.2.10
dovecot-common 1.0.beta3
dovecot-imapd 1.0.beta3
dovecot-pop3d 1.0.beta3


I'm following;

Ubuntu Server Guide
[https://help.ubuntu.com/6.06/ubuntu/serverguide/C/index.html](https://help.ubuntu.com/6.06/ubuntu/serverguide/C/index.html)

to build this LAMP server w/o having encountered much problem.  After completion I started testing it and found postfix can't receive mails.


Remark: 
having run update and upgrade several times


$ telnet localhost pop3```

Trying 127.0.0.1...
telnet: Unable to connect to remote host: Connection refused
```


$ sudo /etc/init.d/dovecot restart```

Restarting mail server: dovecotError: Can't use SSL certificate /etc/ssl/certs/dovecot.pem: No such file or directory

```


$ sudo locate dovecot.pem
No printout


$ ls -al /etc/ssl/certs/```

total 24
drwxr-xr-x 2 root root 4096 2008-05-19 22:27 .
drwxr-xr-x 4 root root 4096 2008-04-18 07:28 ..
lrwxrwxrwx 1 root root   21 2008-04-18 07:28 a69cfdd6 -> ssl-cert-snakeoil.pem
-rw-r--r-- 1 root root 1208 2008-05-19 22:25 cacert.pem
-rw-r--r-- 1 root root  904 2008-05-07 20:39 server.crt
-rw-r--r-- 1 root root  895 2008-05-19 22:20 smtpd.crt
-rw-r--r-- 1 root root 1139 2008-04-18 07:28 ssl-cert-snakeoil.pem

```



/etc/dovecot/dovecot.conf```

ssl_cert_file = /etc/ssl/certs/dovecot.pem
ssl_key_file = /etc/ssl/private/dovecot.pem
ssl_disable = no
disable_plaintext_auth = no

```

Remark:
Previously dovecot.pem were there.


$ telnet localhost pop3```

Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
+OK Dovecot ready.
quit
+OK Logging out
Connection closed by foreign host.

```
It worked prviously.


Please help.   TIA


B.R.
satimis

---

### Post by windependence on 2008-05-23
You should be telneting to the localhost on port 25 for testing....

-Tim

---

### Post by satimis on 2008-05-23
> **windependence said:**
> You should be telneting to the localhost on port 25 for testing....

Hi Tim,


It works w/o problem

$ telnet localhost 25```

Trying 127.0.0.1...
Connected to localhost.localdomain.
Escape character is '^]'.
220 mail.satimis.com ESMTP Postfix (Ubuntu)
ehlo satimis.com
250-mail.satimis.com
250-PIPELINING
250-SIZE 10240000
250-VRFY
250-ETRN
250-STARTTLS
250-AUTH LOGIN PLAIN
250-AUTH=LOGIN PLAIN
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN
mail from: user@satimis.com
250 2.1.0 Ok
rcpt to: satimis@yahoo.com
250 2.1.5 Ok
data
354 End data with <CR><LF>.<CR><LF>

Subject:  Test_lamp_20080523   

This is a test
.
250 2.0.0 Ok: queued as 365E2DF023C
quit
221 2.0.0 Bye
Connection closed by foreign host.

```
Mail received.


Previously
$ telnet localhost pop3```

Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
+OK Dovecot ready.
quit
+OK Logging out
Connection closed by foreign host.

```
also worked w/o problem.


But this is the first testing send/receive mails on this LAMP server.


B.R.
satimis

---

### Post by MJN on 2008-05-23
> **windependence said:**
> You should be telneting to the localhost on port 25 for testing....

Dovecot is a Mail Delivery Agent, i.e. it provides mail storage facilities using POP/IMAP hence port 25 (SMTP) doesn't play a role.

[quote=satimis]/etc/dovecot/dovecot.conf     ```
ssl_cert_file = /etc/ssl/certs/dovecot.pem
ssl_key_file = /etc/ssl/private/dovecot.pem
ssl_disable = no
disable_plaintext_auth = no
```Remark:
Previously dovecot.pem were there.[/quote]

You could just re-create them with the following (although proper (paid for) signed certs would likely be better depending on what you're using this for):

**sudo openssl req -new -x509 -days 365 -nodes -out /etc/ssl/certs/dovecot.pem -keyout /etc/ssl/private/dovecot.pem** 

...answering 'Common Name' with the fully qualified name of your server.

I'd be inclined to try and work out where the old certs went... they shouldn't just disappear by themselves! (It's not anything to do with the recent openssl upgrade is it? I wouldn't have thought it'd delete keys even if it did find some weak ones though...)

Mathew

---

### Post by satimis on 2008-05-23
> **MJN said:**
> Dovecot is a Mail Delivery Agent, i.e. it provides mail storage facilities using POP/IMAP hence port 25 (SMTP) doesn't play a role.



You could just re-create them with the following (although proper (paid for) signed certs would likely be better depending on what you're using this for):

**sudo openssl req -new -x509 -days 365 -nodes -out /etc/ssl/certs/dovecot.pem -keyout /etc/ssl/private/dovecot.pem** 

...answering 'Common Name' with the fully qualified name of your server.

I'd be inclined to try and work out where the old certs went... they shouldn't just disappear by themselves! (It's not anything to do with the recent openssl upgrade is it? I wouldn't have thought it'd delete keys even if it did find some weak ones though...)
Hi Mathew,


Thanks for your advice.


I solved my problem with following steps;


$ sudo ln -s /etc/ssl/certs/ssl-cert-snakeoil.pem /etc/ssl/c
erts/dovecot.pem```

Password:

```


$ sudo ln -s /etc/ssl/private/ssl-cert-snakeoil.key /etc/ssl
/private/dovecot.pem
No complaint


$ ls -l /etc/ssl/certs/```

total 16
lrwxrwxrwx 1 root root   21 2008-04-18 07:28 a69cfdd6 -> ssl-cert-snakeoil.pem
-rw-r--r-- 1 root root 1208 2008-05-19 22:25 cacert.pem
lrwxrwxrwx 1 root root   36 2008-05-23 16:46 dovecot.pem -> /etc/ssl/certs/ssl-cert-snakeoil.pem
-rw-r--r-- 1 root root  904 2008-05-07 20:39 server.crt
-rw-r--r-- 1 root root  895 2008-05-19 22:20 smtpd.crt
-rw-r--r-- 1 root root 1139 2008-04-18 07:28 ssl-cert-snakeoil.pem

```


$ sudo ls -l /etc/ssl/private/```

total 20
-rw-r--r-- 1 root root     963 2008-05-19 22:25 cakey.pem
lrwxrwxrwx 1 root root      38 2008-05-23 16:49 dovecot.pem -> /etc/ssl/private/ssl-cert-snakeoil.key
-rw-r--r-- 1 root root     963 2008-05-07 20:39 server.key
-rw-r--r-- 1 root root     963 2008-05-04 01:01 server.key.origin.20080507
-rw-r--r-- 1 root root     887 2008-05-19 22:21 smtpd.key
-rw-r----- 1 root ssl-cert 887 2008-04-18 07:28 ssl-cert-snakeoil.key

```


$ sudo /etc/init.d/dovecot restart```

Restarting mail server: dovecotWarning: Fixing permissions of /var/run/dovecot to be world-readable
Warning: Corrected permissions for login directory /var/run/dovecot/login
.

```


$ telnet localhost pop3```

Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
+OK Dovecot ready.
quit
+OK Logging out
Connection closed by foreign host.

```


But still it can't receive emails.


I found on router ports, 25, 110, 143, 443, 995 etc. forward to 192.168.0.10 NOT the IP address of this server, 192.168.0.52.


Tried forwarding port 143 to this server 192.168.0.52

Still can't receive emails.  Please advise where shall I check?  


TIA.


Furthermore on building this server previously.

/etc/ssl/certs/dovecot.pem
/etc/ssl/private/dovecot.pem

were there.  I can't resolve why they disappear.  I don't run this server daily.  I resume testing only when I have time.


B.R.
satimis

---

### Post by MJN on 2008-05-23
> **satimis said:**
> I solved my problem with following steps;


$ sudo ln -s /etc/ssl/certs/ssl-cert-snakeoil.pem /etc/ssl/certs/dovecot.pem

Yes, that'll do. That cert is a kind of 'generic' certificate which you can use in multiple packages until you have a 'real' one.

> But still it can't receive emails.You will need to elaborate significantly on this if you want anyone to help you - we're not mind-readers!

Mathew

---

### Post by satimis on 2008-05-23
> **MJN said:**
> 
You will need to elaborate significantly on this if you want anyone to help you - we're not mind-readers!

Hi Mathew,


Sorry, not much information here.


On 1st test w/o forwording port 143 to this server under test, 192.168.0.52.  The webmail sent on yahoo was returned immediately.


Warning on yahoo```

We're sorry. There's a problem with the e-mail address(es) you're
 trying
to send to. Please verify the address(es) and try again. If you
 continue
to have problems, please contact Customer Support at (480) 624-2500.

<satimis@satimis.com>:
child status 100...The e-mail message could not be delivered because
 there are no users here by that name.

--- Below this line is a copy of the message.
.....

```


On the 2nd test forwarding port 143 to 192.168.0.52 the mail was NOT returned immediately.  Neither it was delivered to the server.  On forwarding port 143 back to 192.168.0.10 the pending email was returned to yahoo immediately.  Warning on yahoo was the same as before


$ tail /var/log/mail.log ```

May 23 16:53:35 lampserver dovecot: Dovecot v1.0.beta3 starting up
May 23 16:53:35 lampserver dovecot: Generating Diffie-Hellman parameters for the
 first time. This may take a while..
May 23 16:53:39 lampserver dovecot: ssl-build-param: SSL parameters regeneration
 completed
May 23 17:10:16 lampserver dovecot: pop3-login: Aborted login: rip=127.0.0.1, li
p=127.0.0.1, secured
May 23 18:04:38 lampserver postfix/master[4141]: terminating on signal 15
May 23 18:04:38 lampserver dovecot: Killed with signal 15
May 23 18:56:21 lampserver postfix/master[4141]: daemon started -- version 2.2.1
0, configuration /etc/postfix
May 23 18:56:21 lampserver dovecot: Dovecot v1.0.beta3 starting up
May 23 18:56:21 lampserver dovecot: Generating Diffie-Hellman parameters for the
 first time. This may take a while..
May 23 18:56:24 lampserver dovecot: ssl-build-param: SSL parameters regeneration
 completed

```


$ tail /var/log/mail.err
No printout


$ tail /var/log/messages```

May 23 18:56:13 lampserver kernel: [   35.958665] cdrom: open failed.
May 23 18:56:13 lampserver kernel: [   36.656703] kjournald starting.  Commit interval 5 seconds
May 23 18:56:13 lampserver kernel: [   36.656830] EXT3 FS on sda5, internal journal
May 23 18:56:13 lampserver kernel: [   36.656835] EXT3-fs: mounted filesystem with ordered data mode.
May 23 18:56:13 lampserver kernel: [   40.863301] ppdev: user-space parallel port driver
May 23 18:56:18 lampserver kernel: [   45.921848] Installing knfsd (copyright (C) 1996 [email]okir@monad.swb.de[/email]).
May 23 18:56:18 lampserver kernel: [   46.174942] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
May 23 18:56:18 lampserver kernel: [   46.174960] NFSD: recovery directory /var/lib/nfs/v4recovery doesn't exist
May 23 18:56:18 lampserver kernel: [   46.174963] NFSD: starting 90-second grace period
May 23 18:56:23 lampserver squid[4302]: Squid Parent: child process 4309 started

```


Edit:


$ sudo iptables -L```

Password:
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

```



B.R.
satimis

---

### Post by MJN on 2008-05-23
You are confusing different parts of the mail delivery chain...

Your Mail Transfer Agent (MTA), Postfix, listens on port 25 and is responsible for accepting mail from outside and delivering it to your user's local mailboxes. This is the service that Yahoo corresponds with hence any errors that occur during this process are restricted entirely to Postfix and not Dovecot, port 143, etc etc.

I can connect to your MTA and seemingly send you mail without problem:

```
telnet mail.satimis.com 25
Trying 220.232.213.178...
Connected to mail.satimis.com.
Escape character is '^]'.
220 mail.satimis.com ESMTP Postfix (Ubuntu)
ehlo mail.newtonnet.co.uk
250-mail.satimis.com
250-PIPELINING
250-SIZE 10240000
250-VRFY
250-ETRN
250-STARTTLS
250-AUTH LOGIN PLAIN
250-AUTH=LOGIN PLAIN
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN
mail from: mailme-1@newtonnet.co.uk
250 2.1.0 Ok
rcpt to: satimis@satimis.com
250 2.1.5 Ok
data
354 End data with <CR><LF>.<CR><LF>
This is a test following on from your forum troubles... (from 'MJN')
.
250 2.0.0 Ok: queued as 3B3C0DF023C
quit
221 2.0.0 Bye
Connection closed by foreign host.
```...so that side of things looks like it's working.

Check to see if you got my message (in the user's mailbox - look directly rather than through a mail client), either way only then can we proceed. In the meantime forget about Dovecot and port 143 etc as you need to take these things one step at a time.

Incidentally, I've never heard of a 'Child status 100' error, at least within Postfix. It could well be Yahoo are sending to one of your backup MX's in which case you need to take it up with them as to what the problem is. Given you chopped your error message short you'll have to figure out whether this is the case for yourself.

Mathew

---

### Post by MJN on 2008-05-23
[duplicate post deleted]

---

### Post by satimis on 2008-05-23
> **MJN said:**
> You are confusing different parts of the mail delivery chain...

Your Mail Transfer Agent (MTA), Postfix, listens on port 25 and is responsible for accepting mail from outside and delivering it to your user's local mailboxes. This is the service that Yahoo corresponds with hence any errors that occur during this process are restricted entirely to Postfix and not Dovecot, port 143, etc etc.

I can connect to your MTA and seemingly send you mail without problem:

```
telnet mail.satimis.com 25
Trying 220.232.213.178...
Connected to mail.satimis.com.
Escape character is '^]'.
220 mail.satimis.com ESMTP Postfix (Ubuntu)
ehlo mail.newtonnet.co.uk
250-mail.satimis.com
250-PIPELINING
250-SIZE 10240000
250-VRFY
250-ETRN
250-STARTTLS
250-AUTH LOGIN PLAIN
250-AUTH=LOGIN PLAIN
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN
mail from: mailme-1@newtonnet.co.uk
250 2.1.0 Ok
rcpt to: satimis@satimis.com
250 2.1.5 Ok
data
354 End data with <CR><LF>.<CR><LF>
This is a test following on from your forum troubles... (from 'MJN')
.
250 2.0.0 Ok: queued as 3B3C0DF023C
quit
221 2.0.0 Bye
Connection closed by foreign host.
```...so that side of things looks like it's working.

Check to see if you got my message (in the user's mailbox - look directly rather than through a mail client), either way only then can we proceed. In the meantime forget about Dovecot and port 143 etc as you need to take these things one step at a time.

Incidentally, I've never heard of a 'Child status 100' error, at least within Postfix. It could well be Yahoo are sending to one of your backup MX's in which case you need to take it up with them as to what the problem is.

Mathew
I think I have to explain on this confusion.


I have only one public IP.  The LAMP server under building and a mail server are both connected to a router, having local IP 192.168.0.52 and 192.168.0.10 respectively.  10 ports are forwarded to the mail server, 192.168.0.10. (this router only supports forwarding 10 ports) without any port forwarded to the LAMP server.  


I have to stop postfix running on the mail server for you to test.  The hostname of the LAMP server is "lampserver"


$ hostname -f
lampserver


Now I stop postfix running on the mail server.  Please try again to check whether the LAMP can receive mail and/or contacted.  TIA


satimis

---

### Post by MJN on 2008-05-23
No joy...

```
$ telnet mail.satimis.com 25
Trying 220.232.213.178...
telnet: Unable to connect to remote host: Connection refused
```

To be honest I don't know if I've got the time to be chasing your ever-moving goalposts...

Mathew

---

### Post by satimis on 2008-05-23
> **MJN said:**
> No joy...

```
$ telnet mail.satimis.com 25
Trying 220.232.213.178...
telnet: Unable to connect to remote host: Connection refused
```

To be honest I don't know if I've got the time to be chasing your ever-moving goalposts...

Hi Mathew,


Problem solved as follows;

1) on /etc/postfix/main.cf
add;```

mydestination = localhost.satimis.com

```

2) on router
forward port 25 to 192.168.0.52 (LAMP server local IP)

restart postfix


Now LAMP server can receive emails delivered to /home/user/Maildir/new


Any further action I have to do on "dovecot"?  Thanks


Edit:

As curiosity, is there something on mail server similar to virtual host on webserver.  With only one public IP mails can be delivered to either mail server-1 or mail server-2


B.R.
satimis

---

### Post by MJN on 2008-05-23
> **satimis said:**
> Problem solved as follows;

1) on /etc/postfix/main.cf
add;```

mydestination = localhost.satimis.com

```

That should read **mydestination = localhost.satimis.com, satimis.com**

> 2) on router
forward port 25 to 192.168.0.52 (LAMP server local IP)To be honest I'd assumed you'd done that! You have to forward the port otherwise the router does not know where to send externally-originated traffic to.

> Now LAMP server can receive emails delivered to /home/user/Maildir/newExcellent.

> Any further action I have to do on "dovecot"?  ThanksTell it where to find the users' mail in case it can't figure this out for itself e.g. **default_mail_env = maildir:~/Maildir**

> As curiosity, is there something on mail server similar to virtual host on webserver.  With only one public IP mails can be delivered to either mail server-1 or mail server-2No, as all SMTP traffic will be coming in on port 25 - this is a fixed part of the standard and cannot be changed (or at least you can listen on whatever port you want, but there is no means of telling other servers what this non-standard port is).

Mathew

---

### Post by satimis on 2008-05-23
> **MJN said:**
> That should read **mydestination = localhost.satimis.com, satimis.com**

I posted part of the line only.

$ cat /etc/postfix/main.cf | grep mydestination```

mydestination = satimis.com, localhost.localdomain, localhost.satimis.com
```


> 
Tell it where to find the users' mail in case it can't figure this out for itself e.g. **default_mail_env = maildir:~/Maildir**

I already have this line.

$ sudo cat /etc/dovecot/dovecot.conf | grep default_mail_env```

...
default_mail_env = maildir:~/Maildir  # (for maildir)
...

```

Others noted with thanks


B.R.
satimis

---

