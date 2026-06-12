---
title: "ubuntu and Windows Server email question..."
date: 2008-10-17
forum: Server Platforms
---

### Post by shiznitphoenix on 2008-10-17
Hi,

We currently have a windows 2003 server running exchange to handle our email.  We also have a ubuntu server running a couple of websites.  I need the ubuntu server to be able to send email messages (msg from the websites) but it is not necessary for it to receive.  How would one best go about getting this to work.  What software is the best/easiest?  How do we set it up considering we already have an email server running on our network (exchange)... Any thoughts would be a help.

---

### Post by HalPomeranz on 2008-10-17
You may find this document helpful:

[http://www.deer-run.com/~hal/sysadmin/sendmail.html](http://www.deer-run.com/~hal/sysadmin/sendmail.html)

I wrote it a while ago, so it includes information about older releases of Sendmail, but it does tell you how to get Sendmail 8.12 and later set up to send outgoing email from a Unix/Linux system.

---

### Post by lykwydchykyn on 2008-10-17
You could just install something like nullmailer or postfix and have it relay messages to your exchange server.  I assume this works, though I've not used exchange (we use groupwise here), but if exchange allows for relaying smtp it should be possible.

If that's working, php's mail function should work using the default php config.

---

### Post by shiznitphoenix on 2008-10-18
It looks like exchange can do relaying so hopefully that'll work...  I'll keep you posted. :)

---

