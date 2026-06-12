---
title: "Salio amarok2 - Guia para instalarlo"
date: 2008-12-10
forum: Software
---

### Post by sajnox on 2008-12-10
Bueno, despues de mucho tiempo salio amarok2, asi que vayan nuestras felicitaciones a los desarrolladores que lo lograron!!

Amarok2!!! Lo quiero! lo quiero! lo quiero! Como lo instalo??

Actualmente tengo instalado Ubuntu Intrepid

1) Editamos el sources.list

```
sudo gedit /etc/apt/sources.list

```
al final del archivo incluimos lo siguiente:

```
#Repositorios Amarok2
deb http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu intrepid main

```

2) Hacemos update de los repositorios

```
sudo apt-get update
```

3) Instalamos el amarok2

```
sudo apt-get install amarok-kde4
```

Listo!!!

No me gusto, como lo saco??

```
sudo apt-get remove amarok-kde4
```

y si queremos amarok de nuevo:

```
sudo apt-get install amarok
```

---

### Post by User21 on 2008-12-10
Pero asi nomas de facil, sajnox ? Caracoles!!!
Y ahora que hago con todos esos libros de programación y GNU/Linux profesional que compré???

(No, leerlos no! )

---

### Post by pol666 on 2008-12-10
yo lo vengo usando desde que es RC. Muy bueno la verdad se zarparon con esto

---

### Post by feche_mza on 2008-12-11
che y que onda vale la pena ponerlo y dejar de lado al otro???
que tiene de nuevo este que no tenga el anterior???
no me contesten con un wiki quiero saber si les gustó, por que y punto , ya se que es desvirtuar pero no es lo mismo lo que diga una pagina web a lo que me digan ustedes

---

### Post by pol666 on 2008-12-11
esta hecho en QT4 
tiene una interfaz renovada
soporta video
ahora Last.fm anda 99% bien
tiene una gestion de caratulas y letras muy buena.

lo unico que no me gusto es que no esta la opcion para ver la pagina de wikipedia :\

---

### Post by Hei Ku on 2008-12-11
Tiene servicios para bajar cosas directamente de Magnatune, la BBC y otros, y un monton de add-ons para radios online. De hecho, dicen que es bastante facil asi que podrian crear uno con las radios de aca.

---

### Post by Hernán-Amaya on 2008-12-11
grande sajnox! ya lo voy a probar!

---

### Post by sajnox on 2008-12-11
> lo unico que no me gusto es que no esta la opcion para ver la pagina de wikipedia :\

Eso lo podes agregar como un applet.

En lo particular, volvi a la version anterior.

Por que?

En primer lugar aclaro que lo uso principalmente para escuchar musica que tengo en mi maquina y no servicios on line que es donde entiendo le metieron muchisimo trabajo.

Ahora si, por que?

 * Yo uso ubuntu por lo que qt4 pierde toda apariencia (o por lo menos costumbre que tengo) de integracion grafica
 * No tengo el boton para borrar los tracks de la playlist en curso y pasarlo a cero
 * No me pregunten porque, pero me da la impresion de que le falta un poquito de horno todavia, eso no quita que lo siga de cerca y vea en que anda, ya que Amarok, IMHO, es por lejos *el* reproductor de audio para Linux, probe con cuanta cosa vi dando vueltas que este basado en GTK y no encontre nada que me parezca decente, lo mejor en GTK me parece que es Exaile y no maneja la coleccion de musica como lo hace Amarok, bueno los desarrolladores mismo dicen que por el solo hecho de estar en qt4 es una beta
 * No ofrece/no encontre la opcion para mostrar bajo varios artistas (odio tener artistas en la coleccion por que solo tienen un tema en un disco homenaje, no puedo evitarlo, lo odio!!)

---

### Post by pol666 on 2008-12-11
> 
Eso lo podes agregar como un applet.

Me aparece informacion del disco, yo digo de la banda.. la biografia y eso

> * No tengo el boton para borrar los tracks de la playlist en curso y pasarlo a cero

ip, fijate abajo del playlist, es un icono de una goma

> 
* No ofrece/no encontre la opcion para mostrar bajo varios artistas (odio tener artistas en la coleccion por que solo tienen un tema en un disco homenaje, no puedo evitarlo, lo odio!!)

Si, tenes razon a mi me molesta bastante

---

### Post by Kabezon on 2008-12-15
Y en Hardy cómo se instala? ._.

---

### Post by sajnox on 2008-12-15
> **Kabezon said:**
> Y en Hardy cómo se instala? ._.

[http://magarto.com/blog/archivo/2008/05/07/amarok-2-en-ubuntu-hardy-heron/](http://magarto.com/blog/archivo/2008/05/07/amarok-2-en-ubuntu-hardy-heron/)

---

### Post by guillermon on 2008-12-15
Hola, estaba leyendo el post; pues he escuchado mucho sobre Amarok, y ahora sobre la nueva versión. Yo tengo Hardy; pero Ubuntu, no Kubuntu: ¿puedo usarlo igual?, pues mi "amplia" capacidad de observación de dice que no es lo mismo gnome que kde...
Aprovecho para saludar... Gracias
Guillermo

---

### Post by sajnox on 2008-12-15
Hola Guillermon,

Poder podes, el tema es que cuando levantas un programa de KDE en Gnome (o a la inversa) el programa para andar tiene que levantar librerias (programas) del KDE y eso hace que el sistema sea mas pesado. Si no estas corto de memoria eso no es un problema, pero si venis medio justo con la ram te puede hacer que el uso del programa sea un poco pesado.

El programa en si funciona perfecto en Gnome, desde ahi es que lo uso

---

### Post by lean1984 on 2008-12-15
Buenas gente como va, no suelo postear por aca en general me voy al foro gallego lo confieso XD jaja pero bueno
Hace unas semanas me baje el Amarok2 RC, ya habia probado las beta antes. En fin despues de tenerlo un tiempo instalado me parece que me vuelvo al anterior y comento por que:

a) Por lo que leo aca parece que salió la versión definitiva, voy a ver si la pruebo, pero por lo pronto con la version RC no se que pasa que no me levanta la coleccion, se queda en scanning colection y ahi muere, asi que tengo que abrir los temas "a mano" desde nautilus. Ok, es un bug y en algun momento de la vida se solucionará asi que no cuenta como punto negativo, pero me rompe las p...

b) Yo escucho mas que nada música electronica, es decir que suelo escuchar unos mp3 que duran unas 2 horas donde los temas estan mezclados unos atras de otros en un mismo archivo. En la versión anterior el Amarok tiene algo genial: si junto con tu mp3 tenes un archivo .cue con la informacion sobre los tracks y con el mismo nombre de archivo que el mp3 el programa lo levanta automaticamente y en el menu de contexto se muestran todos los temas y podes ir a cualquiera como si el mp3 estuviera trackeado. Asi si un día querés escuchar un tema en particular del set podes hacerlo sin tener que mutilarlo cortándolo en pedacitos. En Amarok2 no está mas.

c) Suelo escuchar musica por internet desde di.fm, Hasta ahora con Amarok2 no lo pude hacer, se cuelga y no empieza nunca a reproducir. Supongo que será algún tipo de bug pero no se, a lo mejor ya no se puede hacer eso tampoco.

d) En la versión anterior de Amarok la gente pedia que no solo la solapa context sino toda la interfaz fuera "skineable". La respuesta de los muchachos en Amarok2: no mas skins. Esto en realidad es lo de menos, pero ya que no uso KDE sino Gnome por lo menos me gustaria personalizarlo un poco para que se integre mas.

e) en AMSN ya no se muestra lo que estoy escuchando. Trate de retocar el plugin Music pero no tuve exito :(

Bueno como ven son pequeños detalles (salvo el grave problema de la colección). Pero sin embargo muchos de esos pequeños detalles son los que me hacían preferir a Amarok frente a otros reproductores y ahora no están.
Me parece que como dicen por ahi, quisieron reinventar la rueda y les salió mal. No entiendo porque lo escribieron de nuevo desde cero, lo hubiesen mejorado un poco, agregado algunas funciones y sobre todo hacerlo mas agradable a la vista y listo.
En fin me quedo con la version anterior hasta que se solucionen los bugs, se agreguen las funciones que le faltan (ya sea con plugins o lo ke sea) y si esto no pasa me buscaré algún otro reproductor que hay muchos y muy buenos.

Saludos! ):P

---

### Post by Applelnx on 2009-01-07
Hola primero que todo gracias, pude instalar el Amarok 2. Pero tengo un problema, cuando lo ejecuto me salta el siguiente error:

phonon
The audio playback device HDA ATI SB (ALC883 Analog) does not work. Falling Back to default.

Cuando trato de reproducir algo no seuna ni empeiza a reproducir :(
A alguien le paso algo similar?

---

### Post by QrK0 on 2009-01-23
Hola, la verdad es que me he llevado un pequeño chasco con la versión 2. Vengo utilizando Amarok desde antes de pasarme a Gnome, eso fue con la Gutsy ya que antes tiraba de Fedoras y otras.
Como decís por aquí, yo tampoco he encontrado reproductor de música mejor que el anterior Amarok.

En fin, cuando lo he actualizado a la 2, me ha importado casi todo el historial que tenía en el Mysql renombrando, antes, la antigua bbdd (lo cual es una gran gentileza). No ha recuperado la información de las puntuaciones ni de las estadísticas, pero sí la información de las carátulas.

Después, la interface de usuario es muy poco personalizable y tb poco amigable, para mi gusto. Todavía no he visto la manera de descargar las letras, eso que tiene un plugin instalado.

Tampoco veo que se pueda integrar con el moodbar. El gestor de carátulas se come un montón más de cpu que antes.

Y la lista de intérpretes, en fin, qué pena de versión. Y mira que era prometedora.

Creo que me volveré a la versión anterior.

Hala, salut!

---

### Post by QrK0 on 2009-01-23
Pues va a ser que no habrá moodbar:

[http://amarok.kde.org/forum/index.php?topic=15672.0;prev_next=prev]("http://amarok.kde.org/forum/index.php?topic=15672.0;prev_next=prev")

[http://marc2.theaimsgroup.com/?l=amarok&m=121931912717821&w=2]("http://marc2.theaimsgroup.com/?l=amarok&m=121931912717821&w=2")

---

