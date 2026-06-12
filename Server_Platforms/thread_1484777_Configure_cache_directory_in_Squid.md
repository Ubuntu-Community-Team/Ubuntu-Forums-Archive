---
title: "Configure cache directory in Squid"
date: 2010-05-16
forum: Server Platforms
---

### Post by sikander3786 on 2010-05-16
I am running squid on Ubuntu Lucid Lynx. Everything is working fine except Yahoo Messenger (which I already have started a dedicated thread for).

I want to configure cache directory for squid. I have allocated 150 GB ext4 partition mounted in /media/Squid and is owned by me.

Now when I add the line

```

cache_dir ufs /media/Squid/cache 150000 16 256

```

Squid fails to start.

What is going wrong there?

Regards.

---

