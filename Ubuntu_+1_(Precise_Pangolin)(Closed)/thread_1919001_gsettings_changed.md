---
title: "gsettings changed?"
date: 2012-02-02
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by sonicb00m on 2012-02-02
I have a script where I issue some commands with gsettings after a fresh install but they are no longer working

```

gsettings set com.canonical.Unity.Panel systray-whitelist "['all']"
error : 0-7:can not parse as value of type `i'

```

Also, trying to set the launcher no longer has any effect

```

gsettings set com.canonical.Unity.Launcher favorites "['nautilus-home.desktop', 'chromium-browser.desktop', 'thunderbird.desktop', 'pidgin.desktop', 'deluge.desktop', 'filezilla.desktop', 'spotify.desktop', 'virtualbox.desktop', 'geany.desktop','xbmc.desktop']"

```

Looking in dconf-editor, the schemas are the same as before.

---

### Post by mc4man on 2012-02-02
It appears that all settings that use [] can't be edited from gsettings, everything else is ok here

[https://bugs.launchpad.net/ubuntu/+source/glib2.0/+bug/925382](https://bugs.launchpad.net/ubuntu/+source/glib2.0/+bug/925382)

---

### Post by sonicb00m on 2012-02-02
so typical!

---

### Post by MacUntu on 2012-02-02
> **sonicb00m said:**
> so typical!
Yes, the existence of bugs *is* typical for the alpha phase of software development.

---

### Post by MacUntu on 2012-02-02
And [it's fixed](https://bugzilla.gnome.org/show_bug.cgi?id=669253). Typical. ;)

---

### Post by sonicb00m on 2012-02-02
Haha it's typical that I always seem to run into regressions that upset me :P

---

