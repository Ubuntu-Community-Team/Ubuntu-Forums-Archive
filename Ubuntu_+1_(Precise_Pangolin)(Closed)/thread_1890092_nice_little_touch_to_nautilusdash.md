---
title: "nice little touch to nautilus/dash"
date: 2011-12-02
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by mc4man on 2011-12-02
If you wish to open the directory of a file listed in the Dash then you can now drag the file over to the launcher & drop on to the highlighted  Home Folder icon. Enabled in latest nautilus

May show up in 11.10, see a note about oneiric-propsed though not available yet.

Quite a simple change, so for 11.10 just change the Exec= line in nautilus-home.desktop to 
```
Exec=nautilus %U
```

If using a custom one then change there..

Edit: you can do multiple files/nautilus windows & or switch back & forth from nautilus window(s) & the Dash by clicking on either the Dash or Home Folder icons., the Dash initially stays open

---

