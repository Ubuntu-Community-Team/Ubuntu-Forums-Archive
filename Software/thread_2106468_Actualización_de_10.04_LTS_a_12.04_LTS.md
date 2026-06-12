---
title: "Actualización de 10.04 LTS a 12.04 LTS"
date: 2013-01-19
forum: Software
---

### Post by mecdem on 2013-01-19
Equipo: Toshiba Satellite A105-S4384
Sistema: Ubuntu 10.04 (32 bits)
__________

Hola amigos.

Intentando la actualización a Ubuntu versión 12.04 LSC mediante la opción que propone el gestor de actualizaciones, luego de infinidad de mensajes anunciando que no se instaló tal o cual cosa, el proceso se detuvo en el cuarto paso ("Instalando las actualizaciones", "faltan alrededor de 1 hora 39 minutos) y no hay modo de salir de ahí.

Antes de seguir adelante con mi consulta: no he sabido hallar un thread que trate este tema. Si hay alguno, ruego indicarme el enlace.

Gracias.
MEC

---

### Post by guillermolisi on 2013-01-19
Lo mejor para realizar esa actualizacion es usar consola, no entorno grafico.

Ademas mi recomendacion actual es no utilizar mirrors locales sino los servidores centrales que si bien tal vez no ofrecen la misma velocidad, son mas seguros, completos y verifican integridad de todos los paquetes.

Con un ```
sudo do-release-upgrade
``` deberias poder llevar a cabo la tarea con exito.

Si te resistis a usar consola, revisa que mirror estas utilizando, adecualos a los centrales y volve a probar con el Update Manager grafico.

---

### Post by mecdem on 2013-01-19
Hola Guillermo. Gracias por tu ayuda.

> **guillermolisi said:**
> Lo mejor para realizar esa actualizacion es usar consola, no entorno grafico.

El problema es que el gestor de actualizaciones en el entorno gráfico (que es en el que nos movemos los usuarios "rasos") no plantea la opción. Y nos invita a un proceso que luego no funciona adecuadamente.

> Con un ```
sudo do-release-upgrade
``` deberias poder llevar a cabo la tarea con exito.

Como comenté antes, el proceso se detuvo en el cuarto paso, "Instalando las actualizaciones". La pantalla del gestor de actualizaciones que iba mostrando el desarrollo está congelada y no se deja cerrar. Sí funciona el Ctrl+Alt+F1.

La pregunta concreta es: ¿puedo hacer caso omiso de ese estado y acceder directamente a la consola para seguir el camino que me indicás, sudo do-release-upgrade? ¿No va a ser necesario que antes aborte de alguna forma el proceso que estaba en curso?

Gracias mil.
MEC

---

### Post by guillermolisi on 2013-01-20
> **mecdem said:**
> Hola Guillermo. Gracias por tu ayuda.

La pregunta concreta es: ¿puedo hacer caso omiso de ese estado y acceder directamente a la consola para seguir el camino que me indicás, sudo do-release-upgrade? ¿No va a ser necesario que antes aborte de alguna forma el proceso que estaba en curso?

Gracias mil.
MEC
No veo ninguna razon ni riesgo al intentar la actualizacion tal como sugiero. Con solo iniciar la maquina, login en el entorno grafico y luego pasar a una consola deberia funcionar ya que la version 12.04.1 esta disponible hace rato (es decir, la 12.04 no se encuentra mas en los repositorios de desarrollo, tal como se indicaba cuando fue lanzada en Abril del 2012 y se sugeria esperar a la 12.04.1 para realizar una actualizacion desde la 10.04).

No hiciste ningun comentario sobre que servidor estas usando para las actualizaciones. Si es uno local, cambialo. Si son los centrales, dejalo y procede.

---

### Post by mecdem on 2013-01-20
Guillermo, no hice ningún comentario sobre los repositorios (casi seguro que no eran los servidores centrales) porque no había manera de hacer correr ningún programa.

El botón del menú principal funcionaba y podía recorrerlo con el mouse, pero al cliquear una opción (por ejemplo 'Sistema > Orígenes del software') simplemente se cerraba el menú y nada más ocurría. Eso así con cualquiera de los programas. Es que me parece que la actualización frustrada, que había llegado al cuarto paso, ya había estado 'destruyendo' archivos. Por eso no me animaba a hacer nada.

> Con solo iniciar la maquina, login en el entorno grafico y luego pasar a una consola deberia funcionar...

Me lancé: 'Menú principal > Apagar > Apagar'
Y ocurrió lo que temía: el sistema no funciona. Después del grub me muestra la máscara Ubuntu y ahí se queda. Pulso F1, me muestra lo que hizo hasta el punto donde queda detenida la carga del sistema, hay un par de Fails (el último es del Timidity++ Alsa) y nada más. Con 'halt > enter' no pasa nada. Pulsando el botón de 'Encendido/Apagado' aparecen unas cuantas líneas más, la última 'Now will halt' y se apaga el equipo.

En este estado ¿hay alguna opción que no sea una instalación limpia? 

Espero tu instrucción y agradezco desde ya tu enorme paciencia.

---

### Post by guillermolisi on 2013-01-21
Siempre hay alternativas, solo que hay que evaluarlas y elegir aquella que mejor nos queda.

Considerando que tu Ubuntu ya no quiere iniciarse, lo primero que se me ocurre es utilizar un LiveCD/Pendrive y utilizar chroot.

Con esto podes iniciar la maquina desde el pendrive, conectarla a Internet y luego, mediante chroot, decirle al SO que lo que se haga de aqui en adelante se debe aplicar sobre lo que esta en el disco rigido (y no sobre el pendrive). Es decir, cambiar el root directory del pendrive por el que esta en el disco rigido.

De esta forma podrias terminar de actualizar lo que aun esta pendiente, mediante ```
sudo dpkg --configure -a
```.
Terminado este paso probar si la instalacion del disco rigido vuelve a ser iniciable y luego decidir que camino tomar en base a esto.

Si esta alternativa te parece aceptable, desarrollo la idea con mas detalle.

---

### Post by mecdem on 2013-01-22
:lolflag: 
Para una chica que sabe algo de códigos civiles pero nada de código informático parece excesivo... pero dado que ya está todo roto, vamos a intentarlo. Contando con (abusando de) tu infinita paciencia y vocación docente.
______

Tengo la .iso ubuntu-12.04.1-desktop-i386.
¿La paso a un CD o a un pendrive? Para pasarla a pendrive precisaría de instrucciones (o un enlace a donde pueda leerlas). De todos modos, mientras aguardo tu respuesta, voy armando el liveCD.

Una aclaración: estoy utilizando otra notebook con ubuntu-12.04.1. (no sea que alguien piense que estoy utilizando la partición Win de la maquinita donde vamos a recuperar la partición libre... [-X )

MEC

---

### Post by guillermolisi on 2013-01-22
:) Me gusta la gente con tu actitud !!

En esa notebook que esta funcionando genera un pendrive booteable. Hay una opcion que viene por defecto en Ubuntu para ello (Start Up Disk Creator, dice en la que estoy usando ahora).

Luego vas a tener que ver como haces en la Toshiba para que te permita elegir iniciar la maquina desde el pendrive. Normalmente se llama Boot Menu y se accede luego de que cargo el BIOS, presionando una tecla de funcion (que en algunos casos es F8, en otros F12, por mencionar los que mas conozco).

Iniciando esa Toshiba con el pendrive colocado y eligiendo de la lista que te  ofrece desde que unidad queres bootear, podras comenzar a desarrollar lo que voy a enviarte para intentar recuperar la maquina.

Como esta particionado el disco de la Toshiba ? Tenes una particion /home separada de / ? Si no es asi, por favor hace backup de /home.

---

### Post by mecdem on 2013-01-23
> :) Me gusta la gente con tu actitud !!
Je, je... Quizás lleguen a pesarte tus palabras cuando este hilo vaya por la entrada N° 100 en tu esfuerzo porque MEC entienda...
](*,)

> En esa notebook que esta funcionando genera un pendrive booteable. Hay una opcion que viene por defecto en Ubuntu para ello (Start Up Disk Creator, dice en la que estoy usando ahora).
Hecho.
(En mi Ubuntu, que habla español castizo, dice 'Creador de Discos de Arranque').

> Luego vas a tener que ver como haces en la Toshiba para que te permita elegir iniciar la maquina desde el pendrive. Normalmente se llama Boot Menu y se accede luego de que cargo el BIOS, presionando una tecla de funcion (que en algunos casos es F8, en otros F12, por mencionar los que mas conozco).
F12 en mi maquinita.
Configurado: USB en primer lugar, seguido de HDD y CD/DVD.

> Iniciando esa Toshiba con el pendrive colocado y eligiendo de la lista que te  ofrece desde que unidad queres bootear, podras comenzar a desarrollar lo que voy a enviarte para intentar recuperar la maquina.
¡Probado! ¡Iupiii...! ¡Arranca!
Después de una chorrera de líneas con palabras cabalísticas (las ví pulsando F1) ofreció la opción Probar Ubuntu / Instalar Ubuntu. Prudentemente elegí 'Probar' y apareció el escritorio con el ícono para instalar. Luego apagué.
**Quedo a la espera de tus instrucciones**.

> Como esta particionado el disco de la Toshiba? Tenes una particion /home separada de /?
Tengo una partición /home separada de /.
Recordar que tengo una partición Win.

> Si no es asi, por favor hace backup de /home.
Tengo pasado el material a la notebook más nueva.
Para facilitar las referencias dado que las dos son Toshiba: la que vamos a recuperar se llama Hal9002 y la más nueva, Hal9003 (existió una Hal9001, una HP fallecida a temprana edad). Lo de "Hal" es por Hal9000, la computadora de la nave espacial en "2001 - Odisea del espacio".
Pregunta de puro curiosa: ¿cómo habría que hacer para obtener un backup de la partición /home de Hal9002 siendo que el sistema no está funcionando? ¿Algún enlace para leer sobre el tema? (si lo hay, que esté in good spanish, pls).
______

¡Esto se va poniendo divertido!
Guillermo, muchas gracias.
Si logras que MEC instale pasarás de la categoría Ubuntu Member a la de Ubuntu MahaGurú, y deberemos llamarte, reverentes, Maestro Lisiji.

MEC

---

### Post by mecdem on 2013-01-23
Agrego este mini-post para contarte que lo estoy poniendo con Hal9002, usando el 'Probar Ubuntu'
:-D

---

### Post by guillermolisi on 2013-01-23
Excelente, muy bien 10, felicitado !!

Vamos por buen camino y con conexion de datos incluida. Asi que avancemos.

Iniciada la "HAL9002" con el pendrive, hay que abrir una consola/terminal para realizar todo lo que voy a mencionar a continuacion.

**Identificacion de la particion / (root) en el disco rigido**
Ingresar ```
sudo fdisk -l
``` y verificar, tal vez por el tamaño, tal vez por su etiqueta, cual es la particion marcada para alojar el SO y que se monta como / en el disco rigido (que considerando que ahora la maquina vera dos discos habra que determinar cual es el rigido y cual el pendrive. Esto generalmente se logra leyendo la descripcion del dispositivo y se termina verificando por el tamaño total del mismo).
Ejemplo > [guille@tfspc ~]$ sudo fdisk -l

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000095fa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63      208844      104391   83  Linux
/dev/sda2          208845    10458314     5124735   82  Linux swap / Solaris
/dev/sda3        10458315    51424064    20482875   83  Linux
/dev/sda4        51424065   390716864   169646400   83  Linux

Disk /dev/sdb: 15.6 GB, 15606349824 bytes
116 heads, 52 sectors/track, 5053 cylinders, total 30481152 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        8064    30481151    15236544    c  W95 FAT32 (LBA)
[guille@tfspc ~]$ En este ejemplo el pendrive figura como /dev/sdb porque la maquina se inicio desde el disco rigido (/dev/sda).
En /dev/sda vemos una particion /dev/sda3 que es la que aloja al SO y se monta en / (esto lo se porque recuerdo que particione primero con una para /boot, la segunda es /swap, luego / y por ultimo /home). Ademas, el tamaño de /dev/sda3 es lo que acostumbro a reservar para el SO.

Dado que ademas tenes Windows en esa maquina, sugiero que muestres la lista de particiones para ayudarte a determinar cual es la que corresponde usar para este procedimiento de recuperacion.

---

### Post by mecdem on 2013-01-23
> ... Identificacion de la particion... Sugiero que muestres la lista de particiones para ayudarte a determinar cual es la que corresponde usar para este procedimiento de recuperacion.

Va la info.

> ubuntu@ubuntu:~$ sudo fdisk -l

Disco /dev/sda: 160.0 GB, 160041885696 bytes
255 cabezas, 63 sectores/pista, 19457 cilindros, 312581808 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes
Tamaño E/S (mínimo/óptimo): 512 bytes / 512 bytes
Identificador del disco: 0xf88df88d

Dispositivo Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *          63    82638359    41319148+   7  HPFS/NTFS/exFAT
/dev/sda2        82638421   312576704   114969142    5  Extendida
/dev/sda5        82638423   101980619     9671098+  83  Linux
/dev/sda6       101980683   104518889     1269103+  82  Linux swap / Solaris
/dev/sda7       104518953   312576704   104028876   83  Linux

Disco /dev/sdb: 1981 MB, 1981808640 bytes
61 cabezas, 62 sectores/pista, 1023 cilindros, 3870720 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes
Tamaño E/S (mínimo/óptimo): 512 bytes / 512 bytes
Identificador del disco: 0x00022be6

Dispositivo Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdb1   *          62     3868985     1934462    c  W95 FAT32 (LBA)
ubuntu@ubuntu:~$ 
A modo de ejercicio, veamos si entiendo esto.

Disco /dev/sda: es el disco rígido.
160.0 GB

/dev/sda1   *          63    82638359    41319148+   7  HPFS/NTFS/exFAT
Ahí menciona NTFS: eso debe de ser la partición Win.

/dev/sda2        82638421   312576704   114969142    5  Extendida
Parece que han hecho una extendida y dentro de ella van las que siguen.

/dev/sda5        82638423   101980619     9671098+  83  Linux
Por el tamaño, debe de ser la partición / (root), o sea la que aloja el SO.

/dev/sda6       101980683   104518889     1269103+  82  Linux swap / Solaris
Esta no ofrece duda: es la swap.

/dev/sda7       104518953   312576704   104028876   83  Linux
Entonces, esta debe de ser la /home.

Disco /dev/sdb: es el pendrive.
1981 MB - 2 GB

/dev/sdb1   *          62     3868985     1934462    c  W95 FAT32 (LBA)
Es su partición única.

Si mi interpretación es correcta, el próximo paso será saber como direcciono el SO a la partición /dev/sda5.
______

Bien. Quedo a la espera de la siguiente lección.
Gracias. Abrazo. MEC

---

### Post by guillermolisi on 2013-01-23
Excelente MEC !! Brillante !

Con las proximas instrucciones vamos a definir que nuestra particion / sera la que esta en /dev/sda5 y para que no haya problemas con dispositivos ni procesos en ejecucion, tambien vamos a definir los file systems virtuales, que utiliza el SO cuando funciona corrientemente, en el nuevo /.

Montar /dev/sda5 previamente al cambio de /
```
sudo mount /dev/sda5 /mnt
```

Montar los file systems virtuales
```
sudo mount -o bind /proc /mnt/proc
sudo mount -o bind /dev /mnt/dev
sudo mount -o bind /sys /mnt/sys
```
Si hasta aqui todo fue sin advertencias ni errores, podemos continuar. Si hubo algun mensaje, por favor mostralo asi vemos de que se trata.

Cambiar / a /dev/sda5
```
sudo chroot /mnt
``` Si tampoco hubo errores, vamos a intentar una actualizacion de paquetes con ```
sudo apt-get update
sudo apt-get dist-upgrade
``` Y aqui es donde queda picando la pelota hasta que nos digas como resulto esta actualizacion.

Si fue sin mas tramite, proba de reiniciar HAL9002 sin el pendrive (desde el disco rigido), reiniciando la maquina, directamente.

Si resulto con errores, mostralos, por favor.

---

### Post by mecdem on 2013-01-24
Houston, we have a problem... :(
____

> sudo mount /dev/sda5 /mnt
sudo mount -o bind /proc /mnt/proc
sudo mount -o bind /dev /mnt/dev
sudo mount -o bind /sys /mnt/sys
Todo OK

> sudo chroot /mnt
OK y cambió
de ubuntu@ubuntu: $
a root@ubuntu:/#

> sudo apt-get update
```
sudo: imposible resolver el anfitrión ubuntu
apt-get: /usr/lib/libstdc++.so.6: version 'GLIBXX_3.4.15' not found (required by apt-get)
```
____

Cuando intenté salir de la consola, mensaje:
¿Cerrar esta terminal?
Aun hay un proceso ejecutándose en esta terminal. Cerrar la terminal lo matará.

Opté por cerrar.
Cuando vuelva supongo que debo repetir todo el proceso ¿es así? 

Gracias. MEC

---

### Post by guillermolisi on 2013-01-24
Si, cada vez habra que repetir estos pasos.

Antes de volver a intentar el "apt-get update", probemos con ```
sudo dpkg --configure -a
``` A ver que pasa.
Esto deberia terminar de aplicar actualizaciones pendientes interrumpidas. Si no devuelve nada, es que esta todo aplicado (cosa que no creo sea asi).

---

### Post by mecdem on 2013-01-24
Para que me quede bien en claro:

Después del 'sudo dpkg --configure -a',  si va todo bien, ¿continúo con 'sudo apt-get update' y 'sudo apt-get dist-upgrade'?

Gracias.

---

### Post by guillermolisi on 2013-01-24
Si, perdon por no haberlo dicho.

Y para que quede mas claro aun: Para que "apt-get <lo-que-sea>" funcione bien, habra que ver que "dpkg --configure -a" lleva a cabo la aplicacion de nuevos paquetes. Es decir, deberia verse una lista de paquetes que se preparan y actualizan reemplazando viejas versiones por otras mas nuevas.
Si esto no ocurre entonces tendremos que intentar otros metodos ya que claramente esta faltando una libreria fundamental para que apt-get funcione.

---

### Post by mecdem on 2013-01-24
> ...deberia verse una lista de paquetes que se preparan y actualizan reemplazando viejas versiones por otras mas nuevas.
Si esto no ocurre entonces tendremos que intentar otros metodos ya que claramente esta faltando una libreria fundamental para que apt-get funcione.

Después de un listado interminable (solo la parte final llevada al procesador de textos ocupa 10 páginas A4) plagado de errores, el 'sudo dpkg --configure -a' finalizó con un "*Proceso detenido por haber demasiados errores*".

¿Tendremos que intentar otros métodos nomás?
:roll: :?:

---

### Post by guillermolisi on 2013-01-24
MEC, por casualidad tenes instalado Aptitude ? (no recuerdo si en la 10.04 todavia se instalaba por defecto)

Si lo tenes, probaria con```
sudo aptitude update
``` Si el proceso corre sin errores, seguiria con ```
sudo aptitude safe-upgrade
``` para ver si podemos estabilizar y recuperar la instalacion del disco rigido.

Todo esto despues de aplicar los pasos anteriores para el cambio de / a /dev/sda5.

---

### Post by mecdem on 2013-01-25
Buen día Guillermo.

La secuencia
```
ubuntu@ubuntu:~$ sudo mount /dev/sda5 /mnt
ubuntu@ubuntu:~$ sudo mount -o bind /proc /mnt/proc
ubuntu@ubuntu:~$ sudo mount -o bind /dev /mnt/dev
ubuntu@ubuntu:~$ sudo mount -o bind /sys /mnt/sys
ubuntu@ubuntu:~$ sudo chroot /mnt
root@ubuntu:/#
```
funcionó OK
___

```
root@ubuntu:/# sudo aptitude update
```
respondió:
```
sudo: imposible resolver el anfitrión ubuntu
sudo: aptitude: orden no encontrada
```
___

Examino el Centro de software de Ubuntu y veo que existe un 'Aptitude - Terminal-based package manager (terminal interface only)'.
¿Lo instalo y pruebo con sudo aptitude update y luego sudo aptitude safe-upgrade?

(¿Ayudará si durante el proceso musito alguna oración a San Ignuzio? :D )
____

Gracias. Abrazo. MEC

---

### Post by mecdem on 2013-01-25
No encontré una 'cámara fotográfica' pero toqueteando aquí y allá recordé la tecla ImprPant y funcionó. Puse una imagen de las particiones de Hal9002 en
[https://lh5.googleusercontent.com/-Urci8rg1oLM/UQJnd8_LRtI/AAAAAAAACfQ/eqP2kU_FViA/h120/Hal9002+-+GParted+2013-01-25.png](https://lh5.googleusercontent.com/-Urci8rg1oLM/UQJnd8_LRtI/AAAAAAAACfQ/eqP2kU_FViA/h120/Hal9002+-+GParted+2013-01-25.png)

---

### Post by guillermolisi on 2013-01-25
> **mecdem said:**
> 
Examino el Centro de software de Ubuntu y veo que existe un 'Aptitude - Terminal-based package manager (terminal interface only)'.
¿Lo instalo y pruebo con sudo aptitude update y luego sudo aptitude safe-upgrade?

(¿Ayudará si durante el proceso musito alguna oración a San Ignuzio? :D )
____

Gracias. Abrazo. MEC

Si, MEC, dale para adelante con la instalacion de Aptitude y con la oracion tambien. Toda ayuda siempre es bienvenida en estos casos :)

---

### Post by guillermolisi on 2013-01-25
Hay una alternativa mas para intentar que acabo de darme cuenta es factible ya que el pendrive que generaste es version 12.04.1 (confirmar esto, por favor).

Se supone que iniciando HAL9002 desde ese pendrive en modo LiveCD, activando el instalador tendremos una opcion mas a las clasicas de instalacion: La de actualizar la version detectada en el disco rigido.
> Upgrading by using the CD or USB image
If you are using 10.04 LTS or 11.10 and you either insert the live CD or boot from the live CD to start installing it will give a option of upgrading to 12.04. It will automatically detect installed applications and install the updated version of your applications also.

If you download an ISO, the recommendation is to perform a md5sum check to ensure both the ISO downloaded and the burned CD are valid. Esto esta publicado en [AskUbuntu]("http://askubuntu.com/questions/110477/how-do-i-upgrade-from-10-04-or-11-10-to-12-04")
Notar que para la fecha que se realizo esa nota aun no habia sido lanzada la 12.04.1 y por eso los comentarios al respecto.

En mi opinion, deberia verse una imagen como la siguiente cuando arranca el instalador desde el LiveCD/pendrive:

[IMG]http://i.stack.imgur.com/QB7SV.png[/IMG]

---

### Post by mecdem on 2013-01-25
> Hay una alternativa mas para intentar que acabo de darme cuenta es factible ya que el pendrive que generaste es version 12.04.1 (confirmar esto, por favor).
Je, je, esa alternativa la estoy 'olfateando' desde el principio (en el post 5 preguntaba "en este estado ¿hay alguna opción que no sea una instalación limpia?"), pero como a los expertos les encanta agotar todos los caminos antes de ir a esa solución... me dije "shhh, MEC". Además, de la mano de mi Maha-Gurú, no me iba a perder la oportunidad de andar recorriendo esos caminos... :p
____

El live-pendrive está generado con la .iso ubuntu-12.04.1-desktop-i386.

> En mi opinion, deberia verse una imagen como la siguiente cuando arranca el instalador desde el LiveCD/pendrive...
La imagen que veo durante el arranque es como ésta (con la opción Español activada... faltaba más):

[IMG]http://ubuntulife.files.wordpress.com/2011/10/try-intsall.jpg?w=500[/IMG]

y en el escritorio tengo un bonito ícono que dice "Instalar Ubuntu 12.04.1 LTS".
___

Doy vuelta la hoja.

Hice los "deberes". Instalé Aptitude y mientras escribía la primera parte de este post se estuvieron ejecutando las instrucciones 'sudo aptitude update' y luego 'sudo aptitude safe-upgrade', en ese orden.

(Por si tiene alguna importancia: en algún lado el safe-upgrade tiró estas advertencias:
cryptsetup: WARNING: failed to detect canonical device of overlayfs
cryptsetup: WARNING: could not determine root device from /etc/fstab
Aquí se detuvo -lo que me permitió copiar esas líneas- pero luego siguió adelante).
____

Voy a seguir en otro post desde Hal9003: aqui en Hal9002, mientras todavìa se está ejecutanto el safe-upgrade, hay un mensaje de que este equipo tiene 0 bit de espacio (?). Tomé la imagen del analizador de disco pero ya no me deja subirla a internet.

---

### Post by mecdem on 2013-01-25
> Voy a seguir en otro post desde Hal9003: aqui en Hal9002, mientras todavìa se está ejecutanto el safe-upgrade, hay un mensaje de que este equipo tiene 0 bit de espacio (?).

Sigo desde Hal9002: terminó el safe-upgrade y pude volver a ingresar a internet y subir la imagen del analizador de disco, que está en
[https://picasaweb.google.com/100997509458764722861/25DeEneroDe2013#5837545068188257522](https://picasaweb.google.com/100997509458764722861/25DeEneroDe2013#5837545068188257522)
Fijáte que ya no pudo presentar el gráfico de anillo. En una primera advertencia podía verse el anillo casi cerrado. 
Las particiones se pueden ver en
[https://picasaweb.google.com/100997509458764722861/25DeEneroDe2013#5837341831310558930](https://picasaweb.google.com/100997509458764722861/25DeEneroDe2013#5837341831310558930)
____

Continúo relatando qué pasó durante el safe-upgrade. He ido copiando (a mano) algunas líneas como para darte idea de lo que iba sucediendo, aunque no sé si las que pude copiar son relevantes o no.

En un momento apareció el mensaje advirtiendo que quedaba poco espacio en el dispositivo. Traté de guardar la imagen, pero no lo logré. La que muestro en Picasa es un segundo y último mensaje similar, cuando ya quedaba 0 bit de espacio.

En la consola:
Volvió a tirar las dos líneas "cryptsetup".
Después: WARN: el uid es 0 pero "/" pertenece a 1000.
Otra línea: /usr/bin/mandb: no se puede escribir en /var/cache/man/11828: No queda espacio en el dispotivo.
(Siguió configurando).
Otra línea: Eliminado "desviación de /sbin/udevadm a /sbin/udevadm.upgrade por fake-udev... (sigue la línea que no pude completar).
Más adelante repitió las dos líneas "cryptsetup".
Otra línea: Se encontraron errores al procesar: intramfs-tools.
Otra línea: Un paquete no se pudo instalar. Intentando recuperarse.
(Siguió configurando).
Otra línea: error al procesar linux-image-3.2.0-36 generic-pae
Otra línea: cpio - tubería rota

Ya hacia el final:
dpkg: error fatal irrecuperable, abortando: no se pudo ejecutar "flush" /var/lib/dpkg/updates/tmp.i tras el relleno. No queda espacio en el dispositivo.
E: Se interrumpió la ejecución de dpkg, debe ejecutar manualmente "sudo dpkg --configure -a" para corregir el problema.
E: ¡No se puede volver a obtener el sistema de bloqueo! (¿Quizás se está ejecutando otro apt o dpkg?)
E: Se interrumpió la ejecución de dpkg, debe ejecutar manualmente "sudo dpkg --configure -a" para corregir el problema.
Estado actual: 169 actualizaciones (-151)
ubuntu@ubuntu: -$
___

Fin de la 'novela'.
Espero que sirva.

Gracias. Abrazo.
MEC

---

### Post by mecdem on 2013-01-25
Off topic: qué significa (no la traducción sino el sentido) esa frase "A Carafe of Ubuntu" que se ve bajo mi nick? Apareció ahora, antes decía algo sobre "beans".

---

### Post by guillermolisi on 2013-01-26
> **mecdem said:**
> Off topic: qué significa (no la traducción sino el sentido) esa frase "A Carafe of Ubuntu" que se ve bajo mi nick? Apareció ahora, antes decía algo sobre "beans".
Son frases que el sistema vBulletin, que soporta el funcionamiento de UbuntuForums, asigna al azar a quienes se suscriben y habilitan en su perfil que se vea junto con su nickname.
Son frases que nada tienen que ver con la cantidad de thread/posts y antigüedad del suscriptor y tienen como unico fin darle un toque descontracturado al foro (desde el paradigma del sentido del humor sajon, claro esta).

---

### Post by guillermolisi on 2013-01-26
> **mecdem said:**
> Sigo desde Hal9002: terminó el safe-upgrade y pude volver a ingresar a internet y subir la imagen del analizador de disco, que está en
[https://picasaweb.google.com/100997509458764722861/25DeEneroDe2013#5837545068188257522](https://picasaweb.google.com/100997509458764722861/25DeEneroDe2013#5837545068188257522)
Fijáte que ya no pudo presentar el gráfico de anillo. En una primera advertencia podía verse el anillo casi cerrado. 
Las particiones se pueden ver en
[https://picasaweb.google.com/100997509458764722861/25DeEneroDe2013#5837341831310558930](https://picasaweb.google.com/100997509458764722861/25DeEneroDe2013#5837341831310558930)
____

Continúo relatando qué pasó durante el safe-upgrade. He ido copiando (a mano) algunas líneas como para darte idea de lo que iba sucediendo, aunque no sé si las que pude copiar son relevantes o no.

En un momento apareció el mensaje advirtiendo que quedaba poco espacio en el dispositivo. Traté de guardar la imagen, pero no lo logré. La que muestro en Picasa es un segundo y último mensaje similar, cuando ya quedaba 0 bit de espacio.

En la consola:
Volvió a tirar las dos líneas "cryptsetup".
Después: WARN: el uid es 0 pero "/" pertenece a 1000.
Otra línea: /usr/bin/mandb: no se puede escribir en /var/cache/man/11828: No queda espacio en el dispotivo.
(Siguió configurando).
Otra línea: Eliminado "desviación de /sbin/udevadm a /sbin/udevadm.upgrade por fake-udev... (sigue la línea que no pude completar).
Más adelante repitió las dos líneas "cryptsetup".
Otra línea: Se encontraron errores al procesar: intramfs-tools.
Otra línea: Un paquete no se pudo instalar. Intentando recuperarse.
(Siguió configurando).
Otra línea: error al procesar linux-image-3.2.0-36 generic-pae
Otra línea: cpio - tubería rota

Ya hacia el final:
dpkg: error fatal irrecuperable, abortando: no se pudo ejecutar "flush" /var/lib/dpkg/updates/tmp.i tras el relleno. No queda espacio en el dispositivo.
E: Se interrumpió la ejecución de dpkg, debe ejecutar manualmente "sudo dpkg --configure -a" para corregir el problema.
E: ¡No se puede volver a obtener el sistema de bloqueo! (¿Quizás se está ejecutando otro apt o dpkg?)
E: Se interrumpió la ejecución de dpkg, debe ejecutar manualmente "sudo dpkg --configure -a" para corregir el problema.
Estado actual: 169 actualizaciones (-151)
ubuntu@ubuntu: -$
___

Fin de la 'novela'.
Espero que sirva.

Gracias. Abrazo.
MEC

Bueno, podria haber sido mucho peor. Por lo menos sabemos que hay un compromiso de espacio libre en la particion / que impide que termine el proceso de actualizacion y esto se puede resolver manualmente para luego llevar a cabo "sudo dpkg --configure -a".

Iniciando siempre desde el LiveCD/pendrive, montar la particion /dev/sda5 en /mnt (pero NO las demas ni hacer el chroot). Montada la particion, ejecutar ```
sudo ls -al /boot
``` y mostrar su salida asi te indico que archivos se deberan eliminar manualmente para lograr espacio en disco.

No pude ver las imagenes en Picasa. Me dice que la pagina que quiero ver no existe mas.

Al margen de lo anterior, si avanzas con el instalador del LiveCD/pendrive (o sea, click en Instalar), te deberia ofrecer esa imagen que puse (en Ingles) donde tenes la alternativa de actualizar. Esto recien aparecera luego que el instalador verifique el particionado del disco rigido y detecte que sistemas estan instalados en el.

Personalmente y dado el avance que lograste, agotaria las instancias via aptitude. Si llegamos a un punto ciego podremos volver a probar la actualizacion via LiveCD/pendrive.

Pregunta de oficio: el safe-upgrade lo hiciste luego de cambiar / a /dev/sda5 con chroot, cierto ? Esto es para verificar que la falta de espacio en disco es respecto del disco rigido y no del pendrive.

---

### Post by mecdem on 2013-01-26
> Iniciando siempre desde el LiveCD/pendrive, montar la particion /dev/sda5 en /mnt (pero NO las demas ni hacer el chroot).

A ver si interpreto bien.
Tengo que ejecutar la instrucción

```
ubuntu@ubuntu:~$ sudo mount /dev/sda5 /mnt
```

Luego
```
ubuntu@ubuntu:~$ sudo ls -al /boot
```
y muestro la salida.
______

> No pude ver las imagenes en Picasa. Me dice que la pagina que quiero ver no existe mas.

Mmmm... clicando en los enlaces a mí me aparecen, pero me entra la duda de si no podés verlas porque la dirección es una http**s**. No soy muy habilidosa con el uso de Picasa.
______

> ...si avanzas con el instalador del LiveCD/pendrive (o sea, click en Instalar), te deberia ofrecer esa imagen que puse (en Ingles) donde tenes la alternativa de actualizar. Esto recien aparecera luego que el instalador verifique el particionado del disco rigido y detecte que sistemas estan instalados en el.

Esto me parece que es para después. Por ahora voy a provocar la salida del ls -al /boot y te la muestro.
______

> Personalmente... agotaria las instancias via aptitude...;)
¿No te digo? Les encanta todo lo que evite una instalación 'limpia'. Aaahhh, tiempos aquellos en que venía un tipo y te decía "hay que formatear el disco", y arrasaba con todo... :D
______

> Pregunta de oficio: el safe-upgrade lo hiciste luego de cambiar / a /dev/sda5 con chroot, cierto ? Esto es para verificar que la falta de espacio en disco es respecto del disco rigido y no del pendrive.

La secuencia de instrucciones fue esta:
ubuntu@ubuntu:~$ sudo mount /dev/sda5 /mnt
ubuntu@ubuntu:~$ sudo mount -o bind /proc /mnt/proc
ubuntu@ubuntu:~$ sudo mount -o bind /dev /mnt/dev
ubuntu@ubuntu:~$ sudo mount -o bind /sys /mnt/sys
ubuntu@ubuntu:~$ sudo chroot /mnt
root@ubuntu:/#
root@ubuntu:/# sudo aptitude update
root@ubuntu:/# sudo aptitude safe-upgrade
_______

MEC

---

### Post by guillermolisi on 2013-01-26
Todo perfecto, MEC.

Muy bien interpretadas las sugerencias y muy bien hecho el proceso para el chroot.

Ahora, la alternativa de "arrasar con todo" siempre existio. Interprete que no era una opcion valida para vos, o por lo menos era la ultima, la de "quememos las naves y a otra cosa".
De proceder asi no hubieras aprendido lo de cambiar / por la particion en otro soporte de almacenamiento, que tambien sirve para recuperar un grub corrupto y otros menesteres similares, y te hubieses obligado a instalar/desinstalar programas.
Tambien es cierto que este hilo se hubiera cerrado hace unos dias atras :) pero no me molesta que se prolongue siempre que todo este intercambio sirva no solo a vos sino a todo lector eventual.

De todas formas, vos sos la que decide que es mejor y actuar en consecuencia.

Creo que las imagenes que subiste a Picasa estan en un area privada y por eso no se pueden ver.

---

### Post by mecdem on 2013-01-26
Cambio el orden:

> Creo que las imagenes que subiste a Picasa estan en un area privada y por eso no se pueden ver.
Es cierto. No me acordaba de esas opciones de usuario. Ahora las puse de modo que pueda verlas quien tiene la dirección. Por favor ¿podrías probar y decirme si las ves?
[https://picasaweb.google.com/lh/photo/KhiKDBJHKY3dW-rWY1TZrrQkoOmxFVeWvOpfV2HegiU?feat=directlink](https://picasaweb.google.com/lh/photo/KhiKDBJHKY3dW-rWY1TZrrQkoOmxFVeWvOpfV2HegiU?feat=directlink)
[https://picasaweb.google.com/lh/photo/lIAvVToId4Njzd0ZIlfkYbQkoOmxFVeWvOpfV2HegiU?feat=directlink](https://picasaweb.google.com/lh/photo/lIAvVToId4Njzd0ZIlfkYbQkoOmxFVeWvOpfV2HegiU?feat=directlink)

> De todas formas, vos sos la que decide que es mejor y actuar en consecuencia.
No, no, Gurú. Usted decide.
Lo que yo sí decidí fue no desaprovechar la preciosa oportunidad de transitar caminos para mí novedosos, tomada de la mano del experto que me la ofreció, aun a sabiendas de que MEC -no informática- podría ser "un hueso duro de pelar" :) Así que digo 'gracias, Guillermo' y te pido que sigas marcando el rumbo.

> Personalmente... agotaria las instancias via aptitude...
Ay, ay, ay... me temo que estamos agotando las instancias.
Te cuento.

Inicio el equipo de la manera consabida. Después de optar por "Probar Ubuntu" apareció el siguiente mensaje:
```
The system is running in low-graphics mode.
Your screen, graphics card, and input device settings could not be detected correctly.
You will need to configure yourself.
```

Doy enter y aparece este otro mensaje:
```
What would you like to do?
- Run in low-graphics mode for just one session
- Reconfigure graphics
- Troubleshoot the error
- Exit to console login
```
La pregunta 'What would you like to do' es una humorada del programador: la opción tildada es la primera, y no hay manera de hacer nada más (no hay respuesta al mouse, no al teclado), al punto que hasta para salir no queda otra que apagar con el botón de encender/apagar.

¿Cómo seguimos?
La única opción que no acepto =; es tirar la maquinita... :D
______

Advierto que omití mencionar algo: **antes** de los mensajes que cité, hay uno muy fugaz del que solo alcancé a leer estas primeras palabras, "This computer has only 0 bit..."

MEC

---

### Post by guillermolisi on 2013-01-27
Vi las imagenes en Picasa y me confirmaron que en /dev/sda5 no hay lugar libre suficiente para que el SO y las actualizaciones trabajen bien. Por lo tanto sigamos en el camino de hacer lugar, "ls -al /mnt/boot" de por medio.

Seguramente nos encontraremos con imagenes del kernel que ya son historia antigua :)

---

### Post by mecdem on 2013-01-27
> ...Por lo tanto sigamos en el camino de hacer lugar, "ls -al /mnt/boot" de por medio.

"¡Alto allí! ¿De dónde saco una consola?" -me preguntaba. 
Bueno, hice Ctrl+Alt+F1 en la pantalla donde se opta por probar o instalar Ubuntu, y la consola apareció.

Resultado de ls -al /mnt/boot:
**"ls: cannot access /mnt/ boot: No such file or directory"**

Probé "ls -al" y funcionó: tiró un listado de directorios. Pero como no tenía idea de donde pegar la copia de la salida, le saqué fotitos con el celular. Ahora voy a reducir las imágenes (que salen con una resolución enorme), las subo a Picasa, y te aviso cuando estén, con las direcciones.

Algo más: intenté un cd a uno de los directorios del listado, y también dijo que "No such file or directory".
______

Agrego aquí las direcciones de las fotos:
ls 1: [https://picasaweb.google.com/lh/photo/BdQvbHAx6uQXGU6y4BoQ2QVRd1tQrRGoCFmnyh9p8Rs?feat=directlink](https://picasaweb.google.com/lh/photo/BdQvbHAx6uQXGU6y4BoQ2QVRd1tQrRGoCFmnyh9p8Rs?feat=directlink)
ls 2: [https://picasaweb.google.com/lh/photo/DRJvvl5JbzdLot7lqGnAJAVRd1tQrRGoCFmnyh9p8Rs?feat=directlink](https://picasaweb.google.com/lh/photo/DRJvvl5JbzdLot7lqGnAJAVRd1tQrRGoCFmnyh9p8Rs?feat=directlink)
ls 3: [https://picasaweb.google.com/lh/photo/JrlnXO_IQKnOVKtaD8DMaQVRd1tQrRGoCFmnyh9p8Rs?feat=directlink](https://picasaweb.google.com/lh/photo/JrlnXO_IQKnOVKtaD8DMaQVRd1tQrRGoCFmnyh9p8Rs?feat=directlink)
ls 4: [https://picasaweb.google.com/lh/photo/i3ovWKG0mE7wwDAVD1EUDgVRd1tQrRGoCFmnyh9p8Rs?feat=directlink](https://picasaweb.google.com/lh/photo/i3ovWKG0mE7wwDAVD1EUDgVRd1tQrRGoCFmnyh9p8Rs?feat=directlink)
______

Ahora, mirando las fotos, me pregunto si estaba "parada" en el lugar adecuado cuando hice el ls -al /mnt/boot: lo que se ve más bien parece el contenido de un /home/usuario... y no de un sistema.
Mmmm... voy a inspeccionar...
______

MEC

---

### Post by mecdem on 2013-01-27
[B]¡Claaaaro!
¡Era eso![/B]

Es que al abrirse la consola el prompt es 'ubuntu@ubuntu', y no fui capaz de reconocer que ese segundo 'ubuntu' era un usuario.
Debería eliminar el post anterior, pero lo dejaré para que dé testimonio de mis torpezas... y de mis tribulaciones...  :(
______

**Nuevas fotitos en Picasa**

Las tres primeras muestran el contenido de "/".

ls root 1: [https://picasaweb.google.com/lh/photo/hZaSpdrPfdengfNv7zoSeQVRd1tQrRGoCFmnyh9p8Rs?feat=directlink](https://picasaweb.google.com/lh/photo/hZaSpdrPfdengfNv7zoSeQVRd1tQrRGoCFmnyh9p8Rs?feat=directlink)
ls root 2: [https://picasaweb.google.com/lh/photo/v1le2aBUupQplp_LurDvvwVRd1tQrRGoCFmnyh9p8Rs?feat=directlink](https://picasaweb.google.com/lh/photo/v1le2aBUupQplp_LurDvvwVRd1tQrRGoCFmnyh9p8Rs?feat=directlink)
ls root 3: [https://picasaweb.google.com/lh/photo/rhgqEpfCl3vvu8g0_0v6hwVRd1tQrRGoCFmnyh9p8Rs?feat=directlink](https://picasaweb.google.com/lh/photo/rhgqEpfCl3vvu8g0_0v6hwVRd1tQrRGoCFmnyh9p8Rs?feat=directlink)

Y esta muestra el **contenido de /mnt/boot**, que es lo que te interesaba ver:
mnt-boot: [https://picasaweb.google.com/lh/photo/sjl2y5Y9tc729OlI8w_rbgVRd1tQrRGoCFmnyh9p8Rs?feat=directlink](https://picasaweb.google.com/lh/photo/sjl2y5Y9tc729OlI8w_rbgVRd1tQrRGoCFmnyh9p8Rs?feat=directlink)
______

Una duda: aun estando parada en un usuario, la instrucción 'ls -al /mnt/boot' ¿no está indicando la ruta para que vaya a ese directorio?
Cuando me paré en /, tampoco aceptó esa instrucción con la misma sintaxis: llegué con un cd /mnt y luego cd /boot (ahora no recuerdo si con la barra delante del nombre del directorio), y una vez ahí, 'ls -al'. 
______

Aguardo nuevas instrucciones.
Gracias. Abrazo.

MEC

---

### Post by guillermolisi on 2013-01-27
Refresquemos ...

El proceso para obtener la salida de ```
sudo ls -al /boot
```(si, le saque el /mnt por lo que voy a decir a continuacion y disculpas porque me exprese en forma confusa) debe realizarse luego de haber logrado el cambio de / a /dev/sda5 con chroot.

Una vez hecho este cambio con ingresar "ls -al /boot" el sistema siempre se referira al directorio raiz que este activo (en este caso deberia ser el asignado cuando se hizo el chroot).

Como el directorio /boot esta dentro de / (/dev/sda5), no hace falta el /mnt (ademas dentro del /mnt del / activo no hay nada !!)

Luego, por que no pudiste abrir una terminal en el escritorio grafico para poder copiar y pegar la salida de "ls -al /boot" ?

Se supone que estas en una sesion grafica con un LiveCD/pendrive, cierto ?

Si la fotografia de /boot es todo lo que se obtuvo como salida del ls, en algun lugar hay algo que esta ocupando demasiado espacio porque con solo dos imagenes de kernel no puede ser que se quede sin lugar libre, aun considerando que la particion /dev/sda5 podria haber sido mas generosa (suelo asignarle entre 10 y 17 Gb, segun sea el uso que se le de a la maquina y la estructura de particiones que se haga)

Edit: Me corrijo - Una imagen de kernel a la que le falta terminar de generar el resto de los archivos de arranque. La version de kernel que podria usarse es la .29 pero no sirve porque falta su imagen (vmlinuz .....)

---

### Post by mecdem on 2013-01-27
> Luego, por que no pudiste abrir una terminal en el escritorio grafico para poder copiar y pegar la salida de "ls -al /boot"? Se supone que estas en una sesion grafica con un LiveCD/pendrive, cierto?

No, no tengo escritorio gráfico. El proceso de carga se interrumpe, según dije en un post anterior, después de la pantalla de opción Probar/Instalar Ubuntu. Reproduzco:

> Inicio el equipo de la manera consabida. Después de optar por "Probar Ubuntu" apareció el siguiente mensaje:

[I]The system is running in low-graphics mode.
Your screen, graphics card, and input device settings could not be detected correctly.
You will need to configure yourself.[/I]

Doy enter y aparece este otro mensaje:

[I]What would you like to do?
- Run in low-graphics mode for just one session
- Reconfigure graphics
- Troubleshoot the error
- Exit to console login[/I]

La pregunta 'What would you like to do' es una humorada del programador: la opción tildada es la primera, **y no hay manera de hacer nada más (no hay respuesta al mouse, no al teclado), al punto que hasta para salir no queda otra que apagar con el botón de encender/apagar**.

Advierto que omití mencionar algo: antes de los mensajes que cité, hay uno muy fugaz del que solo alcancé a leer estas primeras palabras, "This computer has only 0 bit..."

Esto último parece congruente con los mensajes que antes habían aparecido durante la ejecución de 'aptitude safe-upgrade', que finalizó con estas líneas:
> dpkg: **error fatal irrecuperable, abortando**: no se pudo ejecutar "flush" /var/lib/dpkg/updates/tmp.i tras el relleno. **No queda espacio en el dispositivo**.
E: Se interrumpió la ejecución de dpkg, debe ejecutar manualmente "sudo dpkg --configure -a" para corregir el problema.
E: ¡No se puede volver a obtener el sistema de bloqueo! (¿Quizás se está ejecutando otro apt o dpkg?)
E: Se interrumpió la ejecución de dpkg, debe ejecutar manualmente "sudo dpkg --configure -a" para corregir el problema.
Estado actual: 169 actualizaciones (-151)
ubuntu@ubuntu: -$

Si aun así se puede acceder a un entorno gráfico, no sé cómo hacerlo.
La consola la obtuve con Ctrl+Alt+F1 cuando la carga se detuvo en la pantalla de opción Probar/Instalar Ubuntu.
______

Pregunta: la imagen en [https://picasaweb.google.com/lh/photo/KhiKDBJHKY3dW-rWY1TZrrQkoOmxFVeWvOpfV2HegiU?feat=directlink](https://picasaweb.google.com/lh/photo/KhiKDBJHKY3dW-rWY1TZrrQkoOmxFVeWvOpfV2HegiU?feat=directlink) ¿no deja ver qué hay en la partición? Veo un /mnt de 9,3 GB, lo que es casi el tamaño de la partición.
______

Ahora voy a ver las instrucciones de la primera parte de tu post, y te cuento.

Gracias. MEC

---

### Post by guillermolisi on 2013-01-27
Es que no hay que instalar. Solo iniciar desde el pendrive una sesion Live, proceder con el montaje de las particiones previo al chroot y luego proceder al chroot. Abrir una terminal para el "ls -al /boot", mostrar su contenido, lograr detectar que es lo que esta consumiendo el espacio libre que deberia tener esa particion /dev/sda5, eliminarlo para recuperar lugar util y luego volver a repetir ```
sudo aptitude update
sudo aptitude safe-upgrade
```

---

### Post by mecdem on 2013-01-27
A ver, a ver... :-k
(me estoy perdiendo en la neblina...) :( 
Revisemos:

> Es que no hay que instalar...
En ningún momento intenté instalar.

>  ...Solo iniciar desde el pendrive una sesion Live...

Todo inicio fue desde el pendrive. Cuando llegaba a la pantalla con la opción Probar/Instalar Ubuntu, siempre elegí *Probar*. De este modo llegaba al escritorio de Ubuntu y allí abría una terminal y también el navegador para ver tus instrucciones, y -en su caso- ir copiando las salidas desde la terminal para pegarlas a un post de este hilo.

La secuencia de instrucciones en la consola era ésta:
ubuntu@ubuntu:~$ sudo mount /dev/sda5 /mnt
ubuntu@ubuntu:~$ sudo mount -o bind /proc /mnt/proc
ubuntu@ubuntu:~$ sudo mount -o bind /dev /mnt/dev
ubuntu@ubuntu:~$ sudo mount -o bind /sys /mnt/sys
ubuntu@ubuntu:~$ sudo chroot /mnt
root@ubuntu:/#
root@ubuntu:/# sudo aptitude update
root@ubuntu:/# sudo aptitude safe-upgrade

A partir del safe-upgrade abortado, según recordaba en mi post anterior, no puedo ir más allá de la pantalla de opción Probar/Instalar Ubuntu, ya que -elegido Probar, tal como venía haciendo- el sistema tira los mensajes que mencioné y no permite nada más.

Lo único que puedo hacer es abrir la consola con Ctrl+Alt+F1 cuando la carga está detenida en la pantalla de opción Probar/Instalar Ubuntu.
______

> ...Abrir una terminal para el "ls -al /boot", mostrar su contenido, lograr detectar que es lo que esta consumiendo el espacio libre que deberia tener esa particion /dev/sda5, eliminarlo para recuperar lugar util y luego volver a repetir ```
sudo aptitude update
sudo aptitude safe-upgrade
```

No sé si entendí bien las consignas, te cuento lo que hice:
En la consola ejecuté esta secuencia:
```
ubuntu@ubuntu:~$ sudo mount /dev/sda5 /mnt
ubuntu@ubuntu:~$ sudo mount -o bind /proc /mnt/proc
ubuntu@ubuntu:~$ sudo mount -o bind /dev /mnt/dev
ubuntu@ubuntu:~$ sudo mount -o bind /sys /mnt/sys
ubuntu@ubuntu:~$ sudo chroot /mnt
root@ubuntu:/#
```

Y luego:
```
ls -al /boot
```

El resultado muestra los directorios del sistema. Entiendo que la columna de números que aparece a la derecha de la columna fecha del archivo correspondiente, indica el tamaño del archivo.

Espero que así sea ;) porque 'me largo' a transcribirlos.

```
4096     .
4096     ..
652956   abi-2.6.32-44-generic
653174   abi-2.6.32-45-generic
787231   abi-3.2.0-36-generic
116014   config-2.6.32-44-generic
116036   config-2.6.32-45-generic
147514   config-3.2.0-36-generic
4096     grub
7996805  initr.img-2.6.32-44-generic
8005058  initr.img-2.6.32-45-generic
176764   memtest86+.bin
178944   memtest86+_multiboot.bin
1694274  System.map-2.6.32-44-generic
1695456  System.map-2.6.32-45-generic
2252687  Sistem.map-3.2.0-36-generic
1196     vmcoreinfo-2.6.32-44-generic
1196     vmcoreinfo-2.6.32-45-generic
4050304  vmlinuz-2.6.32-44-generic
4053728  vmlinuz-2.6.32-45-generic
4864480  vmlinuz-3.2.0-36-generic
```
______

¿Están en este listado los archivos a eliminar?
Si es así: ¿cuáles se borran y cuáles no?
En su caso, favor indicarme la sintaxis correcta del 'del'
______

Una vez que haya eliminado archivos para hacer espacio ¿tendría que repetir la secuencia como antes? Muestro:
```
ubuntu@ubuntu:~$ sudo mount /dev/sda5 /mnt
ubuntu@ubuntu:~$ sudo mount -o bind /proc /mnt/proc
ubuntu@ubuntu:~$ sudo mount -o bind /dev /mnt/dev
ubuntu@ubuntu:~$ sudo mount -o bind /sys /mnt/sys
ubuntu@ubuntu:~$ sudo chroot /mnt
root@ubuntu:/#
```

Y luego:
```
sudo aptitude update
sudo aptitude safe-upgrade
```
_____

¿Vamos bien?
¿O me desbarranqué? :D
_____

Gracias por tu paciencia.
Gracias por tus respuestas tan rápidas, aún durante el fin de semana. Aprecio tu dedicación.

Buena semana.
MEC

---

### Post by guillermolisi on 2013-01-28
> **mecdem said:**
> 
```
4096     .
4096     ..
652956   abi-2.6.32-44-generic
653174   abi-2.6.32-45-generic
787231   abi-3.2.0-36-generic
116014   config-2.6.32-44-generic
116036   config-2.6.32-45-generic
147514   config-3.2.0-36-generic
4096     grub
7996805  initr.img-2.6.32-44-generic
8005058  initr.img-2.6.32-45-generic
176764   memtest86+.bin
178944   memtest86+_multiboot.bin
1694274  System.map-2.6.32-44-generic
1695456  System.map-2.6.32-45-generic
2252687  Sistem.map-3.2.0-36-generic
1196     vmcoreinfo-2.6.32-44-generic
1196     vmcoreinfo-2.6.32-45-generic
4050304  vmlinuz-2.6.32-44-generic
4053728  vmlinuz-2.6.32-45-generic
4864480  vmlinuz-3.2.0-36-generic
```
______

¿Están en este listado los archivos a eliminar?
Si es así: ¿cuáles se borran y cuáles no?
En su caso, favor indicarme la sintaxis correcta del 'del'
______

Una vez que haya eliminado archivos para hacer espacio ¿tendría que repetir la secuencia como antes? Muestro:
```
ubuntu@ubuntu:~$ sudo mount /dev/sda5 /mnt
ubuntu@ubuntu:~$ sudo mount -o bind /proc /mnt/proc
ubuntu@ubuntu:~$ sudo mount -o bind /dev /mnt/dev
ubuntu@ubuntu:~$ sudo mount -o bind /sys /mnt/sys
ubuntu@ubuntu:~$ sudo chroot /mnt
root@ubuntu:/#
```

Y luego:
```
sudo aptitude update
sudo aptitude safe-upgrade
```
_____

¿Vamos bien?
¿O me desbarranqué? :D
_____

Gracias por tu paciencia.
Gracias por tus respuestas tan rápidas, aún durante el fin de semana. Aprecio tu dedicación.

Buena semana.
MEC
Ok. Aclarado el procedimiento, seguimos adelante.

Vamos a borrar algunos archivos de /boot segun la siguiente lista ```
sudo rm /boot/config-2.6.32-44-generic /boot/abi-2.6.32-44-generic /boot/initr.img-2.6.32-44-generic /boot/vmlinuz-2.6.32-44-generic /boot/vmcoreinfo-2.6.32-44-generic
``` con esto hacemos algo de lugar y preservamos una imagen de kernel que deberia servir para iniciar la maquina, la que corresponde al kernel 2.6.32-45-generic y que si se elige mediante el menu del GRUB deberia funcionar adecuadamente.

Una vez borrados esos archivos sugiero hacer ```
sudo dpkg --configure -a
``` en una terminal/consola.
En base a los resultados que arroje vemos como seguimos. Salvo que subestime la situacion, creo que estamos cerca de resolver el tema.

---

### Post by mecdem on 2013-01-28
> ...Salvo que subestime la situacion, creo que estamos cerca de resolver el tema.

¡Vamos todavía!!
¡Adelante!! :p
______

Pregunta aclaratoria (aunque sea redundante):

Quedamos en que por ahora solo puedo trabajar en la consola, no hay entorno gráfico.
Una vez en la consola ¿repito siempre la secuencia 'sudo mount /dev/sda5 /mnt... ...sudo chroot /mnt?
Eso me deja 'parada' en root@ubuntu:/#

¿Desde ahí va la instrucción?
```
sudo rm /boot/config-2.6.32-44-generic /boot/abi-2.6.32-44-generic /boot/initr.img-2.6.32-44-generic /boot/vmlinuz-2.6.32-44-generic /boot/vmcoreinfo-2.6.32-44-generic
``` ¿Todo en una sola línea?
______

Si todo fue bien, sigo con esta instrucción:
> Una vez borrados esos archivos sugiero hacer
```
sudo dpkg --configure -a
```
(...más la oración a San Ignuzio... aunque no sé si nos está haciendo mucho caso...)

MEC

---

### Post by guillermolisi on 2013-01-28
Si, a todo lo que acabas de preguntar.

---

### Post by mecdem on 2013-01-29
Hice el 'remove' archivo por archivo. Todo OK salvo:
/boot/initr.img-2.6.32-44-generic

```
sudo: unable to resolve host ubuntu
rm: cannot remove 0/boot/initr.img-2.6.32-44-generic': No such file or directory
```

Revisando con ls -al /boot, el archivo está ahí, la sintaxis se ve correcta...
Pero no se borra. Los permisos son -rw-r--r--
____

¿Continúo con
root@ubuntu:/# sudo aptitude update
root@ubuntu:/# sudo aptitude safe-upgrade
o antes vemos de borrar ese archivo y/o algunos otros?
____

MEC

---

### Post by guillermolisi on 2013-01-29
> **mecdem said:**
> Hice el 'remove' archivo por archivo. Todo OK salvo:
/boot/initr.img-2.6.32-44-generic

```
sudo: unable to resolve host ubuntu
rm: cannot remove 0/boot/initr.img-2.6.32-44-generic': No such file or directory
```

Revisando con ls -al /boot, el archivo está ahí, la sintaxis se ve correcta...
Pero no se borra. Los permisos son -rw-r--r--
____

¿Continúo con
root@ubuntu:/# sudo aptitude update
root@ubuntu:/# sudo aptitude safe-upgrade
o antes vemos de borrar ese archivo y/o algunos otros?
____

MEC
Me llama la atencion que el error mencione "0/boot/init....." cuando deberia decir solo "/boot/init..."

Podrias confirmar si no hubo un error de tipeo en la linea de comando que usaste para borrar ese archivo, o si transcribiste el error con un typo que le agrego el "0" al path ?

Suponiendo que no se puede borrar ese archivo posiblemente debido a que el file system requiere de una revision con fsck, y antes de continuar, sugiero correr ese comando antes de montar la particion /dev/sda5 para luego realizar el chroot desde la sesion Live.

Los pasos serian:
[LIST]
[*]Iniciar la sesion Live
[*]En una terminal/consola ingresar ```
sudo fsck -v /dev/sda5
```
[*]Suponiendo que finaliza corrigiendo defectos en el filesystem, probar de borrar ese archivo "rebelde"
[*]Reiniciar la maquina en modo Live y proceder con el metodo para lograr el chroot
[*]En una terminal/consola correr ```
sudo dpkg --configure -a
``` y si no aparecen errores proseguir con ```
sudo aptitude update
sudo aptitude safe-upgrade
```
[/LIST]

---

### Post by mecdem on 2013-01-29
> Me llama la atencion que el error mencione "0/boot/init....." cuando deberia decir solo "/boot/init..."

Sorry, no ví ese 0.
Fue error de tipeo mío al transcribir aquí el mensaje de error.
______

> ...Los pasos serian: ...
Tomo nota y me pongo a hacerlo.

Gracias.

MEC

---

### Post by mecdem on 2013-01-30
Descubierto el misterio del "rebelde":

No es /boot/initr.img-2.6.32-44-generic
sino /boot/initr**d**.img-2.6.32-44-generic

Ni cuando hice el ls -al /boot lo noté.

Está eliminado.
______

Corrí el sudo dpkg --configure -a

```
Processing was halted because there were too many errors
```

Lo corrí nuevamente y concluyó con igual resultado.
______

Espero instrucciones.
Gracias. Abrazo.
MEC

---

### Post by guillermolisi on 2013-01-30
> **mecdem said:**
> Descubierto el misterio del "rebelde":

No es /boot/initr.img-2.6.32-44-generic
sino /boot/initr**d**.img-2.6.32-44-generic

Ni cuando hice el ls -al /boot lo noté.

Está eliminado.
______

Corrí el sudo dpkg --configure -a

```
Processing was halted because there were too many errors
```

Lo corrí nuevamente y concluyó con igual resultado.
______

Espero instrucciones.
Gracias. Abrazo.
MEC

Bien por la observacion sobre el nombre correcto del archivo !

Podrias mostrar las primeras lineas de la corrida de "sudo aptitude --configure -a" ? Ahi deberiamos poder ver las causas de que aun persistan tantos errores.

Aun nos queda la actualizacion desde el LiveCD como ultimo recurso :) Veamos esas causas y luego decidimos que alternativa seguir.

---

### Post by mecdem on 2013-01-30
> Podrias mostrar las primeras lineas de la corrida de "sudo aptitude --configure -a"?

Por favor, recordáme la sintaxis para que el proceso se desarrolle paso o paso o 'pagina a página'.
______

> Aun nos queda la actualizacion desde el LiveCD como ultimo recurso :) Veamos esas causas y luego decidimos que alternativa seguir.

De acuerdo.
Sea como fuere, este hilo viene siendo toda una cátedra para mí.
Muchas gracias.
______
MEC

---

### Post by guillermolisi on 2013-01-30
> **mecdem said:**
> Por favor, recordáme la sintaxis para que el proceso se desarrolle paso o paso o 'pagina a página'.
______
MEC

```
sudo less /var/log/aptitude
``` y ```
sudo less /var/log/dpkg.log
``` En este ultimo las lineas que interesan son las que corresponden a la ultima fecha de ejecucion, la mas reciente, y a partir de que avisa que hay algun problema. El resto de los problemas que puedan aparecer en ese log por ahora no son para tomar en cuenta ya que muchos seran consecuencia de los primeros.

Estamos hablando de los logs que estan almacenados en /dev/sda5, asi que esta particion debera estar montada (no hace falta aplicar todo el procedimiento para el chroot).

Suponiendo que se monta en /mnt, entonces habra que anteponer este prefijo a cada path de los logs mencionados antes.

---

### Post by mecdem on 2013-02-03
Ingresé a la consola (tty1)
En ubuntu@ubuntu:~$ sudo mount /dev/sda5 <enter>
En ubuntu@ubuntu:~$ sudo less /var/log/aptitude <enter>

Salida:
/var/log/aptitude (END)
que queda sobreiluminado
Si doy otro <enter> la salida es (END)
también sobreiluminado.
¡Y no puedo hacer nada más! No sé salir del proceso.

Probé a salir con Ctrl+C y Ctrl+Q, lo intenté con Ctrl+Alt+C y +Q... nada, quedé atrapada. A lo único que responde es a Alt+F7, con lo que regreso a la pantalla de opción Probar/Instalar Ubuntu, que es de donde había pasado a la consola.
_______

Apagué el equipo. Comencé de nuevo encontrando que la tty1 solo me muestra el cursor titilando en el ángulo superior izquierdo. Abrí una tty2 que me muestra el prompt de la manera habitual. Allí reintenté el proceso solo que -no estaba segura de si correspondía o no- luego de la linea 
ubuntu@ubuntu:~$ sudo mount /dev/sda5 <enter>
corrí la línea
ubuntu@ubuntu:~$ sudo chroor /mnt
y en root@ubuntu:/# sudo less /var/log/aptitude <enter>
con el mismo resultado anterior

Nuevamente apago el equipo, reinicio hasta llegar a la pantalla de opción Probar/Instalar Ubuntu y sucede esto:

- ctrl+alt+F1 da una pantalla con solo el cursor titilando en el ángulo superior izquierdo.
- ctrl+alt+F2 lo mismo: da una pantalla con solo el cursor titilando en el ángulo superior izquierdo.

Si quiero una consola utilizable tendría que abrir la tty3... que también se trabaría. Evidente: no sé salir de esos procesos.

¿Una ayudita, pls?
______

De paso: antes de la pantalla de opción Probar/Instalar Ubuntu sigue apareciendo el mensaje que dice que este equipo tiene 0 bit de espacio, siempre muy fugaz porque enseguida lo tapa la pantalla de opción.
______

Gracias. Saludos.
MEC

---

### Post by mecdem on 2013-02-03
¡Este post es solo de 'celebración':
\\:D/\\:D/

¡ES EL #50!
:!:  :!:  :!:

¿Te acuerdas de estas frases en el post #9)
> Me gusta la gente con tu actitud !![QUOTE] 
Je, je... Quizás lleguen a pesarte tus palabras cuando este hilo vaya por la entrada N° 100 en tu esfuerzo porque MEC entienda...[/QUOTE]

Todavía faltan 50 posts para el #100, pero quizás ya te están pesando tus palabras... Ánimo... :D

Mis felicitaciones y mi agradecimiento por tu paciencia.
=D>=D>

Abrazo.

---

### Post by guillermolisi on 2013-02-03
> Ingresé a la consola (tty1)
En ubuntu@ubuntu:~$ sudo mount /dev/sda5 <enter>
En ubuntu@ubuntu:~$ sudo less /var/log/aptitude <enter>Mec, para montar una particion hay que mencionar cual es el punto de montaje antes de la particion: ```
sudo mount /mnt /dev/sda5
```

Hecho esto, para ver cualquier contenido en esa particion montada, hay que referenciar tambien al punto de montaje (sino siempre traera contenidos desde el / directory activo, en este caso el pendrive): ```
sudo less /mnt/var/log/aptitude
``` Para salir de less con solo ingresar "q" (sin las doble comillas) es suficiente. Para navegar en el archivo con less, RePag/AvPag hace el trabajo de mover las paginas. Las flechitas tambien funcionan.

Para futuros inconvenientes como este con less, en una linea de comando ingresa ```
man <comando>
``` y tendras enseguida como trabajar adecuadamente.

---

### Post by mecdem on 2013-06-20
Hola MahaGurú Lisi.

Quisiera retomar este hilo.
¿Puedo seguir contando con tu paciente guía?

Mientras aguardo tu respuesta, me pongo a repasar lo realizado.
De paso: ¿hay alguna opción que permita guardar en un archivo todo el contenido del hilo?

Gracias.

______

:KS:KS ADVERTENCIA :KS:KS 
PARA EL INTRÉPIDO LECTOR QUE HAYA LLEGADO
HASTA ESTA ENTRADA DEL HILO:

Debes saber que la suspensión de la tarea por tan largo tiempo estuvo motivada solo por situaciones personales mías que me impedían sentarme frente a la pantalla y seguir con continuidad las instrucciones del Gurú.

Ahora vamos nuevamente para adelante.
______

---

### Post by guillermolisi on 2013-06-20
Mec !! Por supuesto que estoy para terminar con lo iniciado !! ;)

---

### Post by mecdem on 2013-06-24
Parece que la maquinita se ha ofendido por su largo tiempo desatendida, porque Houston, we don't have a problem... we have many problems!! :(
______

Trato de retomar la tarea desde las instrucciones del último post. Arranque con el pendrive: OK

Llego a la pantalla que ofrece las opciones “Probar Ubuntu” - “Instalar Ubuntu” (ver post #24, [http://ubuntuforums.org/showthread.php?t=2106468&p=12474560#post12474560](http://ubuntuforums.org/showthread.php?t=2106468&p=12474560#post12474560), imagen en [https://ubuntulife.files.wordpress.com/2011/10/try-intsall.jpg?w=500](https://ubuntulife.files.wordpress.com/2011/10/try-intsall.jpg?w=500))

En este punto, no recuerdo si pulsaba “Probar Ubuntu” o si directamente abría una consola (Ctrl-Alt-F1)
Pruebo los dos caminos.
______

1. Si pulso “Probar...” se produce alguna de estas dos variables:

a) Aparece una advertencia:
'The sistem is running in low-graphics mode - Your screen, graphics card, and input device settings could not be detected correctly. You will need to configure these yourself'. Hay un único botón disponible que dice OK.
Pero en esta primera variable no tengo habilitado el mouse, y el Enter no activa el botón OK. La única forma de salir es apagando la máquina con el botón de encendido / apagado.

b) Aparece la citada advertencia, esta vez con el puntero del mouse habilitado, con el que solo resta pulsar la opción única, OK.
Esto despliega una ventana con varias opcione y sub-opciones.
(No sé si viene al caso transcribirlas. No quiero recargar el post si no es necesario).
Aunque tengo mouse habilitado, no puedo regresar paso a paso hasta la pantalla de opción Probar / Instalar. Salgo apagando la máquina con botón de encendido / apagado.
______

2. Si desde la ventana con las opciones “Probar Ubuntu” - “Instalar Ubuntu” pulso Ctrl-Alt-F1, la pantalla se oscurece como si fuera una consola, pero solo tiene un prompt titilando en el ángulo superior izquierdo, y no responde al teclado.

Nuevamente, la única forma de salir es pulsando el botón de encendido - apagado.

En este punto mi mente ha quedado tan oscurecida como la pantalla :confused:
______

He revisado los posts anteriores, y no me queda claro si tengo que repetir pasos anteriores. Pero no puedo intentar una prueba porque no hallo la manera de acceder a una consola.
¿Cómo se sigue?

---

### Post by guillermolisi on 2013-07-15
Hay que iniciar la maquina en modo Live (Probar Ubuntu), lograr acceso a una consola/terminal y repetir todos los pasos que llevan a cambiar el directorio / por el que esta en el disco (con 10.04), con chroot.

Si la maquina no se inicia correctamente en modo Live (Probar Ubuntu) es posible que sea algun problema de lectura del medio removible/portatil ya que estimo que estas usando el mismo con el cual antes iniciaba sin inconvenientes (ademas, el hardware no ha cambiado). Tambien sugiero revisar meticulosamente los pasos indicados porque podria ser algun equivoco u omision en uno de ellos.

---

