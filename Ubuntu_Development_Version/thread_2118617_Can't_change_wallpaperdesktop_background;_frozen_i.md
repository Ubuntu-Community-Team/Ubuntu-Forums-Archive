---
title: "Can't change wallpaper/desktop background; frozen image of lightdm appears instead"
date: 2013-02-21
forum: Ubuntu Development Version
---

### Post by ClyN3il on 2013-02-21
As stated in the title... An image of the lightdm login screen appears in place of whatever wallpaper I choose. See attached image. What's this about?

PS: This has happened consistently every time I have tried to use Raring, including the first time I upgraded, and then when I upgraded again after doing a fresh install of 12.10.

---

### Post by deadflowr on 2013-02-21
It's a known issue.
Look at mc4man's post for a useful workaround atm.

[http://ubuntuforums.org/showthread.php?t=2115074]("http://ubuntuforums.org/showthread.php?t=2115074")

---

### Post by ClyN3il on 2013-02-21
Thanks! I wasn't sure if that issue was the same as mine because of the way the other post was phrased.

For anyone else who needs to know, the fix is:

```
gsettings set org.gnome.settings-daemon.plugins.background active true
```

---

