---
title: "How do i completely remove all mail server programs in order to start afresh"
date: 2009-11-30
forum: Server Platforms
---

### Post by thepreacher on 2009-11-30
I have spent so much time trying to setup a mail server without success. I have tried so many settings and followed so many tutorials that i think in the end i have messed up the server. What i want to do is that i want to start afresh by getting rid of all the mailserver related programs, postfix etc and all their associated configs. I tried the apt-get remove but the configuration did not get removed. This is a live system and I don't want to mistakenly delete any files that may be used by other programs.

BTW this is my current setup incase any one wants to help.

The Server is behind a 2wire router with a static ip address. the name of the server is pmct1.gateway.2wire.net. I have currently setup 5 domains which are all serving pages to the WWW. For 3 of these domains i want to create users who will be able to have email addresses like [email]username@domain1.com[/email], [email]username@domian2.com[/email] etc and also want them to be able to access their mails from the internet. 

For each of the domains i have created an MX records like mail.domain1.com

---

