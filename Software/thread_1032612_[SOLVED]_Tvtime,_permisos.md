---
title: "[SOLVED] Tvtime, permisos"
date: 2009-01-06
forum: Software
---

### Post by Applelnx on 2009-01-06
Tengo una duda muy simple (ojala tambien sea asi la solucion).

Cuando quiero abrir el tvtime me dice que tengo acceso denegado. Si lo abro desde la consola poniendo sudo tvtime funciona todo en orden. Hay alguna manera de dar permisos para que se ejecute sin poner la pass? 

Gracias y saludos

---

### Post by sdennie on 2009-01-06
Fijate si sos miembro del grupo video:

```

groups | grep video

```

Si no dice nada, proba:

```

sudo adduser $USER video

```

Despues, tenes que logout y volver y tvtime debe funcionar sin sudo.

---

### Post by Applelnx on 2009-01-06
Gracias, funciono perfecto ;)

---

