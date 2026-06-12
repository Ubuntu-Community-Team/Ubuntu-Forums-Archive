---
title: "rescue mode: r/o disk?"
date: 2012-11-02
forum: System76 Support
---

### Post by DaveSeidel on 2012-11-02
Lemur Ultra, 12.10

Hi, I stupidly made a bad change in sudoers (visudo did not save me) and now I no longer have root access. I was able to get into rescue/recovery mode after several tries, but the disk is readonly so I can't fix the file.

How can I boot into recovery mode with a writable disk?

---

### Post by DaveSeidel on 2012-11-02
Gah, I should have googled for another minute before posting. The answer, of course is:

  mount -o remount,rw /

All is now well. Sorry for the noise.

---

### Post by jerome1232 on 2012-11-02
Once in recovery mode, run this command to mount the root file system read/write

```
mount / -o remount,rw
```

---

