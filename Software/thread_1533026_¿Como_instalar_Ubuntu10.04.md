---
title: "¿Como instalar Ubuntu10.04?"
date: 2010-07-17
forum: Software
---

### Post by Cacique1 on 2010-07-17
Hola. Estuve investigando en la Web y elabore un proyecto para instalar Ubuntu 10.04. Mi PC es una Olivetti con Intel Pentium Dual-Core E2200, tiene un disco de 250 GB (particionado en 40 GB para Windows y el resto Libre) y 2 GB de memoria RAM. 
  Mi intención es usar el instalador de Ubuntu para crear una partición de 25600 MB (25 GB) en la partición Libre. Después en ella crearía las siguientes particiones:
   
  • partición raíz (/) de 8192 MB (8 GB).
  • área de intercambio (swap) de 2048 MB (2 GB).
  • partición para datos del usuario (home) de 15360 MB (15 GB).
   
  Aquí es donde tengo algunas dudas:
   
  **1)** ¿Los tamaños de las particiones están bien calculados? ¿Es suficiente espacio?.
   
  **2)** Algunos dicen que las particiones “raíz /” y “home” deben tener formato “ext3” y otros que debe tener “ext4”. ¿Cuál es el formato que debe usarse?.
   
  **3)** En algunos sitios recomiendan que la partición “raíz /” sea Primaria y la partición “swap” sea Lógica. En otros dicen que sean todas Lógicas. ¿Cómo debo configurarlas?.
   
  **4)** En algunos sitios dicen que las particiones “raíz /” y “home” deben ubicarse al Principio y la partición “swap”, al Final. Según dicen, esto es porque la zona exterior de los discos gira más rápido y es conveniente colocar allí las particiones que más van a usarse. ¿Es esto correcto? ¿Debo colocar así las particiones?.
   
  **5)** ¿Cuál distribución de teclado debo elegir? ¿Latino America o España? Lo digo porque en la Latino America pareciera que las eñes no funcionan y en las de España sí. 
   
  **5) **He leído que es importante saber los bits del procesador. ¿Cómo puedo hacer para saber si mi procesador es de 32 bits o 64 bits?. Utilizo el Windows XP Professional.
   
  **6)** Ya que voy a compartir el equipo entre Ubuntu y Windows, quiero instalar el “Avast! Linux Home Edition”. En su página me ofrecen 3 paquetes para descargarlo: RPM package; DEB package; TAR GZ package. ¿Cuál es la que me conviene?. Aclaro que no tengo conexión a Internet, por lo que debo bajar los datos a una memoria USB y luego instalarlos en mi PC.
   
  Bueno, espero no haber formulado demasiadas preguntas. Lo que sucede es que es la primera vez que voy a realizar una instalación de esta naturaleza y quiero estar lo más seguro posible de hacerlo bien. Desde ya, agradezco cualquier respuesta.

---

### Post by alfplayer on 2010-07-17
Ese particionado no parece mal.

Yo usaría ext4, que es el predeterminado de Ubuntu.

La diferencia de usar particiones extendidas y lógicas es para no estar limitado a cuatro particiones (primarias).

Igualmente, se puede usar el particionado automático del instalador de Ubuntu. 

Usá la distribución de teclado que le funcione todos los caracteres. Si es España, usá esa.

Ese CPU soporta 64 bits.

---

### Post by euzkoarima on 2010-07-17
Los tamaños están bien, pero le dejaría 1 a la swap y el Gb ahorrado se lo pasaría a / (que pasaría a 9).
Prefiero Ext4 para / y /home
Con respecto al programa que querés instalar, ubuntu usa los .deb (por ser "descendiente" de debian).

Saludos,
Eduardo

---

### Post by Cacique1 on 2010-07-24
[FONT=&quot][SIZE=3]Hola. Quiero decir que ya instale Ubuntu 10.04 y ya esta funcionando en mi PC. MUCHAS GRACIAS por las respuestas que me ayudaron a llevar la instalación a buen puerto. Hasta ahora solo he tenido un par de problemas.[/SIZE][/FONT][SIZE=3]

[/SIZE]      [FONT=&quot][SIZE=3]Cuando quiero reproducir un video o una canción, me aparece un mensaje diciendo que faltan las siguientes aplicaciones:[/SIZE][/FONT][SIZE=3]
[/SIZE]   [FONT=&quot][SIZE=3]• Decodificador  MPEG-1 Layer3 (MP3).[/SIZE][/FONT][SIZE=3]
[/SIZE]   [FONT=&quot][SIZE=3]• Decodificador XVID MPEG-4.[/SIZE][/FONT][SIZE=3]
[/SIZE]   [FONT=&quot][SIZE=3]He tratado de ver si están en los repositorios del CD de Ubuntu (enviado por correo). Pero al entrar en “Administración” – “Orígenes del software” – “Añadir CD-ROM…”, me aparece un mensaje en inglés diciendo que falló la lectura del CD-ROM. Probe hacer una sesión Live y el CD anduvo perfecto. No sé porque Ubuntu no lo lee.[/SIZE][/FONT][SIZE=3]
[/SIZE]   [FONT=&quot][SIZE=3]¿Debo hacer algo más para que reconozca el CD? ¿Debo bajar las aplicaciones del Centro de Software? Aclaro que no tengo conexión a Internet y debo bajarlas a una memoria USB primero.[/SIZE][/FONT][SIZE=3]

[/SIZE]      [FONT=&quot][SIZE=3]Otro  problema es que usé el pendrive en Ubuntu y cuando lo quiero abrir en Windows XP, este niega el acceso. Debo hacer la “Comprobación de errores”, dejando tildada la opción de “Reparar errores en el sistema de archivos”. Después de hacer esto, puedo abrirlo. Pero si lo desconecto y lo vuelvo a conectar, el problema vuelve a aparecer.[/SIZE][/FONT][SIZE=3]
[/SIZE]   [FONT=&quot][SIZE=3]¿Por qué sucede esto? ¿Debo mover todos los archivos y formatearlo?.[/SIZE][/FONT][SIZE=3]

[/SIZE]      [FONT=&quot][SIZE=3]Desde ya, agradezco cualquier respuesta.[/SIZE][/FONT]

---

### Post by guillermolisi on 2010-07-24
Cacique1

Felicitaciones por el logro !

Para los problemas que mencionas es buena practica:


[LIST]
[*] Buscar en el foro si el problema ya fue tratado y resuelto
[*] Si no lo fue (o luego de su busqueda no encontras algo util) abri un hilo/thread especifico por tema/problema, a saber:
[LIST]
[*]Software (repositorios, utilitarios, aplicaciones, etc. En general todo lo que no se pueda patera y solo se lo pueda insultar excluyendo drivers).
[*]Hardware (todo lo que se pueda patear).
[*]Comunidad (todo lo que pueda ser tratado tomando un cafe, cerveza o mate para mejorar el intercambio de opiniones).
[/LIST]
[/LIST]
Asi lograras aprovechar al maximo la utilidad de este canal de comunicacion.

---

### Post by euzkoarima on 2010-07-24
Con respecto a lo de mp3 y otros formatos, comenzá por instalar el paquete ubuntu-restricted-extras (está en multiverse)

Saludos,
Eduardo

---

### Post by Cacique1 on 2010-07-26
Gracias por las respuestas. Ya abrí un nuevo tema. Hasta luego.

---

