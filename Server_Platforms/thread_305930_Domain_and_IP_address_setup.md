---
title: "Domain and IP address setup"
date: 2006-11-24
forum: Server Platforms
---

### Post by satimis on 2006-11-24
Hi folks,

Ubuntu-6.06.1-LAMP-server-amd64
Apache2
Postfix

For testing Apache and Postfix I have a free dynamic domain setup on dyndns.org with a free hostname and dynamic IP asigned.

Please advise which file/files I have to edit so that I can;

1)
send email
2)
people can browse my website to be created later.

TIA


I'm running ADSL broadband with dynamic IP.


B.R.
satimis

---

### Post by rickyjones on 2006-11-24
Install an MTA (e.g. Postfix) on your server. Forward ports 25 (SMTP), 110 (if you have a POP3 server installed), and 80 (Web) from your router to your STATIC server IP (this is an internal IP).

Then, make sure that your DYNDNS.ORG domain name is updated whenever your IP changes. Have people send mail to your dynamic domain name and it should work (provided that your ISP doesn't restrict and/or block your mail ports).

Hope this helps!

---

### Post by satimis on 2006-11-24
Hi rickyjones,

Tks for your advice.

> Install an MTA (e.g. Postfix) on your server. Forward ports 25 (SMTP),
I have Postfix installed and running.

$ dpkg -l | grep postfix```

ii  postfix                                          2.2.10-1ubuntu0.1              A high-performance mail transport agent
```

I can send mail to myself with following steps;
$ telnet localhost 25```

Trying 127.0.0.1...
Connected to localhost.localdomain.
Escape character is '^]'.
220 server1.example.com ESMTP Postfix (Ubuntu)
ehlo satimis.com
250-server1.example.com
250-PIPELINING
250-SIZE 10240000
250-VRFY
250-ETRN
250-STARTTLS
250-AUTH LOGIN PLAIN
250-AUTH=LOGIN PLAIN
250 8BITMIME
mail from: myself@satimis.com
250 Ok
rcpt to: satimis@localhost
250 Ok
data
354 End data with <CR><LF>.<CR><LF>

Subject: Test

This is a test, a test, a test
.
250 Ok: queued as CEAE9754049
quit
221 Bye
Connection closed by foreign host.
You have new mail in /var/mail/satimis
```

Remark: satimis.com does not exist.
 

> 110 (if you have a POP3 server installed),
I haven't installed Dovecot.

Which file holding port 80 and 110?

> and 80 (Web) from your router to your STATIC server IP (this is an internal IP).
Sorry I'm not quite clear on this point.  I'm running ADSL broadband with dynamic IP.  PC is connected to an ADSL router --> to telephone line.  What shall I do?

> Then, make sure that your DYNDNS.ORG domain name is updated whenever your IP changes.
How to make it?

Dynamic IP setup ???
[http://forums.cjfay.com/showthread.php?t=25](http://forums.cjfay.com/showthread.php?t=25)

DYNDNS.ORG asigned:-
host.domain.com

Is it the domain only = domain.com
OR                    = host.domain.com

TIA


B.R.
satimis

---

### Post by rickyjones on 2006-11-24
The "file" for port 80 would be your webserver - E.g. Apache2. If you have it installed then you should be good for basic webserving.

Port 110 is POP3 - if you have a POP3 server installed then you'll be all set, otherwise ignore this part.

Is your ADSL router an actual router, or is it just a modem? If it's just a modem (i.e., no hardware firewall) then you just have to make sure there are no blocked ports on your system. If it's a router, then forward the ports you need to use to your computer. Your computer should be assigned a STATIC IP address (instead of dynamic) so that your router does not get confused.

Since you have a DYNAMIC public IP (ADSL), you'll want to make sure that you update your DYNDNS name every couple of days, else it might stop working.

Your domain should be host.domain.com. E.g.: [email]richard@myra.ath.cx[/email] (that is an example of my setup at home).

Should work pretty well after that.

---

### Post by MJN on 2006-11-24
> **rickyjones said:**
> Since you have a DYNAMIC public IP (ADSL), you'll want to make sure that you update your DYNDNS name every couple of days, else it might stop working.
 
If you have a dynamic IP then you need to update it whenever it changes, whether that be every hour, day or year. Of course, in practice this depends on your ISP leasing policy and your connection cicrumstances - some will give you a new address every time you connect whereas others will maintain something more akin to a reserved-but-not-guaranteed strategy. Mine is the latter - I've had the same address for over 2 years now (helped by the fact that my connection is always on and hence renews the lease without letting it drop).
 
Mathew

---

### Post by az on 2006-11-24
You should be able to send mail right away.  You will not be able to receive email on a dynamic dns box, though.

As well, apache is serving on your port 80 by default.  If you have a site running, you should be able to access it remotely through your dyndns hostname.

That is, unless your ISP blocks port 80 - and many of them do that for residential broadband connections.

---

### Post by MJN on 2006-11-24
> **azz said:**
> You should be able to send mail right away.  You will not be able to receive email on a dynamic dns box, though.

Eh? What makes you think that?

---

### Post by satimis on 2006-11-24
Hi Mathew,

> If you have a dynamic IP then you need to update it whenever it changes..
Previously I read document on how to overcome this difficulty running server with dynamic IP.  I'm now googling this doc.

> whether that be every hour, day or year....
I suppose every time I connect.  I'll check it.

Tks.


B.R.
satimis

---

### Post by satimis on 2006-11-24
Hi azz,

> You should be able to send mail right away.  You will not be able to receive email on a dynamic dns box, though.
Encountered difficulty sending email to yhoo.com and gmail.com with the new domain registered with dyndns.org.  

I don't know whether port 25 is blocked by ISP.  If YES how to overcome this difficulty?  How to check it?  Tks.

> That is, unless your ISP blocks port 80 - and many of them do that for residential broadband connections.
How to check it?  In case then how to overcome this difficulty?  TIA


B.R.
satimis

---

### Post by satimis on 2006-11-24
Hi rickyjones

> Port 110 is POP3 - if you have a POP3 server installed then you'll be all set, otherwise ignore this part.
I haven't installed Dovecot or Courier-IMAP/Courier-POP3.

> Is your ADSL router an actual router, or is it just a modem? If it's just a modem (i.e., no hardware firewall) then you just have to make sure there are no blocked ports on your system. If it's a router, then forward the ports you need to use to your computer. Your computer should be assigned a STATIC IP address (instead of dynamic) so that your router does not get confused.
I think it is only a ADSL modem.  It didn't need any setup, just connecting the CAT-5 cable to PC and a telephone line to telephone socket.

> Since you have a DYNAMIC public IP (ADSL), you'll want to make sure that you update your DYNDNS name every couple of days, else it might stop working.
I think the IP address only changes on connecting.  I'll check it.  In case changed how to update DYNDNS name?  Which file I have to edit?  Previously I came across  doc re "Setup Webserver on dynamic address".  I'm now googling this kind of document.  Have you had any suggestion?  Tks.

> Your domain should be host.domain.com. E.g.: [email]richard@myra.ath.cx[/email] (that is an example of my setup at home).
Noted with tks.  Is [email]satimis@host.domain.com[/email] my email address?  OR [email]myself@host.domain.com[/email] ?  Tks.


B.R.
satimis

---

