---
title: "Avoiding Spam filtering (sendmail)"
date: 2009-10-01
forum: Server Platforms
---

### Post by dugald on 2009-10-01
Hi All,

I have an Ubuntu web server hosted by a local company.  It has been running flawlessly for years now, and I am very happy with it.

The only difficulty I am having is the number of emails that aren't reaching customers.  We send out statement emails in bulk once a month, and new customers always seem to get them filtered as spam.  I have been reading up and one suggested cause was the server's name and sender's domain name do not match.  

My system host name is like mysitename.localhostingcompany.com and my emails are sent from [email]admin@mysitename.com[/email].  Is this normal?  Can I change the system host name or will that mess things up?

---

### Post by windependence on 2009-10-01
This is one thing I keep trying to tell people here on the board. Relaying or not having proper mail setup will get your mail canned in many cases.

Most important you need to have a reverse DNS set up with your registrar or ISP. The problem you are having is that your domain name does not match your mail headers. 

Why not change your hostname to match your domain? Also, make sure you get revers DNS set up. You do NOT have to run a DNS server to do this, but if you do, then all you need to do is set up a reverse zone.

-Tim

---

### Post by dugald on 2009-10-01
Cheers Tim, that answers my question - I will do some research on how to set up a reverse DNS - its not something I have done before.

Will changing my hostname have any side effects given that the current one was set by the hosting company I use?

---

### Post by dugald on 2009-10-02
For anoyone else interested in this, when I contacted the company that hosts my dedicated server they told me that I should not change my hostname as this would mess things up.

The reverse DNS setup is something that they sort out at their end, so all I had to do was tell them the domain that I wanted the rDNS to point to (mysite.com).

---

