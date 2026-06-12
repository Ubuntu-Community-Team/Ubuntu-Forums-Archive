---
title: "Ubuntu Sin Sonido despues de instalar Virtual Box"
date: 2009-05-17
forum: Software
---

### Post by gulete84 on 2009-05-17
Hola, escribo para comentarles un problema que tengo!
El problema es que me quede sin sonido en mi Ubuntu Hardy despues de haber instalado el paquete
virtualbox-ose-modules-generic (para VirtualBox).
googleando un poco vi algo de un inconveniente entre el kernel y el Alsa.
Pero no vi ninguna solucion
Cambie a Pulse Audio y tampoco tengo sonido.
escribiendo en la terminal "alsamixer" me muestra lo siguiente:
alsamixer: function snd_ctl_open failed for default: No such file or directory
Espero que alguien me pueda dar una mano.
Saludos.

---

### Post by guillermolisi on 2009-05-17
> **gulete84 said:**
> Hola, escribo para comentarles un problema que tengo!
El problema es que me quede sin sonido en mi Ubuntu Hardy despues de haber instalado el paquete
virtualbox-ose-modules-generic (para VirtualBox).
googleando un poco vi algo de un inconveniente entre el kernel y el Alsa.
Pero no vi ninguna solucion
Cambie a Pulse Audio y tampoco tengo sonido.
escribiendo en la terminal "alsamixer" me muestra lo siguiente:
alsamixer: function snd_ctl_open failed for default: No such file or directory
Espero que alguien me pueda dar una mano.
Saludos.
FIjate si cuando inicias Ubuntu tenes un kernel anterior, presionando Esc cuando Grub te muestra esa opcion para ver el menu de arranque.
Algo me dice que estas usando un kernel nuevo en lugar del que usabas con sonido.

Pasa version de kernel en uso, si es el unico o tenes otros disponibles, que version de VBox estas usando.

PS: Pasado a Software porque este tema es software puro !

---

### Post by gulete84 on 2009-05-17
Efectivamente guillermo! el problema era que estaba entrando a otra version de kernel.
Muchisimas Gracias!

---

### Post by tekenika on 2009-06-13
Hola
No sé si este asunto está todavía abierto.
Si lo está. Consulto pues me pasa eactamente lo mismo
Al inicio me aparecen tres kernels con sus correspondientes
eacovery mode. Estos son:
2.6.24-16-386
2.6.24-16-rtai
2.6.24-16-generic
Estoy arrancando con el primero que es el por defecto.
Debería cambiar?
Desde ya muchas gracias

---

### Post by guillermolisi on 2009-06-13
> **tekenika said:**
> Hola
No sé si este asunto está todavía abierto.
Si lo está. Consulto pues me pasa eactamente lo mismo
Al inicio me aparecen tres kernels con sus correspondientes
eacovery mode. Estos son:
2.6.24-16-386
2.6.24-16-rtai
2.6.24-16-generic
Estoy arrancando con el primero que es el por defecto.
Debería cambiar?
Desde ya muchas gracias
Y con cual de los otros dos iniciabas anteriormente ?

Proba con el ultimo de los tres que mencionas y comenta como te fue.

---

### Post by tekenika on 2009-06-14
Guillermo
muchas gracias por tu atención
Arranque en el modo generic y el problema sigue igual
El mensaje que aparece en el control de volúmen es el que sigue

El control de volumen no encontró ningún elemento y/o dispositivo que controlar. Esto significa que no tiene los complementos correctos de GStreamer instalados o que no tiene una tarjeta de sonido configurada.

Puede quitar el control de volumen del panel pulsando con el botón derecho sobre el icono del altavoz en el panel y seleccionando «Quitar del panel» del menú.

En Ubuntu y en esta máquina, nunca tuve problemas, ni con el sonido
ni con el VirtualBox.
El invonveniente apareció luego de instalar con synaptic lo que V Box me pedía: virtualbox-ose-modules generic
Desisntalé el Virtualbox y el anterior también con symaptic 
Ignoro que puede estar sucediendo.
alsaconf, me devuelve orden no encontrada
alsamixer: function snd_ctl_open failed for default: No such file or directory
----
Alguna instrucción o sugerencia?
saludos

---

### Post by tekenika on 2009-06-14
Algo que encontré buscando pistas, es que no carga los modulos snd
:~$ lsmod|grep '^snd'
:~$ 
nada.
Qué puede hacerse?

---

### Post by Hei Ku on 2009-06-14
Si sabes que modulo le corresponde, podes probar de cargarlo manualmente con:

sudo modprobe <nombre_del_modulo>

---

### Post by tekenika on 2009-06-14
Cómo puedo saber el nombre del módulo?

---

### Post by Hei Ku on 2009-06-14
Depende de que placa tengas. Pero era solo una sugerencia, ya que te habias fijado si el modulo estaba cargado o no.

---

### Post by tekenika on 2009-06-14
Yo soy sólo un usuario.
Cómo nunca tuve problemas con el audio
no presté atención a ese asunto.
Googleando, encontré el comando para verificar
los módulos snd, y veo que no hay ninguno cargado.
Me pregunto si resolveré el problema actualizando el kernel
o será peor el remedio que la enfermedad.
Comento sólo como curiosidad, cuando instalé este Ubuntu
todo estaba bien salvo un pequeñisimo detalle, al apagar
quedaba en la pantalla de Ubuntu, pero no apagaba la máquina,
Buscando en la red la opinión más generalizada decía que era un bug
de la versión y lo más aconsejable era esperar a que lo resolvieran,
bien al mismo tiempo que me quedé sin audio se resolvió aquel asunto
ahora, apaga.....
saludos

---

### Post by tekenika on 2009-06-14
Amigos
reinicié la máquina con el kernel
Ubuntu 8.04.2   2.6.24-16-rtai
y voilá, tengo audio.
Para dar el asunto por solucionado, sería bueno
que alguién pudiera explicar que pasó, para que sea de utilidad
a otros con el mismo inconveniente.
Incluso me gustaría saber que significa rtai.
Pregunto: será prudente reinstalar VirtualBox?
saludos

---

### Post by guillermolisi on 2009-06-15
> **tekenika said:**
> Algo que encontré buscando pistas, es que no carga los modulos snd
:~$ lsmod|grep '^snd'
:~$ 
nada.
Qué puede hacerse?
Tenes que dejar un espacio entre "lsmod" y el simbolo "|" .
Sacale el simbolo "^" a "snd".

---

### Post by guillermolisi on 2009-06-15
> **tekenika said:**
> Amigos
reinicié la máquina con el kernel
Ubuntu 8.04.2   2.6.24-16-rtai
y voilá, tengo audio.
Para dar el asunto por solucionado, sería bueno
que alguién pudiera explicar que pasó, para que sea de utilidad
a otros con el mismo inconveniente.
Incluso me gustaría saber que significa rtai.
Pregunto: será prudente reinstalar VirtualBox?
saludos
En los otros kernels te estan faltando los modulos de audio, por eso no tenes sonido salvo si inicias con el que acabas de comentar.

El nombre de los modulos varia con la placa de sonido, con lo cual si inicias con el kernel rtai y nos mostras la salida de lsmod podremos acercarnos a una solucion.

No es un problema de VBox y de ningun otro componente, asi que no toques nada que no tenga que ver con el sonido.

El kernel rtai es un kernel de baja latencia, que funciona en tiempo real y es usado para trabajar con audio en forma profesional (edicion, control de maquinas de sonido MIDI, sintetizacion, etc.).

EL generic posee una letencia adecuada para la mayoria de los usos de maquinas de escritorio/notebooks y el kernel server es para servidores porque privilegia servicios antes que la interaccion con el usuario via monitor/teclado.

---

### Post by tekenika on 2009-06-15
Gracias Guillermo, por tu atención.
Es correcta tu observación, pegué mal el comando lsmod.
Ahora, entre las muchas cosas que no entiendo:
El kernel de arranque por defecto, por qué se cambió en el grub?
O tal vez la pregunta sea, ¿Por qué los otros kernels perdieron los módulos de sonido? Nunca tuve poblemas con el audio.
¿Por qué ocurrió, justo después de instalar lo que VirtualBox me pedía?
Básicamente instalo siempre VB para poder ver con XP archivos CAD DWF.
Cómo dije, ahora lo desinstalé.
Trabajo bastante con sonido, de modo y ahora que me explicas, no me molestaría poner est kernel para que arranque por defecto.
De todos modos no estaría mal dejar a los otros completamente funcionales.
¿esos kernels que van apareciendo en el arranque es consecuencia de las actualizaciones?
Pego el lsmod
Module                  Size  Used by
nls_iso8859_1           4096  1 
nls_cp437               5760  1 
vfat                   11776  1 
fat                    47644  1 vfat
binfmt_misc            10376  1 
i915                   28416  2 
drm                    73620  3 i915
rfcomm                 34580  2 
l2cap                  21124  13 rfcomm
bluetooth              50920  4 rfcomm,l2cap
ppdev                   8580  0 
aes_i586               32500  0 
dm_mod                 52032  0 
lp                     10636  0 
parport                33224  2 ppdev,lp
ipv6                  221780  8 
xt_limit                2560  8 
xt_tcpudp               3072  18 
ipt_LOG                 5632  8 
ipt_MASQUERADE          3456  0 
ipt_TOS                 2176  0 
ipt_REJECT              4480  1 
nf_conntrack_irc        6552  0 
nf_conntrack_ftp        7968  0 
snd_hda_intel         310012  5 
snd_pcm_oss            37920  0 
snd_mixer_oss          15744  1 snd_pcm_oss
snd_pcm                65416  3 snd_hda_intel,snd_pcm_oss
xt_state                2432  6 
snd_page_alloc          9992  2 snd_hda_intel,snd_pcm
snd_hwdep               8836  1 snd_hda_intel
snd_seq_dummy           3844  0 
snd_seq_oss            30740  0 
gspca                 625764  0 
videodev               25856  1 gspca
v4l2_common            16384  1 videodev
snd_seq_midi            8096  0 
v4l1_compat            12164  1 videodev
snd_rawmidi            22560  1 snd_seq_midi
snd_seq_midi_event      6912  2 snd_seq_oss,snd_seq_midi
snd_seq                44956  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              21252  2 snd_pcm,snd_seq
snd_seq_device          8076  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
iTCO_wdt               11296  0 
iTCO_vendor_support     3716  1 iTCO_wdt
serio_raw               6660  0 
snd                    48564  20 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
intel_agp              22804  1 
agpgart                31024  3 drm,intel_agp
psmouse                35728  0 
pcspkr                  3072  0 
evdev                  10752  1 
soundcore               7108  1 snd
iptable_nat             6916  0 
nf_nat                 16540  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      15368  8 iptable_nat
nf_conntrack           53120  7 ipt_MASQUERADE,nf_conntrack_irc,nf_conntrack_ftp,xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
iptable_mangle          2688  0 
iptable_filter          2816  1 
ip_tables              12232  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               13700  9 xt_limit,xt_tcpudp,ipt_LOG,ipt_MASQUERADE,ipt_TOS,ipt_REJECT,xt_state,iptable_nat,ip_tables
ext3                  118920  1 
jbd                    38036  1 ext3
mbcache                 7808  1 ext3
usb_storage            31744  1 
sg                     33312  0 
sr_mod                 15396  0 
cdrom                  32796  1 sr_mod
sd_mod                 26640  4 
libusual               16672  1 usb_storage
ata_piix               15748  2 
ata_generic             7044  0 
libata                134452  2 ata_piix,ata_generic
scsi_mod              139988  5 usb_storage,sg,sr_mod,sd_mod,libata
8139too                23040  0 
mii                     5248  1 8139too
ehci_hcd               28300  0 
uhci_hcd               21392  0 
usbcore               119348  6 gspca,usb_storage,libusual,ehci_hcd,uhci_hcd
fuse                   43284  3 
--------------
saludos

---

### Post by guillermolisi on 2009-06-17
El Grub inicia por defecto el kernel que se encuentre en la primera posicion (generalemnte identificada como 0) de su menu.

Si instalas un kernel nuevo se agrega al grub modificando el orden de inicio.

Generalmente, cuando se actualiza el kernel por uno mas nuevo hay algunas tareas a realizar. Por ejemplo reconfigurar el driver que sustenta el funcionamiento de VBox para que se agregue al nuevo kernel.

Tambien puede ser alcanzados por esto algunos otros modulos (que son drivers que no estan dentro del kernel) como el de sonido, algunas placas de video y algunos paquetes que se han instalado "a mano" compilando desde sus versiones fuente (source).

Esa salida del lsmod muestra que el modulo de sonido esta cargado. A que kernel corresponde ?

---

### Post by tekenika on 2009-06-17
Bien, sin comprender profundamente lo que dices,
me aclara varias cosas.
El VirtualBox que tenía, creo que venía por defecto
con la distribución.
Luego, es posible que instalara un nuevo kernel sin advertirlo?
Vía actualización, por ejemplo.
Entonces, cuando quise usar el VB como otras veces me pidió lo que dices.
 y ahí se comió los módulos.?
En el arranque aparecen y en este orden:
2.6.24-16-386
2.6.24-16-rtai
2.6.24-16-generic
Ahora estoy arrancando con el ....rtai (el lsmod corresponde a este k)
El VB me había pedido virtualbox-ose-modules generic

saludos

---

### Post by guillermolisi on 2009-06-17
> **tekenika said:**
> Bien, sin comprender profundamente lo que dices,
me aclara varias cosas.
El VirtualBox que tenía, creo que venía por defecto
con la distribución.
Luego, es posible que instalara un nuevo kernel sin advertirlo?
Vía actualización, por ejemplo.
Entonces, cuando quise usar el VB como otras veces me pidió lo que dices.
 y ahí se comió los módulos.?
En el arranque aparecen y en este orden:
2.6.24-16-386
2.6.24-16-rtai
2.6.24-16-generic
Ahora estoy arrancando con el ....rtai (el lsmod corresponde a este k)
El VB me había pedido virtualbox-ose-modules generic

saludos
Dependiendo de como esten configuradas las actualizaciones y suponiendo que en tu caso esta como viene de fabrica, cada actualizacion que aceptas llevar a cabo siempre viene acompañada de los paquetes de se actualizaran, en detalle, uno por uno, y podes seleccionar cuales queres y cuales no de todos los que se listan/ofrecen para el proceso.

En cuanto a por que tenes tres kernels distintos, la unica razon que conozco para que ocurra tal cosa es que en algun momento se seleccionaron para agregar al sistema y no fue precisamente en una actualizacion.

Si iniciaste la maquina con un kernel y trabajas/actualizas/instalas paquetes como en el caso de Vbox, la instalacion queda asociada a ese kernel solamente salvo que te tomes el trabajo de agregar los paquetes que corresponden a los demas nucleos.

---

### Post by tekenika on 2009-06-18
Bueno, yo no recuedo haber "decidido" actualizar y o instalar
kernels, pero ahí estan.
Lo que haré es editar el grub, para poner el rtai por defecto
y listo. Lo raro es que este tiene la característica de no apagar la pc
cuando se da shutdown particularidad que había observado en la instalación
original y a la que no le dí importancia, pues hablaban de un bug.
Ahora no recuerdo si los otros dos kernels apagan, pero uno de ellos
seguro sí.
Tambien podría cargarle los módulos al kernel que si apaga.
En cualquier caso, ahora, pregunto, no debería tener problemas para
instalar VB?
saludos

---

