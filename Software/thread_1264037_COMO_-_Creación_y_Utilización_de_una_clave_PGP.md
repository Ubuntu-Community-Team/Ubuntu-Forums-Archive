---
title: "COMO - Creación y Utilización de una clave PGP"
date: 2009-09-11
forum: Software
---

### Post by pablo.s on 2009-09-11
[SIZE=4][B]COMO - Creación y Utilización de una clave PGP
PRIMERA PARTE
[/B][/SIZE]
Traducción de [este post]("http://ubuntuforums.org/showthread.php?t=1146081") realizado por [daboroe]("http://ubuntuforums.org/member.php?u=272412"),
usuario de Ubuntu Forums.

El siguiente tutorial puede ser utilizado para ayudar a
todo usuario que quiera crear una clave OpenPGP con
los fines de cifrar/descifrar archivos o enviar y recibir
correo electrónico cifrado.

[SIZE=3]*** Crear su clave PGP***[/SIZE]

La utilización de PGP (Pretty Good Privacy; en español
significa Privacidad Bastante Buena) es un asunto del
presente y del futuro. En MS Windows usted tiene que
adquirir PGP. En Ubuntu hay una manera de utilizarlo y se
lo conoce como OpenPGP. Es la misma aplicación pero una
implementación abierta. PGP puede ser utilizado para el
cifrado/descifrado de archivos y correo electrónico.

Primero vamos a elegir en el menú Aplicaciones el submenú
Accesorios. En ese submenú nos aparece una entrada que
dice "Passwords and Encryption Keys" (Contraseñas y Claves
de Cifrado). En realidad el programa se llama Seahorse, pero
en Ubuntu se lo ha renombrado así en el menú para una mejor
identificación por parte de los usuarios novatos.

[IMG]http://h.imagehost.org/0865/escrit1.png[/IMG]

Aqui se muestra que actualmente no tenemos ninguna clave
privada para OpenPGP o SSH. En este tutorial se verá la forma
para crear y encontrar claves remotas PGP.

[IMG]http://h.imagehost.org/0774/escrit3.png[/IMG]

Cuando usted haga click en "New", una ventana le solicitará
los datos para crear una clave nueva PGP o SSH. En este caso,
lo que usted desea es crear una clave PGP.

[IMG]http://h.imagehost.org/0663/esxrit.png[/IMG]

Cuando usted haga click en una nueva clave PGP y haga click
en Next, obtendrá un dialogo similar al siguiente. En este dialogo
usted debe completar con su nombre real (no su nick, ni su handle),
su dirección real de correo electrónico y un comentario que usted
considere pertinente. En el ejemplo que se muestra aqui he completado
con datos ficticios de un personaje de fantasía creado para cierta
serie de novelas.

[IMG]http://h.imagehost.org/0102/clave.png[/IMG]

En este ejemplo he elegido un tipo de cifrado RSA con una
fortaleza de 2048 bits, lo cual genera una clave mas extensa que
la de 1024 bits por defecto. He elegido que la clave tenga una
fecha de vencimiento hasta dentro de un año, por la razón que es
una clave de ejemp&#314;o para este tutorial, pero usted puede elegir que
nunca expire.

[IMG]http://h.imagehost.org/0061/contras.png[/IMG]

Cuando haga click en "Create" el programa le solicitará una frase
de contraseña. En mi caso de ejemplo he elegido la primera estrofa
de una canción: la recuerdo suficientemente bien como para olvidarla.
Le sugiero que utilice un criterio similar para su contraseña.
Se le solicitará que ingrese la contraseña dos veces para constatar
que está tipeando correctamente.

[IMG]http://h.imagehost.org/0980/Screenshot-Generating_key.png[/IMG]

Luego de clickear en OK este dialogo comenzará a generar su clave.
Se sugiere que mueva (solo mueva, no presione los botones) el ratón
para generar más entropia en el generador de claves.

[IMG]http://h.imagehost.org/0572/muestra.png[/IMG]

Luego de que concluya la generación de la clave, en la ventana
principal aparecerá en la lista de claves personales.
[B][I]Nuestra clave ha sido creada.
[/I][/B][SIZE=1][/SIZE]

---

### Post by pablo.s on 2009-09-11
[B][I][U][SIZE=4]ADDENDUM:

[/SIZE][/U][/I][/B][SIZE=1][I]Los usuarios de K Desktop Environment tienen una herramienta muy
similar a SeaHorse, llamada KGPG. La pueden instalar mediante
aptitude.
A continuación una secuencia realizada para crear una clave con KGPG.

La primera vez que se abre el programa, nos presenta un asistente de
uso para guiarnos en la configuración de las rutas de OpenGPG.

[IMG]http://h.imagehost.org/0888/1_51.png[/IMG]

El paso siguiente es confirmar que está el binario.

[IMG]http://h.imagehost.org/0542/2_14.png[/IMG]

Luego nos solicita la ruta a guardar el  archivo de configuración:

[IMG]http://h.imagehost.org/0946/3_4.png[/IMG]

El siguiente dialogo es similar al explicado arriba, donde debemos
ingresar nuestros datos.

[IMG]http://h.imagehost.org/0247/6_10.png[/IMG]

Ingresamos la frase de contraseña.

[IMG]http://h.imagehost.org/0149/7_10.png[/IMG]

La confirmación de la creación de la clave:

[IMG]http://h.imagehost.org/0555/8_6.png[/IMG]

El último paso, la clave es agregada.

[IMG]http://h.imagehost.org/0944/9_1.png[/IMG][/I][/SIZE]

---

### Post by Hei Ku on 2009-09-11
Para poder mandar correos codificados o firmados desde KMail van a necesitar Kleopatra, algo que no se menciona y que no viene instalado inicialmente.

---

### Post by pablo.s on 2009-09-11
> **Hei Ku said:**
> Para poder mandar correos codificados o firmados desde KMail van a necesitar Kleopatra, algo que no se menciona y que no viene instalado inicialmente.

Eso iba en la segunda parte:
Kleopatra, Enigmail, et al.
Me gustaria contar con la ayuda
de la muchachada de KDE para
que me asesoren.

---

### Post by juancarlospaco on 2009-09-11
Tambien esta la opcion para compartir tus llaves publicas en Broadcast en red local,
yo lo tengo asi, esta muy bueno, trato de sacarle beneficio a todo lo que trae Ubuntu.
*Cifras, Firmas, etc*

:)

---

### Post by pablo.s on 2009-09-12
[SIZE=4][B]COMO - Creación y Utilización de una clave PGP
SEGUNDA PARTE

[/B][SIZE=3]Sincronización y Publicación de nuestra
clave PGP en servidores de claves.[/SIZE][B][SIZE=3]

[/SIZE][/B][SIZE=1][SIZE=2]Ya hemos creado nuestra clave PGP. El siguiente paso consiste
en publicar la clave en un servidor de claves para que los
destinatarios de nuestros mensajes de correo (o quienes quieran
comprobar que, efectivamente hemos sido nosotros los que
hemos enviado el mensaje; en otras palabras, comprobar la
identidad del remitente).
En Seahorse clickeamos sobre el menú Remote -> Sync and
Publish Keys.[/SIZE]

[IMG]http://h.imagehost.org/0677/1_37.png[/IMG]

[SIZE=2]Una ventana de dialogo nos comenta que estamos a punto de publicar 
y/o sincronizar la clave. También informa que no hemos seleccionado
ningún servidor de claves para sincronizarla.[/SIZE]

[IMG]http://h.imagehost.org/0157/2_21.png[/IMG]

[SIZE=2]Presionamos sobre el botón que dice Key Servers para configurar los datos
del servidor de claves.[/SIZE]

[IMG]http://h.imagehost.org/0464/3_1.png[/IMG]

[SIZE=2]En nuestro ejemplo vamos a sincronizar la clave con el servidor de Ubuntu, 
aunque siempre es buena idea sincronizarla con servidores más populares,
como el de MIT o el de pgp.com
[/SIZE] 
[IMG]http://h.imagehost.org/0759/4_2.png[/IMG]

[SIZE=2]Otra ventaja es la de compartir las claves con nuestra red, permitiendo a los
usuarios de la red el poder tener las claves que obtengamos.[/SIZE]

[IMG]http://h.imagehost.org/0071/5_18.png[/IMG]

[SIZE=2]Una vez que hemos configurado los servidores de claves, cerramos
la ventana de dialogo.
[/SIZE] 
[IMG]http://h.imagehost.org/0367/6_4.png[/IMG]

[SIZE=2]Y entonces Seahorse procede a sincronizar la clave con el servidor.
Puede demorar un momento.
[/SIZE] 
[IMG]http://h.imagehost.org/0179/7_10.png[/IMG]

[IMG]http://h.imagehost.org/0087/9_5.png[/IMG]

[SIZE=2]***Al terminar, ya tenemos nuestra clave publicada.***[/SIZE]

[/SIZE][/SIZE]

---

### Post by pablo.s on 2009-09-12
[B][SIZE=4]COMO - Creación y Utilización de una clave PGP
TERCERA PARTE[/SIZE][/B]

**[SIZE=3]Firma y Cifrado de Correo Electrónico[/SIZE]**
[SIZE=2]Aclaración: Para esta parte se utiliza como software
de gestión de correo electrónico a Mozilla Thunderbird
y en el addendum para usuarios de KDE utilizamos KMail.
Usuarios de Evolution, pueden colaborar mediante PM
al traductor/autor.

Para firmar y cifrar los mensajes de correo electrónico
precisamos de un plug-in para Thunderbird llamado Enigmail.

[IMG]http://h.imagehost.org/0865/1_40.png[/IMG]

Este plug-in se descarga de su sitio oficial en forma
de archivo .XPI (el cual debemos descargar de forma
separada, cuidando que Firefox no lo instale para si;
NO es un plug-in para Firefox).

Luego que descargamos el plug-in procedemos a la
instalación desde Thunderbird en su menú Tools -> Add-ons.

[IMG]http://h.imagehost.org/0629/2_15.png[/IMG]

Una vez instalado, Enigmail nos pedirá que reiniciemos
a Thundebird. Procedemos.

[IMG]http://h.imagehost.org/0537/3_19.png[/IMG]

Cuando reinicia Thunderbird, aparece un item nuevo
en el menú con el nombre OpenPGP.
Hacemos click en el submenú Preferences.

[IMG]http://h.imagehost.org/0542/4_14.png[/IMG]

Aparece una ventana con un Asistente. Aqui en la captura
de pantalla aparece editado y simplificado, pero basicamente
tiene los pasos a seguir.

[IMG]http://h.imagehost.org/0455/wizard.png[/IMG]

Luego volvemos a las Preferencias y si quedamos
conformes con la configuración, cerramos la ventana.

[/SIZE][IMG]http://h.imagehost.org/0737/5_10.png[/IMG]

[SIZE=2]Por último, componemos un mensaje de correo y nos aseguramos 
que el mensaje se firme y/o cifre con el botón OpenPGP.[/SIZE]

[IMG]http://h.imagehost.org/0044/6_1.png[/IMG]

[SIZE=2]Listo. Nuestros mensajes ahora son más seguros para
enviar y nuestra identidad está avalada.[/SIZE]

---

### Post by josecuervo86 on 2009-09-12
Groso pablo.s! te pasaste con el thread :D

---

### Post by pablo.s on 2009-09-12
Todavia falta una parte o dos...

---

