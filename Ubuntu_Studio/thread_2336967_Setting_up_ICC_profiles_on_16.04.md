---
title: "Setting up ICC profiles on 16.04"
date: 2016-09-13
forum: Ubuntu Studio
---

### Post by hannu2 on 2016-09-13
After upgrading from 14.04 to 16.04 I realized that I cannot load my ICC profiles for my displays. I created the profiles with *DisplayCAL* on Trusty and now when I try to use it for applying the profiles again, it reports on failed import. On the next pop up it reports that the profile has been installed, but may have problems.

```
colord: The profile has been imported. You may need to manually assign and activate it under "Color" System settings.

Profile loader: OK
```

I've seen the advice of using the *System Settings* -> *Color* on various forum posts but I cannot find it from my own computer. There is only "*Display Calibration*" on the *System Settings* tray but I don't own calibration device. Using *Profile Loader* gives me:

```
Calibration curves could not be loaded.
```

Ubuntu Software Center shows that I have both *ICC Profile Installer (gnome-color-manager)* and* Color (gnome-color-manager)* installed. But where do I find or how can I run this "Color"? Or should I install some other program?

---

