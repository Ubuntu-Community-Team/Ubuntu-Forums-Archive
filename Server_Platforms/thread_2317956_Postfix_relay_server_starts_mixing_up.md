---
title: "Postfix relay server starts mixing up"
date: 2016-03-21
forum: Server Platforms
---

### Post by Lyute on 2016-03-21
Hi there,

First of all, sorry if I posted this in the wrong section; this will be my first post in this forum. Please let me know if I'm doing something incorrectly.

We are running Ubuntu Server 14.04.4 in a virtual environment with postfix installed and everything updated with apt-get dist-upgrade.
What we are trying to do is to send out a newsletter to multiple users with phpmailer.
We first sent a couple (maybe 100 or so) emails and were successful. However when trying to send out around 3000 emails we started to see that some emails are not being sent correctly.
When we looked at the logs, it would have the correct To address, but the relay server is the server of another completely different user.

ie. members postfix/smtp [26436]: ###...: to=<someone@gmail.com>, relay=someoneelse-com.mail.protection.outlook.com[ipaddress]:25, ...

The first half of the emails are OK. The error starts kicking in after that but randomly; most of them have the correct relay server info but some don't.
Is this because that we've pushed too much in queue?
If someone can give me an insight on where to look, that will be great.
Thank you,

---

### Post by Seb_Boffen on 2016-03-28
These are the google limitations: [https://support.google.com/a/answer/166852?hl=en](https://support.google.com/a/answer/166852?hl=en)

---

