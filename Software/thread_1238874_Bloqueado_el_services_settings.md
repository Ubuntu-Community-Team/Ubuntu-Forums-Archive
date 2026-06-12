---
title: "Bloqueado el services settings"
date: 2009-08-12
forum: Software
---

### Post by capcabgue on 2009-08-12
Hola a todos:

Cometí un error más o menos grave y no he podido solucionarlo.
Les cuento estaba eliminando unos servicios que se inician (apache y sql) bueno y por error hice click en "**graphical login manager (gdm)"** se me terminó la interfaz grafica y desde la pantalla de inicio (negra con letras, como si fuera una gran terminal)después de mucho buscar hice un dpkg reconfigure xorg algo, luego hice startx.
Con esto logré recuperar la interfaz gráfica, pero no puedo reiniciar definitivamente la interfaz, si me meto al services settings no lo puedo "unlock", esta deshabilitado.
Alguien me puede ayudar para decir que hacer o como solucionarlo.
Tengo un Notebook dell 1525 inspiron con ubuntu 9.04.

Gracias.

---

### Post by Carlos C on 2009-08-13
Movido a software.

---

### Post by moreback on 2009-08-13
Creo que puedes volverlo a su estado anterior con los siguientes comandos de consola:

```
sudo update-rc.d gdm start 30 2 3 4 5
sudo update-rc.d gdm stop 01 0 1 6
```

Saludos.

---

