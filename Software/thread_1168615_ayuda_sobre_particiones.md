---
title: "ayuda sobre particiones"
date: 2009-05-24
forum: Software
---

### Post by joseluis on 2009-05-24
hola..la cuestión es esta y pido ayuda.
Tengo dos discos en mi PC,
1. disco SATA maestro, de 160 gigas, con WinXP y datos varios.
2 disco IDE esclavo, en donde tengo dos particiones, una con Ubuntu 9.04 y otra fat32 con datos.

Quisiera reparticionar el disco SATA poniendo en una particion WinXP y dejar el resto para datos y archivos.

El tema, según tengo entendido, es que al hacer esto, luego el Ubuntu tendría problemas con el grub, el fstab, etc etc etc..

¿cómo lo resuelvo antes de caer en el desastre de tener que reinstalar el ubuntu para reconocer todas las particiones nuevas?

gracias

---

### Post by guillermolisi on 2009-05-24
> **joseluis said:**
> hola..la cuestión es esta y pido ayuda.
Tengo dos discos en mi PC,
1. disco SATA maestro, de 160 gigas, con WinXP y datos varios.
2 disco IDE esclavo, en donde tengo dos particiones, una con Ubuntu 9.04 y otra fat32 con datos.

Quisiera reparticionar el disco SATA poniendo en una particion WinXP y dejar el resto para datos y archivos.

El tema, según tengo entendido, es que al hacer esto, luego el Ubuntu tendría problemas con el grub, el fstab, etc etc etc..

¿cómo lo resuelvo antes de caer en el desastre de tener que reinstalar el ubuntu para reconocer todas las particiones nuevas?

gracias
Depende de como este instalado Ubuntu, en que disco grabo la informacion de inicio.

Si lo hizo en el MBR del segundo disco no deberias tener inconvenientes ya que el trabajo lo harias en el primero. Si es asi, cada vez que quieras iniciar con Ubuntu tendrias que elegir de que disco queres bootear (esto no es dual boot).

Ahora, si tenes dual boot en un solo disco, es otro tema (es cuando te aparece un menu con la opcion de seleccionar que sistema operativo queres iniciar).

---

### Post by joseluis on 2009-05-24
El dual bot está en el primer disco, es decir, en el mbr

---

### Post by guillermolisi on 2009-05-24
> **joseluis said:**
> El dual bot está en el primer disco, es decir, en el mbr
O sea que vos queres volver a particionar el disco con XP que actualmente tiene una sola particion.

Siendo que tenes XP en ese disco podrias usar alguna herramienta Windows (partition Magic, por ejemplo) para hacerlo, previa defragmentacion del mismo.

Nunca lo hice con maquinas con dual boot, pero se me ocurre que no deberia haber cambios en el MBR ya que no estaria instalando nada nuevo.

Por las dudas, es recomendable un backup del dsco que vas a subdividir (un clonado seria ideal).

Que alguien con mas experiencia en esta labor haga su aporte.

---

### Post by staar on 2009-05-24
para particionar el disco, podés tranquilamente usar, con el disco de windows desmontado, el Editor de Particiones de ubuntu (gparted), achicarías la partición que tiene Ventanas (es altamente recomendable desfragmentar el disco previamente), y crearías una nueva en el espacio libre...

si no tenés explicitada ninguna partición del primer disco en el fstab, no creo que tengas problemas, ya que el montado lo está haciendo HAL, y detectaría las nuevas particiones al reiniciar...

con el GRUB tampoco creo que tengas problemas, ya que ubuntu está instalado en el segundo disco, donde las particiones no van a cambiar, y el número de la partición de ubuntu seguirá siendo el mismo, esto si no reinstalás windos, en cuyo caso sobreescribiría la MBR del primer disco, donde está GRUB, y tendrías que volver a escribirlo (cualquier cosa preguntá, no es difícil), pero las configuraciones no se van a perder (con el menu.lst actual, en el escenario que querés, es suficiente, no tendrías que modificarlo)...

saludos

---

### Post by Hei Ku on 2009-05-24
Aclaracion: El editor de particiones de Ubuntu es gparted, no gedit.

---

### Post by joseluis on 2009-05-24
Gracias Staar. Ese es el dato que estaba necesitando.
Se como hacer la nueva particion con Gparted, y eso no hay problemas, pero tenía esas dudas sobre el grub, fstab y todo eso. Pero con lo que aclarás, me parece que no tendría problemas.
gracias nuevamente

---

### Post by Brath-ga on 2009-11-12
Vamos a ver.
No encontré por aquí nada parecido a lo que a mi me sucede.
Hasta ayer tenía un disco ATA en IDE1 de 80 GB con XP y 2003 server colocado como primario y otro colocado en el mismo IDE de 80 GB como secundario en donde instalara Ubuntu.
Aunque actualmente utilizo solo Ubuntu, todo iba perfectamente con el Grub en el MBR del disco de 80 GB.
Digo hasta ayer, porque se me hacía pequeño el de 20 GB, me compré uno Sata de 500 GB.
Tenía entendido que los SATA arrancaban de primeros con respecto a los ATA con lo cual solo fué sacar el disco esclavo de Ubuntu y sin tocar otra configuración colocar el nuevo en SATA1.
Particioné el nuevo con 8 GB para "/", 20 GB para "/home", 2 GB para "Swap" y 350 GB para /Datos.
Instalé el Karmic y todo correcto, pero al entrar en la utilidad de discos me aparece que ahora tengo dos MBR y lo que es peor, el disco que figura como hda0 es el antiguo de 80 GB cuando yo quiero que sea el nuevo.
Alguna sugerencia ?

---

### Post by biale on 2009-11-12
Todo disco que se precie de tal tiene una zona denominada MBR. En esa zona puede tener instalado un cargador de arranque cualquiera o no tener ninguno. Por ejemplo yo tengo en un disco el MBR de grub 0.97 legacy y en otro el de grub 2.

Si recordas, Karmic te ofrecía la posibilidad de instalar sobre el mbr de uno de los discos, en otro o en todos. Lo que abunda no daña, pero puede confundir.

Ahora bien, en principio grub recibe la enumeración del bios y habría que intentar modificar la cosa desde ahí. No tengo ahora una computadora Linux cerca, pero acordate que es posible que se necesite tocar luego a ubuntu.

Saludos.

---

### Post by Brath-ga on 2009-11-13
Bueno, ya los cambié.
Ahora el problema es otro.
Según entendiera el SATA sería reconocido siempre como primario, pero no fué asi. Me aparecía como sda el IDE y como sdb el SATA.
Le cambié los jumpers al IDE para ponerlo como esclavo y lo coloqué tambien en el cable de datos como esclavo.En la bios lo puse para que arrancase de 1º el Sata. Nada de nada.
Con el editor de particiones le cambié el boot para que arrancase desde el SATA y arranca, pero tuve que tener cuidado que el Grub se instalase en sdb1 que sigue siendo el SATA.
Particioné el disco de nuevo e instalé Karmic de la siguiente manera:
8 GB para "/" como primaria
20 GB para "/home" como primaria
2 GB para "swap" como lógica
Intenté una partición de 350GB como "/Datos", pero me dió error varias veces y lo dejé para hacerlo en otro momento.
Parece ser que el error está en no poder instalar "dev/disk"

---

### Post by Brath-ga on 2009-11-17
Solucionado.
Parece una chorrada, pero al cambiar el disco SATA de SATA1 a SATAII_1 me reconoce como sda dicho disco, por lo tanto como hd0 y arranca el grub perfectamente.
Ahora mi duda es otra.
Dejé 350 GB sin particionar con la la intención de hacer de el una unidad para datos pero independiente de la carpeta "/". Quisiera formatearla en FAT32 para poder acceder a los datos desde Ventanas, que está en el 2º disco duro.
Debo de formatearla como "primaria" o como "extendida" ?

---

