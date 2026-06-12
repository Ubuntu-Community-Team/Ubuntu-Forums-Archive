---
title: "Agrandar particiones"
date: 2014-03-03
forum: Software
---

### Post by Vero1 on 2014-03-03
Hola,

Uso Ubuntu 12.04 en un Disco de 500 Gb. 
Necesito en forma urgente agrandar las particiones de Raiz y Home.
Por favor indiquenme los pasos a seguir para no perder nada de lo que ya tengo.
Adjunto screencap de Gparted.

Desde ya muchas gracias por una pronta respuesta.

Saludos

---

### Post by gmunioz on 2014-03-07
Lo que parece más práctico es:
Desde una sesión live.
Cargar gparted.
Desmontar, si estuviera montada /dev/sdb4
Eliminar /dev/sdb4
Desmontar si estuviera montada /dev/sdb3
Aumentar con el espacio sin particionar en la cantidad necesaria /dev/sdb3
Crear una nueva /dev/sdb4 para swap.
Aplicar los cambios.
Averiguar las uuid de /dev/sdb3 y /dev/sdb4
> sudo su
blkid /dev/sdb3
blkid dev/sdb4
Montar /dev/sdb2 si no estuviere montada
Buscar y abrir el archivo  /dev/sdb2/etc/fstab
Verificar que la uuid de /home no cambió, si cambió cambiarla.
Cambiar la uuid de swap
Para hacer espacio en /, ejecutar:
> sudo su
apt-get clean
apt-get autoremove
Agrandarla es complicado e impresiona como innecesario.
De última podrías luego de:
Eliminar /dev/sdb4
Desmontar si estuviera montada /dev/sdb3
Aumentar con el espacio sin particionar en la cantidad necesaria /dev/sdb3
Crear una partición extendida del espacio sobrante.
Crear en la partición extendida una lógica para swap, una lógica para /var, una lógica para /tmp
Mover /var y /tmp a sus respectivas particiones y registrarlo en el archivo  /dev/sdb2/etc/fstab
El procedimiento es complejo:
Una vez que tengas creadas las particiones debes montarlas en un directorio de nombre temporario 
para poder copiar a ella los archivos de directorio original.

sudo su
mkdir /mnt/vartemp
mkdir /mnt/tmptemp
mount /dev/sdb? /mnt/vartemp
mount /dev/sdb? /mnt/tmptemp
cd /dev/sdb2/var
cp -ax . /mnt/vartemp
cd /dev/sdb2/tmp
cp -ax . /mnt/tmptemp
Estas últimas lineas son las únicas que sirven para clonar, atención con "." del final.
cd /dev/sdb2
mv /var /var.old
mv /tmp /tmp.old
mkdir /var
mkdir /tmp
blkid /dev/sdb? (/var)
blkid /dev/sdb? (/tmp)
gedit /dev/sdb2/etc/fstab

Añades estas lineas al final.

# /var was on /dev/sdb?
UUID=df0ce520-b0ba-4e6b-899e-a1a615c8c10a /var           ext4    defaults        0       2
# /tmp was on /dev/sdb?
UUID=df0ce520-b0ba-4e6b-899e-a1a615c8c10a /tmp           ext4    defaults        0       2

Y verificas la uuid de swap
# swap was on /dev/sdb4
UUID=c9eb230e-ab85-4bc0-b24f-06caeac4d953 none            swap    sw              0       0

---

### Post by Vero1 on 2014-03-11
Muchas gracias por tu respuesta.
Volveré.

Saludos

---

### Post by Vero1 on 2014-05-03
Hola,
Me veo obligada a pedir socorro. Se estropeó el disco donde está Windows XP. Quiero conservarlo por si me pasa algo con Ubuntu.
El otro disco donde está Ubuntu 12.04 tiene una capacidad total de 500 Gib., de los cuales solamente se ocupan algo menos de 50 Gib, quedando sin asignar el resto.
Como quería reinstalar en forma urgente Windows, reparticioné el disco. Les envío una captura de pantalla para que vean como está actalmente.
Como verán, no tengo partición SWAP porque la tuve que eliminar para tener una partición primaria para Windows.(esa partición está vacía todavía)
En el espacio sin asignar quise hacer una partición extendida para SWAP pero no me lo permite.
Quisiera me indiquen cómo hago para tener esa partición extendida.
[IMG][[IMG]http://i.imgur.com/D8YQ9sH.png[/IMG]](http://imgur.com/D8YQ9sH)[/IMG]

Mucho agradeceré vuestra respuesta lo antes posible.

Saludos

---

### Post by enriquek2 on 2014-05-04
Ya no puedes crear particiones primarias o extendida, llegaste al límite de tener 4 primarias , si quieres crear una extendida vas a tener que eliminar una primaria lo que puedes probar es eliminar la partición /boot para ello sigue estos pasos
1.- sudo gedit /etc/fstab 
le pones  # delante de la linea que hace referencia al montaje de la parición boot
2.- Entra a gparted y le pones etiqueta a la partición es / y /boot , por ejemplo le pones
Raiz y Boot respectivamente
3.- Arranca con el LiveCD de Ubuntu, entra a una carpeta cualquiera y selecciona Raiz y Boot en el menú lateral con eso habrás montado a esas particiones
4.- Entra a Boot, selecciona todos lo elementos incluyendo los ocultos si los hubiere , los arrastras a la carpeta boot de la partición Raiz  con el botón central del ratón ---> copiar aquí
5.- completada la copia reinicia el sistemade de forma normal, si todo sale bien, ya podrás eliminar la paerición sda1 ,  que era la de /boot , y ahora si podrás crear una partición extendida en el espacio no asignado
La verdad es que lo mas recomendable es reinstalar Ubuntu con una adecuada tabla de particiones, si te interesa esta opción, te puedo dar orientaciones para hacerlo lo mas simple y rápido posible

---

### Post by Vero1 on 2014-05-04
Gracias por responder.

Ahora hago la siguiente pregunta.
Teniendo en cuenta que agrandé /home y creé una partición para Windows pensé. Como lo que agrandé está sobre la derecha, presuntamente no tiene nada lo mismo que la partición que le hice a Windows, no puedo volver atrás y eliminar lo que agrandé en /home y la partición que preparé para Windows?
De esa manera quedaría como antes, o sea con un espacio sin asignar de más o menos 300 GB y entonces crear una partición primaria para Win y una extendida para SWAP? (supongo que SWAP no va a figurar porque está eliminado)-

No sé si me expliqué bien. 

Si se puede hacer mejor. 

Te agrego una captura de lo que era GParted, antes de reparticionar.

[IMG][[IMG]http://i.imgur.com/fkQosMt.png[/IMG]](http://imgur.com/fkQosMt)[/IMG]

Gracias

perdón veo que no es el GParted que necesitaba enviar.

Ahora lo corrijo.

[IMG][[IMG]http://i.imgur.com/zJd25pJ.png[/IMG]](http://imgur.com/zJd25pJ)[/IMG]

---

### Post by enriquek2 on 2014-05-04
No cambia nada por que tu problema es que si creas una primaria para windows eliminando previamente la swap, sigues en las mismas, , o sea en  un DD puedes tener como máximo
1.- 4 primaria
2.- 3 primarias y la extendida y dentro de esta todas las lógicas que quieras o puedan caber, en materia de lógicas no hay límites
Otra cosa, en comentario anterior me olvidé de decir que para copiar el contemido de la partición Boot a directorio boot de la partición Raiz, previamente montadas, debes hacerlo como root  sería hacer esto
1.- en terminal pones
gksudo nautilus /media/Boot
con eso te abre el contenido de la partición Boot
abre otro terminal y pones
gksudo nautilus /media/Raiz/boot
se te abre la carpeta boot de la partició Raiz 
Luego procede a la copia usando el botón central del ratón, -ruedita-

---

### Post by enriquek2 on 2014-05-04
Te doy otra alternativa que tal vez te guste mas
1.- Pone tu tabala de particiones como estaba originalmente y elimina la swap, va a quedar el gran espacio no asignado, a ese lo asignas como extendida, dentro de esta creá una lógica para swap de tamaño igual a tu ram otra lógica que será tu nueva home aprovecha de darle el tamaño adecuado y finalmente otra lógica en formato ntfs para datos de windowsm cuando tengas todo esto hecho pone lo que te sale al ejecutar
sudo blkid /dev/sdax
en donde x representa la futura partición home, con estos datos te preparo un Script que se encargará de todo y cuando lo ejecutes y comprobado que salió bien, te explico como sigue la película

---

### Post by Vero1 on 2014-05-04
Enriquek2,

Pregunto: si hago tu segunda instrucción, qué va a pasar con la /home actual /raiz y /boot actuales?
Windows no tiene que ir a una partición primaria? 
La SWAP no tiene que ser el doble que mi RAM? Tengo 2 de RAM.
Mientras preparas el script, Ubuntu funcionará con /home actual?
Los datos que hay en /home cómo se pasarán al nuevo lugar y qué pasará con el espacio que ocupa ahora? o de ésto se va a ocupar tu script?
Por otro lado me comentaron que /raiz tiene poco lugar tambien y que convendría agrandar.

Gracias EnriqueK2

---

### Post by enriquek2 on 2014-05-04
De lo que se trata es que copiarás todo el contenido de tu home a otra partición que sea lógica, y esto no conlleva ningún riesgo y recién si luego del primer reinicio  todo  sale bien, podrás borrar tu actual home y allí instalarás tu windows no sin antes quitarle un poco de espacio para darle a tu partición de Ubuntu, por eso no me quiero adelantar e ir por lo seguro , lo primero como te dije es que crees las particiones lógicas y me pases el dato`de la UUID de la que será la futura home
Respecto a que valor darle a la swap, soy de la opinoón de debe tener el mismo valor de la ram por que cuando hibernas toda la ram se vuelca a la swap , esto es en mi opinión para lo  máximo que reqyuerirás la swap

---

### Post by Vero1 on 2014-05-05
Ok Enriquek2, 
Con respecto a la SWAP nunca hiberné ni creo que lo haga por lo tanto, si no te ofendés, me quedo con los 4 Gb teniendo en cuenta que no me falta espacio.
Bueno, trataré de hacer lo que me indicas y espero no tener problemas y poder comunicarme con vos para que siga la "película" :-)

Volveré.

Gracias.

---

### Post by enriquek2 on 2014-05-05
A ver, para ir adelalantando , supongamos que la partición en donde quieres tener a home es la sda6 ejecuta
  sudo blkid /dev/sda6
 supongamos que te  sale esto
 /dev/sda6: UUID="bcb52cfe-a54b-4d76-bc3d-55be09edead2" TYPE="ext4" 
 Con ese dato, ejecuta 
gksudo gedit /etc/fstab 
vas a la linea en donde indica el punto de montaje /home y reemplaza el valor de la UUID por el  valor
   bcb52cfe-a54b-4d76-bc3d-55be09edead2
guardas y cierras Luego copia el siguiente script en /tmp y le pones de nombre 1111 

 #!/bin/sh 
#ajustar valores al caso
 mkdir /media/sss
 mount /dev/sda6 /media/sss
 cp -ax /home/. /media/sss 
init 6  

Seguidamente abres terminal y pones 
sudo bash /tmp/1111 
No toques nada y deja que reinicie el sistema y cuando lo haga será teniendo a home en la otra partición, la demora dependerá de lo que tengas que copiar solo quedaría borrar la carpeta tempmporal que se creó para montarla y poder copiar el contenido de tu home antigua, o sea ejecuta 
sudo rm -R /media/sss  
Si todo esto salió bien ya puedes hacer el resto, o sea borrar la antigua home y poner allí tu Xp

---

### Post by Vero1 on 2014-05-05
Gracias Enriquek2,

Si todo sale bien, aquí me tendrás informándote :-)


Saludos

---

### Post by gmunioz on 2014-05-09
Me parece más práctico:
Mover /boot a /.
Eliminar las particiones.
Crear la primaria para ¿Windows?, gustos son gustos y la lógica para swap.

> sudo su
mkdir /boottemp
cd /boot
cp -ax . /boottemp
mv /boot /bootold
mv /boottemp /boot
nano /etc/fstab

Comentar la línea:

# /boot was on /dev/sdb1
# UUID=df0ce520-b0ba-4e6b-899e-a1a615c8c10a /boot ext4 defaults 0 2

Reiniciar
Desde gparted eliminar /dev/sdb1 y /dev/sdb4
Crear una partición primaria ntfs para Windows.
Crear una partición extendida del resto libre.
Crear una partición lógica dentro de la extendida para swap
Crear una partición lógica del resto libre de la extendida ntfs para datos.
El espacio de /boot se puede anexar a /, si hiciera falta en un futuro.
Al instalar Windows se pierde el Grub y es necesario reinstalarlo.

---

### Post by Vero1 on 2014-05-10
Hola Gabriel, 

Gracias por contestar.

Cuando hablás de " eliminar particiones" a cuáles te referís?

Mi actual GParted es éste:

[[IMG]http://i.imgur.com/hY6G6Sl.png[/IMG]](http://imgur.com/hY6G6Sl)


Con este esquema, tus instrucciones son las mismas?


Saludos

---

### Post by gmunioz on 2014-05-10
No, no, no:
Ahora, con este esquema sería:
> 
sudo su
mkdir /boottemp
cd /boot
cp -ax . /boottemp
mv /boot /bootold
mv /boottemp /boot
nano /etc/fstab

Comentar la línea:

# /boot was on /dev/sdb1
# UUID=df0ce520-b0ba-4e6b-899e-a1a615c8c10a /boot ext4 defaults 0 2


Reiniciar
Desde gparted eliminar /dev/sdb1
Crear una partición primaria ntfs para Windows.
Crear una partición extendida del resto libre.
Crear una partición lógica dentro de la extendida para swap
Crear una partición lógica del resto libre de la extendida ntfs para datos.
El espacio de /boot se puede anexar a /, si hiciera falta en un futuro.
Al instalar Windows se pierde el Grub y es necesario reinstalarlo.

---

### Post by enriquek2 on 2014-05-10
Veo que no has hecho lo que te puse , en realidad es una de las etapas para dejarlo bien ordenado, la segunda etapa es hacer lo que te puso Gabriel referente a mover boot a la partición raiz luego borras la antigua home y tomas parte de ese espacio para Ubuntu, el resto de ese espacio lo formateas con EXT4 y mueves allí el contenido de la partición de Ubuntu , seguidamente entra  a Gparted en LiveCD  eliminas sda1 , formateas en NTFS e instalas Xp .  cumplido todos estos pasos tu tabla quedaría
sda1 ---> Xp
sda2 ---> Ubuntu
sda3 ---> Extendida
sda5 --->> swap
sda6 ---> home
sda7 ---> ntfs datos para Xp

Respecto al Grub, se arregla fácil teniendo el Super Grub2 Disk Live CD

---

### Post by Vero1 on 2014-05-11
Hola EnriqueK,

No te ofendas. Lo que pasa es que tu propuesta me parece muy dificil de hacer para mí.
Tengo un amigo en España a quien tambien le pedí opinión y estoy esperando respuesta.
En cuanto la tenga me comunico con ustedes, tambien con Gabriel, a ver qué les va a parecer el comentario de mi amigo.

Gracias y hasta entonces.

---

### Post by Vero1 on 2014-05-11
Hola Gabriel,
por favor leé lo que le escribí a EnriqueK.

Gracias

---

### Post by gmunioz on 2014-05-11
Hola Vero:
Este es un foro de usuarios con más ó menos experiencia, que sugieren según su leal saber y entender, posibles soluciones a los problemas planteados. De ninguna manera se trata de imponer procedimientos u ordenar determinadas acciones. Es el usuario que consulta el único responsable del accionar a nivel sistema, que puede ser tanto alguno de los sugeridos como cualquier otro que le plazca o parezca.

---

### Post by Vero1 on 2014-05-11
Hola Gabriel,
Conozco el Foro desde el año 2007, como podrás observar en mi perfil y más de una vez me han ayudado, cosa que agradezco al igual que la ayuda que ustedes dos me están brindando.
Si pedí opinión a mi amigo de España era para tener una tercera y luego compartirla con ustedes, ya que él mismo siempre me dice que consulte en el Foro de Ubuntu para saber su opinión. Todo con la esperanza de que esta tarea resulte algo mas fácil.
La verdad es que si pudiera me compraría otro disco e instalaría Windows sin tanto problema, pero vos debés saber que los discos, hoy en día, no cuestan cien pesos.
Espero que vos tampoco te sientas ofendido y cuando tenga la respuesta de mi amigo, me des tu opinión.

Saludos
p.d.
y no creo que seas mas malo que el Diablo LOL

---

### Post by gmunioz on 2014-05-11
Hola Vero:
Despues de haber dado 63 vueltas alrededor del sol y comenzar la 64, nada puede ofenderme en la vida, es más si visitas Ubuntu-es donde soy Gabriel_M, verás que en mis post que jamás me sentí ofendido por lo que se publica en los posts. 
Y sí, los discos cuestan unas siete veces más que cien pesos.

---

