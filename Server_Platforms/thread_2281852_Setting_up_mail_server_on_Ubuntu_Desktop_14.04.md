---
title: "Setting up mail server on Ubuntu Desktop 14.04"
date: 2015-06-10
forum: Server Platforms
---

### Post by Nian_Ying_Toh on 2015-06-10
Hi all, 

[COLOR=#111111][FONT=Ubuntu]I need help on setting up a mail server on Ubuntu Desktop 14.04 with a web interface for sandbox testing, tried using postfix and exim4 and it does not seems to work.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]My main concern is to setup a mail server to simulate the sending and receiving of email. I need it to run on my cuckoo sandbox for the scanning process.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Appreciate all the help that the experts can give.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]To be precise, I tried almost all the tutorials on both web and youtube, and I also tried squirrelmail for web gui, it shows the login page and after the login it pops a IMAP error.[/FONT][/COLOR]

Thank in advanced.

---

### Post by TheFu on 2015-06-10
Well, DNS MX records are closely tied to having a mail server that accepts inbound email from external locations. I don't scan emails from inside the LAN in the same way that I scan and assume emails from the nasty internet are full of stuff I don't want in our network.

So - what have you done? Post the config files and firewall rules and please describe how your different servers are supposed to be connected, or we really can't help much.  I'm a postfix guy - have been since the mid-1990s. Don't know anything about exim ... except to purge that if it ever gets installed due to a bad dependency (which has happened before).  

Only 1 MTA should be installed on a system at a time, BTW.

Sorry - dont know what "cuckoo sandbox" means.

---

### Post by Nian_Ying_Toh on 2015-06-10
Cuckoo sandbox is a malware analysis system, ermm... what I need is a simple email server internally, no external locations is needed as it is a testing environment. For this to work, it does not need any firewall. Sorry for asking a general question as I am new to forums.

---

### Post by SeijiSensei on 2015-06-11
You can try a pre-packaged server like [iRedMail]("http://www.iredmail.org/") or [Citadel]("http://www.citadel.org/doku.php").  Faster and easier than rolling your own.

---

### Post by wildmanne39 on 2015-06-11
*Thread moved to **Server Platforms**.*

---

### Post by Nian_Ying_Toh on 2015-06-11
> **SeijiSensei said:**
> You can try a pre-packaged server like [iRedMail]("http://www.iredmail.org/") or [Citadel]("http://www.citadel.org/doku.php").  Faster and easier than rolling your own.

Thanks a lot, will try =)

---

### Post by Habitual on 2015-06-12
Zimbra also!

---

### Post by TheFu on 2015-06-13
> **Habitual said:**
> Zimbra also!

Setting up Zimbra is too much of a hassle for something like this, IMHO. Zimbra **demands** MX DNS records. It **demands** 2G+ of RAM, cannot handle a non-trivial /etc/hosts and it is quite bloated compared to a postfix/dovecot solution which easily runs in 384MB of RAM for 50 users.

I've been running Zimbra servers since 2008 and if you need a full Ms-Exchange replacement with enterprise calendaring and delegation,  I don't know any better solution.

---

### Post by Nian_Ying_Toh on 2015-06-24
ok i tried iRedMail and now i got this error "This program was unable to connect or stay connected to the Citadel  server.  Please report this problem to your system administrator." , how do I solve this ?

---

