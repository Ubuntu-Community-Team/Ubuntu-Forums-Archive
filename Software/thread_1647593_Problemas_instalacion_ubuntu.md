---
title: "Problemas instalacion ubuntu"
date: 2010-12-17
forum: Software
---

### Post by tinolinux on 2010-12-17
Hola a todos los usuarios de Ubuntu! Me presento en estos foros con gran alegria :)
Necesito su ayuda. Soy bastante nuevo en linux y todavía no tengo muchos conocimientos técnicos.
Intenté instalar Ubuntu 10.04.(Antes tenia Fedora 13). Toda la intalación fue normal, excepto al final. Al 95% de la instalación se quedo cargando el dpkg. Después de MEDIA HORA asumí que un error apareció y se quedó trabado. Me vi obligado a resetear, cancelando la instalación. Como esto hizo que se instale erroneamente, después de resetear intenté reinstalar ubuntu. Pero antes de cargarse las opciones de instalación sale un mensaje de error diciendo "el instalador de ubuntu sufrio un error del que no puede recuperarse". Y no me deja instalarlo. Entonces decidí usar Gparted para formatear las particiones correspondientes al linux (también tengo Windows. Cuando mostró mi sistema de particiones, me llamó la atención que el dev/sda 3 esta en lvm2. Yo no conocía este sistema de archivos.Igual no me preocupó y configuré todo para formatear todas las particiones de linux (las sda, el swap..)
para que no quede rastro del ubuntu mal instalado.Al sd3 le puse para que al formatearlo lo convierta en ext4. Pero al momento de comenzar el formateo del sd3 me dice que es imposible formatear esa unidad.
Como ven tengo grandes problemas, encima que el Gparted me da la opción de guardar el log del error para ver que paso, pero no se como se usa eso. A donde se guarda?
Les voy a agradecer mucho su ayuda!

---

### Post by marcelo_bur on 2010-12-17
Hola. Sinceramente no puedo serte de gran ayuda, salvo para comentar que en mi primer intento de instalar Ubuntu 8.04, hace ya bastante tiempo, cometí el mismo error. Da la impresión de que se hubiese detenido la instalación, pero no es así, me sucedió posteriormente y simplemente me fui y dejé la máquina trabajar tranquila, al regresar estaba todo en orden. Pero, volviendo a esa primer vez, y como también era muy novato en Ubuntu ni soy tampoco un gran entendido en estos asuntos, tuve que recurrir a la ayuda de un técnico (el que se ocupa normalmente de mis máquinas, ya sea repararlas o armarme nuevas). Le llevó un montón de tiempo, usó cantidad de programas especiales, antes de poder formatear, y tuvo que formatear el disco completo. Espero que quienes realmente saben en este foro puedan ayudarte y, de paso, aprendo yo también leyendo.
Saludos

---

### Post by biale on 2010-12-18
lvm es muy fedora y tambien es muy poco lo que se al respecto. 

Introduce el concepto de volumenes logicos y volumenes fisicos. Y si recuerdo bien incluso marca el inicio del disco físico (?). La partición de arranque o parte de ella (/boot etc), no podía ser lvm.

El punto es que gparted no maneja lvm, habría que usar los utilitarios propios de lvm para hacer desaparecer todo esas cosas.

Para comenzar, en el manual de instalacion de fedora hay una explicacion sobre lvm. Quizas sea un buen punto para arrancar.

No mucha ayuda, espero que alguien pueda aportar algo mas concreto...

---

### Post by granjero on 2010-12-18
yo tampoco voy a aportar demasiado. pero si mal no recuerdo el instalador de ubuntu server  te propone algo de lvm. quizá con el instalador al momento de llegar a las particiones puedas eliminarlas o formatearlas...

salud!

---

### Post by biale on 2010-12-19
Quizas sirva algo de esto...

[http://forums.whirlpool.net.au/archive/1142552](http://forums.whirlpool.net.au/archive/1142552)

---

### Post by gmunioz on 2010-12-19
No es un error de gparted.
Debes eliminar la partición y volver a crear una no lvm.
Esto es asi por las características de lvm.


[I]LVM es el acrónimo de “Logical Volume Management” que en español significa “Administración de Volúmenes Lógicos” 

Volume Group (VG) “Grupo de Volúmenes”
Es el punto de abstracción más alto en LVM, es como un disco duro gigante que suma el espacio de los discos duros existentes en el sistema. Contiene una colección de volúmenes físicos y lógicos formando en una sola unidad administrativa.

Physical Volume (PV) “Volumen Físico”
Generalmente es un disco duro o algo que se le asemeje, como un arreglo RAID por ejemplo.

Logical Volume (LV) “Volumen Lógico”
Es equivalente a lo que conocemos comúnmente como una partición. Puede contener a un sistema de archivos.

Physical Extent (PE) “Extensión Física”
Cada volúmen físico esta divido en pequeños pedazos de datos llamados physical extents. Cada physical extent es del mismo tamaño que una logical extent.

Logical Extent (LE) “Extensión Lógica”
Cada volúmen físico esta divido en pequeños pedazos de datos llamados logical extents.

Supongamos que tenemos 2 particiones /dev/sda1 y /dev/sda2 de diferentes tamaños, creamos un Grupo de Volúmenes llamado vg1 e introducimos en él las 2 particiones, ahora éstas particiones se convierten en los Volúmenes Físicos pv1 y pv2.

Si el Grupo de Volúmenes vg1 tiene una Extensión Física de 4Mb entonces los Volúmenes Físicos estarán dividos en pedazos 4Mb de datos.

Supongamos que el pv1 tiene 50 Extensiones Físicas y el pv2 tiene 80 Extensiones Físicas, entonces podremos crear Volúmenes Lógicos de cualquier tamaño entre 1 y 130 extensiones (50+80=130). Cuando se crea un Volumen Lógico se genera un mapeo entre las Extensiones Lógicas y las Extensiones Físicas, por ejemplo si la Extensión Lógica 1 está mapeada  a la Extensión Física 20, entonces los datos escritos en la Extensión Lógica 1 serán realmente escritos en la Extensión Física  20.

Cada Volumen Lógico puede contener un determinado sistema de archivos y éstos a su vez albergar a un punto de montaje como /home, /usr, /var y sus archivos y directorio.[/I]

---

