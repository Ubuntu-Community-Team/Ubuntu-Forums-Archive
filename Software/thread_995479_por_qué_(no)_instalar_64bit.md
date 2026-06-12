---
title: "por qué (no) instalar 64bit"
date: 2008-11-27
forum: Software
---

### Post by Kantier on 2008-11-27
Leyendo otro thread, me agarró la duda. Yo ya de costumbre voy derecho a 32bit a pesar de tener un micro de 64, porque hay binarios que hinchan las bolas, y en teoría las cosas copadas de x86_64 no se notan en el uso diario... ¿o si?

Acudo a lo que hayan tenido de experiencias (traten de mantener "científicas" las comparaciones, si no hicieron comparaciones mano a mano que sean confiables preferiría que no las posteen, porque en ese caso no serían respuestas a mi pregunta (si, sé que lo que acabo de decir suena ofensivo)), a lo que sepan de la arquitectura nueva... en fin, a los argumentos válidos que tengan para estar a favor o en contra de instalar ubuntu 64bit en una máquina de 64bit.

Mi caso de uso en particular para ahora y probablemente para el futuro es: PC compuesta de mother, micro, memoria, rígido, VGA + teclado + mouse + monitor + scanner (soportado por SANE), uso wine/cedega/whatever cada tanto, corro Opera, corro flash, ocacionalmente win32codecs (existe win64codecs, así que eso está), hago procesamiento de fotografías (RAWs especialmente), casi no corro juegos.

Doy mi caso de uso para que se entienda de dónde vengo, pero si tienen planteos que sirvan para otros casos de uso, son bienvenidos. Mi idea es llegar a una conclusión como para, en el futuro, poder decirle a nuevos usuarios si tiene sentido instalar 64bit o no, y saber que no estoy mandando fruta. Por ahora, mi repsuesta es "32 bit anda, 64bit tiene algunos dramas con cosas binarias y populares", pero cambiará si veo que no viene así la mano.

---

### Post by guisheca on 2008-11-28
Verás, en cuanto a rendimiento no tengo realizadas las pruebas "científicas" que requerías, pero visto y considerando que no estás recibiendo respuestas y que soy usuario de ubuntu de 64 bits, igual quise darte mi comentario, espero no te moleste.

Como se puede apreciar en las imágenes que estoy adjuntando, corro perfectamente flash, tanto en el navegador como en el escritorio (se ve una entrevista a Stallman en youtube y el perrito que te "lava" la pantalla en el escritorio, funcionando 100%). También tengo wine corriendo como la seda, si, eso que se ve es el Call of Duty 4, corriendo bajo wine, junto con compiz y firefox, y no tuve que hacer nada propio de un usuario de "elite", simplemente le dí doble click al .exe que tengo instalado en mi partición de win (la cual uso como consola XD). Y digo que no hice nada propio de un usuario de elite, porque de hecho no lo soy, soy estudiante de ingeniería electromecánica y uso GNU/Linux para mis tareas diarias de PC.

El único problema que tuve con ubuntu 64bits, es con el java, en el navegador, no logro que funcione correctamente y ya me habían dicho que así sería. Pero cuando no me queda otra que usar una página que contenga java, abro mi xp virtualizado en virtualbox y no tengo problemas allí.

Pero sólo en el navegador web, en los programas hechos en java no tengo ningún problema.
En general te cuento que, mientras uses software libre, no vas a tener problemas con la arquitectura de 64 bits, ya que siempre habrá un alma caritativa que te puede crear un paquete para nuestro micro, o en su defecto se pueden compilar las fuentes. Me pasó con [Guake]("http://www.guake-terminal.org/") el cual uso mucho y no tiene paquetes para 64 bits, por lo que me ví obligado a compilarlo por mí mismo, tarea que no supone un desafío para cualquier homo-sapiens.

Hablando estrictamente de los motivos para tener ubuntu de 64, opino que usar un sistema de 64, es optimizar un poco nuestra pc, creo que puede compararse con aquel que se instala un gentoo o un arch en su sistema para tenerlo todo optimizado, pero en este caso sería algo no tan drástico, algo mas bien para usuarios, no se si novatos, pero si que sólo quieren usar su pc y listo, como yo, pero al mismo tiempo saber que usa un sistema que explota una característica de su micro que de otra forma no lo hace.

Para concluir te puedo decir que siento el sistema mucho mas "fluido", como que das un click y ubuntu te responde más rápido. Además de hacer las proezas como las que muestran las capturas, sin que el uso de micro ascienda al 100% ni se sobrecaliente nada, todo lo hace con soltura. Yo pienso que tranquilamente se puede recomendar el uso de ubuntu 8.10 64 bits, para cualquier tipo de usuarios, siempre teniendo en cuenta que el java en el navegador no funciona, y quien sabe que otro software propietario no lo haga, pero como sólo 0.2% de mi sistema es propietario (lo dice el vrms) eso no me preocupa, ya que uso ubuntu para escapar del software propietario. De otra forma, si no se puede lidiar con ello, no queda otra que recomendar el viejo y querido sistema de 32 bits.

Espero mi comentario no te moleste y te sirva de algo

Saludos.

------------------------------------------------------------------

[[img]http://www.ubuntu-pics.de/thumb/6492/screenshot_05_n4Mn7Z.jpg[/img]](http://www.ubuntu-pics.de/bild/6492/screenshot_05_n4Mn7Z.jpg)[[img]http://www.ubuntu-pics.de/thumb/6493/screenshot_06_YOZWcF.jpg[/img]](http://www.ubuntu-pics.de/bild/6493/screenshot_06_YOZWcF.jpg)

---

### Post by Kantier on 2008-11-28
o sea que corre flash, drivers sé que en mi caso de uso no hay drama, y corre wine, todo sin intervención de usuario.

pinta que la próxima instalación en mi máquina va a ser de 64bit.

---

### Post by Hei Ku on 2008-11-29
Si la vas a usar para procesamiendo de imagenes, que es muy intensivo en el CPU, los 64bits te dan una ventaja interesante. Y en cuanto a instalación de programas, en general tenés una alternativa. De última, podés incluso instalar la version de 32 bits de los programas en un chroot.
Una de las cosas que no anda bien todavia es el plugin de java para el Firefox. Algunos applets no se abren bien con el icedtea, y el plugin de Sun para web no esta para 64 bits.

---

### Post by Kantier on 2008-11-29
¿no se puede recompilar el plugin ese de sun?

---

### Post by Hei Ku on 2008-11-29
> **Kantier said:**
> ¿no se puede recompilar el plugin ese de sun?

Si fuera libre, sí. Pero todavía no es libre el plugin.

---

### Post by sebastianabate on 2008-11-30
Una "contra" que hay que tener en cuenta a la hora de usar un sistema de 64 bits es que el uso de memoria de los programas es ¿considerablemente? mayor que en uno de 32 bits.

Sinceramente no entiendo del todo por qué, pero cuando me pasé de 32 a 64 (uso mucho el virtualbox, y la posibilidad de usar más de 4GB de memoria es muy interesante) me percaté que los programas usaban más memoria que antes, me puse a averiguar qué pasaba y me enteré que esto es normal, ya que la arquitectura de 64 bits necesita este extra de memoria por la forma en que direcciona la memoria (no me preguntes qué quiere decir todo esto, pero te aseguro que es así)

El ¿considerablemente? lo puse así porque depende mucho de la cantidad de memoria que tengas y los programas que uses; en mi caso que firefox use un 20% más de memoria no me afecta en nada, pero en tu caso (que retocás fotografías) no sé cómo te puede afectar.

En cuanto a la ganancia en cuanto a poder de procesamiento, es real, y bastante. Lo pude comprobar con el Virtualbox (el arranque y uso de cualquier VM es mucho más fluido en 64bits), y sobre todo con los juegos 3D, tengo una placa onboard ATI X1250 bastante mediocre para esos menesteres, y desde que estoy en 64 bits los juegos son mucho más fluidos (por ejemplo el Spring lo puedo usar con un zoom más alto en los momentos de acción, cosa que era imposible cuando usaba el sistema de 32 bits)

Y con respecto a los problemas con el plugin de java, yo sinceramente no tuve ningún tipo de problemas con el Icedtea, pero la verdad que no le doy un uso "profesional" (léase aplicación web de un portal corporativo) al plugin, lo uso simplemente para navegar.

Y por último, ya está disponible una versión alpha del plugin de flash en 64 bits. Lo tengo instalado y la verdad que no me trajo ningún problema; es más, es mucho más estable y rápido que el plugin de 32 bits usando ese maltido wraper (o como se escriba) npviewer.bin.
Está disponible en el sitio de Adobe, ahora no tengo el link a mano, pero si googleás "flash player 64 bits" (sin las comillas) lo encontrás en los primeros resultados.

Espero que mi experiencia te pueda servir de algo; y si te animás a "convertirte" a los 64 bits, te recomiendo el foro "x86 64-bits Users" ([http://ubuntuforums.org/forumdisplay.php?f=343](http://ubuntuforums.org/forumdisplay.php?f=343)) donde encontrás solución a cualquier problema que te pueda surgir (lamentablemente es un foro en inglés)

---

### Post by z37a on 2008-11-30
> **Hei Ku said:**
> Si la vas a usar para procesamiendo de imagenes, que es muy intensivo en el CPU, los 64bits te dan una ventaja interesante. Y en cuanto a instalación de programas, en general tenés una alternativa. De última, podés incluso instalar la version de 32 bits de los programas en un chroot.
Una de las cosas que no anda bien todavia es el plugin de java para el Firefox. Algunos applets no se abren bien con el icedtea, y el plugin de Sun para web no esta para 64 bits.

Eso es lo unico me me molesta a mi, pero como planeo usar mas de 4GB de memoria y no uso el plugin java casi nunca la safo!!!

Igualmente tengo en mi laptop un ubuntu de 32(tiene un procesador que si bien trae EM64T, anda pal ogt, 64 bits es AMD, no quiero saber mas nada de intel!!!) y ahi puedo usar el plugin que necesite, si esta prendida y la esta usando alguien entro a la web que necesito tirando un "ssh IP.DE.LA.LAPTOP -X firefox" y listo uso el firefox de aquella maquina.

---

### Post by Kantier on 2008-11-30
> **z37a said:**
> Eso es lo unico me me molesta a mi, pero como planeo usar mas de 4GB de memoria y no uso el plugin java casi nunca la safo!!!

Igualmente tengo en mi laptop un ubuntu de 32(tiene un procesador que si bien trae EM64T, anda pal ogt, 64 bits es AMD, no quiero saber mas nada de intel!!!) y ahi puedo usar el plugin que necesite, si esta prendida y la esta usando alguien entro a la web que necesito tirando un "ssh IP.DE.LA.LAPTOP -X firefox" y listo uso el firefox de aquella maquina.
erm... la implementación de 64bit de intel es buena. Los que son basura de esa empresa son los de garketing (cofcorewillimatecofcofcof), no los de investigación y desarrollo.

por lo de memoria, si querés usar más de 4 GB y 32bit es posible, hay un mecanismo que se llama PAE para permitir direccionar más memoria (hasta 64GB), y si no me equivoco está incluido en el kernel de las distros de 32bit.

---

### Post by MeduZa on 2008-12-10
> **Kantier said:**
> erm... la implementación de 64bit de intel es buena. Los que son basura de esa empresa son los de garketing (cofcorewillimatecofcofcof), no los de investigación y desarrollo.

por lo de memoria, si querés usar más de 4 GB y 32bit es posible, hay un mecanismo que se llama PAE para permitir direccionar más memoria (hasta 64GB), y si no me equivoco está incluido en el kernel de las distros de 32bit.

el PAE esta en el paquete ubuntu server, te agrega 4 bits mas al registro de memoria y aunque es un parche feo funciona, lo que si seguis teniendo es que un ejecutable no puede usar mas de 4gb de ram.

Por otro lado un programa de 64 bits no siempre va o deberia andar mas rapido que uno de 32 bits, depende el caso, si es una aplicacion que usa mucho coma flotante el de 64 bits le va a sacar humo al de 32, si es una aplicacion normal, lo mas seguro que los 2 anden igual o incluso el de 32 bits tenga una leve y casi inperseptible ventaja.

Por el lado de memoria, si los de 64 bits van a comer mas memoria, y es logico ya que su largo de palabra ahora es del doble.

saludos.

---

### Post by guillermolisi on 2008-12-10
> **MeduZa said:**
> 
Por el lado de memoria, si los de 64 bits van a comer mas memoria, y es logico ya que su largo de palabra ahora es del doble.

saludos.
El mayor consumo de RAM no viene por el lado de como direcciona la memoria una maquina con aquitectura Intel ? (que debe reservar parte de la misma para remapear direcciones que estan por encima de cierto valor. Tambien sucede, en menor escala, con 32 bits y 4Gb RAM. Nunca se logra todo ese valor util por esa razon y cambia segun la implementacion del chipset/fabricante)

No es el tamaño de palabra una propiedad del procesador y chipset periferico a este ?

---

### Post by MeduZa on 2008-12-11
> **guillermolisi said:**
> El mayor consumo de RAM no viene por el lado de como direcciona la memoria una maquina con aquitectura Intel ? (que debe reservar parte de la misma para remapear direcciones que estan por encima de cierto valor. Tambien sucede, en menor escala, con 32 bits y 4Gb RAM. Nunca se logra todo ese valor util por esa razon y cambia segun la implementacion del chipset/fabricante)

No es el tamaño de palabra una propiedad del procesador y chipset periferico a este ?

se usan metodos para ahorro de memoria pero no siempre, basicamente usa mas memoria porque en vez de almacenar un nuemoro de 32 CEROS o UNOS ahora tiene que almacenar numero de 64 CEROS o UNOS eso pasa si o si, el CPU no tiene nada que ver con la memoria o el bus, el CPU necesita numero en 64 bits e instrucciones en 64 bits cuando trabaja en ese modo, ademas de que en 64 bits conseguis nuevos sets de intrucciones que en 32 bits no estan, eso depende de la marca normalmente.

---

### Post by guillermolisi on 2008-12-11
Algo mas de info en este link (en Ingles):

[http://en.wikipedia.org/wiki/64-bit](http://en.wikipedia.org/wiki/64-bit)

---

### Post by marianom on 2008-12-11
Desde la óptica de un desarrollador no me gustó como Ubuntu dispone las librerias. usr/lib/lib32 es un enlace a /usr/lib/lib64 y poder compilar aplicaciones que solo funcionan en 32 bits o que pueden presentar problemas en 64 bits es todo un tema.
Conste que mi experiencia con 64 bits fue solo de apenas semanas mientras esperaba que llegara mi máquina nueva pero en ese período tuve que compilar Thunderbird 3 para 64 bits ya que los build eran solo para 32 y no andaban en Ubuntu 64 bits por falta de algunas librerías. Mi experiencia real con 64 bits es en servidores RH/Centos donde podés tener librerías 32 y 64 coexistiendo alegremente. Posiblemente me faltó más tiempo con el Ubuntu 64 para entenderlo o descubrir como manejarme en esas circunstancias.

---

### Post by faktorqm on 2008-12-12
Consume mas memoria siempre y cuando se trabaje con enteros, por que eso no lo puede "acortar", pero a menos que corras cosas muy zarpadas que requieran procesador, "esta controlado" para el uso diario.

---

### Post by Apipote on 2008-12-12
Desde que me pasé a 64 bits, noto: mayor suavidad, menor uso de la cpu, y un algo más de consumo de ram.
Pago ese precio con gusto (tengo 2 gigas), globalmente, creo que anda mejor con 64 bits. Ah...y creo que calienta menos.

Flash de 64, hasta ahora...excelente.

Lo recomiendo.
Slds.

---

### Post by MeduZa on 2008-12-13
> **marianom said:**
> Desde la óptica de un desarrollador no me gustó como Ubuntu dispone las librerias. usr/lib/lib32 es un enlace a /usr/lib/lib64 y poder compilar aplicaciones que solo funcionan en 32 bits o que pueden presentar problemas en 64 bits es todo un tema.
Conste que mi experiencia con 64 bits fue solo de apenas semanas mientras esperaba que llegara mi máquina nueva pero en ese período tuve que compilar Thunderbird 3 para 64 bits ya que los build eran solo para 32 y no andaban en Ubuntu 64 bits por falta de algunas librerías. Mi experiencia real con 64 bits es en servidores RH/Centos donde podés tener librerías 32 y 64 coexistiendo alegremente. Posiblemente me faltó más tiempo con el Ubuntu 64 para entenderlo o descubrir como manejarme en esas circunstancias.

creo, si mal no recuerdo, que ubuntu cuando trabaja a 64 bits crea una carpeta lib32 y una lib64 y la lib64 en realidad es la lib normal, recuerdo que era un maneje porque lo hace diferente que los otros, fue por eso que volvi corriendo a 32bits (ademas de que solo tengo 1 gb de ram  y no se justificaba)

---

