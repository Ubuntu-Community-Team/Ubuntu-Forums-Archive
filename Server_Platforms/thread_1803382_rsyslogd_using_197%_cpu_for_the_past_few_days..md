---
title: "rsyslogd using 197% cpu for the past few days."
date: 2011-07-13
forum: Server Platforms
---

### Post by Schalken on 2011-07-13
I'm running natty server on Rackspace cloud and rsyslogd has been using 197%  off my cpu (quad core I believe) for the past few days. Does anyone have an pointers as to how to figure out what is going on?

---

### Post by ruffEdgz on 2011-07-13
Is this a fresh install of Ubuntu 11.04 Server? You haven't touched the /etc/rsyslog.d/50-default.conf file recently have you?

Depending on what its logging and were (which can be a lot of different locations, levels, etc...) it might be hard to pin point.

Can you also check your /var/log/ directory and see which of the files are filling up the most:
```

sudo du -ha /var/log/

```
This will display every file/directory in /var/log/ and show their size in human-readable.

Hope this helps!

---

