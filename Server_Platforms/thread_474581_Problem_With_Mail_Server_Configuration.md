---
title: "Problem With Mail Server Configuration"
date: 2007-06-15
forum: Server Platforms
---

### Post by lightnb on 2007-06-15
I'm running Ubuntu 7.04 Server with ISPConfig.

When I send mail to it using my Bellsouth email address, I get the bounce error:

> sorry, relaying denied from your location [205.152.59.67] (#5.7.1)

If I try to setup an outlook account to receive the email from the address, it finds the server ok, but authentication fails.

Where do I even start to troubleshoot?

---

### Post by rickyjones on 2007-06-15
Start troubleshooting on the server itself. It sounds like you need to authenticate to your server, so now you just need to make sure that your server will allow you to authenticate. I'm not sure on /how/ to do that though. But it's a step in the right direction.

-Richard

---

