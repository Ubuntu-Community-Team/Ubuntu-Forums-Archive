---
title: "Administrador de Dispositivos"
date: 2008-07-25
forum: Software
---

### Post by h9005 on 2008-07-25
Tengo ubuntu 8.04 y no encuentro desde donde ver todos los dispositivos de hardware.

---

### Post by sdennie on 2008-07-26
Lo mas fácil es usar lshw.  Por ejemplo:

```

sudo lshw -html > hardware.html

```

Y después podés ver "hardware.html" en FireFox.

---

