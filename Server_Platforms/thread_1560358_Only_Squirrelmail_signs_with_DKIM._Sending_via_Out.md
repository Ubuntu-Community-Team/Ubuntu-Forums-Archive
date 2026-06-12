---
title: "Only Squirrelmail signs with DKIM. Sending via Outlook does not."
date: 2010-08-24
forum: Server Platforms
---

### Post by ledzepln86 on 2010-08-24
I have set up a server with the following guide:

[http://www.howtoforge.com/perfect-server-ubuntu-10.04-lucid-lynx-ispconfig-3](http://www.howtoforge.com/perfect-server-ubuntu-10.04-lucid-lynx-ispconfig-3)

I am using amavisd-new to sign my outgoing emails with DKIM and have it all properly configured. The only issue is:

 - When sending through Outlook (from another machine) , the DKIM signatures do not pass. I am sending via an authenticated user.

* When sending through Squirrelmail , the DKIM signature sends fine.

---

