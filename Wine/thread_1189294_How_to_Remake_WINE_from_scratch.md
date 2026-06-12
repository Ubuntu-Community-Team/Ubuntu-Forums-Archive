---
title: "How to Remake WINE from scratch?"
date: 2009-06-16
forum: Wine
---

### Post by amazurenko on 2009-06-16
Hello,

I made some mistakes on wine, and tried to redo it from scratch. Reinstalling unfortunately did not remake the folder and thus I deleted the folder. But now, when I reinstalled it again, wine has no folder and I have no virtual C drive. How can I get a perfectly fresh install of wine?

Thank you,

amazuerenko

---

### Post by Bios Element on 2009-06-16
```
sudo apt-get purge wine
```

Then delete your /home/<username>/.wine folder and then run

```
sudo apt-get install wine
```

Oh, and google is your friend. You'd have probably found an answer quicker if you just searched for it yourself.

---

