---
title: "Spent three months and still can't configure Postfix"
date: 2009-01-04
forum: Server Platforms
---

### Post by anil_robo on 2009-01-04
This is really really annoying. I can just enter some basic information to configure Evolution and it's able to send emails using my gmail account. However, even after trying to configure it for three months, Postfix is not yet working.

I've come to a point where I even can't start/stop/remove postfix. This is what I get:

```
postfix: fatal: config variable inet_interfaces: host not found: smtp_tls_loglevel
```

And now I'm angry. smtp_tls_loglevel is just a variable, it's not an inet interface! Any help would be greatly appreciated! Please someobdy help!

---

### Post by HermanAB on 2009-01-04
Well, Postfix is a good way to learn how a mail system works, but actually using it is painful (though much less painful than sendmail).

I suggest that you go here and install Citadel (It only takes about 20 minutes to configure):
[http://www.citadel.org/doku.php?id=installation:start](http://www.citadel.org/doku.php?id=installation:start)

Here is a guide: [http://aeronetworks.ca/citadel-howto.html](http://aeronetworks.ca/citadel-howto.html)

You can also download a preconfigured Citadel VM from the VMware web site, but it is actually faster to run the Easy Install script than to download the VM.

Citadel is very old, stable and does every mail protocol.  It also works with all mail clients (even Outlook) and includes a web mail system, calendars and more.  It can handle tens of thousands of users on modest hardware and can store up to 256 Terabytes of mail.  You can literally replace dozens of Exchange servers with a single Citadel server.  Yet, it works just as well with a single user account as with thousands of accounts.

Cheers,

Herman

---

### Post by anil_robo on 2009-01-04
Thanks [HermanAB]("http://ubuntuforums.org/member.php?u=44990")

It seems Citadel is like setting up your own email server rather than relaying through gmail (for example). It looks simple enough, and I'm tempted to give it a try. However, do you think it'll work without removing postfix first?

---

### Post by HermanAB on 2009-01-04
I think the Citadel installer will disable Postfix.  You cannot have multiple mailers running on one machine since they will want to bind to the same ports.

It can also forward mail to an ISP mail system and can pop mail off an ISP as well.  Everything you need is built in.

Citadel is a complete mail system.  I have been using it for a number of years and I host mail for a number of small companies on a single server.  It just works - no trouble at all.  If you use Thunderbird with it, do use IMAP over SSL for a secure connection.

Cheers,

Herman

---

### Post by anil_robo on 2009-01-04
Unfortunately Citadel installation failed... it couldn't install "Webcit" and the logfile is full of warnings and two errors :(

---

### Post by HermanAB on 2009-01-05
The log file should tell you what is the matter.  You can also post questions on the Citadel Uncensored BBS: [http://www.citadel.org/doku.php?id=mailing_lists](http://www.citadel.org/doku.php?id=mailing_lists)

Cheers,

Herman

---

### Post by anil_robo on 2009-01-05
I gave up and retried Exim4 and I am now able to send emails using Webmin interface. I'm now working to make php send emails using "mail" function so my phpbb forum can be email-enabled. Thanks for the support, HermanAB!

---

### Post by HermanAB on 2009-01-05
Good news!

However, if you can remember what Citadel complained about during the install, then you should report it on the Uncensored BBS since then some good can come of it.  Otherwise, your struggle with it was a pure waste of time.

Cheers,

Herman

---

