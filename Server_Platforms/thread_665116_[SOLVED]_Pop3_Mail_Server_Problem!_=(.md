---
title: "[SOLVED] Pop3 Mail Server Problem! =("
date: 2008-01-11
forum: Server Platforms
---

### Post by notaloafer on 2008-01-11
I searched around a bit and can't seem to find a answer to my question, so here's the spheal.

Today I called Comcast at 3AM and aparently they no longer allow their internet subscribers to use smtp.comcast.net as a open relay anymore. I can deal with that and I created a email account with comcast.net and relay all my emails with my domains through Comcast via authenication.

Here's the big problem: For some reason (it worked perfect before) my mail server cannot be connected to. I can send mail but I can't receive anything!

When I go to a remote computer and type in "telnet mail.notaloafer.com 110" I get the standard "Dovecot Ready+" prompt. However when I use DNSStuff.com and mxtoolbox.com it says that my mail servers time out and are unreachable. 

Did Comcast block port 110 inbound too? If so why can I telnet to it but not receive mail on it? Is there a way to use port 1100 instead for mail and have it work for whoever is sending me mail?

Thanks a ton guys... this is rather urgent (my users are getting pissed they can't get any mail)

-Eric

P.S- When I send a test email to my server nothing comes up in the logs at all... wouldn't this mean that the message is never getting to my server in the first place?

---

### Post by notaloafer on 2008-01-12
Bump anyone? This is rather really important that I fix.....

-Eric

---

### Post by freymann on 2008-01-12
> **notaloafer said:**
> 
Here's the big problem: For some reason (it worked perfect before) my mail server cannot be connected to. I can send mail but I can't receive anything!


 I think you've already answered your question.

 If your ISP is blocking port 25, they are most likely going to block 110 too, no?

 If you can't check your popmail account on your machine from the outside world, and you can no longer send out email from your machine, then I would say YES, they've blocked the ports.

 You can configure your MTA to relay outgoing mail through your ISP's SMTP server. Using some weird dynamic dns port mumbo jumbo you can redirect ports too, or even tell your system to use a different port and configure your mail client that way...

 My ISP blocks port 25 but I can use 26. Smoke and mirrors.

---

