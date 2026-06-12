---
title: "Local E-Mail Setup"
date: 2009-04-25
forum: Server Platforms
---

### Post by wayne on 2009-04-25
I need some help!

What I'm trying to accomplish is receiving e-mail notification to watch for errors (like cron logs) & security issues.  I don't need to send e-mail to local users or outside the network.

My question is what e-mail service do I use?  I know postfix is the default MTA, will that work and do I need anything else?  One finale question, is it possible to send or have the e-mail forwarded to a outside address like gmail without setting up a MDA service?

I have a Ubuntu 8.04 LTS file server ONLY on a 192.168.44.0 private network.  I'm using a Comcast business account for the ISP.

Any suggestions or a direction to head would be appreciated.

Thanks in advance.

---

### Post by HermanAB on 2009-04-25
Yup, use nullmailer.  It has only two things to configure: Who you are and where you want the mail sent to.  There is nothing simpler than that.

---

