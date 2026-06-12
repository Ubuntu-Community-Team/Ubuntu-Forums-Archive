---
title: "Sendmail not sending"
date: 2008-12-02
forum: Server Platforms
---

### Post by R.Bucky on 2008-12-02
I have installed about a dozen Ubuntu servers thus far. So far, this is the only install where sendmail is causing problems. Any internal system email from Wordpress or one of my sendmail scripts sits and spins for about 2 minutes and then tells me it sent ok. But, i never receive the mail. Here is the output from 
```
telnet localhost 25
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
220 markserver ESMTP Sendmail 8.14.1/8.14.1/Debian-8ubuntu1; Mon, 1 Dec 2008 22:36:55 -0800; (No UCE/UBE) logging access from: localhost(OK)-localhost [127.0.0.1]
```

Here is the output from my mail.log
```
Dec  1 22:36:14 markserver sm-mta[4811]: mAO2tx04010773: to=<user@example.com>, ctladdr=<www-data@buckyspalace.net> (33/33), delay=8+03:40:15, xdelay=00:10:18, mailer=esmtp, pri=32250365, relay=example.com. [208.77.188.166], dsn=4.0.0, stat=Deferred: Connection timed out with example.com.
Dec  1 22:36:14 markserver sm-mta[4811]: mAO2tx04010773: mB26PuEl004811: sender notify: Cannot send message for 5 days
Dec  1 22:36:14 markserver sm-mta[4811]: mB26PuEl004811: to=<www-data@buckyspalace.net>, delay=00:00:00, xdelay=00:00:00, mailer=local, pri=30000, dsn=2.0.0, stat=Sent

```

Does this make sense to anyone? I currently host my domain with Ubuntu 7.10. I have reinstalled a couple of time previous (my errors) with no problems from sendmail. It used to be as simple as sudo apt-get install sendmail. Now, I am baffled.

---

### Post by hictio on 2008-12-02
- You send emails directly from your server, or thru a relay? (in Sendmail parlance, thru a SMART_HOST)
- From your box, you can open an smtp connection over localhost, but, can you connect to the remote SMTP server? Perhaps there is a firewall limiting outgoing SMTP connection?
(Do the same test you did over localhost, but with the IP/ hostname of the server you want to sendmail to)

---

### Post by R.Bucky on 2008-12-02
I send mail directly from my server. I disabled my firewall and IPBlock. It did not improve the performance or efficiency of sendmail. Here is the respnse from a telenet to my ip
> telnet 24.18.97.15 25
Trying 24.18.97.15...
telnet: Unable to connect to remote host: Connection refused
Would my /etc/hosts have anything to do with the refusal of sendmail functionality? Here is what I have so far.
> 127.0.0.1 localhost buckyspalace.net
127.0.1.1 markserver

---

### Post by andr100 on 2008-12-02
> **R.Bucky said:**
> I have installed about a dozen Ubuntu servers thus far. So far, this is the only install where sendmail is causing problems. Any internal system email from Wordpress or one of my sendmail scripts sits and spins for about 2 minutes and then tells me it sent ok. But, i never receive the mail. Here is the output from 
```
telnet localhost 25
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
220 markserver ESMTP Sendmail 8.14.1/8.14.1/Debian-8ubuntu1; Mon, 1 Dec 2008 22:36:55 -0800; (No UCE/UBE) logging access from: localhost(OK)-localhost [127.0.0.1]
```

Here is the output from my mail.log
```
Dec  1 22:36:14 markserver sm-mta[4811]: mAO2tx04010773: to=<user@example.com>, ctladdr=<www-data@buckyspalace.net> (33/33), delay=8+03:40:15, xdelay=00:10:18, mailer=esmtp, pri=32250365, relay=example.com. [208.77.188.166], dsn=4.0.0, stat=Deferred: Connection timed out with example.com.
Dec  1 22:36:14 markserver sm-mta[4811]: mAO2tx04010773: mB26PuEl004811: sender notify: Cannot send message for 5 days
Dec  1 22:36:14 markserver sm-mta[4811]: mB26PuEl004811: to=<www-data@buckyspalace.net>, delay=00:00:00, xdelay=00:00:00, mailer=local, pri=30000, dsn=2.0.0, stat=Sent

```

Does this make sense to anyone? I currently host my domain with Ubuntu 7.10. I have reinstalled a couple of time previous (my errors) with no problems from sendmail. It used to be as simple as sudo apt-get install sendmail. Now, I am baffled.

I have the same problem

---

### Post by hictio on 2008-12-02
Well, the /etc/hosts its not by specs, it should be:
```

127.0.0.1   localhost.localdomain localhost
IP.address  FQDN 

```

The IP address as returned by the ifconfig command.
It seems to me that you have a firewall blocking access to the SMTP server, at least that one, have you tried sending an email test to a webmail address like Gmail or similar?
I don't think its a block form your internal firewall.

The DNS works ok on your box, right? Not the service, I mean, the name resolution is working Ok? Do you have a couple of nameservers declared on /etc/resolv.conf?

---

### Post by cdenley on 2008-12-02
> **R.Bucky said:**
> 
Here is the output from my mail.log
```
Dec  1 22:36:14 markserver sm-mta[4811]: mAO2tx04010773: to=<user@example.com>, ctladdr=<www-data@buckyspalace.net> (33/33), delay=8+03:40:15, xdelay=00:10:18, mailer=esmtp, pri=32250365, relay=example.com. [208.77.188.166], dsn=4.0.0, stat=Deferred: Connection timed out with example.com.
Dec  1 22:36:14 markserver sm-mta[4811]: mAO2tx04010773: mB26PuEl004811: sender notify: Cannot send message for 5 days
Dec  1 22:36:14 markserver sm-mta[4811]: mB26PuEl004811: to=<www-data@buckyspalace.net>, delay=00:00:00, xdelay=00:00:00, mailer=local, pri=30000, dsn=2.0.0, stat=Sent

```

So sendmail is unable to connect to example.com, and buckypalace.net works since it's local. It sounds like a networking problem to me.
```

dig mx +short example.com

```
Replace smtp.example.com with the first hostname from the output above.
```

nc -v -z smtp.example.com 25

```

Also, test your internet connection with something that should definitely work.
```

nc -v -z ubuntuforums.org 80

```

---

### Post by R.Bucky on 2008-12-02
I reconfigured the /etc/hosts file to read > 127.0.0.1   localhost.localdomain localhost
routerip  buckyspalace.net
Am I taking the localhost.localdomain to literally by leaving it exactly as above, or should the first line read something like localhost.computername  localhost?

After changing the /etc/hosts to what I have at the beginning of this post, my mail functions process extremely fast. However, no email was received at my gmail account. Going to restart my box and try it again...

---

