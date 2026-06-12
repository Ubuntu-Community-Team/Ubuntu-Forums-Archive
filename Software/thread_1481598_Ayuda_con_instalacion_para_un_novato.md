---
title: "Ayuda con instalacion para un novato"
date: 2010-05-12
forum: Software
---

### Post by Torals on 2010-05-12
Buenas a todos.

Necesito un poco de ayuda para la instalacion con ubuntu, soy nuevo en el tema y no quiero tocar nada de mas que me perjudique.

Tengo la pc con un disco particionado en dos. En el disco C tengo windows XP mientras que en el D solo lo tengo para guardar archivos.

Instale Ubuntu desde el menu del CD como un programa mas en el disco D, pensando que de esa manera al iniciar la pc me preguntara con cual SO quiero ingresar, pero eso no paso.

Asi que si alguien me puede dar un tutorial o decirme como hacer para que me de la opcion de elegir entre windows y ubuntu, le agradeceria.

En lo posible, me gustaria no tener que tocar las particiones manualmente.

Saludos y gracias

---

### Post by spydeyrch on 2010-05-12
Bienvendio al foro.

Antes de poder ayudarte, me gustaria preguntarte cuales son los componentes principales de tu PC.

CPU
Tarjeta de Video
Memoria (RAM)
Disco Duro
Disco Optico

Tambien me parece que instalaste ubuntu atraves del WUBI. Me podrias verificar eso por favor? Gracias.

-Spydey :guitar:

---

### Post by Torals on 2010-05-12
Gracias por la bienvenida.

No se lo que es el WUBI :P .... lo instale desde el menu del CD, como un programa mas dentro de windows en el disco D.

Mi PC es 
Core 2 Duo E5500.
2 Gb de Ram
Disco de 160 (Partido en dos partes C: de 50 D: de 110 ... aprox)
Video Gforce 8500 GT de 512 Mb.
Unidad lectograbadora de CD otra de DVD
Todo con Windows XP SP3

PD: Si todo sale bien con ubuntu (que espero que si por que estoy realmente cansado de windows), me van a ver seguido por el foro hasta que este un poco mas versado en el tema.

Gracias!

---

### Post by spydeyrch on 2010-05-12
> **Torals said:**
> Gracias por la bienvenida.
No se lo que es el WUBI :P .... lo instale desde el menu del CD, como un programa mas dentro de windows en el disco D.


Asi que si te entiendo bien, estabas en windows, ingresaste el disco de ubuntu, aparecio un menu de ubuntu y en ese menu, escojiste la opcion de instalarlo dentro de windows, como un programa normal. Fue asi?

Esa opcion de instalarlo dentro de windows es algo que se llama WUBI. Te da la oportunidad de probar ubuntu, si es que todo sale bien. En el caso tuyo, parece que no todo salio bien. :(

Tambien, aunque todo salga bien, por razon de que ubuntu esta instalado dentro de windows, si por alguna razon falla windows, no tentrias acseso al ubuntu.

Asi que tienes dos opciones:

Instalarlo con WUBI

o

Instalarlo en una configuracion de "dual boot" (lo siento por el termino en ingles, no se cual seria la traducion adecuada en espanol.  :confused:)

Independientement de la opcion que escojas, necesitamos arreglar la instalacion actual. Cuando instalaste ubuntu por el WUBI, WUBI debia haber puesto una opcion para iniciar ubuntu o windows. pero por lo que me dices, parece que esa opcion no existe y solo se inicia windows automaticamente. Es cierto asi?

-Spydey :guitar:

---

### Post by spydeyrch on 2010-05-12
Si solo quieres probar ubuntu, entonces wubi es la opcion para ti. En el fin, si no te gusta, lo desinstalas como un programa normal de windows y ya, todo bien.

Pero, si piensas que vas a usar ubuntu mas que windows y que poco a poco vas a dejar windows, entonces que recomiendo que intentes hace un dual boot. Lo podriamos llamar al "dual boot" sistema doble, esta bien asi?

-Spydey :guitar:

---

### Post by Torals on 2010-05-12
> **spydeyrch said:**
> Asi que si te entiendo bien, estabas en windows, ingresaste el disco de ubuntu, aparecio un menu de ubuntu y en ese menu, escojiste la opcion de instalarlo dentro de windows, como un programa normal. Fue asi?

Esa opcion de instalarlo dentro de windows es algo que se llama WUBI. Te da la oportunidad de probar ubuntu, si es que todo sale bien. En el caso tuyo, parece que no todo salio bien. :(

Tambien, aunque todo salga bien, por razon de que ubuntu esta instalado dentro de windows, si por alguna razon falla windows, no tentrias acseso al ubuntu.

Asi que tienes dos opciones:

Instalarlo con WUBI

o

Instalarlo en una configuracion de "dual boot" (lo siento por el termino en ingles, no se cual seria la traducion adecuada en espanol.  :confused:)

Independientement de la opcion que escojas, necesitamos arreglar la instalacion actual. Cuando instalaste ubuntu por el WUBI, WUBI debia haber puesto una opcion para iniciar ubuntu o windows. pero por lo que me dices, parece que esa opcion no existe y solo se inicia windows automaticamente. Es cierto asi?

-Spydey :guitar:

A Ubuntu lo estuve probando booteando desde el CD, por eso me decidi a instalarlo. El tema es que elegir "Instalar dentro de windows" (o algo asi) pensando que me iba a dar la opcion de que la pc bootee con ubuntu, evidentemente no fue asi.

En la instalacion, nunca me dio la opcion para iniciar con ubuntu.... se instalo como un programa mas ..... ya lo desinstale.

> **spydeyrch said:**
> Si solo quieres probar ubuntu, entonces wubi es la opcion para ti. En el fin, si no te gusta, lo desinstalas como un programa normal de windows y ya, todo bien.

Pero, si piensas que vas a usar ubuntu mas que windows y que poco a poco vas a dejar windows, entonces que recomiendo que intentes hace un dual boot. Lo podriamos llamar al "dual boot" sistema doble, esta bien asi?

-Spydey :guitar:

Si, mi idea es que a medida que conozca mas a fondo Ubuntu (lamentablemente soy un hijo de windows, es lo que siempre tuve), la idea es que finalmente lo reemplace totalmente a windows, por eso queria la opcion de doble boot.

Ahora, chusmeando el foro vi un tutorial con sticky sobre como instalar con dual boot, pero me surgio una duda.

Si yo quiero instalarla en la particion "D" (siendo que en "C" tengo windows), cuando se inicie la PC, no me va a leer la primer particion de windows o me va a dar a elegir entre los dos SO?

Por que sino, me quedaria la opcion de instalarlo en la misma particion de windows o de tocar la bios para que botee desde D

Encima de este tema medio que toco de oido por que no soy muy versado en estos temas, voy aprendiendo en base a mocos que me suelo mandar :P

Gracias!

---

### Post by spydeyrch on 2010-05-13
> **Torals said:**
> A Ubuntu lo estuve probando booteando desde el CD, por eso me decidi a instalarlo. El tema es que elegir "Instalar dentro de windows" (o algo asi) pensando que me iba a dar la opcion de que la pc bootee con ubuntu, evidentemente no fue asi.

En la instalacion, nunca me dio la opcion para iniciar con ubuntu.... se instalo como un programa mas ..... ya lo desinstale.


Si. Normalmente cuando instalas ubuntu dentro de windows, debe de poner una opcion en el menu de windows (que normalmente no se ve). Entonces verias dos opciones: la primera para iniciar windows y la segunda para iniciar ubuntu. Desafortunadamente, parece que no se instalo correctamente en tu caso. Pero ya lo desinstalaste, que bueno.

> **Torals said:**
> 
Si, mi idea es que a medida que conozca mas a fondo Ubuntu (lamentablemente soy un hijo de windows, es lo que siempre tuve), la idea es que finalmente lo reemplace totalmente a windows, por eso queria la opcion de doble boot.

Ahora, chusmeando el foro vi un tutorial con sticky sobre como instalar con dual boot, pero me surgio una duda.

Si yo quiero instalarla en la particion "D" (siendo que en "C" tengo windows), cuando se inicie la PC, no me va a leer la primer particion de windows o me va a dar a elegir entre los dos SO?

Por que sino, me quedaria la opcion de instalarlo en la misma particion de windows o de tocar la bios para que botee desde D

Encima de este tema medio que toco de oido por que no soy muy versado en estos temas, voy aprendiendo en base a mocos que me suelo mandar :P

Gracias!

Si vas a hacer un doble boot, esto es basicamente lo que tendras que hacer. Ahora, te recomiendo que lo leas varias veces para entenderlo y saber cuales son los pasos necesarios. Tambien, no es un guia digamos, muy afondo. Eso uno basico que esoty haciendo ahorita misma. Asi que, antes de hacerlo, pregunta si tienes preguntas. Sale?

Esto es lo que yo haria en tu caso:

1.) Haria un respaldo de todos mis archivos.
2.) Defragmentaria el disco D:\
3.) Bajaria GParted del internet y quemarlo a un CD.
4.) Iniciaria el PC con el disco del GParted ingresado y bootearia mi sistema del disco que contiene GParted.

GParted, por si acaso no sabes, te permitira cambiar las particiones de los discos.

5.) Usando GParted, minimizaria la particion del disco D:\ a una cantidad aceptable para los archivos.
6.) Usando GParted, crearia una tercera particion, usando el espacio que queda in el disco D:\.

Por ejemplo - Tendrias: el disco C:\ una sola particion que contiene Windows. el disco D:\ dos particiones - una que contiene tus archivos, la otra sera usada para la instalacion de ubuntu

7.) Iniciaria el sistema con el disco de ubuntu adentro del PC y bootearia el PC del disco de ubuntu.
8.) En lugar de usar el CD para probar ubuntu, selecciona instalarlo.
9.) sigue las instrucciones para instalarlo y cuando llegues al paso para seleccionar donde instalarlo, seleciona la tercera particion que habias creado anteriormente. Y deja que GRUB se instala solo y automaticamente.

Eso debe de permitirte instalar y usar ubuntu en una configuracion doble boot.

Espero que mis instrucciones hayan sido claras. El espanol no es mi primer idioma. Soy de los estados unidos. Asi que si tienes alguna pregunta o duda, con confianza, pregunta.

-Spydey:guitar:

---

### Post by Torals on 2010-05-13
Esta perfecto amigo, entendi bien la guia... el fin de semana lo hago y te comento como salio. 
 
Lo que si, me quedo una duda... (si es que se le puede llamar asi): Yo no tengo dos discos duros distintos, era uno solo de 160 Gb y yo lo particione en una de las tantas formateadas que hice para tener el C con windows y el D con otras cosas, asi no tenia que hacer backup de todo el disco cuando necesitaba formatear windows por sus tantos problemas que trae.
 
Entonces, si hago esa particion del D que me aconsejas, seria lo mismo? quedaria el mismo disco duro dividido en tres.
 
Y en todo caso, cuanto espacio de disco me aconsejas para dejarle a Ubuntu?
 
Por todo lo demas, entendi perfectamente
 
Muchas gracias.
 
PD: Alguno sabe donde puedo bajarme algun manualcito completo de linux para novatos como yo, donde explique que son los scripts, como se instalan.... como instalar programas que se bajan como extension .bin (eso me perdio feo cuando lo vi), el uso de la consola, etc?

---

### Post by guidito73 on 2010-05-13
> **Torals said:**
> Esta perfecto amigo, entendi bien la guia... el fin de semana lo hago y te comento como salio. 
 
Lo que si, me quedo una duda... (si es que se le puede llamar asi): Yo no tengo dos discos duros distintos, era uno solo de 160 Gb y yo lo particione en una de las tantas formateadas que hice para tener el C con windows y el D con otras cosas, asi no tenia que hacer backup de todo el disco cuando necesitaba formatear windows por sus tantos problemas que trae.
 
Entonces, si hago esa particion del D que me aconsejas, seria lo mismo? quedaria el mismo disco duro dividido en tres.
 
Y en todo caso, cuanto espacio de disco me aconsejas para dejarle a Ubuntu?
 
Por todo lo demas, entendi perfectamente
 
Muchas gracias.
 
PD: Alguno sabe donde puedo bajarme algun manualcito completo de linux para novatos como yo, donde explique que son los scripts, como se instalan.... como instalar programas que se bajan como extension .bin (eso me perdio feo cuando lo vi), el uso de la consola, etc?

Buenas, voy a responder algunas de tus preguntas :)

En cuanto al espacio en el disco, te comento... Hay algo que no mencionaron en el post anterior, y es el sistema de particionado de Ubuntu. La regla general, y lo recomendado, es hacer 3 particiones.

Una se llama Root (o más conocida como / simplemente), donde van todos los archivos del sistema operativo, además de los programas instalados y a instalar. Sería el núcleo duro del sistema, digamos. Dependiendo de la cantidad de programas que vayas a instalar, paquetes, etc, el tamaño óptimo yo diría sería entre 10 y 15 GB (yo por lo menos nunca usé más de eso).

La otra, también muy importante, es /home. Aquí vas a guardar todos tus documentos, música, videos, etc: pero no sólo esto. Linux utiliza /home también para guardar TODAS las configuraciones de tus programas (véase perfiles de Firefox, de tu cliente de correo, configuraciones de apariencia del SO, TODO). El tamaño de tu /home va a depender de la cantidad de datos que vos quieras poner en él: es recomendable hacerlo lo bastante grande para alojar tus documentos, toda tu música y demás multimedia. (En mi caso es de 60 GB por ejemplo)

Cuál es la ventaja de particionar de esta forma el disco? Básicamente, que si tuvieses algún problema en el /, o si simplemente querés hacer una instalación limpia, mantendrías TODAS tus configuraciones tras la reinstalación del sistema operativo (no me digas que esto no te traía montones de dolores de cabeza en Windows XD). Esto es gracias a que podés mantener tu /home sin tocar y modificar únicamente el /.

Por último, es necesario crear un área de intercambio de la RAM, también llamada Swap. Con que sea de 1 GB es suficiente en tu caso.

En este caso, tanto / como /home van a usar el Sistema de Ficheros Transaccional EXT4. El área de intercambio se define en GParted y linux como tal, o a lo sumo, como SWAP.

En cuanto a tu última pregunta sobre manuales, scripts, etc, yo te diría que primero llegues a hacer una instalación y vayas consultando mucho en los foros y googleando, es la mejor forma. Una vez que estés familiarizado, podés empezar una búsqueda un poco más fina de lo que querés :)

Cualquier consulta, estamos a tu disposición!

---

### Post by spydeyrch on 2010-05-13
> **Torals said:**
> Esta perfecto amigo, entendi bien la guia... el fin de semana lo hago y te comento como salio. 

Me parece perfecto. Mantenme al pendiente de tus resultados, sale.

 
> Lo que si, me quedo una duda... (si es que se le puede llamar asi): Yo no tengo dos discos duros distintos, era uno solo de 160 Gb y yo lo particione en una de las tantas formateadas que hice para tener el C con windows y el D con otras cosas, asi no tenia que hacer backup de todo el disco cuando necesitaba formatear windows por sus tantos problemas que trae. 

Ok, ya entendi. Te explico lo de mas abajo. Sigue leyendo.
 
> Entonces, si hago esa particion del D que me aconsejas, seria lo mismo? quedaria el mismo disco duro dividido en tres.

Si, quedara el mismo disco dividido en tres particiones. Y esta bien asi. Si solo tienes un disco duro, pues, no nos queda de otro, verdad. jejeje :P
 
> Y en todo caso, cuanto espacio de disco me aconsejas para dejarle a Ubuntu?

Pues eso depende de unas cuantas cosas importantes. Dices que tienes un disco duro de solo 160GB, verdad? Cuanto espacio es la particion de Windows (el disco "C:\")? Y cuanto espacio toman los archivos en la particion de Windows?

Por ejemplo: La particion de windows es de, digamos, 80GB, pero los archivos solo toman 60GB de espacio. Asi que te quedan 20GB de espacio todavia en el disco "C:\".

Cuanto espacio toma la particion del disco "D:\"? Y cuanto espacio toman los archivos en el disco "D:\"?

Oye, solo para que sepas, aveces intercambio los terminos "primera particion" con "Disco C:\", es lo mismo. Y tambien "segunda particion" con "disco D:\", tambien es lo mismo. Y mas al rato, usare "tercera particion" con "Ubuntu", de igual, es lo mismo. 
 
> Por todo lo demas, entendi perfectamente
 
Muchas gracias.
 
PD: Alguno sabe donde puedo bajarme algun manualcito completo de linux para novatos como yo, donde explique que son los scripts, como se instalan.... como instalar programas que se bajan como extension .bin (eso me perdio feo cuando lo vi), el uso de la consola, etc?

De nada. :) La verdad, es la primera vez, que me acuerdo, que le he ayudado a una persona en espanol aqui en este foro. Creo que hay una seccion del foro para otros idiomas, pero no estoy seguro.

En cuanto a un manualcito, si se de varios pero todos estan escritos en ingles. No se si eso te ayudaria. Puedo buscar y si encuentro uno en espanol, pues te lo digo, sale.

-----------------

En cuanto al disco y las particiones, por razon de que es un solo disco distinto, yo haria esto:

1.) Haria un respaldo de mis archivos importantes: fotos, videos, documentos, etc. De los dos discos: "C:\" y "D:\".

2.) Defragmentaria los dos discos (las dos particiones). Usa el programa Defraggler. No se si tengan una version en espanol, lo siento.

3.) Usaria GParted para minimizar la segunda particion (pero depende de cuanto espacio queda sin usar en la segunda particion), el disco "D:\". 

4.) Usando el espacio que queda despues de minimizar la segunda particion, crearia la tercera particion, donde se instalara ubuntu. No debes de tocar la primera particion, el disco C:\, si es posible. Si se te hace necesario, pregunta primero, a menos que estes familiairzado con como funciona GParted.

5.) Instalaria Ubuntu en la tercera particion.

6.) Despues de que se haya instalado, cuando se reinicie la PC, veras un menu boot. Sera diferente al menu boot de windows. Ese menu se llama GRUB. Te mostrara varias opciones. La primera cosa que debes hacer es ver si la opcion de windows existe en el menu. Normalmente se encuentra hasta el fin del menu. Si esta alli, selecionalo y inicia windows. Necesitamos verificar que todavia funciona tu sistema de windows.

7.) Si windows se inicia bien, y puedes entrar en tu escritorio, perfecto. Verifica que todavia puedes ver la segunda particion y los archivos que deben estar alli. Lo que nos vas a poder ver es la tercera particion. Windows no tiene la habilidad de ver sistemas de archivos de ext3 o ext4.
 Si no se inicia bien o normal, asi como antes de empezar todo este rollo, entonces hazmelo saber porque tendriamos que arreglarlo. Normalmente no sale mal la instalacion del menu boot GRUB, pero aveces si, pero muy rara a la vez. :)

8.) Despues de que se inicia bien windows, reinicia la PC. Cuando aparezca el menu boot GRUB (de aqui en adelante, solo lo voy a llamer GRUB), seleciona Ubuntu. Debe de ser la primera opcion en la lista. Probablamente no se llamara solo "Ubuntu", sino algo como "Ubuntu, Linux 2.6.31-xx-generic" (los "xx" cambian cada vez que un nuveo kernel sale (lo siento, no se como se llama "kernel" en espanol))

9.) Al selecionar ubuntu, se debe de iniciar el SO de Ubuntu. :P

10.) De ahi en adelante, puedes usarlo a tu gusto. Te aconsejaria que instales "Ubuntu restricted", "Ubuntu Tweak", "System Info", y los controladores propitarios para los componentes de tu PC que los necesitan. Puedes instalarlos desde el menu sistema -> Administrar -> ??? (En ingles se llama "Hardware") el icono parece ser como una tarjeta circuito de una computadora, como si fuera una tarjeta de video. Algo asi. Espero que me explico.

11.) Tambien, despues de instalar los controladores de hardware, deberias actualizar el sistema. Aveces eso requiere que reinicies el SO, pero mas que nada no se necesita.

Dejame saber como te sale todo. Yo no voy a tener acseso a una computadora este fin de semana hasta el sabado en la noche. Me voy de excursion a las montanas. Espero que todo te salga bien. Suerte!

-Spydey

P.D. Oye, por curiosidad, de donde eres? :)

---

### Post by spydeyrch on 2010-05-13
> **guidito73 said:**
> Buenas, voy a responder algunas de tus preguntas :)

En cuanto al espacio en el disco, te comento... Hay algo que no mencionaron en el post anterior, y es el sistema de particionado de Ubuntu. La regla general, y lo recomendado, es hacer 3 particiones.

Una se llama Root (o más conocida como / simplemente), donde van todos los archivos del sistema operativo, además de los programas instalados y a instalar. Sería el núcleo duro del sistema, digamos. Dependiendo de la cantidad de programas que vayas a instalar, paquetes, etc, el tamaño óptimo yo diría sería entre 10 y 15 GB (yo por lo menos nunca usé más de eso).

La otra, también muy importante, es /home. Aquí vas a guardar todos tus documentos, música, videos, etc: pero no sólo esto. Linux utiliza /home también para guardar TODAS las configuraciones de tus programas (véase perfiles de Firefox, de tu cliente de correo, configuraciones de apariencia del SO, TODO). El tamaño de tu /home va a depender de la cantidad de datos que vos quieras poner en él: es recomendable hacerlo lo bastante grande para alojar tus documentos, toda tu música y demás multimedia. (En mi caso es de 60 GB por ejemplo)

Cuál es la ventaja de particionar de esta forma el disco? Básicamente, que si tuvieses algún problema en el /, o si simplemente querés hacer una instalación limpia, mantendrías TODAS tus configuraciones tras la reinstalación del sistema operativo (no me digas que esto no te traía montones de dolores de cabeza en Windows XD). Esto es gracias a que podés mantener tu /home sin tocar y modificar únicamente el /.

Por último, es necesario crear un área de intercambio de la RAM, también llamada Swap. Con que sea de 1 GB es suficiente en tu caso.

En este caso, tanto / como /home van a usar el Sistema de Ficheros Transaccional EXT4. El área de intercambio se define en GParted y linux como tal, o a lo sumo, como SWAP.

En cuanto a tu última pregunta sobre manuales, scripts, etc, yo te diría que primero llegues a hacer una instalación y vayas consultando mucho en los foros y googleando, es la mejor forma. Una vez que estés familiarizado, podés empezar una búsqueda un poco más fina de lo que querés :)

Cualquier consulta, estamos a tu disposición!

Estoy de acuerdo en cuanto a crear unas particiones separadas para el / y para /home. No te lo iba a mencionar porque aveces se confunden las personas cuando uno les menciona eso. Lo que yo hice las primeras veces que empzaba a usar linux fue crear una sola particion. Luego que me iba acostumbrando y entendiendo mas y mas, pues entonces hice una instalacion limpia y en eso hice las particiones / y /home separadas. Es tu decision como lo quieres hacer.  :)

En cuanto al espacio, tambien estoy de acuerdo a lo que dijo guidito. Pero tambien depende de cuanto tengas libre, no. :P
------
Yo estaba escribiendo mi ultima respuesta cuando guidito hizo la suya. jejejeje

Haznos saber si tienes alguna pregunta.

Y otra vez, lo siento si algunos terminos tecnicos no son correctos, hay varios terminos que apenas estoy aprendiendo. Asi que mas veces que nada, tengo que adivinar cual es el termino. jejejeje

-Spydey :guitar:

---

### Post by Torals on 2010-05-13
Nuevamente, muchas gracias por las respuestas. Es un verdadero gusto entrar a un foro y que se tomen parte de su tiempo en contestar algo completo y con respeto como lo hacen ustedes. Lamentablemente, en otros lugares que uno entra no recibe la misma respuesta.

He tomado nota sobre que es lo que tengo que hacer.

Por suerte tengo un HD portatil que uso para hacer backup de cosas en la PC, asi que ahi salvare lo mas importante que tengo en el disco D (es de 100 Gb.), para luego particionarlo segun vuestas indicaciones.

Entiendo la importancia de dividir en disco raiz / y disco /home, pero no se por que tengo el leve presentimiento que se me puede llegar a complicar.... entonces pregunto (una vez mas y van...) si no hago la division entre raiz-home-swap, e instalo todo en una sola particion exclusiva para ubuntu, no hay problema?

Por que en todo caso, es para seguir probando y acostumbrarme a linux, yo se que en algun momento voy a tomar la segura desicion de formatear todo con windows incluido y dejar solo ubuntu en mi pc.

Por cierto... soy de Cordoba, Argentina.

Saludos, y nuevamente gracias.

---

### Post by spydeyrch on 2010-05-13
> **Torals said:**
> Nuevamente, muchas gracias por las respuestas. Es un verdadero gusto entrar a un foro y que se tomen parte de su tiempo en contestar algo completo y con respeto como lo hacen ustedes. Lamentablemente, en otros lugares que uno entra no recibe la misma respuesta.

He tomado nota sobre que es lo que tengo que hacer.

Por suerte tengo un HD portatil que uso para hacer backup de cosas en la PC, asi que ahi salvare lo mas importante que tengo en el disco D (es de 100 Gb.), para luego particionarlo segun vuestas indicaciones.

Entiendo la importancia de dividir en disco raiz / y disco /home, pero no se por que tengo el leve presentimiento que se me puede llegar a complicar.... entonces pregunto (una vez mas y van...) si no hago la division entre raiz-home-swap, e instalo todo en una sola particion exclusiva para ubuntu, no hay problema?

Por que en todo caso, es para seguir probando y acostumbrarme a linux, yo se que en algun momento voy a tomar la segura desicion de formatear todo con windows incluido y dejar solo ubuntu en mi pc.

Por cierto... soy de Cordoba, Argentina.

Saludos, y nuevamente gracias.

Bueno, si no quieres tener que hacer la division entre raiz-home-swap manualmente, no lo tienes que hacer. Si dejas que ubnutu se instale solo, ubnutu creara las divisiones necesarias. Y no tendrias que hacer nada asi. Solo que no habra division entre / (raiz) y /home. /home estara bajo / (raiz). Me explico?

Asi lo he hecho muchas veces para probar ciertas cosas. Es mas facil pero tiene sus desventajas. Espero que eso te haya dado la respuesta que buscabas.  :)

-Spydey :guitar:

---

### Post by guidito73 on 2010-05-13
Claro, se puede hacer tranquilamente.

Pero te digo, no es nada difícil, los instaladores de Ubuntu han llegado a ser realmente fáciles. Yo lo hice la primera vez que lo instalaba :)

En fin, elijas el método que elijas, no te olvides de postear los resultados!

PD: También soy de Córdoba, cuando quieras salen unas birritas :P

---

### Post by Torals on 2010-05-15
Bueno aquí estoy de vuelta, luego de toda una mañana sorteando diversas situaciones que se me presentaron a la hora de instalar ubuntu.

Tal como me recomendaron, baje el gparted y lo queme en un cd para botearlo.

Previamente, hice backup de las dos particiones del disco duro, intuyendo lo que luego podía llegar a suceder. También desfragmente el disco.

Al hacer eso, inicie el sistema con gparted, mi intencion era dejar la unidad C intacta con su windows XP, mientras que a la particion D miniminzarla y hacer una tercera particion para ubuntu.

Por suerte el programa es en apariencia, facil de usar, asi que eso lo hice sin problemas, reservando aproximadamente 30 gb del disco D para ubuntu creando una particion ext4.

Hasta ahi, todo perfecto. Reinicie el sistema para ver si windows me cargaba.... pero nunca lo hizo, algo debi haber tocado cuando hice las particiones (no recuerdo que, pero estaba convencido de que no habia tocado la particion de windows).

Luego de varias reiniciadas para ver si me cargaba windows, y ante la realidad de que nunca iba a botear ese SO, volvi a ingresar con Gparted, elimine todas las particiones y cree las nuevas: "/" "/home" "/swap" y un sistema de archivos ntfs por las dudas nomas.

"/": 15 Gb.
"/Home": 30 Gb.
"Swap": 2.5 Gb
"NTFS": 100 Gb. <---- para este sistema de archivos me pedia una etiqueta al instalar ubuntu, asi que le puse "windows", no se si hice bien (me referire a esto mas abajo)

Luego, ingrese con el CD de ubuntu e instale el SO conforme las particiones que hice.Se instalo de lo mas bien, sin problema alguno.

La cosa es que ahora estoy solamente con ubuntu, algo perdido todavia pero de a poco le voy tomando la mano, seguramente no conzoco ni el 5% de las posibilidades que me va a dar este nuevo sistema, pero confio ir conociendolas a medida que pase el tiempo.

En cuanto al sistema de archivos ntfs que creé, la cual, como dije mas arriba me pidio una etiqueta y le puse "windows" no me aparece como una particion clasica, al menos comparada como te lo mostraba windows, donde veias dos discos duros (cuando tenia las dos particiones), sino que me aparece todo como un solo disco, en el mismo, hay una carpeta llamada "Windows" del tamaño de esa particion.

Eso me confundio un poco, la carpeta obviamente esta vacia, pero yo quisiera saber si el SO lo toma realmente como otra particion, es decir.. que si algun dia yo quiero eliminar ubuntu o simplemente reinstalarlo o lo que sea, me la va a dejar intacta.

No se si me explico mas o menos.

Bueno, basicamente eso es lo que me paso, y decidi, como les dije, dejar solamente ubuntu... por ahora estamos en "fase de prueba" con gran confianza de que quede definitivamente.

Muchas gracias a todos los que se molestaron en ayudarme con esto, fueron realmente de mucha ayuda. 

Ahora, me voy a poner a bucear en el foro para ver si voy encontrando cosas nuevas para probar.

Saludos

---

### Post by Torals on 2010-05-16
De paso hago otra nueva pregunta: No se que habre tocado que me desaparecio la barra de abajo de la pantalla, donde salen las ventanas abiertas y los iconos de "mostrar escritorio" y papelera

---

### Post by spydeyrch on 2010-05-16
Hola,

lo siento que ser perdio tu particion de windows. Espero que estes bien con eso, muchos se habrian enojado si hubieran perdido su SO windows.

Oye, dime si todavia necesitas ayuda con lo del barrito de abajo. Tambien, si quisieras un guia de como instalar ubuntu y windows juntos, te lo puedo proveer. :)

-Spydey :guitar:

---

### Post by Torals on 2010-05-16
> **spydeyrch said:**
> Hola,

lo siento que ser perdio tu particion de windows. Espero que estes bien con eso, muchos se habrian enojado si hubieran perdido su SO windows.

Oye, dime si todavia necesitas ayuda con lo del barrito de abajo. Tambien, si quisieras un guia de como instalar ubuntu y windows juntos, te lo puedo proveer. :)

-Spydey :guitar:

Lo de la barrita ya lo solucione, era una tontera en realidad.

No me molesto haber perdido windows, por que no perdi ningun dato importante. Lo tenia todo asegurado en un HD portatil.

Lo que si, aprovechandome de tu ofrecimiento, me gustaria saber, en caso que quiera hacerlo, como instalar windows teniendo ya ubuntu, en caso que quiera.

Esto es principalmente por el tema juegos... si bien no soy de ponerme a jugar por que estoy todo el dia trabajando y estudiando, a veces los fines de semana de descanso me gusta hacer un par de partiditos con el PES 10.

Como dije, tengo una particion que deje con sistema de archivos ntfs bajo la etiqueta "windows" (mas arriba lo explique creo)

Si booteo el sistema con un cd de windows, lo podre instalar ahi dejando intacto ubuntu?

Edit: Otra de las causas por las que quiero tener windows instalado, es por que tengo un programa de la facultad con el que estudio que no puedo instalar con wine.

Saludos

---

### Post by guillermolisi on 2010-05-16
Si instalas Win despues de haber instalado Ubuntu, el Grub te va a quedar mal, solo tendra informacion para Win porque no "reconoce" la existencia de otros sistemas en la misma maquina (que no sean MS, por lo menos).

Para usar esa aplicacion para el estudio, mi recomendacion es virtualizar Win con VirtualBox o equivalente. Si los juegos requieren aceleracion de video, entonces nada como correr Win en modo real (no virtualizado) para lo cual si se impone dual boot (si es que con Wine no funcionan adecuadamente, claro).

Si tenes mas de un disco tal vez sea una buena alternativa instalar Win en un disco distinto del cual contiene Ubuntu y elegirlo para iniciar a traves de las opciones de booting del BIOS. Asi descartas problemas con el Grub.

---

### Post by Torals on 2010-05-16
> **guillermolisi said:**
> Si instalas Win despues de haber instalado Ubuntu, el Grub te va a quedar mal, solo tendra informacion para Win porque no "reconoce" la existencia de otros sistemas en la misma maquina (que no sean MS, por lo menos).

Para usar esa aplicacion para el estudio, mi recomendacion es virtualizar Win con VirtualBox o equivalente. Si los juegos requieren aceleracion de video, entonces nada como correr Win en modo real (no virtualizado) para lo cual si se impone dual boot (si es que con Wine no funcionan adecuadamente, claro).

Si tenes mas de un disco tal vez sea una buena alternativa instalar Win en un disco distinto del cual contiene Ubuntu y elegirlo para iniciar a traves de las opciones de booting del BIOS. Asi descartas problemas con el Grub.

Lo que tengo es un disco con las siguientes particiones:

/
/home
/swap
ntfs (de 100 gb aprox)

Esas particiones las hice al instalar ubuntu.... podre instalar windows en la particion ntfs?

---

### Post by guillermolisi on 2010-05-16
> **Torals said:**
> Lo que tengo es un disco con las siguientes particiones:

/
/home
/swap
ntfs (de 100 gb aprox)

Esas particiones las hice al instalar ubuntu.... podre instalar windows en la particion ntfs?
Suponiendo que puedas, vas a tener problemas con el Grub ya que sobreescribira la MBR del disco rigido.

Cuando sucede esto, el Grub se puede reconstruir pero ya es una tarea mas.

---

### Post by guidito73 on 2010-05-16
Como dice Guille, reconstruir el Grub no es ninguna cosa difícil. Abundan los tutoriales por internet, sólo googlea "recuperar GRUB 2" y listo ;)

---

### Post by Torals on 2010-05-18
Ya logre que queden instalados los dos SO dandome la opcion con cual de los dos ingresar al inicio de la PC.
 
Muchas gracias por la ayuda de todos, la verdad mucha buena onda en el foro.
 
Asi que si quieren ponerle el "Solved" al titulo, haganlo nomas.
 
Saludos y ya me veran preguntando alguna otra cosita rara cuando se me presente alguna otra duda

---

### Post by alfplayer on 2010-05-18
> **Torals said:**
> Ya logre que queden instalados los dos SO dandome la opcion con cual de los dos ingresar al inicio de la PC.
 
Muchas gracias por la ayuda de todos, la verdad mucha buena onda en el foro.
 
Asi que si quieren ponerle el "Solved" al titulo, haganlo nomas.
 
Saludos y ya me veran preguntando alguna otra cosita rara cuando se me presente alguna otra duda

Tenés para marcarlo com *solved* en *Thread Tools*, el menú arriba del primer mensaje.

---

