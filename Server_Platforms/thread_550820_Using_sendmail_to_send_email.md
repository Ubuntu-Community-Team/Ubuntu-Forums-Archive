---
title: "Using sendmail to send email?"
date: 2007-09-14
forum: Server Platforms
---

### Post by UbuNewbie123 on 2007-09-14
I have installed sendmail on my Ubuntu Server machine.

Edit php.ini: 

```
; For Win32 only.
;sendmail_from = me@localhost.com

; For Unix only.  You may supply arguments as well (default: "sendmail -t -i").
sendmail_path = /usr/sbin/sendmail -t -i

```

Then I restarted my XAMPP. I tried to send email with a PHP mail script but I don't receive any emails. Is there anything else I should edit?

Here's the /var/log/mail.log file contents: 

```
Sep 14 11:52:42 ubuntu-server sendmail[7413]: My unqualified host name (ubuntu-server) unknown; sleeping for retry
Sep 14 11:53:42 ubuntu-server sendmail[7413]: unable to qualify my own domain name (ubuntu-server) -- using short name
Sep 14 11:53:42 ubuntu-server sendmail[7413]: gethostbyaddr(192.168.0.6) failed: 1
Sep 14 11:58:31 ubuntu-server sendmail[7418]: My unqualified host name (ubuntu-server) unknown; sleeping for retry
Sep 14 11:59:31 ubuntu-server sendmail[7418]: unable to qualify my own domain name (ubuntu-server) -- using short name
Sep 14 11:59:31 ubuntu-server sendmail[7418]: l8E3xVHi007418: from=nobody, size=123, class=0, nrcpts=1, msgid=<200709140359.l8E3xVHi007418@ubuntu-server>, relay=nobody@localhost
Sep 14 11:59:31 ubuntu-server sm-mta[7423]: l8E3xVpO007423: from=<nobody@ubuntu-server>, size=344, class=0, nrcpts=1, msgid=<200709140359.l8E3xVHi007418@ubuntu-server>, proto=ESMTP, daemon=MSP-v4, relay=localhost [127.0.0.1]
Sep 14 11:59:31 ubuntu-server sendmail[7418]: l8E3xVHi007418: to=myemail@whatever.com, ctladdr=nobody (65534/65534), delay=00:00:00, xdelay=00:00:00, mailer=relay, pri=30123, relay=[127.0.0.1] [127.0.0.1], dsn=2.0.0, stat=Sent (l8E3xVpO007423 Message accepted for delivery)
Sep 14 11:59:33 ubuntu-server sm-mta[7425]: STARTTLS=client, relay=whatever.com., version=TLSv1/SSLv3, verify=FAIL, cipher=AES256-SHA, bits=256/256
Sep 14 11:59:34 ubuntu-server sm-mta[7425]: l8E3xVpO007423: to=<myemail@whatever.com>, ctladdr=<nobody@ubuntu-server> (65534/65534), delay=00:00:03, xdelay=00:00:03, mailer=esmtp, pri=120344, relay=whatever.com. [74.200.79.210], dsn=5.1.1, stat=User unknown
Sep 14 11:59:35 ubuntu-server sm-mta[7425]: l8E3xVpO007423: l8E3xZpO007425: DSN: User unknown
Sep 14 11:59:35 ubuntu-server sm-mta[7425]: l8E3xZpO007425: to=<nobody@ubuntu-server>, delay=00:00:00, xdelay=00:00:00, mailer=local, pri=30000, dsn=2.0.0, stat=Sent
Sep 14 12:00:01 ubuntu-server sm-msp-queue[7444]: My unqualified host name (ubuntu-server) unknown; sleeping for retry
Sep 14 12:01:01 ubuntu-server sm-msp-queue[7444]: unable to qualify my own domain name (ubuntu-server) -- using short name 
```

I am trying to send an email to [email]myemail@whatever.com[/email]. I am getting errors like **unable to qualify my own domain name (ubuntu-server)** and **DSN: User unknown**.

Could anyone help me out? This is my first time using sendmail for Linux. I have successfully configured sendmail for Windows.

---

### Post by HermanAB on 2007-09-14
Uhhh, unless you are a committed masochist, you should uninstall sendmail and rather use Postfix or Qmail.

I suggest that you go to the postfix.org web site and start reading.

Cheers,

Herman

---

### Post by UbuNewbie123 on 2007-09-14
Postfix looks more complicated to me. I am checking out Qmail now.

---

### Post by HermanAB on 2007-09-14
If you want a complete mail system that does absolutely everything and installs in about 20 minutes, then you should look at Citadel: [http://www.citadel.org/doku.php](http://www.citadel.org/doku.php)

Citadel Easy Install is the easiest thing ever.

Cheers,

H.

---

### Post by UbuNewbie123 on 2007-09-14
I remember in the windows version of sendmail, I could specify a username and password for my SMTP service. Any idea how to do that in sendmail for linux?

---

### Post by UbuNewbie123 on 2007-09-15
I finally got it to work by installing and configuring exim4 on top of sendmail.

Here's how I did it:

[http://ubuntuforums.org/showthread.php?p=3368753#post3368753](http://ubuntuforums.org/showthread.php?p=3368753#post3368753)

---

### Post by UbuNewbie123 on 2007-09-15
I tried sending emails to a few different email addresses. One of them reached me within 5 seconds while the others have not reached me yet. I hope they are not lost

---

### Post by UbuNewbie123 on 2007-09-15
> **HermanAB said:**
> If you want a complete mail system that does absolutely everything and installs in about 20 minutes, then you should look at Citadel: [http://www.citadel.org/doku.php](http://www.citadel.org/doku.php)

Citadel Easy Install is the easiest thing ever.

Cheers,

H.

I just want my PHP mail function to send emails. Why would I need to install citadel with all the bells and whistles I do not need?

---

### Post by HermanAB on 2007-09-15
Depends on what you need.  If you need a full blown mail system, then Citadel is hard to beat.

---

### Post by Johnsie on 2007-09-15
sudo apt-get install postfix

That should make it easy to install postfix

to use postfix in php you just use the lines:

> 
$subject=  "subject of the email";
$to = "john@nospam.net";
$headers = 'From: whatever';   //you can change whatever to the something else
$body ="blahhhh)";
mail("$to","$subject","Message: $body",$headers);  


Play around with the code a bit to get some emaills sending the way you want. Make sure outside users cannot connect to port 25 on your machine.

---

### Post by UbuNewbie123 on 2007-09-15
My PHP code is fine because I have managed to send an email to 1 of my email addresses.

I am trying to use my ISP's SMTP mail server to send emails to avoid all the relaying problems.

---

