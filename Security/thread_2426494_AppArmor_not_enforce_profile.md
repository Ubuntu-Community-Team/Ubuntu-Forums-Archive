---
title: "AppArmor not enforce profile"
date: 2019-09-10
forum: Security
---

### Post by lance bermudez on 2019-09-10
aa-logprof on usr.bin.chromium-browser profile not apparmor will not enforce it.

# aa-enforce usr.bin.chromium-browser
```

Setting /etc/apparmor.d/usr.bin.chromium-browser to enforce mode.

ERROR: profile has merged rule with conflicting x modifiers
ERROR processing regexs for profile /usr/lib/chromium-browser/chromium-browser, failed to load

```

---

