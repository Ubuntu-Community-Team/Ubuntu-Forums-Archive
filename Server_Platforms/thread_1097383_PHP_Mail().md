---
title: "PHP Mail()"
date: 2009-03-15
forum: Server Platforms
---

### Post by jonwcode on 2009-03-15
So I'm working on a register form right now for my users can login to my site. So anyways, when I try and send out a activation email, my Ubuntu server isn't sending any emails out with the PHP function. I have PHP installed, and postfix install on my server right now. I'm using a DNS. I'm new to ubuntu, and I'm not to sure if I'm setting up everything right to do this. I tried reading the postfix setup guide but I'm kinda confused where I start... lol So what do I have to do to setup my postfix email server so that I can send out emails with the PHP mail()?

Host File:

-----------------------------------------------------------------

127.0.0.1	localhost

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

-----------------------------------------------------------------

If you need any other files just let me know.

---

### Post by askreet on 2009-03-17
Are you sitting on a residential cable line, such as Comcast?  A lot of companies don't let you send mail out by yourself.  They provide SMTP servers you can configure postfix to send to using the "relayhost = " parameter.

My comcast has to use authenticated SMTP, which I did a quick google to figure out how to configure postfix to log into the SMTP server before delivering my message.

Hope this helps.

---

