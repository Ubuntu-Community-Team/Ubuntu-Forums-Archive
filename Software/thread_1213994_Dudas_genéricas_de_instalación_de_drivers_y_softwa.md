---
title: "Dudas genéricas de instalación de drivers y software [primer contacto]"
date: 2009-07-15
forum: Software
---

### Post by jukitx on 2009-07-15
Hola,
   
  Bueno, antes de nada aprovecho mi primer post para saludar a todo el mundo :)
   
  Antes de nada comentar que solo he trabajado con Windows con lo cual en el tema Linux estoy muy muy verde. A pesar de eso, en el pasado, ya hice algún intento con Linux (suse, redhat y otros) y al final acabé volviendo siempre a Windows porque nunca me acababa de aclarar con la instalación del hardware y el software que usaba habitualmente. El post será un poco largo porque quisiera ver si es posible aclararlo todo de una vez. Si no es posible repartiré las dudas en varios post y lo pondré en el sitio correspondiente sin problema. Sin embargo, creo que si me podéis aclarar todas las dudas que hay en este post puede ser útil a mucha gente que se encuentra en mi misma situación porque, a mi juicio, son las dudas que debe tener la mayoría de gente cuando se cambia de Windows a Linux.
   
  Bien, antes de nada quería comentar lo siguiente. Tengo una ISO creada de Windows Vista x64 y mi idea era la de instalar Ubuntu bien y luego crear una ISO para irlo usando eventualmente hasta que me acostumbre. De esta forma, cuando quiera cambiar de sistema operativo solo tengo que regenerar mi disco duro usando norton ghost. De momento prefiero no instalar los dos sistemas operativos de forma simultánea ya que tendría que hacer particiones.
   
  Actualmente ésta es la configuración del hardware de mi equipo:
   
  - Disco duro 500GB SATA con una sola partición primaria de todo el espacio para usar con el sistema operativo.
  - Disco duro de 1500GB SATA con una sola partición primaria para guardar datos y en formato NTFS. No deseo cambiar el sistema de ficheros de ésta partición por el momento.
  - Tarjeta grafica Asus Nvidia Geforce 9800GTX+ 
  - Tarjeta wifi USB con chipset realtek RTL8187L
  - Impresora multifunción con scanner Epson Stylus DX4850
  - Tarjeta de sonido Realtek integrada en placa base.
  - Tarjeta Ethernet Realtek integrada en placa base.
  - Placa Base Asus M3A78-EM. Dispone de VGA integrada pero no la uso ya que tengo una externa mejor.
  - Memoria 4GB DDR3-800MHz
  - Procesador AMD Phenom X4 9950 a 2.6GHz
  - Chipsets de placa base AMD 780G/SB700
  - Ubuntu 9.04 x64
   
  Bien antes nada, comentar que ya he instalado el Ubuntu pero al encontrarme con varios problemas de instalación de hardware he regenerado el Windows otra vez de modo que tendré que volver a instalar Ubuntu.
   
  A continuación planteo una duda de instalación de Ubuntu:
   
  1- Creo que hay que hacer como mínimo 2 particiones. Una para el SO y otra para el archivo de paginación para la memoria RAM. Así pues usaré el disco duro de 500GB para tal fin. Veo que hay varios sistemas de ficheros para formatear la partición del SO. Cuál es el mejor sistema de ficheros para Ubuntu? por qué es mejor? En la partición para la memoria RAM no me sale ningún sistema de ficheros, así que entiendo que solo hay uno. De qué tamaño tiene que ser la partición para RAM? El doble que el tamaño de mi RAM? o sea, 8GB? si pongo más es mejor? si pongo menos es peor? por qué?
   
  Una vez instalado el SO tengo que instalar los drivers. Comentar que vi que muchos drivers ya están pre-instalados sin embargo, tenía problemas con la tarjeta wifi y la tarjeta gráfica. De todas maneras lo que quería saber es como se instalan los drivers de forma general para saberlo para siempre y cada vez que me cambie el hardware no tenga problema. Además así podré poner drivers optimizados para cada cosa.
   
  Varias dudas acerca de los drivers en Linux:
   
  2- Puedo usar drivers de Windows vista x64 en Linux? De Windows vista x86 o Windows xp x86 en Linux? Tienen el mismo rendimiento que los de Linux x64 o x86 respectivamente? Si es posible hacerlo es algo muy complejo de hacer? 
   
  3- Si dispongo de drivers optimizados para Linux  pero no me especifica si son x64 o x86 puedo instalarlos indistintamente en Ubuntu x64? No es obligatorio que sean x64? Como puedo saber si un driver está optimizado para x64 o x86 en Linux? Obviamente supongo que lo ideal es que sean para Linux x64 para que sea lo más optimizado posible.
   
  4- A la hora de descargar drivers en la web del fabricante debo mirar para qué distribución de Linux son? Es decir, si pone Linux me vale tanto para Ubuntu, redhat, suse, etc.? Es que normalmente pone solo Linux y no menciona la distribución. Están igualmente optimizados?
   
  Algunas aclaraciones sobre los drivers que me he descargado:
   
  -  Dispongo de la última versión de drivers para la tarjeta grafica Nvidia optimizado para Linux x64
  - Dispongo de drivers para Linux pero no sé si son x64 o x86 de la web de Asus para los siguientes componentes: tarjeta de sonido integrada, tarjeta  Ethernet integrada y chipset de la placa base.
  - Dispongo de drivers para Linux pero no sé si son x64 o x86 de la web de realtek para la tarjeta wifi USB.
   
  5- Si no voy a usar la tarjeta grafica integrada, es necesario instalar los drivers para el chipset de la placa base? Ya sé que no es obligatorio, pero lo digo en el sentido de que el sistema tenga un mejor rendimiento. Comentar que en la web de AMD no he encontrado drivers para Linux específicamente para el chipset aunque sí para la tarjeta grafica integrada. Comentar que la grafica integrada esta dentro del mismo chipset para mi placa base, entonces de ahí la duda. En la web de Asus me salen drivers separados para Linux para la tarjeta grafica y para el chipset, por tanto debería instalar al menos el chipset no?
   
   
  Bueno, ahora voy al grano. 
   
  Dudas concretas para instalar la tarjeta grafica:
   
  Según la web de Nvidia me dice que para instalar el drivers tengo que seguir estos 3 pasos:
   
  ==================================================================
  Para descargar e instalar los controladores, siga estos pasos:
   
  PASO 1: Lea detenidamente la Licencia de software de NVIDIA.
   
  Es necesario aceptar esta licencia antes de descargar cualquier archivo.
   
  PASO 2: Descargue el archivo del controlador
  Descargue  - NVIDIA-Linux-x86_64-185.18.14-pkg2.run
   
  Usuarios de SuSE: leer las instrucciones de SuSE NVIDIA Installer HOWTO antes de descargar el controlador.
   
  PASO 3: Instale el controlador
  Escriba "sh NVIDIA-Linux-x86_64-185.18.14-pkg2.run" para instalar el controlador y modifique el archivo archivo de configuración de X server * según corresponda. Consulte el archivo README si necesita instrucciones más detalladas. 
  ====================================================================
   
  * X server que es esto??? 
   
  Bien, de entrada intento hacer doble clic encima del archivo "NVIDIA-Linux-x86_64-185.18.14-pkg2.run" para ver si es “auto-instalable”. Me sale error y me dice que tengo que iniciar sesión como Root. Luego intento hacer lo que dice en el paso 3, o sea, abro una consola y escribo el comando:
   
  "sh NVIDIA-Linux-x86_64-185.18.14-pkg2.run"
   
  Me sale error también, creo que es porque antes tengo que situarme previamente en el directorio donde está el archivo a ejecutar. Entonces, como se hace eso? Aunque preferiría saber cómo se instala esto sin tener que usar comandos. 
   
  6- Para instalar drivers o programas, debo crear una cuenta Root? Si lo hago sin crear una cuenta Root voy a tener problemas de éste tipo?
   
  7- Como se crea un cuenta Root de una forma rápida?
   
  Luego, para instalar la resta de componentes de hardware no veo ningún archivo que pueda ejecutar de modo que sea “auto-instalable”.
   
  8- Existe algún administrador de dispositivos para Linux? Es decir, yo selecciono la carpeta donde están los drivers y que estos se instalen solos sin que tenga que ponerme a teclear comandos.
   
  9- Si no hay administrador de dispositivos para Linux, que procedimiento GENERAL puedo usar para instalar cualquier componente de hardware sea cual sea. Es decir, lo que quiero es saber alguna forma de instalar hardware haciéndolo siempre igual y que no tenga que aprender un método especifico para cada dispositivo.
   
  10- Una vez tenga instalado todo el hardware, deberé configurar los programas que van a usar ese hardware o puedo usarlos directamente? Es decir, por ejemplo, el navegador firefox, el reproductor de música, etc.
   
  Bien, ahora algunas dudas sobre el sistema Ubuntu:
   
  11- existe algún aplicativo tipo “Windows update” que yo lo ejecute y pueda descargar actualizaciones criticas para la estabilidad del sistema? Me podéis dar la ruta de ese aplicativo para que lo ejecute de vez en cuando? Debo iniciar sesión como Root para hacerlo?
   
  12- me saldrán solo componentes del sistema operativo en el “Ubuntu update”? O también me saldrán programas generales? Por ejemplo, un reproductor de música, un visualizador de fotos, etc. Es fácil distinguirlo de la resta de componentes del sistema operativo? Es que me gustaría usar este aplicativo solo para actualizar el SO, luego, los programas que yo vaya a usar ya me los descargaré yo por mi cuenta. Pregunto esto porque me da miedo encontrarme con componentes que desconozco y que sean programas que no voy a usar y lo descargue e instale todo sin darme cuenta.
   
  12- qué es eso de compilar el núcleo del sistema? El kernel? Se hace con el “Ubuntu update”? o tengo que descargarlo de forma independiente? Hace falta instalarlo como Root? Sería el equivalente al service pack del Windows? Es mejor compilar el núcleo o reinstalar el sistema operativo completo con la última versión del kernel?
   
  13- en el tema del hardware el “Ubuntu update” detecta nuevos drivers? Es seguro que si yo tengo un hardware instalado descargado de la web del fabricante es aconsejable que me descargue el que me salga en el Ubuntu update? 
   
  14- Para instalar software general, los programas son  auto-instalables? O sea, es suficiente hacer doble clic encima del archivo descargado para instalarlo directamente y seguir los pasos? O depende del tipo de programa? 
   
  15- Cuando vaya a instalar un programa como elijo en qué ubicación del disco duro se va a instalar? O sea, en qué carpeta.
   
  16- Una vez instalado el SO en la barra de direcciones me salen cosas como /DEV y pero no me salen la dirección de las carpetas. Pero luego veo que si vas “medios de almacenamiento” (o algo así) entonces ya puedes ver el contenido del disco duro “normal”. Tenéis algún tipo de guía para que entienda un poco que son esas “direcciones”? son componentes de hardware del ordenador? O son componentes del sistema operativo? Son visibles los archivos del SO desde el explorador de carpetas del disco duro?
   
  17- Cuando instalé el SO en mi intento anterior intenté actualizar firefox como hacía con Windows pero no me salía la opción de “actualizar” en el mismo firefox. Es necesario que inicie sesión como Root para que me aparezca? O solo es posible hacerlo reinstalado todo el programa firefox? Los complementos de firefox de Windows valen igual para Linux?
   
  18- Tema de codecs para video y audio. Cuales formatos de video y audio puedo reproducir en Ubuntu? Tenéis una lista? Algún pack de codecs/contenedores recomendado? Tipo klite para Windows.
   
  19- Es necesario reiniciar el PC después de instalar programas o drivers? Es suficiente con cerrar cesión y abrir otra vez? Es igual de eficiente?
   
  20- Como se desinstala un programa? Se hacen todos igual? Hay algún aplicativo especifico donde salgan todos los programas instalados para poder desinstalarlos uno a uno?
   
  21- Como se desinstala un driver? Debo desinstalar un driver viejo si tengo una actualización? Lo digo por la tarjeta grafica ya que suelo actualizar los drivers con frecuencia.
   
  22- Como desfragmentar el disco duro?
   
  23- Puedo escribir y leer en particiones con NTFS?
   
  24- Como puedo ordenarme el “menú inicio” donde salen accesos directos a todos los programas? Es decir, crear accesos directos a los programas, crear carpetas en el menú de programas, etc.
   
  25- Si se va la luz y se me apaga el PC de golpe, en Linux, se me puede fastidiar el SO como en Windows? Supongo que es igualmente recomendable apagarlo bien, pero los daños son igualmente graves?
   
  26- Se pueden instalar programas para Windows en Linux? Como? Funcionan igual de bien? :)
   
  En fin, creo que con esto para empezar será suficiente.  Si puedo hacer todo esto el siguiente paso sería instalarme los dos SO para usarlos de forma general porque prácticamente podría hacer lo mismo que con Windows.
   
  Quiero aprender a usar Linux porque la verdad es que ya estoy harto del Windows. Tengo un ordenador potente y a pesar de que lo he instalado todo perfectamente y tengo todos los parches de seguridad tengo la sensación de tener un PC lento y muchas veces inestable.
   
  A ver si entre todos y algunos días podéis aclararme estas dudas pliz!!!!
   
  Muchas gracias de antemano!!!
   
  PD he comprimido todos los archivos de drivers en un pack .rar y lo he subido a rapidshare. Así veréis lo que tengo y creo que será más fácil. Lo podéis descargar de la siguiente dirección (son 75MB) y estad tranquilos que hay virus ni troyanos jeje :P
   
  [http://rapidshare.com/files/256130148/Linux_Drivers.rar](http://rapidshare.com/files/256130148/Linux_Drivers.rar)
   
  PD2 el tema de la impresora y algunas dudas de las interfaces graficas como el kde y todo eso lo dejaremos para otro día jeje :) aunque espero que con todas estas dudas aclaradas pueda hacerlo por mí mismo y no tenga que venir a molestar cada 2x3 :P

---

### Post by Hei Ku on 2009-07-15
Hmmm, por que no bajas un LiveCD, lo corres, y si te anda bien te vas familiarizando con el uso directamente?

El LiveCD te permite bootear el OS desde el CD sin necesidad de instalarlo. Como en muchas otras cosas, Linux y Windows son diferentes.

---

### Post by jukitx on 2009-07-15
gracias por la respuesta hei ku!

si, eso ya lo he hecho. ademas tambien lo instalé una vez. Entonces, en base a esas dos experiencias he redactado este post para intentar recojer las dudas más importantes que tenia :)


un saludo

---

### Post by Hei Ku on 2009-07-15
Seguí mirandolo entonces. Salvo el de la placa de video, el resto de los drivers no los vas a necesitar.

La instalación seguro es a traves de repositorios. Para eso usas Synaptic. Elegi el programa, clickea y se instala. Para desinstalar, lo mismo. Desde ahi tambien actualizas, kernel, escritorio y aplicaciones que hayas instalado por ese metodo.
Los programas tienen que estar disponibles para la arquitectura que uses, pero eso en general no es problema. No cometas el error de los usuarios de Windows de buscar programas en Google e instalar. Eso es malo, malo. Te vas a agarrar la gripe porcina si lo haces.

Programas de Windows podrias usarlos con Wine, que es una aplicacion que te permite correr algunos de estos programas. Sin garantias, y generalmente tenes equivalentes en Linux que hacen lo mismo y andan mejor.

Para instalarlo te va a crear al menos 2 particiones. El filesystem y el swap. Podes crear mas, como el home, para guardar tus archivos en una particion separada. El instalador se encarga de esto.

Con esto tenes para empezar. Arranca de vuelta el LiveCD y dale otra vuelta. Hasta podes probar de instalar programas mientras corres el LiveCD, aunque obvio no van a estar ahi la proxima.

---

### Post by Hei Ku on 2009-07-15
Otra cosa mas. Todas estas preguntas estan respondidas en el foro y subforos. Aprovechalos.

---

### Post by jukitx on 2009-07-15
> **Hei Ku said:**
> Seguí mirandolo entonces. Salvo el de la placa de video, el resto de los drivers no los vas a necesitar.

La instalación seguro es a traves de repositorios. Para eso usas Synaptic. Elegi el programa, clickea y se instala. Para desinstalar, lo mismo. Desde ahi tambien actualizas, kernel, escritorio y aplicaciones que hayas instalado por ese metodo.
Los programas tienen que estar disponibles para la arquitectura que uses, pero eso en general no es problema. No cometas el error de los usuarios de Windows de buscar programas en Google e instalar. Eso es malo, malo. Te vas a agarrar la gripe porcina si lo haces.

Programas de Windows podrias usarlos con Wine, que es una aplicacion que te permite correr algunos de estos programas. Sin garantias, y generalmente tenes equivalentes en Linux que hacen lo mismo y andan mejor.

Para instalarlo te va a crear al menos 2 particiones. El filesystem y el swap. Podes crear mas, como el home, para guardar tus archivos en una particion separada. El instalador se encarga de esto.

Con esto tenes para empezar. Arranca de vuelta el LiveCD y dale otra vuelta. Hasta podes probar de instalar programas mientras corres el LiveCD, aunque obvio no van a estar ahi la proxima.


gracias por tu respuesta hei ku,

a ver, la última vez que instalé ubuntu en efecto solo necesité el driver de la tarjeta de video. Sin embargo, la tarjeta wifi usb me daba problemas y por eso me descargé el driver de la web del fabricante pero no sé como instalarlo. Ademas tengo algunas espinas clavadas que necesitaria aclarar para abrirme camino con mas facilidad. Si me pongo a buscar todas estas dudas sin tener ni idea de usar linux me voy a hacer un lio tan grande que no me voy a enterar de nada jejeje

Entonces, lo que queria principalmente es aprender a instalar hardware en linux de una forma general y si de paso pues se me pueden contestar las otras cuestiones entre varia gente pues mejor, sino pues no pasa nada.

Volviendo al tema, qué es Synaptic? es una interface que lleba el ubuntu? desde ahi puedo instalar y desinstalar programas? que son los repositos? perdon por la pregunta amigo pero es que no tengo ni idea del tema :S

Creo que lo que voy a hacer es a instalar otra vez el ubuntu y voy a ver si me aclaro. Sin embargo, lo que más prisa me correria es como instalar la tarjeta grafica y la tarjeta usb wifi para no tener problemas con internet. A partir de ahi creo que ya me podria poner a trastear y seria todo mas rapido

gracias de antemano y un saludo!!

PD edito: otra cosa más, cual es el mejor sistema de archivos para hacer el formateo? es que veo que hay varios tipos.

---

### Post by staar on 2009-07-15
uf, que ensalada que tenés...

primero que nada, hacete a la idea de GNU/Linux es un SO completamente diferente a Ventanas, y se maneja de forma completamente diferente, asi que no intentes buscar reemplazos para cada herramienta de aquél, porque vas muerto, además, ambos sistemas son binariamente incompatibles, por lo que los drivers (y en general, cualquier software) de uno no funcionan en el otro (hay excepciones a esto, pero pocas)

primero tu duda principal, en linux los drivers para los dispositivos vienen incluidos en el kernel (el núcleo del sistema operativo) y no es necesario instalar otros, con excepción de algunos pocos como las placas de video o algunas tarjetas wifi, por los otros no te preocupes, generalmente todo funciona a la primera, y no es necesario configurar nada para que ande (de nuevo, obviamente hay excepciones, nada es perfecto), para instalar los drivers privativos de tu placa de video andá a Sistema > Administración > Controladores de hardware, e instalalos desde ahí, es más fácil, más seguro, y se van a actualizar solos...

segundo, la instalación de software no es algo estandarizado en linux, existen diversos métodos, que dependen de como sea distribuido el software, el que más vas a usar en ubuntu, es a través de paquetes binarios comprimidos en archivos .deb (que se instalan con doble click), para eso se usa principalmente Synaptic (hay otros, como apt-get que es por consola), que es un programa que viene con el SO que te permite acceder a los repositorios (básicamente, servers con archivos .deb almacenados) y bajar e instalar programas desde ahí, la lista de los diferentes repos puede ser modificada, y periodicamente se actualiza la información y se descargan las actualizaciones y nuevas versiones, todo el software instalado desde los repos oficiales es confiable y se recomienda mantenerlos actualizados, acostumbrate a usar los repos y no bajes software de cualquier lado...

el mejor filesystem depende de tus necesidades, el mejorcito para mi gusto actualmente es ext4 (el default es ext3, estos son sistemas en serio, no necesitan desfragmentación manual como NTFS :-D ), linux puede leer y escribir en incontables tipos, incluido NTFS...

ubuntu es una distro que no usa mucho el usuario root, lo sustituye por el uso de sudo, que es una herramienta que permite elevar temporalmente los permisos del usuario normal para que pueda realizar tareas administrativas, generalmente, cuando algo necesite de permisos de root (como instalar software), te va a saltar un díalogo pidiéndote la contraseña de tu usuario, ponela y listo...

mirá, en realidad, de todos estos temas abunda información, y son demasiado extensos como para tratarlos bien acá, te recomiendo que te pases por el thread de enlaces útiles que está como sticky en el foro...

bueno, seguro que no respodí a todas tus dudas (26!), pero hice un intento :lolflag: igual, con el uso te vas a ir dando cuenta de las cosas...

saludos

---

### Post by guillermolisi on 2009-07-15
> **jukitx said:**
> gracias por la respuesta hei ku!

si, eso ya lo he hecho. ademas tambien lo instalé una vez. Entonces, en base a esas dos experiencias he redactado este post para intentar recojer las dudas más importantes que tenia :)


un saludo
Jukitx

Con el fin de facilitar las respuesta, las busquedas que otros puedan hacer por temas que vos tocas en ese hilo/thread y para mantener un orden tematico (fijate que hay subforos especificos), te recomiendo leer las reglas, sitios de interes y utilidad y otros temas realcionados que figuran como sticky threads (fijos) al comienzo de la seccion Normal Threads y de cada subforo.

Ademas, familiarizate con las herramientas de busqueda que hay disponibles en el foro con el fin de revisar si alguien ya soluciono tus problemas o hizo algun comentario clarificador sobre cuestiones sobre las que tenes dudas.

Las dudas que te surjan sobre la mejor utilizacion del foro, podes canalizarlas via mensaje privado (PM) a los moderadores (cuyo nickname se ve en color verde).

Gracias y bienvenido

---

### Post by jukitx on 2009-07-15
voy a ponerme a analizar toda la info que me habeis posteado, de verdad, muchas gracias staar por todo. 

Y guillermolisi, tienes razón. es demasiado para un post. deberia haber usado la función de buscar. lo que pasa es que estaba tan verde que no sabia por qué sitio empezar ya que no tenia un punto de vista global de todo, por eso lo puse todo junto. para el resto de cuestiones usaré las funciones de buscar y para lo que no sepa seguiré tu consejo.

En fin, voy a ponerme manos a la obra y cuando tenga toda la info editaré el post inicial con todas las respuestas y así quedará como un manual por si alguien más quiere mirarlo.

creo que con lo que me habeis puesto ya tengo trabajo para dos dias.

un saludo y muchas gracias!

---

### Post by jukitx on 2009-07-15
el tema ya está practicamente aclarado, una alma bondadosa me ha respondido a todas las dudas por privado :)  (las 26) voy a ver si me inicio entre lo que me habeis aclarado vosotros y esa persona. 

voy a reinstalar ubuntu e iré posteando cuando me quede clavado!!

una cuestión mas, es mejor que lo haga en posts separados? o lo hago directamente en este? (es una pregunta al moderador).

un saludo

---

### Post by guillermolisi on 2009-07-15
Lo ideal es que puedas reunir en un thread las dudas relacionadas con un mismo tema, por ejemplo audio.

En caso que te sea dificil determinar si es para Hardware, Software o Comunidad, los indicios que aconsejamos son: Si se puede patear, el tema es claramente de hardware (drivers incluidos). Si solo se lo puede insultar, es claramente software (exluidos los drivers) y si el tema se pone bueno y amerita una cafe, cerveza o gaseosa de moda y es de interes para la comunidad Ubuntu/Linux/OSS, va a Comunidad.

Para que no te marees con las respuestas y puedas llevar a cabo un trabajo algo mas metodico que el solo impulo de la ansiedad, abri threads que te permitan ir resolviendo algunas cosas primero para quitarlas del medio y pasar a las demas. Con esto solito vas a racionalizar la cantidad de hilos abiertos y poder digerir todo lo que por aqui te sugieran.

Si no se entiende lo que propongo, hacemelo saber.

---

