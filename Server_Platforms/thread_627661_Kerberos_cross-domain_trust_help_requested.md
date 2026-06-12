---
title: "Kerberos cross-domain trust help requested"
date: 2007-11-30
forum: Server Platforms
---

### Post by rouben on 2007-11-30
Hi everyone!

Is there any way to set up something similar to Microsoft's "cross-domain trust" type relationship between Kerberos servers? Ideally I'd like the following scenario:

1. Kerberos would be doing authentication strictly, no authorization.
2. I have a master kerberos server that I can't touch other than use it for authentication on my machine.
3. I have a slave kerberos server that I would simply like to forward all auth requests to the master, without having a copy of the master's database (i.e. not a slave in the traditional sense).
4. I'd like to have a whole bunch of other machines authenticating to my "slave" kerberos instance.

Thanks!

---

