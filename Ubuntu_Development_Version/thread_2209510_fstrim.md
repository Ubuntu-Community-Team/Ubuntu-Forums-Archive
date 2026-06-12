---
title: "fstrim"
date: 2014-03-06
forum: Ubuntu Development Version
---

### Post by Hreinsi on 2014-03-06
Hi is fstrim enabled in 14.04

---

### Post by fooman on 2014-03-06
yes it is.  you should see it in: /etc/cron.weekly

---

### Post by ventrical on 2014-03-06
Applies as such:

```

#!/bin/sh
# call fstrim-all to trim all mounted file systems which support it
set -e

# This only runs on Intel and Samsung SSDs by default, as some SSDs with faulty
# firmware may encounter data loss problems when running fstrim under high I/O
# load (e. g.  https://launchpad.net/bugs/1259829). You can append the
# --no-model-check option here to disable the vendor check and run fstrim on
# all SSD drives.
exec fstrim-all


```

---

### Post by Hreinsi on 2014-03-06
thx

---

