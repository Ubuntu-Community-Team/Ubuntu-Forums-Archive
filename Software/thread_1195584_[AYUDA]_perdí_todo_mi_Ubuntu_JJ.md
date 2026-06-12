---
title: "[AYUDA] perdí todo mi Ubuntu JJ"
date: 2009-06-24
forum: Software
---

### Post by r@fitiiixxx on 2009-06-24
Hola gente!!

 tengo un problema muy grave!!! estaba viendo una pelicula en Ubuntu y mientras descargaba las actualizaciones que me pedía para funcionar correctamente los programas, no me acuerdo cuales eran o como eran, luego me pide que reinicie el equipo, le pongo que lo hago yo después al reinicio porque quería terminar la pelicula, cuando pongo play en el Gstreamer se veía todo re trabado, y me dije
"seguro que es porque algún paquete se actualizó y ya no es el mismo, voy a reiniciar y después la pongo desde donde estaba (la peli)"
voy a reiniciar, bip bip, me inicia el GRUB, y me dice lo siguiente:¨> Booting ' Debian GNU/Linux, kernel 2.6.28-13-generic' 
Filesystem type is ntfs, partition type 0x07
The current working directory(i.e., the relative path) is ubuntu/disks kernel  /vmlinuz-2.6.28-13-generic root=UUID=90A8FBC7A8FBAA3C loop=/ubuntu/disks/root.disk ro splash vga=769 

Error 15: File not found

Press any key to continue..._

y si presiono cualquier tecla, me sale el grub que dice lo de la foto adjunta (se ve medio fea porque la saque con el nokia 5200 y tiene camara VGA medio mala)
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=118744&stc=1&d=1245815821[/IMG]
(la opción que no se ve es el Window$ XP professional SP3 que lo tengo para este tipo de cosas)


no importa cual toque, todas me mandan al primer mensaje que Quotié, que por cierto está escrito sin interfaz gráfica ni nada, así como el grub. 
 Aunque la _terminación del mensaje_ es diferente si pongo "recovery mode" (cualquiera de los dos recovery) o la ultima opción "memtest+86", que dicen así:

la 1º y 3º opcion:> .disk ro splash vga= 769
la 2º y 4º opción:> .disk ro single
la 5º (memtest) opción:> /memtest86+.bin(esta ultima tiene menos cosas escritas en total pero no pude llegar a copíar todo, entiendan que lo copíe a mano con el cel, si de verdad lo necesitan lo hago, pero traté de hacerlo lo mejor posible.)

la verdad no se que paquetes habré instalado, yo puse actualizar, aceptar y listo, si total eran paquetes del gestor de actualizaciones, no veo porqué su software sería problematico no?, tal ves algún source que agregué a los sources.list puede ser? (me acuerdo haber visto algo de Compiz que se actualizaba, varias cosas de compiz, mas allá de eso no me acuerdo por ahora.)

en fin, quería ver la peli pero solo la tengo en Ubuntu y no puedo verla, puede que haya perdido todos los datos también, así que a ver si me pueden dar una mano, este problema no me a sido para nada menor.

mi Hard/soft: AMD 64 AthlonX2 [dual core processor 2.4Ghz] & AM2 socket, chipset Nvidia nForce 410. 2Gb RAM DDR2 (aprox). Nvidia GeForce 8600 GT 512 mb
Ubuntu JJ 9.04 + Gnome desktop + Compiz + Beryl

llaves PPA's agregadas recientemente: _[Global Menú]("http://code.google.com/p/gnome2-globalmenu/downloads/list")_

porfavor ayudenme, estoy desesperado :oops: :sad:

---

### Post by guillermolisi on 2009-06-24
Con "grub error 15" en Google tenes mucha informacion al respecto.

Aqui te acerco un link a la primera de las que obtuve [http://www.gentoo.org/doc/es/grub-error-guide.xml](http://www.gentoo.org/doc/es/grub-error-guide.xml) (es de Gentoo pero el grub es el mismo)

PS : Lo movi a Software por el Grub y los archivos que falten no se pueden patear, solo insultar.

---

### Post by gmunioz on 2009-06-24
Hola r@f....:

Veo tres cosas llamativas.

```
Una: Grub4dos

Dos: Filesystem type is ntfs

Tres: loop=/ubuntu/disks/root.disk
```

Estos parámetros me permiten inferir que no estas

usando Ubuntu instalado nativamente.

Estas usando Ubuntu como programa instalado en 

Windows.

Si es así, no tienes un error de Ubuntu.

Tienes un típico, usual y habitual error del

sistema operativo de Microsoft que degradó los 

archivos de su sistema de archivos.

Sugerencia: Instala Ubuntu, si ya te satisfizo su

funcionamiento como operativo independiente en particiones

separadas, y en sistemas de archivos propios, ext4 por ejemplo.

---

### Post by r@fitiiixxx on 2009-06-24
> **guillermolisi said:**
> Con "grub error 15" en Google tenes mucha informacion al respecto.

Aqui te acerco un link a la primera de las que obtuve [http://www.gentoo.org/doc/es/grub-error-guide.xml](http://www.gentoo.org/doc/es/grub-error-guide.xml) (es de Gentoo pero el grub es el mismo)

PS : Lo movi a Software por el Grub y los archivos que falten no se pueden patear, solo insultar.

hola y perdon por haber confundido los foros, la verdad es que pensé que sería hardware.

con respeto al link, no me queda muy claro que tengo que hacer, no entiendo mucho del lenguaje tecnico o lo que tengo que hacer ahí. creo que tengo que iniciar desde liveCD y despues hacer algo ahí...
ahora me fijo.

estube buscando información por inet del error 15, hasta ahora no encontré nada que yo entendiera, pero sigo buscando...

> **gmunioz said:**
> Hola r@f....:

Veo tres cosas llamativas.

```
Una: Grub4dos

Dos: Filesystem type is ntfs

Tres: loop=/ubuntu/disks/root.disk
```

Estos parámetros me permiten inferir que no estas

usando Ubuntu instalado nativamente.

Estas usando Ubuntu como programa instalado en 

Windows.

Si es así, no tienes un error de Ubuntu.

Tienes un típico, usual y habitual error del

sistema operativo de Microsoft que degradó los 

archivos de su sistema de archivos.

Sugerencia: Instala Ubuntu, si ya te satisfizo su

funcionamiento como operativo independiente en particiones

separadas, y en sistemas de archivos propios, ext4 por ejemplo.

Sisi desde XP lo tengo instalado... significa que perdí mis datos?

si yo quiero instalar Ubuntu por serparado, pero no tengo un disco extra, el disco está particionado con C y D y me ocupa todo el disco, y no hay forma de que haga backup. porque el D es mucho mas grande que el C y ya con lo que tiene

osea perdi todo mi Ubuntu? no hay chance de que lo recupere?

tenía muchas cosas de valor ahí! :(
y si uso mas ubuntu que windows, de echo hacía 2 meses que no usaba windows.
 y e roto mi racha :(

pd: perdón por los errores ortográficos, pero el corrector del foro me anda re mal, parece que pensara que escrivo en ingles. y como siempre me faltan los acentos, bueh así quedó

---

### Post by gmunioz on 2009-06-24
Hola r@f...:

1- Respecto de Windows, ignoro si desde él, podrás

recuperar los datos perdidos, es que hace muchos años

que no lo uso.

2- Si estabas usando Ubuntu desde Windows, significa, 

que tienes espacio disponible para instalarlo en forma

independiente.

Desde Windows, con paciencia, previo eliminar todo aquello 

que no te sirva, este demás, duplicado o tenga respaldo en

otro medio, ejecuta sobre ambas particiones, discos C: y D:

para Windows, las aplicaciones:

chkdsk /f   

(esta corre en la consola de Windows, Inicio - Ejecutar

cmd) seguramente chdksk /f sobre D: correrá, pero sobre C:

te pedirá reiniciar.

defrag

(Esta corre en modo gráfico)

Luego habrá que reducir alguna o ambas particiones, para

dejar espacio libre para instalar Ubuntu, antes de aconsejarte

algun procedimiento es necesario que desde una sesión live-cd

de Ubuntu  ejecutes en consola (Aplicaciones - Accesorios - 

Terminal) el comando:

sudo fdisk -l

copies la salida que da y la pegues en el post para ver como

está particionado tu disco rígido y obrar en consecuencia.

---

### Post by staar on 2009-06-24
si tenés espacio libre, podés redimensionar las particiones que tenés, y crear las necesarias para ubuntu, lo podés hacer desde el livecd con el Editor de particiones (obligatorio desfragmentar el NTFS bien antes)

con respecto a tu problema, no conozco mucho de las instalaciones con wubi, desde windos no podés acceder a los datos de ubuntu?

saludos

---

### Post by r@fitiiixxx on 2009-06-24
@gmunioz:
 ok, lo voy a poner en practica a eso, justo ahora tengo que salir para la facu, pero a la noche cuando vuelva lo hago a ese temita. Es que los datos de windows tambien son importantes (tengo juegos ahí que me a costado mas de un día bajarlos), tendría que ver cuanto me queda, seguro que hoy a la noche me puedo hacer un espacio para ver esto

> **staar said:**
> si tenés espacio libre, podés redimensionar las particiones que tenés, y crear las necesarias para ubuntu, lo podés hacer desde el livecd con el Editor de particiones (obligatorio desfragmentar el NTFS bien antes)

con respecto a tu problema, no conozco mucho de las instalaciones con wubi, desde windos no podés acceder a los datos de ubuntu?

saludos

no no puedo ver lo que tengo en ubuntu :'( ojalá pudiera, aquél editor de particiones supuestamente me podría redimensionar el disco D:\ pero de manera grafica?
porque si es de consola me va a costar bastante jeje.

cuando vuelva me pongo a hacer...

---

### Post by staar on 2009-06-24
si si, es gráfico, con una barrita muy clara que representa tu disco y sus particiones, muy fácil de usar, y sin miedo, porque los cambios no pasan al disco hasta que oprimis el botón grande que dice Aplicar :-P, lo encontrás en Sistema > Administración...

saludos

---

### Post by sebastianabate on 2009-06-24
Una opción para levantar la data que tenés en el Ubuntu Wubi es levantar la máquina con el LiveCD, montar la partición de Windows donde está instalado el Ubuntu y después montar la imágen de disco de Wubi. Un ejemplo del comando para montar la imágen es:

```
sudo mount -o loop /media/punto_de_montaje_particion_windows/ubuntu/disks/root.disk /media/directorio_creado_por_vos
```
[COLOR=#010122][FONT=sans-serif][/FONT][/COLOR]

---

### Post by gmunioz on 2009-06-24
Hola Sebastian:

Felicitaciones por la sugerencia.

Ya esta agendada.

Edito =====================================================

Si he comprendido el método detallado para acceder a los

datos de una instalación de Ubuntu mediante Wubi, sería

siempre y cuando el sistema de archivos de Windows  lo permita:


1- Iniciar el ordenador con un LiveCD.

2- Verificar que se haya montado la partición de Windows donde 

se instaló Ubuntu mediante Wubi

Se supone para el ejemplo que se ha montado en:

/media/punto_de_montaje_particion_windows

Queda montar la imágen de disco de Wubi, que generalmente es:
 
c:/ubuntu/disks/root.disk

Lo que para Ubuntu en su sesión live sería:

/media/punto_de_montaje_particion_windows/ubuntu/disks/root.disk

Previo crear un directorio, por ejemplo /media/ubuntuwubi

Ejecutando en consola

sudo mkdir /media/ubuntuwubi

Un ejemplo del comando para montar la imágen sería entonces:

sudo mount -o loop /media/punto_de_montaje_particion_windows/ubuntu/disks/root.disk /media/ubuntuwubi

Fin edicion =================================================

---

### Post by sebastianabate on 2009-06-24
Gabriel, gracias por la ampliación de la info; cuando mandé el mensaje no tenía tiempo de entrar en detalles. Es tal cual lo explicás vos, impecable el paso a paso.

---

### Post by r@fitiiixxx on 2009-06-24
> **gmunioz said:**
> Hola Sebastian:

Felicitaciones por la sugerencia.

Ya esta agendada.

Edito =====================================================

Si he comprendido el método detallado para acceder a los

datos de una instalación de Ubuntu mediante Wubi, sería

siempre y cuando el sistema de archivos de Windows  lo permita:


1- Iniciar el ordenador con un LiveCD.

2- Verificar que se haya montado la partición de Windows donde 

se instaló Ubuntu mediante Wubi

Se supone para el ejemplo que se ha montado en:

/media/punto_de_montaje_particion_windows

Queda montar la imágen de disco de Wubi, que generalmente es:
 
c:/ubuntu/disks/root.disk

Lo que para Ubuntu en su sesión live sería:

/media/punto_de_montaje_particion_windows/ubuntu/disks/root.disk

Previo crear un directorio, por ejemplo /media/ubuntuwubi

Ejecutando en consola

sudo mkdir /media/ubuntuwubi

Un ejemplo del comando para montar la imágen sería entonces:

sudo mount -o loop /media/punto_de_montaje_particion_windows/ubuntu/disks/root.disk /media/ubuntuwubi

Fin edicion =================================================

y @sebastianabate:

Gracias por la explicación! ahora e montado los archivos, pero eso significa que ya estan recuperados por completo y el sistema me está andando sin errores? o me falta algo por hacer? porque esto es muy diferente de lo que me dijo @staar, que justo ahora voy a probar, eso de redimensionar, ahora estoy desde el live.

otra cosa me habían pedido esto: 
"$ sudo fdisk -l"
y salió esto:
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disco /dev/sda: 320.0 GB, 320072933376 bytes
255 cabezas, 63 sectores/pista, 38913 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0xd869d869

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1        7649    61440561    7  HPFS/NTFS
/dev/sda2            7650       38912   251120047+   f  W95 Ext'd (LBA)
/dev/sda5            7650       38912   251120016    7  HPFS/NTFS
ubuntu@ubuntu:~$ 

```

en fin ahora voy a winxp para hacer eso del defrag y la redimensión luego, a menos que el problema ya esté solucionado en cuyo caso solo preguntaría si puedo hacer back up de los archivos e instalar Kubuntu sin wubi porque lo quería probar, y ya que estamos, osea si lo recupero a los datos diganme si no pasa nada el back up de un SO a otro. tengo jueguitos tmb... jaja

bueno gracias por la ayuda! pero todavía me falta mucho por hacer, creo.

ahora hago back up de la pelicula que estaba viendo ayer que se me cortó y sigo.

):P

---

### Post by staar on 2009-06-24
con montar el sistema no es suficiente, hace el backup de lo que necesitas (no importa donde los pongas, pendrive, dvd, o partición de windos)

después instalá el sistema de la manera tradicional (previamente desinstalá el instalado con wubi, sobre todo por el espacio), para el redimensionamiento de las particiones, te recomiendo que achiques /dev/sda5 (el D: de windos, importantisimo desfragmentar muy bien) que es la más grande, y dejes espacio libre sin particionar suficiente para ubuntu, después en el instalador seleccioná 'usar espacio libre' para que te haga solo las particiones en ese espacio y no te hagas tanto lio...

saludos

---

### Post by r@fitiiixxx on 2009-06-30
> **staar said:**
> con montar el sistema no es suficiente, hace el backup de lo que necesitas (no importa donde los pongas, pendrive, dvd, o partición de windos)

después instalá el sistema de la manera tradicional (previamente desinstalá el instalado con wubi, sobre todo por el espacio), para el redimensionamiento de las particiones, te recomiendo que achiques /dev/sda5 (el D: de windos, importantisimo desfragmentar muy bien) que es la más grande, y dejes espacio libre sin particionar suficiente para ubuntu, después en el instalador seleccioná 'usar espacio libre' para que te haga solo las particiones en ese espacio y no te hagas tanto lio...

saludos

Hola gente!! volví, pasa que tube parciales, y con los parciales no prendi mucho la pc, también porque era windows, ahora me pongo a hacer lo que dijo staar.

enfin ahora volví y estoy desfragmentando el disco, mas tarde hago el backup y para hoy a la madrugada tengo Kubuntu, ahora mi pregunta,

e leido por ahí que me recomendaron la partición ext4. pero yo no entiendo mucho de particiones,e leido algo y sigo leyendo en internet acerca de los beneficios y

de que es el ext4 frente al ext3, si encuentro algo que no se seguro lo voy a postear, realmente me interesa eso de la velocidad de carga.

ahora mismo tengo muchas preguntas porque estuve usando windows estos dias y se empezó a notar la diferencia en velocidad y cuelgues.

otra cosa, como hago el menú que tenía instalado con wubi que me permitía elegir el S.O.al comienzo del booteo? porque quiero tener acceso a los dos S.O.'s

off:bueno muchisimas gracias y no pretendía revivir post, lo que pasa es que suspendí todo por la facu, espero no haber echo algun daño...

off2: ahora le mando un pm a guillermolisi porque quiero levantar muchos threads nuevos de preguntas (sobre todo navegadores)

y no se si se puede postear tanto jeje

Salu2 ):P

---

### Post by staar on 2009-06-30
el menu que te permite elegir el SO al inicio es el GRUB, se instala solo durante la instalación, y te reconoce el Ventanas instalado, y lo agrega a la lista...

para instalar con ext4 en jaunty tenés que usar el particionado manual (el automático es con ext3), y, como se ve que no tenés mucha idea, no te lo recomendaría, pero si te querés mandar, en el espacio libre tendrías que crear, mínimo (durante la instalación) dos particiones:
-una del tamaño de tu ram para usar como área de intercambio
-otra en el resto del espacio con formato ext4 y punto de montaje '/'

si quisieras tener una partición aparte para el /home (que generalmente se recomienda, yo personalmente no lo hago), el '/' no usaría todo el espacio, sino aprox. 6-10 gb, y el resto otra partición con formato a elección (puede ser ext3, ext4 o el que más te guste) y punto de montaje '/home'

saludos

---

### Post by r@fitiiixxx on 2009-07-01
> **staar said:**
> el menu que te permite elegir el SO al inicio es el GRUB, se instala solo durante la instalación, y te reconoce el Ventanas instalado, y lo agrega a la lista...

para instalar con ext4 en jaunty tenés que usar el particionado manual (el automático es con ext3), y, como se ve que no tenés mucha idea, no te lo recomendaría, pero si te querés mandar, en el espacio libre tendrías que crear, mínimo (durante la instalación) dos particiones:
-una del tamaño de tu ram para usar como área de intercambio
-otra en el resto del espacio con formato ext4 y punto de montaje '/'

si quisieras tener una partición aparte para el /home (que generalmente se recomienda, yo personalmente no lo hago), el '/' no usaría todo el espacio, sino aprox. 6-10 gb, y el resto otra partición con formato a elección (puede ser ext3, ext4 o el que más te guste) y punto de montaje '/home'

saludos

uu es muy complicado y sin un navegador a mano para googlear o para forear... no me parece buena idea,

ya que la mayor parte de lo que escriviste se me hace muy complicado, mejor voy a lo seguro y mas adelante hago el cambiaso.

igual muchas gracias por explicar :)

me fui a instalar kubuntu

salu2, ):P

r@fitiiixxx

---

