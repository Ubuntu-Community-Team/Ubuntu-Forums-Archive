---
title: "dist-upgrade if there is no ubuntu-ce-wallpapaers"
date: 2009-08-16
forum: Ubuntu Christian Edition
---

### Post by david_kt on 2009-08-16
If for some reasons you have ubuntu-ce repository but you do not have ubuntu-ce wallpapaers, open terminal and do the following:

```
sudo apt-get update
sudo apt-get dist-upgrade 
```

After that, you should remove firehol as it is not needed anymore:
```

sudo apt-get remove --purge firehol
```


DK

---

