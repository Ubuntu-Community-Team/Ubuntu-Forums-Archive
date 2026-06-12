---
title: "desintalación de avast"
date: 2010-05-14
forum: Software
---

### Post by capcabgue on 2010-05-14
Hola:

Bueno les cuento en mi pega trabajamos en su mayoría con linux y unos pocos con guin2, por este motivo y como se pidió (ya que tuvimos un troyano y 1 virus) instalé un antivirus (avast) forcé la instalación, ya que solo existe la arquitectura para 32 bit de este antivirus. Instalé todas las dependencias que me faltaban.

Cuando comienzo a correr la aplicacion me arroja un error: 
"avast: can not initialize avast! engine: Invalid argument"
Lo he tratado de desintalar para poner otro Antivirus (AVG o cual me recomiendan que instale) y no me permite sacar avast ni purgando con dpkg o forzando la desintalación.

Alguien me puede ayudar a como desintalar avast.

Gracias

---

### Post by asterix77 on 2010-05-14
Yo instalé Avast siguiendo estas instrucciones: [http://www.tecnohispanos.com/principal/2010/01/25/como-instalar-avast-4-para-linux-en-ubuntu-9-10/](http://www.tecnohispanos.com/principal/2010/01/25/como-instalar-avast-4-para-linux-en-ubuntu-9-10/)

Me funcionó sin ningún problema en mi equipo AMD64 por un buen tiempo, hasta que hace unas par de semanas, en una actualización que realicé me arrojó el mismo error tuyo. Volví a realizar los mismos pasos del link sin remover nada, y nuevamente quedó operativo.

Saludos

---

### Post by capcabgue on 2010-05-17
Hice caso de lo que decía asterix 77 (gracias, volvi a instalarlo). Sin embargo corrí de inmediato avast y sin problema.
Luego volví a revisar otro pendrive y me dio el mismo error.
Luego pensé que hice distinto ahora de la otra vez... Hay que correr avast como superusuario.
Asunto resuelto.

Gracias a todos por la ayuda y espero que esto le sirva a alguien más.

---

