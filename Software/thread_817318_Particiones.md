---
title: "Particiones"
date: 2008-06-03
forum: Software
---

### Post by Vero1 on 2008-06-03
Hola,

Tengo una cuestión con las particiones. Si corro gparted me muestra una de las particiones sin el candado, lo que presupone(si no me equivoco) que no está montada, pero si marco esa partición y pulso el botòn derecho del mouse, lo único que me permitiría es desmontar. No lo entiendo. Por qué no aparece el candado si está montada?

Por otra parte, si corro el Live CD todo esta montado.

Ésto viene porque necesito hacer lugar para instalar Hardy.

Algun comentario por favor.

Gracias.

---

### Post by anarko on 2008-06-03
yo no se de gparted, pero si abris una consola y pones "mount" sin las comillas te muestra, si es que estan montadas las particiones y donde. 

Deberia salirte algo como :
```
anarko@AnArKa:~$ mount
/dev/sda2 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-17-generic/volatile type tmpfs (rw)
/dev/sda3 on /home type ext3 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/anarko/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=anarko)
anarko@AnArKa:~$
```

Ahi me muestra que tengo montado sda2 en el / y sda3 en /home generalemte los discos duros son HDA/B/C/D... o SDA/B/C/D... siendo A,B,D,C el disco A = primario master, B = secundario master y asi, los numeros que lo presiguen son el numero de particion de cada disco.

---

### Post by Vero1 on 2008-06-03
Hola y gracias por contestar.

Puse en práctica lo del mount y me dice:

veronica@veronica@veradri:~$ mount
/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)

Yo tengo 3 particiones: hda1 que está montado
hda2 que es el Swap
hda3 que NO está montado

Hice un mkdir para la que no está montado pero despues cuando pido que lo monte me dice que no lo encuentra en el fstab y realmente no está.

Cuando se hace un mkdir debería figurar en el fstab?

Qué tengo que hacer?

Gracias

Me olvidé de decir que tambien me informa que no están en orden las particiones y no lo están porque cuando hice una ampliación el Swap no quedó en último lugar.

---

### Post by anarko on 2008-06-04
Para montar una particion tenes 2 opciones:
1: Ir a "Lugares" y donde dice "soporte de XXXGb" le das click y la monta solito sin preguntar, y deberia agregarte un icono en el escritorio para accederla.

2: usar el comando mount, para esto tenes que crear la carpeta donde queres que se monte la particion y usar el comando "sudo mount -t auto /dev/hda3 /path/a/la/carpeta" el "-t auto" uso yo para no complicarme, o por costumbre ya no recuerdo, pero es para dericle el tipo de sistema de archivos que tiene la particion.

Para agregarlo en el fstab tenes que editar el archivo /etc/fstab, pero eso es ya mas complicado y tenes que darle algunas opciones que dependen del tipo de  sistema archivos en que esta formateada la particion.

PD1: el comando mkdir es solamente para crear carpetas.

PD2: jeje recien probando me di cuenta de lo que pasa.
```

anarko@AnArKa:/media$ umount /media/disk
umount: /media/disk no está en fstab (y usted no es el usuario root)

```
es porque no puse "sudo" adelante ( aqui entre nos. ODIO EL SUDO )

PD3: Sobre lo del orden de las particiones, es nuevo para mi, yo el swap la pongo siempre primero porque siempre crei que si el disco si tiene que andar alternando entre escribir/leer los datos y escribir/leer en la swap le quedaria mas comodo si esta al principio del disco y no al final.Pero eso para mi es mas brujeria que otra cosa, si alguien sabe como funcionan los discos por dentro y como maneja los datos el kernel ke me desasne.

---

### Post by faktorqm on 2008-06-04
> **anarko said:**
> 
PD3: Sobre lo del orden de las particiones, es nuevo para mi, yo el swap la pongo siempre primero porque siempre crei que si el disco si tiene que andar alternando entre escribir/leer los datos y escribir/leer en la swap le quedaria mas comodo si esta al principio del disco y no al final.Pero eso para mi es mas brujeria que otra cosa, si alguien sabe como funcionan los discos por dentro y como maneja los datos el kernel ke me desasne.

Muchas preguntas... Voy a intentar explicarte lo mejor que pueda. Lo que vos preguntas, depende mucho del disco y de una cuestion mas estadistica que otra cosa. Para empezar: la swap es lo mismo en cualquier parte. Ahora, lo que si seria conveniente pensar, es, en un disco grande (> 300gb) poner la particion de /home y swap una a continuacion de la otra.
Esto tambien depende de la tecnologia de lectura del disco, tamaño de la caché y velocidad de RPM. Supongamos que tenemos un estandard sata, de 150 mbit/s, 7200RPM y 8mb de cache, de 500 gb. Bueno, existe algo que se llama tiempo de acceso de lectura, que es el tiempo maximo que el disco tarda en leer algo en cualquier parte del disco. Esto es importante remarcarlo, por que cuanto menor sea este valor más rapido va a leer. Ahora, como se podria minimizar aún más este tiempo? Poniendo las particiones que mas se van a escribir juntas. En nuestro caso, puede ser el /home y el swap. Internamente no trabaja tan "cuadradamente", pero sino no termino mas....:D
Si te fijas las especificaciones tecnicas de un disco, por ejemplo seagate de 160gb sata, tarda por ejemplo, 350 milisegundos. Un disco "generico" (no quiero poner marca para no ofender a nadie) capaz tarda 550 ms. y se nota mucho la diferencia. 
Capaz omiti varios aspectos un poco mas tecnicos, pero si tenes dudas volve a preguntar y ya. Salu2!!

---

### Post by anarko on 2008-06-04
En tonces no estaba tan pifiado yo, pero yo no pondria el swap y el home, yo pondria swap y / ya que si tengo que leer todas las librerias para iniciar un programa y levantarlas a la swap le va a kedar mas comodo, ahora con la Pc que tenemos hoy en dia rara vez se usa la swap.

---

### Post by Vero1 on 2008-06-04
Hola de nuevo anarko,

Probé tu comando pero me envía al manual de mount...

Mi idea original es agrandar la partición hda3 porque le precede un espacio sin asignar de mas de 3 Gb, porque quiero hacer una nueva partición para Hardy.

Con el LiveCD puedo en primer lugar montar hda3? y luego agrandarla?

Gracias

---

### Post by anarko on 2008-06-04
Eso mismo hice yo cuando instale HH en el laburo, levanta con el live CD ( pero sin montarlas ) cambiale el tamaño a las particiones con el gPrted o con lo que mas te guste. ( Tarda mucho muchisimo, ponete una paba y hacete unos mates proque la espera es larga )

---

### Post by Vero1 on 2008-06-05
anarko, el problema es que no tomo mate :-)

Bueno, veremos qué sucede con el LiveCD.

Gracias por tu tiempo y saludos.

---

### Post by sergiom99 on 2008-06-05
me sumo a preguntar una burrada:
si tengo 2Gb RAM, puedo tener solo 512Mb de SWAP?
Ahora tengo 1Gb de SWAP, pero como voy a hacer un clean install, aprovecho para reparticionar.
gracias!

---

### Post by Mister X on 2008-06-05
> **sergiom99 said:**
> me sumo a preguntar una burrada:
si tengo 2Gb RAM, puedo tener solo 512Mb de SWAP?
Ahora tengo 1Gb de SWAP, pero como voy a hacer un clean install, aprovecho para reparticionar.
gracias!

Si, podés, lo que no vas a poder hacer es hibernar, ya que el contenido de la RAM te lo baja a la SWAP.
Si no te interesa esa funcion, no es necesario destinar tanto espacio a la SWAP, yo tengo 2GB de RAM y 1GB de SWAP, con un uso intensivo de la maquina: muchos programas abiertos, maquinas virtuales corriendo, etc, la SWAP solo la llegó a ocupar en un 3% como maximo

---

### Post by sergiom99 on 2008-06-05
en realidad mas por curiosidad q otra cosa. creo q no hay != entre .5Gb o menos de disco.

---

### Post by anarko on 2008-06-06
> **Vero1 said:**
> anarko, el problema es que no tomo mate :-)

Bueno, veremos qué sucede con el LiveCD.

Gracias por tu tiempo y saludos.

... seguira esperando que termine gparted? quiero saber como termina la novela....

---

### Post by Vero1 on 2008-06-06
anarko no sé cómo pero se han mezclado aquí dos temas :)

Con respecto al montaje ya lo he solucionado. Resulta que en esa partición está Debian y no estaba montada...(es que soy todavía novata y mas con Debian). Bueno la cuestión es que en ubuntu-es me dieron el comando necesario para montar la partición de Debian y ya está, pero... siempre hay un pero.

He decidido hacer un dist-upgrade o sea que no tocaré la partición de Debian.
Desaparecerá Gutsy y quedará Hardy en su lugar.

Así que la novela se termina aquí, aunque voy a abrir otro thread con otro problema que se me presenta para hacer backup.

Será hasta la próxima entonces.

Gracias por tu intervención y saludos.:guitar:

---

