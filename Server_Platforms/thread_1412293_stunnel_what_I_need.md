---
title: "stunnel what I need?"
date: 2010-02-21
forum: Server Platforms
---

### Post by bone2006 on 2010-02-21
I have a printer in the office that is connected to the network.  I need to use the scanning capability and have it email the newly scanned pdf file. 
The SMTP gateway only allows for IP addresses and doesn't allow SSL...etc  I'm currently using smtp.gmail.com for email service.

I'm not sure how to get around this, because I don't think I want to setup an email server, because if the box goes down or because of SPAM I prefer it being hosted elsewhere.

So the printer only allows me to enter an SMTP gateway IP address.  I don't know what to do, since my SMTP is out of the office.  I was thinking about setting up a server that does a few things and using stunnel?  I only need to send out emails with the files attached.

I would prefer it not even going out of the local network for security, but not sure what to do.

---

### Post by HermanAB on 2010-02-21
Google for nullmailer.

---

### Post by bone2006 on 2010-02-21
thank you for the reply.

I googled  tried to read as much as I could about nullmailer, but wasn't sure how it works or how to configure it or how it works.

I found the official website though
[http://www.untroubled.org/nullmailer/](http://www.untroubled.org/nullmailer/)

The printer would send information to this box, that nullmailer would then forward it to google's apps servers?  I can't find where I would enter things like smtp.gmail.com, port, TLS...etc

Unless nullmailer never leaves the local network.   The other computers are windows that receive emails on the network using outlook if that helps.

Any setups would be beyond appreciated

Thanks in advance

---

### Post by cariboo on 2010-02-21
There is a nullmailer tutorial [here]("http:///ubuntuforums.org/showthread.php?t=56077"), it's kind of old, but should work for you.

---

### Post by bone2006 on 2010-02-21
> **cariboo907 said:**
> There is a nullmailer tutorial [here]("http:///ubuntuforums.org/showthread.php?t=56077"), it's kind of old, but should work for you.

Is esmtp the same nullmailer?  Because the installation is talking about esmtp and I've seen instructions for actually 
sudo apt-get install nullmailer.

The title also says no forward, which I believe that tutorial is only for sending out an email when on that system.

I need the printer to send to that system to then be forwarded to my email host.

---

