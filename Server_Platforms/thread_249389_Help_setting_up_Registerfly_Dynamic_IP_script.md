---
title: "Help setting up Registerfly Dynamic IP script"
date: 2006-09-02
forum: Server Platforms
---

### Post by barrmulio on 2006-09-02
Hi

I'm trying to setup registerfly for dynamic ip.  I had it working before thru a cron job running ipcheck every 15 until my server bombed and now I'm trying to trace back what I did.

I installed ipcheck and setup for dyndns and it's working.  Registerfly has me hitting a http url to update: 
```

http://dynamic.registerfly.com?domain=domain.com&password=password&host=

```

what I need is a cron job hit that url every 15min for auto update, i'm guessing I don't even need ipcheck since hitting that url will pull the ip

thanks in advance

---

