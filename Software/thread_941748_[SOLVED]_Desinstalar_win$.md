---
title: "[SOLVED] Desinstalar win$"
date: 2008-10-08
forum: Software
---

### Post by ramiro_md on 2008-10-08
Gente, hoy prendí mi computadora y lamentablemente tuve que bootear en win$, debido a que tenía que hacer unos trabajillos. Al iniciar me lleve la grata sorpresa de que mi particion ntfs "datos", no era leida por el sistema.
Lo primero que pense fue, a la mierrrrcoles con todos mis datos :(, entonces pare la pelota y me fije si ubuntu lo reconnocia, cosa que si sucedio.
Entonces volvi a win$ a ver si ahora si reconocia la particion...y nada...hice un mentiroso scandisk y volvi a reiniciar y nada. 
Una vez hecho todo esto, me serené y dije, hay que terminar de erradicar a window$s de mi pc.
He ahi mi duda, cómo lo desinstalo ??...alguien:) podría darme una idea ??:). Un saludo.

---

### Post by pol666 on 2008-10-08
abri el gparted, desmonta la particion donde esta Tu windows y tan simple como borrarla, despues fijate si extendes alguna para ganar el espacio donde estaba.

---

### Post by ramiro_md on 2008-10-08
GRacias maan, hice algo parecido para no toquetear tanto las particiones que tantos problemas me daaan.
Metí el Livecd, formatee la partición de windows en ext3 e instale ubuntu ahi. 
La vieja partición ubuntera, va a formar parte de la partición de "datos" en cueanto termine de migrar las configs.
Un saludo. Gracias.

---

### Post by pol666 on 2008-10-08
Mira te dejo una organizacion de mi disco principal.
[IMG]http://img261.imageshack.us/img261/1654/pantallazodevsdagpartedyl9.png[/IMG]

Tengo 50gb para windows, 5 y 5 para Kubuntu y Debian, y el resto de /home, hay van los archivos de mas uso y las configuraciones, tal como vos tenes tu home pero yo lña puse en otra particion, con eso tenes la ventaja de cuando reinstalas conservas las configuraciones.
En el segundo disco que todavia no organize, guardo los datos pesados, y backups, tambien tengo partciones para probar SO, pero no lo puedo hacer bootear asi que por ahora lo deje para almacenar.

Edito: ahi figura la /home como /media/datos por que es una captura de Debian, y la home es de Kubuntu, las config de debian estan en su misma particion.  Pero con acceso directos comparto las carpetas de forma ordenada.

---

### Post by ramiro_md on 2008-10-08
GRacias x mostarme como tenias organizada tu vida xD. Le dejaste mucho a win$ :S to apenas le deje 10 gb no sé por qué todavía...pero nunca se sabe.
Un saludo loco.Cuidate querete jajaja.

---

### Post by sartrejp on 2008-10-08
10 gigas para windows? 
Yo le dejé 50 también por una simple razón...
Juegos
Es para lo único que me sirve. Mi novia lo usa para otras cosas, pero yo no, y si le doy poco espacio después no sirve para nada, si como 4 o 5 gigas se van en la instalación y el pagefile.sys (o algo así)

---

### Post by valucha on 2008-10-09
> **pol666 said:**
> Mira te dejo una organizacion de mi disco principal.

Tengo 50gb para windows, 5 y 5 para Kubuntu y Debian, y el resto de /home, hay van los archivos de mas uso y las configuraciones, tal como vos tenes tu home pero yo lña puse en otra particion, con eso tenes la ventaja de cuando reinstalas conservas las configuraciones.
En el segundo disco que todavia no organize, guardo los datos pesados, y backups, tambien tengo partciones para probar SO, pero no lo puedo hacer bootear asi que por ahora lo deje para almacenar.

Edito: ahi figura la /home como /media/datos por que es una captura de Debian, y la home es de Kubuntu, las config de debian estan en su misma particion.  Pero con acceso directos comparto las carpetas de forma ordenada.


[COLOR="DarkOrchid"]
Una pregu, qué es eso de tener "extended" y adentro otras particiones?... para qué sirve?
Yo lo tengo organizado parecido a vos pero no lo tengo dentro de un extended. mirá mirá! 
[/COLOR]

---

### Post by faktorqm on 2008-10-10
Las particiones extendidas se crearon por que existia una limitacion fisica de los discos y solo podias tener 4 particiones primarias por disco. La historia en criollo: imaginate que tenes una hoja con 4 renglones, pero necesitas escribir 6 cosas, entonces no podes. Lo que invento m$, es un tipo de particion muy peculiar, que se paso a llamar extendida. 
Una particion extendida es una particion primaria (o sea, te ocupa un lugar de los 4 disponibles) y sólo podés tener una por disco, y no la podes formatear, solo podes crearle particiones logicas adentro.
Siguiendo con el ejemplo anterior, imaginate que escribis 3 renglones, pero en el ultimo le pones una flecha a la hoja de atras, en la de atras escribis los dos que te faltan, y listo.
Las particiones logicas son iguales que las primarias pero estan adentro de la extendida, y eso técnicamente no es muy bueno que digamos, por que por ejemplo si tenes un problema en el sistema de archivos de alguna de las particiones logicas, muchas veces te ves obligado a borrar la extendida con todas las logicas adentro para reparar el error. En servidores lo que se hace, es poner todas las particiones que van a ser solo lectura en las logicas (/usr/bin por ejemplo) y asi se reducen los riesgos. (en realidad nunca hay drama con gnu/linux, a menos que se te rompa fisicamente un sector del disco).
Para mas informacion, [http://es.wikipedia.org/wiki/Partición_de_disco](http://es.wikipedia.org/wiki/Partición_de_disco)
Salu2!!

---

### Post by ramiro_md on 2008-10-10
Vecino jejeje por otra de las razones por la cual le deje poco espacio es para no poner muchos juegos (asi me pongo mas las pilas con el estudio :(). Imaginate si tengo 50 gigas me instalo todo y me re paj**. En cambio con 10 gigas estoy mas limitado :P y para poner muchas cosas tendria que modificar la particion y me da mas pereza jajaja.
Faktorqm me sorprende lo facil que explicas las cosas. Un maestro al verdad.
Un saludo gente.

---

