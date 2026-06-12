---
title: "Modifying PATH in wine"
date: 2010-05-14
forum: Wine
---

### Post by dodle on 2010-05-14
According to [wine's website]("http://www.winehq.org/site/docs/wineusr-guide/environment-variables"), I am supposed to open the registry editor and go to the key HKEY_CURRENT_USER/Environment.  But I do not have an Environment key under HKEY_CURRENT_USER.  Is there another way to add to PATH in wine?

---

### Post by pedro_orange on 2010-05-14
```
wine cmd
```

Have you tried opening this to edit your PATH environment variable?

---

### Post by dodle on 2010-05-18
Yes, thank you.  Also, I completely forgot about a tool I use often for windows: [Rapid Environment Editor](http://www.rapidee.com/).

---

