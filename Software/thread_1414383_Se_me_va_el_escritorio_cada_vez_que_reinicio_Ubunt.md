---
title: "Se me va el escritorio cada vez que reinicio Ubuntu 9.10"
date: 2010-02-23
forum: Software
---

### Post by Tio Bill on 2010-02-23
Hola a todos, después de un tiempo he vuelto a probar iniciarme en el mundo de Ubuntu con la versión 9.10 con un disco que me enviaron por correo. Esta vez no tuve mayores inconvenientes a la hora de instalar, pero al actualizarlo se me fué la conexion a internet y se conecta cuando quiere, a veces automáticamente, a veces tengo que configurar la conexion dsl.  Y cada vez que reinicio el escritorio desaparece y aparece cuando le doy click al icono del disco donde está instalado Ubuntu. Quisiera saber como hacer para que se conecte automáticamente al iniciar sesión, y como hacer que no se vaya el fondo de escritorio ni los iconos de los discos duros. Gracias de antemano y tengan paciencia con este fanboy de Windows que está incursionando en el mundo de linux. Y si hay que hacer un hilo de cada tema avisenme.

---

### Post by guillermolisi on 2010-02-23
La conexion DSL es via Ethernet o via USB ?
Cuando configuras la conexion DSL, que pasos realizas ?
Normalmente tenes una conexion estable a Internet o es frecuentemente impredecible y a cada rato tenes que resetearla para que el modem se vuelva a conectar (sin importar que sistema estes usando) ?

Luego de haber instalado, actualizaste Ubuntu al dia ?

Que placa de video estas usando ? (marca y modelo)

Podrias darnos mas caracteristicas sobre tu maquina: procesador, cantidad de memoria RAM, espacio en disco asignado a Ubuntu.

---

### Post by Tio Bill on 2010-02-23
Estimado Guillermo, respondo a sus preguntas: La conexión es vía ethernet a través de un modem ZTE zxdsl 831 provisto por mi isp Speedy. Al terminar de instalarse Ubuntu la conexión la hice mediante la terminal con *pppoeconf*, y se conectó sin inconvenientes. Al momento de actualizar (Apenas terminé de instalar Ubuntu) y reiniciar ya no se conectó mas. Luego de un par de reinicios comprobé que a veces si se conectaba aunque el icono de notificación de red aparecía como desactivado. En el administrador de red aparece la conexion cableada con el nombre *ifupdown (ethO)* pero dice Not Managed, con el icono del cable desconectado, y la conexion *dsl* figura como *New PPPoE connection- last used: never*. Y estoy en estos momentos escribiendo desde Ubuntu así que no entiendo. Tengo una conexion de 1Mb estable y nunca se corta a pesar de tener la pc prendida las 24hs. En cuanto a la placa tengo una nVidia GeForce 8800Gs 384mb Alpha Dog Edition a la cual para instalar los drivers tuve que hacerlo con una aplicacion creo que EnvyNG, ya que se instalaba desde el file manager pero al reiniciar no se reconocía. Mi pc es una Pentium D 925 3,00 @ 3,6 Ghz, 2,5 Gb de Ram, mother Asus P5 KPL-AM SE.Dos HD uno de 500Gb con una particion de 40Gb para W7 y el resto para almacenamiento, y otro de 160 con dos particiones, una de 11Gb para Ubuntu y el resto W XP y almacenamiento. Espero su respuesta, estimado.

---

### Post by guillermolisi on 2010-02-23
El Network Manager, el programa que gestiona las conexiones de red y que se ve con ese icono que mencionas, muestra como desconectadas aquellas cuya gestion fue realizada por otro programa o metodo, en este paso pppoe. Mientras tengas conexion no le des mucha importancia a menos que cambies la forma de vincularte con el modem DSL (por ejemplo, convirtiendolo de Bridge a Router con lo cual el discado lo hace el aparato mismo y vos no tenes que hacer nada en la PC).

Con esa placa de video no deberias tener problemas a menos que no hayas activado los drivers privativos de nVidia (cosa que no deberia suceder si usaste EnvyNG, pero lo menciono para que verifiques).

Esa instalacion esta al dia con las actualizaciones, cierto ?

Podrias mostrarnos la salida de la siguiente ejecucion en una consola/terminal ?
```
df -h
```es para saber cuanto espacio libre tenes en cada particion del disco para Ubuntu.

---

### Post by Tio Bill on 2010-02-23
[CENTER]Estimado Guillermo, aqui le dejo lo que me solicitó: [/CENTER]
S.[LEFT]```

ficheros                Tamaño    Usado    Disp   Uso%  Montado en
/dev/sda5               8,5G       4,5G       3,7G  55%    /
udev                       1,3G      252K       1,3G    1%     /dev
none                       1,3G      316K       1,3G    1%     /dev/shm
none                       1,3G        84K       1,3G    1%     /var/run
none                       1,3G          0         1,3G    0%     /var/lock
none                       1,3G          0         1,3G    0%     /lib/init/rw
dermadroid@dermadroid-desktop:~$
``` [/LEFT]
Por otra parte debo decirle que el problema con el escritorio parce haberse solucionado al cambiar a KDE, y mover a la carpeta *home* la imagen que había predefinido como fondo.

---

### Post by guillermolisi on 2010-02-23
> **Tio Bill said:**
> [CENTER]Estimado Guillermo, aqui le dejo lo que me solicitó: [/CENTER]
S.[LEFT]```

ficheros                Tamaño    Usado    Disp   Uso%  Montado en
/dev/sda5               8,5G       4,5G       3,7G  55%    /
udev                       1,3G      252K       1,3G    1%     /dev
none                       1,3G      316K       1,3G    1%     /dev/shm
none                       1,3G        84K       1,3G    1%     /var/run
none                       1,3G          0         1,3G    0%     /var/lock
none                       1,3G          0         1,3G    0%     /lib/init/rw
dermadroid@dermadroid-desktop:~$
``` [/LEFT]
Por otra parte debo decirle que el problema con el escritorio parce haberse solucionado al cambiar a KDE, y mover a la carpeta *home* la imagen que había predefinido como fondo.
Te quedan 3,7Gb en la particion Linux.

Si al hacer lo que hiciste el tema se soluciono algo fuera de lugar tenes en el perfil de sesion de usuario en Gnome que hace se presente esa anomalia.
Si queres seguir usando Gnome mi consejo es que crees un usuario nuevo y veas como funciona, sin tocarle ninguna caracteristica de tema ni fondo de pantalla, nada. Una vez que sepas que esta funcionando bien y estable, ahi comenza a modificar el escritorio pero de a una cosa por vez asi sabes que es lo que lo inestabiliza y podes volver atras facil y rapidamente.

---

### Post by Tio Bill on 2010-02-25
Estimado Guillermo, he decidido quedarme con KDE puesto que me resulta mas agradable estéticamente y se ha solucionado el problema de la desaparición del escritorio.Por otro lado el tema de la conexión es que se conecta en determinadas ocasiones. Por ej la primera vez que inicio Ubuntu no se conecta, si reinicio si se conecta, ya probé reiniciar tres veces y se conecta automáticamente. El problema es al arrancar la primera vez. ¿Habrá una solución al problema? Por otro lado les cuento que me está gustando cada vez mas el entorno de Ubuntu (ahora Kubuntu puesto que instale el paquete de KDE) y estoy ansioso por aprender mas al respecto. Saludos.

---

### Post by guillermolisi on 2010-02-25
> **Tio Bill said:**
> Estimado Guillermo, he decidido quedarme con KDE puesto que me resulta mas agradable estéticamente y se ha solucionado el problema de la desaparición del escritorio.Por otro lado el tema de la conexión es que se conecta en determinadas ocasiones. Por ej la primera vez que inicio Ubuntu no se conecta, si reinicio si se conecta, ya probé reiniciar tres veces y se conecta automáticamente. El problema es al arrancar la primera vez. ¿Habrá una solución al problema? Por otro lado les cuento que me está gustando cada vez mas el entorno de Ubuntu (ahora Kubuntu puesto que instale el paquete de KDE) y estoy ansioso por aprender mas al respecto. Saludos.
Paso la consulta por el tema de la conexion erratica [a un nuevo hilo en seccion Hardware]("http://ubuntuforums.org/showthread.php?t=1415947").

Me alegro que te guste KDE :)

---

### Post by Tio Bill on 2010-02-25
Entonces este tema podría darse como solucionado. Gracias por su tiempo Guillermo.

---

### Post by guillermolisi on 2010-02-25
> **Tio Bill said:**
> Entonces este tema podría darse como solucionado. Gracias por su tiempo Guillermo.
Mmm .. no se si el termino solucionado es de aplicacion porque en realidad nunca pudimos llegar al origen del problema. Mas que una solucion fue un "rebusque", una vuelta como para poder seguir trabajando pero con otro entorno grafico.

Para poder decir que este tema estaria solucionado deberiamos seguir revisando y haciendo pruebas con Gnome, Por ejemplo creando un usuario nuevo y observando si se repite el mismo sintoma de aspecto ya que es posible que en los archivos de configuracion de Gnome para el usuario que estas usando haya algo que lo hace fallar (estan en /home/<usuario>/)

---

### Post by Tio Bill on 2010-02-25
Voy a seguir su consejo y probar con otro usuario en el entorno de Gnome para así poder encontrar una solución verdadera.

---

### Post by Tio Bill on 2010-02-25
He probado como bien me indicó, creando otro usuario, y sucede exactamente lo mismo, los iconos de los discos no aparecen, ni el fondo que yo había puesto, hasta que hago click en el disco donde está instalado Ubuntu y ahí si aparece el fondo, salvo que tengo que poner los accesos directos a los discos manualmente.

---

### Post by guillermolisi on 2010-02-26
> **Tio Bill said:**
> He probado como bien me indicó, creando otro usuario, y sucede exactamente lo mismo, los iconos de los discos no aparecen, ni el fondo que yo había puesto, hasta que hago click en el disco donde está instalado Ubuntu y ahí si aparece el fondo, salvo que tengo que poner los accesos directos a los discos manualmente.
La idea era probarlo sin modificar su aspecto original, ni siquiera su wallpaper, para verificar que como viene por defecto funciona bien o de entrada funciona mal.

Hubo casos en que el usuario modifica algo, un tema o juego de iconos que por alguna razon resulta incompatible, y ahi comienza a funcionar con defectos.

Probado como viene de fabrica, si funciona bien se modifica una sola cosa, por el ejemplo el fondo de pantalla, se verifica que siga funcionando bien y luego se sigue adelante con otras modificaciones hasta que deja de funcionar. Entonces lo ultimo que se modifico es lo que esta generando el problema. Identificado esto se podra buscar el por que y una posible solucion.

---

