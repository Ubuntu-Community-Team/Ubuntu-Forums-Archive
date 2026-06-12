---
title: "Instalar paquetes ubuntu offline"
date: 2009-12-01
forum: Software
---

### Post by pinguinosaurio on 2009-12-01
**Ultima actualización: 04-01-2010 **(Publicado UNVi 0.04c, actualizado para funcionar en Ubuntu Maverick y cambio de sitio web.)

UNVi es un simple Script con interfaz gráfica amigable para el usuario común, mediante la cual se pueden instalar paquetes de software .deb de ubuntu, sin necesidad de tener una conexión a internet en su PC. Simplemente se necesita tener acceso a internet desde otro PC que use Windows, tener un pendrive o similar para guardar información, y las ganas de aprender :P
Descargue la última versión desde aquí:
 
[http://unvi-gnulinux.blogspot.com/]("https://sourceforge.net/projects/unvi/")
 
En la siguiente página web podrán encontrar información avanzada sobre el uso de UNVi, como por ejemplo, adaptar el script para usarlo en Debian:
 
[http://novatocba.netii.net/](http://novatocba.netii.net/)
 
A quienes me envían mails agradeciendo mi trabajo y notificando bugs, muchas gracias.

---

### Post by 3nG3ndR0 on 2009-12-03
primero que todo felicidades esta muy interesante amigo, me u viese servido mucho cuando no tenia Internet.

seguro que mas de alguien le vendrá de lujo este post

---

### Post by pinguinosaurio on 2009-12-03
Hice este script lo mas simple posible, tanto que incluso tiene interfaz grafica para que el usuario novato que se acerca recien linux, no se agarre con la terminal :)

gracias por tomarte el tiempo de contestar, hasta la proxima

---

### Post by Patriciologico on 2009-12-08
Felicitaciones, agrego que las instrucciones van dentro del paquete,

Saludos!

---

### Post by Abraxsmano on 2009-12-14
> **pinguinosaurio said:**
> Que tal amigos, soy nuevo en el foro y queria informarles que he creado un Script con interfaz grafica para que los usuarios de ubuntu karmic, que no tienen conexion a internet puedan descargar e instalar paquetes sin los problemas de dependencias de paquetes desde otro pc que use windows. dentro del fichero viene un manual, les recomiendo que lo lean antes, sino se perderan. Esta testeado que funciona.
 
[este es el link]("http://sourceforge.net/projects/unvi/")
 
Saludos!!!!!!
 
Cualquier duda pueden consultarla aqui
 
Gracias ,es un gran aporte, a mi me fue de gran utilidad , todo fue rapido sin mayores complicaciones, saludos;)

---

### Post by pinguinosaurio on 2009-12-20
Me alegra que le haya servido, estoy trabajando para que el prceso siga siendo aun mas automatico, y talvez crear un instalador de paquetes exclusivo para instalar paquetes offline en un futuro.
 
hasta la proxima!!!!

---

### Post by pinguinosaurio on 2010-01-09
[FONT=Comic Sans MS][SIZE=2]Que tal nuevamente, les escribo para informarles que he actualizado el Script UNVi, las mejoras son:

[/SIZE][/FONT][FONT=Comic Sans MS][SIZE=2]Versión             0.03 (8 de Enero del 2010)[/SIZE][/FONT]
             [FONT=Comic Sans MS][SIZE=2]-             Agregado el soporte para el repositorio 'ubuntu-proposed'[/SIZE][/FONT]
             [FONT=Comic Sans MS][SIZE=2]-             Mejora del código del script UNVi[/SIZE][/FONT]
             [FONT=Comic Sans MS][SIZE=2]-             UNVi ahora se puede usar en cualquier versión de Ubuntu que tenga             instalado Zenity (viene por defecto en las últimas versiones)[/SIZE][/FONT]
             [FONT=Comic Sans MS][SIZE=2]-             Corrección de algunos bugs[/SIZE][/FONT]
[FONT=Comic Sans MS][SIZE=2]
[/SIZE][/FONT]

---

### Post by pinguinosaurio on 2010-01-14
[FONT=Comic Sans MS][SIZE=2]Debido a serios problemas para subir UNVi en sourceforge, debí buscar un host temporal, afortunadamente se ha solucionado el problema y he vuelto a usar Sourceforge, he editado el primer post para que los el link los dirija a sourceforge.
Espero que los moderadores no se enojen con tanta edicion de este hilo :)[/SIZE][/FONT]

---

### Post by Carlos C on 2010-01-15
No hay problema, es mejor que lo mantengas actualizado.

Saludos.

---

### Post by pinguinosaurio on 2010-08-25
Que tal, luego de algun tiempo de inactividad, comenzaré a trabajar nuevamente en UNVi, pero esta vez necesitaré ayuda, pensaba que quizá en este foro me pudiesen dar una mano.
 
El que ha usado UNVi se habrá dado cuenta que necesita una maquina con Windows que tenga conexion a internet para descargar los repositorios y luego los paquetes .deb, mediante scripts .bat. Estos scripts para descargar los repositorios, creaban un directorio con subcarpetas en Windows y mediante el programa wget para windows se descargan los repositorios desde internet en las carpetas creadas.
Los paquetes .deb se descargan con un script que los descarga desde internet usando wget para windows.
 
Pienso que es un tanto "ilógico" tener que depender de un sistema operativo exclusivamente, se me ha ocurrido entonces que desde el sitio web de UNVi el usuario pueda seleccionar su distribucion de Ubuntu y que se cree un directorio y sus subcarpetas automaticamente, guardandose allí los repositorios descargados en el PC con conexión a internet, independiente del sistema operativo que se use, lo mismo sería con los paquetes .deb, en que el sitio web le pida el archivo que contiene los links de descargas de los paquetes .deb y luego los descargue automáticamente al PC.
 
He pensado que usar JAVA seria una solucion. Lamentablemente yo no tengo idea de como programar algo así en Java, por eso invito a quien tenga conocimientos en este lenguaje para echarme una mano.
 
Desconozco si esto se puede hacer con CGI o PHP, pero si se puede hacer en estos lenguajes, tambien invito a quiene puedan ayudar.
[EMAIL="infragilisx2@gmail.com"][/EMAIL]

---

### Post by peixe80 on 2010-09-09
Hola.

Hace varios años había una web desde donde uno se podía generar sus propios índices y buscar y descargar programas. Estaba pensada para Debian, pero funcionaba en Ubuntu y cualquier otra distribución basada en Debian. Al cabo de un tiempo dejaron de mantener ese proyecto y la web desapareció. Yo la utilicé durante unos meses y funcionaba perfectamente. No me acuerdo de cuál era la ruta de la página y, aunque he buscado, no he encontrado en Internet información antigua sobre ella. Si encuentro algo lo posteo aquí. Quizás novatocba se acuerde...

Por otra parte, no sé si conocéis este otro proyecto:
[http://keryxproject.org/](http://keryxproject.org/)
No he tenido tiempo de probarlo, pero tiene buena pinta.
Ya diréis qué os parece.

Siento no poder aportar más.

Saludos y ánimo con el trabajo.

---

### Post by WillmanBlanco on 2012-03-29
Lo probe para la distribucion Lucid y funciono muy bien, este es un gran aporte. Espero puedas seguir mejorandolo y actualizarlo para las nuevas distribuciones de Ubuntu.

Estare esperando nuevas de este post, un saludo cordial.

):P

---

