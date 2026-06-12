---
title: "Browsing log based on user id"
date: 2008-09-05
forum: Security
---

### Post by fallnomega on 2008-09-05
Hey guys and gals,

Unless I am completely missing it in the description fields, I have been unable to locate a security application for the project I have taken up. In otherwords I am turning to the forums for help.

What I am trying to accomplish is the following - 

I work for a ISP that requires our phone support techs to attempt replication of browsing/authentication/etc issues on test machines located throughout the office. There about 10 - 15 of them spread out in a large building, and most are running XP with a dab if Vista here & there. The issue that has arisen with them is that they are also used for browsing during down times which has led to some feeling that what should STAY at home is perfectly fine to check out on work machines. Yep, porn and what not. This has lead to reimaging them about once a week and I am fed up with it.

So now I am hunting for something that will log surfing history based on a an NT username and log it on the server they authenticate through. I thought about a keylogger but then again that will only give key strokes and as of rightnow the machines dont require a login to use. I was thinking maybe Samba Auth Gateway for autheticating on the test machines but I am lost on whether or not it can generate log files of the users surfing history. Is this possible with Samba ? I ask incase I overlooked the paragraph on it under the FAQ for Samba or there is something else that can do it.

Any assistance would be appreciated. I havent decided on whether I am going to run with Ubuntu server 7.10 or 8.04 so the door is open for those.

---

### Post by rogeriopvl on 2008-09-06
Why not instead of finding out their surfing habbits, block the access to those sites with a proxy? And with a proxy you can also log all HTTP traffic (I' not sure, if the username gets logged also).

---

