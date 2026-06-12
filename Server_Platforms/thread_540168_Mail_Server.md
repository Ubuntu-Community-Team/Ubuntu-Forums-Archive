---
title: "Mail Server"
date: 2007-09-01
forum: Server Platforms
---

### Post by zzrjj on 2007-09-01
Hi, I'm trying to setup a mail server. what i want it to do is retrieve email from a capture all account at my ISP and distribute it to different aparments eg: sales, admin, tech. Some setup like mdaemon would be good what im currently using now but i want to get away from windows. I don't really want to point the mx records to the IP address as i have done it before and had alot of trouble with spam, going through the isp filters the spam.

If this can be done or if someone knows of a howto somewhere please let me know.

Thanks in advance

Joe

---

### Post by NewbieNik on 2007-09-01
1st problem is the catch-all address. It basically throws all addressed email into one ¨mailbox¨ making it virtually impossible to seperate out after without using search filters for subject and test bodies.
MX records to your IP is better as you can put in you&#341;e oen spam filter and ¨tweak¨ accordingly.

---

### Post by zzrjj on 2007-09-03
Thanks i will try that. Does anyone know of a good email server how to?

Thanks

---

### Post by HermanAB on 2007-09-04
You could use Citadel.  It is the easiest mail system to set up: [http://www.citadel.org](http://www.citadel.org)

Installing a Citadel server takes about 20 minutes - about an hour to add SpamAssassin and Clamav too.  With Citadel it is easy to set up various mailboxes (called rooms) and you can define special filters for each room.  You can access Citadel with a common mail client like Thunderbird and with a web browser (Firefox and Explorer both works).

A Citadel system is very efficient and hardly loads a server.

BTW, you don't need a Howto Guide for Citadel - just use 'Easy Install' and answer a few questions - clickety, clickety, long wait, done!

Cheers,

Herman

---

