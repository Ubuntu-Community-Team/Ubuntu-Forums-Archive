---
title: "Instalar shell script cada vez que arranque el SO"
date: 2009-09-01
forum: Software
---

### Post by Kernel Loco on 2009-09-01
Hola,
La cosa es que diseñé un shell script para modificar un par de cosas del sistema, y ahora quiero que arranque automáticamente cada vez que se inicie Ubuntu. Porque según tengo entendido, siempre que suspendes o apagas la máquina, todos los sh que estaban corriendo son borrados de la memoria. La verdad que no sé mucho de este asunto.
Gracias por su ayuda.

---

### Post by josecuervo86 on 2009-09-01
y si pones el path a tu script en Aplicaciones al inicio? (Sistema > Preferencias > Aplicaciones al inicio)

---

### Post by pablo.s on 2009-09-01
Lo tenés que agregar al
rc que quieras y se va
a ejecutar en el init.
Hay que anteponerle @S

---

### Post by juancarlospaco on 2009-09-01
Depende si sea del espacio de usuario o del lado del sistema,
puede ser con "aplicaciones al inicio", 
sino con un run-level o un Cron

---

### Post by Kernel Loco on 2009-09-02
Ya probé lo que dijo [josecuervo86]("http://ubuntuforums.org/member.php?u=695699") y no funciona. Cuando reinicio la máquina, puedo ver al sh "Durmiendo" en el monitor de procesos. Es decir, no se ejecuta nunca.
Lo que recomendaron [pablo.s]("http://ubuntuforums.org/member.php?u=610217") y [juancarlospaco]("http://ubuntuforums.org/member.php?u=784640") no lo pude entender. ¿Que es "rc"? ¿Donde lo encuentro?
Gracias.

---

### Post by pablo.s on 2009-09-02
[Aqui hay]("http://www.guia-ubuntu.org/index.php?title=Runlevel") [más información]("http://es.wikipedia.org/wiki/Nivel_de_ejecuci%C3%B3n")
[acerca de]("http://www.debianadmin.com/debian-and-ubuntu-linux-run-levels.html") [los runlevels]("http://ubuntu-unleashed.com/tag/ubuntu-runlevels").

---

### Post by Kernel Loco on 2009-09-03
Gracias Pablo,
está bien si meto el script adentro de *rc.local*? ¿Por qué hay que anteponerle @S?

---

### Post by pablo.s on 2009-09-03
Te aconsejaria que lo
apuntes dentro de rc5.d
que es el runlevel de la
GUI.
Hay que anteponerle
@S para que lo ejecute
y @K para que no lo 
ejecute. O sea, cuando
no lo necesites ejecutar
nunca más le anteponés
@K.

---

### Post by Kernel Loco on 2009-09-04
10 puntos, funciona a la perfección.
Muchas gracias gente.

---

