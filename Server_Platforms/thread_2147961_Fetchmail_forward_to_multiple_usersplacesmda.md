---
title: "Fetchmail forward to multiple users/places/mda"
date: 2013-05-23
forum: Server Platforms
---

### Post by ooglyboogly on 2013-05-23
I have my fetchmailrc configured perfectly right now to pass my mail on to request-tracker (a help desk ticketing system) after a poll every 2 minutes from my GoDaddy account. The problem is that I want to also send an SMS message to the IT staff upon receiving the email. So, first off, is there a way to send mail to multiple users/places when polling?

Right now: poll imap.secureserver.net username "bigdaddy@godaddymail.com" password "password" mda "/usr/bin/rt-mailgate --queue general --action correspond --url http://localfixed.url" keep ;

So, is there a way to add a second mda?

Also, is there a way to strip any info from the mail when polled, such as strip everything but the sender and get rid of subj and message?

Thanks, Oogly

---

