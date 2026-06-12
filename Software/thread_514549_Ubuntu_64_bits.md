---
title: "Ubuntu 64 bits"
date: 2007-07-31
forum: Software
---

### Post by Mataca on 2007-07-31
Hola gente 

Hace poco instale ubuntu anda bien, es muy estable (excepto con beryl que a veces se ****, pero nada serio) pero tengo una pregunta:

tengo un AMD64+ por lo cual tengo la version de 64bits, pero hay cosas que no me funcionan bien, es mejor tener el ubuntu de 32 bits? quiza sea por que todavia no hay mucho para esta estructura, no se... alguna opinion???

Por ejemplo no puedo instalar el wine, y segui todos los datos de la pag oficial, pero hay una dependencia que no funka.... ni tampoco el awn

Ahh y otra cosa, como hago para ver videos en YOUTUBE??? instale el gnash y no veo videitos :(

- Gracias a la gente del foto se me hizo facil el cambio =) encontre programas de diseno muy buenos!!!

Pd. no se poner la enie :P:lolflag:

---

### Post by jajajavi on 2007-07-31
Te cuento que para mí que soy neófito en GNU/Linux los 64 bits fueron todo un dolor de 00's, con respecto a los videitos flash recomiendo el **Swiftfox** que es un Firefox optimizado para cada micro en [http://getswiftfox.com/debian.htm](http://getswiftfox.com/debian.htm) te podés bajar el .deb para amd64 y luego instalar el plugin de flash que sólo corre en 32bits.
El Wine sigue siendo una asignatura pendiente, aunque temporariamente pude hacer correr programas como Photoshop CS y Quarkxpress 5.0 con el Crossover Office [http://www.codeweavers.com/](http://www.codeweavers.com/) que es un programa comercial basado en Wine. El [Inkscape]("http://inkscape.org/") es un gran programa de diseño y el Gimp tiene lo suyo. En cuando a la Ñ fijate en Distribuciones en Preferencias > Teclado

---

### Post by juanman on 2007-08-01
Soy usuario de Kubuntu 7.04 64b. Al wine, al swiftfox de 32 bits con los plug ins de flash y demas lo instale con automatix. Creo q es lo mas facil aunq muchos no lo recomiendan. Yo si, solo asegurate de borrar (o comentar) los repositorios q te agrega en el sources.list para evitar problemas de estabilidad y actualizaciones de versiones... En realidad, yo esto de comentar no lo hice, pero lo hare cuando actualice mi version de kubuntu...

---

### Post by faktorqm on 2007-08-01
Mi consejo es que cambies a 32 bits antes de romperte la cabeza. Yo en el trabajo tengo 64 bits y en casa 32, en casa estoy de mil maravillas, y en el trabajo es un dolor de cabeza tras otro. Yo lo del flash no lo pude solucionar, aun siguiendo la guia que aparece en ubuntu-ar.
El amsn no te lo actualiza, lo tuve que compilar a mano, y creeme, no es apto para cardiacos intentarlo. 
Cuando quise cambiar el teclado, lo unico que consegui fue generar un error en el XKB que jamas volvio a funcionar, y me quede sin escribir las eñes. (ahora toy en casa xD) ponga el teclado como lo ponga, no funciona.
El gestor de actualizaciones, en 32 me botonea al toque si hay actualizaciones, en 64 hasta que no le doy "apt-get update" no me dice nada.
Consejo, pasate a 32 antes de volverte mono, por que yo le puse tantas ganas al de 64, que ahora me da "cosa" sacarlo y sigo sin ver flash............ 
Capaz jajajavi te puede ayudar en todo y la mia solo fue una muy muy muy mala experiencia, no se, por eso es un consejo, tomalo o dejalo. salu2!!!!!!!

---

### Post by Mataca on 2007-08-01
Gracias gente!

Les comento, el amsn lo instalé joya, para cosas de diseño hace unas semanas que puse el ubuntu studio y anda de 10, es muy fácil de usar yo lo recomiendo! edito video, audio, y de gráfica.

Hay miles de juegos que se me re complica poner con el de 64 bits (me siento en la época de la commodore) :lolflag:

Quiza instale el de 32bit, depaso me vendria bien, porque hice un bardo jejeje no entendia nada  de ubuntu y me mande cada verdura...

voy a ver

---

### Post by rojojuan on 2007-08-01
Desinstalé 64 y le puse 32 ando todo bien. Cuando mejore 64 lo vuelvo a instalar, mientras tanto 0 drama!

---

### Post by facundocorradini on 2007-08-01
Definitivamente si no tenés mucha experiencia en linux te recomiendo que instalés la versión de 32bits.

Si bien soy fan absoluto de los 64bits, actualmente es bastante complicado hacer andar todo en este tipo de sistemas. (y los usuarios de 64 tenemos sueños donde  bombardeamos a macromedia ... )

Y la verdad es que no hay taaaanta diferencia de velocidad, al menos por el momento. Cuando las aplicaciones comienzen a aprovechar realmente los 64, ahí veremos un gran salto.

---

### Post by sdm_cacto on 2007-08-01
> **facundocorradini said:**
> Definitivamente si no tenés mucha experiencia en linux te recomiendo que instalés la versión de 32bits.

Si bien soy fan absoluto de los 64bits, actualmente es bastante complicado hacer andar todo en este tipo de sistemas. (y los usuarios de 64 tenemos sueños donde  bombardeamos a macromedia ... )

Y la verdad es que no hay taaaanta diferencia de velocidad, al menos por el momento. Cuando las aplicaciones comienzen a aprovechar realmente los 64, ahí veremos un gran salto.

Es que no es un tema de velocidad, la difrencia es q la arquitectura x64 soporta 4gb de RAM para arriba, osea q vamos a tener que cambiarnos cuando tengamos esa cantidad de RAM, mientras tanto la velocidad es la misma, pero la compatibilidad es mucho peor (por ahora).

---

### Post by Mataca on 2007-08-01
Gracias por la data gente, seguramente me paso a 32bits, porque encima que soy nuevo en esto, estas cosas q no son compatibles me matan.

---

### Post by facundocorradini on 2007-08-02
> **sdm_cacto said:**
> Es que no es un tema de velocidad, la difrencia es q la arquitectura x64 soporta 4gb de RAM para arriba, osea q vamos a tener que cambiarnos cuando tengamos esa cantidad de RAM, mientras tanto la velocidad es la misma, pero la compatibilidad es mucho peor (por ahora).

En realidad, lo que soporta es **direccionamiento** de +4gb, por lo que el cambio obligatorio vendrá cuando necesitemos usar más de 4gb de ram simultaneamente (cosa que a mí me parece un disparate).

Pero creeme que de momento he obtenido mucho mejores tiempos en tares "pesadas" en ubuntu 64 que en 32 (con el mismo equipo)

---

### Post by facundocorradini on 2007-08-02
Off-Topic: como es el sitio para crear esos pingüinitos?

---

### Post by marianom on 2007-08-02
Ya están hechos. Te bajas uno y listo.
Buscá "tux" en el buscador de este subforo, hace algunos cuantos meses yo pregunté eso y alguien me respondió.

---

### Post by marianom on 2007-08-02
[Cá ta]("http://ubuntuforums.org/showthread.php?t=332870")

---

### Post by Mataca on 2007-08-03
Cheee me desvirtuaron el post!! jajajaja
muy buenos los tux

---

### Post by sebas.rhcp on 2007-08-04
Yo tengo kubuntu 64 bits y tengo flash con swiftfox use un script del foro de 64bits, agregue los repositorios de wine y tengo wine 64bits, nada complicado

---

### Post by facundocorradini on 2007-08-05
Hola Seba.  Por favor, si sabés cual toturial es, pasamelo... ya que probé varios y no he conseguido hacer andar bien el flash.   instalé el swiftfox mediante automatix, pero el flash me anda con las cuestiones mas "basicas", y no me permite ver videos broadcast (lo mas interesante del flash...)

gracias por adelantado.

---

### Post by spg76 on 2007-08-05
Facundo, en el sitio de ubuntu-ar hay un tutorial sobre eso en [http://ubuntu-ar.org/soporte/comos/flash64](http://ubuntu-ar.org/soporte/comos/flash64)
Espero que te sirva.

---

### Post by matog on 2007-08-05
Yo tengo la versión de Feisty de 64 bits y no tuve muchos problemas. Instale el flash, el wine, y todo corre de mil maravillas.
Aunque al principio fue frustrante...pero ahora todo anda bien, y cuando instalo de cero (alguna vez lo hice) no me lleva mas de 15 minutos instalar flash y el wine y alguna otra cosita rara...

---

### Post by sebas.rhcp on 2007-08-05
Aca les dejo el thread de donde saque el script:

[aca]("http://home.comcast.net/~ubuntume/nsplugin-wrapper-install-0-1.1.tar.gz")

---

### Post by Hei Ku on 2007-08-05
hay un script que en conjunto con el nspluginwrapper te permite usar flash en el firefox de 64 bits, sin necesidad de instalar el swiftfox ni nada raro. el unico tema es que no me acuerdo de donde lo baje. basicamente es un plugin que baja lo que necesita de los repo, baja el flash y configura el nspluginwrapper. El unico problema es que no me acuerdo de donde lo saque. :( Pero esta ahi afuerta!

---

### Post by Mataca on 2007-08-06
Ahhh bueno :) voy a ver que onda, yo la verdad no pude con el flash
y con el wine, segui las indicaciones de la pagina y no anda para nada
me pide una libreria que tira error.

Alguno tiene un tutorial para wine para 64bits?
yo no pude y soy nw en esto GRACIAS!!!

---

### Post by facundocorradini on 2007-08-06
insisto. si sos nuevo, te recomiendo que instales el de 32 bits. 
vas a tener muchos menos "problemas"

---

### Post by sebas.rhcp on 2007-08-06
> **Hei Ku said:**
> hay un script que en conjunto con el nspluginwrapper te permite usar flash en el firefox de 64 bits, sin necesidad de instalar el swiftfox ni nada raro. el unico tema es que no me acuerdo de donde lo baje. basicamente es un plugin que baja lo que necesita de los repo, baja el flash y configura el nspluginwrapper. El unico problema es que no me acuerdo de donde lo saque. :( Pero esta ahi afuerta!

No es nada raro instalar el firefox, swiftfox, iceweasel o swiftweasel es ELECCION

Es el q postie yo ...

---

### Post by Cripton on 2007-08-09
Yo soy nuevo en ubuntu, me mandé de una al 64 bits feisty, el flash, el java andaron muy bien gracias al tutorial, lo hago andar con el swixfox o como sea que se llame, aunque descubrí que directamente instalando el opera para win, haciendolo andar con el wine, era mucho mas facil, lo que si no me andan los juegos con el wine, supongo que debe ser alguna libreria de opengl que no instalé, pero busca que busca y no encuentro como resolver el problema de la pantallla negra cuando inician los juegos y se cuelga todo

---

### Post by sebas.rhcp on 2007-08-13
Eso depende para cada juego... anda a la pagina de wine y fijate

---

### Post by Cripton on 2007-08-13
bueno, con el synaptic instalé las librerias de cuanto tutorial acerca de eso vi por la web, pero me sigue pasando lo mismo pa los juegos, se pone todo negro, pero los programas andan todos bien, así que sigo pensando que debe ser una librería que no instalé


n00b question: ¿Puede ser que haya instalado alguna de más?:confused:

sinó la otra es reinstalar el wine

por favor no se rindan ante lo desconocido del 64 bits ¡ HAY QUE HACERLO POPULAR/FUNCIONAL !

---

### Post by facundocorradini on 2007-08-13
enserio, yo uso 64 bits,pero creeme q tengo bastante experiencia en linux, y dos años de amor al soft libre, y un año y medio de amor a ubuntu.....

Pero sinceramente, recomiendo a los nuevos, a los que vienen de window$, intalar siempre el de 32 bits...
Por la simple razón de que en 64 hay muchas cosas que son mucho mas dificiles de hacer, y si se mandan derecho a éste, van a pensar q todo en ubuntu es así de complicado...

Creeme, el 90% de los q vienen de win le escapan a la consola como si se tratara del cuco..,

---

### Post by faktorqm on 2007-08-13
jajajajja el cuco! jajajaj lo peor de todo es que tenes razon men! alguien sabe que hasta millenium windows corria con un d.o.s. abajo? incluso xp entero se puede manejar por consola, desde crear un usuario hasta compartir internet. Obviamente hay que sentarse y leer un manual para windows....... perdón, primero comprar el manual y luego......... :P
Lo que me intriga a mi es por que anda tan mal el de 64, o sea, no quiero generar una discusión con esto, pero los que hacen ubuntu no saben que no anda? o simplemente no pueden hacer nada? salu2!!

---

### Post by Mataca on 2007-08-13
Ehh loco q bardea' ?? jajaja

Yo ya me pasé al de 32bits, pero el de 64 no anda para nada mal, el tema es que hay mucho software incompatible.

Aclaro que el sistema era super estable, solo que tuve algunos dramas, con cosas como el Wine y el flash, (a pesar de seguir los tutoriales, las cosas no me salián)
Creo que cuando la arquitectura tenga un poco mas de tiempo en el "mercado", van a desarrollar mas cosas para esta.

No se.. es una humilde opinión

---

### Post by facundocorradini on 2007-08-13
> **faktorqm said:**
> 
Lo que me intriga a mi es por que anda tan mal el de 64, o sea, no quiero generar una discusión con esto, pero los que hacen ubuntu no saben que no anda? o simplemente no pueden hacer nada? salu2!!

El ubuntu  64 anda perfecto. Lo que no anda son muchos paquetes, debido tal vez a la vagancia de los desarrolladores.  y de ahí todos los inconvenientes.
Pero en esto nada tiene que ver ubuntu..

---

### Post by Hei Ku on 2007-08-13
En general, lo que sucede es q los paquetes precompilados estan solo para la version de 32bits. Igual, es para algunos casos, no siempre. Pero si te asusta compilar un programa, mas vale mantenerse en el de 32bits.

Ojo, que compilar tampoco es muy complicado. Te bajas los paquetes para compilar, y despues de eso, en general no es mas que poner make, sudo make install.

Y fuera de eso, es un caño.

---

### Post by matesasesinos on 2007-08-14
buenas, yo tengo el 64 y lo tengo entero configurado como practicamente un windows, teclas de acceso rapido y ñ y demas, no tube problemas, el tema del plugin de flash si, me esta volviendo loco, pero ya lo voy a encontrar (espero), lo que si tengo una pregunta, porque no me deja instalar el 32bits?? tengo un semptron 2800 64bits con una placa asrock k8 vm800 no es nada raro, pero el 32bits dice no ser compatible con el hard ni bien arranca... salu2.

---

### Post by Exheon on 2009-10-05
> **facundocorradini said:**
> enserio, yo uso 64 bits,pero creeme q tengo bastante experiencia en linux, y dos años de amor al soft libre, y un año y medio de amor a ubuntu.....

Pero sinceramente, recomiendo a los nuevos, a los que vienen de window$, intalar siempre el de 32 bits...
Por la simple razón de que en 64 hay muchas cosas que son mucho mas dificiles de hacer, y si se mandan derecho a éste, van a pensar q todo en ubuntu es así de complicado...

Creeme, el 90% de los q vienen de win le escapan a la consola como si se tratara del cuco..,

jeje, entonces yo sería parte del 10% que estaba tan harto del win que se apasionó con el hecho de que en linux todo se pueda hacer con simples y refrescantes instrucciones de texto ...

   :guitar:TERMINAL RULEZ!!!:guitar:, y las X en Linux no andan nada de mal

En este presiso momento estoy usando Jaunty de 64b, tengo porblemas para arrancar algunos juegos (supertux, neverball, etc), he tratado de instalar el zsnes, pero no pasa nada, por apt-get no lo encuetra, (probablemente busca una para 64b), trato de compilarlo, pero al momento de configurarse arroja errores sobre una librería (sdl) que no encuentra, (compilé esa librería, probablemente se configuró una versión de 64b y zsnes necesitaría una de 32b), por estas razones es que estoy casi seguro que por lo menos con zsnes el problema es la arquitectura x64. Si alguien  conoce una forma de arreglar esto, bienvenido sea, creo que me quedo por el momento con Jaunty 64, por los menos hasta que salga Karmic Koala...   *ya se viene*

Salu2

---

