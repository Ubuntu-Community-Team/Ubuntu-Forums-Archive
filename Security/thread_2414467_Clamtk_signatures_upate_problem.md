---
title: "Clamtk signatures upate problem"
date: 2019-03-11
forum: Security
---

### Post by rudolf-kunzli on 2019-03-11
Hello,

If I check for updates Clamtk hangs for ever and I have to kill it (Force Quit).
This happens since a week or so.
Is there a reason and a workaround?

Thanks
Rudolf

---

### Post by &amp;KyT$0P# on 2019-03-11
Try running these commands in Terminal -
```
sudo rm -v /var/lib/clamav/daily.cld
sudo freshclam
```

Does it work now?

---

