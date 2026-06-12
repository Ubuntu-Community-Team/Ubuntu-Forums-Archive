---
title: "Sendmail Delay"
date: 2007-01-28
forum: Server Platforms
---

### Post by HAL98 SE on 2007-01-28
Hi, i'm wondering if anybody can help me with sendmail.

As i was initially going through the procedures and tutorials for setting up sendmail (still am) i thought that something was broken as it appeared to hang whenever i execute a sendmail command, i.e:-

```
sendmail -d0.1 -bp
```

On further inspection this wasn't the case at all, there's delay of exactly 1 minute between submitting any command like the above, and sendmail then processing it. This delay also occurs when attempting to send email from any site I have hosted on the server, indicating that this is a configuration setting...somewhere....err....

Is this default sendmail behaviour? if so, how can i modify it?

---

### Post by Adam_NZ on 2008-04-28
> **HAL98 SE said:**
> Hi, i'm wondering if anybody can help me with sendmail.

As i was initially going through the procedures and tutorials for setting up sendmail (still am) i thought that something was broken as it appeared to hang whenever i execute a sendmail command, i.e:-

```
sendmail -d0.1 -bp
```

On further inspection this wasn't the case at all, there's delay of exactly 1 minute between submitting any command like the above, and sendmail then processing it. This delay also occurs when attempting to send email from any site I have hosted on the server, indicating that this is a configuration setting...somewhere....err....

Is this default sendmail behaviour? if so, how can i modify it?

I see this thread is 2 years old! I've just upgraded to 8.04 (Hardy Heron) and have discovered I have the same problem. I have some PHP routines that use mail() - which then calls Sendmail (as  defined in php.ini). The page just sits there for 1 minute, then finally sends.

I'm not too familiar with the intricacies of Sendmail. From my Googling around, it appears it may be something to do with my test server not having a fully qualified domain name. I'm running it as "localhost" to test sites that will go live elsewhere.

Would I need to set up a "dummy" domain of some sort?

---

