---
title: "Postgrey Greylist Problems"
date: 2012-10-05
forum: Server Platforms
---

### Post by 1-Up on 2012-10-05
I haven't had this problem much on the local or my email account.  However, other users on my server have a problem with getting greylisted.

```
postfix/smtpd[6698]: NOQUEUE: reject_warning: RCPT from ...: 504 4.4.2 <OmegaStar>: Helo command rejected: need fully qualified hostname
postgrey[1405]: action=greylist, reason=new, client_name=... client_address=..., sender=..., recipient=...
postgrey[1405]: cleaning up old logs
postfix/smtpd[6698]: NOQUEUE: reject: RCPT from...: 450 4.2.0  Recipient address rejected: Greylisted, see (webpage)
```

I'm not sure what the problem is here.  In the case of this log a SQL email account was sending to another SQL email account on my server.  However, the sender was connecting from the WAN.  I'm not sure what's causing this issue, and any help would be appreciated.

---

### Post by lisati on 2012-10-05
The first line, the one with "reject_warning" doesn't have anything to do with postgrey. It looks to me more like something to do with an smtpd_helo_restrictions.

The next thres lines are normal, and you don't need to worry. Part of postgrey's configuration includes cleaning out its cache every so often, and if someone hasn't sent you an email for a while, their details will drop off postgrey's database.

You will notice that your server is giving a "450" error. This means "try again later." If someone sends you an email that gets bounced back with a message that claims greylisting as the reason, the problem is at their end. They will need to contact their email provider.

You might want to look at this article: [http://projects.puremagic.com/greylisting/](http://projects.puremagic.com/greylisting/)

---

### Post by 1-Up on 2012-10-05
Well, in this case, the sender and receiver are hosted on my server.  So, do I need to worry about it?

On the smtpd_helo_restrictions, I can't remember everything I have currently, but accept_sasl_authenticated should be there.  Do I need to worry about that reject warning?

---

