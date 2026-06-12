---
title: "Asqueado con la intalacion de Ubuntu"
date: 2012-05-01
forum: Software
---

### Post by raycol on 2012-05-01
Buenas, ya mosqueado y deprimido por no poder instalar ubuntu os comento el problema:

Tengo un MSI GT780DXR y al instalar ubuntu normal no puedo:

El principal problema es la grafica, la GTX 570M necesita otros drivers, vale.. uso el alternate CD y e conseguido instalar ubuntu pero al instalar el grub.. no me deja.. ya que tengo un RAID 0 y no me detecta las particiones
el dichoso GRUB!!

Buscando en internet e visto que existen optativas, pero por ahora el EasyBCD no va, me pilla windows, pero si pongo la particion de ubuntu no hay quien consiga que inicie.

Ahora mismo tengo ubuntu instalado particiones (SWAP,/home,/) sin grub, y sin manera de arrancar ubuntu... alguna ayuda? :confused:

PDT: Llevo 4 dias intentandolo, probando cosas, terminales, pero ya esque nose que hacer... necesito ayuda encerio.

---

### Post by guillermolisi on 2012-05-01
El RAID 0 que comentas tener, es por software, por hardware o hibrido ?

Si es una instalacion nueva, no una actualizacion, y segun el tipo de soporte que tengas para el RAID 0, el procedimiento puede variar.

Por otra parte, GRUB se instala en el MBR del disco, sea este fisico o logico, asi que no se requiere visualizar/detectar particion alguna para que se instale correctamente.

---

### Post by raycol on 2012-05-01
el raid 0 es por hardware.. por eso mis dudas

---

### Post by guillermolisi on 2012-05-01
QUe controladora estas usando ? Seguro que no requiere de un driver para poder operar un RAID ? (que la convertiria en una controladora hibrida)

---

### Post by raycol on 2012-05-01
Me acabas de matar, se qe el RAID 0 es de bios, ya que casi siempre que inicio con el pc me deja editarlo, montarlos y demas..

Aun asi como podria vertificar eso?


Porcierto a preguntas, tengo una solucion. Ubuntu ya lo tengo instalado, podria usar el EasyBCD para usar el cargador de windows para que cargara ubuntu y solucionado pero,

1) Que punto de montaje "/" "/home" etc, usa ubuntu para levantarse, es decir, en windows es la particion de windows pero ubuntu?

2) Si se el punto de montaje, lo podria poner y logearme, pero saltaria problema de grafica, entonces con un live cd, podria iniciar una terminal y hacer instalaciones en el Disco Duro? y si se pudiera como? :S

Si ya pudo hacer instalaciones en el disco duro tendria ubuntu funcionando y los drivers intalados..  y fin del tema... espero que asi me podais ayudar mas facil

Saludos

---

### Post by guillermolisi on 2012-05-01
Si la controladora esta incorporada a la motherboard y se configura a traves del BIOS lo mas probable es que sea una controladora que administre RAID en forma hibrida para lo cual deberias contar con un driver (extra o puede usar uno que ya exista en el kernel de Linux).

Las controladoras inteligentes, que poseen su propio BIOS, no suelen estar integradas a la motherboard y son muy caras.

El punto de montaje de la particion "/" es el direcotrio raiz /.
El de la particion "home" es el directorio home.
Esto siempre y cuando la persona que instalo eligio esta disposicion. Si no fue asi entonces puede diferir, particularmente "home".

El proceso de booting de Linux es leer la informacion que se encuentra en el MBR del disco rigido que le indique el BIOS, luego el bootloader que encuentre en el MBR le dira que particion usar para el inicio a partir de la seleccion del usuario o la que figure como unica si no hay otros sistemas instalados.

Creo que antes de llevar a cabo todo eso que supones podria ser una solucion, trataria de averiguar en que parte del proceso de instalacion se produjo el inconveniente para no volver a repetirlo.

En todo caso, si es tu primera incursion con Linux, tal vez lo mas aconsejable es volver a instalar prestando especial atencion cuando se instale GRUB.

Esto despues de verificar si Windows vuelve a iniciar una vez quitado Ubuntu (antes de volver a instalar).

---

### Post by juancarlospaco on 2012-05-02
Es una Notebook, seguro es un RAID Fake o Hibrido Emulado.
( [http://www.msimobile.com/level3_productpage.aspx?id=319](http://www.msimobile.com/level3_productpage.aspx?id=319) )

---

### Post by raycol on 2012-05-02
Muchas Gracias por la ayuda...Enserio.

Pos la verdad, el problema es ese [[COLOR=#339900]**guillermolisi**[/COLOR]]("http://ubuntuforums.org/member.php?u=299461"), no es posible instalar el GRUB da un error critico y como ya comente por mucho que ponga "/dev" "/dev/mapper" etc.. no consigo hacerlo rular; y si.. windows se arranca con normalidad.

Aunque no es mi primer encuentro en linux (he salido hace poco de un ciclo medio y lo dimos bastante) 

Segun entendi: Ubuntu necesita GRUB para iniciarse si o si.. :S, me da que tendre que sacrificar el RAID para poder tener ubuntu.

En casa pensando, existe la posibilidad de instalar el GRUB en un pendrive pero para mi eso no es una solucion, aunque si fuera un CD estilo "chamaleon 2" me podria valer.

Tambien existe la posibilidad que use un GRUB2 del EasyBCD, el cual lo use y me permite poner un grub en el arranque pero me sale linea de comandos del grub, podria intentar levantar el ubuntu a mano pero ahi no tengo ni idea de como hacerlo.



Ya lo ultimo seria sacrificar el RAID o FakeRaid como comenta [juancarlospaco]("http://ubuntuforums.org/member.php?u=784640"), pero ya perderia bastante rendimiento y no me agrada mucha esa opcion.

Ya nose que hacer..

---

### Post by guillermolisi on 2012-05-02
Una disposicion RAID 0 nada tiene que ver con el rendimiento del sistema. No se utiliza para mejorar ese factor.

---

### Post by juancarlospaco on 2012-05-02
Off Topic: si es muy critico el tema de rendimiento podes ver de comprar un disco SSD, o Disco de Estado Solido, no son caros hoy dia :)

El Grub Si se puede instalar en un Pendrive, obvio debera estar presente y operativo al momento de Bootear...

---

### Post by raycol on 2012-05-03
Gracias por la ayuda.. al final busque temas de "como instalar grub2 en un fakeraid" y el famoso bumblebee y ahora mismo lo tengo funcionando con el raid ... espero que le ayude a alguien saludos

---

