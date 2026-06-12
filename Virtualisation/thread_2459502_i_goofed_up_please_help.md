---
title: "i goofed up please help"
date: 2021-03-20
forum: Virtualisation
---

### Post by debiscuit on 2021-03-20
i am new to Ubuntu and i tried to use xen, however when i restarted my pc it moved to only console(tty's).  does anyone know how to get it back to graphic mode?(focal fossa lts is the version)

---

### Post by wildmanne39 on 2021-03-20
Moved to the virtualisation forum

---

### Post by debiscuit on 2021-03-20
but i dont know what to do

---

### Post by The Cog on 2021-03-20
If it's just that the GUI is running behind the scenes and you need to switch back to it, try Alt+F7 (or Alt+F1, Alt+F2 - I think they may have moved it recently). 
If it's not there on one of the other consoles, then try to restart the desktop manager. It's probably gdm or lightdm, so try one of these two commands:
```
sudo systemctl restart gdm
sudo systemctl restart lightdm
```
Beyond that, I'd be stuck myself.

---

### Post by deadflowr on 2021-03-20
> **The Cog said:**
> If it's just that the GUI is running behind the scenes and you need to switch back to it, try Alt+F7 (or Alt+F1, Alt+F2 - I think they may have moved it recently). 
If it's not there on one of the other consoles, then try to restart the desktop manager. It's probably gdm or lightdm, so try one of these two commands:
```
sudo systemctl restart gdm
sudo systemctl restart lightdm
```
Beyond that, I'd be stuck myself.

That should be how to do it,
but we might need to know what or how you tried to setup xen, in case something there did something.

---

