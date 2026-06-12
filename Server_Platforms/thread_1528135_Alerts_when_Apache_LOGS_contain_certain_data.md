---
title: "Alerts when Apache LOGS contain certain data"
date: 2010-07-10
forum: Server Platforms
---

### Post by mistypotato on 2010-07-10
Does anyone know of any software that can monitor the Apache logs for certain phrases or keywords then send an alert when found?

For example I know an attempt to hack has been made when I see log entries like this....

/admin/
/admin/phpadmin/
/phpadmin/

But by the time I see it, the attempt has long since failed or succeeded.

What I need is a way for my server to alert me WHILE someone is entering these phrases.

I realize there may be a "hit" to performance but my server is not that busy anyway (except for hackers).

Thx

---

### Post by zabuch on 2010-07-10
I'm not sure how do you imagine that - would you like your server to send you an email every time given URL is accessed? You can imagine how many emails that would generate...
I think what you are looking for here is [modsecurity]("http://www.modsecurity.org/") - it will enable you to perform some actions (like blocking the request) while (actually before) it's done.

---

