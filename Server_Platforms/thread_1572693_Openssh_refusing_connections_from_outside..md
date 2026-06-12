---
title: "Openssh refusing connections from outside."
date: 2010-09-11
forum: Server Platforms
---

### Post by waloshin on 2010-09-11
When ever I try to sftp or even ssh into my server I get connection refused.

I have the port forwarded in my router.

What am I missing?

Also I have installed Ngnix so what do I need to do for it to work?

---

### Post by hictio on 2010-09-11
Are you using a user that you know it can connect to the server? IE, not the root user, for instance.
Can you do a basic connection test from the outside and see if you, at least, reach the server?
```

telnet IP.address.of.server 22 ENTER

```

You'll have to see something like this:
```

Connected to IP.address.of.server.
Escape character is '^]'.
SSH-2.0-OpenSSH_5.3p1 Debian-3ubuntu4

```

---

### Post by waloshin on 2010-09-11
> **hictio said:**
> Are you using a user that you know it can connect to the server? IE, not the root user, for instance.
Can you do a basic connection test from the outside and see if you, at least, reach the server?
```

telnet IP.address.of.server 22 ENTER

```

You'll have to see something like this:
```

Connected to IP.address.of.server.
Escape character is '^]'.
SSH-2.0-OpenSSH_5.3p1 Debian-3ubuntu4

```

When using the servers internal ip address it works ,but when using the outside ip address I get:


telnet: Unable to connect to remote host: Connection refused

---

### Post by waloshin on 2010-09-11
I also just phoned my isp and they dont block port 22

---

### Post by CharlesA on 2010-09-11
Are you trying to connect with the external ip address?

Normally you won't be able to do that from inside the network. Try from a different network - wifi hotspot, etc.

---

### Post by waloshin on 2010-09-11
> **CharlesA said:**
> Are you trying to connect with the external ip address?

Normally you won't be able to do that from inside the network. Try from a different network - wifi hotspot, etc.

Ok I will do that tonight, after work at a free wifi hotspot.

EDIT:

I have tried with the free wifi hotspot and have constantly got timed out. Though I checked their speed and they were running at 0.5 Mb/s so maybe that was the limiting factor though I did try on another wifi hotspot which I didn't test and it was much faster at loading webpages ,but it still time-out.

---

