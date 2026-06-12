---
title: "[MOVER UBUNTU] - moverlo de la partcion de win y que sea independiente"
date: 2009-05-26
forum: Software
---

### Post by r@fitiiixxx on 2009-05-26
Holas estoy queriendo saber si se puede hacer lo siguiente..
seria mover el ubuntu de disco... porque la cosa es q yo lo instalé arriba de XP... y como q no quiero depender mas de XP para usar ubuntu... de echo XP no lo uso ya.. ase 2 meses.. lo tengo por los jueguitos... (tengo el Far Cry 2) pero cada tanto formateo la pc vio ud? para que ande menos choteado el win... pero si la formatearia ahora... mi ubuntu muere con mi xp... aunque esté adentro del disco D:\ no? osea yo cuando lo instalé puse el CD en la lectora y me preguntó si instalaba arriba de win XP cosa del doble arranque y que se yo... osea no le creé 1 particion extra... pero estoy pensando que eso ya no me conviene... la onda seria moverlo no? o si no como?

lo mas importante para mi es conservar las configuraciones, los programas como estan, los accesos directos y todas las webadas q 1 puede meterle... osea muuucha cosa...

a ver si me pueden dar 1 mano :D

==============================================================

otro problema que tengo, es que metí mano en el tema del GRUB Splash y el Usplash... creo q borré el usplash... porque no lo encuentro.. leí 1 post por ahi que decia... que instale el administrador de arranque.. el Boot Manager creo que se llamaba... pero cuando fui a poner 1 nuevo usplash no me aparecia.. y por error saqué el que ya tenia y no pude poner 1 GRUB splash nuevo... :S

la idea seria recuperar y si puedo cambiar el Usplash y tmb instalar 1 GRUB Splash mas copado que 1 pantalla negra fea... osea ya tengo los temas que quiero... el problema es que no me funciona bien el coso ese :(

---

### Post by staar on 2009-05-26
chee, urgente una clase de ortografía y gramática para vos :lolflag: (va con onda)

por lo que entendí, vos instalaste con wubi, osea ubuntu como un 'programa' dentro de windos y ahora querés deshacerte de XP...

entonces no vas a poder 'mover' ubuntu, vas a tener que instalarlo de nuevo, pero tranquilo que hay solución, hace un backup de tu carpeta /home (tu carpeta personal, donde estan todas tus configuraciones) incluyendo todos los archivos ocultos...

después instalá ubuntu, con la opción de usar todo el disco, en el paso de las particiones, y crea tu usuario con el mismo nombre  que el que tenés en la actual instalación...

cuando tengas instalado el ubuntu, copiá el backup de nuevo en el /home y listo :-D

al reinstalar, el tema del grub y el usplash se va a quedar como nuevo, no te preocupes...

saludos

---

### Post by r@fitiiixxx on 2009-05-26
> **staar said:**
> chee, urgente una clase de ortografía y gramática para vos :lolflag: (va con onda)

por lo que entendí, vos instalaste con wubi, osea ubuntu como un 'programa' dentro de windos y ahora querés deshacerte de XP...

entonces no vas a poder 'mover' ubuntu, vas a tener que instalarlo de nuevo, pero tranquilo que hay solución, hace un backup de tu carpeta /home (tu carpeta personal, donde estan todas tus configuraciones) incluyendo todos los archivos ocultos...

después instalá ubuntu, con la opción de usar todo el disco, en el paso de las particiones, y crea tu usuario con el mismo nombre  que el que tenés en la actual instalación...

cuando tengas instalado el ubuntu, copiá el backup de nuevo en el /home y listo :-D

al reinstalar, el tema del grub y el usplash se va a quedar como nuevo, no te preocupes...

saludos

Eeaaaaa gracieeelaaaa :D mañana mismo lo hago... que bueno pensé q iba a ser mas difícil pero aparentemente nop jeje :P 
si yo instalé con wubi... wubi se llama? jajajaja xD tengo 1 carpeta en win xp que dice ubuntu y tiene 1 coso adentro que dice wubi... y lo puedo desinstalar desde windowsh

y lo de la ortografía es 1 tema, sabes lo q pasa? que el acento está re mal ubicado... eso y muchos años de msn van cavando neuronas hasta q no podes escrivir la palabra QUE y pones q y después t salteas letras y eventualmente con el pasar de los años te vas convirtiendo en 1 zombie de Umbrella :| 
jajajajaja me hace acordar al juego de play en una parte que lees el diario de un chabon que se va convirtiendo jeje.. así voy yo :P

cuando pueda terminar con la reinstalacion te cuento como quedo ;) el tema es que yo tmb tengo... muchos archivos importantes, va creo, en carpetas tipo /usr/ y la verdad no se cual salvar... :S
porque solo home me quedo corto no? es decir mis iconos! mis preciosos iconos que los seleccione uno por uno!! jajaja

si mañana entre la tarea y la facu (si voy a la facu y no se escrivir pero no soy gay y que? xD) veo si empieso con el backup...

salu2 ):P

---

### Post by staar on 2009-05-27
los iconos se instalan, generalmente, en tu home, dentro de una carpeta oculta llamada .icons (en linux los archivos ocultos tienen un punto delante), si haces Ctrl + H en el navegador de archivos, vas a poder ver los archivos ocultos, en tu home están los que corresponden a tu configuración, importantes las carpetas .config, .gnome2, .gconf, .icons, .themes, etc

dentro de /usr no creo que tengas nada que pertenezca a tu usuario...

te aviso, por si no te diste cuenta, que vas a tener que volver a instalar todos los programas que uses, aunque las configuraciones se van a mantener...

saludos

---

### Post by Tosh78 on 2009-05-27
Tiene razon el pibe, los iconos los podes instalar tambien /usr si queres que se mantengan para todos los usuarios en lugar del tuyo, asi si te loggeas con root o con otro, vas a tener por default los iconos que estan en esa carpeta. 
Consejo: copiate los iconos que instalate ahi y backupealos porque sino los vas a perder.

---

### Post by Mauro22 on 2009-05-27
Hola!


En este post [0] el Sr. Lega da los pasos necesarios para armar una lista de los paquetes instalados y asi volverlos a instalar despues sin mucho esfuerzo.



[0] [http://ubuntuforums.org/showthread.php?t=887073&highlight=generar+lista+paquetes](http://ubuntuforums.org/showthread.php?t=887073&highlight=generar+lista+paquetes)

---

### Post by r@fitiiixxx on 2009-05-27
@Tosh78: claarooo yo tenia los iconos ahi en /usr/blablabla porque es el unico lugar donde vi que estaban los iconos human y oxygen... = ahora con el pack Mac4Lin le modifiqué adentro de esos mismos... asi que ya me quedaron en la carpeta home :D
exepto por el icono del aMSN que lo cambie... porque no me gustaba el que venía... y ese si solo esta en /usr/share/icons/amsn/64x64 (yo le meti uno de 256x256 asi en la barra Gnome Do docky se me ve super bien :D)

@Staar: no si pero yo los iconos me loos baje de iconspedia y los cambié de a uno los que no me gustaban del pack... y me qdaron afuera de la carpeta home... no se porque hice así pero ahora ya los tengo en .icons. el tema es que no está para cambiarle a cada aplicacion por separado los iconos... como menciono arriba. solo algunas cosas.. pero el amsn no está

fijate yo le puse este icono [center][[IMG]http://www.iconspedia.com/uploads/372839043.png[/IMG]]("http://www.iconspedia.com/icon/msn-explorer-2235.html")[/center]

@Mauro22: gracias! ese post me re sirve jeje... justo lo que nesesitaba...
despues pruebo eso de la clonacion de la lista de paquetes... pasa que estos dias tengo muchas cosas que hacer para la facu... cuando lo aga les comento :)

1 salu2 a todos y gracias por ayudar ;)

):P

---

