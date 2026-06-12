---
title: "How to limit the number of concurrent clients in ssh server"
date: 2011-02-01
forum: Server Platforms
---

### Post by vksingh on 2011-02-01
Dear Friends,

I am using ssh server to connect to my Ubuntu desktop. I opened the file sshd_config and change my port number of the server.

I want to put a limit on the number of clients in the ssh server.

Please help.


Regards,

Vivek

---

### Post by lisati on 2011-02-01
*Thread moved to **Server Platforms**.*

---

### Post by moody_mark on 2011-02-01
Hi, im not sure if you tried looking at the man page but a lot of the config files in linux will have a man page for them too:

```

man sshd_config
```

I had a quick check and found the following flag

> MaxSessions
             Specifies the maximum number of open sessions permitted per network connection.  The default is 10.

The example config files wont always have every option in them.

Hope this helps

---

