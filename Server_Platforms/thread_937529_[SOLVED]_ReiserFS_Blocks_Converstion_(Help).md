---
title: "[SOLVED] ReiserFS Blocks Converstion (Help)"
date: 2008-10-03
forum: Server Platforms
---

### Post by Keymaster on 2008-10-03
How can I convert to, and from ReiserFS blocks to Mega/Gigabytes?

Edit: I found it:
```

sudo /sbin/debugreiserfs /dev/yourdisk | grep "Blocksize"

```

---

