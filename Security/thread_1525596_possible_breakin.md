---
title: "possible breakin?"
date: 2010-07-06
forum: Security
---

### Post by mrj001 on 2010-07-06
For the past few days, odd things have been happening.

My network has an Ubuntu 10.04 server, two Ubuntu 10.04 clients and one windows client.  It is protected by a D-Link Firewall/router, connected to the Internet.

I have been able to log in from my main client system to the server using ssh without problems.  It did randomly ask for my password, but only on some logins.  

Two days ago, I suddenly got a message that the server key was not valid.  The server was not installed/reformatted/updated at that time.  I manually changed the key and re-added to my known_hosts, checking the signature.

Yesterday, the same thing happened!  The key was not recognized again.  Again I manually changed the key and added it to my known_hosts, checking the signature.  This time I wrote the signature down, so I could check the error message from ssh if it happened again.

Today, it did not happen.  However, mysql will no longer permit me to connect from this client.  I had been routinely connecting from this client before today.  I can ssh to the server and connect to mysql.  The user table still looks like I should be able to connect from this client.

chkrootkit did not reveal any installed root kits on the server or client.  On the client, it did reveal that the output of lastlog is incorrect.  'lastlog' claims I last logged in yesterday.  This client machine was shut off overnight, and I logged in this morning, and again this evening.  'lastlog' also incorrectly claims that three users have never logged in. They have.  At least two of those users were logged in within the last 24 hours.

On the server, lastlog appears to be OK.

Any ideas/suggestions?  Do these odd happenings point to a break in?

---

