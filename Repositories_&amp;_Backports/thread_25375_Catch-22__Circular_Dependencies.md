---
title: "Catch-22?  Circular Dependencies"
date: 2005-04-10
forum: Repositories &amp; Backports
---

### Post by drchatty on 2005-04-10
I'm currently trying to download the packages required to use OpenGL with C++.  For this, I seem to need libxi-dev, which requires libx11-dev, which requires libxi-dev, and so on.  I still haven't been able to correctly configure my modem (dreaded linmodem), so I have to download to my Windows machine and transfer the files.  Both are currently downloaded.  How can I install them when one can't install without the other?

Matt

---

### Post by heimo on 2005-04-10
I don't know if there's better solution to this problem, but you could try manualy forcing the install of libxi-dev. Using dpkg (debian package manager) like this:
```
sudo dpkg --force-depends -i [file-name-of-package-here]

```

---

### Post by drchatty on 2005-04-10
Thanks, it worked.

---

