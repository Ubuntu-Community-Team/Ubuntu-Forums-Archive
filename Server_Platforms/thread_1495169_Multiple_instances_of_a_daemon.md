---
title: "Multiple instances of a daemon"
date: 2010-05-27
forum: Server Platforms
---

### Post by Carson Dyle on 2010-05-27
I have a test server on which I'd like to run up to 30 separate instances of a program as daemons, each running on a different IP address bound to the server.  I've created a init script that takes an additional command line parameter - the last octet of the IP address.  For example:

```

sudo myprog 40 start
sudo myprog 41 start

```

This would run instances of the program on IP addresses 192.168.1.40 and 192.168.1.41 respectively.  But it's looking like this approach isn't doable if I wish to have any or all of these run at startup, as the links in the rcN.d directories can only link to the init script, not pass a parameter.

Is there some workaround that can be suggested, or do I really need to create 30 instances of the init script?  I suppose I could churn those out with another script, but...

---

### Post by Vegan on 2010-05-27
Linux is designed for threads not multiple instances. You would have to change the code sigfnificantly to support multiple instances.

---

### Post by Carson Dyle on 2010-05-27
Huh?  I'm not sure what/if that has to do with anything.  The multiple instances of the daemon run just fine.

---

