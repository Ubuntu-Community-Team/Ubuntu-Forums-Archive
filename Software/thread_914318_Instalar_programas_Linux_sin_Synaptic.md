---
title: "Instalar programas Linux sin Synaptic"
date: 2008-09-08
forum: Software
---

### Post by FighterPepe on 2008-09-08
Me gustaría tener un enlace con el modo de instalar archivos de extensión .deb en ubuntu (bueno probé con uno y me sorprendió, practicamente me valió con dos clics de ratón). 

Y también los programas que vienen comprimidos, o como se instala un programa a través de la terminal o consola. 

Gracias

---

### Post by Afkael on 2008-09-08
[http://www.guia-ubuntu.org/index.php?title=A%C3%B1adir_aplicaciones](http://www.guia-ubuntu.org/index.php?title=A%C3%B1adir_aplicaciones)

Leete eso que es interesante.. Saludos

---

### Post by FighterPepe on 2008-09-08
Gracias Afkael. 

Un abrazo. 

[img]http://img101.imageshack.us/img101/7251/besotene2.gif[/img]

---

### Post by pol666 on 2008-09-08
**Con Gestor**

_Synaptic _o Agregar y Quitar Programas.

**Desde consola**

_apt-get install_
aptitude install

**Con paquetes .deb independientes.**

Doble click y se abre _Gdebi _y se instala
Si no tambien se pueden instalar con dkpg o con gdeb.

---

### Post by Hei Ku on 2008-09-08
los .deb se instalan con dpkg.

sudo dpkg -i <nombre del deb>

apt-get se encarga de bajar los archivos de los repositorios.

---

### Post by faktorqm on 2008-09-09
Para instalar programas tambien podes compilarlos. Te bajas el codigo fuente, las herramientas para compilar, y la secuencia por lo general es configure (configurar), make (hacer) y make install (hacer instalar) y listo.

---

### Post by pablo atheist on 2008-09-09
la verdad de la milanesa es que instalar programas en ubuntu es mucho mas facil que en windows y/o cualquier otro sistema oprativo habido y por haber

---

### Post by Afkael on 2008-09-09
> **pablo atheist said:**
> la verdad de la milanesa es que instalar programas en ubuntu es mucho mas facil que en windows y/o cualquier otro sistema oprativo habido y por haber

ni mejor ni peor a mi criterio... 

Consulto acá para no abrir otro hilo... cómo hago para que en mis repositorios haya soft más nuevo?.. por ejemplo: yo queria instalar Blender y se que hace muy póco se liberó la versión 2.47.. pero en los repositorio están recién por la 2.45.. 
Hay repositorios con soft más actual?

Saludos

---

### Post by pol666 on 2008-09-09
fijate en la pagina oficial. Y si es mas facil y mejor instalar programas, no como en windows que tenes que recurrir a la bondad de alguien que suba un programa, para descargarlo, parchearlo e instalarlo, reiniciar la pc y usar ufff

---

### Post by Afkael on 2008-09-09
> **pol666 said:**
> fijate en la pagina oficial. Y si es mas facil y mejor instalar programas, no como en windows que tenes que recurrir a la bondad de alguien que suba un programa, para descargarlo, parchearlo e instalarlo, reiniciar la pc y usar ufff

No entiendo a que te refieres, para el ejemplo que di antes del blender, me dices que me fije en la página oficial.. y es exactamente como lo haria en Windows!!! y si vamos a los repositorios, se podrian tomar como tales los sites como softtonic, softpedia, download.. ahora, si vamos a el software comercial, por lo general, no están en synaptic... y conseguirlos de formas menos ortodoxas.. es más fácil en windows.

La ventaja del synaptic es la actualización... pero tiene sus contras (como el soft algo desactualizado). Toda ventaja es una desventaja también, con el sistema de repositorios evitás tener paquetes "duplicados" en tu PC y ahorás espacio... pero se complica determinar fácilmente qué sofware depende de tal paquete y hasta en algunos casos se dan problemas de dependencias circulares...
Queda todavia más que claro que si necesitás de urgencia un openOffice no te vas a poner a compilarlo..

Saludos

---

### Post by leo_rockway on 2008-09-09
> **Afkael said:**
> ni mejor ni peor a mi criterio... 


Agregar y quitar programas... no sólo quita ¡sino que también agrega!

> **Afkael said:**
> Consulto acá para no abrir otro hilo... cómo hago para que en mis repositorios haya soft más nuevo?.. por ejemplo: yo queria instalar Blender y se que hace muy póco se liberó la versión 2.47.. pero en los repositorio están recién por la 2.45.. 
Hay repositorios con soft más actual?

Para Blender en particular: te lo bajás de la página, lo descomprimís y lo ejecutás, tan fácil como eso. No hay que instalar nada ni compilar.

---

### Post by Afkael on 2008-09-09
lo cierto es que pensé que podian existir repositorios (quizá no oficiales) donde conseguir el soft más actual.. Sabia que lo podia descargar desde la página (supongo que todo el software se puede obtener asi) lo que pretendía es conseguirlo todo con el Gestor..

---

### Post by WanderingKnight on 2008-09-09
> la verdad de la milanesa es que instalar programas en ubuntu es mucho mas facil que en windows y/o cualquier otro sistema oprativo habido y por haber

El tema de tener repositorios no es exclusivo de Ubuntu. La gran mayoría de las distribuciones grandes de Linux tienen un sistema similar.

De hecho, Ubuntu le debe gran parte de su sistema de repositorios a papá Debian ;)

El hecho de poder tener este tipo de repositorios tiene mucho más que ver con una ventaja del software libre (que en realidad estoy segurísimo que nació para sobreponerse a una de sus mayores desventajas, el fraccionamiento) que con Ubuntu en sí mismo.

---

### Post by Afkael on 2008-09-09
> **WanderingKnight said:**
> El tema de tener repositorios no es exclusivo de Ubuntu. La gran mayoría de las distribuciones grandes de Linux tienen un sistema similar.

De hecho, Ubuntu le debe gran parte de su sistema de repositorios a papá Debian ;)

El hecho de poder tener este tipo de repositorios tiene mucho más que ver con una ventaja del software libre (que en realidad estoy segurísimo que nació para sobreponerse a una de sus mayores desventajas, el fraccionamiento) que con Ubuntu en sí mismo.

Un sistema que es bastante frondoso también es el Portage de Gentoo

---

### Post by WanderingKnight on 2008-09-09
Sip, pero ese ya no es para binarios precompilados sino que es un poco más complejo, por eso no lo pondría en la misma categoría...

---

### Post by Hei Ku on 2008-09-09
> **Afkael said:**
> No entiendo a que te refieres, para el ejemplo que di antes del blender, me dices que me fije en la página oficial.. y es exactamente como lo haria en Windows!!! y si vamos a los repositorios, se podrian tomar como tales los sites como softtonic, softpedia, download.. ahora, si vamos a el software comercial, por lo general, no están en synaptic... y conseguirlos de formas menos ortodoxas.. es más fácil en windows.

La ventaja del synaptic es la actualización... pero tiene sus contras (como el soft algo desactualizado). Toda ventaja es una desventaja también, con el sistema de repositorios evitás tener paquetes "duplicados" en tu PC y ahorás espacio... pero se complica determinar fácilmente qué sofware depende de tal paquete y hasta en algunos casos se dan problemas de dependencias circulares...
Queda todavia más que claro que si necesitás de urgencia un openOffice no te vas a poner a compilarlo..

Saludos

Lo cierto es que para las distros más populares, los sites proveen por ejemplo un .deb para instalar, o un PPA de donde instalarlo a través de Synaptic directamente.

Y los repositorios no son ni por asomo un site de download solamente.

---

### Post by Afkael on 2008-09-10
> **Hei Ku said:**
> Lo cierto es que para las distros más populares, los sites proveen por ejemplo un .deb para instalar, o un PPA de donde instalarlo a través de Synaptic directamente.

Y los repositorios no son ni por asomo un site de download solamente.


con lo de los sites de download me referia más bien a la posibilidad de ordenar el software por categorias y descripciones, no un repositorio en si.. 
Sinceramente no creo que un usuario de Windows le encuentre utilidad a un sistema como synaptic, como bien dice WanderingKnight es también una necesidad del software libre, ahora si fuese algo universal y más pulido donde mantengo mi sistema y mi software (comercial o no) actualizado, entonces si seria contemplado en Windows...
Insisto.. no es mejor ni peor.. es diferente..

Saludos

---

### Post by pol666 on 2008-09-10
ehhhhhhh tenes ra... NO.

Los gestores, te permiten ordenar el software y administrarlo, manejar dependencias, reparar paquetes, controlar repositorios, agregar, reinstalar, actualizar,  quitar, eliminar configuraciones.

si, vos vas a e instalas un software comercial desde un .deb, te va a aparecer tambien en el synaptic.




> Vamos, suponte que reinstalas windows y tenes que volver a poner los programas.

*Suponte, que los descargas (desde un warez o desde un softonic por ejemplo)
*Bajar de rapidshare, esperar, blablabla...
*En caso que lo bajaste del warez, tenes que buscar el serial, el crack si el usuario que lo subio no lo inluyo.
*Instalas el programa, siguiente, siguiente, aceptar, blabla, siguiente, aceptar, siguiente.
*Ahora lo tenes que crackear, poner esto, esto, esto
*listo.. ahora vamos CON OTRO PROGRAMA.


Cuantos, usuarios de windows, envidian poder seleccionar un gran lista de programas, darle ok, y que lo descargue e instale de una. mmm

---

### Post by Hei Ku on 2008-09-10
Si alguna vez tuviste que armar un entorno de desarrollo en Windows, sabrías que lo que decis no es verdad ni por asomo.

Estoy hace dias ejecutando un instalador tras otro para instalar todo lo que necesito. Ojo, lo tengo todo en un disco compartido, con las licencias, etc.
Pongo a instalar uno, bajo a fumar, vuelvo, pongo a instalar el otro, bajo, pongo el otro, me dice que le falta uno anterior, pongo el anterior, bajo, instalo el que queria. 

Todos los instaladores distintos, porque pertenecen a distintas empresas, y manejan las dependencias de manera diferente. Como eso es igual a los repositorios, no lo veo.

A un nivel muy abstracto, todos cumplen la misma funcion, pero en la practica, son muy diferentes.

Y ni hablar en el momento que necesite desinstalar algo. Es mas facil pedir que me instalen una imagen nueva que desinstalar y las cosas queden bien.

---

### Post by Afkael on 2008-09-10
Nop, no he instalado un "entorno de desarrollo" pero me sorprende bastante lo que decís.. Hace dias? una instalación local (o en una red local)?... quizá debieras comentar que software estás instalando..
Mi "entorno de diseño" lo consigo instalando Adobe CS2 (unos 15min).
En cuanto a los instaladores distintos.. No todo está en Synaptic, no todo está en .deb.. linux tiene problemas mucho más graves en ese sentido (linux en general, no ubuntu), espero que se pongan de acuerdo para hacer un instalador universal para linux (también uno del SO).
Tampoco dije que era igual (es más.. dije que eran distintos) pero (vuelta) los WinUsr tienen lo que se ajusta a lo que necesitan. En cuanto a los paquetes, synaptic los gestiona casi a la perfección pero el SO no.

Igualmente cuando me referia a un usuario común me referia a quienes utilizan su PC para todo un poco (porque si es para trabajar siempre aparece un Maquero -moquero- presumiendo de su MacOS) y no son ñoños (de esos que explota la PC y dicen "creí que era normal").. me resulta mucho más "fácil" instalar el driver de la VGA en windows que en Linux, no lo encontré ni en Synaptic, ni en .deb y eso probablemente tenga que ver con que cada distro usa su sistema de instalación, tampoco pude instalar el flash player (aunque creo que si está en synaptic).
Digo, lo que consigue Win con ese sistema es que todo software para Windows sobre la faz de la tierra se instale de la misma manera y a linux le cuesta horrores decir "see, el sistema de rpm´s es mejor.. todos utilizemos ese" (es un ejemplo)y entonces.. cada maestrito con su librito (Richard LaVolpe).

Saludos

---

### Post by WanderingKnight on 2008-09-10
>  Nop, no he instalado un "entorno de desarrollo" pero me sorprende bastante lo que decís.. Hace dias? una instalación local (o en una red local)?... quizá debieras comentar que software estás instalando..

No lo hice personalmente, pero acá en el laburo me comentaron en una oportunidad que se puede estar más de un día entero instalando cosas.

Un entorno de desarrollo es algo bastante delicado, ya que dependés un montón de las diferentes versiones de compiladores, VMs, etc.

---

### Post by Afkael on 2008-09-10
Bueno, yo me referia a algo más sencillo.. además, según entiendo, ubuntu es una distro más enfocada al usuario común de PC.. al que va a escuchar música, retocar sus fotografias, leer su correo... includo si quisiera programar (como hobby), no pasaria horas instalando software.. supongo que optaria por algo como Visual en Windows o Kdevelop en Linux que en unos minutos los tenes instalados..
Insisto.. si linux unificara criterios nvidia/ati podria empaquetar sus drivers para que instalarlo sea sólo ejecutar un archivo (es más.. Ubuntu es uno de los que más a roto criterios medianamente unificados).

PD: Hei ku, según entiendo Linux es de lo más potente para armar un entorno de desarrollo.. por qué no has logrado (..convenciendo a tu jefe supongo) deshacerte de Windows?

---

### Post by leo_rockway on 2008-09-10
> **Afkael said:**
> espero que se pongan de acuerdo para hacer un instalador universal para linux

Jamás voy a entender esa manía que tienen algunos por estandarizar los sistemas de instalación o unificar distros o de que todo se haga de la misma manera en todos los entornos...

Si yo quiero usar yast uso yast, si quiero usar yum uso yum, si quiero usar emerge uso emerge, si quiero usar dpkg uso dpkg. Nadie se tiene que poner de acuerdo en nada porque cada uno tiene la libertad de elegir lo que le gusta más o de codear algo nuevo si así lo desea.

Y si me quiero poner a compilar OO.o y Firefox... sigo en todo mi derecho.

EDIT:
> **Afkael said:**
> si linux unificara criterios nvidia/ati podria empaquetar sus drivers para que instalarlo sea sólo ejecutar un archivo

Perdón, pero instalar los drivers de ati/nvidia __es__ ejecutar un archivo. E incluso en este caso lo veo mal. GNU/Linux no tiene que cambiar sus criterios, son AMD y NVidia los que tienen que hacerlo (AMD ya lo hizo). Si los drivers son libres entonces cada distro se encarga sin problemas de empaquetarlo como más le guste.

---

### Post by Afkael on 2008-09-10
No es dificil de entender, todo esfuerzo sin orden resulta poco eficiente y menos eficaz.. Nunca hable de eliminar los sistemas de instalación actual.. pero ofrecer una alternativa universal es un beneficio para mejor que aporta en gran medida la accesibilidad del sistema.

Para darte un ejemplo, los Driver de mi 8600GT los tuve que instalar con Envy, ya que ejecutando archivos no funcionó... Kubuntu trae una herramienta para instalar driver restringidos.. pero tampoco funcionó... Ati/Nvidia, asi como vos tenés la libertad de instalar de la manera que más te guste, tiene la libertad de distribuirlo como quiera (tanto para linux como para windows).. pero como el objetivo de distribuir un software es que todos puedan acceder a él busca hacerlo de la manera más sencilla y a la que puedan acceder usuarios de extensa experiencia como vos, y sin experiencia como yo...
Es medio egoista lo que dices porque no todo el mundo dispone del conocimiento ni le sobra el tiempo para compilar OOo (lo digo asi porque compilar no te ofrece ventajas notables con respecto a los binarios) incluso algunas distribuciones (como Gentoo) te limitan a disponer de medios de primer mundo como una conexión a internet de Banda Ancha (see, yo emergi kde con dialup). Entonces la libertad de la que hablas no termina siendo tal (yo quiero Blender 2.47 por synaptic y tampoco puedo)

Saludos

---

### Post by faktorqm on 2008-09-10
amm no te iba a contestar por que la mitad de las cosas que posteaste me parecen a mi que no solo no tenes razón (repito: para mi) sino que encima no tenes fundamento para sostener ninguna (repito: para mi) y aparte no aporta nada al titulo original de la conversacion, pero esto que te quoteo aca fue demasiado.

> **Afkael said:**
> (lo digo asi porque compilar no te ofrece ventajas notables con respecto a los binarios)

Entiendo que no sos programador (ya que nunca instalaste un entorno de desarrollo de programacion) asi que te cuento como es un poco la movida, vos cuando programas, haces tus algoritmos, la interfaz grafica, y demas. Suponete que vos desarrollas blender, todo ese tipo de programas utilizan lo que son instrucciones de assembler (que es el lenguaje de programacion que entiende el microprocesador por hacerte un resumen) para "mejorar" u "optimizar" el rendimiento, por que? te tiro un ejemplo asi no mas, un algoritmo de renderizado de textura, vos lo programas y te anda y todo barbaro. Bueno, existen lo que se llaman juegos de instrucciones, que se crearon para optimizar POR HARDWARE y mediante pocas instrucciones cosas que antes se hacian con muchas instrucciones de assembler, los ejemplos mas tipicos son MMX, SSE, 3D NOW!, que seguro lo escuchaste nombrar cuando te fuiste a comprar un micro. 
Entonces, vos programas tu algoritmo de renderizado y usa instrucciones SSE por ejemplo, pero el que programaste originalmente sin usar nada de eso, lo incluis tambien en el paquete. Entonces yo me bajo tu programa, y lo compilo. El compilador agarra y se fija que juegos de instrucciones tiene mi micro, si tiene SSE, lo compila con esa optimizacion y el programa me va a andar NOTABLEMENTE mas rapido, que alguien que tiene un micro sin ese juego de instrucciones, y lo usa igual, pero la velocidad es menor renderizando lo mismo y suponiendo hardware equivalente.

Por eso Gentoo aun en la actualidad es entre un 5 y (me animaria a decir) un 10% mas rapido que otra distribucion "compilada genericamente", por que usa solo los juegos de instrucciones que vos tengas. (eso si, tarda 20 horas en instalar, y necesitas un micro con lo ultimo de lo ultimo...)

Yo por ejemplo tengo un athlon xp 2600+, y el adobe premiere cs2 no me deja instalarlo (en windows) por que no tengo el juego de instrucciones sse2. ahh y proba de borrar los archivos que se llaman msiexec.exe de tu windows, a ver como haces para instalar/desinatalar algo despues... (no lo hagas ;)) a mi si me borran el synaptics no me pasa nada...

con respecto a lo de tu metodo de instalacion "universal" (que feo que suena eso!!!) lo que se hizo hace mucho ya son los instaladores en  scripts de shell pero no tuvo muuucho exito que digamos. la primera que tengo registro que lo hizo fue Loki software hace mucho tiempo atras. (hacia jueguitos para gnu/linux)

Bueno, espero que hayas aprendido, y si tenes dudas/consultas preguntame que esta todo ok. perdón si desvirtue un poco el tema original. Salu2!!

---

### Post by Afkael on 2008-09-10
El tema original fue resuelto en el primer o segundo post, y por eso me explayé sobre un tema que planteó un usuario diciendo que Synaptic era mejor que el sistema de instalación de Windows.. dije que no era ni mejor ni peor, y no me baso más que en decir que es imposible adaptar una especie de synaptic en windows, simplemente porque no hace falta. Ambos sistemas tienen pros y contras (innegable, por cierto).
En cuanto a lo de compilar.. no saqués de contexto lo que he dicho, leo se referia a OOo, que es de lo más pesado para compilar y en definitiva las ventajas que deja no son significativas comparadas a los binarios (provalo si querés.. OOo compilado vs OOo binario... -no lo prueves-)..
También he instalado Gentoo y me encantaria tenerlo todabia porque el sistema de portage es hermoso (utopico, pero hermoso) y los mismos usuarios te dicen que si es por la velocidad que puedes obtener de tu sistema ni te gastes en compilarlo.. la ventaja es la personalización y que tu sistema es optimo para tu equipo.. 
Es raro.. pero, por ejemplo, blender renderiza más rápido en windows que en linux (aún compilado con optimizaciones)... También lo que digo es una impresión mia.. si conociera la verdad, estaria haciendo plata..

---

### Post by WanderingKnight on 2008-09-10
> 
En cuanto a lo de compilar.. no saqués de contexto lo que he dicho, leo se referia a OOo, que es de lo más pesado para compilar y en definitiva las ventajas que deja no son significativas comparadas a los binarios (provalo si querés.. OOo compilado vs OOo binario... -no lo prueves-)..

Jaja, es muy gracioso porque justamente oí de gente que respeto bastante que OOo es uno de los programas más notorios en cuanto a mejora de rendimiento al compilar para procesadores más limitados.

Obviamente que con un Dual Core obtener un 2% más de un procesador de texto no importa demasiado, pero bueh.

Lo del sistema universal de instalación es una bobada porque ni siquiera en Windows todos los programas se instalan de la misma manera. A veces directamente te dan el binario precompilado sin InstallShield ni ninguna de esas cosas.

En fin, el tema de cómo instalar un programa es cuestión de quién lo hace. Si es un programa que desarrollé yo (que no desarrollo nada, pero no importa a efectos del ejemplo), lo más probable es que te de el código, el binario precompilado con todas las bibliotecas propias necesarias en un lindo tarball, y te mande a los repos de tu distribución (si es que está incluído) si necesitás que estén todos los archivos ordenaditos y no tenés ganas de resolver dependencias.

PD: Una última cosa: El sistema "universal" de Ubuntu _ya existe_, y son los repositorios. Difiere del sistema "universal" de otros sistemas operativos como Gentoo o Fedora. Linux en sí no es un sistema operativo así que no le importa mucho el tema de tener un sistema "universal" de instalación de cosas.

---

### Post by leo_rockway on 2008-09-10
Yo puse a FF y a OO.o como ejemplos justamente por ser extremos. Gentoo, si no me equivoco, ofrece binarios para ambos paquetes. Quería remarcar específicamente que un instalador universal (o cualquier cosa que se haga llamar universal) nunca deja conforme a nadie.

Mi opinión es que dejemos los sistemas de instalación como están, que son buenísimos por separado y mejores que los de Windows (sí... mejores que los de Windows).

---

### Post by Hei Ku on 2008-09-10
Afkael, mi comentario es simplemente que no tenés idea de lo que hablás. Ni en Windows ni en Linux.
Fin de este thread para mí.

---

### Post by faktorqm on 2008-09-10
> **hei ku said:**
> afkael, mi comentario es simplemente que no tenés idea de lo que hablás. Ni en windows ni en linux.
Fin de este thread para mí.

+1

---

### Post by Afkael on 2008-09-10
Bueno, puede que esté equibocado... nadie es perfecto.. pero noto que no han entendido lo que quise expresar...
No digo que el sistema de Windows es mejor... digo que es el sistema que mejor se adapta a Windows.. y tiene que ver con la expresión de pol666 que dijo..
> es mas facil y mejor instalar programas, no como en windows que tenes que recurrir a la bondad de alguien que suba un programa, para descargarlo, parchearlo e instalarlo, reiniciar la pc y usar ufff
... descargarlo e instalarlo son los pasos normales (no se a qué se refiere con esos otros pasos \\:D/\\:D/) y en definitiva es lo que hace synaptic.. (se que me van a hablar de control paquetes.. pero en windows no se puede..).
Lo de OpenOffice.. estaba confundido.. ahora veo que hay bastante ventaja en cuanto a rendimiento del programa compilado.. pero igual considero que no es un programa para ponerse a compilar.
Y no se enojen.. la gente puede pensar diferente.. y además NO DIJE QUE EN WIN SEA MÁS FÁCIL.

---

