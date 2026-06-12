---
title: "[SOLVED] Nueva particion que no puede usar totalmente"
date: 2009-08-22
forum: Software
---

### Post by xc36e on 2009-08-22
Hola 
Bueno el tema es que el otro dia cree una nueva particion ext4 y no puedo copiarle nada adentro (a menos q entre como root). Entonces. ¿Como hago para que esa particion sea mia y no del root? Cosa de usarla como se me antoje, para meterle lo que quiera sin necesidad de ser root.

Bueno muchas gracias . Saludos

---

### Post by gmunioz on 2009-08-22
Hola xc3.....:

Suponiendo que tu partición se monta en:

/media/particion_nueva

Debes darle permisos de lectura escritura

por todos, esto lo haces con el comando chmod

man chmod, te dirá lo que hace.

El comando sería, en tu caso:

[HTML]sudo chmod -Rf 777 /media/particion_nueva[/HTML]

**Cambia /media/particion_nueva, por lo que corresponde**

---

### Post by Hei Ku on 2009-08-22
de esa manera la haces abierta para todos , no solo para un usuario

sudo chown usuario:usuario -R /media/particion_nueva

---

### Post by xc36e on 2009-08-24
Okey muchas gracias asunto resuelto : )

---

