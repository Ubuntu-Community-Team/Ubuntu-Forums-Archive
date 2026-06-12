---
title: "Postfix not receiving email"
date: 2012-12-18
forum: Server Platforms
---

### Post by keithclark on 2012-12-18
I have just installed postfix for the first time every and seem to be able to send emails just fine, but I cannot receive them.  I think the following might be a hint in the logs?

Dec 18 19:04:46 kitty postfix/error[6288]: 34FE5627B1: to=<keithclark@sandowne.dlinkddns.com>, relay=none, delay=153258, delays=153224/34/0/0.22, dsn=4.4.1, status=deferred (delivery temporarily suspended: connect to sandowne.dlinkddns.com[173.206.93.96]:25: Connection timed out)

Any help would be appreciated.

Thanks,

Keith

---

### Post by chadk5utc on 2012-12-19
posted by mistake

---

### Post by SeijiSensei on 2012-12-21
Make sure the mynetworks directive in main.cf is not restricted solely to 127.0.0.1, the localhost interface.  Read [this](http://www.postfix.org/BASIC_CONFIGURATION_README.html#relay_from) if you have not yet done so.

Scanning the IP address listed above shows only ports 22 and 80 open.  Is this a publicly-visible machine, or one in a home or office?  If the latter, does your ISP allow you to run servers under its Terms of Service for your account?  Perhaps they have blocked port 25?

---

