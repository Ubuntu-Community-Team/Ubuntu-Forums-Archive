---
title: "Domain and email server"
date: 2019-05-24
forum: Server Platforms
---

### Post by wantedstarling on 2019-05-24
Hello, I have been trying for the past weeks to set up a mail server using Zimbra on Ubuntu 14.04. I successfully managed to build it, installed Zimbra and have valid MX records but the problem now is that the server is local and cannot receive emails from external accounts like hotmail and gmail. I tried to send a mail from my main Hotmail account to my server but I get response that no DNS records found for this recipient. I have been reading how to make my server public in some way so it can be seen by the DNS servers. I found out that it is difficult, so I rented a domain from Bluehost. So, my question now is how can I use the domain I rented to point on my server and DNS servers see my server so I can accept incoming emails.

The way I have currently set up my DNS is with dnsmasq but I dont think dnsmasq has the capability of making a server known to the internet. Any suggestions how can I do this?

Thank you for your time

---

### Post by TheFu on 2019-05-24
Ubuntu 14.04 standard support has ended.  [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)  If you don't have a paid contract with Canonical, then 14.04 shouldn't be used.  There are already some kernel bugs known which are important for system security.

Zimbra is supported on 16.04 only now with 18.04 still in the works.  There are many changes in going from 14.04 to 16.04. I started with a fresh Zimbra install on 16.04 and migrated over all the data a few months ago, before 14.04 support ended.  Tried to do a migration and it failed.  Keeping Zimbra current has always been a hassle.  Seems the new releases haven't changed that at all.

dnsMasq is a local DNS server on your LAN. That isn't useful to anyone else.

You need a registered domain, $3-$10/yr.

You need a public DNS server, that can be free or $20/yr.  Just depends on how much time you are willing to waste with the free providers.

You need to make the DNS updates to point to your public, static, IP for mail.{your-domain-here}.{TLD}.  You'll need "A" record, probably want a CNAME, MX and a few TXT records for SPF and DMARC so you are part of the anti-spam solution.  

If I can't lookup your domain from anywhere in the world, then you don't have the domain and DNS setup on public servers.  If you don't have MX record(s), then nobody will *attempt* to email your server.  If your server doesn't have SPF  TXT DNS records, then many other email servers will mark it as spam or reject it completely.  The good news is that because these are all DNS, they are all public so there are millions of proper examples.

If you public IP isn't static and non-residential, nobody will accept email from your server either.  When you get a static IP, check it in the spammer DBs you can find.  If it is listed, ask the ISP/hosting provider for another IP.  It can be difficult to impossible to get a blocked IP off the spamming list.  The IP/DNS lookup should match in both directions to have better luck staying out of spam.  That means that DNS lookups by name and by IP should answer with the opposite of the other, not some funky 12-34-56-78-static.host.domain.net response.  Setting up this reverse DNS is something your internet provider should do for free.

Might I suggest that you NOT allow direct access to your Zimbra server from the internet even if it is fully patched and properly maintained.  Zimbra is a beast with thousands of settings.  It is easy to get a few wrong which would compromise security.  The better security architecture is to use an email gateway. It is tiny, 1 vCPU, 512MB of RAM and very little disk storage.  Have all inbound and outbound emails go through this gateway going to/from the Zimbra server.  The Zimbra server should only accept email from this external gateway and other systems you maintain.  The gateway will block 98% of inbound spam and keep the attacks going to a postfix server that is constantly updated.  A simple gateway would be [http://www.scrolloutf1.com/](http://www.scrolloutf1.com/) . I've been using it for a very long time.  Just be certain to block the configuration web-app from everyone except localhost and always use an ssh-tunnel to access it.  If that webapp is available for even a few minutes, the machine will be pwn'd.  If this ssh stuff isn't clear, learn it BEFORE you do email.  Being intermediate at ssh stuff is required, IMHO.

Running and email server is thankless and takes time to get comfortable.  I started in the mid-90s out of necessity at a job and have been doing it for small businesses and my personal needs since then.  SMTP is really simple, but all the extra stuff that has been added on to slow down spammers has made it more complex and dangerous.  DNS, email and web servers are the most likely services to be attacked.  I've been hacked via DNS.  I see thousands of hacking attempts against my email gateway every day and even more attacks against my different web services.  Server monitoring and alarming are very important if you put a server on the internet.  

After you've been hacked, you'll be thankful to have daily, automatic, versioned, backups.  Just be certain the hacked client machine has ZERO access to the backups.

And don't forget, this stuff is supposed to be fun!

---

### Post by wildmanne39 on 2019-05-24
*Thread moved to **Server Platforms a more appropriate sub-forum**.*

---

### Post by wantedstarling on 2019-05-26
> **TheFu said:**
> Ubuntu 14.04 standard support has ended.  [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)  If you don't have a paid contract with Canonical, then 14.04 shouldn't be used.  There are already some kernel bugs known which are important for system security.

Zimbra is supported on 16.04 only now with 18.04 still in the works.  There are many changes in going from 14.04 to 16.04. I started with a fresh Zimbra install on 16.04 and migrated over all the data a few months ago, before 14.04 support ended.  Tried to do a migration and it failed.  Keeping Zimbra current has always been a hassle.  Seems the new releases haven't changed that at all.

dnsMasq is a local DNS server on your LAN. That isn't useful to anyone else.

You need a registered domain, $3-$10/yr.

You need a public DNS server, that can be free or $20/yr.  Just depends on how much time you are willing to waste with the free providers.

You need to make the DNS updates to point to your public, static, IP for mail.{your-domain-here}.{TLD}.  You'll need "A" record, probably want a CNAME, MX and a few TXT records for SPF and DMARC so you are part of the anti-spam solution.  

If I can't lookup your domain from anywhere in the world, then you don't have the domain and DNS setup on public servers.  If you don't have MX record(s), then nobody will *attempt* to email your server.  If your server doesn't have SPF  TXT DNS records, then many other email servers will mark it as spam or reject it completely.  The good news is that because these are all DNS, they are all public so there are millions of proper examples.

If you public IP isn't static and non-residential, nobody will accept email from your server either.  When you get a static IP, check it in the spammer DBs you can find.  If it is listed, ask the ISP/hosting provider for another IP.  It can be difficult to impossible to get a blocked IP off the spamming list.  The IP/DNS lookup should match in both directions to have better luck staying out of spam.  That means that DNS lookups by name and by IP should answer with the opposite of the other, not some funky 12-34-56-78-static.host.domain.net response.  Setting up this reverse DNS is something your internet provider should do for free.

Might I suggest that you NOT allow direct access to your Zimbra server from the internet even if it is fully patched and properly maintained.  Zimbra is a beast with thousands of settings.  It is easy to get a few wrong which would compromise security.  The better security architecture is to use an email gateway. It is tiny, 1 vCPU, 512MB of RAM and very little disk storage.  Have all inbound and outbound emails go through this gateway going to/from the Zimbra server.  The Zimbra server should only accept email from this external gateway and other systems you maintain.  The gateway will block 98% of inbound spam and keep the attacks going to a postfix server that is constantly updated.  A simple gateway would be [http://www.scrolloutf1.com/](http://www.scrolloutf1.com/) . I've been using it for a very long time.  Just be certain to block the configuration web-app from everyone except localhost and always use an ssh-tunnel to access it.  If that webapp is available for even a few minutes, the machine will be pwn'd.  If this ssh stuff isn't clear, learn it BEFORE you do email.  Being intermediate at ssh stuff is required, IMHO.

Running and email server is thankless and takes time to get comfortable.  I started in the mid-90s out of necessity at a job and have been doing it for small businesses and my personal needs since then.  SMTP is really simple, but all the extra stuff that has been added on to slow down spammers has made it more complex and dangerous.  DNS, email and web servers are the most likely services to be attacked.  I've been hacked via DNS.  I see thousands of hacking attempts against my email gateway every day and even more attacks against my different web services.  Server monitoring and alarming are very important if you put a server on the internet.  

After you've been hacked, you'll be thankful to have daily, automatic, versioned, backups.  Just be certain the hacked client machine has ZERO access to the backups.

And don't forget, this stuff is supposed to be fun!

I rented a domain from Bluehost and have created A, MX and TXT records but I am not sure if they are valid. If I do a lookup on dnsstuff I get that MX are not correct:

[IMG]http://i68.tinypic.com/kcknxc.jpg[/IMG]

But dig shows valid records:
[IMG]http://i65.tinypic.com/25u45s2.jpg[/IMG]

And A records:
[IMG]http://i64.tinypic.com/104n2n9.jpg[/IMG]

[IMG]http://i63.tinypic.com/2ecdd0n.jpg[/IMG]

I use the two DNS address that Bluehost has.

Now I have Zimbra installed without MX record. About that email gateway you said, how do you use it? If its only for security then I wont bother using it because I am not going to use the server for long, I will just send an email to my teacher to see that I built the server, send me an answer, give me the grade for the project and then I will shut it down because It's a lot of hassle to maintain it and I dont have the knowledge too. But anyway, I read on the internet that a CNAME is not required for a mail server because A points to the IP of the instead of CNAME which points to another name, correct me if I am wrong.

---

### Post by SeijiSensei on 2019-05-26
Never use CNAMEs for the hosts in MX or NS records.  The hosts referenced there need A records.

---

