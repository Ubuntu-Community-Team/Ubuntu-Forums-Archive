---
title: "[SOLVED] Cambiar iconos del área de notificacion."
date: 2007-12-19
forum: Software
---

### Post by valucha on 2007-12-19
[COLOR="DarkOrchid"]Hola chicos, acá vengo nuevamente a molestar :). Ahora esuna pregunta más de personalización.
Quería saber como poder cambiar los iconos de cada programa en el applet del área de notificacion. EN el gconf-editor hay una opcón dentro de Panel que te dice "use custom icon" y te da la posibilidad de poner un custom icon. Pero me suena que me va a poner 1 solo icono para todos los programas.

Después busqué por cada programa pero no encontré nada...

Tienen idea de donde los puedo encontrar?

MIl gracias desde ya.[/COLOR]

---

### Post by User21 on 2007-12-19
DONDE DONDE, no se, pero cada programa tiene su icono especial. Yo lo buscaría en la carpeta del programa, y cambiaría el PNG que usa como icono en el area de notificación, copiandolo con otro nombre, y poniendo el de mi elección. Ya se que es muy vaga mi respuesta, pero dado la naturaleza LIBRE del código, en Ubuntu, solo reemplazaría el PNG que a mi entender es el que pone en el tray, conservando el nombre original. 

Ahora no estoy en mi casa, pero quiero probarlo cuando llegue. Voy a cambiarle el icono al Rythmbox, a ver que onda.
de todas formas, cada vez que pones un nuevo icon theme, estos cambian! Por alli, si notas que alguno cambia algunos de esos iconos del tray, podrias editar el paquete de iconos! el tar.gz o tar.bz ! Suerte.

---

### Post by valucha on 2007-12-19
> **User21 said:**
> DONDE DONDE, no se, pero cada programa tiene su icono especial. Yo lo buscaría en la carpeta del programa, y cambiaría el PNG que usa como icono en el area de notificación, copiandolo con otro nombre, y poniendo el de mi elección. Ya se que es muy vaga mi respuesta, pero dado la naturaleza LIBRE del código, en Ubuntu, solo reemplazaría el PNG que a mi entender es el que pone en el tray, conservando el nombre original. 

Ahora no estoy en mi casa, pero quiero probarlo cuando llegue. Voy a cambiarle el icono al Rythmbox, a ver que onda.
de todas formas, cada vez que pones un nuevo icon theme, estos cambian! Por alli, si notas que alguno cambia algunos de esos iconos del tray, podrias editar el paquete de iconos! el tar.gz o tar.bz ! Suerte.
[COLOR="DarkOrchid"]
Tengo unb paquete de iconos de mac4lin , porque es el unico que hasta ahora me cambio la mayor parte de los iconos.
Estuve investigando y tiene los iconos de la red, rhythmbox, y las cosas que quiero cambiar pero no los usa :S usa el predeterminado que es feucho.

Igualmente me ayuudaria mucho saber tambien como sacar el icono de la red solo, porque lo tengo medio al ****.

Otra cosa es que yo tengo el applet del tiempo, y me había cambiado los iconitos por unos negros que quedaban re lindos. Pero de un segundo para el otro (parece ser que se actualizó) se cambió al viejo, que no es que no me guste, pero me gustaria tener toda la barra con los iconos negros.
[/COLOR]

---

### Post by User21 on 2007-12-19
El icono de la red, es un gnome-applet! Con solo darle clic derecho, destildar la opción de Bloquear al panel, y quitar del panel, debería desaparecer. Si queres cambiar los iconos, deberíamos averiguar la ruta de los applets y ver que se puede hacer. NUEVAMENTE, hablo desde lo hipotético. Sigo en el trabajo! xD

---

### Post by valucha on 2007-12-19
[COLOR="DarkOrchid"]NO, no es un applet cualquiera, hago click derecho y me aparece activar red, o info sobre la conexión. Hago click izquierdo y dice red cableada y conf manual. La unica forma que conozco de sacarlo es sacando el sistray :)[/COLOR]

---

### Post by thenry on 2007-12-19
valucha, el applet que decis de red lo sacas en Sistemas-Preferencias-Sesiones y desmarca la opción Networ manager que es el applet de red.
Con respecto a los iconos en el area de notificación , en la mayoria tenes que ir a la carpeta del programa en cuestion por ejemplo en el rhythmbox vas a /usr/share/rhythmbox/icons/hicolor/22x22/status . como administrador y cambias el icono por el que te gusta. en el pidgin seria en /usr/share/pixmaps/pidgin/status y elegis el tamaño deseado y ahi cambias el icono.
ahora para cambiar los iconos del gweather o el applet del tiempo , lo primero que tenes que hacer es ir a esta ruta /usr/share/icons/gnome/22x22/status fijarte bien los iconos del tiempo que aparecen con sus respectivos enlances y copiarles los nombres , una vez que ya tenes los nombres y los iconos que vos queres poner ,y ya que tenes el paquete de mac4lin anda a /home/usuario/.icons/Mac4Lin_Icons_v0.3a/scalable/stock y ahi pegas los iconos que vos queres con los nombres que figuraban en la carpeta de iconos de gnome. sino te llegan a aparecer los iconos de una, saca el applet y volvelo a poner y ahi tendria que andar.
espero que te sirva.
salu2!

---

### Post by valucha on 2007-12-20
> **thenry said:**
> valucha, el applet que decis de red lo sacas en Sistemas-Preferencias-Sesiones y desmarca la opción Networ manager que es el applet de red.
Con respecto a los iconos en el area de notificación , en la mayoria tenes que ir a la carpeta del programa en cuestion por ejemplo en el rhythmbox vas a /usr/share/rhythmbox/icons/hicolor/22x22/status . como administrador y cambias el icono por el que te gusta. en el pidgin seria en /usr/share/pixmaps/pidgin/status y elegis el tamaño deseado y ahi cambias el icono.
ahora para cambiar los iconos del gweather o el applet del tiempo , lo primero que tenes que hacer es ir a esta ruta /usr/share/icons/gnome/22x22/status fijarte bien los iconos del tiempo que aparecen con sus respectivos enlances y copiarles los nombres , una vez que ya tenes los nombres y los iconos que vos queres poner ,y ya que tenes el paquete de mac4lin anda a /home/usuario/.icons/Mac4Lin_Icons_v0.3a/scalable/stock y ahi pegas los iconos que vos queres con los nombres que figuraban en la carpeta de iconos de gnome. sino te llegan a aparecer los iconos de una, saca el applet y volvelo a poner y ahi tendria que andar.
espero que te sirva.
salu2!
[COLOR="DarkOrchid"]
Thenry, mil gracias por tu ayuda, hice lo que me recomendaste pero los íconos no cambian aún. 
Noté que sí lo hacen en la Avant Window Navigator por ejemplo. :S
Será en otro lugar?[/COLOR]

---

### Post by thenry on 2007-12-20
valucha, me equivoque en darte en la ruta del rhythmbox el tamaño , proba cambiando /usr/share/rhythmbox/icons/hicolor y cambiando los demas tamaños , igual me parece que cambiando el de 16x16 tendria que andar, el nombre del archivo a cambiar seria "rhythmbox-notplaying.png". En el pidgin tendria que andar, /usr/share/pixmaps/pidgin/status , yo personalmente ahi cambie el del tamaño 16x16 y me anda.
Para el applet del tiempo a mi me funciono asi, tomemos el ejemplo del icono de un día soleado y despejado. primero agarra el icono que queres suplantar por el sol de los iconos predeterminados de gnome, en este caso se llama "weather-clear.png",ponele ese nombre a tu icono y ponelo en la carpeta /home/usuario/.icons/Mac4Lin_Icons_v0.3a/scalable/ stock, una vez puesto en esa carpeta hacele click derecho y pone "crear un enlace" y pegalo en esa misma carpeta llamandolo "stock_weather-sunny.png". o sea que en la carpeta /home/usuario/.icons/Mac4Lin_Icons_v0.3a/scalable/ stock tiene que estar tu icono y su respectivo enlace con los nombres que te dije anteriormente.
Una vez que te cambio por ejemplo el del dia soleado anda a 
/usr/share/icons/gnome elegi el tamaño y despues la carpeta status y anda fijandote los nombres de todos los iconos del gweather con los nombres de sus respectivos enlaces asi podes ir cambiandolos todos. una cosa importante es el tamaño para el ejemplo que te di yo cambie los de 22x22 y me anda, cualquier cosa cambia tambien los de 16x16 y los otros hasta que te ande . pero cambiandolos asi a mi me andan bien.
salu2!

---

### Post by valucha on 2007-12-20
[COLOR="DarkOrchid"]Mil gracias, me sirvió un montón tu respuesta. Unicamente que los íconos del tiempo los cambie en todos los tamaños pero no se ponen, sino que quedan los viejos. ¿Tenés idea qué puede ser?[/COLOR]

---

### Post by thenry on 2007-12-21
la verdad ni idea por que no se te cambian a mi me anduvo bien como te explique antes, lo único que se me ocurre es que te fijes bien en que los iconos nuevos tengan el mismo tamaño que los que queres cambiar, que te fijes a ver si pusiste bien los nombres y con sus respectivos enlaces,y si no, lo que podes hacer es como administrador cambiar los iconos del  tiempo directamente de gnome, por ejemplo al archivo de día despejado llamado "weather-clear.png" renombralo como "bakweather-clear.png" y pega el tuyo con el nombre "weather-clear.png" asi con todos los demás, para mi en esta ruta /usr/share/icons/gnome/tamaño/status, principalmente serian los de 16x16 22x22 y 24x24, y por ultimo si no llegan a aparece hace en terminal "sudo gtk-update-icon-cache -f /usr/share/icons/gnome" para actualizar la cache de iconos,y saca y volve a poner el applet. eso es todo lo que se me ocurre cualquier cosa si no te llega a funcionar volves a renombrar los icono bak a sus nombres originales.estas son las dos formas que conozco y particularmente a mi me resultaron ambas, te dejo una captura de mi escritorio en el cual al sol amarillo del día soleado lo cambie por un sol negro abajo a la derecha.
[[IMG]http://img212.imageshack.us/img212/2504/pantallazoce3.th.png[/IMG]](http://img212.imageshack.us/my.php?image=pantallazoce3.png)

Si te llegan a interesar unos iconos del clima negros, en este enlace hay unos que estan buenos: [http://www.gnome-look.org/content/show.php/Weather+Replacement+Icons?content=70662](http://www.gnome-look.org/content/show.php/Weather+Replacement+Icons?content=70662)
si cualquier cosa me llego a enterar de algo mas te lo hago saber.
salu2!

---

### Post by valucha on 2007-12-21
[COLOR="DarkOrchid"]Listo, ahora me cambiaron era cuestion de reiniciar varias veces :).

Mil gracias.. ahora lo pongo solved.[/COLOR]

---

### Post by valucha on 2007-12-21
[COLOR="DarkOrchid"]Tengo un uuuultimo problema.
El ícono del rhythmbox no cambia cuando estás reproduciendo, se pone el viejo. ¿Como hago?, en mi theme de iconos está el icono chiquitito y se llama algo de "rhithmbox-on" , todo diría que debiera funcionar pero no es asi :(. Ya no veo más el ícono viejo (ese blanco cuadrado como si fuera un parlante), sino que veo el mismo que me pone para el rhythmbox en el panel.
¿Cómo lo cambio?
Gracias nuevamente.[/COLOR]

---

### Post by paulita78 on 2010-02-03
Hola a todos!Gracias a las indicaciones que leí aquí pude cambiar los iconos.Pero con el de Bluetooth me está siendo imposible¿Teneis alguna idea de como hacerlo?

---

