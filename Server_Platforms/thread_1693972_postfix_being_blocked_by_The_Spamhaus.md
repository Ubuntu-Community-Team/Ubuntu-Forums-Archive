---
title: "postfix being blocked by The Spamhaus"
date: 2011-02-23
forum: Server Platforms
---

### Post by DrReaper on 2011-02-23
Hi everyone,
I am setting up a LAMP server for my website and it's all working. I setup postfix and sent an email to myself which I didn't get. I checked the log on the lamp server and it said to check this error message

[PHP]
407/0.01/0.93/0, dsn=4.7.1, status=deferred (host  cdptpa-smtpin02.mail.rr.com[75.180.132.244] refused to talk to me: 554  5.7.1 - ERROR: Mail refused - <76.89.114.72> - See  http://www.spamhaus.org/query/bl?ip=76.89.114.72)
[/PHP]

I am getting stopped from getting an email from my server for some reason? Anyone have any advice?

---

### Post by SeijiSensei on 2011-02-24
Did you read the web page cited in the error message?  If not, this is the relevant part:  [http://www.spamhaus.org/pbl/query/PBL256364](http://www.spamhaus.org/pbl/query/PBL256364)

Running mail servers on residential connections is fraught with failure.  Many ISPs block outbound port 25; many anti-spam organizations list residential IP blocks in their black lists.  You may also be violating the terms of service in your ISP contract by running a server.

---

### Post by DrReaper on 2011-02-24
I have also been reading up on it. I am going to use my existing server for my email so I can get around this blocking garbage. I guess I understand why it's there but I hate it when my freedom is compromised by people doing stupid things.

---

### Post by SeijiSensei on 2011-02-24
It has nothing to do with "people doing stupid things."  It has to do with the economics of providing Internet services.  I pay a premium for a business-class Internet connection because the terms of service for residential connections don't meet my professional needs.  I also know my IP address won't end up on black lists of residential connections.

---

### Post by DrReaper on 2011-02-24
I am not going to be spamming the internet. I am going to be sending out an activation email if someone signs up to my blog. If i make any money I will upgrade to a business account. I don't want a business account BEFORE I am making money. Then only the ISP is making money. 

I need a way to get my server to send a simple activation email. I have a paid for email server. Is there a way to configure my LAMP server to send an email to a SMTP server and it can forward it to the end user?

---

### Post by James78 on 2011-02-25
There's multiple solutions for this.

For example,
You could use a professional or free service to relay through,
You could use your own ISP's email server, e.g. mail.charter.net (this is what I do),
You could buy a internet connection suited for this (best solution).

But as for using an email server and sending email directly from your machine using your residential connection will be met with failure. Email relay is the best choice without a new internet connection.
> **DrReaper said:**
> _I am not going to be spamming the internet. I  am going to be sending out an activation email if someone signs up to my  blog._ If i make any money I will upgrade to a business account. I don't  want a business account BEFORE I am making money. Then only the ISP is  making money. 

I need a way to get my server to send a simple activation email. I have a  paid for email server. Is there a way to configure my LAMP server to  send an email to a SMTP server and it can forward it to the end  user?
It has less to do with spamming and more with features residential users don't need. You're paying for a residential connection, and residential users don't need outbound 25. It only has the added benefit of blocking most virus spam directly by blocking port 25 (although that of course can easily be circumvented).

When you buy a basic "$59.99" a month residential connection, 99% of the people are residential people, and don't need a business class "$159.99" a month features. There's not enough demand for it, so no supply is needed to be given. You wouldn't see some online hosting service offering all the features of their professional "$299" a month service on the basic "$99.99" a month plan, just because it'd be nice.

Anyways, that being said, like I said above, there are a few alternatives. ;)

---

### Post by DrReaper on 2011-02-27
I got it working by setting up a wordpress plugin to SMTP through google.
The plugin is configure-SMTP
It was the only thing I can find that worked.

---

