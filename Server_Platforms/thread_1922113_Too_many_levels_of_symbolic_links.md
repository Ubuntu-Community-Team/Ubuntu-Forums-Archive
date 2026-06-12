---
title: "Too many levels of symbolic links"
date: 2012-02-08
forum: Server Platforms
---

### Post by subhojit on 2012-02-08
i am getting this error while executing drush:

ls: cannot access ./bin/drush: Too many levels of symbolic links

how do i solve it?

---

### Post by rubylaser on 2012-02-08
You likely have a loop in your symbolic links, so that drush is pointing back  at itself like this.

```
ln -s /usr/local/bin/drush /bin/drush
ln -s /bin/drush /usr/local/bin/drush
./bin/drush
```

If this is the case, you just need to clean up the loop in the symbolic links by deleting the link that's causing the loop.

---

