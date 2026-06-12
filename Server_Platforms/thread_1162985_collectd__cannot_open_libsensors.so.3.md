---
title: "collectd  cannot open libsensors.so.3"
date: 2009-05-18
forum: Server Platforms
---

### Post by Barry53 on 2009-05-18
Hi all,

I'm having trouble getting sensors plugin working in collectd. 
```
collectd -t -C /etc/collectd/collectd.conf
lt_dlopen failed: libsensors.so.3: cannot open shared object file: no such file or directory
Unable to load plugin sensors.
```

I do have:
/usr/lib/libsensors.so.4
/usr/lib/libsensors.so.4.0.0

So how do I tell collectd to use libsensor.so.4?
What other information can I post to help answer this?

Other plugins do work so, this is a problem with the sensors plugin.

Thanks in advance,
Barry

---

