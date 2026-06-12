---
title: "What is the minimum I need to do to get my server to send emails"
date: 2007-03-22
forum: Server Platforms
---

### Post by d.j.schroeder on 2007-03-22
I have a Drupal based forum running on my machine.  So far I have not been sending emails to authenticate users I just let them create a user ID and a password, but I really think I should do something more.  From what I have read on Drupal's forum, it assumes a working STMP server on the host to be able to send email.  That makes sense I guess, but I don't have one.

I don't need a "real" mail server.  I don't even want the thing to be able to receive mail.  I just want it to be able to send an email to someone who requests a user ID to validate that they have a real email.  I know absolutely nothing about this.  What is the minimum set of packages that I need to install in order to do this?

Also, if I only want to send emails out do I even need to open port 25 on my firewall?

---

### Post by deuce868 on 2007-03-22
What I do on my test systems that I don't need a full server is to run esmtp.

[http://esmtp.sourceforge.net/](http://esmtp.sourceforge.net/)

You need somewhere you're allowed to send mail through to setup as a relay and all of your email then gets sent to that relay host.

---

### Post by d.j.schroeder on 2007-03-22
Why can't I send mail from my machine directly?

Sorry if that's a stupid question I don't know a thing about email.

---

### Post by markusfarkus on 2007-03-22
You can send mail directly from your machine.  I don't think it is the easiest thing in the world, but I use this program to send backup emails.

sudo apt-get install mailx

You can configure it for a local workstation.  It will work great to send mail out.  You asked what the minimum was and I would say this is pretty close to that :)

---

### Post by Mr. C. on 2007-03-22
d.j.schroeder,

There are two mechanisms used by most web apps to send email: the sendmail program or SMTP.

The sendmail program is available either with postfix or Sendmail.  It handles ensuring that mail is prepared to be sent via SMTP.

Some web apps can talk SMTP, and so are able to connect to a remote server for relay or delivery. 

There are problems to be aware of:

1) Many ISPs and alike reject email sent directly from systems with dynamic IP addresses or improperly configured DNS'.  It is expected that your ISP's mail servers are to be used.  

2) many ISPs (perhaps yours) block outbound port 25, which prevents you from sending email directly from your systems, forcing you to use theirs.  You will have to discover if this is the case.

3) You will find that enabling your web apps to send email directly, without any anti-spam or abuse controls, will result a fair amount of email registrations being sent to innocent people whose email addresses have been usurped for weblog or forum spamming.

You do not need inbound port 25 open on your firewall, because you will not be an MSA (mail submission agent) and will have no MX listed in DNS.  Rather, you simply want to be an MTA for your own server.

A simple postfix installation will handle either SMTP or sendmail nicely.

MrC

---

### Post by Cheese Sandwich on 2007-05-19
Can you change your outgoing mail port to get around ISP port 25 blockage?

---

### Post by Mr. C. on 2007-05-19
I think you're misunderstanding.  Your MUA or MTA connect to another server via *destination* port 25.  If your ISP is blocking destination port 25, you cannot get around that.

MrC

---

### Post by tturrisi on 2007-05-20
3 ways to go about it easily:
1. use an automated php signup script that generates login info and sends it to the person after they submit their info.
2. manually send them an email using your mail client.
3. configure your MTA to act as a smarthost (uses your isp smtp server).
I prefer exim over other mta's:
[http://newbiedoc.sourceforge.net/networking/exim.html](http://newbiedoc.sourceforge.net/networking/exim.html)

---

