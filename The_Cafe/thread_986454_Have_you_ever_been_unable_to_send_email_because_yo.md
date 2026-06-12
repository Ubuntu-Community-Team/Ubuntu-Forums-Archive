---
title: "Have you ever been unable to send email because your server was blacklisted?"
date: 2008-11-18
forum: The Cafe
---

### Post by diablo75 on 2008-11-18
I use Lunarpages.com for my web hosting.  Today, it seemed like ever email I attempted to send would result in me recieving a failure of delivery notification in my inbox.  The message produced would say something like:

> SMTP error from remote mail server after RCPT TO: <recepient@theiraddress.com>: host theiraddress.com [host IP address}: 550-Message rejected because procyon.lunarpages.com [lunar IP address] is 550 blacklisted

They say they put in a request with Barracuda Central.org to have my IP address delisted, and say it could take up to 48 hours before I'm able to send email again!

Reasons they list for this possibly occuring are:

*Your email server contains a virus and has been sending out spam (I use Linux, and I don't send spam)
*Your email server may be misconfigured (confirmed by tech support to not be the problem)
*Your PC may be infected with a virus or botnet software program (I use Linux)
*You may be utilizing a dynamic IP address which was previously utilized by a known spammer (I suppose this is possible, but unlikely)
*Your marketing department may... (stop right there... I am my own marketing department)
*You may have an insecure wireless network (WPA-AES, don't think so)
*In some rare cases, your reciepient's Barracude Spam Firewall may be misconfigured (how could that my fault?)

Has this ever happened to anyone else out there?

---

### Post by psusi on 2008-11-18
> **diablo75 said:**
> 
*Your email server contains a virus and has been sending out spam (I use Linux, and I don't send spam)

It said your mail server, not you.  You need to contact whoever runs your mail server and tell them to fix it.

> **diablo75 said:**
> 
*Your email server may be misconfigured (confirmed by tech support to not be the problem)
*Your PC may be infected with a virus or botnet software program (I use Linux)
*You may be utilizing a dynamic IP address which was previously utilized by a known spammer (I suppose this is possible, but unlikely)

Ignore these since you aren't sending directly from your machine; you are using someone else's mail server.

> **diablo75 said:**
> *Your marketing department may... (stop right there... I am my own marketing department)

Again, referring to your mail provider, not you.

> **diablo75 said:**
> 
*You may have an insecure wireless network (WPA-AES, don't think so)

Again, ignore because you aren't sending the mail directly.

> **diablo75 said:**
> *In some rare cases, your reciepient's Barracude Spam Firewall may be misconfigured (how could that my fault?)

It wouldn't be your fault.  It is just saying that the mail server that bounced your message might have made a mistake rather than your mail server actually being blacklisted.

---

