---
title: "Problemas Con la Desinstalacion de Slim"
date: 2008-12-11
forum: Software
---

### Post by NickCis on 2008-12-11
Bueno, tras encontrar la solucion de como hacer que el ubuntu entre directamente en un usuario, desinstale el Slim, mi problema es que lo desinstale usando "sudo aptitude remove slim", y bue ahora la maquina no prende.
Se queda en booteando y deja este mensaje en pantalla "Starting X display manager: slimstart-stop-daemon: Unable to start /usr/bin/slim : No such directory (No such file or directory)
Already running".
Puedo bootear, usando la opcion de recupero y escribiendo startx por consola.

Como puedo solucionar el problema del Slim?

Saludos.

P.D.: Tengo LXDE y Ubuntu 8.04 (Low Memory install), no se si eso tiene algo que ver.

---

### Post by Hei Ku on 2008-12-12
Probaste reinstalar slim?

```

sudo aptitude install slim

```

---

### Post by NickCis on 2008-12-12
Si, osea, probe y vuelve a andar, pero lo que qiero es desinstalar el Slim, no qedarme con el Slim...

Saludos.

---

### Post by Hei Ku on 2008-12-13
Es un componente core. Por qué lo querés eliminar?

---

### Post by NickCis on 2008-12-14
Mira, hice una instalacion de ubuntu, las para "low memory machines", y bue, probe varios manejadores de ventana (openbox, xfce, etc). Y lo usaba para cambiar entre ellos, pero ahora elegi LXDE, desinstale los demas, y no veo la nececidad de seguir teniendo el slim.
Ensima, no me detecta bien el LXDE, lo que hace qe siempre tire un error, y no puedo hacer que entre directamente a la sesion sin pedir usuario y pass.
Entonces lo le veo el uso de tenerlo, solo hace que la maquina tarde mas en iniciar el linux.

Alguien tiene idea de como sacarlo, y que la computadora siga funcionando?

Saludos.

---

### Post by andy_91 on 2008-12-14
instale ubuntu lite que ya viene con LXDE, capaz eso te soluciona el problema

---

### Post by NickCis on 2008-12-14
mmm,,, buena opcion, pero tendria que formatear la pc...
Me parece que intentar de conseguir mas ram para esta pc, es una Compaq Presario 5473, el 2000, apenas tiene 128mb. :S
Si consigo las dos memorias de 256mb, voy a probar Xubuntu o Ubuntu.

Saludos.

---

