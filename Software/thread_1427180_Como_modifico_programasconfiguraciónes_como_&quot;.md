---
title: "Como modifico programas/configuraciónes como &quot;desktop user&quot;?"
date: 2010-03-11
forum: Software
---

### Post by atari130xe on 2010-03-11
Gente, hasta ahora nunca me había preguntado lo siguiente:

En mi PC, tengo mi usuario (como administrador) más 2 usuarios más (Mi hna. y mi sobrino para cuando me visitan).

Eh aquí que hace un momento accedí a los 2 usuarios "Desktop user" para configurar los programas y el aspecto de cada sesión y me encontré con el impedimento (lógico) de no poder por ejemplo, hacer lo siguiente: Instalé la última version de Firefox 3.6 y tiene un pequeño inconveniente que no accede al plugin Java por lo que hay que hacer una modificación (bug de Java documentado). Al querer hacer esa modificación, no es posible porque los usuarios no tienen privilegios administrativos. Como puedo hacer moficiaciones de esa clase en estos 2 usuarios sin privilegios de administrador?

gracias como siempre!

---

### Post by juancarlospaco on 2010-03-11
**man su**

---

### Post by atari130xe on 2010-03-11
Solucionado:
```
su (nombre del usuario con privilegios de administrador) y el comando a ejecutar 
```

Gracias!

PD: Siempre se aprende algo nuevo (por más "tonto" que parezca...):p

---

