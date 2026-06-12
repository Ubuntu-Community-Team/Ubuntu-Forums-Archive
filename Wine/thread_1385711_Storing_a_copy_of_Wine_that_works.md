---
title: "Storing a copy of Wine that works"
date: 2010-01-19
forum: Wine
---

### Post by fester225 on 2010-01-19
Wine hasn't worked on Sketchup for me since 1.1.31. Now 1.1.36 works and I don't want to lose a version which does.

How do I download this Ubuntu (.deb?) friendly version of Wine so I can reload it if I need to? (The version I have now was automatically loaded through Syanaptic Package Manager, so I can't just save that.)

---

### Post by beastrace91 on 2010-01-19
```
sudo apt-get --download-only install <package name>
```

Or if you have already installed the package via apt-get check out **/var/cache/apt/archive/** - it keeps any application apt-get has installed stored there until you clear it.

EDIT: You also might wanna check the link in my sig for installing multiple Wine versions - this way you can always keep 1.1.36 (or any version) installed for running certain programs.

~Jeff

---

