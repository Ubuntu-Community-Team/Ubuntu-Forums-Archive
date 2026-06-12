---
title: "Instalar paquetes &quot;no actualizados&quot;"
date: 2009-12-07
forum: Software
---

### Post by guidito73 on 2009-12-07
Bueno, resulta que cuando hago un apt-get upgrade, la consola me informa de

> 0 actualizados, 0 se instalarán, 0 para eliminar y 12 no actualizados.

Ahora, busqué y no pude encontrar cómo actualizarlos!

Alguna ayuda? Gracias :D

---

### Post by luks911 on 2009-12-07
¿No te dice cuáles son los paquetes? ¿Si ejecutás sudo aptitude safe-upgrade no te da algún dato más? ¿Agregaste algún repositorio en forma manual? ¿Qué versión de Ubuntu es?
Es probable que haya versiones más nuevas de esos 12 paquetes pero por la falta de alguna dependencia no se puedan actualizar, entonces los deja así.

---

### Post by guidito73 on 2009-12-07
Gracias luks!

Ese comando me vino justo al pelo. Me listó los paquetes y me da la opción de actualizarlos :D

Solved.

---

