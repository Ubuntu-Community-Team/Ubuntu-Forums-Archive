---
title: "Lost Home lens in Saucy"
date: 2013-05-19
forum: Ubuntu Development Version
---

### Post by Chanath on 2013-05-19
The Home lens in Saucy had vanished. I tried to redo it using Dconf Editor, but it doesn't appear to respond. Set to default button is greyed out. I have now only Applications and Search icons at the bottom of the Dash. Is there a way to get the Home lens back, and also add more lenses? Thanks!

---

### Post by Chanath on 2013-05-20
Does anyone know how to add lenses to Dash? I tried with Dconf, but doesn't work. Unity Tweak tool also doesn't have a way.

---

### Post by kuvanito on 2013-05-20
ok in dconf go to:
com/unity/dash and type:['applications.lens', 'files.lens', 'music.lens']

---

### Post by grahammechanical on 2013-05-20
There are lens and scopes in the Software Centre. You may find more through Synaptic. Search for unity. But you will not find a Unity Home lens. I have looked. You may need to re-install Unity if this command does not do what you want.

```
unity --reset-icons
```

By the way, it is not long now before we will get the promised 100 scopes

Regards.

---

### Post by Chanath on 2013-05-21
Nothing worked. Uninstalled Unity, but it won't install again. Have to re-install Saucy.
Do you know how to install other lenses in Saucy?

---

