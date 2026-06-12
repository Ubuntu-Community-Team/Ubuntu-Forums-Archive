---
title: "Easiest way to send mail from Ubuntu 16.04?"
date: 2018-03-19
forum: Server Platforms
---

### Post by foomate on 2018-03-19
Hi,
I just created a Digital Ocean droplet. The issue is that, in my testing environment I was able to send test emails via my own GMAIL account (just for testing)
But now I installed LAMP stack on a VPS, and I want it to send a message showing somehting like "webmaster@hostname.com"

So far I do not have a domain name, only IP address.

the problem is that, only in the first time, I am able to send mail using the PHP Mail() function. But the sender is shown as "www-data@ubuntu.com", is in Gmail's spam folder, and afterwards I get no more emails..

I've spent entire day yesterday to make my mail script work (It's important for registration and password reset).

What is the easiest way to send mails assuming I am on a fresh installation of Ubuntu 16.04 server? Any help:(

---

### Post by TheFu on 2018-03-19
SMTP is a very simple protocol.  But, since spam email is a huge issue for the entire world, layers have been placed over it to make sending email harder for people trying to do it without any of the extra anti-spam features. Your server as it is today won't be able to successfully send email anywhere. It will be blocked.

To successfully send email, you **Must** setup VALID forward and reverse DNS for the server.  It needs a VALID MX DNS record and must have a static IP that isn't on any SMTP block lists. That is the minimal requirements.
To have more servers accept email from the server, you'll want to add SPF txt DNS records and perhaps DKIM signatures for every email.

If your email server every allows open-relay of email, it will be placed onto a block list. Getting removed will be non-trivial.  I got on 1 huge ISP block list and it took 5 yrs to be removed. The rest of the world never had any  issues with my server(s).  I tried for months to get removed and they ignored me.  There was never any misconfiguration - the initial cause was because a friend of mine using that ISP had send a virus to my server and I tried to let him know.

FROM addresses in email can be anything valid. There isn't any checking. Just set the SMTP header FROM to the value you want.

Email is a really simple.  It is getting around all the anti-spam stuff that makes it complex.  Most people shouldn't run their own email servers.

---

