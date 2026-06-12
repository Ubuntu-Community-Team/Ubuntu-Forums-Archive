---
title: "My Own Mail Server?"
date: 2010-08-27
forum: Server Platforms
---

### Post by asddf on 2010-08-27
How can I set up my own mail server, and send emails from it, without having to pay for a webhost or gmail etc?

Just a server I can send email from?

---

### Post by lisati on 2010-08-27
Moved to "Server Platforms"

Getting an email server up and running *can* take a little bit of work. 

I use [Postfix]("https://help.ubuntu.com/community/PostfixBasicSetupHowto") to send and receive emails in conjunction with a free domain name from [dyndns]("https://www.dyndns.com").

For POP/IMAP/SMTP access on my system I use [Dovecot]("https://help.ubuntu.com/community/Dovecot"). There are also options available for giving your system webmail functionality.

Something to note is that receiving emails can be a bit tricky (but not impossible) if you have a dynamic IP address or your ISP blocks port 25. One workaround is to use your current email address to receive emails, and have fetchmail pull in emails into your local server.

---

### Post by Lars Noodén on 2010-08-29
You are looking for an SMTP server.  Look in the Ubuntu repository and you'll find several for low-traffic, including exim and postfix.

---

### Post by baudday on 2010-08-29
One thing you should know, some ISPs (such as comcast for instance) blacklist their block of IPs to try and avoid their customers sending spam. 

I have a post on my blog I did a few years back where I detail setting up my first mailserver.

---

### Post by Lars Noodén on 2010-08-30
> **baudday said:**
> One thing you should know, some ISPs (such as comcast for instance) blacklist their block of IPs to try and avoid their customers sending spam. 

I have a post on my blog I did a few years back where I detail setting up my first mailserver.

Too many do that because too many home users try to connect Windows to the net.  Some ISPs allow sending via their stmp server and then you can set up a 'smart host' or satellite.  Receiving mail might be harder.

---

