---
title: "How to check NTFS partition"
date: 2009-12-19
forum: Sudan Team
---

### Post by zero-n on 2009-12-19
1- You need to install **[COLOR="Red"]ntfsprogs[/COLOR]** package.
```
sudo apt-get install ntfsprogs
```

2- Check your NTFS partition:
```
sudo ntfsfix /dev/[COLOR="red"]**hda1**[/COLOR]
```

Change **[COLOR="red"]hda1[/COLOR]** to your NTFS partition name.

---

