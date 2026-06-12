---
title: "Mail server, is this correct ??"
date: 2011-10-09
forum: Server Platforms
---

### Post by Pat-UK on 2011-10-09
Hi guys, 
 
total newbie to Ubunto server, have downloaded installed 11.04 server have selected yest to all the additional programs at the end of the install, have installd all the updates.
 
Now what I want to do is move my small office mail system form our web host server to our own server in our office, we have moved office and now have a very slow connection so it made sense to cut down out bandwidth and hopfully increase our dead slow internet.
 
we have about 1gig of mail in total in our IMAP folders online for the 10 email addresses, one domain , can I just confirm that, I can use the server to download all the email as and when it comes in clear it from our web hosts imap folders, store it all on our in office server and allow the various users get theirown email internally ?
 
if this is right, is there any good how to's around ??
 
Many Thanks

---

### Post by HermanAB on 2011-10-10
Yes, this sounds like a job for Citadel.

---

### Post by collisionystm on 2011-10-10
> **Pat-UK said:**
> Hi guys, 
 
total newbie to Ubunto server, have downloaded installed 11.04 server have selected yest to all the additional programs at the end of the install, have installd all the updates.
 
Now what I want to do is move my small office mail system form our web host server to our own server in our office, we have moved office and now have a very slow connection so it made sense to cut down out bandwidth and hopfully increase our dead slow internet.
 
we have about 1gig of mail in total in our IMAP folders online for the 10 email addresses, one domain , can I just confirm that, I can use the server to download all the email as and when it comes in clear it from our web hosts imap folders, store it all on our in office server and allow the various users get theirown email internally ?
 
if this is right, is there any good how to's around ??
 
Many Thanks

Dont use 11.04 for a server. The support does not extend far enough, and performing upgrades on an email server is always a nightmare.

I suggest Zentyal. It is probably the easiest thing to configure that I have seen so far.

[www.zentyal.com](www.zentyal.com)

based on 10.04 server. It has lxde gui and a nice web interface. 

Configuring mail in it is a snap. It even makes retrieving mail from an external source as easy as a check box and an email address.

---

