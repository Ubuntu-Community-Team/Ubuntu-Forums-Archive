---
title: "Appindicators disapeared"
date: 2019-10-01
forum: Ubuntu Development Version
---

### Post by mobile-harvey on 2019-10-01
Hi

I am running Eoan having upgraded from Disco. Something has happened to have made the appindicators disappear from the top bar. It looks like the extension isn't running any more as when I log-in to my desktop my Nextcloud Client opens a window instead of just silent appearing in the appindicator area. I'm at a loss as to how to diagnose this and so far have just re-installed the package with no improvement thus:

```
sudo apt install gnome-shell-extension-appindicator --reinstall
```

Any help on diagnosing this would be appreciated.

Thanks
Nick

---

### Post by mobile-harvey on 2019-10-01
Update: I am wrong - Steam and Skype icons appear in the appindicator area but Nextcloud does not. It was working previously! I'll try to figure out what has changed...

---

### Post by mobile-harvey on 2019-10-06
It looks like this is related to this bug: [https://github.com/ubuntu/gnome-shell-extension-appindicator/issues/190](https://github.com/ubuntu/gnome-shell-extension-appindicator/issues/190)

---

