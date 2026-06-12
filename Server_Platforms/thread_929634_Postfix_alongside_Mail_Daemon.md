---
title: "Postfix alongside Mail Daemon"
date: 2008-09-25
forum: Server Platforms
---

### Post by HornedBeast on 2008-09-25
My Scenario


I have a Windows Server 2003 running MDaemon which collects mail from my ISP's POP server. We also send mail out from Outlook Clients connected to MDaemon, sending the mail from our ISP's Mail Server. The accounts are setup in MDaemon as such "your.name@mydomain.com"

However, our ISP doesn't allow bulk emailing through its own mail server, so they advised us to setup our own.

So, I have installed a little Ubuntu 8.04 Server which is now running Postfix. I wish to send mail from this server from an account name on MDaemon, such as "my.email@rawgarden.co.uk". However, when I try and send an email to myself from this mailserver, it never arrives. When I then send a mail to a Gmail account, however, it arrives fine.

Is there anyway to have Postfix setup to basically mimic MDaemons accounts, or is there something I need to do in MDaemon to allow mail sent from a different mail server to be allowed through?

I ask this because I wish to mass mail out customers, but I'm unsure how many of them will get the email with this occurring.


Any help regarding this, or just general postfix setup, would be appreciated.

Thank-you kindly!

---

### Post by HermanAB on 2008-09-25
You need to get a server account with your ISP, a couple of fixed IP addresses, a domain name and an easy to configure mail server.  I suggest using Citadel [http://www.citadel.com](http://www.citadel.com) since running the easy install script takes only about 20 minutes.

You can use Postfix with Apache, Dovecot, Roundcube, SpamAssassin and ClamAV, but setting that lot up the first time will take a couple of weeks, therefore Citadel is a much better idea than building a mail server from a Lego kit.

Cheers,

H.

---

### Post by HornedBeast on 2008-09-25
Server Account with my ISP? Whats that!?

We have a fixed IP here already in the office. But our domains points to a seperate server somewhere else for our web hosting. God knows how our ISP has its mail setup basically.

I only need to be able to send mail from a PHP script basically, from our domain.

Any other ideas?

---

