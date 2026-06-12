---
title: "apache archaeology, how to examine runaway process?"
date: 2008-05-05
forum: Server Platforms
---

### Post by thnn on 2008-05-05
This is sort of a general methodology question... meaning, how would investigate a situation like this...

Over the weekend my server stopped :( I was able to ssh in, and everything seemed normal, but Apache wasn't running - 'apache2ctl start' and I was in business.

The end of /var/logs/apache2/error.log :

```

[Sun May 04 06:25:08 2008] [warn] child process 3116 still did not exit, sending a SIGTERM
[Sun May 04 06:25:10 2008] [warn] child process 3116 still did not exit, sending a SIGTERM
[Sun May 04 06:25:12 2008] [error] child process 3116 still did not exit, sending a SIGKILL
[Sun May 04 06:25:13 2008] [notice] caught SIGTERM, shutting down

```

So I'm guessing this runaway process killed Apache? How can I investigate more? There isn't much in /var/logs/apache2/access.log for the same time period (last access on May 04 at 3:22) There are other errors in error.log - but I can't tell what process 3116 corresponds to...

---

