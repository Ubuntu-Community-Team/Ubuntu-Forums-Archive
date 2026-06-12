---
title: "Dovecot can't recieve emails"
date: 2008-12-04
forum: Server Platforms
---

### Post by andrewjmonks on 2008-12-04
I'm trying to set up a mail server using Postfix and Dovecot.  I installed and configured them pretty much exactly according to [the Ubuntu 8.10 Server Guide]("https://help.ubuntu.com/8.10/serverguide/C/email-services.html").  However, I haven't been able to receive any mail with Dovecot.  I know that it's listening, and I know that it allows remote login, and I know that it finds INBOX (by the guide at the [Dovecot Test Installation page]("http://wiki.dovecot.org/TestInstallation")).  I'm using mbox.

I can connect to it with mail.app, and with squirrelmail.  I can put mail onto the server by mving mbox files into ~/mail.  I can drag emails from other accounts into my imbox using mail.app, and they show up in /var/mail/ajm.

However, if I actually try to send an email to [email]ajm@andrewmonks.net[/email], it doesn't show up anywhere.

I've never set up a mail server before, and this is frustrating.  I have no idea what's going on.

---

### Post by Buffalo Soldier on 2008-12-04
Hi Andrew,

I'm not much of a help here, never configured Ubuntu as a mail server before. But I plan to do so next week, using the official documentation:
[LIST=1]
[*]Install MTA (Postfix) - [https://help.ubuntu.com/8.10/serverguide/C/postfix.html](https://help.ubuntu.com/8.10/serverguide/C/postfix.html)
[*]Install MDA (Dovecot) - [https://help.ubuntu.com/8.10/serverguide/C/dovecot-server.html](https://help.ubuntu.com/8.10/serverguide/C/dovecot-server.html)
[/LIST]

Is that the same guide you've been using?

---

### Post by hictio on 2008-12-04
> **andrewjmonks said:**
> I'm trying to set up a mail server using Postfix and Dovecot.  I installed and configured them pretty much exactly according to [the Ubuntu 8.10 Server Guide]("https://help.ubuntu.com/8.10/serverguide/C/email-services.html").  However, I haven't been able to receive any mail with Dovecot.  I know that it's listening, and I know that it allows remote login, and I know that it finds INBOX (by the guide at the [Dovecot Test Installation page]("http://wiki.dovecot.org/TestInstallation")).  I'm using mbox.

I can connect to it with mail.app, and with squirrelmail.  I can put mail onto the server by mving mbox files into ~/mail.  I can drag emails from other accounts into my imbox using mail.app, and they show up in /var/mail/ajm.

However, if I actually try to send an email to [email]ajm@andrewmonks.net[/email], it doesn't show up anywhere.

I've never set up a mail server before, and this is frustrating.  I have no idea what's going on.

What happens with the email that "doesn't show up anywhere"?
Does it bounce? Have you seeing any error message there?

Are you sure that the server that has the Dovecot service running is actually accepting emails?

---

### Post by andrewjmonks on 2008-12-04
> **hictio said:**
> What happens with the email that "doesn't show up anywhere"?
Does it bounce? Have you seeing any error message there?

Are you sure that the server that has the Dovecot service running is actually accepting emails?

The email doesn't bounce, and I haven't seen any error messages.  There's no record on the server of ever having received an email, but on the computer sending the mail there's no indication that it didn't work.

As for weather Dovecot is actually accepting emails, I assume so.  How could I check?  Could there be some recieve_email = yes setting in /etc/dovecot/dovecot.conf that I'm missing?  That wouldn't really surprise me if there was, but I can't find anything obvious.



Buffalo Soldier:  Yes.  Those are exactly the guides Im using.  [http://www.debianadmin.com/debian-mail-server-setup-with-postfix-dovecot-sasl-squirrel-mail.html](http://www.debianadmin.com/debian-mail-server-setup-with-postfix-dovecot-sasl-squirrel-mail.html) is pretty useful too, though, if you're still looking around.

---

### Post by hictio on 2008-12-04
> **andrewjmonks said:**
> The email doesn't bounce, and I haven't seen any error messages.  There's no record on the server of ever having received an email, but on the computer sending the mail there's no indication that it didn't work.

As for weather Dovecot is actually accepting emails, I assume so.  How could I check?  Could there be some recieve_email = yes setting in /etc/dovecot/dovecot.conf that I'm missing?  That wouldn't really surprise me if there was, but I can't find anything obvious.



Buffalo Soldier:  Yes.  Those are exactly the guides Im using.  [http://www.debianadmin.com/debian-mail-server-setup-with-postfix-dovecot-sasl-squirrel-mail.html](http://www.debianadmin.com/debian-mail-server-setup-with-postfix-dovecot-sasl-squirrel-mail.html) is pretty useful too, though, if you're still looking around.

Try basic networking stuff, from a Terminal, type one of these at a time:

SMTP (receives emails)
```

telnet IP.address.dovecot.server 25 (ENTER)

```

POP3 (Dovecot mail server)
```

telnet IP.address.dovecot.server 110 (ENTER)

```

IMAP (Dovecot mail server)
```

telnet IP.address.dovecot.server 143 (ENTER)

```

POP3S (Dovecot secure mail server)
```

telnet IP.address.dovecot.server 995 (ENTER)

```

IMAPS (Dovecot secure mail server)
```

telnet IP.address.dovecot.server 993 (ENTER)

```


Use either the internal IP address, and then the public IP address of the Dovecot server, to see if the problem it's there as well.

---

### Post by andrewjmonks on 2008-12-04
Yup.  I've tried that.  They all get 
```
Escape character is '^]'.
+OK Dovecot ready.
```
And once I'm logged into IMAP on a mail client (remotely or not), I can make mailboxes, and move things around and whatnot.  The only problem is that it won't receive mail sent to it.  That is, if I open Gmail and send a message to [email]ajm@andrewmonks.net[/email], it doesn't bounce, but it doesn't show up on the server, either.  It just sends itself into the void.

---

### Post by hictio on 2008-12-04
> **andrewjmonks said:**
> Yup.  I've tried that.  They all get 
```
Escape character is '^]'.
+OK Dovecot ready.
```
And once I'm logged into IMAP on a mail client (remotely or not), I can make mailboxes, and move things around and whatnot.  The only problem is that it won't receive mail sent to it.  That is, if I open Gmail and send a message to [email]ajm@andrewmonks.net[/email], it doesn't bounce, but it doesn't show up on the server, either.  It just sends itself into the void.

You even tried the SMTP one? Using the public IP address as well?
How long have you been testing this? Email usually bounce instantly if the destination address doesn't exist, but for "transient" network problems it might take up to 4 hours till you get the first notification that something's wrong (at least, on a plain vanilla Sendmail setup)

---

### Post by andrewjmonks on 2008-12-04
Gosh, you're right.  I hadn't tried the SMTP one.  "Connection refused".
I've been testing this for a few days now, and nothing's bounced.  But I guess that's because of SMTP not working.  Come to think of it, I haven't tested sending mail yet.
What should my next step be?

---

### Post by hictio on 2008-12-04
I would say that you have to determine why you can't connect to the SMTP port of that mail server.
make sure that the MTA that you are using is running (be that Sendmail, Postfix, etc) and if its, on the case of Sendmail, you have to be sure that it is listening not only on the loopback interface, and it isn't , then, make sure you don't have an internal firewall blocking access to the SMTP port, and if you don't make sure you don't have an external firewall blocking access to the SMTP port.
If you don't either, make sure you have port forwarding, etc, correctly setup to reach your server.

If I might ask, what kind of setup is this? Is this a box you made for testing out of a plain vanilla residential DLS line, for instance? If that's the case, it is really, really unlikely that you'll be able to reach your SMTP port from any other site than your LAN.

---

### Post by andrewjmonks on 2008-12-04
A ha!  I got postfix working, and I can send mail.  I can remotely connect to the SMTP port of the server, now, too.  SMTP is good, but I still haven't been able to recieve mail.  Now I guess it's a matter of waiting 4 hours to see if it bounces, right?

I'm using a plain vanilla Comcast cable modem connection, but I can connect to SMTP now, so I'm pretty sure that isn't the problem.

---

### Post by hictio on 2008-12-04
Ok, now that the things start to get more clear, its time to hit the logs!
Check the log file '/var/log/mail.log', you can page thru it with 'less' on the terminal, and also, setup dovecot to do logging, so you can see what's going.
On the Dovecot's config file, look for:
```

log_path =
info_log_path =

```
See where are they pointing, and if they are enabled.
Restart dovecot if you edit the file, to make the changes active.
You can see logs in real time on the console/ terminal like this:

```

tail -f /var/log/mail.log

```

Hit Ctrl + C to get back to the prompt.

---

### Post by andrewjmonks on 2008-12-04
New developments!

After trying to send an email to the server, I got the following message:

> This is an automatically generated Delivery Status Notification

THIS IS A WARNING MESSAGE ONLY.

YOU DO NOT NEED TO RESEND YOUR MESSAGE.

Delivery to the following recipient has been delayed:

    [email]andrew@andrewmonks.net[/email]

Message will be retried for 2 more day(s)

Technical details of temporary failure:
The recipient server did not accept our requests to connect. Learn more at [http://mail.google.com/support/bin/answer.py?answer=7720](http://mail.google.com/support/bin/answer.py?answer=7720)
[andrewmonks.net (1): Connection dropped]

  ----- Message header follows -----

Received: by 10.142.157.9 with SMTP id f9mr5688609wfe.87.1228359326266;
       Wed, 03 Dec 2008 18:55:26 -0800 (PST)
Received: by 10.142.224.15 with HTTP; Wed, 3 Dec 2008 18:55:26 -0800 (PST)
Message-ID: <677d4e280812031855t31e1a22dof8aca10838dec84e@mail.gmail.com>
Date: Wed, 3 Dec 2008 21:55:26 -0500
From: "Andrew Monks" <andrewjmonks@gmail.com>
To: [email]andrew@andrewmonks.net[/email], [email]ajm@andrewmonks.net[/email]
Subject: test
MIME-Version: 1.0
Content-Type: multipart/alternative;
       boundary="----=_Part_53741_11875483.1228359326275"

  ----- Message body suppressed -----

What now?

---

### Post by hictio on 2008-12-04
Read the link on the warning email, I bet its:
"The other domain is experiencing temporary networking problems."

Personally, I can't connect to the SMTP port of andrewmonks.no-ip.org nor andrewmonks.net.

```

% telnet andrewmonks.no-ip.org 25
Trying 24.91.110.60...
telnet: connect to address 24.91.110.60: Permission denied
telnet: Unable to connect to remote host
% telnet andrewmonks.net 25
Trying 24.91.110.60...
telnet: connect to address 24.91.110.60: Permission denied
telnet: Unable to connect to remote host

```

Check that you really have the port opened/ forwarded and that the ISP doesn't block it.

---

### Post by andrewjmonks on 2008-12-05
Well, darn.
I guess that's the problem, then.
Thanks for the help.

---

### Post by hictio on 2008-12-05
Yeah, again, check with your ISP, and double an triple check that you aren't firewalling or miss port forwarding the service.
Personally I have seeing many ISPs that are really anal when it comes to the SMTP port because of spamming.

---

### Post by MJN on 2008-12-05
Your server also isn't set as the responsible MTA for andrewmonks.net hence your mail will never be hitting your server anyway:
 
```
 <<>> DiG 9.2.3 <<>> @dns1.menandmice.com andrewmonks.net MX  
;; global options: printcmd 
;; Got answer: 
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 23429 
;; flags: qr rd ra; QUERY: 1, ANSWER: 2, AUTHORITY: 2, ADDITIONAL: 2 
 
;; QUESTION SECTION: 
;andrewmonks.net. IN MX 
 
;; ANSWER SECTION: 
andrewmonks.net. 86400 IN MX 10 mx00.1and1.com.   
andrewmonks.net. 86400 IN MX 10 mx01.1and1.com.   
 
;; AUTHORITY SECTION: 
andrewmonks.net. 172800 IN NS ns58.1and1.com.   
andrewmonks.net. 172800 IN NS ns57.1and1.com.   
 
;; ADDITIONAL SECTION: 
ns57.1and1.com. 14530 IN A 74.208.2.9   
ns58.1and1.com. 14530 IN A 74.208.3.8   
 
;; Query time: 410 msec 
;; SERVER: 217.151.171.7#53(dns1.menandmice.com) 
;; WHEN: Fri Dec 5 11:37:03 2008 
;; MSG SIZE rcvd: 154 
```
 
Mathew

---

### Post by KuruOujou on 2009-03-23
I don't like drudging up an old post, but this seems the perfect place to ask. I'm having the same problem, except I'm using 587 as my smtp port instead of 25. I can send mail OK, but I have to relay it through another server, but I can't receive any mail from anywhere other than this network. What do you think?

---

### Post by hictio on 2009-03-23
> **KuruOujou said:**
> I don't like drudging up an old post, but this seems the perfect place to ask. I'm having the same problem, except I'm using 587 as my smtp port instead of 25. I can send mail OK, but I have to relay it through another server, but I can't receive any mail from anywhere other than this network. What do you think?

What do you mean by "this network" exactly? Your LAN, that is, a private network?
You can't (and want to) receive emails over the internet to your domain?

---

### Post by Buffalo Soldier on 2009-03-23
Can you check your /etc/postfix/main.cf file? Look for the line that starts with "mydestination=". What does it says?

---

### Post by KuruOujou on 2009-03-23
> **hictio said:**
> What do you mean by "this network" exactly? Your LAN, that is, a private network?
You can't (and want to) receive emails over the internet to your domain?

I mean my LAN, and I would like to receive emails over the internet but can't. Sorry I didn't make that clear.

> **Buffalo Soldier said:**
> Can you check your /etc/postfix/main.cf file? Look for the line that starts with "mydestination=". What does it says?

```
ydestination = devnull.endoftheinternet.org, kuroserver, localhost.localdomain, localhost

```

I am using DynDNS, if that will change anything.

---

### Post by Buffalo Soldier on 2009-03-23
> **KuruOujou said:**
> I mean my LAN, and I would like to receive emails over the internet but can't. Sorry I didn't make that clear.



```
ydestination = devnull.endoftheinternet.org, kuroserver, localhost.localdomain, localhost

```

I am using DynDNS, if that will change anything.

Usually,

mydestination = {FQDN}, {mail server hostname}, localhost.localdomain, localhost

I guess that's not a problem with you mydestination settings.

---

### Post by KuruOujou on 2009-03-23
Guess not. Dang. Well, would using smtp over ssl help? What port is that, 4-something?

---

### Post by filidis on 2011-06-25
> **andrewjmonks said:**
> I'm trying to set up a mail server using Postfix and Dovecot.  ...

... I've never set up a mail server before, and this is frustrating.  I have no idea what's going on.

It was much more simple to me.
I configured Dovecot to search the mails in /var/mail instead of ~/Maildir (default)

---

