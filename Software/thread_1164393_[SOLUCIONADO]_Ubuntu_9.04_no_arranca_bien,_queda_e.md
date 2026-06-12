---
title: "[SOLUCIONADO] Ubuntu 9.04 no arranca bien, queda en texto"
date: 2009-05-19
forum: Software
---

### Post by PedroLuis on 2009-05-19
Hola, tengo un pc Compaq Presario 450 Mhz de cpu, 382 Mg ram, 40 G de disco duro. Tarjeta ATI Technologies Inc 3D Rage LT Pro AGP-133 (rev dc) 
 
Lo uso para probar distintas distros, he cargado indistintas veces Ubuntu desde el 4ó 5 en adelante, pasando por los últimos 8.04 y el 8.10, además he provado en este pc Debian 4 y 5. Todos han funcionado a la larga bien, pero con Ubuntu 9.04 no he tenido el mismo resultado. 
 
Al principio queme el 9.04 y no me dio resultado, así que espere el que pedí de Canonical, ya me llego pero me pasa el mismo problema, la instalación funciona bastante bien pero cuando reinicio es cuando se queda pegado en un ultimo texto, ** Kinit :No resume imge, doing normal boot**..... y no pasa a la parte gráfica. 
 
Algun consejo?  :p

---

### Post by Carlos C on 2009-05-19
Hola. Entiendo que esto te pasa al instalar, pero, ¿puedes entrar al entorno gráfico usando el LiveCD?

---

### Post by moreback on 2009-05-19
Si no le entra con el LiveCD que intente instalar con el "Alternate CD" que tiene la instalación en modo texto. Para variar sería la tarjeta de video ATI la causante.

Saludos.

---

### Post by PedroLuis on 2009-05-19
> **Carlos C said:**
> Hola. Entiendo que esto te pasa al instalar, pero, ¿puedes entrar al entorno gráfico usando el LiveCD?

El 9.04 ya lo instale, cuando me hizo reboot y saque el cd para que partiera es que se queda pegado y no entra a modo grafico.

Con el LiveCD del 9.04 no puedo entrar, pero si con el 8.10, o con cualquier otra version.

Como hacen dias que he estado buscando por la Internet una solucion he visto que podria activar xorg.conf , lo podria hacer del LiveCd pero realmente no se como hacerlo, quisiera por lo menos entrar en modo consola pero tampoco puedo.

Lo ideal seria saber como hacer cambios en el sistema con el LiveCD.

Saludos.

---

### Post by guywithcable on 2009-05-19
Puedes montar la particion con un live CD?

Es que no puedas iniciar un live CD en el modo graphico, o solalmente la sistema duespes de instalar?

(Perdoname si mi espanol no es correcto. No es mi primer idioma, y no se como hacer accentos con mi teclado EEUU.)

---

### Post by PedroLuis on 2009-05-19
> **moreback said:**
> Si no le entra con el LiveCD que intente instalar con el "Alternate CD" que tiene la instalación en modo texto. Para variar sería la tarjeta de video ATI la causante.

Saludos.
 
Si, yo tambien creo que es la tarjeta ATI, pero como lo podria solucionar?

Bueno, mañana seguire buscando, que ahora aqui ya son las 12,30 de la noche y me levanto a la 05:00 para ir a la pega.

gracias a todos por respoder.

---

### Post by PedroLuis on 2009-05-19
> **guywithcable said:**
> Puedes montar la particion con un live CD?

Es que no puedas iniciar un live CD en el modo graphico, o solalmente la sistema duespes de instalar?

(Perdoname si mi espanol no es correcto. No es mi primer idioma, y no se como hacer accentos con mi teclado EEUU.)

Solo con el cd del 9.04 que ya ahoran no puedo entrar en modo grafico, pero antes de instalarlo habia entrado y probado esta version del LiveCd en modo grafico y no hubo ningun problema, tanto asi que la instalacion fue completa y sin probelmas.

Puedo usar los LiveCd de  todas las otras versiones.

---

### Post by guywithcable on 2009-05-19
> **PedroLuis said:**
> Si, yo tambien creo que es la tarjeta ATI, pero como lo podria solucionar?

Bueno, mañana seguire buscando, que ahora aqui ya son las 12,30 de la noche y me levanto a la 05:00 para ir a la pega.

gracias a todos por respoder.

No creo que sea un problema con la tarjeta. Creo que es el driver de las tarjetas ATI en 9.04. El driver propietario todavia no funciona con la version X en Ubuntu 9.04.

---

### Post by guywithcable on 2009-05-19
> **PedroLuis said:**
> Solo con el cd del 9.04 que ya ahoran no puedo entrar en modo grafico, pero antes de instalarlo habia entrado y probado esta version del LiveCd en modo grafico y no hubo ningun problema, tanto asi que la instalacion fue completa y sin probelmas.

Puedo usar los LiveCd de  todas las otras versiones.

Oh. Que extrano. Hmm, no se. :(

---

### Post by radixs on 2009-05-19
Pregunta.... cuando prendes el pc y carga la partida del sistema, te muestra la barra cargando?

---

### Post by Carlos C on 2009-05-19
Entiendo que no puedes entrar al entorno gráfico de Ubuntu "instalado" en tu equipo, pero puedes entrar con el LiveCD del mismo modo en que lo hiciste antes.

Si consigues entrar al entorno gráfico desde el LiveCD puedes montar las particiones de tu disco duro. Para eso tendrás que crear una carpeta en donde montar cada partición y luego proceder a montarlas y modificar tus archivos.
Saludos.

---

### Post by PedroLuis on 2009-05-20
> **radixs said:**
> Pregunta.... cuando prendes el pc y carga la partida del sistema, te muestra la barra cargando?

Eso solo lo hace cuando quiero entrar con el LiveCD en la obsion de "probar ubuntu sin alterar su equipo" muestra la barra de cargando hasta que se queda congelada, al final se salta a texto y sale
*Preparin restricted drivers......                         [OK]
*Starting kernel event manager.....                   [OK]
*Loading hardware drivers......                         
udevd-event [1988] : '/sbin/modprobe -b pci: v000000125 (y una chorrera de numeros)
abnormal exit

*Loading kernel modules......                               [OK]
*Loading manual drivers.....                                 [OK]
*Setting kernel variables (/etc/sysctl.conf).......     [OK]  , asi siguen dos temas de variables hasta que queda parado en una raya de DOS , como esperando, pero no puedo ya hacer nada mas , porque no se puede escribir, la tangente no responde.
   
De lo contrario al partir el pc no alcanza a llegar al icono de ubuntu cargando la barra, sale en texto la cargada, hasta pararse en el  ese Kin.... es decir la frase que puse en el primer comunicado.

Espero que se entienda lo que quiero explicar, pero es raro, debe de ser el drive para la tarjeta ATI, que me esta haciendo una mala jugada.

---

### Post by guywithcable on 2009-05-20
> **PedroLuis said:**
> *Preparin restricted drivers......                         [OK]
*Starting kernel event manager.....                   [OK]
*Loading hardware drivers......                         
udevd-event [1988] : '/sbin/modprobe -b pci: v000000125 (y una chorrera de numeros)
abnormal exit

Me aparece que es un problema con un driver restricto. Lo dijo que hay una salida abnormal mientras estaba cargando un driver de una tarjeta PCI. Es posible que sea la tarjeta ATI.

---

### Post by Carlos C on 2009-05-20
PedroLuis, considerando lo que dice guywithcable deberías revisar cómo tienes configurado tu archivo xorg.conf (supongo que tendrías que entrar al sistema usando el LiveCD). Por otro lado, ¿qué driver estás usando? ¿los privativos o los libres?

---

### Post by PedroLuis on 2009-05-21
> **Carlos C said:**
> PedroLuis, considerando lo que dice guywithcable deberías revisar cómo tienes configurado tu archivo xorg.conf (supongo que tendrías que entrar al sistema usando el LiveCD). Por otro lado, ¿qué driver estás usando? ¿los privativos o los libres?
Hola Carlos, los drives no se cual quedaron en este 9.04, pero por lo general uso los libres.

Puedo entrar con el cd del 8.10 , pero no se como hacer cambios, como llegar al disco duro del pc, y no estar viendo las carpetas del cd solamente.

Cuando entro al pc,  abro en terminal el xorg.conf esta vacio, no se si es el del cd o del disco duro. como se hace para entrar del cd al disco duro y hacer los cambios que tu mencionas ?

Te agradesco la ayuda, seguire investigando para echar a andar este 9.04.

Saludos.

---

### Post by Patriciologico on 2009-05-21
Desde el LiveCd abre gparted (editor de particiones) que esta en el menu Sistema/Administracion esa aplicacion te va a montar tus particiones, luego busca la que corresponda a tu ubuntu y abres xorg.conf

Saludos!

---

### Post by PedroLuis on 2009-05-21
> **Patriciologico said:**
> Desde el LiveCd abre gparted (editor de particiones) que esta en el menu Sistema/Administracion esa aplicacion te va a montar tus particiones, luego busca la que corresponda a tu ubuntu y abres xorg.conf

Saludos!
Hola, cuando entro con Lcd  de 8.10 a gparted salen las particiones  especificando  que en /dev/sda1  esta en ext3, pero no esta montada
/dev/sda2  extended si esta montada
/dev/sda5  linux-swap  esta  activa

Raro que la unica que no este montada seria la que nesecito, y en consola me dice que no encuentra /dev/sda1 en /etc/fstab ni en /etc/mtab.

Como podria hacerlo para montar o poder entrar al sistema de ficheros del disco duro?
y asi poder ver que puedo hacer con xorg.conf

---

### Post by Patriciologico on 2009-05-21
Cuando haces click con el boton derecho, sobre la particion /dev/sda1 (desde gparted) ¿te sale la opcion montar/desmontar? Puede estar con errores la particion.

---

### Post by Carlos C on 2009-05-21
Para montar esa partición debes, desde el livecd, crear una carpeta en /media. Para ello en el terminal puedes escribir:
```
sudo mkdir /media/nombre_que_quieras
```Estas creando la carpeta en memoria ram. Si reinicias se perderá, pero no importa, te sirve. Luego montas la partición en esa carpeta:
```
sudo mount -t ext3 /dev/sda1 /media/nombre_que_quieras
```Ahora cuando accedas a la carpeta /media/nombre_que_quieras estarás accediendo a tu partición "/".

---

### Post by guywithcable on 2009-05-21
> **PedroLuis said:**
> Hola Carlos, los drives no se cual quedaron en este 9.04, pero por lo general uso los libres.

Puedo entrar con el cd del 8.10 , pero no se como hacer cambios, como llegar al disco duro del pc, y no estar viendo las carpetas del cd solamente.

Cuando entro al pc,  abro en terminal el xorg.conf esta vacio, no se si es el del cd o del disco duro. como se hace para entrar del cd al disco duro y hacer los cambios que tu mencionas ?

Te agradesco la ayuda, seguire investigando para echar a andar este 9.04.

Saludos.

Puedes montarla del menu "Lugares" de Gnome. (En la version ingles, es Lugares, no se si sea el mismo.) Se lista como "XX GB Media".

---

### Post by PedroLuis on 2009-05-21
> **Carlos C said:**
> Para montar esa partición debes, desde el livecd, crear una carpeta en /media. Para ello en el terminal puedes escribir:
```
sudo mkdir /media/nombre_que_quieras
```Estas creando la carpeta en memoria ram. Si reinicias se perderá, pero no importa, te sirve. Luego montas la partición en esa carpeta:
```
sudo mount -t ext3 /dev/sda1 /media/nombre_que_quieras
```Ahora cuando accedas a la carpeta /media/nombre_que_quieras estarás accediendo a tu partición "/".
  Segui tus indicaciones, y agrege al xorg.conf lo que encontre en una paguina por que en el que yo tenia se veia bastante reducido, no se que pasara pero le agrege lo siguiente

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection
Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	**DefaultDepth	24**
EndSection
Section "Device"
	Identifier	"Configured Video Device"
	[B]Driver	"vesa"
	Option	"NoLogo"	"True"[/B]
EndSection
Yo tenia solo lo que esta en letras simples , le agrege lo que marco mas negro.
Ahora voy a reiniciar sin el Live cd para ver si funciona.

---

### Post by PedroLuis on 2009-05-21
Lamentablemente no solucione el problema, seguire investigando, pero ahora por lo menos se como montar particiones desde el LiveCD.

Si alguien tiene una idea o consejo es bien aceptado.

Saludos.

---

### Post by Patriciologico on 2009-05-22
Las opciones que agregaste indican, que usas el driver Vesa, que es un "digamos" genérico cuando no se encuentra el driver de tu tarjeta (aveces pasa con las Via) DefaultDepth 24 es la profundidad de color 24 bits, generalmente ese valor esta bien, se puede bajar a 16 se gana en rendimiento, pero se pierde en calidad. Y la opción Nologo, la usaba con los drivers Nvidia, que tendían a instalarte un splash de inicio, con esa opcion se  desactivaba.

[Aqui pegue el Xorg de Jaunty]("http://ubuntuforums.org/showpost.php?p=7321287&postcount=13") **Si tu usas Hardy no uses el que yo postee** , mas bien carga un live cd y copialo de ahi.

---

### Post by PedroLuis on 2009-05-22
> **Patriciologico said:**
> Las opciones que agregaste indican, que usas el driver Vesa, que es un "digamos" genérico cuando no se encuentra el driver de tu tarjeta (aveces pasa con las Via) DefaultDepth 24 es la profundidad de color 24 bits, generalmente ese valor esta bien, se puede bajar a 16 se gana en rendimiento, pero se pierde en calidad. Y la opción Nologo, la usaba con los drivers Nvidia, que tendían a instalarte un splash de inicio, con esa opcion se  desactivaba.

[Aqui pegue el Xorg de Jaunty]("http://ubuntuforums.org/showpost.php?p=7321287&postcount=13") **Si tu usas Hardy no uses el que yo postee** , mas bien carga un live cd y copialo de ahi.

Realmente este que me muestras es el que estaba en el 9.04 que tengo instalado en el pc que no puedo hacer funcionar, lo cambiare nuevamente, por que veo que esa no era la solucion a mi problema. 

gracias.

---

### Post by Carlos C on 2009-05-24
Hola. Me gustaría saber si luego de restaurar tu xorg.conf en qué situación te encuentras. Si usas el driver libre, consigues entrar a tu sesión o continua la cosa igual?

---

### Post by PedroLuis on 2009-05-26
> **Carlos C said:**
> Hola. Me gustaría saber si luego de restaurar tu xorg.conf en qué situación te encuentras. Si usas el driver libre, consigues entrar a tu sesión o continua la cosa igual?
 
Solucione el problema, cambie la tarjeta grafica, el disco duro, ( tengo restos de pc que encuentro en una casa de resiclaje, donde botan pc). 

Instale el 8.10 y de ahi lo actualise a 9.04, funciona de lo mas bien.

Gracias por las respuestas, deje anotada ya bastante informacion que me servira en el futuro.

Que esten bien.

---

