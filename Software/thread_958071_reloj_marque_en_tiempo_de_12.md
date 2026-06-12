---
title: "reloj marque en tiempo de 12"
date: 2008-10-25
forum: Software
---

### Post by tsueseres on 2008-10-25
como hacer para que el reloj marque la hora en 12 osea que si van a ser la 1 no diga 13, 

posdata encontre una opcion para que valla en 12 pero cada vez que reinicio se vuelve a poner ocmo antes

---

### Post by hictio on 2008-10-25
El reloj del Panel? El de arriba en la pantalla?
Probaste haciendo click derecho en la hora, selecciona 'Preferencias' (o como sea en espanol) y selecciona 'Formato de 12 horas'.
Yo lo tengo asi, y en mi caso, no se cambia para nada luego de reboots.

---

### Post by tsueseres on 2008-10-25
> **hictio said:**
> El reloj del Panel? El de arriba en la pantalla?
Probaste haciendo click derecho en la hora, selecciona 'Preferencias' (o como sea en espanol) y selecciona 'Formato de 12 horas'.
Yo lo tengo asi, y en mi caso, no se cambia para nada luego de reboots.

k raro el mio si

---

### Post by valucha on 2008-10-25
[COLOR="DarkOrchid"]Es un bug, no lo podés poner en ese formato, ya lo van a solucionar.[/COLOR]

---

### Post by santiagoward2000 on 2008-10-25
Voy a robarle un post a [vk-cdg]("http://ubuntuforums.org/showthread.php?t=897551&highlight=finos"). PERDON!
Si seguís las instrucciones de esta página: [http://120linux.com/aspecto-reloj-ubuntu/]("http://120linux.com/aspecto-reloj-ubuntu/")
Podés poner que el reloj marque como vos quieras, pero de meter **%H:%M**, ponelo como **%I:%M**.
Así lo tengo en 12 hr (la verdad que no me había dado cuenta que de la otra forma no andaba).
Si querés que te aparezca el AM/PM al final agregás **%p** (para que esté en mayúsculas) o **%P** (minúsculas).
Saludos!

_EDIT:_
Fijate que las opciones que hay entre <> son para cambiar colores y tamaños de letras. Si eso no te interesa no hace falta que lo pongas.

---

### Post by hictio on 2008-10-25
> 
Es un bug, no lo podés poner en ese formato, ya lo van a solucionar.


Sera un problema relacionado con el idioma setteado en Ubuntu?
Yo lo tengo en ingles. y no me esta pasando, acabo de probar con un reboot, y sigue en formato de 12 hrs.

Antes reboot:
[[IMG]http://img366.imageshack.us/img366/9641/hora1200ee2.th.jpg[/IMG]](http://img366.imageshack.us/my.php?image=hora1200ee2.jpg)

Despues reboot:
[[IMG]http://img222.imageshack.us/img222/1631/hora1201ty7.th.jpg[/IMG]](http://img222.imageshack.us/my.php?image=hora1201ty7.jpg)

---

### Post by santiagoward2000 on 2008-10-25
> **hictio said:**
> Sera un problema relacionado con el idioma setteado en Ubuntu?
Yo lo tengo en ingles. y no me esta pasando, acabo de probar con un reboot, y sigue en formato de 12 hrs.

Antes reboot:
[[IMG]http://img366.imageshack.us/img366/9641/hora1200ee2.th.jpg[/IMG]](http://img366.imageshack.us/my.php?image=hora1200ee2.jpg)

Despues reboot:
[[IMG]http://img222.imageshack.us/img222/1631/hora1201ty7.th.jpg[/IMG]](http://img222.imageshack.us/my.php?image=hora1201ty7.jpg)

Puede ser... acabo de desactivar las opciones custom para ver si andaba o no y acá (que lo tengo en inglés) sí lo puedo poner en 12hr.

---

