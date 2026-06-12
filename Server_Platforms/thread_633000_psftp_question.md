---
title: "psftp question"
date: 2007-12-06
forum: Server Platforms
---

### Post by e1ektrob0y on 2007-12-06
what am i doing wrong here?
```

psftp> lpwd
Current local directory is C:\Program Files\PuTTY
psftp> lcd C:\Program Files\Mozilla Firefox
lcd: unable to change directory: The system cannot find the file specified.
psftp>

```
how do i change the lwd?

---

### Post by e1ektrob0y on 2007-12-07
Anyone?

---

### Post by p_quarles on 2007-12-07
Never used this program, but a search for it indicates that it uses SSH as a backend. Like most *nix shells, it probably doesn't support spaces in file paths. You can escape the spaces by using either:
```
lcd "C:\Program Files\Mozilla Firefox"
```
or
```
lcd C:\Program\ Files\Mozilla\ Firefox
```

---

