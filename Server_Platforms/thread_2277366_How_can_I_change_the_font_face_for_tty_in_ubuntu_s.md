---
title: "How can I change the font face for tty in ubuntu server?"
date: 2015-05-08
forum: Server Platforms
---

### Post by mikcho2 on 2015-05-08
Can I change it to powerline font?

---

### Post by slickymaster on 2015-05-08
Hi mikcho2, welcome to the forums.

To adjust the font/font-size used for the TTY, run the following:```
sudo dpkg-reconfigure console-setup
```and then you will be guided through the steps to choose a font and font-size.

The new settings will be effective after reboot. To apply immediately, just run```
setupcon
```

---

