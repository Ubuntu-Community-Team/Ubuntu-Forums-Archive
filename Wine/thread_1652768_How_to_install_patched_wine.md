---
title: "How to install patched wine?"
date: 2010-12-25
forum: Wine
---

### Post by trinitydan on 2010-12-25
I used Wine-git to patch Wine, but it still showed that I had my prior installation of Wine.  So I uninstalled previous Wine and tried the patch again, which seemed successful, but now I don't seem to have Wine installed, just the directories to my Wine applications.  

Output of wine --version:
```
bash: /usr/bin/wine: No such file or directory
```Can someone please help me to get my patched Wine installed?

Thanks in advance!

EDIT:  The solution was simple.  Just run Wine from the directory where it was patched.  Uninstall existing Wine installs first.

---

