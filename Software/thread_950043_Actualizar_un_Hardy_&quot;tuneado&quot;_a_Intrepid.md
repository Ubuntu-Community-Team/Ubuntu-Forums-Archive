---
title: "Actualizar un Hardy &quot;tuneado&quot; a Intrepid Ibex ¿Desestabilizador?"
date: 2008-10-16
forum: Software
---

### Post by nahuel_89p on 2008-10-16
Hola foro, con miras al release de la proxima y prometedora entrega de ubuntu, me surgió una duda en cuanto a si actualizar o no, ya que el hardy que uso ahora esta bastante tocado, y temo que hayan problemas de compatibilidad.
Como nunca antes experimenté una actualizacion de ubuntu (me inicié con hardy directamente), no se en que medida realmente ocurre lo que sospecho... pero teniendo en cuenta, por ej, que tengo emerald, compiz, Screenlets, cairo dock, customizaciones de tipografias, etc, osea, como cualquiera de ustedes, supongo.
Con el tema compatibilidad de hardware no creo para nada que hayan problemas. ¿Pero con respecto a las aplicaciones de uso diario? firefox? wine? emesene?

---

### Post by luks911 on 2008-10-16
Si con "tuneado" te referís a eso que contás, o sea programas instalados y configurados, entonces no tiene que haber ningún problema en la actualización. Los programas se van a actualizar y se van a mantener como los configuraste y tus datos.
Distinto es si instalás Intrepid encima de lo que tenés. Algunos lo recomiendan, pero no es necesario. En mi caso actualicé en su momento de Gutsy a Hardy y no hubo drama. 
Ahora, si querés instalar Intrepid encima de Hardy, lo conveniente es tener (o si no lo tenés hacerlo) el home en una partición independiente, para mantener todas tus configuraciones.

Saludos

---

### Post by nahuel_89p on 2008-10-16
te referis a que basta con el comando apt-get dist-upgrade? porque tambien podria instalar desde cd y sobreescribiendo la particion pertenecienta a los archivos del sistema.

Otra pregunta, ya que tengo hardware de 64bit, mas concretamente AMD quad core, es recomendable aprovechar para instalar intrepid 64?mm aunque ahi me suena a que voy a tener q reinstalar las app a modo 64. Y no se si no sigue medio verde la adecuacion 64 bit de ubuntu todavia.

---

### Post by luks911 on 2008-10-16
Exacto. Con un sudo apt-get dist-upgrade es suficiente.
Pasar a 64 ya requiere instalar todo de nuevo, y si no necesitás aplicaciones de 64bits, no tiene sentido, no vas a notar diferencias.

Un saludo

---

### Post by Thalskarth on 2008-10-19
Aprovecho este thread para hacer una pregunta...

Me pasó en su momento con Hardy y ahora lo mismo con Intrepid..
No se, probé de actualizar mi ubuntu a la siguiente versión, pasando en éste caso desde hardy a Intrepid... y tras finalizar con todo, noto el sistema "más pesado" o "más lento"..
Todo tarda más, incluso se cuelga por momentos tardando en responder. En cambio, haciedno una instalacion limpia de intrepid.. el sistema anda de 10, rapido y sin problemas como los citados...

Y haciendo memoria, lo mismo me ocurrió cuando quise actualizar desde Gutsy a Hardy, que como andaba tan "pesado", terminé haciendo una instalación limpia en si momento...

Es normal que eso pase?? a que puede deberse??

Gracias

---

### Post by pol666 on 2008-10-19
yo al tener la /home separada me es lo mismo, prefiero Reinstalar desde 0 que actualizar, total concervo mis config y el sistema esta estable

---

### Post by PeTTi on 2008-10-19
Yo actualize a 8.10 y no tuve ningún problema.. :)

---

### Post by guisheca on 2008-10-20
> **pol666 said:**
> yo al tener la /home separada me es lo mismo, prefiero Reinstalar desde 0 que actualizar, total concervo mis config y el sistema esta estable

Es verdad, incluso al reinstalar conservás hasta la configuración de la apariencia. Pareciera que no ocurrió nada con el sistema.
El único inconveniente es que hay que volver a instalar todos los programas que tenías antes y que no venían por defecto, pero si tenés internet es sólo un pequeño trámite.

---

### Post by nahuel_89p on 2008-10-20
> **guisheca said:**
> Es verdad, incluso al reinstalar conservás hasta la configuración de la apariencia. Pareciera que no ocurrió nada con el sistema.
El único inconveniente es que hay que volver a instalar todos los programas que tenías antes y que no venían por defecto, pero si tenés internet es sólo un pequeño trámite.

Noo, volver a reinstalar todo no, es agobiante, programas, themes, configuraciones, plugins, recustomizar... (las dos veces que reinstale ubuntu me disuaden completamente de volver a pasar horas para dejarlo "a punto")... Si actualizo a Intrepid Ibex, lo hago desde el comando; pero si me llega a pasar lo que le pasó a Thalskarth, habrá manera de arreglarlo sin instalar desde el cd? o es un paso de no retorno?

---

### Post by guisheca on 2008-10-20
> **nahuel_89p said:**
> Noo, volver a reinstalar todo no, es agobiante, programas, themes, configuraciones, plugins, recustomizar... (las dos veces que reinstale ubuntu me disuaden completamente de volver a pasar horas para dejarlo "a punto")... Si actualizo a Intrepid Ibex, lo hago desde el comando; pero si me llega a pasar lo que le pasó a Thalskarth, habrá manera de arreglarlo sin instalar desde el cd? o es un paso de no retorno?

Nauel, si tenés el /home en una partición aparte eso no es así. Debido a que en el /home se almacena toda la configuración de todos los usuarios del sistema (configuraciones de programas, themes, modificaciones varias, etc), si reinstalás lo único que vas a tener que hacer es volver a instalar los programas que usas y que no vienen por defecto en ubuntu.
Por eso siempre se recomienda tener el /home aparte. Obvio que cuando reinstalas tenés que mantener el /home intacto, lo único que tenés que formatear es la partición donde va ls raíz (/).
Saludos.

---

