---
title: "Using a different proxy server for chromium vs chrome?"
date: 2016-11-01
forum: The Cafe
---

### Post by hip13044b on 2016-11-01
I use both Chrome, AND Chromium, for different things. However when I opt to use a proxy server for Chromium, then Chrome also uses this server. It appears both of them share the proxy setting "Use manually specified proxy configuration". I was wondering if anyone knows a way to separate them?

---

### Post by ArgentWarrior on 2016-11-06
This should work:
```
http_proxy="address:port" browser
```

---

