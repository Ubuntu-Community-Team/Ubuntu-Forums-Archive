---
title: "Mail server to replace exchange"
date: 2008-02-21
forum: Server Platforms
---

### Post by jcampbell on 2008-02-21
Hi There,

Sorry if a similar post has been made before.  I had a look through the search but couldn't see anything that I hadn't already seen.

I'm currently an all microsoft enviroment but the licensing costs have seen me look to linux a bit more and i'm lookig to get a test enviroment up.

I will be keeping an AD domain regardless.  I need to add a file server, mail server, web server and a DB server for 100-150 users.  Samba bound to the Domain and kerberos authentication looks to be the way to go for file services.  I've looked at this through webmin and I think it should be fairly simple to administer. 

I see the mail server being the biggest problem.  I'm not too fussed if it's Imap or Mapi but no pop3.  I also need to be able to create mailboxes that are associated with AD accounts, and I see this being a big hurdle.

The SQL server isn't hammered hard but again I'd need it to authenticate AD accounts.  

Basically my problems stem from the fact that AD integration is required but it's got to stay.

If anyone has anything that would help me in implimenting this i'd be grateful for your input.

Thanks
Jamie

---

### Post by astrotech226 on 2008-02-21
You are probably looking to implement an IMAP server.  There are many out there, but I've had much success with Cyrus.  I like it because each email is stored in the filesystem as an individual file.  It's easy to backup/restore/replicate.

I don't have much experience with AD, but going open source for email is sort of hard to tackle anyway.  When adding users to AD, I don't see a way for it to add the mailboxes at the same time.  So you'll have have to maintain them separately.  If you could dump AD, it's easy to integrate it all together.

The other problem with your environment (I am going to guess) is the mail client itself.  If your users are entrenched in Outlook, that is another issue.  You can't natively store contacts and calendars in IMAP, so you have to install some 3rd party app to make it work.  I've used Bynari Insight Connector with some success.  For the most part, we just force Thunderbird on the users.

Let me know if you need more information.

---

### Post by igknighted on 2008-02-21
There is a thread comparing the various exchange-type servers in the cafe right now, see here for more info: [http://ubuntuforums.org/showthread.php?p=4376255](http://ubuntuforums.org/showthread.php?p=4376255)

---

### Post by HermanAB on 2008-02-21
[http://citadel.org](http://citadel.org)

Citadel scales much better than Exchange.  Typically, you can replace a whole rack of Exchange servers with a single Citadel server.

---

