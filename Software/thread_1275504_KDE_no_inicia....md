---
title: "KDE no inicia..."
date: 2009-09-25
forum: Software
---

### Post by Cajuma on 2009-09-25
Hola gente:
Definitivamente no tengo feeling con Kde, estuve toqueteando
Cairo, (fue lo ultimo que hice) hoy al mediodía apague la Pc y
ahora quiero iniciar llego al pass y me dice:

> The following installation problem was detected while
trying to start KDE.
No write access to /home/alfredo/.ICEauthority
KDE is unable to start.

Acepto y despues:

> Could not start ksnserver
check your installation.

Alguna sugerencia ?
Gracias.

---

### Post by oktubrer on 2009-09-25
Te diría que primero desde la consola verifiques los permisos de /home/alfredo/.ICEauthority
Por lo menos en mi caso, el owner es mi usuario y el grupo tambien:

```
-rw------- 1 rodrigo rodrigo 1970 2009-09-25 23:25 /home/rodrigo/.ICEauthority
```

Edito:
Por las dudas te paso los pasos:
Desde la pantalla de KDM, o cuando da el error, ALT + CTRL + F1 (o F2, F3, F4, F5, F6) para ir a una terminal virtual.
Te logueas con tu usuario y clave.
Ejecutas:
```

ls -l /home/alfredo/.ICEauthority

```
Si el owner o el grupo es root, habría que cambiarlo a tu usuario, para eso:
```

sudo chown alfredo:alfredo /home/alfredo/.ICEauthority

```

---

### Post by Cajuma on 2009-09-25
Gracias por tu pronta respuesta, cambio de So y veo que
onda, después te cuento.....
Saludos. :)

---

### Post by Cajuma on 2009-09-25
Gracias....

> Si el owner o el grupo es root, habría que cambiarlo a tu usuarioEstaba como alfredo/alfredo, sin embargo ejecute:

```
sudo chown alfredo:alfredo /home/alfredo/.ICEauthority
```Así pude iniciar sesión y acá estoy........
Alguna idea del motivo...
Saludos !!:popcorn:

---

### Post by oktubrer on 2009-09-26
Me alegro que haya resultado, pero la verdad si ya estaba con tu usuario y grupo no tengo idea del motivo.  Cosa e'mandinga.

---

### Post by emiliano_raso on 2009-09-27
A mi me pasó lo mismo una vez que mandé "chmod 777" al home entero para ver que pasaba :-P
Obviamente ese fue 1 de miles de problemas que me generó eso.

---

