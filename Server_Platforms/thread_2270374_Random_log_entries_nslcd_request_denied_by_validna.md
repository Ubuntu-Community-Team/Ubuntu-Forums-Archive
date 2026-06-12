---
title: "Random log entries: nslcd: request denied by validnames option"
date: 2015-03-22
forum: Server Platforms
---

### Post by peridian on 2015-03-22
Hi,

On one of my servers, I keep seeing entries similar to the below line appearing randomly in the syslog:

```

nslcd[1873]: [155dbc] <passwd="*"> request denied by validnames option

```

There doesn't seem to be anything corresponding to this in the auth.log.

How can I figure out what this is related to?

Regards,
Rob.

---

### Post by nerdtron on 2015-03-25
A quick search returns [http://linux.die.net/man/8/nslcd](http://linux.die.net/man/8/nslcd)
I don't think it is malicious.
Is your server locked down on your network? then you can try using wireshark to see which IP this type of request comes from.

---

### Post by peridian on 2015-03-26
I think this occurs when I try a command requiring sudo and haven't yet entered my password.  I had thought it was random, but I've realised it's whenever I am logged in.

Thanks,
Rob.

---

