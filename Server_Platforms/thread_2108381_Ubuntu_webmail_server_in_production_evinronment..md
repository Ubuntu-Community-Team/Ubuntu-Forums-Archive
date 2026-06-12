---
title: "Ubuntu web/mail server in production evinronment."
date: 2013-01-24
forum: Server Platforms
---

### Post by billyboy1978 on 2013-01-24
I've recently installed a server (12.04) with Apache, Postfix and Courier. Is this a system you can rely on in a production evinronment? The server (VPS) is hosting both emails and websites.

> Specs:
Ram 2GB
120 GB disk
OS: Ubuntu 12.04 (64-bit)

The thing that worries me the most is, what do I have to do to keep the mail-part up to date? Does this setup require much work in terms of servermanagement?

This is my first fullblown Apache, postfix and Courier install ever. But for now it's working perfectly.
I do have some experience with CentOS (servers) and Ubuntu (desktop)

Thanx for any replies ;)

EDIT:
btw. followed [this How-To]("http://www.howtoforge.com/virtual-users-and-domains-with-postfix-courier-mysql-and-squirrelmail-ubuntu-12.04-lts")

---

### Post by sandyd on 2013-01-24
Running
```

sudo apt-get upgrade
```
once in a while will keep all of the software on the system updated.

If the mailserver is quite important, you may want to setup a testing/staging server to test updates before installing it on the actual server.

---

### Post by billyboy1978 on 2013-01-24
Thank you for your reply.

So the mail server is vulnerable in terms of system-updates? What about configs, any possibility that they're being overwritten in a debian based system without any warning?

---

### Post by sandyd on 2013-01-24
> **billyboy1978 said:**
> Thank you for your reply.

So the mail server is vulnerable in terms of system-updates? What about configs, any possibility that they're being overwritten in a debian based system without any warning?

Havent ever experienced anything like that. yet. I still backup them anyways.

---

### Post by billyboy1978 on 2013-01-25
Ok, thanx. But I wonder.. I might gonna outsource the mailservice, and run a webserver only. Dont want to lose mails for my clients, thats bad business for sure.

Any thoughts about this?

---

### Post by SeijiSensei on 2013-01-25
Outsource to another mail provider?  How about [Google]("http://www.google.com/intl/en/enterprise/apps/business/products.html")?  They won't lose your clients' mail.  

Are the clients organizations for which you need to support multiple mailboxes, or largely individuals?  For the latter, you might find your domain provider offers simple POP3 mail drops for the domains you register like my provider [DirectNIC]("http://directnic.com/features/email.php") does.

---

### Post by billyboy1978 on 2013-01-26
> **SeijiSensei said:**
>  Are the clients organizations for which you need to support multiple mailboxes, or largely individuals?  [..]

Both actually, thanx, I'll have a look into it.

BTW, Is it recommended to run my own combined web/mailserver?

---

### Post by SeijiSensei on 2013-01-26
That's pretty much impossible to say without knowing your abilities in greater detail.  How much attention do you intend to pay to it?  How much experience do you have with mail services?  What will you do about spam and viruses?  What about mail that apparently gets "lost" because it was falsely tagged as spam? Will you be available to hold your clients' hands while you figure out what the problems are?  Do you intend to offer IMAP as well as POP?  IMAP puts a greater load on storage space because all the mail resides there.  It also creates the need for reliable backups and for strong security.

What kinds of clients you have makes a difference as well.  Medical providers in the US are governed by the HIPAA privacy and security rules, for instance, which means you would be governed by them as well.

In general clients are much more cognizant about problems with mail because they expect it to magically appear in their mailboxes 24/7 and will notice it when something goes wrong.  They are less likely to notice problems with web services since the intended audience is outside the organization.

---

### Post by billyboy1978 on 2013-01-27
Thats what im talking about, looks like it 'll give me hard times regarding this mailservice. Better get an external mailservice for my clients. 

My primary "administratorskills" are within the CentOS/RHEL webserver (only) segment, and that mean I've to compile a lot of packages for postfix, as this is not native RHEL packages. I KNOW this will give me a headache, when Ill are updating the system. This is the main reason for trying Ubuntu this time.

Anyway, thanx for your responses..

---

### Post by SeijiSensei on 2013-01-28
I use CentOS for servers and have used sendmail for SMTP for years.  I usually wrap it with [MailScanner]("http://www.mailscanner.info/") to add virus and spam scanning.

---

