---
title: "Mail from POSTFIX getting bounced."
date: 2009-04-27
forum: Server Platforms
---

### Post by michwill on 2009-04-27
Hi All,

I'm having some trouble out of a simple POSTFIX setup.  Basically some servers (e.g. GoDaddy) are bouncing all emails coming from my local mailserver.  However, others (e.g. BlueHost, Gmail) accept email just fine.  Keep in mind I'm not trying to relay mail -- I'm simply sending it from the local machine to clients/accounts on those servers.

I have no DNS,MX, etc.  This POSTFIX installation is simply a "dummy" mail server for eGroupware to use since I kept getting "Could not connect to SMTP server" errors from eGroupware when I used my remote accounts.

I realize that some servers might view it as a "SPAM" node and bounce, but I need to know what I can do (short of DNS/FQDN) that will allow GoDaddy, etc. to accept mail.

Best.

---

### Post by HermanAB on 2009-04-27
Howdy,

"I have no DNS,MX, etc."

Either fix your DNS or forward mail via your ISP mail server using the relayhost option in main.cf.

---

### Post by michwill on 2009-04-27
Drat you Herman!

*waves fist*

Why would most servers accept the email just fine?  Also, how do I go about getting an internal server "outside world approved" without assigning an external, static IP to it?  I don't really care for external visibility or any of that.  

<RANT>
I simply want a piece of digital information sent and accepted!!! Why is this more complex than necessary?!?!?!  I don't need a resolvable physical address to send a real letter (although they prefer it).  Why does the webbernet (a.k.a. interweb) require such?!?!
</RANT>


...as far as the relay, I was trying that, but Bluehost for some reason decides it's tired of relaying and will start denying logins -- then a few hours later, all is well.  The only reason I set POSIX up was because of this particular annoyance.  Any ideas either way?

---

### Post by HermanAB on 2009-04-28
You only have two options:  Relay mail through another working MTA, or configure your DNS properly.  Blame the spammers for causing some admins to configure their mail servers with reverse DNS checks.

---

### Post by lisati on 2009-04-28
You might want to check out setting up an account with a free DNS server account.

---

### Post by michwill on 2009-04-28
> **HermanAB said:**
> You only have two options:  Relay mail through another working MTA, or configure your DNS properly.  Blame the spammers for causing some admins to configure their mail servers with reverse DNS checks.

Well, for now, actually getting a resolvable DNS to an internal address is out.  Although I suppose we could route port 25, 443, etc. to the internal machine from the router.  Is there any way to host the MX records directly on the internal machine or are they required to be recognized/hosted by my ISP/Hosting company?

...anyway, now I'm getting a 553 error from my webhosting company when I attempt to relay from Postfix. It's saying:  ***"553 Sorry, that domain isn't in my list of allowed rcpthosts"***.

Thoughts?

---

