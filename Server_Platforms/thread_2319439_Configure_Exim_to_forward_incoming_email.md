---
title: "Configure Exim to forward incoming email"
date: 2016-04-04
forum: Server Platforms
---

### Post by swiftoid on 2016-04-04
Hi,

I've just set up a new VPS as a web-server running 15.10. The web-server side of things is easy peasy, email is a little harder. I have set up exim successfully to send emails from local processes (php etc.), but I've been unable to configure it to forward emails.

I have several domain names pointed at my server. I'm not interested in creating actual email accounts, but I would like to be able to create forwarders. So, say my server's hostname is example.com. I want to be able to forward [email]info@example.com[/email] -> [email]myinfo@gmail.com[/email], [email]me@mydomain.com[/email] -> [email]someperson@gmail.com[/email] etc.

Can anyone help me accomplish this? I need to know:

How to configure exim
How to set up a record on my DNS (third-party, not on same server) to point each domain to exim

Many thanks

Jamie

---

### Post by Graham_Willis on 2016-04-05
About exim configuration for forwarders - try this:

[http://serverfault.com/questions/10279/setting-up-exim-to-forward-mail](http://serverfault.com/questions/10279/setting-up-exim-to-forward-mail)

And as to DNS configuration - you just delete the old MX records and create the new one:

example.com. 3600 MX 10 example.com.

Be sure not to forget about the trailing periods. I assume that example.com already has assigned A record pointing it to the correct IP on that DNS server. It's possible that it will be also necessary to disable the option of using local mail server or something similar. The changes can take up to several hours to take effect.

---

