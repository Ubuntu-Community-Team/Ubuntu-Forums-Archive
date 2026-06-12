---
title: "spam/antivirus firewall?"
date: 2006-06-05
forum: Server Platforms
---

### Post by badjohny on 2006-06-05
I am looking to try to setup a firewall of sorts for my email server.  I want to setup a box that scans all incoming emails for spam or viruses before the mail is even delivered to my main email server.  Is this possible?  And if so, could anyone point me in the right direction for setting this up?

---

### Post by linuxone on 2006-06-05
Hi,

[QUOTE=badjohny]I am looking to try to setup a firewall of sorts for my email server.  I want to setup a box that scans all incoming emails for spam or viruses before the mail is even delivered to my main email server.  Is this possible?  And if so, could anyone point me in the right direction for setting this up?[/QUOTE]

check ... for expample:

[postfix spam configuration](http://www.postfix.org/spam.html)
[spamassasign](http://spamassassin.apache.org)

[clamav - Linux AntiVirus](http://www.clamav.net/)

[commercial anti-virus solution](http://www.kaspersky.com/smb?chapter=153207951) (Kaspersky Anti-Virus for Linux/Unix Mail servers)

Thomas

---

### Post by badjohny on 2006-06-06
[QUOTE=linuxone]Hi,



check ... for expample:

[postfix spam configuration](http://www.postfix.org/spam.html)
[spamassasign](http://spamassassin.apache.org)

[clamav - Linux AntiVirus](http://www.clamav.net/)

[commercial anti-virus solution](http://www.kaspersky.com/smb?chapter=153207951) (Kaspersky Anti-Virus for Linux/Unix Mail servers)

Thomas[/QUOTE]


Those will allow me to setup a sperate server just for scanning emails?  The reason i need this is we have multiple brances of our organization that don't share common hardware.  But, I would like to setup one machine that would allow all our various email servers to point to it to get email that has already been scanned for viruses and spam.  

We currently have 5 email servers and it would be alot easier to have a central location setup to scan for virus/spam.  I realize these programs listed will scan for virus and spam, but i was looking for a guid to setup this proxy/firewall to filter out the spam and how to setup my network to use this server.  right now we have multiple email servers all with their own IP addresses.  The process I would like to see would be something like this:


incoming email goes to the email/spam server.
the server scans all the email.
the 5 email servers of the various branches then get the email from the server after it has been scanned.
the it is passed out like normal email.

Sorry if this is confusing.  I am not sure i am explaining it correctly.

---

### Post by mjm115 on 2006-06-06
[http://www.howtoforge.com/perfect_setup_ubuntu_6.06](http://www.howtoforge.com/perfect_setup_ubuntu_6.06)

This guide is a detailed description about how to set up a Ubuntu 6.06 LTS (Dapper Drake) based server that offers all services needed by ISPs and hosters (web server (SSL-capable), mail server (with SMTP-AUTH and TLS!), DNS server, FTP server, MySQL server, POP3/IMAP, Quota, Firewall, etc.).  I hope this will help you.

---

### Post by badjohny on 2006-06-06
I will read that through.  I also found a link to a program that looks to do what i want.

[http://assp.sourceforge.net/](http://assp.sourceforge.net/)

a anti spam smtp proxy.

---

### Post by A1ex on 2006-06-08
One word - MailScanner

[http://www.mailscanner.info/]("http://www.mailscanner.info/")

-A free anti-virus and spam filter
-Can be used with all the popular MTA's
-Protects 1 billion emails a day
-800,000 downloads
-Used by a huge list of corporations and academic institutions
-completely free

If you want to have added AV protection then you can add on commercial engines like sophos and kaspersky.

---

