---
title: "[SOLVED] [rhythmbox] Tags de canciones rebeldes"
date: 2008-07-22
forum: Software
---

### Post by valucha on 2008-07-22
[COLOR="DarkOrchid"]Hola!...
Hace un tiempo que ando renegando con los tags de 2 cd's que me prestaron. Uno es el último de Arbol, vino sin ningún tag (y me olvidé de agregarlo con el soundjuicer) y el Rhythmbox me lo reconoce como Artista Desconocido y las canciones son Pistas 1, 2 etc... Lo cambié desde el Rhythmbox, se ordenan, después el Rhythmbox analiza nuevamente mi carpeta y me los vuelve a nombrar como se le canta.
Por otro lado un compilado de Reggaeton ( :D ) está ordenado por artista (encima todo en minúsculas, horrible) y yo lo quiero meter en Reggaeton, comosi ese fuese su artista. Lo ordeno, se mete, analiza y se desordena todo de nuevo.

Probé con el EasyTAG que es con el que ordeno todas las canciones, y no hay caso, las graba, aparecen ordenadas, luego el Rhythmbox anaiza mi carpeta y me las desordena.


Ambos están en formato .mp3


Y he hecho esto millones de veces y nunca me pasó.

Espero ver sus respuestas...

GRacias desde ya[/COLOR]

---

### Post by niko_3100 on 2008-07-22
Imposible el easyTag es muy bueno, fijate si guardas los datos, porque puede que no los estes guardando, a mi me resulto muy bueno el easytag pero tenia ese problema que no me guardaba automatico tenia que hacerlo yo.

---

### Post by valucha on 2008-07-24
> **niko_3100 said:**
> Imposible el easyTag es muy bueno, fijate si guardas los datos, porque puede que no los estes guardando, a mi me resulto muy bueno el easytag pero tenia ese problema que no me guardaba automatico tenia que hacerlo yo.

[COLOR="DarkOrchid"]
Lo guardo!... siempre lo hago de la misma forma, y hay canciones que se cambian y otras que no :S[/COLOR]

---

### Post by User21 on 2008-07-25
Se puede escribir en esos archivos? Tenes permisos de modificacion? Están marcados como SOLO LECTURA?
Antes que nada. Asumimos que estás haciendo bien las cosas y estás guardando todos los cambios de TAGS en esos MP3. 
Pusiste además los TRACKS ? 01, 02, 03 ?
Otra cosa: en los compilados, al ser de varios Artistas, los players pueden reorganizar la música basados en ALBUM o en ARTISTAS. Atenta a eso, si es que te cambia el orden. 

01 Pablito           NombreCancion            ALBUM01
02 Carlitos         NombreCancion2          ALBUM01
03 Raul              NombreCancion3          ALBUM01

Si ves, ahi, esta ordenado por ALBUM, pero los artistas son diferentes. 

02 Carlitos              NombreCancion2            ALBUM01
01 Pablito               NombreCancion              ALBUM01
03 Raul                  NombreCancion3            ALBUM01

Si ordena alfabeticamente por ARTISTAS, cambia la cosa... 

Y si hace diferencias en los contenidos de cada ARTISTA, te va a tomar que RAUL tiene un album llamado "ALBUM01" con 1 solo tema "NombreCancion3". De la misma forma, a los otros 2 artistas. 

Y aun debes contemplar la posibilidad de que algunos MP3 tengan una, dos o tres TAGS, que segun eso, el player rellena las demas con DESCONOCIDO o VACIO, afectando el orden en que se muestran! UN QUILOMBO :P 

Esas cosas son ineherentes a cada player, o como se ordenan las columnas con que estas visualizando la informacion... 

Se entendió algo ??? :P

---

### Post by valucha on 2008-08-04
> **User21 said:**
> Se puede escribir en esos archivos? Tenes permisos de modificacion? Están marcados como SOLO LECTURA?
Antes que nada. Asumimos que estás haciendo bien las cosas y estás guardando todos los cambios de TAGS en esos MP3. 
Pusiste además los TRACKS ? 01, 02, 03 ?
Otra cosa: en los compilados, al ser de varios Artistas, los players pueden reorganizar la música basados en ALBUM o en ARTISTAS. Atenta a eso, si es que te cambia el orden. 

01 Pablito           NombreCancion            ALBUM01
02 Carlitos         NombreCancion2          ALBUM01
03 Raul              NombreCancion3          ALBUM01

Si ves, ahi, esta ordenado por ALBUM, pero los artistas son diferentes. 

02 Carlitos              NombreCancion2            ALBUM01
01 Pablito               NombreCancion              ALBUM01
03 Raul                  NombreCancion3            ALBUM01

Si ordena alfabeticamente por ARTISTAS, cambia la cosa... 

Y si hace diferencias en los contenidos de cada ARTISTA, te va a tomar que RAUL tiene un album llamado "ALBUM01" con 1 solo tema "NombreCancion3". De la misma forma, a los otros 2 artistas. 

Y aun debes contemplar la posibilidad de que algunos MP3 tengan una, dos o tres TAGS, que segun eso, el player rellena las demas con DESCONOCIDO o VACIO, afectando el orden en que se muestran! UN QUILOMBO :P 

Esas cosas son ineherentes a cada player, o como se ordenan las columnas con que estas visualizando la informacion... 

Se entendió algo ??? :P
[COLOR="DarkOrchid"]
Los permisos de escritura los tiene para todos los grupos: leer y escribir
Estoy guardando los tags en esos MP3
No puse los tracks

NO me importa el orden en el que se muestren dentro de el compilado, solo quiero que queden dentro de un solo artista que para mi es Reggaeton o Electronica o Ochentosos... ¿Entienden?... Porque en realidad el rhythmbox si me los ordena bien, me los discrimina por artista, pero yo no quiero eso porque realmente es un bardo buscarlos en el aparatito de mp3 cuando en realdiad quiero poner la carpeta "electronica" y escuchar toda la música de una.

Los de Reggaeton los borré porque eran una ca**da de todos modos... pero me quedó el cd de Arbol, Hormigas, me lo ordena por track y por album pero el artista no lo recoonce, me lo pone como desconocido.
Le cambié los permisos y l0o arreglecon el easytag y se ordenan, y luego el rhythmbox anañiza mi carpeta y los vuelve a poner en artista desconocido.

LO cambio con el rhythmbox y tampoco hay caso...

[/COLOR]

---

### Post by faktorqm on 2008-08-05
Al parecer no sos la unica que tuvo el problema. 

blog con la solucion (julio de 2008 ): [http://www.savvyadmin.com/rhythmbox-id3-tag-issues/](http://www.savvyadmin.com/rhythmbox-id3-tag-issues/)

bug en launchpad: [https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/8839](https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/8839)

Salu2! :KS

---

### Post by valucha on 2008-08-05
[COLOR="DarkOrchid"]Ah! era un bug!!:..


Miiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiil gracias  Fak...

Solved :)[/COLOR]

---

