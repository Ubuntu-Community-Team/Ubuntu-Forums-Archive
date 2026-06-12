---
title: "Incoming mail problem from gmail (Postfix)"
date: 2024-03-21
forum: Server Platforms
---

### Post by zeero_k on 2024-03-21
I have been running my own personal email server since the late 1990&#8217;s. Currently using Ubuntu 22.04 with postfix/dovecot and using a static IP via VPN service (since I cannot get a static IP over my internet connection). I have had this particular static IP for about 4 years. Also use letsencrypt/certbot for SSL/TLS.

Sending outgoing mail became increasingly difficult over the last decade since my IP didn&#8217;t generate enough email to develop a positive reputation and the VPN provider blocked outgoing port 25 connections, but I&#8217;ve worked around that issue by relaying outgoing email through mailgun.org via Port 587. That works pretty well and it&#8217;s a free service for low email volumes.

The latest issue I am having is with incoming email. Gmail suddenly stopped delivering to my static IP sometime around 3/6/2024. When sending a test message to myself from gmail and monitoring /var/mail.log, nothing shows up. I first get a delayed delivery message in gmail, followed by a delivery failure notice a few days later with the message &#8220;The recipient server did not accept our requests to connect&#8221;
Meanwhile, I&#8217;m getting email just fine from other sources.

I&#8217;ve tried a few SMTP test tools, and getting mixed results.

Using this one results in &#8220;unable to connect&#8221; and nothing shows up in my postfix logs:
[https://mxtoolbox.com/diagnostic.aspx](https://mxtoolbox.com/diagnostic.aspx)

This one results a connection timeout error on port 25, although I do see a connection attempt in my postfix log. Also connecting on port 465 with SSL works successfully:
[https://smtpserver.com/smtptest](https://smtpserver.com/smtptest) 

This one connects successfully on port 25 with and without encryption:
[https://www.smtper.net/](https://www.smtper.net/) 

I initially accused my VPN provider of blocking incoming port 25 connections, but after doing some testing I see that some port 25 connections are coming though, just not from everywhere. Any ideas or work-arounds? Unfortunately mailgun doesn&#8217;t seem to be set up very well for relaying incoming mail.

---

### Post by TheFu on 2024-03-21
I followed the setup here: [https://theorangeone.net/posts/wireguard-haproxy-gateway/](https://theorangeone.net/posts/wireguard-haproxy-gateway/)

I haven't noticed any issues recently.

---

### Post by zeero_k on 2024-03-23
> **TheFu said:**
> I followed the setup here: [https://theorangeone.net/posts/wireguard-haproxy-gateway/](https://theorangeone.net/posts/wireguard-haproxy-gateway/)

I haven't noticed any issues recently.

Thanks, yeah I've been thinking of going the VPN via VPS route, so I'll check that out.

It turns out that my VPN provider implemented some screwy firewall settings right around the time that this issue started. They said they reverted the changes but the problem is still happening. I went ahead and purchased a super-cheap VPS from racknerd and installed postfix configured as a secondary MX on it, and the email is flowing again. Now that I have this VPS and second IP to play with, maybe I'll try setting up a VPN server on it, that seems to be cheaper than the VPN service anyway!

---

### Post by TheFu on 2024-03-23
> **zeero_k said:**
>   that seems to be cheaper than the VPN service anyway!

Probably not.  $4/month isn't cheaper than a $20/yr VPN AND if you go over the VPS monthly transfer limits, expect to pay. For email, that might not be a problem, but if you use the VPN for everything, those cheap VPS plans don't give away bandwidth - or at least mine doesn't.  The VPS I use didn't email SMTP by default. I had to request it and follow up 3 times.  I like that.  It means it is too much hassle for spammers to bother using.  So the server subnet for my VPS is unlikely to get on a spammer list.

Anyway, glad you found a solution, though I never used it without a VPN. It actually never crossed my mind.  OTOH, I use a VPN between my wifi network and my other home LANs. I don't trust wifi at all.  Wifi traffic is like bare internet traffic to me, until there's a full VPN.

---

