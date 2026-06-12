---
title: "Ubuntu no arranca"
date: 2010-03-24
forum: Software
---

### Post by Camilow on 2010-03-24
Los molesto para pedirles ayuda. Estoy medio asustado, tanto que no revisé si existe algún otro post sobre este problema. 

Tengo (o solía tener) Ubuntu 9.10 64 bits (ahorita les escribo desde la partición con windows del mismo PC). De un día a otro ocurrió el problema. Aparece al principio como si estubiera cargando correctamente, mostrando el logo y todo. Cuando viene la hora de mostrar el escritorio la pantalla se vuelve negra, mostrando sólo el cursor. Despues de unos segundos aparece un mensaje de error que dice:

> Ha ocurrido un error mientras cargaba o guardaba la información de configuración de evolution-alarm-notify. Puede que alguno de sus ajustes de configuración no funcione adecuadamente.El aviso muestra una ventana de detalle que dice:

> Falló al conectar con el servidor de configuraciones; alguna de las posibles causas son que necesite activar TCP/IP en ORBit, o que tiene bloqueos de NFS debido a una caída de sistema. Consulte [http://www.gnome.org/projects/gconf/](http://www.gnome.org/projects/gconf/) para más información. (Detalle - 1 : No se pudo enviar un mensaje al demonio de GConf: Message did not recive a reply (timeout by message bus)).Luego de aceptar el mensaje puedo esperar todos los minutos que sean y el sistema no arranca. Por favor, no quisiera perder lo que tengo en esa partición y tener que formatear. No tengo idea qué hacer sin acceder al sistema.

Muchas gracias y saludos.

---

### Post by Carlos C on 2010-03-24
Puedes intentar entrar en recovey mode:

[https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode)

El sistema iniciará una sesión sin entorno gráfico. Te sugiero ver los mensajes del sistema con el comando "dmesg" para ver si encuentras más información. Si no ves nada de utilidad puedes desinstalar evolution:
```
sudo apt-get remove evolution
```Después lo vuelves a instalar, la idea es ver si es ese programa el culpable (recuerda primero consultar los mensajes del sistema).

También puedes borrar los archivos de configuración en tu /tmp:

/tmp/gconfd-usuario
/tmp/mapping-usuario
 /tmp/orbit-usuario
etc.

Por último, siempre es posible acceder a la información en el disco duro desde el LiveCD, de esa manera se puede recuperar y respaldar tus datos en caso de que el sistema esté muy dañado.

Saludos.

---

### Post by Camilow on 2010-03-24
Pedí los mensajes del sistema, que es una lista larguísima, y no pude interpretar nada útil. Desinstalé y reinstalé evolution, Busque los rachivos en /tmp, pero no existen, /tmp está vacío (excepto por los archivos ocultos, que niguno era de esos listados). Pero finalmente nada cambió, sólo que ahora no me sale el mensaje de error, simplemente muestra la pantalla negra.:confused: 

Existe un comando que repare el disco o los archivos sensibles o algo así?... intenté verificar la integridad del disco con fsck, pero para eso debo desmontar el disco, y hay no se qué procesos que están usando el disco y no puedo desmontar. Este comando lo encontré en un manual por ahí, no es que yo sea un experto.

Creo que tendré que recuperar con live CD y formatear... Espero alguna otra ayudita. Gracias. Saludos.

---

### Post by Carlos C on 2010-03-24
Para utilizar fsck tienes que iniciar desde el LiveCD, porque el disco no debe estar montado. Desde ahí corres los comandos:

[http://blockdeubuntu.blogspot.com/2009/01/escaneando-el-sistema-de-archivos-de.html](http://blockdeubuntu.blogspot.com/2009/01/escaneando-el-sistema-de-archivos-de.html)

Si eso no resulta también puedes eliminar los archivos de configuración en tu home. Puedes hacerlo desde nautilus si tienes seleccionada la opción "Mostrar los archivos ocultos".

Y si, el tmp está vacío jaja, mi error, quería decir el home.

---

### Post by CdK1 on 2010-03-24
Más fácil, crea un usuario, entra con ese usuario, si puedes entrar, entonces borrar los mismos archivos que te dijo Carlos_C pero en tú $HOME...

---

### Post by moreback on 2010-03-24
Por alguna razón el demonio de gconf-2 se está cayendo, a lo mejor tienes algun archivo dañado dentro de tu ~/.gconf

Saludos.

---

### Post by Camilow on 2010-03-24
gracias a todos por intentar ayudarme.

ocurre que ingresé con otro usuario, pero no me da autorización para ver las carpetas .gconf o gconfd. Y como root desde el modo recovery no encontré los archivos o no se que archivos borrar.

¿Como puedo hacer para correr los comandos de e2fsck desde el liveCD? resulta que tengo 2 discos, uno con ubuntu y otro con window. cuando ingreso con liveCD pido info sobre las particiones y me muestra las que genera el liveCD en la memoria. No se como llamar a la partición sobre la que quiero correr el e2fsck.

gracias y saludos

---

### Post by Carlos C on 2010-03-29
Arranca con el LiveCD y escribe en el terminal:
```
sudo fdisk -l
```
y copia acá lo que te aparece.

Saludos.

---

### Post by Camilow on 2010-04-02
Gracias Carlos, pero la verdad que ya formateé.

---

