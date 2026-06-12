---
title: "Mail for a moron"
date: 2016-04-15
forum: Server Platforms
---

### Post by matthewboh on 2016-04-15
All I want to do is to be able to send out mail from my Ubuntu server. I have followed the Postfix documentation, read the Dovecote documentation and banged my head against a wall repeatedly.

I just want mail to be sent out and forwarded. For example, I want to use mail() in a php script to send out mail. I have a hosting company. Do I forward the mail to my hosting company? Is there a mail for dummies? I just feel like I'm diving into an ocean when all I need is a sip of waater.

Thanks all

---

### Post by Habitual on 2016-04-15
Have you asked your hosting company?
How does [http://www.imparisystems.com](http://www.imparisystems.com) usually do it?

---

### Post by matthewboh on 2016-04-15
Not sure what you're asking. I have my hosting company taking care of the email servers. Iknow how to set up my laptop at home to send email out to the imparisystems.com server and how to pull it back.

I'm stuck with how to do it on the Ubuntu server that's in my office. I just want it to send my mail to the imparisystems.com email server at the hosting company and  not really even concerned with pulling anything back. Do I use sendmail, Postfix? Is there a default I use? Is it called Satellite only or is it Internet mail?

---

### Post by Graham_Willis on 2016-04-16
Why do you want to do it? What type of Ubuntu server do you have in your office? Does it have a static IP address assigned to it and a domain delegated to it? Is this server visible from the Internet or is it just for internal use? Is this server at your home? It sounds a bit strange what you said that you want to have your e-mail sent out and forwarded. Where should it be sent and by what and where should it be forwarded? And why? Seems a bit like you want to send mass mailing by a forwarder which would forward all messages incoming to it to a list of predefined addressed. But then you don't need to have a mail server at your office at all, you can do it just by sending (in the usual way) an e-mail to this forwarder.

You can set up a SMTP server with Postfix, Exim or Sendmail (the last one is nowadays less popular due to the security issues), but if you're on a residential connection it is possible that running a mail service is not compliant with the agreement that you have with your ISP. If somebody breaks into your server and sends spam, then your IP address will (most likely) get blacklisted. If you configure your mail server as an open relay then you will turn it into a tool ready for be exploited by spammers world-wide. In other words, managing a mail server can be a bit complicated...

---

### Post by matthewboh on 2016-04-17
It's my home server and it's Ubuntu 14.04 LTS. It does not have a static IP address assigned to it but I do have a domain associated it with DynDNS. The server only has port 22 open to the Internet.

I'm doing some development and testing for local non-profits, and I want to test some of the capabilities available in CiviCRM. I don't want to create an open relay. I don't know which one to use between Postfix, Exim and Sendmail. I don't want to send a mass mailing by a forwarder.

Hope this gives you enough information - can you assist?

---

### Post by mastablasta on 2016-04-18
try this: [https://wiki.debian.org/sSMTP](https://wiki.debian.org/sSMTP)

you can use gmail account to forward the message. just make sure you (i mean your server) do not spam.

---

