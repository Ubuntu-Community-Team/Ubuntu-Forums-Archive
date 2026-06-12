---
title: "Why are these accounts in /etc/passwd please?"
date: 2013-08-09
forum: Security
---

### Post by phoenix1963 on 2013-08-09
Yes, I know I'm paranoid, it's the internet...
here are the entries:
```
guest-JDBtnk:x:114:126:Guest,,,:/tmp/guest-JDBtnk:/bin/bash
guest-d2X8hZ:x:115:127:Guest,,,:/tmp/guest-d2X8hZ:/bin/bash

```

Thanks in advance,
phoenix1963

---

### Post by SlugSlug on 2013-08-09
caused when you use the guest login account. I've never used it but believe it will clear it's self up..

---

### Post by CharlesA on 2013-08-09
If I remember right, any time you use the guest account, it is given a random password. Shouldn't be something to worry about as it should be wiped on reboot.

---

### Post by phoenix1963 on 2013-08-09
Hmmm, I've never knowingly used a guest account....

And they're still there after reboot.

phoenix1963

---

