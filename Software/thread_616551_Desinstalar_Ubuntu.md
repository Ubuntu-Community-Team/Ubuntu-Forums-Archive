---
title: "Desinstalar Ubuntu"
date: 2007-11-18
forum: Software
---

### Post by ketzelleshelle on 2007-11-18
Hola quisiera saber como desinstalar Ubuntu. Ni siquiera estoy seguro de adonde lo instalé, si no me equivoco en la particion D de windows (que está compartida con otras cosas de windows), pero resulta que además me han quedado unas carpetas en distintas particiones  de windows (que cuando las abro se ven vacias) asociadas a Ubuntu que no se me permite quitarlas.

Por otro lado cuando inicio en Ubuntu tarda muchísimo, empieza a hacer comprobaciones en la pantalla negra y recién despues de un rato largo inicia.

Lo que no quiero es **FORMATEAR** ya que como les dije en D tengo otras cosas (¿y porqué han quedado carpetas asociadas a Ubuntu en otras particiones?)

Espero que puedan ayudarme, porque hace tiempo que estoy con esto, quiero dejar todo limpio y volver a instalar.

Muchas Gracias.

---

### Post by staticvoid on 2007-11-18
debes buscar una aplication llamado "thunar" y installar lo en ubuntu. despues en un terminal pones "gksu thunar" y entres tu contrasenna. Asi puedes hacer todo lo que qieres pero QUIDADO, eres root.

sv

sudo apt-get install thunar

gksu thunar

******* (contrasena ;])

---

### Post by fscodelaro on 2007-11-18
Tenes que ir a una terminal y poner:

```
sudo fdisk -lu
```

Te va a pedir la contrasena y luego copias la salida de ese comando aqui en el foro. Lo que va a decir es que particiones tiene tu PC de forma de saber cual hay que eliminar para "desinstalar" ubuntu.

---

### Post by fscodelaro on 2007-11-18
Dicho sea de paso, no entres a thunar y empieces a borrar directorios con permisos de root!! Si no tenes cuidado y no sabes bien que hay que borrar, mejor no hacerlo. De esa manera podes perder tus particiones de windows tambien (ejemplo, borrando el directorio /media, que es donde son montadas por defecto).

El comando mas informativo es

```
sudo fdisk -lu
```

Posteas la salida aca y te podemos seguir ayudando.
Y cualquiera sea la medida a tomar, y aunque cueste trabajo y algunos CDs/DVDs virgenes, es mejor siempre tener un backup, aunque sea de las cosas esenciales,  sea que decidas trabajar en windows o cualquier otro sistema operativo. Va de onda.

---

### Post by ketzelleshelle on 2007-11-18
Fscodelaro:

Gracias por la ayuda.

Este es el resultado de lo que vos me pediste:

[B]Uso:   fdisk [-b SSZ] [-u] DISCO    Cambia tabla de particiones
       fdisk -l [-b SSZ] [-u] DISCO Lista tabla(s) de particiones
       fdisk -s PARTICIÓN           Obtiene tamaño de particiones en bloques
       fdisk -v                     Obtiene versión de fdisk
El valor de DISCO tiene el formato /dev/hdb o /dev/sda
y el valor de PARTICIÓN tiene el formato /dev/hda7
-u: Obtener Principio y Final en sectores (en lugar de cilindros)
-b 2048: (Para algunas unidades MO) Utilizar sectores de 2048 bytes [/B]

Y de paso te hago la siguiente pregunta: Cómo hago para que las partes compartidas entre ambos sistemas dejen de pertenecer a Ubuntu?

Gracias de nuevo.

Ketzel.

---

### Post by fscodelaro on 2007-11-18
Hola Ketzel,

creo que ingresaste mal el comando.Te habras confundido quizas la ele con un 1? Proba copiando y pegando en la terminal desde aca:

```
sudo fdisk -l
```

No se bien eso que decis de las "partes compartidas". Realmente me ayudaria la salida del comando que esta ahi arriba para entender las particiones en tu sistema.

Federico

---

### Post by ketzelleshelle on 2007-11-18
Bueno ahora creo que sí:

[B]Disco /dev/hda: 82.3 GB, 82348277760 bytes
255 cabezas, 63 sectores/pista, 10011 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/hda1   *           1        2932    23551258+   c  W95 FAT32 (LBA)
/dev/hda2            2933       10011    56862067+   f  W95 Ext'd (LBA)
/dev/hda5            2933        5984    24515158+   7  HPFS/NTFS
/dev/hda6            8979       10011     8297541    7  HPFS/NTFS
/dev/hda7   *        5985        8848    23005048+  83  Linux
/dev/hda8            8849        8978     1044193+  82  Linux swap / Solaris

Las entradas de la tabla de particiones no están en el orden del disco

Disco /dev/hdb: 122.9 GB, 122942324736 bytes
255 cabezas, 63 sectores/pista, 14946 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/hdb1               1       14946   120053713+   7  HPFS/NTFS[/B]


Lo que te digo de las "partes compartidas" es lo siguiente: en un momento recuerdo haber hecho algo que me posibilitaba "compartir" archivos de windows con Linux... Entonces me quedaron visibles en distintas particiones de windows unas carpetas con el nombre "trash" que están vacías (al menos en windows) y no puedo borrarlas...

Gracias por la ayuda.

Ketzel

---

### Post by fscodelaro on 2007-11-19
Bueno, si mal no entiendo la info, tenes dos discos, primary y slave. El segundo disco es todo NTFS o sea esta tomado por windows asi que ese queda fuera de la discusion de ahora en adelante.

En el disco 1 tenes 6 particiones, 1 primaria y 1 logica (hda2) que contiene 4 a su vez, y que vienen en este orden:

Win (hda1) particion primaria
Win (hda5) - extendida
Linux (hda 7) - Linux (esta es la raiz, y es lo que queres borrar)
Linux swap (hda8 ) - el espacio de swap que tambien queres borrar
Win (hda 6) - Otra particion windows

O sea, las particiones que tenes que borrar son hda7 y hda8 si queres sacar al ubuntu, y re-dimensionar de forma de dar ese espacio a hda6 o hda5 (o un poco y un poco). Como se llamen esas particiones en la notacion de windows, solo vos sabras (D:, E:, etc)

Lo que yo entendi es que querias desinstalar ubuntu y volver a windows en todo el disco, y los pasos siguientes estan basados en esa asuncion. El procedimiento para desinstalar ubuntu consiste en dos pasos basicamente:

1) restaurar el Master Boot Record de Windows. Que significa? Que Grub (ese menu que aparece cuando booteas) no tome control del booteo, sino que windows lo haga, dado que grub reside en la particion que vas a borrar.

2) borrar las particiones de Ubuntu (en tu caso, hda7 y hda8 ) y redimensionar la 6 o la 5 para que adquieran ese espacio libre, o crear una nueva.


Los pasos en concreto:

1) antes de proceder, backupea todos tus datos importantes. Si no tenes algo removible (CDs / DVDs) donde copiar la info mas importante, al menos copiala a tu segundo disco (el disco 2) y asegurate de no tocar para nada ese disco en los pasos que sigan (estas avisado!!).  Asegurate tambien de que en tu carpeta personal de ubuntu no haya nada que quieras conservar.

2) bajate un programita que se llama Mbrfix.exe, que hace justamente eso, lo conseguis en [http://www.sysint.no/en/Download.aspx](http://www.sysint.no/en/Download.aspx) . Las instrucciones de como usarlo estan en esa pagina. La verdad que nunca lo use asi que en eso no puedo ayudarte. Por lo que yo entendi, es simplemente bajarlo a la raiz del C: , te vas a una terminal en windows y pones "cd \" sin comillas, de forma que el prompt te aparezca como "C:\>" y ahi escribis "MbrFix /drive 0 fixmbr /yes" sin comillas. Ya esta, rebootea para ver si funciona, deberia entrar de una al windows sin ver nada del grub. Si funciona (y solo si funciona) pasa al siguiente paso.

3) borra particiones: inicia la pc con el live CD de ubuntu. Anda a la terminal en Aplicaciones > Accesorios. Ahi escribis:

```
sudo gparted
```

Y vas a entrar a un programa que graficamente te muestra todo tu disco (elegi el disco hda con el selector de la derecha) . Ahi podes facilmente elegir las particiones que queres eliminar, Aplicas los cambios (guarda antes de aplicar! verifica doblemente!). Luego podes re-dimensionar las otras particiones de windows para que usen el espacio que quedo libre (puede ser la que esta antes o la que viene despues).

4) mucha suerte en el proceso. Conserva tu live CD de ubuntu, te puede ayudar a recuperar datos de un disco no booteable (por ejemplo si, o cuando, la instalacion de windows queda corrompida por algun virus o troyano). Y no te pierdas! No descartes esto de por vida. Ubuntu evoluciona rapidamente, con una version nueva cada 6 meses, cada vez mas pulida y con menos errores y mejores aplicaciones. Que no te haya servido ahora no quiere decir que de aca a un anio ya este a la altura de tus expectativas. Quizas dentro de 12 meses le des otra chance, quizas esa vez con la mente un poco mas abierta, en lugar de preguntar "como desinstalar" quizas preguntes "por que ubuntu hace comprobaciones con la pantalla negra antes de iniciar? como las evito?". Hay un tiempo para todo y este no fue el tuyo. Mientras tantos podes seguir usando algunos de los mejores programas que hay en ubuntu como firefox, thunderbird, openoffice, gimp, en sus versiones windows. Una buena manera de correr software bueno sin gastar (y legalmente). Y si algun dia retomas por estos lados, sos mas que bienvenido por aca.

Saludos,

Federico

---

### Post by ketzelleshelle on 2007-11-19
Federico: mil gracias. Me pongo manos a la obra y después te cuento.

Mi intención es seguir con Ubuntu, sólo que me quedó una especie de lío en la maquina y quiero arrancar de cero, de hecho hace una semana me llegaron los cds de gutsy gibbon...

Mas tarde te cuento como me fué.

Saludos.

K.

---

### Post by fscodelaro on 2007-11-19
Ahh entendi mal entonces, disculpas.

Si queres reinstalar ubuntu entonces no hagas el paso 2 ni el paso 3 (y no le prestes atencion al 4).
Solo insertá el CD y decile que lo queres instalar en la particion donde ya está Ubuntu, y que la formatee y ya. Así te va a quedar todo nuevito, no es necesario borrar la partición antes ni restaurar el MBR de windows.

Lo de las carpetas de trash en las particiones windows sigo sin saber como se hace pero si averiguo te digo.

---

### Post by nexopd on 2012-10-16
[SIZE="4"]Hola chicos![/SIZE]

se que este tema esta viejo pero googleando llegue hasta aca y vi que el foro es bastante activo y decidí usarlo.

TENGO EL SIGUIENTE PROBLEMA:

1) Tengo una Notebook (Olivetti Olibook 500) la cual tiene un disco de 120GB particionado y tenia en una particion Windows 7 y en la otra Windows XP.

2) Instale Ubuntu 12.04 Desktop sobre la particion que tenia WINDOWS 7 y anda perfecto! (no me arrepiento)

Peeeeeeeeeeeeeeeeeeeeero el problema es que no se si me olvide de marcar algo, o no se que tengo que hacer para poder prender la compu y que me de la opcion de que Sistema quiero Usar...
**[COLOR="Navy"][SIZE="2"](antes tenia la opcion Windows 7 o Windows XP)[/SIZE][/COLOR]**

**[COLOR="Navy"][SIZE="2"]Me Encantaria poder volver a tener esa opcion, por eso recurro a ustedes... (Poder elegir entre Ubuntu 12.04 y Windows XP)[/SIZE][/COLOR]**

PD: No quiero desisntalar Ubuntu por que me encariñe, pero si no hay opcion y tengo que desinstalarlo y volverlo a instalar para tener esa "opcion" con gusto leo la forma de poder hacerlo :)

Desde ya muchisimas gracias por leer esto y querer darme una mano!
quedo atento a sus indicaciones!
Los Saluda desde La Plara, Buenos Aires, Argentina y para Todo el Mundo... Nex

---

### Post by z37a on 2012-10-17
> **nexopd said:**
> [SIZE="4"]Hola chicos![/SIZE]

se que este tema esta viejo pero googleando llegue hasta aca y vi que el foro es bastante activo y decidí usarlo.

TENGO EL SIGUIENTE PROBLEMA:

1) Tengo una Notebook (Olivetti Olibook 500) la cual tiene un disco de 120GB particionado y tenia en una particion Windows 7 y en la otra Windows XP.

2) Instale Ubuntu 12.04 Desktop sobre la particion que tenia WINDOWS 7 y anda perfecto! (no me arrepiento)

Peeeeeeeeeeeeeeeeeeeeero el problema es que no se si me olvide de marcar algo, o no se que tengo que hacer para poder prender la compu y que me de la opcion de que Sistema quiero Usar...
**[COLOR="Navy"][SIZE="2"](antes tenia la opcion Windows 7 o Windows XP)[/SIZE][/COLOR]**

**[COLOR="Navy"][SIZE="2"]Me Encantaria poder volver a tener esa opcion, por eso recurro a ustedes... (Poder elegir entre Ubuntu 12.04 y Windows XP)[/SIZE][/COLOR]**

PD: No quiero desisntalar Ubuntu por que me encariñe, pero si no hay opcion y tengo que desinstalarlo y volverlo a instalar para tener esa "opcion" con gusto leo la forma de poder hacerlo :)

Desde ya muchisimas gracias por leer esto y querer darme una mano!
quedo atento a sus indicaciones!
Los Saluda desde La Plara, Buenos Aires, Argentina y para Todo el Mundo... Nex

Desde Ubuntu podes acceder a la particion de Windows XP? popr que suele pasar que a veces esta esta mal y al instalar Ubuntu no accede y no reconoce el segundo sistema operativo, por lo cual no te instala en Grub la opcion de boot de Windows XP (ya que no lo ve). Por eso siempre antes de instalar recomiendo pasar chkdsk en windows y apagar correctamente!

Es necesario que comentes si lo ves asi se puede describir que partes siguen para agregar Windows al Grub!

---

