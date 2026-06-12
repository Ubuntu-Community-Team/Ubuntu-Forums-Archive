---
title: "Connect to my server via SMTP and send emails"
date: 2021-07-15
forum: Server Platforms
---

### Post by hiandyhi on 2021-07-15
I have Ubuntu 18.04 server. I have installed Postfix. I have set SPF record for domain + DKIM + TLS. Everything is working. Basically I can send emails via PHP scripts.

Now I want to send emails from this server by connecting to it via SMTP from remote server. How do I do that? I think I have to install Dovecot? Or can I use relay? I need simple solution. Simple authentication and send that email. That would be it.

---

### Post by TheFu on 2021-07-15
Dovecot is for imap only and has nothing to do with SMTP. Postfix is an MTA and all you need for a basic SMTP server.  It can be a relay or not.  Depends on your requirements. Generally, it is a bad idea to setup postfix as a relay, since when it is an open-relay, the world will discover it quickly and start using it to spam everyone.

SMTP traffic is 2 types. Unauthenticated and authenticated.

Unauthenticated is email between unrelated SMTP servers.  All this happens on post 25/tcp. That's what happens when smtp.gmail.com sends you an email at [email]bob@domain.com[/email].  Your email server with a DNS MX record for domain.com accepts random emails from any SMTP in the world looks at the TO, decides if those make sense for the mail.domain.com server to accept or not. If the "TO" isn't for a domain that postfix has been configured to accept, then the email should be rejected.  If the remote server connecting to you mail.domain.com server is in a spam block list or the domain it comes from isn't in the SPF list or the DKIM signatures for the message and the server don't match, then it should also be rejected. SMTPS is optional.  Get SMTP working first.

Authenticated is email between a client that connects to your server with a login on port 587/tcp or 465/tcp.  That means the email server must have a list of all users and all aliases, in addition to a password database.  Running an email server that does this requires stronger security, because 100,000 "bad guy" servers around the world will start trying to brute force userids and passwords very quickly.  Be certain you setup a limit for the number of failed passwords for each userid and from each remote server.   Back when I allowed remote email to be sent without a VPN connection first, my server was seeing hundreds of thousands of attempted logins.  In the end, it was just easier to take authenticated email connections off the internet and mandate client access go through a VPN, get onto a subnet we control before allowing any SMTP from end-users.

If you want steps, howtoforge has this: [https://www.howtoforge.com/ispconfig-autoinstall-debian-ubuntu/](https://www.howtoforge.com/ispconfig-autoinstall-debian-ubuntu/) Just don't enable the parts you don't want and don't open the firewall ports for services you don't want exposed.
> 
Now I want to send emails from this server by connecting to it via SMTP from remote server. How do I do that? I think I have to install Dovecot? Or can I use relay? I need simple solution. Simple authentication and send that email. That would be it. 

Any remote email server should be able to send unauthenticated SMTP to your server, unless the system is blocking port 25 or the ISP is blocking port 25. This assumes you own the domain and have configured the C, A, and MX records in DNS for the mail server.
If you want a remote server that is under your control to be allowed to send SMTP to this server, then configure the remote server to post to it as a relay host in the postfix. This happens on the remote system.  /etc/postfix/main.cf - obviously, use your IP or DNS name.
```
relayhost = 150.22.22.45
```
On the local email server, setup the mynetworks in the  /etc/postfix/main.cf  to include that remote system.  There are other details, mostly around the FQDNs for each system that should be related, but those aren't THAT important, just handy for good filters.

Be certain you run SMTP tests from remove services to verify that none of your email system will accept emails from any servers and relay them to servers you don't control, unless the domain used comes from systems under your control.  If you fail to do this for very long, your systems will be placed onto a email server blacklist.  Good luck getting off that.

---

### Post by hiandyhi on 2021-07-15
Thank you for your reply. I had to read it 3 times to absorb all the information.

I'm not sure your linked step by step guide is related. **My end goal is to give you (or somebody else) this information:**

[PHP]
MAIL_MAILER=smtpMAIL_HOST=mail.myserver.comMAIL_PORT=2525MAIL_USERNAME=theFuMAIL_PASSWORD=yourPasswdMAIL_ENCRYPTION=tls[/PHP]

**You will insert it to into you PHP framework and will be able to use my server to send emails. That's the goal.**

---

### Post by TheFu on 2021-07-15
If you want to treat remote php programs as "users", then it isn't an SMTP -to- SMTP connection.  It is an end-user -to- email server connection. This doesn't sound like a very good idea to me. You are at the whim of these other systems and are trusting them not to spam the world. If any one of them does, then you'll need to cancel their account quickly and probably try to get your email server removed from blacklist status.  You couldn't pay me enough to do that.   $20K/month isn't enough, since I'd need a team of people to deal just with those negative aspects.

If it were me, I'd rather have those remote servers setup their own email sending stuff and keep me and my systems out of it.  When they get blacklisted, it wouldn't impact my server at all.

Plus, php webapps are constantly being cracked, so having email sending easily available from them wouldn't be good.

The link for instructions above most definitely sets up an email server that can accept inbound end-user emails. The usernames/passwords are stored inside a MariaDB, I think. Having 20,000 email users wouldn't be hard for that single system on any $5K Linux server.  200 email users would be easy on a $10/month VPS following those instructions.

BTW, while you could use port 2525/tcp for this, normally port 587/tcp would be preferred.

---

### Post by ActionParsnip on 2021-07-15
Can you send an email using telnet OK? Does this work as expected?

---

### Post by hiandyhi on 2021-07-15
Essays on internet security won't help me at all.

I simply have server that is capable of sending emails. It works. On separate machine I want fill in these fields in Laravel (PHP framework) and use first server to send emails.

[PHP]
MAIL_MAILER=smtp
MAIL_HOST=mail.myserver.com
MAIL_PORT=2525
MAIL_USERNAME=theFu
MAIL_PASSWORD=yourPasswd
MAIL_ENCRYPTION=tls 
[/PHP]

Every single emailing service will give you access to their server in this format. So it is possible and secure. I just don't know how to set it up on my own server.

---

### Post by howefield on 2021-07-15
Thread moved to the "*Server Platforms*" forum.

---

### Post by TheFu on 2021-07-15
[http://www.postfix.org/SASL_README.html](http://www.postfix.org/SASL_README.html) and  [https://www.howtoforge.com/postfix-smtp-authentication-on-the-secure-port-only](https://www.howtoforge.com/postfix-smtp-authentication-on-the-secure-port-only) are probably what you want.

How many spam emails did you get today? Guess where those originated?  Not from my systems.

---

### Post by hiandyhi on 2021-07-16
How would they originated from my server if login is necessary?

---

### Post by LHammonds on 2021-07-16
Are you only wanting capability to send email from scripts on your server?  You can just use a lightweight SMTP mailer configured to use an existing mail server.

Example: [Setup Server for Sending Email using sSMTP]("https://hammondslegacy.com/forum/viewtopic.php?f=40&t=257")

LHammonds

---

### Post by TheFu on 2021-07-16
> **hiandyhi said:**
> How would they originated from my server if login is necessary?

That is obvious, isn't it?
[LIST]
[*]Misconfigured server
[*]Program bugs
[*]Poor passwords
[/LIST]

In the data security world, if you are using passwords to secure stuff, then you've already lost the battle.
How much spam is there in the world?  That amount shows how bad humans are at setting up and running secure servers. I assume I'm bad at it too, though I'm the best driver in the world, really. ;)  I'm an excellent driver.

---

### Post by MAFoElffen on 2021-07-16
> **LHammonds said:**
> Are you only wanting capability to send email from scripts on your server?  You can just use a lightweight SMTP mailer configured to use an existing mail server.

Example: [Setup Server for Sending Email using sSMTP]("https://hammondslegacy.com/forum/viewtopic.php?f=40&t=257")

LHammonds

That is exactly what I use SMTP for... I use scripts to generate email notifications to admin email accounts. And use ACL lists for where they are routed to/from within that infrastructure.

Note.: Do not use TelNet is place of. Generally speaking, there are more vulnerabilities in TelNet than in Email Servers.

It all depends how the infrastructure lays out and on what internal networks to that. You haven't mentioned what is Public, and what is not. Generally, there are security issues if that is Public. But if that is all shielded internally, or if pipes between are tunneled and encrypted within that infrastructure, well... Then a different story. Right?

---

### Post by TheFu on 2021-07-17
I'm fairly certain that the suggestion to telnet into the SMTP daemon was just for testing. Doubt anybody here would suggest installing and running telnetd.

Telnet as a client is handy for connecting to different services and manually sending commands.  An entire mail connection and sending message can be manually done using telnet as a client.  Also handy for HTTP server testing - connect to a server and enter "GET" - see what happens.
```
$ telnet www.google.com 80
GET
```

---

