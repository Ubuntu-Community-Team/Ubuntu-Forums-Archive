---
title: "Restore Ubuntu to default settings (Unity)"
date: 2011-11-10
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by ruinairas on 2011-11-10
I think there should be a quick and easy method to setting Ubuntu to default settings. It's very common for the desktop environment to stop working and it's rather difficult to fix this issue. I think such tool should be placed at the login screen. It should be on the top taskbar labeled (Default Settings).

---

### Post by philinux on 2011-11-10
> **ruinairas said:**
> I think there should be a quick and easy method to setting Ubuntu to default settings. It's very common for the desktop environment to stop working and it's rather difficult to fix this issue. I think such tool should be placed at the login screen. It should be on the top taskbar labeled (Default Settings).

There is.
```
unity --reset
```

---

### Post by JRV on 2011-11-10
Output from:```
unity --help
```

```
  --version         show program's version number and exit
  -h, --help        show this help message and exit
  --advanced-debug  Run unity under debugging to help debugging an issue. /!\
                    Only if devs ask for it.
  --distro          Remove local build if present with default values to
                    return to the package value (this doesn't run unity and
                    need root access)
  --log=LOG         Store log under filename.
  --replace         Run unity /!\ This is for compatibility with other desktop
                    interfaces and acts the same as running unity without
                    --replace
  --reset           Reset the unity profile in compiz and restart it.
  --reset-icons     Reset the default launcher icon.
  -v, --verbose     Get additional debug output from unity.

```

---

### Post by seeker5528 on 2011-11-10
How "default" do you want it?

You could always delete your '~/.local/' and/or '~/.config/' directories (a bit extreme), or some combination of files/directories they contain. 

The previously mentioned 'unity --reset' is the best option if you are just talking about the Unity desktop.

Don't know if there is any'--reset' kind of thing for unity-2d.

Later, Seeker

---

