---
title: "Ubuntu Forums has been pwned! (with review)"
date: 2013-07-31
forum: Ubuntu, Linux and OS Chat
---

### Post by samiux on 2013-07-31
Congrats that the forum is resumed.

For those who do not know what has happened these days, I wrote [an article]("http://samiux.blogspot.com/2013/07/ubuntu-forums-has-been-pwned.html") for that.

Meanwhile, I have a quick and dirty review for the resume [here]("http://samiux.blogspot.com/2013/07/ubuntu-forums-has-been-pwned-part-2.html").

The review is just my opinion and you may not agree with me.  Anyway, comments are welcome.

Samiux

---

### Post by oldos2er on 2013-07-31
Not a support request, moved to Ubuntu, Linux & OS Chat.

---

### Post by cariboo on 2013-08-01
@samiux, I think you missed a few things in you analyses, We do know which account was compromised, and how the attacker got the admin password, the only thing we don't have is a copy of the script. As far as what we done to to protect the forum, We no longer store any password in the forum DB. We've removed all privileges from loco mod accounts, and there is now a script in place that removes any inactive moderators privileges at a set period of time. Php has been sanitized, and the hacks put in place by previous forum councils have been removed. It was one of these hacks the attacker exploited to gain access to the db. Canonical IS also found an exploitable bit of vBulletin code, and they worked with the vBulletin developers to close the hole. This fix has been added to the vBulletin code, so that other users of the forum software won't have a problem from that exploit.

We the current forum council have to take part of the responsibility for the hack, as we didn't check the privileges of all the loco mods, because in some cases, they had admin privileges. We also didn't check the hacks put in place to get something that we no longer need to work.

Much more was done, than what was posted in the blog, and what I want to go into here.

We are very thankful for all the hard work and long hours that Canonical IS put in to get the forum back up again.

---

### Post by samiux on 2013-08-02
> **cariboo907 said:**
> @samiux, I think you missed a few things in you analyses, We do know which account was compromised, and how the attacker got the admin password, the only thing we don't have is a copy of the script. As far as what we done to to protect the forum, We no longer store any password in the forum DB. We've removed all privileges from loco mod accounts, and there is now a script in place that removes any inactive moderators privileges at a set period of time. Php has been sanitized, and the hacks put in place by previous forum councils have been removed. It was one of these hacks the attacker exploited to gain access to the db. Canonical IS also found an exploitable bit of vBulletin code, and they worked with the vBulletin developers to close the hole. This fix has been added to the vBulletin code, so that other users of the forum software won't have a problem from that exploit.

We the current forum council have to take part of the responsibility for the hack, as we didn't check the privileges of all the loco mods, because in some cases, they had admin privileges. We also didn't check the hacks put in place to get something that we no longer need to work.

Much more was done, than what was posted in the blog, and what I want to go into here.

We are very thankful for all the hard work and long hours that Canonical IS put in to get the forum back up again.

Malicious attackers are very clever and very creative.  They can turn impossible to possible.  May be you do not agree with me.

"A" attacker will use "A" method to attack your (web) server.  "B" attacker will use "B" method to attack your (web) server.  "C" attacker will use "C" method to attack your (web) server and so on.  No attack method is same to all attackers.

You blocked "A" method but how about "B", "C" and "D" ….?  You may overlook or miss some areas when you are studying the source code of the (web) application.  How about the attacker gains access to your (web) server via the overlooked breakpoints?

If the attacker cannot get your database of your clients, the attacker can plant some malicious codes to your (web) server in order to do another evil things.  The malicious codes can be planted to somewhere of the web application.  Who knows!

Just my opinion.

Samiux

---

### Post by mastablasta on 2013-08-02
well there is no 100% security. all you can do is secure as best as you can and then hope noone can/will break in. 

also hard security and being at the same time easy to use, and connected to web and used by thousands every day is probably difficult.

---

