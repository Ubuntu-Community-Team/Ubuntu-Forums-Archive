---
title: "Hide system information"
date: 2010-06-25
forum: Security
---

### Post by jooz87 on 2010-06-25
Im using Ubuntu 9.10.
When I use Nessus scan to scan my computer I can receive information about how match RAM, how man CPU etc. How can I hide this? Any suggestions? Thanks!

---

### Post by cdenley on 2010-06-25
I'm not very familiar with Nessus, but I assume you mean that information can be retrieved remotely without any authentication? That would be surprising. I think the only way that would be possible is if a listening service is revealing that information, so what listening processes do you have running?
```

sudo netstat -tulnp

```

If you are running Nessus on the system you are scanning, then of course it can determine that kind of system information with local access.

---

