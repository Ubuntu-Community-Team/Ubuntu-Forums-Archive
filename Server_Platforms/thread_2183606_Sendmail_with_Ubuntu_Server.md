---
title: "Sendmail with Ubuntu Server"
date: 2013-10-25
forum: Server Platforms
---

### Post by chrisguk on 2013-10-25
I am trying to create a mail routing solution for some services on my network.

Basically I have a program that sends reports emails  to an external client computer in a different city and on an unrelated network.   I believe I need to use sendmail and use it as a relay in order for this to work.  Do I need SMTP information for a route out before I can make this happen?

I dont want the work done for me here but just to point me in the right direction would help.

---

### Post by SeijiSensei on 2013-10-26
If you are asking about the original sendmail, and not a clone like Postfix, then you can handle routings using a "[mailertable]("http://www.sendmail.com/sm/open_source/docs/m4/mailertables.html")".  It ignores MX lookups and sends messages directly to specified servers based on host or domain names.

For instance, let's suppose you process mail for two subdomains in example.com, hr.example.com and mktg.example.com, both of which have local mail servers at 10.10.10.10 and 10.10.10.11 respectively.  Then in /etc/mail/mailertable you would have:

```

hr.example.com     relay:[10.10.10.10]
mktg.example.com   relay:[10.10.10.11]

```

(When using bare IP addresses for relaying they need to be enclosed in squared brackets.)

Mail addressed simply to "example.com" or to any other subdomain of example.com would still be handled locally.

---

### Post by TheFu on 2013-11-01
postfix with transport entries can solve this.
OTOH, if things are on your internal network, then just configure each end-node as a satellite and relay everything to your real-email server to be forwarded wherever it needs to go.  I've got 20+ servers setup this way here.  logwatch outputs daily emails on the system status. All those emails are forwarded (relayed) to my real email account on the main email server for easy filtering.  It will also send email to normal internet servers this way - provided those machines accept email from my server.  The MX is only needed if there is a question about the target email server to receive the emails. If you know it, the transport map will handle that for you.  If postfix is already installed, then **man transport** will explain.

---

