---
title: "smtp-auth proxy"
date: 2007-03-15
forum: Server Platforms
---

### Post by amatten on 2007-03-15
Hi all, I'm building a spam/virus smtp filter (postfix, sa, amavisd-new, clamav, etc.) and am running into some problems with smtp-auth for roadwarriors.  I'd like to be able to re-use the system and have it be independant of the destination MTA.  It seems my options are:

a) Local databases for remote user smtp-auth
b) Webmail sending only
c) Change destination MTA smtp to port 26 and change roadwarriors smtp port (bypassing filter)

a) is too admin intensive for a plugin & forget utility.  b) doesn't meet my clients requirements.  c) seems like too much of a kludge to me, personally, and I question  the possibilty of spammers finding that port.  

I've briefly looked into smtpprox and spampd but couldn't find detailed integration instructions.  

I've dropped in Barracudas before and they have this great feature called 'smtp-auth proxy' where you just enter the IP of your destination MTA (that uses smtp-auth) and the barracuda checks there for sender smtp-auth.  Is there an easy way to get this kind of functionality with postfix?  Should I just dig deeper into smtpprox or spampd (I *think* they do what I want).

Thanks for any help.

---

### Post by Mr. C. on 2007-03-15
You'll get more responses, and better results if you post this on the postfix user's list.

MrC

---

