---
title: "Dos Discos: XP/Ubuntu. Problema GRUB no puedo entrar XP"
date: 2008-06-22
forum: Software
---

### Post by Alvaro77 on 2008-06-22
Hola a todos,

Soy nuevo en este foro y espero que este thread este bien aqui.

Bueno, comenzando con el pronlema: he instalado Ubuntu en un disco y tengo XP en otro, he pasado por un par de otros problemitas q he podido solucionar gracias a hilos que encontraba por este foro pero ahora estoy casi en la ultima fase, por decirlo así, y creo que es mas conveniente especificar mi problema especificamente.

Como dije tengo dos discos en uno Ubunto y en el otro XP, la cuestion es que cdo inicio y entro al menu GRUB (ya que no me aparece el menu de eleccion del GRUB de S.O.s automaticamente, cosa que tambien es un problemita porque seria bueno q apareciera el menu atomat. asi mi flia puede acceder a XP), me aprece las opciones para elegir Ubuntu o XP, si selecciono XP se queda tildado sin avanzar y este es mi problema. Yo logré q apareciera la opcion del XP en este menu editado el archivo menu.lst del grub y agregando lo siguiente:

> title		Otros sistemas operativos:
root

title		Windows XP Professional SP2
root		(hd1,0)
savedefault
makeactive
chainloader	+1

entonces menu.lst quedó así:

> ## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=fadd594d-123e-485d-ad70-84a19d5d62b4 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=fadd594d-123e-485d-ad70-84a19d5d62b4 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

title		Otros sistemas operativos:
root

title		Windows XP Professional SP2
root		(hd1,0)
savedefault
makeactive
chainloader	+1

### END DEBIAN AUTOMAGIC KERNELS LIST

bien, les paso un poco de info sobre configs en gral:

Discos rigidos:

HD1 10 GB, MASTER chanel 0, SO: Ubuntu > 1ro en la prioridad de booteo
HD2 6 BG, MASTER chanel 1, SO: XP 

#sudo fdisk -l, muetra lo siguiente:

> Disco /dev/sda: 10.2 GB, 10204766208 bytes
255 cabezas, 63 sectores/pista, 1240 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x423e423d

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1        1182     9494383+  83  Linux
/dev/sda2            1183        1240      465885    5  Extendida
/dev/sda5            1183        1240      465853+  82  Linux swap / Solaris

Disco /dev/sdb: 6402 MB, 6402170880 bytes
255 cabezas, 63 sectores/pista, 778 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0xa339a339

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdb1   *           1         777     6241221    7  HPFS/NTFS


Espero que esta info sea suficiente para que puedan ayudarme con esto, como se darán cuenta basicamente lo que quiero es que al inciarl la pc me de la opcion de ingresar a Ubuntu o XP y que funcionen ambas.

gracas.-

---

### Post by Mauro22 on 2008-06-22
Proba asi:

title        Microsoft Windows XP Professional
root        (hd1,0)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1

---

### Post by Alvaro77 on 2008-06-22
> **Mauro22 said:**
> Proba asi:

title        Microsoft Windows XP Professional
root        (hd1,0)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1

Muchas Gracias Mauro, era asi!...

Una ultima cosita por favor. Como dije antes para ir la menu de seleccion de SO del GRUB al inicializarse el equipo debo precionar escape cdo dice algo como "press ESC to enter the nenu.." preciono escape y recien ahi me da el menu para elegir yo quisiera que aparciera solo ya que en mi casa hay otras personas q usan la PC y usan XP.. como puedo hacer???

saludos.-

---

### Post by Mauro22 on 2008-06-22
Fijate en el menu.lst tendras algo asi: (al principio)

```

# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

```

supuestamente tendrias el hiddenmenu sin #. 

Ponele # al principio para que el GRUB ignore esa linea o borrala, como mas te guste.

---

### Post by Alvaro77 on 2008-06-22
> **Mauro22 said:**
> Fijate en el menu.lst tendras algo asi: (al principio)

```

# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

```

supuestamente tendrias el hiddenmenu sin #. 

Ponele # al principio para que el GRUB ignore esa linea o borrala, como mas te guste.

Gracias de nuevo... efectivamente habia que anteponer el "#" para q ignore la linea y no oculte el menu...
Otra cosita :P dura un par de segundos el menu nomas y luego entra a Ubuntu, muy poco y casi q no da tienpo a elegir habrá alguna forma de lograr q se mantenga mas tiempo... busque en por ahi en menu.lst haber si habia por el estilo pero no pude encontrar nada...

---

### Post by Mauro22 on 2008-06-22
Como que no lo encontraste? Si era un perro seguro que te mordia.

Esta arriba de hiddenmenu

```

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

```

---

### Post by Alvaro77 on 2008-06-22
> **Mauro22 said:**
> Como que no lo encontraste? Si era un perro seguro que te mordia.

Esta arriba de hiddenmenu

```

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

```

jajaja me habia re echo la cabeza de que entre tanto texto no lo hiba a encontrar y eso me cegó jeje...
gracias kpo la tenes muy clara...

Y ya que estamos te consulto otra cosa, cdo fui a cambiar en las opciones de apariencia para poner los efectos me pidio q instalara no se q cosa creo q sobre los controladores de la placa de video y q reinicie la pc y dspues los cambie, la cuestion es q ahora no me deja poner resoluciones mayores a 1024x780.. :(
mi placa: GeForce nvidia 6800

salutes.-

---

### Post by faktorqm on 2008-06-25
Anda a sistema -> administracion -> gestor de paquetes synaptic. buscas "envy-ng" y lo instalas. Vas a aplicaciones -> herramientas del sistema -> envi-ng y te instalas el controlador de nvidia. Luego vas a aplicaciones -> herramientas del sistema -> nvidia settings y configuras todo como mas te guste. Salu2!

---

