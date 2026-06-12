---
title: "idle-dim-time"
date: 2013-02-06
forum: Ubuntu Development Version
---

### Post by zika on 2013-02-06
```
Processing triggers for libglib2.0-0:amd64 ...
No such key `idle-dim-time' in schema `org.gnome.settings-daemon.plugins.power' as specified in override file `/usr/share/glib-2.0/schemas/10_ubuntu-settings.gschema.override'; ignoring override for this key.

```
I've just comment-ed out that line in aforementioned file... Wrong?

---

### Post by dino99 on 2013-02-06
dconf is missing lot of schemas here too on i386; simply meaning settings are hardcoded  :( or not yet upgraded (or purged)

---

### Post by jbicha on 2013-02-06
That warning is harmless so there's no need to comment it out. gnome-settings-daemon 3.7.5 (as seen in the GNOME3 Staging PPA) dropped that key so the Ubuntu default override won't do anything.

---

### Post by ft_ on 2013-02-06
Not the same issue but somewhat related :

Since some weeks, my screen does not follow the idle-dim-time at all, the luminosity is always the same. What could be the cause ?
(video : Intel HD3000)

Thanks !

---

