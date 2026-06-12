---
title: "email server error(?)"
date: 2006-01-29
forum: Server Platforms
---

### Post by Zelut on 2006-01-29
I'm running a webhost/email server (more recently added email) and I notice the following in my mail.log.  Can anyone tell me what this means & how I can fix it?  I'm assuming msn/hotmail isn't accepting connections from me.  Do I need SSL connections for my email as well?  Thanks..

Jan 29 20:16:35 whitebox postfix/smtp[6155]: connect to mx1.hotmail.com[65.54.245.8]: Connection timed out (port 25)
Jan 29 20:16:35 whitebox postfix/smtp[6156]: connect to mx2.hotmail.com[65.54.245.40]: Connection timed out (port 25)
Jan 29 20:17:05 whitebox postfix/smtp[6155]: connect to mx3.hotmail.com[64.4.50.179]: Connection timed out (port 25)
Jan 29 20:17:05 whitebox postfix/smtp[6156]: connect to mx4.hotmail.com[65.54.244.232]: Connection timed out (port 25)
Jan 29 20:17:35 whitebox postfix/smtp[6155]: connect to mx2.hotmail.com[65.54.245.40]: Connection timed out (port 25)
Jan 29 20:17:35 whitebox postfix/smtp[6156]: connect to mx3.hotmail.com[65.54.245.72]: Connection timed out (port 25)
Jan 29 20:18:05 whitebox postfix/smtp[6155]: connect to mx2.hotmail.com[65.54.190.50]: Connection timed out (port 25)
Jan 29 20:18:05 whitebox postfix/smtp[6156]: connect to mx2.hotmail.com[65.54.244.168]: Connection timed out (port 25)
Jan 29 20:18:35 whitebox postfix/smtp[6155]: connect to mx1.hotmail.com[65.54.244.136]: Connection timed out (port 25)
Jan 29 20:18:35 whitebox postfix/smtp[6156]: connect to mx1.hotmail.com[64.4.50.50]: Connection timed out (port 25)
Jan 29 20:19:05 whitebox postfix/smtp[6155]: connect to mx1.hotmail.com[64.4.50.50]: Connection timed out (port 25)
Jan 29 20:19:05 whitebox postfix/smtp[6156]: connect to mx1.hotmail.com[65.54.245.8]: Connection timed out (port 25)
Jan 29 20:19:35 whitebox postfix/smtp[6155]: connect to mx4.hotmail.com[65.54.244.104]: Connection timed out (port 25)
Jan 29 20:19:35 whitebox postfix/smtp[6156]: connect to mx3.hotmail.com[65.54.244.200]: Connection timed out (port 25)
Jan 29 20:20:05 whitebox postfix/smtp[6155]: connect to mx4.hotmail.com[65.54.245.104]: Connection timed out (port 25)
Jan 29 20:20:05 whitebox postfix/smtp[6156]: connect to mx4.hotmail.com[65.54.245.104]: Connection timed out (port 25)
Jan 29 20:20:35 whitebox postfix/smtp[6155]: connect to mx3.hotmail.com[65.54.244.72]: Connection timed out (port 25)

---

### Post by MJN on 2006-01-30
If you only had trouble with Hotmail then I'd suspect a problem at their end. Try a **telnet <ip address> 25** to each of the IPs above (don't use the domain name as you won't have control over which IP it's using) and see if you get a response (if you connect type **quit** to ..err... quit ;)). I've just tried it from here and some did indeed time out...

As for SSL, no, you won't need it to send mail to other MTAs (unless you want to relay via them, but you'd only want to do this with your ISPs server if at all).

Mathew

---

### Post by Zelut on 2006-01-30
Seems odd that all of those servers would time out.  I'll keep watching it & see if it changes.  If it continues to time out I would think it would be something on my end.

I also notice that anything sent to "cox.net" now says "[my ip] is blacklisted".  Any ideas on that?  Should I maybe use my ISP smtp for outgoing or.. I can't have this kind of unreliability on my email server.  Ugh!

---

### Post by MJN on 2006-01-30
> **kuyaedz]Seems odd that all of those servers would time out. I'll keep watching it & see if it changes. If it continues to time out I would think it would be something on my end.[/quote] 
Not beyond the realms of possibility that you'd time out to them all - many are on the same subnet and remember how busy Hotmail must be what with all those spammers..  said:**
> I also notice that anything sent to "cox.net" now says "[my ip] is blacklisted". Any ideas on that? Should I maybe use my ISP smtp for outgoing or.. I can't have this kind of unreliability on my email server. Ugh! 
Did it say *why* it's blacklisted? If you're on a dynamic IP you could well be listed on one of the dynamic-IP lists that many organisations utilise so, yes, your safest bet would probably be to use your ISP as a relay (I do for this very reason). Further on the dynamic IP issue, if the previous owner did anything naughty and got himself on one of the spammer lists then that could explain it. The error message ought to detail exactly what list you're on, and provide details of how to look up why you're on it (and what to do about it if it possible to be removed).

Mathew

---

### Post by Zelut on 2006-01-30
From what I'm reading it sounds like many big ISPs are now blocking port 25 in an attempt to cut down on spam.  This would explain the timed-out error or even the blacklisted errors.  It sounds like my best bet here is using "relayhost" thru postfix & relaying the email thru my ISP via my authentication.

Anyone have any experience doing this?  I'm trying it out now but not sure if its working yet.

---

### Post by Horndog on 2006-01-30
Has your mail server ever worked? If not then your ISP probably has port 25 blocked. It's common for Dynamic-residential connection. They don't wont insecure mail servers spewing out spam from being hacked.

---

