---
title: "Mail log retrieval help"
date: 2009-04-02
forum: Server Platforms
---

### Post by tr33m4n on 2009-04-02
Hello there,

This is my situation: Basically I host a wordpress blog on my server with a contact form that submits data via php post to exim4, which in turn sends the info to my ISPs smtp server. I recently discovered that the contact form was not working correctly and when a client got in touch through it, no header information was sent to my email (senders name, email etc), only the message was sent.

I now have the problem of a paying client getting in touch, but having no means to respond!

I was wondering whether exim4 has a sent mail log (I realise it has a cued message log) that I could view... or could it be logged via php somewhere? or do I have to ask my ISP for the logs to the smtp server?

I realise this is not quite an ubuntu question... but I am running ubuntu, and you guys are generally pretty good at giving good answers :)

Many thanks
Dan

---

### Post by hyper_ch on 2009-04-03
/var/log/mail*.log

---

### Post by tr33m4n on 2009-04-03
Thanks for the reply, but I have already checked the usual mail log places (and mine appears to be empty... I think this is due to exim using its own logs... which I have checked)

Cheers
Dan

---

