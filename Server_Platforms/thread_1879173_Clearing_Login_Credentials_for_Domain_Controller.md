---
title: "Clearing Login Credentials for Domain Controller"
date: 2011-11-11
forum: Server Platforms
---

### Post by renzokuken on 2011-11-11
Apologies for this because it might be more of a windows question than Ubuntu, but here goes anyway.

I have a ubuntu domain controller/fileserver that users log into from their Windows machines, usually via Start -> Run -> \\servername\.

Now, if one person connects to their share on a certain PC, is there a way for that PC to forget the login details so someone else can login for their share? Basically, once one person has logged in, running the \\servername\ command simply opens up their share and no one else can access theirs. It seems to forget after a period of time, but i was wondering if this could be done instantly?

Hope this makes sense?

Thanks

Rob

---

### Post by renzokuken on 2011-11-11
never mind, solved it by running

```
net use * /delete
```

---

