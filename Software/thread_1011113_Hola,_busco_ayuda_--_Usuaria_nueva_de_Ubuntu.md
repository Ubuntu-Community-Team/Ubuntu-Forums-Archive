---
title: "Hola, busco ayuda -- Usuaria nueva de Ubuntu"
date: 2008-12-14
forum: Software
---

### Post by bramalia on 2008-12-14
Hola a tod@s, no estoy segura de que este sea el lugar correcto para satisfacer mis dudas, pero veo que son gente amable y que en tal caso me indicaran dónde encontrar respuestas.
Por empezar, aclaro que no se nada de software, hardware ni del mundo cibernético en general. Soy fotógrafa y uso photoshop y otros programitas relacionados con la fotografía, pero ahí se termina mi destreza. Hasta ahora usé windows xp, pero resulta que compré una nueva compu y vino con ubuntu. Después de explorar un poco  el sistema (obviamente de manera superficial, pues no me queda otra ;), me pregunto si será muy complicado para alguien que lo ignora todo acerca de la cibernética, manejarse con él. Funcionan todos los programas que pueda necesitar de la misma manera con este sistema? puedo instalar el PS sin problema? Quizás mis preguntas sean muy básicas, pero, como ya dije, soy una lega en estas materias. 

Muchísimas gracias por toda posible respuesta!
Saludos.

---

### Post by smo0th on 2008-12-14
hola bramalia y bienvenida al mundo de ubuntu =)

el sistema en si es mas facil de utilizar, seguro y eficiente que sus contrapartes de windows, llevo mas de 2 anios usandolo y no veo manera de regresar al viejo y viciado mundo de las pantallas azules y reinicios en cada estornudo

sobre PS yo mismo lo tengo instalado en mi ubuntu, te recomiendo bajar wine-doors de aqui: [http://www.wine-doors.org/releases/wine-doors_0.1.2_all.deb](http://www.wine-doors.org/releases/wine-doors_0.1.2_all.deb) 

wine es una capa que usa linux para la interpretacion de comandos de windows, actualmente esta tan avanzada que se pueden jugar juegos de windows con aceleracion 3D bajo linux y con mejor rendimiento en muchos casos.

volviendo al tema, bajas e instalas wine-doors usando la terminal, antes que nada abres una terminal en Applications>Accesories>Terminal y tecleas 

sudo apt-get install wine

das tu password de usuario y esto te instalara el sistema base de wine, enseguida vas al folder donde descargaste wine-doors y lo instalas mediante:

sudo dpkg -i wine-doors_0.1.2_all.deb

para ir al directorio donde descargaste el .deb usas el comando cd:

cd /ruta/directorio

para desplegar tu actual directorio usas simplemente pwd

wine-doors es un manejador de paquetes que te facilita la vida al instalar paqueterias basadas en windows, una vez que hayas ejecutado el instalador y seguido las instrucciones ejecutas wine-doors buscandolo bajo el menu Applications, una vez que estes dentro de wine-doors buscas el PS, lo seleccionas para instalacion y le das aplicar.

Lo unico que tendras que hacer una vez instalado el PS para que te funcione bien es copiar todas tus fonts de tu directorio de windows al directorio de wine en linux.

salu2, intenta lo de arriba y si necesitas mas ayuda por aca andaremos ;)

---

### Post by c4d0rn4 on 2008-12-14
> **bramalia said:**
> Hola a tod@s, no estoy segura de que este sea el lugar correcto para satisfacer mis dudas, pero veo que son gente amable y que en tal caso me indicaran dónde encontrar respuestas.
Por empezar, aclaro que no se nada de software, hardware ni del mundo cibernético en general. Soy fotógrafa y uso photoshop y otros programitas relacionados con la fotografía, pero ahí se termina mi destreza. Hasta ahora usé windows xp, pero resulta que compré una nueva compu y vino con ubuntu. Después de explorar un poco  el sistema (obviamente de manera superficial, pues no me queda otra ;), me pregunto si será muy complicado para alguien que lo ignora todo acerca de la cibernética, manejarse con él. Funcionan todos los programas que pueda necesitar de la misma manera con este sistema? puedo instalar el PS sin problema? Quizás mis preguntas sean muy básicas, pero, como ya dije, soy una lega en estas materias. 

Muchísimas gracias por toda posible respuesta!
Saludos.

Con respecto a lo que es diseño, linux le falta madurar un poquito, o tal vez, adobe y otras compañías les falta hacer un esfuercito más y hacer sus programas multiplataformas.

Photoshop puede usarse en ubuntu. [http://appdb.winehq.org/objectManager.php?sClass=application&iId=17](http://appdb.winehq.org/objectManager.php?sClass=application&iId=17)
fíjate cual versión usas. Lo bien o lo mal que corra una aplicacion de windows en wine está dado por "medallas", platinum (no da problema alguno), gold (puede haber que tocar una pavada para que ande como en windows), silver (anda...), bronze (la cosa es media color de hormiga pero anda) y garbage (no funca ni aunque le pongas una vela a san expedito, o el papa exorcice el binario).

En el caso del photoshop te diría que con un poco de paciencia vas a poder trabajar. En mi caso yo uso Paint shop pro y no corro con la misma suerte [http://appdb.winehq.org/objectManager.php?sClass=application&iId=76](http://appdb.winehq.org/objectManager.php?sClass=application&iId=76) la mayoría es basura.

siempre que necesites usar una aplicación de windows en linux fíjate acá antes, te va dar una buena idea de que hacer.
[http://appdb.winehq.org/](http://appdb.winehq.org/)

Salvo aplicaciones de diseño, y algunas pocas otras, no es necesario usar aplicaciones de windows dado que en linux hay aplicaciones nativas que hacen las cosas muy bien.

---

### Post by faktorqm on 2008-12-14
Hola y bienvenida al foro. Ubuntu es el gnu/Linux mas facil de usar, y no necesitas <saber> si sos una usuaria "normal". Podes llegar a tener problemas (al igual que en win) y los podes poner aca que si lo sabemos y tenemos tiempo te vamos a contestar de muy buen grado.
A veces, si queres hacer cosas muy avanzadas si vas a necesitar saber, pero si estas en la parte de diseño, despreocupate. Hablando de diseño, tenes el GIMP (en aplicaciones -> graficos -> editor de imagenes GIMP) que vendria a cumplir la misma funcion del PS. Algunos dicen que una vez que se acostumbran al GIMP no quieren volver al PS, por el manejo que tiene el programa. Yo no puedo hablar por que no soy usuario grafico :P pero podes tener los dos al mismo tiempo y listo con las guias que te pasaron los compañeros (suena re sindicalista no? jajaja)

Despues para chatear tenes por defecto el pidgin, y te podes instalar el emesene o amsn desde aplicaciones -> añadir y quitar o desde sistema -> administracion -> gestor de paquetes Synaptic. (opcion buscar)

Y nada, esperamos tus preguntas en particular. Salu2!!!

---

### Post by bramalia on 2008-12-14
Muchísimas gracias por sus respuestas!
@ c4d0rn4, me fijé en el sitio que me pasaste (de mucha ayuda!) y PS3, que es el que yo tengo, es silver, con lo cual me desentusiasmo un poco de usar el sistema. De hecho, ya había empezado a instalar el wine para hacer la prueba y hay mil cosas que se me complican, imagínense que no sé qué es el comando cd, ni hablar de copiar fonts de directorio a directorio (?!). Créanme que me encantaría poder usar el ubuntu, pero no tengo realmente tiempo para encontrarme con muchos problemas para resolver. Me parece que me tendré que conformar con malo conocido :(

Gracias de nuevo por el tiempo que les hice perder. Quizás vuelva a acercarme en el futuro, si es que aprendo un poco más a manejarme en este ámbito.

Saludos.

---

### Post by andy_91 on 2008-12-14
para instalar photoshop una vez instalado wine ejecutas el programa y se te instala.

yo para imágenes usaba el psp 7.4 y me andaba de maravilla, también como ya dijeron esta el GIMP, te recomiendo que al principio para instalar programas uses añadir y quitar... del menú aplicaciones

También te recomiendo que hagas esto:

Añadir esta web a tus repositorios y marca todos los que estén destildados (menos los que digan CD)

> deb [http://ubuntu.org.ua/](http://ubuntu.org.ua/) getdeb/

Para agregar la web en Ubuntu:

Sistema>Administración>Orígenes del software

allí vas a la pestaña software de terceros, tildas los destildados y le das al boton añadir

te aparecerá una ventana donde ingresas la web y luego aprietas el botón añadir origen

por ultimo cierras la ventana y actualizas el repositorio (te saldrá una ventana a la que deberás tildarle recargar)

ahí vas a tener mas programas disponibles para instalar o versiones mas nuevas de los que ya tenias disponibles

---

### Post by smo0th on 2008-12-14
******


=/

---

### Post by Hei Ku on 2008-12-14
Si necesitas sí o sí utilizar el Photoshop por tu trabajo, entonces tenes la posibilidad de instalarlo en una maquina virtual. Pero en tu caso, yo lo evaluaría bien antes de hacer la migracion.

---

### Post by sajnox on 2008-12-14
Hola,

Que la maquina haya venido con ubuntu no significa que si o si tengas que usarlo, obvio que los que estamos aca creemos que Ubuntu es superior a Windows en muchos aspectos. Mi consejo es que si vas a usar ubuntu es por que te gusta y no por que crees que es tu unica opcion. 

Respecto al photoshop, no lo conozco demasiado ya que no lo uso pero venia siendo posible de ser instalado en ubuntu con wine como te comentaron antes.

Tambien podes instalar windows y ubuntu en tu maquina y elegir cual de los dos sitemas usar en el arranque.

Desde ya que cualquier duda que tengas con ubuntu es bienvenida y con gusto lo aclaramos.

Para mas datos contanos que notebook compraste para que tengamos una idea de las posibilidades que el equipo tiene.

Si tenes instalado ubuntu fijate que tenes Gimp que es un editor de graficos como lo es photoshop, a muchos les sirve y les parece muy bueno y otros dicen que no es tan potente como el photoshop, cuestion de gustos u necesidades

---

### Post by bramalia on 2008-12-14
Gracias de nuevo por tada la ayuda. Se que no tengo obligación de usar ubuntu sajnox, sólo que me pareció muy agradable el lay out (no se cómo se dira :P) y me gusta la idea de que sea libre, pero realmente se me haría muy difícil con las exigencias de tiempo de mi trabajo, lidiar con algo nuevo de lo que no conozco nada. No se me ocurriría cambiar el PS por otro programa, pues me costó bastante conocerlo y usarlo con cierto nivel, y además es el softw más extendido en mi profesión con lo cual hay mucha ayuda, tutoriales etc. Por lo que me contó c4d0rn4, el PS3, que es el que tengo yo, no funciona bien con ubuntu sin una preparación previa.
Gracias hei ku por tu input, me sirve, pero además quería decirte que leí el post de smooth que moderaste y me parece, creo, no estoy segura, pero creo que no fue con intención ofensiva, al menos yo no me lo tomé así.
La verdad que todas las ganas de ayudar que hay acá, me hacen lamentar más no tener la capacidad para iniciarme en este sistema.

Saludos.

---

### Post by andy_91 on 2008-12-15
hay un tutorial en la web de como instalar photoshop 3 en Ubuntu, si no vi mal el otro día

[http://tuxpepino.wordpress.com/2007/05/28/instalar-dreamweaver-y-photoshop-en-ubuntu/](http://tuxpepino.wordpress.com/2007/05/28/instalar-dreamweaver-y-photoshop-en-ubuntu/)

[http://www.lagg3r.com.ar/instalar-dreamweaver-cs3-en-ubuntu-804/](http://www.lagg3r.com.ar/instalar-dreamweaver-cs3-en-ubuntu-804/)

[http://www.ubuntu-ve.org/node/2128](http://www.ubuntu-ve.org/node/2128)

[http://foros.softonic.com/showthread.phtml?t=74028](http://foros.softonic.com/showthread.phtml?t=74028) (Disculpen el enlace de otro foro)

---

