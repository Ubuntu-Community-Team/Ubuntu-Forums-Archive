---
title: "Compiz dejó de arrancar al inicio - Lucid Lynx"
date: 2010-07-15
forum: Software
---

### Post by Peter Smile on 2010-07-15
Muchachos, la verdad es que estoy muy confundido y espero que uds. puedan ayudarme porque ya intenté todo lo que se me ocurrió y sigo sin resolver el problema.

La cosa es que de la noche a la mañana (literalmente) compiz dejó de arrancar al inicio (me quedo sin gestor de ventanas alguno). Si lo ejecuto (ya sea con "compiz &" o "compiz --replace &" desde la terminal) funciona pero deja de andar cuando cierro la terminal; si en cambio lo ejecuto desde el dialogo "ejecutar aplicación" (apretando alt+F2) también arranca pero por unos segundos y luego vuelvo a estar como antes (sin gestor de ventanas). Ahora viene lo que encuentro más extraño: si hago click derecho en el escritorio y elijo "activar los efectos visuales" compiz arranca sin problemas (con la configuración por defecto, claro). Pero vuelvo a tener el mismo problema al reiniciar la sesión.

Ya probé desistalando compiz y volviendo a instalarlo previa purga y autoclean pero nada. Intenté que arrancara desde "aplicaciones al inicio" y tampoco obtuve resultados positivos.

Lo único que pudo causar algún problema es que ayer hice una actualización ("sudo apt-get update && sudo apt-get upgrade"). Tal vez alguno de los paquetes se ha actualizado y me está generando algún problema, no lo sé.

Por las dudas les muestro la salida del siguiente comando: ```
$grep -i ppa.launchpad.net /etc/apt/sources.list.d/*.list | sed -e 's/\/etc\/apt\/sources.list.d\///'


am-monkeyd-nautilus-elementary-ppa-lucid.list:deb http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu lucid main
bisigi-ppa-lucid.list:deb http://ppa.launchpad.net/bisigi/ppa/ubuntu lucid main
b-sides-ppa-lucid.list:deb http://ppa.launchpad.net/b-sides/ppa/ubuntu lucid main
chromium-daily-ppa-lucid.list:deb http://ppa.launchpad.net/chromium-daily/ppa/ubuntu lucid main
c-korn-ppa-lucid.list:deb http://ppa.launchpad.net/c-korn/ppa/ubuntu lucid main
cybolic-ppa-lucid.list:deb http://ppa.launchpad.net/cybolic/ppa/ubuntu lucid main
deluge-team-ppa-lucid.list:deb http://ppa.launchpad.net/deluge-team/ppa/ubuntu lucid main
docky-core-ppa-lucid.list:deb http://ppa.launchpad.net/docky-core/ppa/ubuntu lucid main
docky-core-stable-lucid.list:deb http://ppa.launchpad.net/docky-core/stable/ubuntu lucid main
dylanmccall-ppa-lucid.list:deb http://ppa.launchpad.net/dylanmccall/ppa/ubuntu karmic main
effie-jayx-turpial-lucid.list:deb http://ppa.launchpad.net/effie-jayx/turpial/ubuntu karmic main
ehoover-compholio-lucid.list:deb http://ppa.launchpad.net/ehoover/compholio/ubuntu lucid main
flam3-ppa-lucid.list:deb http://ppa.launchpad.net/flam3/ppa/ubuntu intrepid main
hrickards-lives-lucid.list:deb http://ppa.launchpad.net/hrickards/lives/ubuntu lucid main
jason-scheunemann-ppa-lucid.list:deb http://ppa.launchpad.net/jason-scheunemann/ppa/ubuntu lucid main
moovida-packagers-ppa-lucid.list:deb http://ppa.launchpad.net/moovida-packagers/ppa/ubuntu karmic main
nilarimogard-webupd8-lucid.list:deb http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu lucid main
osd-lyrics-ppa-lucid.list:deb http://ppa.launchpad.net/osd-lyrics/ppa/ubuntu lucid main
pdfmod-team-ppa-lucid.list:deb http://ppa.launchpad.net/pdfmod-team/ppa/ubuntu karmic main
psyke83-ppa-lucid.list:deb http://ppa.launchpad.net/psyke83/ppa/ubuntu lucid main
riccetn-clementine-lucid.list:deb http://ppa.launchpad.net/riccetn/clementine/ubuntu lucid main
shutter-ppa-lucid.list:deb http://ppa.launchpad.net/shutter/ppa/ubuntu lucid main
stellarium-stellarium-releases-lucid.list:deb http://ppa.launchpad.net/stellarium/stellarium-releases/ubuntu lucid main
telepathy-ppa-lucid.list:deb http://ppa.launchpad.net/telepathy/ppa/ubuntu lucid main
tualatrix-ppa-lucid.list:deb http://ppa.launchpad.net/tualatrix/ppa/ubuntu lucid main
ubuntu-mozilla-daily-ppa-lucid.list:deb http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu lucid main
ubuntu-wine-ppa-lucid.list:deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu lucid main
```

---

### Post by emiliano_raso on 2010-07-16
Es una negrada esto, pero por ahi te falta actualizar algo.

Probá con:
```
sudo aptitude update && sudo aptitude full-upgrade
```

Si podes hacer ALT+F2 entonces tenes activo metacity.

---

### Post by Peter Smile on 2010-07-16
Nopo, dice que no hay nada nuevo que instalar.

```
Inicializando el estado de los paquetes... Hecho
No se instalará, actualizará o eliminará ningún paquete.
0 paquetes actualizados, 0 nuevos instalados, 0 para eliminar y 0 sin actualizar.
Necesito descargar 0B de ficheros. Después de desempaquetar se usarán 0B.
```

---

### Post by Peter Smile on 2010-07-16
Me acabo de dar cuenta de algo que tal vez no tenga nada que ver, pero por las dudas de que sea señal de algo lo posteo:

**Ahora las Xs ya no están en tty7 sino en tty8** (es decir, que para ir a las Xs luego de apretar ctrl + alt + F1 debo apretar ctrl + alt + F8 ).

Esto es cada vez más raro para mis pocos conocimientos.

---

### Post by biale on 2010-07-17
Solo por decir algo y sin mucha claridad...

Fijate que hay muchos ppas y alguno indirectamente puede tener que ver con compiz.

El "Compiz Fusion icon" a lo mejor te tira alguna punta.

Create un usuario nuevo 0 Km y fijate como funciona. Es solo para determinar hasta donde los problema estan a nivel de sistema y hasta adonde estan a nivel de configuración de usuario.

---

### Post by chispa on 2010-10-02
Hola amigo, bueno yo también tengo ese problema y para mas soy novato, pero realice una solución temporal mientras se consigue la falla y la solución de dicho problema.

1) Crea un archivo con gedit compiz.sh
2) Escribes en el "compiz & compiz --replace" sin las comillas
3) Guardas y le das permiso de ejecutar como un programa
4) Le asignas una ubicación que quieras
5) En Sistemas - Preferencias - Aplicaciones de Inicio, lo agregas

con eso lo invocamos el compiz y aplicar el borde de las ventanas al iniciar sesión.

Esta solución la detesto porque no soluciona realmente el problema pero por lo menos la hace menos fastidiosa.

Si consigues una solución real no dejes de portearlo..

Se me olvido decir que esto me paso y formatee 2 veces y volvió a pasar  según unos foros viejos que leí este problema esta asociado a los  drivers de la tarjeta Nvidia's de hecho la mía es una GF 8600 y utilice  los drivers que vienen con Ubuntu y también los de la pagina de Nvidia y  nada de nada. asi que ya que eres mas experto que yo por allí deberías  de andar. Saludos


:lolflag:

---

### Post by chispa on 2010-10-02
no se borrar dios

---

