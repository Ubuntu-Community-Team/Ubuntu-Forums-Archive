---
title: "Learning how to set up and admin a ubuntu server"
date: 2008-03-12
forum: Server Platforms
---

### Post by radtek on 2008-03-12
I've never set up a server knowingly and strongly want to learn how. I've been running Ubuntu exclusively for close to two years so I know this is the way to go.

I downloaded 7.10 x86 64bit.

However, I wouldn't mind just setting up a server through my existing install of 7.10 386 32bit. Just to learn the ropes and still have a functional PC while I learn. I mostly use my laptop anyway so the PC can double as a server for now before being fully converted.

I want to have these features to start:

1. Web server to host my own low-traffic domain.
2. Email server to host my own mail.
3. FTP server to download files from anywhere.

Advice guys?

---

### Post by dmizer on 2008-03-12
have several suggestions for you.

1) keep your email server separate from your web/ftp server, as it will be your biggest target.
2) set up an sftp server instead of a regular ftp server, or just use stand alone ssh/scp for file transfer (good windows clients do exist for this).
3) install your server(s) in a vmware (or virtual server of your choice) virtual machine.

i think the best suggestion is the last one though.  this way, it is extremely easy to keep complete backups of your server.  if you mess things up or get hacked, you don't have to re-install anything, just pull out a backup and keep going.  you don't expose your production machine to the dangers of open ports.  much easier to control your server environment this way.  it also makes for a perfect test sandbox because you can clone your server and test how new implementations will work before putting them onto your production site.

---

### Post by sam-c on 2008-03-12
> **dmizer said:**
> have several suggestions for you.

1) keep your email server separate from your web/ftp server, as it will be your biggest target.
2) set up an sftp server instead of a regular ftp server, or just use stand alone ssh/scp for file transfer (good windows clients do exist for this).
3) install your server(s) in a vmware (or virtual server of your choice) virtual machine.

i think the best suggestion is the last one though.  this way, it is extremely easy to keep complete backups of your server.  if you mess things up or get hacked, you don't have to re-install anything, just pull out a backup and keep going.  you don't expose your production machine to the dangers of open ports.  much easier to control your server environment this way.  it also makes for a perfect test sandbox because you can clone your server and test how new implementations will work before putting them onto your production site.

[FONT="Arial Black"][SIZE="4"]Thanks
I have a similar Question.
I have a New Lenovo with AGH!! Vista and this Ubuntu 7.10
And Old Computer with two linux's on it and some VMware.
I want Lenovo as Server and PBell as Client with only One ADSL External Connection, 
Somewhere I heard that Eclipse can help me configure Webservers!?
Is that correct?
I have not managed to get Webmin running on Ubuntu 7.10.
I want a Simple Solution,
Thanks
Uncle Sam[/SIZE][/FONT]

---

### Post by hyper_ch on 2008-03-12
would you want a "web hosting" complete solution (multiple clients, apache2/php5, email, ftp, ssh, ...)?

---

### Post by faulkes on 2008-03-12
> **radtek said:**
> 
Advice guys?

See my signature for official and community based documentation
as it relates to running a server.

That should be a good starting point and reference for you as you
start your journey.

Faulkes

---

### Post by radtek on 2008-03-12
Nothing too fancy or complex. I just want to host a simple website- mainly to display how-to pages with pics for homebrewers. Not planning to sell stuff or even advertise- though that might be an option later.

---

### Post by hyper_ch on 2008-03-13
well, apache2/php5/mysql is quite easy to install however for running your own mailserver you'll need a static ip...

---

### Post by dmizer on 2008-03-13
> **hyper_ch said:**
> well, apache2/php5/mysql is quite easy to install however for running your own mailserver you'll need a static ip...

is it not possible to run a mail server through a dynamic domain service like dyndns?

edit:
confirmed ... at least with dyndns: [http://www.dyndns.com/support/kb/email_mail_exchangers_and_dns.html#dynamicdns](http://www.dyndns.com/support/kb/email_mail_exchangers_and_dns.html#dynamicdns)

---

### Post by hyper_ch on 2008-03-13
my mailserver blocks incoming mail from mailservers on dynips.

---

### Post by Harlequin on 2008-03-13
I would advise against building your own server from scratch unless building it is specifically what you want to learn and getting it up and running is secondry.

I would recommend grabbing Clark Connect.

[www.clarkconnect.com](www.clarkconnect.com)

There is a community open source version with only minor limitations on the purchased version (namely a 10 mailbox limit).  It comes with everything you need - webmail, smtp, ldap, ftp server, imap, sendmail, clamav, spamassassin (also compatable with D-spam if you're brave), webserver, etc etc.

Its an RPM based system rather than a deb based but it can be up and running off the disk in under an hour.  

I started with this system and then expanded my network behind it.  Now it acts as my LDAP, Mail, DHCP, web proxy / filtering system and firewall with a FreeNAS file server, a MySQL server, Asterisk phone, and backup server behind it.  I'm using it in a commercial mission critical environment and not had a single problem with it in close to 2 years other than D-Spam which is an add in and had its own issues.

---

### Post by dmizer on 2008-03-13
> **hyper_ch said:**
> my mailserver blocks incoming mail from mailservers on dynips.

the isp smtp server would be suitable (and preferable) ... i believe dyndns provides for that option as well.  just have to make sure that the dyndns pop account is entered into the "return to" field of the outgoing email.

though, i suppose that would negate about half the point of making an email server as a learning tool.

---

### Post by vpsville on 2008-03-13
I would suggest using a VPS, since it will give you a static IP and you can re-install in a minute or two if you screwed up very badly.  Backups are also a good idea :)

For email you will want a static IP and SPF defined on your DNS server.  Otherwise you won't be able to send to gmail or hotmail addresses, and probably many more places too.

---

### Post by hyper_ch on 2008-03-13
spf is getting more popular... although I don't enforce that sender mailservers have it defined (as most haven't yet) I do however check if it is set whether supplied info is ok...

---

