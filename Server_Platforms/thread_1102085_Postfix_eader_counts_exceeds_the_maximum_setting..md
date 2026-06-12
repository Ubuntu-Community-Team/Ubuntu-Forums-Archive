---
title: "Postfix: eader counts exceeds the maximum setting."
date: 2009-03-21
forum: Server Platforms
---

### Post by rtenklooster on 2009-03-21
Hi everyone,
I spent my evening setting up my mailserver.
i followed [this HOWTO]("http://http//www.howtoforge.com/virtual-users-domains-postfix-courier-mysql-squirrelmail-ubuntu8.04") exactly, and almost everything seems to bee working.
When i connect to my own mailserver by imap, with evolution, and try to send a message to my gmail adress, my isp does not accept the message.
I am receiving the following message:

host mail.kpnplanet.nl[213.75.63.13] said: 552 Your
"received:" header counts exceeds the maximum setting. (in reply to end of
DATA command)

Is there any way to increase the header count? Btw. I am using my isp's relay server becouse port 25 is blocked.

Yesterday i was able to send mail trough this relayserver, by a previous installed postfix mailserver, so i expect the problem is in my configuration.
I would be glad if anyone can help me solving this problem.

The second problem is, i am not receiving mail from the internet, while my postfix configuration has inet_protocols = all

The third problem is when i login to squirrel, i get a blank page. Just blank.

Thanks in advance

---

