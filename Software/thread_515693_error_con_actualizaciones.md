---
title: "error con actualizaciones"
date: 2007-08-02
forum: Software
---

### Post by aceki on 2007-08-02
Gente consulta cuando en ubuntu (gnome), me dice que tengo actualizaciones pendiente, estro me dice cuales hay,  le doy instalar actualizaciones y me sale un carte que dice:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Y me vuelve a la pantalla anterior y no me instala nada, parece que el dpkg esta corrupto, puede ser? como lo soluciono

---

### Post by aceki on 2007-08-02
Gente ya lo soluciones en una consola puse;

sudo dpkg --configure -a

Creo que lo que hace es reconfigrar el dpkg, asi que al que le pase ya tiene esta solucion.

---

### Post by facundocorradini on 2007-08-02
Efectivamente, este "error" ocurre cuando hay un paquete corrupto. Probablemente hayas tenido algun error al instalar algun software.
En realidad el sistema te está impidiendo instalar cosas adicionales para evitar un error mas grave.

Esto se corrige, como bien dice el mismo mensaje, mediante 
sudo dpkg --configure -a

Aunque la mayoría de las veces basta con entrar al sinaptic, aplicar el filtro de "rotos" y  marcar para desinstalar los paquetes corruptos.

---

### Post by Amatista on 2008-09-27
Gracias por la ayuda que he recibido de la comunidad Linux.

tengo otra question.

a donde debo dirigirme para configurar el dpkg y/o como uso la funcion de 
"sudo"

---

### Post by faktorqm on 2008-09-28
aplicaciones -> accesorios -> terminal

---

