---
title: "[SOLVED] How can I set up a MTA for PHP scripts?"
date: 2008-01-22
forum: Server Platforms
---

### Post by pofigster on 2008-01-22
I've seen the how-to's on setting up a PostFix mail server - I've never been able to figure them out.  I can install all the software, but I don't know how to configure it properly.  Here's my situation, maybe somebody can help me.

I purchase my domain names through GoDaddy.com - for this situation, the domain is stat221.org.  I host the site on a computer I have at home which runs Ubuntu 7.10 Desktop using Blackbox as the DE.  It's a LAMP server - everything is current.

What I want to do is write a PHP script which sends an e-mail to a supplied e-mail address (and they will be many and varied).  To do this, I know I need either a mail server or an MTA installed to make it work.

So, what I'm wondering is, do I need a full scale mail server or just the MTA?  Regardless of this, what DNS entries do I need to modify and how do I need to modify them to get the system to work properly?  I know this is basically asking for a how-to but, I haven't yet found very clear instructions on all the details of setting up this kind of a service.

GoDaddy does provide an SMTP service - if there's some way to just send the mail through that SMTP service, that would be fine, too.

Thanks!

---

### Post by crouton on 2008-01-22
I doubt you would need to use GoDaddy's SMTP servers as you are hosting the site on your home computer.  You'd be better off using your ISP's servers, either by having something like Postfix using the ISP as the smarthost or by using PHP scripts that send the mail through the ISP directly.

---

### Post by MJN on 2008-01-22
Try nullmailer as suggested recently in [this thread](http://ubuntuforums.org/showthread.php?t=667649). Sounds good.

Mathew

---

