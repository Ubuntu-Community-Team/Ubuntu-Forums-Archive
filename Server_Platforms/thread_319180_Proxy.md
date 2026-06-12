---
title: "Proxy"
date: 2006-12-15
forum: Server Platforms
---

### Post by DrNick on 2006-12-15
Hi all

Bit of a stupid question but can't figure out how... how would I set the system proxy server with the CLI?  This is for a Ubuntu server machine, which has no GUI.

Cheers,

Tom Byrne

---

### Post by yota on 2006-12-15
```

export http_proxy="http://*username:password@proxy.ip.address.or.hostname"

```

Hope it helps!

---

### Post by DrNick on 2006-12-15
Excellent, thanks!

---

