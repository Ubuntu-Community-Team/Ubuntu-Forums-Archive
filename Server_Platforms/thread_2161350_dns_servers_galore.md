---
title: "dns servers galore"
date: 2013-07-10
forum: Server Platforms
---

### Post by Vegan on 2013-07-10
I am familiar with BIND but mostly via webmin.

Is there any shell script I can use to call to add a new A record, CNAME record and MX record to bin in a way that it is smart enough to increment versions and create if not known

also operating like a public DNS, such Google's 8.8.8.8 and 8.8.4.4

I am aware that SAMBA can deal with Windows clients fine

if I need a database MySQL can be installed etc as needed

---

### Post by CharlesA on 2013-07-10
You might need to write something up and pass on whatever arguments you want to add. I don't use BIND, but that shouldn't be too difficult as everything is stored in flat files.

---

### Post by Habitual on 2013-07-10
[http://bash.cyberciti.biz/domain/create-bind9-domain-zone-configuration-file/](http://bash.cyberciti.biz/domain/create-bind9-domain-zone-configuration-file/) ?

---

### Post by Vegan on 2013-07-12
what I wanted to do was use a simply web form, with one box for the domain.net and the other for the IP address

so I when I post I wanted to insert the domain and ip address into the DNS 

I can use a shell script but I also have PHP available

---

### Post by SeijiSensei on 2013-07-13
> **Vegan said:**
> what I wanted to do was use a simply web form, with one box for the domain.net and the other for the IP address

Just a warning that you will need to configure permissions for the zone files carefully if you take this approach.  The Apache server is running as user www-data which has no permissions to write to /etc/bind9/.  

Any domain will need more than a single IP address, unless they all share the same NS and MX servers.  Plus you'll need to handle multiple hostnames within the domain.  You'll also need to add an entry for the domain to named.conf, and you'll have to update the backup DNS server's named.conf as well.  Since the backup should be on another server, preferably in a different geographic location, you'll have to run some kind of background task to update the backup's named.conf.

Frankly, I think it is easier simply to clone existing zone files and edit them as needed.  I once thought about designing a PHP app for the task and decided it was overkill.

---

### Post by Vegan on 2013-07-15
the way I see DNS is to have one primary DNS server and the rest are slaves

besides LAMP+BIND what other packages will be needed for a MX server

usually a shell script is what I have found to be useful

Webmin can do some of the work manually, but I wanted to see if I could mechanize the whole show

---

### Post by SeijiSensei on 2013-07-16
> **Vegan said:**
> besides LAMP+BIND what other packages will be needed for a MX server

Postfix or an equivalent MTA like sendmail or exim to handle exchanges with other servers.  If the server also will store the users' mailboxes, then a POP/IMAP server like dovecot will be required as well.  

However I would recommend you look into [MailScanner]("http://www.mailscanner.info/") which can manage all the virus and spam scanning for you.  In conjunction with ClamAV and SpamAssassin, it will make a big dent in the amount of junk you will receive and protect your users from malware.

Remember, on most mail servers, for every legitimate piece of email you receive, you'll get nine pieces of junk.

---

### Post by Vegan on 2013-07-17
I downloaded the PDF manual for mailscanner, may as well learn about its use

I have looked at postfix, but not the others, are all MTAs created equal?

I have also seen dovecot which seems to be the #1 choice for mailbox service

SpamAssassin is known to me as well, as is ClamAV, but I am not using a desktop, only the CLI

---

### Post by Vegan on 2013-07-17
I want to also use domain specific email accounts, which will need lots of configuration

i want to filter out messages from unrecognized hosts etc

how about a swarm of MTAs riding beside the DNS servers

---

### Post by CharlesA on 2013-07-17
> **Vegan said:**
> 
I have looked at postfix, but not the others, are all MTAs created equal?

I've used Exim and Postfix before and I prefer Postfix, but that might be cuz I'm used to the configuration now. :lol:

Sendmail is also out there, but I have seen it only recommended for experienced people, who know how to secure it properly.

---

### Post by SeijiSensei on 2013-07-17
Current versions of sendmail are no more vulnerable than current versions of other MTAs.  Sendmail's reputation for insecurity is due largely to its longevity.  It's been considerably hardened over the years.  I still use a version of the ancient store-and-forward SMTP listener called [Obtuse smtpd]("http://ubuntuforums.org/showthread.php?t=2020502&p=12086826#post12086826") on my main server because it has excellent anti-spam controls, but I have other machines running where sendmail is directly exposed to the Internet.  We haven't had any problems with security.

Any decent mail server needs to filter malware and spam.  There are many alternatives for this, but I like MailScanner because it enables everthing to be managed centrally.  Each message that arrives is scanned first for viruses using a combination of filetype rules (no ".exe" file attachments for instance) and ClamAV.  (You can use commercial scanners if you prefer.)  Then if the message is marked clean, it is passed to SpamAssassin for scoring.  I tag messages that get an SA score between 4 and 7 as "likely spam" and deliver them to the recipients with a {Spam?} tag in the subject line.  Anything over seven gets put in quarantine.  At one client's site, with about 200 employees, we quarantined over 2100 spam messages just yesterday alone.

---

