---
title: "can't set google-chrome default"
date: 2019-10-11
forum: Ubuntu Development Version
---

### Post by VMC on 2019-10-11
Tried LXQT Session Settings > Default Applications > Web Browser = /usr/bin/google-chrome
also:
 sudo xdg-settings set default-web-browser google-chrome.desktop
Does not work. Lubuntu is the only one I have trouble getting Chrome to stick.

Usually a reboot fixes everything. Not anymore.

---

### Post by #&amp;thj^% on 2019-10-11
Humm? Try this:
```
sudo update-alternatives –config x-www-browser
```
should see and select the one you want there.
Also I use this a lot also:
```
sudo update-alternatives --install /usr/bin/x-www-browser x-www-browser /snap/bin/**_chromium_** 200
```
Note this command is for **"chromium" **, I don't use Chrome so I don't know the proper syntax.;)

---

### Post by deadflowr on 2019-10-12
You should just be able to throw this into the address bar
```
chrome://settings/defaultBrowser
```
and set it there.

---

