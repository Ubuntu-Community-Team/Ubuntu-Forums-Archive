---
title: "Problema parpadeo pantalla Ubuntu 10.04"
date: 2010-06-15
forum: Software
---

### Post by rco251 on 2010-06-15
hola, soy medio nuevo en el foro no se este thread esta en el lugar correcto, pero bueno tengo un problema con la pantalla de mi notebook que en determinados momentos hace como un parpadeo horizontal en la pantalla como una interferencia cuando hay un telefono cerca... 
he probado a desinstalar el compiz y tambien instalar drivers de intel pero sigo con el mismo problema...

a alguien le pasa lo mismo???
tengo una lenovo g450 con placa de video intel 4 series family.
Saludos y gracias de antemano...

---

### Post by marcelo_bur on 2010-06-16
Hola. No se tanto como otros aqui, pero se me ocurre que si la interferencia es cuando estás cerca de un teléfono tal vez sea porque estas usando una conexíon inalambrica a internet y, por otra parte, el teléfono al que te referis también sea inalámbrico.
Por otro lado podes probar en cambiar el valor de la "tasa de refresco" en Sistema>Preferencias>Resolución de pantallas. Esta ruta es para Ubuntu 8.04, no decis cual es tu versión y no se si en todas es la misma.
También podes probar con los controles del monitor.
Saludos

---

### Post by rco251 on 2010-06-16
hola marcelo, no tengo ningun telefono cerca ese es el problema, la pantalla hace como cuando hay un telefono cerca pero no hay ninguno, en versiones anteriores de ubuntu no lo hace y en otros so tampoco...

gracias

---

### Post by guillermon on 2010-06-18
Hola, a mi me pasa lo mismo! Iba a sacar un post con varias cosas que me pasan con mi flamante lenovo g550. Pero aprovecho el post. Me ocurren también pantallazos hacia el lado inferior, todo horizontal; sin algo con lo que relacionarlo. Lo puede hacer cada 5 minutos, como cada una hora. Tengo activado el compiz.
Alguna idea? gracias desde ya
Guillermo

---

### Post by rco251 on 2010-06-18
hola Guillermo. Es exactamente lo mismo que me pasa en mi lenovo...
vos decis que tenes instalado el compiz, yo tengo casi descartado que sea problema del compiz porque he desinstalado por completo el compiz y todos sus librerias y seigue haciendo lo mismo...
saludos

---

### Post by rco251 on 2010-06-18
hola guillermo, una pregunta!!
antes tenias otros SO? y te pasaba lo mismo? o no..
porque quiero descartar la posibilidad de que sea algun problema de hardware...
gracias, saludos

---

### Post by guillermon on 2010-06-19
> **rco251 said:**
> hola guillermo, una pregunta!!
antes tenias otros SO? y te pasaba lo mismo? o no..
porque quiero descartar la posibilidad de que sea algun problema de hardware...
gracias, saludos
Hola rco251, no, no la he instalado nunca otro SO, jeje! Casualmente la compré porque venía free dos (no  le doy un mango al señor Gates). Del mismo modo, tampoco he instalado otra versión que la 10.04 (pero descarto error, pues instalé de crear un disco de arranque en mi pc de escritorio que anda un chiche).Estoy pensando que anoche por ejemplo estuve muchas horas y no parpadeó... Eso es lo que me extraña... A vos cada cuánto te parpadea?


Aprovecho el post, pues podemos intercambiar experiencia... Hay botones con la "tecla función" que curiosamente no 'funcionan'! El brillo por ejemplo, pero lo solucioné añadiendo al panel una aplicación, la que controlo por mouse. Entre varias, he notado que en mi conexión de red a través de mi router inalánmbrico solo descarga hasta 67 KiB/s (he instalado el samba).
Una pregunta importante es si te ha traido una partición con un giga de información... que al instalar el ubuntu me ha creado el grub como si tuviera el vista. Sabes qué es?
El botón para encender el wifi no funciona, pero como tiene un encendido físico no hay problema!
Bueno, tengo más comentarios y preguntas.. pero no quiero que se haga largo. Me gustaría saber si está contento con tu lenovo y con ubuntu...Saludos. 
Guillermo

---

### Post by rco251 on 2010-06-20
hola guillermo. a veces me parpadeaba cada 5 minutos y otras veces cada 1 hora por ejemplo, ahora instala el ubuntu 9.10 y me anda de maravilla, tendre que dejar ese aunque este mucho mejor el 10.04...

el brillo a mi tampoco me funciona con las teclas, pero esa funcion no es de vital importancia... a mi parecer.
en cuanto a la velocidad de descarga yo fui a el centro de software de ubuntu y en origenes de software puse servidor principal en vez de servidor para argentina y asi me baja dependiendo el dia a 100 KiB/s y algo...

en cuanto a las particionas, yo al instalar las borro a todos y luego creo tres desde cero una ext4 para la raiz (/) y otra ext4 para home (/home) y por ultimo una swap (espacio de intercambio) y no me ha creado ninguna para windows...

el wifi despues de instalar los drivers funciona perfecto..

en cuanto a la compu anda bien, no es muy grande, pero si estoy contento por como funciona hasta ahora, y ubuntu lamentablemente no me funciona bien.. pero bueno uso el viejo por ahora...
saludos..

---

### Post by guillermon on 2010-06-20
> **rco251 said:**
> 
en cuanto a las particionas, yo al instalar las borro a todos y luego creo tres desde cero una ext4 para la raiz (/) y otra ext4 para home (/home) y por ultimo una swap (espacio de intercambio) y no me ha creado ninguna para windows...
Rco251, respecto de la partición, me refiero a que traía una oculta, con una info, que sospecho que servirá para algo en relación a win. Aquí la monté con sudo mount /dev/sda3 /media/, y te pongo un pantallazo para que lo veas. Por lo visto tu pc no lo trajo. Ahora haciendo una prueba con la batería (para ver sifuncionaba la configuración de que hiberne antes de que se apague, lo que no anda) he ingresado. Se llama Lenovo OneKey Rescue 6.0 Partition. Y no funciona nada me parece, porque no lee ext4.  El problema es que ubuntu detectó esos archivos, y creó el menú como si tuviera otro sistema, lo cual no es así (y me molesta tener el grub cada vez que inicio). Y la verdad es que no entiendo el grub2! Tengo que ponerme al leer.
> en cuanto a la compu anda bien, no es muy grande, pero si estoy contento por como funciona hasta ahora, y ubuntu lamentablemente no me funciona bien.. pero bueno uso el viejo por ahora
Yo a pesar del destello me quedo con lucid... no sé. Lo importante que necesitaría saber es si afectan al hardware o al sistema... Pero bueno, estaría bueno que Ubuntu te funcione bien, que estés satisfecho con él.
Ah, y respecto a los kiB que te preguntaba, no me refería a la descarga de internet, sino a la descarga dentro de una red, que tengo a través de samba y mi router linksys.
Bueno, saludos y hasta pronto

---

### Post by rco251 on 2010-06-20
Guillermo, puede que esa particion sea el recovery e windows ya que las lenovo tienen un boton para poder hacer y backup del sistema y luego poder recuperarlo apretando dicho boton que en la mia esta al lado del boton de encendido, mi compu tambien tenia esa particion oculta pero la borre manualmente al instalar linux..

en cuanto al destello, a mi me gusta mucho eso por eso me cambie a una version anterior, solo espero que aparezca una solucion o por lo menos que el 10.10 no tenga ese problema...

pero coincido con vos en que el lucid es mejor y con respecto a lo del router no se mucho de eso, por lo que no podre ayudarte ademas de que no tengo ninguna red de ese tipo, solo tengo un router muy precario pero anda bien jaja...

saludos...

---

### Post by SplinterGU on 2010-06-23
tengo el mismo problema... lenovo g450 4gb ram... video intel mobile 4.

parte inferior, horizontal toda la pantalla... pasa cada 5 minutos, cada hora o cuando se le da la gana... mas que un parpadeo es como cuando se cambia de modo de video, ese "flick" que se hace en ese momento... en otras ocaciones ese flick vi que es mas bien basura que se escribe en pantalla, porque en momentos fue de 1/3 de la pantalla, por lo general es de 1/10 de la pantalla en la zona 9/10 de la pantalla (si la dividimos en 10 zonas horizontales) mas o menos.

probe con compiz, sin compiz, sin acceleracion de ningun tipo, y pasa siempre, no es una frecuencia de tiempo exacta, pero pasa, y no pasa con otros operativos.

no quiero tener que pasarme a debian ahora que tengo todo configurado y actualizado.

tiene que ser un problema de los drivers xorg, o algo similar, estaria bueno saber que cosas cambiaron entre esta version y la version anterior de ubuntu.

me alegra saber que no es un problema de mi equipo, sino que es una constante con estos equipos y ubuntu.

---

### Post by guillermon on 2010-06-26
> **SplinterGU said:**
> tengo el mismo problema... lenovo g450 4gb ram... video intel mobile 4.

me alegra saber que no es un problema de mi equipo, sino que es una constante con estos equipos y ubuntu.
Hola Splinter, bienvenido al foro! y bienvenido a este estado de mayor tranquilidad (saber que no es nada malo) pero de queda en la mera contemplación... no estamos solucionando el problema mientras vemos flick al antojo de algún demonio. Me encantó el término "flic"; ahora mi flamante lenovo 'flicquea' cuando se le da la gana. Estoy pensando en reportar el bug, pero no sé cómo se hace. Es buena idea hacerlo?
Vos la has probado con otra Distro? No me imagino cambiando, pero no estaría mal probar
Saludos

---

### Post by SplinterGU on 2010-06-27
muchas gracias por la bienvenida.

la verdad aun no probe en otra distro, tengo que bajar algun live y probar un buen rato, me da no se que tener que reinstalar todo, aunque no pierda los archivos porque tengo el home en una particion separada, si tendria que instalar y todo de nuevo, actualmente este es el unico problema que me queda resolver en la lenovo.

si, estaria bueno reportarlo, pero no se si el termino flick seria el adecuado, por eso no reporte yo tampoco.

---

### Post by SplinterGU on 2010-06-28
probe con debian live creo que 6.0, de mayo 2010, testing, y pasa lo mismo.

probe tambien con opensuse live y no pasa, estuve como 30 minutos y no paso nada.

---

### Post by SplinterGU on 2010-06-28
instale el paquete kde-full, y probando kde parece que no falla, pero no estoy seguro de haber probado el tiempo suficiente, si alguien puede confirmar.

asi por lo menos intentamos ver por donde viene la falla.

gracias

---

### Post by guillermon on 2010-06-30
> **SplinterGU said:**
> instale el paquete kde-full, y probando kde parece que no falla, pero no estoy seguro de haber probado el tiempo suficiente, si alguien puede confirmar.

asi por lo menos intentamos ver por donde viene la falla.

gracias
Sería bueno que cuando puedas decir cómo te fue con este cambio lo digas. Encontré en una página externa un comando larguísimo que reemplazaría el escritorio gnome por el kde... En el caso que funcione podría ser una posibilidad (si el comando es realmente bueno). La otra puede seguir teniendo un poco de paciencia hasta que se corrija (sigo pensando que lo importante en mi caso es saber si el parpadeo es o no perjudicial tanto para soft como hardware). Saludos

---

### Post by SplinterGU on 2010-07-01
hola, la verdad que no tengo tiempo ahora para probarlo en kde, el kde es muy incomodo y la verdad que no me acostumbro, y ahora mismo estoy con mucho trabajo, asi que no puedo cambiar de desktop, necesito productividad, por eso decia si alguien mas podria probarlo.

con respecto al parpadeo, estoy seguro que es basura en el video en un frame, y cuando movemos le mouse o tecleamos algo se actualiza, porque me ha pasado que me ha dado el parpadeo sin estar tocando nada, y el parpadeo se transformo en basura en la pantalla, como fragmentos diversos de ventanas ya escritas.

lamentablemente estoy intentando encontrar algun otro post similar en otro lugar, pero no encuentro nada.

agradeceria que si alguien encuentra algo, ponga los links.

saludos

EDIT: Me olvidaba, aunque estoy seguro que no tiene nada que ver, ya aparecio mi primer pixel vago, no esta muerto porque solo se apago la componente verde, el rojo y el azul van bien, o quizas este muerto, no lo se.

---

### Post by SplinterGU on 2010-07-04
he desistido de debian y sus variantes, con kde va igual... ahora estoy con opensuse y va de maravillas, me costo activar la red y ahora tengo el problema que compiz no arranca por defecto y cuando arranca no tengo decoracion de ventanas en las aplicaciones kde, pero esto es tema de configuracion.

saludos, y suerte.

---

### Post by canci_rc on 2010-09-30
hola! soy nuevo. hace poco me compre una lenovo g450 y tengo el mismo problema del parpadeo de pantalla. lo preocupante es q pueda llegar a causar un daño al hardware. si alguien puede solucionar
el problema avise!!

---

### Post by mchojrin on 2010-10-02
Hola:

  Estoy teniendo el mismo problema. Compre una Lenovo G550, instale Ubuntu 10.04 y he notado estos inconvenientes:

1 - El parpadeo de la pantalla es bastante irregular. Al principio pense que se trataba de mi router wi-fi interfiriendo de alguna manera, pero aparentemente no es asi. No logro detectar un patron para que se produzca el parpadeo
2 - No se como apagar el mousepad y realmente se me hace molesto al teclear que el puntero se vaya a cualquier lado.

  Aun no desinstale el Win que venia de fabrica, asi que quiero probar para cerciorarme de que el problema no es del hardware si no de algun problema del driver de video...

  Yo vengo de unos cuantos años de usar OpenSuse (tengo otra compu en la que todavía lo uso). Es una buena distribución, pero sinceramente me resulta más cómodo Ubuntu asi que me gustaría poner todo a punto para seguir usando esta distro... veremos que pasa en 10.10.

  Gracias!

---

### Post by canci_rc on 2010-10-19
gente buenas noticias! problema solucionado, actualize mi ubuntu 10.04 al 10.10 y se corrigio el problema del parapadeo. comprobado por una semana de uso y corriendo peliculas full hd. tambien ahora me reconoce las teclas de subir y bajar el brillo de la pantalla. les comento que la actualizacion no me modifico casi nada en cuanto a configuracion y funcionamiento de programas. les recuerdo que el modelo de mi note es lenovo g450 con video intel corporation mobile 4 series chipset integrated graphics controller, habra q probar si lo soluciona en otros modelos de ntoebooks. les paso el link de donde saque como activar la actualizacion a la version 10.10 ya que no aparece sola [URL="http://ubuntulife.wordpress.com/2010/10/10/actualizar-de-ubuntu-10-04-a-ubuntu-10-10-maverick-meerkat/"]http://ubuntulife.wordpress.com/2010/10/10/actualizar-de-ubuntu-10-04-a-ubuntu-10-10-maverick-meerkat/ 
[/URL]

---

### Post by dvpe on 2010-10-20
Hola chicos.
Siento deciros que yo tenía el mismo problema, actualicé incluso a la 10.10 y todo parecía ir de maravilla... estaba encantadísimo cuando de repente vuelve a suceder el famoso parpadeo que parece que hay 10 moviles cerca.
Lo que más me molesta es que no consigo descubrir el patrón por el cual sucede.
Saludos y a ver si alguién lo soluciona.

---

### Post by jahrmando on 2010-10-20
Acerca del parpadeo de pantalla en la distro ubuntu he llegado a estas conclusiones. 

1. Sucede desde la versión Ubuntu 10.04
2. Sucede también en Debían 6 un-estable pero no en la 5
3. Los dos puntos distros anteriores generan parpadeo por que usan la version GNOME 2.30.2

Dos datos curiosos que probare con usar KDE y openSUSE con GNOME que al parecer no falla. Para descartar posible bug de GNOME en caso contrario seria bug de GNOME 2.30.2

---

### Post by guillermolisi on 2010-10-21
> **jahrmando said:**
> Acerca del parpadeo de pantalla en la distro ubuntu he llegado a estas conclusiones. 

1. Sucede desde la versión Ubuntu 10.04
2. Sucede también en Debían 6 un-estable pero no en la 5
3. Los dos puntos distros anteriores generan parpadeo por que usan la version GNOME 2.30.2

Dos datos curiosos que probare con usar KDE y openSUSE con GNOME que al parecer no falla. Para descartar posible bug de GNOME en caso contrario seria bug de GNOME 2.30.2

Tambien me fijaria en que version de kernel y X-server se usan en cada caso porque normalmente es lo que mas impacto tiene respecto de cuestiones de video.

---

### Post by guillermon on 2010-10-22
Ah... me ilusioné por unos segundos de que con kde dejaría el parpadeo. Mi experiencia desde hace un par de meses (que tengo una lenovo g550) es que han disminuido los parpadeos a medida que han ido cambiando los kernels. Prácticamente no los hace; cuando abro openoffice, seguro alguno ocurre! (o ya me acostumbre??!)...
 Los botones de función andan bien, salvo el del brillo (en otro post mencionan que no puede bloquear el mouse pad).
    Canci_rc solucionó el problema al actualizar, pero con una lenovo g450.La actualización de dvpe no solucionó; me resultaría interesante saber de qué modelo, y si realiza las actualizaciones normales... Espero la respuesta, gracias y saludos

---

### Post by canci_rc on 2010-10-25
bueno les comento que despues de un mes de uso no he vuuelto a ver ningun parpadeo, ni ningun inconveniente. En cuanto a las actualizaciones andan perfecto ya lo he actualizado varias veces, incluso actualize el kernel y nigun problema. Me reconoce TODAS las teclas, hasta ahora la 10.10 esta de 10...

---

### Post by guillermon on 2010-11-07
> **canci_rc said:**
> bueno les comento que despues de un mes de uso no he vuuelto a ver ningun parpadeo, ni ningun inconveniente. En cuanto a las actualizaciones andan perfecto ya lo he actualizado varias veces, incluso actualize el kernel y nigun problema. Me reconoce TODAS las teclas, hasta ahora la 10.10 esta de 10...
Bueno, Canci, a partir de tu experiencia entonces el problema es con el modelo g550 (y no con el g450, que es el que tu tienes). Si alguien ha encontrado hecho alguna experiencia al respecto, por favor que avise... Gracias

---

### Post by elkilian on 2010-11-10
a mi me parpadea con ubuntu y kubuntu 10.10
tengo un pc con una tajeta ati radeaon 1300

con opensuse parece q va bien

---

### Post by edisonr430 on 2010-12-18
Hola a todos

De casualidad llegué a este foro y me di cuenta que compartimos el mismo problema, aunque con una notebook diferente. Anteriormente había hecho la misma consulta en [http://www.chilecomparte.cl/index.php?showtopic=1265702](http://www.chilecomparte.cl/index.php?showtopic=1265702) pero tampoco me dio resultado. 

Poseo una notebook samsung NP-R430-JA02CL con Tarjeta de video Intel GMA 4500M (Int. Graphic). Según veo, pudiera ser también que el problema su produjera con las tarjetas integradas intel, aunque tampoco puedo decir esto a ciencia cierta. 

Probé la versión 10.10 y si bien ya no lanzaba los parpadeos horizontales, al parecer pegaba unos chispazos en la parte superior de las ventanas de vez en cuando. De todas maneras era mejor esta última interrupción que la del 10.04. Volví nuevamente a la 10.04 porque los videos se me veían mejor acá. 

Según leí en otra parte, las gráficas en 10.04 las maneja automáticamente el kernel, así que tengo la esperanza que futuras actualizaciones recojan este problema. 

En fin, el mismo problema no sólo para las Lenovo. 

Saludos

---

### Post by Fer1987 on 2011-01-04
Hola amigos del foro!!! Bueno les cuento mi experiencia.
Tengo una notebook Lenovo G550, donde por las dudas aclaro que tiene un microprocesador Intel Pentium Dual-Core T4500 de 2.3 GHz con 2 GB de RAM. Tenía instalado un Ubuntu 10.04, donde compartí el mismo problema que todos ustedes del maldito parpadeo como si recibiera interferencias constantes sin un posible patrón.
Un grave error de mi parte fue no interiorizarme acerca del microprocesador que poseo, ya que hice la presuposición que era de 32 bits. Luego, investigando en la página del fabricante me doy cuenta que la arquitectura de este microprocesador es de 64 bits.
En este punto, y leyendo en el foro que algunas personas con otros modelos de notebooks solucionaron el problema actualizando a Ubuntu 10.10, se me dió por migrar a la versión 10.10. Obviamente, esta vez descargué Ubuntu 10.10 de 64 bits.
La verdad es que no sé si la arquitectura afecta o no, y de ser así, no se en qué medida (si alguien puede informarme de esto agradezco). El tema es que llevo casi 1 semana y media con esta versión instalada y adiós parpadeo. No les quepan dudas que si en las próximas semanas vuelvo a notar algo de este estilo les estaré informando.
Gracias a todos por la ayuda brindada en el foro.
Saludos.

---

### Post by guillermon on 2011-01-10
> **Fer1987 said:**
> Hola amigos del foro!!! Bueno les cuento mi experiencia.
Tengo una notebook Lenovo G550, donde por las dudas aclaro que tiene un microprocesador Intel Pentium Dual-Core T4500 de 2.3 GHz con 2 GB de RAM.  Obviamente, esta vez descargué Ubuntu 10.10 de 64 bits.
La verdad es que no sé si la arquitectura afecta o no, y de ser así, no se en qué medida (si alguien puede informarme de esto agradezco). El tema es que llevo casi 1 semana y media con esta versión instalada y adiós parpadeo. No les quepan dudas que si en las próximas semanas vuelvo a notar algo de este estilo les estaré informando.
Gracias a todos por la ayuda brindada en el foro.
Saludos.
Hola Fer, que importante descubrimiento. Estoy sorprendido. Es cierto lo de 64 bits. Pero seguramente lo interesante es que se haya solucionado (porque yo he tenido pc de escritorio de 64 bits usadas con sistema de 32 y nunca tuve problema). Es por eso que te pido que confirmes esta situación... estaré agradecido.
Por la dudas, ¿estás seguro que no se debe a haber pasado de la versión 10.04 a 10.10 (y no de 32 a 64 bits)?
Espero tu respuesta... gracias!

---

### Post by Fer1987 on 2011-01-11
> **guillermon said:**
> Hola Fer, que importante descubrimiento. Estoy sorprendido. Es cierto lo de 64 bits. Pero seguramente lo interesante es que se haya solucionado (porque yo he tenido pc de escritorio de 64 bits usadas con sistema de 32 y nunca tuve problema). Es por eso que te pido que confirmes esta situación... estaré agradecido.
Por la dudas, ¿estás seguro que no se debe a haber pasado de la versión 10.04 a 10.10 (y no de 32 a 64 bits)?
Espero tu respuesta... gracias!

Hola Guillermo.
Antes de dar con este foro, he leído que con la actualización a la versión 10.10 no fue suficiente. Incluso, en este mismo foro, "dvpe" posteó lo siguiente:

> Hola chicos.
Siento deciros que yo tenía el mismo problema, actualicé incluso a la  10.10 y todo parecía ir de maravilla... estaba encantadísimo cuando de  repente vuelve a suceder el famoso parpadeo que parece que hay 10 moviles cerca.
Lo que más me molesta es que no consigo descubrir el patrón por el cual sucede.
Saludos y a ver si alguién lo soluciona.Habría que ver qué máquina posee "dvpe" (si podés especificar te agradecemos).
Por esta razón, no me atrevo a asegurar que la "falta" de parpadeo sea únicamente por la actualización de la versión. Por otro lado, es cierto que un sistema operativo de 32 bits puede tranquilamente ser instalado en una máquina con un micro de 64 bits. Pero sigo prefiriendo instalar un sistema operativo de 64 bits para aprovechar al máximo la capacidad del micro.
Me gustaría saber si ya te habías dado cuenta de esta característica del micro o si lo descubriste en estos días.
Espero que sea de utilidad la información. Si llego a experimentar lo mismo que "dvpe" lo postearé.
Saludos.

---

### Post by Fer1987 on 2011-01-11
Me olvidé de comentar que también ya me andan las funcionalidades de brillo que no me andaban con la versión 10.04.
Saludos.

---

### Post by guillermolisi on 2011-01-11
> **Fer1987 said:**
> .... Pero sigo prefiriendo instalar un sistema operativo de 64 bits para aprovechar al máximo la capacidad del micro.
Saludos.
Y cual seria esa capacidad que queres aprovechar al maximo de un procesador de 64 bits ?

Mi pregunta no es para iniciar un flame sino para conocer caracteristicas de los sistemas de 64 bits que tal vez este pasando por alto (y perdiendome algo realmente bueno al seguir usando sistemas de 32 bits).

---

### Post by juancarlospaco on 2011-01-11
Del micro puntualmente nada, 
con 64bit se puede tener mas RAM usable y que siga funcionando despues del año 2038.

---

### Post by Fer1987 on 2011-01-12
> **juancarlospaco said:**
> Del micro puntualmente nada, 
con 64bit se puede tener mas RAM usable y que siga funcionando despues del año 2038.

Bueno, voy a responder de la misma forma que respondí el mail anterior, es decir, "contando mi experiencia"... jeje. Estuve conversando con la gente de Sistemas del lugar donde trabajo, ya que se encuentran en la misma oficina que nosotros, pero en un box distinto. Varios tópicos los "googlié" y encontré ciertas verdades.
En primer lugar, digo algo personal. Me gustaría decir que si la única ventaja de tener un microprocesador de 64 bits fuera que se puede extender la capacidad de la memoria RAM más allá de los 4 GB, estamos fritos!!! El solo sentido común nos dice que debe haber algo más aparte de eso.
Una de las primeras cosas que me comentaron, y que luego encontré en la web, es que con los microprocesadores de 64 bits se introduce el bit NX (No eXecute) que actúa sobre el subdesbordamiento de buffer (buffer underrun). Esto del buffer underrun les sugiero que lo lean del Wikipedia como para tener una idea de qué se trata y de sus efectos (en algunos casos serios), pero de la versión en Inglés. Esto solo les sugiero porque leí la versión en español y me pareció que la traducción está un poco incompleta.
Otra de las cosas a tener en cuenta y que me pareció vital es lo siguiente. Si el microprocesador es de 64 bits y el Sistema Operativo es de 64 bits, una aplicación desarrollada para 64 bits correrá de maravilla (es cierto que no todas las aplicaciones de uso común están desarroladas para ambos casos, 32 y 64). Pero aquí viene lo interesante de los microprocesadores de 64 bits con un apropiado Sistema Operativo de 64 bits, y es que se mejora la ejecución de aplicaciones de 32 bits. Esto va en contra de lo que muchos han posteado acerca de que una aplicación de 32 bits corre igual en un Sistema Operativo de 32 o de 64 bits. Según lo que estuve leyendo, si una aplicación es de 32 bits, correrá a 32 bits si el Sistema Operativo es de 32 bits (sin importar si el microprocesador es de 64 bits). Mientras que si el Sistema Operativo es de 64 bits y el microprocesador también lo es, se mejora la ejecución de las aplicaciones de 32 bits. Lamentablemente, están las 2 versiones, y estaría bueno que sigamos buscando información de fuentes confiables referido a esto. Pero obviamente, si contamos con un microprocesador de 64 bits y con un SO de 64 bits, debemos intentar conseguir la aplicación de 64 bits.
Por otra parte, se mejora la capacidad de una transferencia de datos, ya que se permite más información procesada por ciclo, SIEMPRE Y CUANDO EL SISTEMA OPERATIVO TAMBIÉN SEA DE 64 BITS. En caso contrario, lo limita a 32 bits por ciclo. Esto es muy perceptible si se lo piensa bien, ya que es mayor cantidad de datos procesados por cada ciclo de clock. De nuevo, sentido común.
Sin embargo, en varios foros leí que el principal problema de los Sistemas Operativos de 64 bits es la falta de drivers compatibles. Pero también así, he leído gente que dijo "Yo nunca tuve problemas con los drivers", y tanto gente que utiliza Linux como gente que utiliza ese Sistema Operativo prehistórico. En este punto, se los dejo a su elección. Yo me sitúo en el grupo de gente que dijo "Yo nunca tuve problemas de compatibilidad de drivers" (por lo menos hasta ahora).
Bueno gente, estaría bueno que creemos otro foro aparte para esta cuestión. Volviendo a nuestro foro "Problema parpadeo pantalla Ubuntu 10.04", les comento que sigo sin tener problemas de parpadeo en la pantalla. Esto es lo que YO particularmente estoy experimentando. Mi Ubuntu10.10 de 64 bits me anda de maravilla en mi lenovo G550 (por lo menos hasta ahora). De nuevo, cualquier inconveniente lo postearé.
Saludos.

> **guillermon said:**
> Hola Fer, que importante descubrimiento. Estoy sorprendido. Es cierto lo de 64 bits.

¿Ya sabías que tu microprocesador es de 64 bits? ¿O lo descubriste recientemente?

---

### Post by guillermon on 2011-01-13
Hola Fer, interesante todo lo que has descripto... muy completo. Respondiendo a tu pregunta, no sabía lo del procesador; lo confirmé cuando leí tu post. 
   Lo que me quedo pensando es que queda todavía un cabo suelto: no sabemos si ubuntu 10.04 de 64 bits andará sin problemas.... ¿? Particularmente prefiero instalar 10.04, por LTS... Toda la lógica diría que sí... pero esa doña lógica a veces es media guacha... ¿qué opinas?
   Muchas gracias por tus datos!

PD: genial que te ande la función del brillo!!!

---

### Post by Fer1987 on 2011-01-15
Hola Guille.
La verdad, me parecen interesante las 2 cosas. En primer lugar, estaría bueno que pruebes Ubuntu 10.04 de 64 bits y nos comentes cómo anda esa versión con el parpadeo. Y en segundo lugar, me parece importante priorizar la versión con soporte. Espero tus comentarios.
Saludos.

---

### Post by jalesan on 2011-02-05
buenas tardes a todos!! Tengo una lenovo g450 y con el mismo problema que todos uds. Queria consultar a [canci_rc]("http://ubuntuforums.org/member.php?u=1158330") si instalo la version de 32 bits o la de 64 cuando actualizo a 10.10.
Por otro lado, porque la version de 64bits hace referencia a amd en el nombre del archivo a descargar? Es decir, la misma se llama ubuntu-10.10-desktop-amd64.iso mientras que la de 32 bits es ubuntu-10.04.1-desktop-i386.iso

Espero que me puedan orientar y desde ya muchas gracias!!
Saludos
JP

---

### Post by guillermolisi on 2011-02-05
ubuntu-10.10-desktop-amd64 es la denominacion generica para los sistemas de 64 bits con arquitectura Intel (IA-64). Vale tanto para procesadores Intel como AMD de 64 bits (o cualquiera que adhiera a la arquitectura Intel).

---

### Post by alfplayer on 2011-02-05
> **guillermolisi said:**
> ubuntu-10.10-desktop-amd64 es la denominacion generica para los sistemas de 64 bits con arquitectura Intel (IA-64). Vale tanto para procesadores Intel como AMD de 64 bits (o cualquiera que adhiera a la arquitectura Intel).

Una pequeña corrección: la forma corta IA-64 refiere a Itanium, que no es la arquitectura de las PC conocidas por todos, como la típica PC para el hogar, notebook u oficina. Para ver nombres equivalentes a amd64 se puede ver [http://es.wikipedia.org/wiki/X86-64]("http://es.wikipedia.org/wiki/X86-64").

Saludos.

---

### Post by guillermolisi on 2011-02-06
Cierto. Gracias por la aclaracion de la forma que en realidad quise usar para referirme a la arquitectura legacy.

Interesante lo de IA-64 que corre 32 bits en un procesador aparte.

---

### Post by guillermon on 2011-08-01
Hola, revivo el tema por lo siguiente: iba a reinstalar a 64 bits para solucionar el problema del parpadeo, pero no lo hice hasta terminar un trabajo importante en la pc. Pero resulta que ha dejado de hacerlo, a medida que se han ido actualizando los kernels; ahora, también he actualizado a 10.10 (quería probar Unity, lo cual fué un fracaso porque no puedo modificar nada, con la actualización está muy básico). 
Ahora bien, estoy en duda sobre qué hacer, pues:
-Si reinstalo 10.04  (32 bits) no habrá más parpadeos?
-Instalo -limpio- 11.04 (¿¿¿32 o 64 bits??) y pierdo el LTS?
-Actualizo a 11.04 para disfrutar de Unity?
-Me paso a Windows? (o me tiro por la ventana?)

En fin... Aprovecho para enviar saludos, y gracias desde ya

Guillermo

---

### Post by guillermolisi on 2011-08-01
Proba con un LiveCD de 11.04 y si no hay problemas, actualiza a esa version.

Igualmente con la 10.04 tenes soporte para rato y si no hay una genuina necesidad de actualizar, mantene lo que tenes que ahora funciona bien (haciendo honores al dicho "Si funciona bien, no lo toques").

---

