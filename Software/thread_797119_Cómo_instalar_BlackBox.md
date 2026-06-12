---
title: "Cómo instalar BlackBox?"
date: 2008-05-17
forum: Software
---

### Post by Friendy on 2008-05-17
Hola, soy un newbi y quisiera saber si puede ayudarme a instalar este paquete, uso la versión 6.10 y se me ha complicado encontrar el paquete en la extensión .deb y no sé que rayos.

Y tengo la duda si este theme es para balckbox u otro cosa xD 
[http://customize.org/litestep/themes/54367](http://customize.org/litestep/themes/54367) (no sé si lo considerarán spam, si es así pido disculpas)

Ojalá que me puedan ayudar, he buscado varios tutos entre otras cosas pero no me salió y no sé donde poder preguntar.

Saludos.

---

### Post by faktorqm on 2008-05-17
Es para litestep eso, absolutamente nada que ver con blackbox.

---

### Post by Friendy on 2008-05-17
Gracias por sacarme la duda. 
Bueno decidí probar con los gnome themes que encontré en la misma pág. pero están en extensión tar.gz lo mismo con [este]("http://www.gnome-look.org/content/show.php/Blue+Abstract?content=81177") tema. No sé cómo poder instalarlos, pensé que sólo tenía que usar los formatos .deb asi que me he mareado un poco, disculpen mi ignorancia.

Saludos.

---

### Post by valucha on 2008-05-18
[COLOR="DarkOrchid"]> **Friendy said:**
> Gracias por sacarme la duda. 
Bueno decidí probar con los gnome themes que encontré en la misma pág. pero están en extensión tar.gz lo mismo con [este]("http://www.gnome-look.org/content/show.php/Blue+Abstract?content=81177") tema. No sé cómo poder instalarlos, pensé que sólo tenía que usar los formatos .deb asi que me he mareado un poco, disculpen mi ignorancia.

Saludos.


Bueno, tenés que tener cuidado con esa página porque no todo lo que hay allí son themes:

Lo que dice GTK serían los controles, te cambia el "skin" de todos los programas por decirlo de una forma, los botones, las barritas, el color de fondo, etc. Se instalan yendo a Sistema->Preferencias->Apariencias.. Alli te va a aparecer un recuadro con muchos themes que vienen por defecto en Ubuntu y agarrás el theme que te bajaste y lo arrastrás a esa caja, acto seguido te va a decir "el tema xxxxxxxxx ha sido instalado correctamente, desea utilizarlo ahora?" y si asi lo deseas le pones OK.

Lo que dice "metacity" serían los bordes de ventana, donde esta el título y los botones de maximizar minimizar y cerrar. Los bajas y los instala de la misma misma forma que los GTK.

Ojo que si vos te instalaste Compiz Fusion y también Beryl para adornar los bordes de ventanas, los cambios que hagas con el "metacity" ni los vas a ver... Tenés dos ociones, o desactivar Beryl como "adornador" de ventanas o buscarte temas para Beryl.  ELlos se encuentran en la parte de "Beryl" o "Compiz" de esa misma página. Para instalarlos vas (creo, porque yo no tengo instalado  Beryl) sistema->preferencias->"algo con Beryl" y te aparece una caja de dialogo en la que tenés que buscar un boton a la derecha que dice "install", lo apretás, buscas en dondehayas dejado el archivo que bajaste (que si o si debe ser .emerald  , ej: blue.emerald) y lo instalás. LUego se te va a agregar automaticamente a la lista de themes abajo y lo seleccionas... OJo que el cambio puede no verse instantaneamente como con los themes de gtk y metacity, tal vez tengas que reiniciar los graficos poniendo "ctrl+alt+backspace" (backspace = tecla borrar).

GDM es el programa que te maneja el inicio, y por ende, la forma que tienen tus ventanas de inicio (donde pones la contraseña y demases). Cuando te bajes un theme desde la seccion "GDM" de esa pág vas a tener que ir a Sistema->administracion->ventana de entrada... Allí seleccionas la pestaña "local" y te aparece una lista con los themes disponibles. Luego hacés lo mismo que con el gtk y metacity, arrastras tu theme y luego lo seleccionas.

Los iconos se bajan desde la sección iconos :p y lo instalas igual igual que el metacity y el gtk. Puede que haya iconos que te cambien TODOS Los iconos y quede muy bonito, pero puede  que haya otros que te cambien parcialmente. Eso depende de: la cantidad de iconos que tiene ese paquete, y además de la version de gnome que soporta. Hace poco se cambio la version y no había paquete de iconos que te cambiara los iconos del menú y a mi persdonalmente no me gustaban, así que los cambiaba a mano. Luego empezaron a hacer y a arreglar los paquetes para que se solucionara y ahora andan bien la mayoria de los nuevos, pero si te pones uno viejo es posible que no te los cambie. Igualmente si te gusta,no te preocupes, no te afecta en nada el redimiento o la configuración de la máquina, es cuestión de gustos.


Info aparte:

1) Los themes de: GTK, Metacity, Iconos y GDM tienen la extensión .tar.gz es decir, son archivos comprimidos. Si hacés doble click vas a ver los archivos y todo eso, no pasa nada. Pero para instalarlos no los descomprimas arrastralos asi comprimidos como te indiqué arriba.

2)EN la ventana de "Apariencia" podés cambiar varias cosas... Pero si te localizas en la pestaña "tema" podés seleccionar un theme cualquiera y poner uno de los botones de abajo "Personalizar" ahi podés cambiarle los iconos por otros si es que no te gustan los que instalaste, el metacity o el gtk. Algunos GTK como los qye son "clearlooks algo" "murrine algo" "aurora algo" permeten que le cambies los colores... Asi que podes seleccionar por ejemplo "clearlooks classic" y cambiarle los colores por el que te plazca...

3) Para cambiar los iconos del menú, tenes que hacer click derecho sobre él y poner "editar los menus".. Te aparece una ventana con todos los programas que tengas y no solo que podés ocultarlos (es decir que no aparezcan en el menu) y desocultarlos (que aparezcan) sino que también si hacés click derecho sobre alguno y ponés "editar" te aparecen las propiedades de ese lanzador (que serian como accesos directos al programa) y allí haciendo click en el ícono podés cambiarlo por otro quer te guste más...


Bueno, creo que es todo, es muy fácil, lo único que te puede marear es el tema de Beryl y metacity. Que básicamente cumplen la misma funcioón pero hay gente a la que le gusta más uno y hay gente que gusta más del otro. 
Por defecto viene "metacity" asi que si tenes dudas es posible que utilices este. 
Si querés cambiarlo por Beryl avisanos que te enseñamos como.

Si tenés otra duda, avisá...

Espero que te haya servido


Saludos[/COLOR]

---

### Post by faktorqm on 2008-05-18
[http://ubuntuforums.org/showthread.php?t=571448](http://ubuntuforums.org/showthread.php?t=571448)

---

### Post by Friendy on 2008-05-20
Muchas gracias Valucha! Tu post explayado me ha ayudado muchísimo, algunas cosas no me salerion del todo bien xp ya que se me dificulta por la versión que tengo, ya me estoy bajando el hardy...

Realmente, muchas gracias. También a faktorqm por pasarme el link! Volveré con manos a la obra!

Saludos.

---

