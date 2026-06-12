---
title: "Postfix configuration: multiple processes"
date: 2013-06-28
forum: Server Platforms
---

### Post by insidus on 2013-06-28
Heres the scenario. I need to accommodate an Email relay for my workplace in Ubuntu 12.04. I need this relay to accept any one of two situations. 

The first: The VOIP phone system runs on x.x.x.246, and it must send unauthenticated emails through the Ubuntu Postfix server to Office365. This has to be on port 25 (The phone system is quite old, doesn't support authentication or port changing)

The second: Every week, mass emails are sent out with invoices from multiple clients. To advoid any viruses or malware sending out emails from anyhost, authentication must be set up. This clients will log onto the Postfix server, and send their emails through that login.

Both situation one and two must be able to co-exist, where the VOIP system sends out unauthenticated emails, the other clients must use authentication.

I believe this could be done by running multiple processes, or by changing the outwards port (which can be done for situation 2)

Any help in this matter would be highly appreciated.

ps. I haven't included any config files, I have just the stand postfix installation currently, and was hoping for guidance instead of exact configurations. Thanks.

---

### Post by chrisguk on 2013-06-30
Hi,

Have you taken a look at this post. I believe it is very useful for your needs:

[http://serverfault.com/questions/126282/postfix-check-outgoing-mail-for-spam](http://serverfault.com/questions/126282/postfix-check-outgoing-mail-for-spam)

---

