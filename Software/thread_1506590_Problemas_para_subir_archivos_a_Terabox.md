---
title: "Problemas para subir archivos a Terabox"
date: 2010-06-10
forum: Software
---

### Post by marcelo_bur on 2010-06-10
Hola, Hace un año y medio que soy usuario de Ubuntu, aún me manejo con la versión 8.04 porque me funciona muy bien, casi no he tenido problemas y los pocos que tuve los solucione leyendo en la red, por lo me da no se que cambiar. Tengo idea de comprar un nuevo HD e instalar alli la version 10.04. Pero en realidad todo esto no viene mucho al caso, salvo para indicar que versión de Ubuntu utilizo.
El asunto es que se me dio por pedir el servicio Terabox de Telefónica de Argentina, tengo Speedy como ISP. Sabía de antemano que el sofware que ellos te dan no funciona en Linux, salvo quizás bajo Wine, pero nunca use nada de Windo$ en mi Ubuntu. Pero mi sorpresa fue que tampoco puede subir archivos via web. Puedo ver mis archivos, abrir carpetas, bajar archivos (los subi con una partición que tengo con XP por si las moscas), etc. Pero cuando quiero subir un archivo aparentemente todo va bien, se ejecuta el applet, puedo elegir el archivo a subir, le doy a subir... y nada. Incluso me marca que está transfiriendo el archivo, pero la barra de progreso no se muve del 0% y no hay forma. Busqué en la red y encontré muy poca información, solo un post de alguien a quien supuestamente le pasa lo mismo. Esta persona usa Firefox, igual que yo, y dejo escrito que con el navegador de Google se funciona. Bajé el navegador y tampoco, nada. Hice el reclamo a Telefónica, tengo que volver a llamar mañana, pero seguro que me salen con cualquier verso.
Si alguien aqui le paso, o sabe algo al respecto, especialmente si sabe como solucionarlo, le quedaré muy agradecido.
Saludos

Marcelo

---

### Post by alfplayer on 2010-06-10
No es lo que preguntaste, pero por si no lo conocés, Ubuntu One puede ser una alternativa a Terabox, que además está integrado al escritorio de Ubuntu 10.04.

---

### Post by marcelo_bur on 2010-06-10
Hola y gracias alfplayer por la información. No conocía el servicio y siempre es bueno aprender. Pero no es lo que busco, y te explico por que. Todavía no tengo instalada la versión 10.04, además el costo es muy superior al de Terabox (10 U$S por mes, 40 pesos argentinos mas o menos, contra 14 pesos de terabox), tambien hay que tener en cuenta que Ubuntu One te ofrece por ese dinero 50 GB de alojamiento, en tanto que en Terabox es ilimitado, o al menos eso dice y pienso ponerlo a prueba. Y, quizás lo más importante de todo, es que en realidad yo puedo usar el servicio ya que tengo una partición con XP en esta máquina que sube los archivos sin problemas y una notebook con Vista, pero yo quiero poder hacerlo con Ubuntu, quiero que todo lo que te ofrecen se pueda hacer desde sistemas operativos Linux. Ese es el motivo de que dedique tiempo a buscar en la red, que publique este tema y que pierda mi tiempo en llamadas y reclamos intentando que telefónica de argentina resuelva el problema, si no hay otro modo.
Saludos

Marcelo

---

### Post by alfplayer on 2010-06-10
Ubuntu One ofrece hasta 2 GB sin costo.

Con respecto a este servicio (que no sabía que existía hasta ver este tema), probablemente no hay soporte para linux, por lo que cualquier llamada es inútil. Por las pocas páginas web que visité de Telefónica es evidente que la calidad del diseño de las páginas es muy baja o están muy desactualizadas. No confío para nada en la calidad del servicio. Igualmente, puede suceder que el problema solo aparece con versiones viejas de los navegadores en 8.04, que el problema no esté presente con versiones nuevas.

---

### Post by marcelo_bur on 2010-06-10
Hola. Realmente me llama mucho la atención este asunto. No es mi máquina, ya que en XP y con una versión de Firefox que no está muy actualizada que digamos ya que casi no la uso, todo funciona bien. En Ubuntu 8.04 Firefox se actualiza periodicamente, también revisé mis versiones de Java y Adobe Flash Player y son las mismas o superiores. Ademas de estar ahí el problema no cargaría el applet. En cuanto al navegador de Google, descargue la última versión disponible para Linux, también carga bien el applet pero no sube los archivos. Se me ocurre que puede haber algún problema en los permisos de algo, la verdad no se. Cargo archivos en muchos otros sitios, tengo sistemas para carga online de imágenes y archivos en mi sitio, puedo manejar sin problemas el file manager del servidor de mi sitio (lo cual probe por curiosidad, ya que por supuesto uso FTP para ese trabajo), y también probé con el file manager de un sitio alojado en otro servidor que es de una amiga. Nada me da problemas, solo esto. Es muy raro.

Saludos

---

### Post by alfplayer on 2010-06-10
Ubuntu 8.04 usa por defecto la serie 3.0 de Firefox. Firefox queda con esa serie si el usuario no instala una versión de series más nuevas (3.5.x o 3.6.x).

---

### Post by SLA_leandrin on 2010-06-10
Tal vez quieras probar con Dropbox, como otra alternativa, me funciona muy bien en clientes linux y windows...

[www.dropbox.com](www.dropbox.com)

---

### Post by marcelo_bur on 2010-06-10
Gracias SLA_leandrin. Conozco más o menos Dropbox, pero el asunto acá es que quiero usar Terabox con Ubuntu. Como ya comenté puedo cargar archivos desde la note, es más, ya cargue 3 Gigas. 
Me quedé pensando en lo que comentó alfplayer sobre que Hardy Heron usa por defecto Firefox 3.0. Y tal cual, a pesar de las actualizaciones que hace, sigue siendo 3.0.x, o mejor dicho, era. Porque acabo de actualizarlo a la version 3.6.x y realmente creí que con eso se iba a solucionar el problema. Pero no...
En verdad ya no se por donde buscar. No me queda otra que esperar que alguien a quien le haya pasado lo mismo publique aqui o en algún otro sitio la solución, si es que existe.
Saludos

---

### Post by alfplayer on 2010-06-10
Lo siguiente creo que es modificar el valor de MTU de la interfaz de red. Con Network Manager se puede modificar editando la conexión.

---

### Post by marcelo_bur on 2010-06-10
> **alfplayer said:**
> Lo siguiente creo que es modificar el valor de MTU de la interfaz de red. Con Network Manager se puede modificar editando la conexión.

Gracias por todo, pero creo que llegué al límite de mis conocimientos. Se donde ver el valor de MTU, pero no se como modificarlo, ni que valor asignarle si supiese como, ni en que forma modifica eso las cosas.
Creo que me toca esperar que alguien publique la solución.
Saludos

---

### Post by alfplayer on 2010-06-10
> **marcelo_bur said:**
> Gracias por todo, pero creo que llegué al límite de mis conocimientos. Se donde ver el valor de MTU, pero no se como modificarlo, ni que valor asignarle si supiese como, ni en que forma modifica eso las cosas.
Creo que me toca esperar que alguien publique la solución.
Saludos

Es por si hay problemas en la transferencia. No se si es la solución pero es algo rápido y no riesgoso que se puede probar. Te recomiendo probar con el valor 1450, y si funciona elevar el valor, por ejemplo a 1492 que es el valor que uso en mis computadoras.

---

### Post by marcelo_bur on 2010-06-10
Olvidé comentar que me conecto a través de un router, aunque no creo que ese es el problema. El asunto es que entré a la configuración del router, el MTU estaba en 1492, lo bajé a 1450 y no sirvió de nada, por lo que lo dejé como estaba, a ver si por eso anda mal otra cosa...lol
Saludos y gracias por preocuparse en encontrar una solución.

---

### Post by alfplayer on 2010-06-10
> **marcelo_bur said:**
> Olvidé comentar que me conecto a través de un router, aunque no creo que ese es el problema. El asunto es que entré a la configuración del router, el MTU estaba en 1492, lo bajé a 1450 y no sirvió de nada, por lo que lo dejé como estaba, a ver si por eso anda mal otra cosa...lol
Saludos y gracias por preocuparse en encontrar una solución.

No, en el router que quede como estaba, en 1492. Hay que cambiarlo en Ubuntu.

---

### Post by marcelo_bur on 2010-06-11
Hola. En mi máquina figura que tengo instalado el NetworkManager, sin embargo no encuentro desde donde ejecutarlo. En la red encontré los comandos para cambiarlo desde la terminal, pero tengo miedo de meter la pata. Ademas el valor MTU que me da mi información de red es muchisimo más alto que los que mencionas.
En este link te dejo una captura de pantalla con los datos

[http://i47.tinypic.com/dczl3r.jpg](http://i47.tinypic.com/dczl3r.jpg)

Lástima que en este foro está deshabilidado html, sino la redimensionaba y la dejaba visible aqui.
Saludos

---

### Post by marcelo_bur on 2010-06-11
Bien, para dejar lo más completo posible este asunto sigo dejando la información que he podido encontrar.

Según el consola de errores de Firefox (se me ocurrió revisarla...) el motivo de mi problema es el siguiente:

Error: applet.setUploadAllowed is not a function
Source File: [https://terabox.telefonica.com.ar/application/Script/digidata_scripts.es-ES.js](https://terabox.telefonica.com.ar/application/Script/digidata_scripts.es-ES.js)
Line: 1227

Subi dos capturas de pantalla, espero que se vean bien. Note que solo queda una miniatura en el mensaje.

Saludos

---

### Post by marcelo_bur on 2010-06-12
Hola. No se si realmente esta es la solución, ya que considero que se debería poder cargar archivos en terabox con cualquier navegador, como ocurre si utilizo Window$, pero finalmente instleé el navegador Opera 10.10 para Linux y si carga los archivos.
Saludos

PD: Estoy buscando como etiquetar el tema como "SOLVED"

---

### Post by alfplayer on 2010-06-12
Hola.

> **marcelo_bur said:**
> Estoy buscando como etiquetar el tema como "SOLVED"

Está en *Thread Tools*.

---

### Post by marcelo_bur on 2010-06-12
Lamento tener que volver a cambiar la etiqueta de este tema, pero Opera se pone lento en la página de Terabox, carga unos pocos archivos y se cuelga. Evidentemente no es la solución.
Saludos

---

### Post by marcelo_bur on 2010-06-14
Hola. Para gran sorpresa mia el servicio técnico de Telefónica de Argentina se tomó la molestia de comunicarse conmigo (antes de que yo les siga metiendo reclamos). Lo cual no quiere decir que mi problema se haya solucionado, sino todo lo contrario, que no tiene solución, o que no les interesa solucionarlo porque ya se habían atajado antes en los Térmitos y Condiciones del servicio. Supongo que eso pasa por no tomarse el trabajo de leer con cuidado, o a veces ni leer, estos extensos documentos que imponen mil obligaciones y posibles acciones judiciales al cliente en tanto les libran a ellos de cualquier responsabilidad. El hecho es que yo si lo leí, pero no a fondo y, cuando leí que solo soportaba Window$ y Mac como sistemas operativos, supuse que se refería al software que te dan para descargar, nunca me imaginé que la página web estaba incluida. Sin embargo esto es lo que me hizo notar quien me llamó, dice "el servicio", lo cual incluye todo.
Al menos tuvieron la delicadesa de aclararme que no funciona en Ubuntu porque es necesario que se ejecuten dos plug-in de Microsoft, Minimum Microsoft .Net Framework y Dot Net (.NET) 2.0 o superior.
No se si poner este tema como SOLVED o no, porque la etiqueta correcta creo que debería ser IMPOSIBLE DE SOLUCIONAR, al menos por ahora.
Solo me resta esperar que este tema sirva de advertencia a los usuarios de Linux que hayan pensado en contratar Terabox y dejar una recomendación a partir de mi experiencia personal en este caso: **Lean bien los Terminos y Condiciones de lo que desean contratar**.
Saludos

---

### Post by alfplayer on 2010-06-14
Es posible que funcione con wine, aunque dudo que valga la pena el esfuerzo.

---

### Post by marcelo_bur on 2010-06-14
Hola. Definitivamento no vale el esfuerzo ni tengo interés en usar Wine en mi Ubuntu. Para eso uso la partición que tengo con XP o la note.
Ahora es mucho lo que quiero resguardar, aunque por lo que lei ahora atentamente en los Términos y condiciones, si algo se pierde no se hacen responsables de nada. Luego será solo de vez en cuando. Además soy algo obsesivo con resguardar mis archivos, tambien uso CD, DVD y luky venga.
El meollo de todo este asunto es que me indigna que armen una página web que saben que no va a funcionar con Linux, y que me digan, como me dijeron, que está especificado en los famosos "términos" y que ni siquiera van a notificar al servidor ni a los responsables de manejar el sistema del inconveniente.
Y creo que con esto se termina el tema.
Saludos.

---

### Post by alfplayer on 2010-06-14
Para los de soporte es simple: No hay soporte. No se cubre en los términos. Puede funcionar o no en linux.

Ellos creen que no deben resolverlo. La respuesta es la esperada.

---

### Post by marcelo_bur on 2010-06-17
Hola. Se que dije que no valia la pena, pero sinceramente me interesa poder usar el servicio de Terabox. Y ya se me hacia complicado andar cambiando de sistema operativo en esta máquina, sobre todo teniendo en cuenta que todo el material que trabajo esta en la partición de Ubuntu, y también en la de Windows algo, pero como todos saben desde Ubuntu se accede a Window$ pero no a la inversa. Y la note en realidad es de mi hija, que casi no la usa durante el día, pero igual y por si las moscas prefiero usar la mia. Así que hice la prueba con Wine y por suerte no fue en vano ni demasiado complicado. Corriendo Firefox bajo Wine puedo subir archivos a Terabox sin problemas.
Saludos

---

### Post by alfplayer on 2010-06-17
Si efectivamente usa .NET hacerlo funcionar mejor probablemente es imposible. Ahora se puede marcar como *Solved*.

---

### Post by marcelo_bur on 2010-06-19
Hola. Sigo el tema por curiosidad, ya que con lo logrado el problema está prácticamente resuelto para mi. Pero me llama la atención que si intento cargar archivos que pesen más de 14 Megas el file manager de Terabox se cuelga, y me refiero a que un solo archivo pese más, porque puedo poner a cargar lo que quiera en archivos de menor tamaño que no pasa nada. No me gusta mucho quedarme con estos intringulis, así que si alguien tiene idea de donde puede estar el problema le agradeceré me saque de la duda.
Saludos.

---

### Post by alfplayer on 2010-06-19
No sucede en windows?

---

### Post by marcelo_bur on 2010-06-19
Hola. No, no sucede en window$, en esta misma máquina y con la misma versión del navegador. De lo unico que no estoy seguro es de si instalé la misma versión de flash player, aunque dudo que ese sea el problema. Tal vez sea algo mal pensado, pero da la impresión de que Telefónica tuviese algún acuerdo con Billy para que este servicio funcione bien solo donde el quiere.
Saludos

---

### Post by marcelo_bur on 2010-06-26
Hola. Subo este tema para comentar que he encontrado la solución definitiva a este problema, o mejor dicho, no la he encontrado, ya existe en Ubuntu 10.04.
Como comenté anteriormente no me decidía a cambiar mi versión, 8.04, ya que la conozco muy bien y me funciona muy bien. Y de pronto se me ocurrió una alternativa. En esta máquina tengo una partición con Window$ que rara vez utilizo y con mucho espacio libre. Entonces lo que hice fue instalar la versión 10.04 con la opción "Instalar dentro de Window$". Hasta ahora todo esta funcionando bien, salvo un molsto parpadeo en la pantalla que ya he visto comentado por ahí y, para mi sorpresa y alegría, acabo de subir un archivo de 250 Megas a Terabox con Firefox tal como viene preinstalado sin ningún problema, solo tuve que instalar el plug-in.
De aqui en más solo me resta aprender más sobre esta versión y ver si la dejo como de uso por defecto o no.
Saludos

---

