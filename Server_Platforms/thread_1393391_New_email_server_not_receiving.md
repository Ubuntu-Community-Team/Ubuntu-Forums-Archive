---
title: "New email server not receiving"
date: 2010-01-29
forum: Server Platforms
---

### Post by Tube Shark on 2010-01-29
I am setting up a new email server by following the Flurdy guide.  I can send but I can't receive.  I can telnet in with both the IP address & telnet mail.domain.com 25  I'm not using or loading shorewall because I will be relying on the firewall that is in the router.  I have been following the test section of the flurdy tutorial.  I am tailing the mail.log file and only see the status as being different from the example

"status=bounced (mail for domain.com loops back to myself)"

It seems like it is getting through to the server but then getting rejected. 

I'm running out of reading information to try Any help would be great!

Thanks

---

### Post by flurdy on 2010-02-01
> **Tube Shark said:**
> I am setting up a new email server by following the Flurdy guide.  I can send but I can't receive.  I can telnet in with both the IP address & telnet mail.domain.com 25  I'm not using or loading shorewall because I will be relying on the firewall that is in the router.  I have been following the test section of the flurdy tutorial.  I am tailing the mail.log file and only see the status as being different from the example

"status=bounced (mail for domain.com loops back to myself)"

It seems like it is getting through to the server but then getting rejected. 

I'm running out of reading information to try Any help would be great!

Thanks

Sounds like your server tryes to forward an email for domain.com onwards, but then realises domain.com's mx is the same as your server. Ie your server is not configured to receive emails for domain.com in "virtual_mailbox_domains".

---

### Post by Tube Shark on 2010-02-03
I tried from a xchange and got #554  5.7.1 <mail@domain.com>: relay access denied##

I reloaded everything from scratch and I have ended up with the same errors.  

When loading the mysql tables I got 0 lines added each time with some small amount of time to process. Is that right?  If not I am cutting and pasting out of tutorial and have tried hand loading but I get errors.  Could this be my issue?

---

