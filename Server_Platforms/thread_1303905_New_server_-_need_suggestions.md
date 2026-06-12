---
title: "New server - need suggestions"
date: 2009-10-28
forum: Server Platforms
---

### Post by elvinatom on 2009-10-28
I run a (8.04 I believe) Ubuntu web- and mail-server right now.  Since my domain/IP is banned by barracuda and several other blocking services for spamming I decided to redo that box.  Here is the thing, I'm obviously a nooby, I don't know much about Linux, specifically about postfix and friends.  I need some kind of guide that works and is secure enough to not get infiltrated by spammers and hackers like my current one did.  Any suggestions or pointers would be greatly appreciated.

---

### Post by elvinatom on 2009-10-29
Never mind that last post, I checked my logs up and down and there seems to be no spamming going on after all.  Having said that, I'm going to leave that server alone for now.  Only thing I am concerned about now is why I do get blacklisted as a spammer.  Any idea how to go about it?

---

### Post by JordanCook on 2009-10-29
If you are using a Dynamic Ip Address Most commercial mail servers will block Mail From Servers on them.

---

### Post by volkswagner on 2009-10-29
> **JordanCook said:**
> If you are using a Dynamic Ip Address Most commercial mail servers will block Mail From Servers on them.

Absolutely true, and your most likely cause.  If your ISP allows, your can use their SMTP server as a relay.

---

### Post by elvinatom on 2009-10-30
Thank you for your replies.  I do use a static IP though and have a name registered to it, so I am a bit at a loss here.  I now frequently check my mail.log for suspicious entries - it all seems very legitimate.

A little background though: I was indeed spamming about a year ago - my logs look very different then: there was no unoccupied second to be found in them.  I then redid the server, used encryption, removed unneeded user accounts and set new passwords for the remaining user.

I still got blacklisted though.  I sent a request to barracuda to have my IP removed from their blacklist and they replied that they have done so, but would keep monitoring and reblock me if necessary.  And that is what happened about a week later.  My wife told me a few days ago that she tried to send a mail and it would just bounce back every time - another filter blocked me then (it worked fine a week earlier), which I had to request to get unblock.

It's all very confusing to me ...

---

