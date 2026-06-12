---
title: "[SOLVED] VideoPics preview en Ubuntu"
date: 2008-09-04
forum: Software
---

### Post by User21 on 2008-09-04
Alguien conoce algún programa o alguna forma de generar este tipo de previews de videos en Ubuntu ?  

[IMG]http://85.17.45.27/%7Eipix/out.php/i13861_AlizeEllaEllela.jpg[/IMG]

No KDE por favor!

---

### Post by SLA_leandrin on 2008-09-04
TOTALMENTE OT:

Alizeee!!! que linda mina loco!

---

### Post by User21 on 2008-09-04
OT2: Sii, es una preciosura... y tan graciosa y sensual... T_T

---

### Post by Kabezon on 2008-09-06
> **User21 said:**
> OT2: Sii, es una preciosura... y tan graciosa y sensual... T_T
A mí no me parece la gran cosa xP

---

### Post by User21 on 2008-09-06
Al parecer, esta es una posible respuesta a mi pedido: [**qframecatcher**]("http://developer.berlios.de/projects/qframecatcher"). Se puede descargar desde [aqui.]("http://download.berlios.de/qframecatcher/qframecatcher-0.4.1.tar.gz") 

Pero es necesario compilarlo, y para ello, instalar las librerias QT para ejecutarlo. En el README del tar.gz dice:
"Dependencies:
- Qt 4.1.0 or higher
- libxine 1.1.1 or higher
- libpng

How to compile and install:
$ qmake
$ make
# make install

Run:
  qframecatcher
 qframecatcher <videofile>" 

Como leerán, está bastante claro. Intenté hacerlo via apt-get. Obtengo esto:
```
user@host:~/Escritorio/qframecatcher/src$ qmake
El programa «qmake» puede encontrarse en los siguientes paquetes:
 * libqt4-dev
 * qt3-dev-tools
Pruebe: sudo apt-get install <paquete seleccionado>
bash: qmake: orden no encontrada
user@host:~/Escritorio/qframecatcher/src$ sudo apt-get install libqt4-dev
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Se instalarán los siguientes paquetes extras:
  comerr-dev libaudio-dev libexpat1-dev libfontconfig1-dev libfreetype6-dev
  libglib2.0-dev libice-dev libjpeg62-dev libkadm55 libkrb5-dev liblcms1-dev
  libmng-dev libpng12-dev libpq-dev libqt4-core libqt4-gui libqt4-qt3support
  libqt4-sql libsm-dev libsqlite0-dev libssl-dev libxcursor-dev libxext-dev
  libxfixes-dev libxft-dev libxi-dev libxinerama-dev libxmu-dev libxmu-headers
  libxrandr-dev libxrender-dev libxt-dev x11proto-fixes-dev x11proto-randr-dev
  x11proto-render-dev x11proto-xext-dev x11proto-xinerama-dev zlib1g-dev
Paquetes sugeridos:
  libglib2.0-doc krb5-doc postgresql-doc-8.3 qt4-doc sqlite-doc
Paquetes recomendados
  qt4-dev-tools qt4-qtconfig
Se instalarán los siguientes paquetes NUEVOS:
  comerr-dev libaudio-dev libexpat1-dev libfontconfig1-dev libfreetype6-dev
  libglib2.0-dev libice-dev libjpeg62-dev libkadm55 libkrb5-dev liblcms1-dev
  libmng-dev libpng12-dev libpq-dev libqt4-core libqt4-dev libqt4-gui
  libqt4-qt3support libqt4-sql libsm-dev libsqlite0-dev libssl-dev
  libxcursor-dev libxext-dev libxfixes-dev libxft-dev libxi-dev
  libxinerama-dev libxmu-dev libxmu-headers libxrandr-dev libxrender-dev
  libxt-dev x11proto-fixes-dev x11proto-randr-dev x11proto-render-dev
  x11proto-xext-dev x11proto-xinerama-dev zlib1g-dev
0 actualizados, 39 se instalarán, 0 para eliminar y 0 no actualizados.
Necesito descargar 20,6MB de archivos.
Se utilizarán 72,5MB de espacio de disco adicional después de desempaquetar.
¿Desea continuar [S/n]? 
```

Realmente necesito tooooodas esas librerías para correr un programita minusculo? 
Pues, me parece una exageración bajar 72 MBs de librerías que no se si son nativas, para minúsculo programita... Alguien me explica ? Qué debo hacer?

---

### Post by luks911 on 2008-09-06
Una aclaración que tal vez no ayude mucho, pero bueh... vas a tener que descargar 20 MB que después van a ocupar 72. 
Y otra cosa, ¿y si probás instalando qt3-dev-tools en lugar de libqt4-dev hay mucha diferencia de peso? Yo me fije y tengo ese paquete y el qmake. No sé por qué ni cuando se instaló, pero ahí está, y no tengo el libqt4-dev.

EDIT: También encontré un tal Videocut que sirve para lo mismo, aunque también es para KDE ([http://code.google.com/p/videocut/](http://code.google.com/p/videocut/))..

---

### Post by Hei Ku on 2008-09-06
libqt4-dev tiene todos los headers de desarrollo de qt, por eso es tanto.

qt3dev-tools parece una mejor opcion.

---

### Post by leo_rockway on 2008-09-06
Te negás a KDE, pero después querés instalar bibliotecas QT... no entiendo.

---

### Post by User21 on 2008-09-06
No es que quiera instalarlas! Son las obligadas dependencias del programa, y no he encontrado nada parecido en Gnome o para GTK. No es una decisión propia. De poder usar una aplicación nativa, no estaría escribiendo este post...

Por qué siempre salta algún flame??? ¬_¬

En definitiva. Acabo de probar con la 3, y el programa me exige al menos la 4.1.0 ! Pequeño detalle.
Al demonio. ¬_¬

---

### Post by leo_rockway on 2008-09-06
> **User21 said:**
> 
Por qué siempre salta algún flame??? ¬_¬


Jaja, no era flame, simplemente no entendía la contradicción.

---

### Post by User21 on 2008-09-07
Gracias a Lucas Livchits , desde la lista de correo de Ubuntu-AR, conozco esta simple solución a mi problema!  
" [Movie Thumbnailer ]("http://www.cli-apps.org/content/show.php/Movie+Thumbnailer?content=74676")es un script de bash que te permite **extraer varios frames de un video y componerlos en una imagen única**. Puedes elegir cuántas capturas quieres, el tiempo que debe transcurrir entre ellas y el tamaño final de la imagen. Tiene una función de captura aleatoria para que cada vez que lo ejecutes el resultado sea diferente. "
También me remitió al siguiente [enlace]("http://www.genbeta.com/2008/02/10-capturar-pantallazos-y-miniaturas-de-videos-en-gnulinux"). Muchísimas gracias!
El resultado final fue este:

---

### Post by Kabezon on 2008-09-07
> **leo_rockway said:**
> Jaja, no era flame, simplemente no entendía la contradicción.
Es que KDE no nos convence xP Yo lo usé pero nah, no sé, Gnome me parece mucho más práctico y, mátense de risa, más lindo :P Pero no se puede negar que algunas aplicaciones de KDE son zarpadas, así que las uso igual.

---

### Post by JuanC on 2009-02-06
> **User21 said:**
> No es que quiera instalarlas! Son las obligadas dependencias del programa, y no he encontrado nada parecido en Gnome o para GTK. No es una decisión propia. De poder usar una aplicación nativa, no estaría escribiendo este post...

Por qué siempre salta algún flame??? ¬_¬

En definitiva. Acabo de probar con la 3, y el programa me exige al menos la 4.1.0 ! Pequeño detalle.
Al demonio. ¬_¬

Prueba a usar [GFrameCatcher]("http://gnomefiles.org/app.php/GFrameCatcher")

---

