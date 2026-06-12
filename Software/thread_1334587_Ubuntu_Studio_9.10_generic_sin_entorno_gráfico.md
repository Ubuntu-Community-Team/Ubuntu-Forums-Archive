---
title: "Ubuntu Studio 9.10 generic sin entorno gráfico"
date: 2009-11-22
forum: Software
---

### Post by cordaxter2.0 on 2009-11-22
Hola de nuevo. 
He actualizado UbuntuStudio de 9.04 a 9.10. Aún no sé si cometí un error al permitir que desinstalara todos las aplicaciones obsoletas. 
El problema es que en el Grub ahora solo me dejó dos opciones:
[B]ubuntustudio 9.10 generic
ubuntustudio 9.10 rt[/B]
además de XP.
No recuerdo el número de los Kernels, pero eran diferentes entre sí. Ahora bien, **generic **me abre sin entorno gráfico y **rt **me inicia correctamente.

He buscado información y encontré esto: **[http://www.tuxapuntes.com/drupal/taxonomy/term/9](http://www.tuxapuntes.com/drupal/taxonomy/term/9)**
 No sé si aplicarlo en generic o no, por el hecho de que en rt sí me reconoce la Nvidia. 

Si alguien puede explicarme qué es lo que pudo haber pasado, se lo agradezco.
No aseguro contestar enseguida debido a que también me desinstaló el wvdial y estoy sin internet en ubuntu. Pero estoy por solucionarlo, espero.

muchas gracias...

---

### Post by cordaxter2.0 on 2009-11-22
Esto es lo que aparece cuando se inicia ubuntustudio generic:

Udevd [2421]: inotify_add_watch (6, (null), 10) failed: Bad address

Udevd [2421]: inotify_add_watch (6, (null), 10) failed: Bad address

Udevd [2421]: inotify_add_watch (6, (null), 10) failed: Bad address

Udevd [2421]: inotify_add_watch (6, (null), 10) failed: Bad address

Udevd [2421]: inotify_add_watch (6, (null), 10) failed: Bad address

Udevd [2421]: inotify_add_watch (6, (null), 10) failed: Bad address

fsck from util-linux-ng 2.16
/dev/sda2:clean, 200025/14360576 files, 12838190/57440407 blocks.

*Preparing restricted drivers...
*starting AppArmor profiles
*starting the winbind daemon winbind
*Setting up ALSA
*Starting Common Unix Printing System: cupsd
[COLOR=Orange]*[/COLOR]Pulse Audio configured for per-user session
*Enabling additional executable binary formats binfmt-support
*Checking battery state...
...done
*Starting TiMidity++ ALSA midi emulation...

---

### Post by cordaxter2.0 on 2009-11-26
Paso las versiones de Kernel:

ubuntu 9.10 kernel 2.6.31-9-rt
ubuntu 9.10 kernel 2.6.27-14-generic

Se presentan en ese orden.

---

### Post by guillermolisi on 2009-11-26
> **cordaxter2.0 said:**
> Paso las versiones de Kernel:

ubuntu 9.10 kernel 2.6.31-9-rt
ubuntu 9.10 kernel 2.6.27-14-generic

Se presentan en ese orden.
El kernel adecuado para Ubuntu Studio es el primero de esa lista porque es Real Time.

---

### Post by cordaxter2.0 on 2009-12-01
Sí, eso tengo entendido, sobretodo para el tema del audio. Que de hecho no uso mucho.
Hubo nuevos sucesos. Abrí el gestor de actualizaciones, el cual me decía que faltaban descargar paquetes y que la última actualización fue parcial. Actualicé, reinicié, pero opté por elegir "generic", el cual inicio correctamente. Por cuestiones de tiempo no pude hacer mucho más, hasta hoy, que inició, pero esta vez sin sonido. Decidí reiniciar y nuevamente volvimos a la pantalla del principio. Otra vez estoy sin entorno gráfico. 
También he probado la guía que publiqué en el post #1, pero al ejecutar el comando:                    **sudo dpkg-reconfigure xserver-xorg**, me lo acepta, pero no se abre ningún asistente. 
Ya no sé que hacer, supongo que reinstalar...

---

### Post by guillermolisi on 2009-12-01
> **cordaxter2.0 said:**
> Sí, eso tengo entendido, sobretodo para el tema del audio. Que de hecho no uso mucho.
Hubo nuevos sucesos. Abrí el gestor de actualizaciones, el cual me decía que faltaban descargar paquetes y que la última actualización fue parcial. Actualicé, reinicié, pero opté por elegir "generic", el cual inicio correctamente. Por cuestiones de tiempo no pude hacer mucho más, hasta hoy, que inició, pero esta vez sin sonido. Decidí reiniciar y nuevamente volvimos a la pantalla del principio. Otra vez estoy sin entorno gráfico. 
También he probado la guía que publiqué en el post #1, pero al ejecutar el comando:                    **sudo dpkg-reconfigure xserver-xorg**, me lo acepta, pero no se abre ningún asistente. 
Ya no sé que hacer, supongo que reinstalar...
Quede mareado :)
No se con que kernel tenes video y con cual audio.

De todas formas, inicia con el kernel que tiene inconvenientes con el entorno grafico.
Con Ctrl+Alt+F1 vas a una consola, inicia sesion/login y edita (con nano o cualquier editor que sea de tu comodidad) el archivo xorg.conf:
```
sudo nano /etc/X11/xorg.conf
```

Tenes que ubicar un bloque _similar_ a este:
```
Section "Device"
        Identifier     "nVidia Corporation NV44 [GeForce 6200 TurboCache(TM)]"
        VendorName     "NVIDIA"
        BoardName      "NVIDIA GeForce 6 Series"
        BusID          "PCI:2:0:0"
        Screen          0
        [COLOR=Blue]Driver  "nvidia"[/COLOR]
        Option  "NoLogo"        "True"
EndSection
``` 
Reemplaza "nvidia" por "vesa" en la linea que destaque en color azul.

Guarda los cambios y reinicia.

Una vez que tengas activo el entorno grafico (sin aceleracion y con pobre resolucion), activas el driver de la placa y volve a reiniciar para comentar luego como te fue.

Si no tenes ese bloque en el archivo mencionado, podes copiar este:
```
Section "Device"
        Identifier     "Device"
        Screen          0
        Driver  "vesa"
EndSection
```

---

### Post by cordaxter2.0 on 2009-12-01
Ok! Creo que Envy NG me explicó cual es el problema. Por alguna extraña razón, no tengo instalado [B]linux-headers-generic.
[/B]
Ocurrió esto: En una de esas tantas veces que reinicie, entre en el kernel generic e inicio correctamente, sin hacer lo que tú (guillermo) me dijiste, ya que todavía no lo había leído. Decidí instalar el driver nvidia con envy ng a través de la terminal. Esta fue su respuesta: 

[B]EnvyNG has detected that the headers for you kernel are missing and cannot be installed.

[/B]Abrí synaptic, busqué linux headers, y descubrí que sólo tengo instalado el linux-headers-rt y su versión de kernel rt.
 Así que instalaré linux-headers-generic y veré que pasa...

Te parece?

---

### Post by guillermolisi on 2009-12-01
> **cordaxter2.0 said:**
> Ok! Creo que Envy NG me explicó cual es el problema. Por alguna extraña razón, no tengo instalado [B]linux-headers-generic.
[/B]
Ocurrió esto: En una de esas tantas veces que reinicie, entre en el kernel generic e inicio correctamente, sin hacer lo que tú (guillermo) me dijiste, ya que todavía no lo había leído. Decidí instalar el driver nvidia con envy ng a través de la terminal. Esta fue su respuesta: 

[B]EnvyNG has detected that the headers for you kernel are missing and cannot be installed.

[/B]Abrí synaptic, busqué linux headers, y descubrí que sólo tengo instalado el linux-headers-rt y su versión de kernel rt.
 Así que instalaré linux-headers-generic y veré que pasa...

Te parece?
Totalmente de acuerdo ! Conta como te resulto !

---

### Post by cordaxter2.0 on 2009-12-01
instalé linux-headers-generic versión 2.6.31.15.28. Lo raro que al reiniciar, no me aparece en el grub ese kernel, si no el viejo y problemático 2.6.27.14. Intenté actualizar, por las dudas, pero el gestor me dice que ya está actualizado. Eso sí, tengo entorno gráfico. 
Otra cosa extraña, que no sé si tendrá algo que ver, es que no tengo instalado grub2, que en teoría venía por defecto con esta nueva distribución.

---

### Post by guillermolisi on 2009-12-01
> **cordaxter2.0 said:**
> instalé linux-headers-generic versión 2.6.31.15.28. Lo raro que al reiniciar, no me aparece en el grub ese kernel, si no el viejo y problemático 2.6.27.14. Intenté actualizar, por las dudas, pero el gestor me dice que ya está actualizado. Eso sí, tengo entorno gráfico. 
Otra cosa extraña, que no sé si tendrá algo que ver, es que no tengo instalado grub2, que en teoría venía por defecto con esta nueva distribución.
Deberias haber instalado los headers del kernel que estabas usando, no una version mas nueva porque esa actualizacion conviene hacerla con un update via Synaptic (te cambia el kernel y resto de paquetes instalados).

Si el tema del thread esta resuelto, marcalo por favor como SOLVED.

Si queres hacer mas consultas que no tengan que ver con el asunto de este hilo, hacelas en otro aparte (siempre que ya no exista uno generado con anterioridad sobre el mismo tema de tu consulta).

---

### Post by cordaxter2.0 on 2009-12-01
El kernel anterior (2.6.27.14) no me aparece en synaptic. De todas formas lo daré como resuelto. En todo caso si surgen problemas, hago un nuevo thread.

Muchas gracias

---

