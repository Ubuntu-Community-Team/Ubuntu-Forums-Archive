---
title: "Jaunty carga demasiado lento"
date: 2009-07-24
forum: Software
---

### Post by donmatas on 2009-07-24
HOlanda:

tengo Jaunty en un easynote Mx456+. Todo funciona muy bien, salvo que se demora muchísimo en arrancar. Se queda pegado unos 5 minutos en la pantalla de carga de ubuntu. Despuès de eso todo bien.

Reinicié en modo seguro y vi que se demoraba en la siguiente línea:

[10.559491] INPUT SYMP5/2 synaptics touchpad as devices/plataform/i842/serie04/INPUT/INPUT9

Cuando terminó de cargar fuimos a ver qué archivo era pero no existía el archivo.

Después desactivé el touchpad y reinicié pero el problema persiste.

¿alguna sugerencia?

salud
DM

---

### Post by moreback on 2009-07-24
El primer indicador en esa línea creo que muestra los segundos transcurridos desde el inicio, a lo mejor no es ese el hardware problemático ¿qué es lo que sale en la línea siguiente? Esto lo ves en /var/log/messages o con dmesg.

Saludos.

---

