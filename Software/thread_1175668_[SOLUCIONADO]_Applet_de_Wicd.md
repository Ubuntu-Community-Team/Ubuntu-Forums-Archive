---
title: "[SOLUCIONADO] Applet de Wicd"
date: 2009-06-01
forum: Software
---

### Post by Iced_R on 2009-06-01
Holas! 

Estoy configurando un gestor de ventanas (PekWM) para dejarlo como escritorio predeterminado en mi Ubuntu, pero tengo un problema con el applet de Wicd (no sé cómo llamarlo para dejarlo en segundo plano). Alguien podría ayudarme con eso? 

Saludos a todos.

---

### Post by Patriciologico on 2009-06-07
Si tienes Gnome, desactivalo desde el Menu Sistema/Preferencias/Aplicaciones al inicio.

Si eso no sirve, tu gestor de ventanas debe tener un fichero con las aplicaciones ejecutadas al iniciar sesion.

Saludos!

---

### Post by Carlos C on 2009-06-08
Si entiendo bien el problema es que no tienes el applet de wicd, el ícono en el panel que queda cuando cierras la ventana del programa. En Gnome, si lo añades a tus programas que cargan al inicio en Sistema-->Preferencias-->Sesiones, es cosa de añadir el comando:
```
python /opt/wicd/tray.py
```
De esa manera se carga el applet. No estoy familiarizado con PekWM, pero creo que tendrías que ver la manera de utilizar este dato.
Saludos.

---

### Post by Iced_R on 2009-06-08
Gracias por el dato. Precisamente es lo que Carlos C entregó. Es que me dio por ocupar un escritorio distinto a GNOME o KDE, y como estoy trabajando en un humilde water en la universidad, se me ocurrió un gestor de ventanas xD. 

Tengo más dudas acerca de cosas que quiero llamar, pero el problema es que no sé cómo llamarlas. Las posteo aparte, cierto?


Saludos a todos, y gracias por las respuestas.

---

### Post by Carlos C on 2009-06-08
Me alegro que el applet de wicd esté funcionando. Creo que sería lo mejor que las otras dudas las hicieras en threads separados, cada una con un título descriptivo. Y cuando tengas el equipo funcionando a tu pinta no sería malo aportar con un How-to ;)

---

### Post by Patriciologico on 2009-06-09
> **Patriciologico said:**
> Si tienes Gnome, desactivalo desde el Menu Sistema/Preferencias/Aplicaciones al inicio.

Si eso no sirve, tu gestor de ventanas debe tener un fichero con las aplicaciones ejecutadas al iniciar sesion.

Saludos!


Yo había entendido al revés :p

---

