---
title: "locate can find deleted directory"
date: 2010-06-16
forum: Security
---

### Post by weazuul on 2010-06-16
Hi guys,

I tried to delete a certain directory but then when i use locate i can find it althow it does not appear in that place. I know that ext4 does such a thing as to just delete the inode but i was wondering if there is a way to remove that registration altogether and not get it in locate?

Thanks

---

### Post by meklu on 2010-06-16
AFAIK, locate has a database from which it seeks the requested files. Perhaps you should update the database:
```
sudo updatedb
```

---

### Post by weazuul on 2010-06-16
thx that solved it, can mark as solved is possible and/or wanted :)

---

