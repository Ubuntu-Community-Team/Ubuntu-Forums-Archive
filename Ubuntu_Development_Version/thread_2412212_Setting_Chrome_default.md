---
title: "Setting Chrome default"
date: 2019-02-09
forum: Ubuntu Development Version
---

### Post by VMC on 2019-02-09
I forgot I brought up this topic before, but I found a fix for it on Lubuntu's Disco:
This will reveal who's in charge:
```
xdg-settings get default-web-browser
```
This will change default to Chrome:
```
sudo xdg-settings set default-web-browser google-chrome.desktop
```

Xubuntu it seems isn't affected.

---

