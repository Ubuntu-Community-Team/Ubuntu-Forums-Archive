---
title: "Mail Server (PosftFix + DoveCot + MySQL) email delivery error"
date: 2014-04-14
forum: Server Platforms
---

### Post by Muhammad_Raheel on 2014-04-14
Hi dear all,

I'm not an Ubuntu professional user. I'm configuring a mail server and I followed this article [https://workaround.org/ispmail/wheezy/installing-packages](https://workaround.org/ispmail/wheezy/installing-packages) to setup mail server. First I tried on local and it works perfectly but when I setup Windows Azure virtual Ubuntu server machine then it gives following error:

**Error when sending email from shell:**
[http://pastebin.com/kg4HYy6w](http://pastebin.com/kg4HYy6w)

[B]Postfix main.cf:
[/B][http://pastebin.com/Rs0awU7q](http://pastebin.com/Rs0awU7q)

I guess problem related with defining hostname. I've a domain but I don't know how to map domain with this mail server and then add hostname for whole server and for postfix configuration.

Please advise me.

Thanks

---

### Post by sharkey77 on 2014-04-14
Can you send directly from telnet?

If so make sure you checked "server requires authentication" in your email client.

Here's the page in the guide you followed on how to test telnet.  Make sure to telnet from the machine you are trying to send from, not the localhost.  If you can't telnet externally then try from localhost.

[https://workaround.org/ispmail/wheezy/authenticated-smtp](https://workaround.org/ispmail/wheezy/authenticated-smtp)

---

### Post by Muhammad_Raheel on 2014-04-14
Thanks Sharkey for your quick response. I will try and share results with you.

---

