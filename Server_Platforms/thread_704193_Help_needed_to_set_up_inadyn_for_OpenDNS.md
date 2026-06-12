---
title: "Help needed to set up inadyn for OpenDNS"
date: 2008-02-22
forum: Server Platforms
---

### Post by theolster on 2008-02-22
I've searched all over the intweb and have only found partial solutions to get this to work.

I need to set up inadyn to update my OpenDNS hostname.  I first tried running this as a cron job:```
*/15 * * * * /usr/sbin/inadyn -u MYUSERNAME -p MYPASSWORD --iterations 1 -a MYHOSTNAME
```

This worked, sort of, OpenDNS temporarily disabled my acc because I was running inadyn as a single iteration every 15 mins, which essentially forced an update whether one was needed or not.

I've tried to mess around with init.d to get the following command going from bootup, but with little success.  Where should I be placing this command?```
/usr/sbin/inadyn -u MYUSERNAME -p MYPASSWORD --update_period_sec 600 -a MYHOSTNAME
```

It would also be handy to view some kind of logs, if anyone knows how to set that up?

---

