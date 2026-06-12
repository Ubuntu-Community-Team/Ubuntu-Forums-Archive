---
title: "Formateando para volver a empezar"
date: 2009-02-25
forum: Software
---

### Post by sirkurt on 2009-02-25
la cosa viene asi, yo era usuario de windows hasta hace unas semanas, entonces decidi provar ubuntu como corresponde y la verdad me parece perfecto y ahora quiero hacerlo mi unico SO, el problema viene por este lado.
Para instalar ubuntu cree una particion desde windows de 20 gigas solamente para probar, ahora lo que quiero hacer es borrar wundows y ubuntu unir las particiones que me quedaron, la de windows de 114 y la de ubuntu de 20 e instalar unicamente ubuntu en esa particion, tambien les aviso que tengo una particion aparte para guardar archivos de unos 100 gigas y esa particion no quiero que se vea afectada para nada.

en resumen lo que busco es un programa o una foma para unir la particion de 20 y la de 114 y volver a instalar ubuntu para poder usarlo de lleno.

---

### Post by santiagoward2000 on 2009-02-25
> **sirkurt said:**
> la cosa viene asi, yo era usuario de windows hasta hace unas semanas, entonces decidi provar ubuntu como corresponde y la verdad me parece perfecto y ahora quiero hacerlo mi unico SO, el problema viene por este lado.
Para instalar ubuntu cree una particion desde windows de 20 gigas solamente para probar, ahora lo que quiero hacer es borrar wundows y ubuntu unir las particiones que me quedaron, la de windows de 114 y la de ubuntu de 20 e instalar unicamente ubuntu en esa particion, tambien les aviso que tengo una particion aparte para guardar archivos de unos 100 gigas y esa particion no quiero que se vea afectada para nada.

en resumen lo que busco es un programa o una foma para unir la particion de 20 y la de 114 y volver a instalar ubuntu para poder usarlo de lleno.

Hola!
La más simple es bootear desde el CD de Ubuntu y abrir GParted (**Sistema > Administración > Editor de Particiones**). Ahí vas a ver una barra que representa tu disco y todas las particiones hechas. Solo seleccioná las que quieras borrar y tocá el botón **Borrar**.
Después, cuando instales, fijate de seleccionar la opción para que use el máximo espacio libre disponible.
Y listo!
Suerte!

---

### Post by sirkurt on 2009-02-25
no tengo esa aplicacion en mi ubuntu, igual cabe destacar que es la version 7.10 actualizada a 8.04 seguramente en las versiones mas nuevas viene incluida en el live cd no?

---

### Post by santiagoward2000 on 2009-02-25
> **sirkurt said:**
> no tengo esa aplicacion en mi ubuntu, igual cabe destacar que es la version 7.10 actualizada a 8.04 seguramente en las versiones mas nuevas viene incluida en el live cd no?

Eh, no te lo instala de fábrica, pero está si booteas desde el LiveCD. Desempolvé mi Xubuntu 7.10 para ver si estaba, y sí. Fijate.
Si no está, abrí una terminal y meté **gksudo gparted**.
Saludos!

---

