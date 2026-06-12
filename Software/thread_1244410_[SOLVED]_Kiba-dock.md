---
title: "[SOLVED] Kiba-dock"
date: 2009-08-19
forum: Software
---

### Post by ALEXEX on 2009-08-19
Hola gente.
 
Tengo algunas dudas sobre kiba-dock, pero por internet no puedo encontrar nada nuevo de información. Y es que de kiba-dock tengo algunas dudas, que so:
 
*Como puedo cambiar la imagen de los iconos en el dock, es decir cuando doy clic derecho y voy a opciones no veo donde puedo cambiar la IMAGEN y el NOMBRE
 
*Existen temas para kiba-dock como en Cairo
 
*Existen complementos para kiba, es decir agregar nuevos efectos.
 
Espero sus respuestas

---

### Post by santiagoward2000 on 2009-08-19
Hola!
Hace mucho que no uso Kiba-Dock, dejé de usarlo poco después que dejaran de actualizarlo, pero vamos a ver que me acuerdo:

[LIST]
[*] Las imágenes de los íconos estoy seguro que se pueden cambiar desde el menú para editarlos. Si hacés click derecho en el ícono que querés editar, debe haber alguna opción tipo editar o propiedades. Se debe editar de ahí.

[*]Sobre los temas, nunca ví nada prearmado. Kiba no tiene nada parecido al manejador de temas de Cairo-Dock, así que si encontrás alguno (aunque lo dudo) tendrías que copiarlo a la carpeta de configuración: ~/.kiba-dock

[*]Respecto a los complementos, no sé cómo lo hayas instalado. Cuando bajás el código para compilarlo, hay 4 paquetes:
[LIST]
[*]kiba-dock (que tiene lo básico para que ande)
[*]kiba-dock-plugins (ahí están casi todos los complementos que existen para Kiba, como papelera, reloj, monitor del sistema, etc.)
[*]kiba-dock-gaim (que es un complemento más, agrega un ícono para manejar gaim/pidgin)
[*]akamaru (el motor físico que en algún momento hizo que los íconos tengan efectos físico, pero que hace mucho que no anda)
[/LIST]
No hay otros plugins oficiales, y dudo mucho que alguien haya hecho alguno no oficial, yo personalmente nunca ví.
[/LIST]

El proyecto Kiba-Dock está "congelado". El creador avisó que estaba ocupado y que no iba a poder trabajar en el proyecto por seis meses. Eso fue hace más de un año. Aunque no lo hayan hecho oficial, creo que el proyecto está abandonado, por lo que no tengo muchas esperanzas de que alguien se ponga a armar más complementos.

[OT]Perdón que me vaya de tema, ¿pero hay alguna razón por la que quieras usar Kiba-Dock en lugar de Cairo? Cairo-Dock 2 tiene muchos más complementos que los que tenía Kiba, y más efectos (sacando akamaru, que los últimos meses no anduvo).[OT]

Saludos!

---

### Post by ALEXEX on 2009-08-20
> **santiagoward2000 said:**
> Hola!
Hace mucho que no uso Kiba-Dock, dejé de usarlo poco después que dejaran de actualizarlo, pero vamos a ver que me acuerdo:

[LIST]
[*]Las imágenes de los íconos estoy seguro que se pueden cambiar desde el menú para editarlos. Si hacés click derecho en el ícono que querés editar, debe haber alguna opción tipo editar o propiedades. Se debe editar de ahí.

[*]Sobre los temas, nunca ví nada prearmado. Kiba no tiene nada parecido al manejador de temas de Cairo-Dock, así que si encontrás alguno (aunque lo dudo) tendrías que copiarlo a la carpeta de configuración: ~/.kiba-dock

[*]Respecto a los complementos, no sé cómo lo hayas instalado. Cuando bajás el código para compilarlo, hay 4 paquetes:
[LIST]
[*]kiba-dock (que tiene lo básico para que ande)
[*]kiba-dock-plugins (ahí están casi todos los complementos que existen para Kiba, como papelera, reloj, monitor del sistema, etc.)
[*]kiba-dock-gaim (que es un complemento más, agrega un ícono para manejar gaim/pidgin)
[*]akamaru (el motor físico que en algún momento hizo que los íconos tengan efectos físico, pero que hace mucho que no anda)
[/LIST]No hay otros plugins oficiales, y dudo mucho que alguien haya hecho alguno no oficial, yo personalmente nunca ví.
[/LIST]
El proyecto Kiba-Dock está "congelado". El creador avisó que estaba ocupado y que no iba a poder trabajar en el proyecto por seis meses. Eso fue hace más de un año. Aunque no lo hayan hecho oficial, creo que el proyecto está abandonado, por lo que no tengo muchas esperanzas de que alguien se ponga a armar más complementos.
 
[OT]Perdón que me vaya de tema, ¿pero hay alguna razón por la que quieras usar Kiba-Dock en lugar de Cairo? Cairo-Dock 2 tiene muchos más complementos que los que tenía Kiba, y más efectos (sacando akamaru, que los últimos meses no anduvo).[OT]
 
Saludos!
 
 
Tengo el kiba, pero se me hace que de donde lo descarge no venia completo solo venia para instalarlo, no venia eso de los plugins, pero los buscare.
 
Ya e utilizado antes los tres mas conocidos: AWN, Kiba y Cairo, cairo fue el que mas me llamo la atencion por las tantas opciones que trae, pero al iniciar me aparece una ventana que si deseo utilizar GL o algo asi, le pongo que NO porque si le pongo que si, me aparece la barra de cairo de color negro y el efecto tipo MAC (desplegar mas opciones dentro de un icnono en la barra) tambien se pone el recuadro de color negro, cosa que se ve espantosa, quizas sea porque tengo una netbook y no soporta esa calidad de efectos, mi netbook tiene 128mb de video.
 
Saludos.

---

### Post by santiagoward2000 on 2009-08-20
> **ALEXEX said:**
> Tengo el kiba, pero se me hace que de donde lo descarge no venia completo solo venia para instalarlo, no venia eso de los plugins, pero los buscare.
 
Ya e utilizado antes los tres mas conocidos: AWN, Kiba y Cairo, cairo fue el que mas me llamo la atencion por las tantas opciones que trae, pero al iniciar me aparece una ventana que si deseo utilizar GL o algo asi, le pongo que NO porque si le pongo que si, me aparece la barra de cairo de color negro y el efecto tipo MAC (desplegar mas opciones dentro de un icnono en la barra) tambien se pone el recuadro de color negro, cosa que se ve espantosa, quizas sea porque tengo una netbook y no soporta esa calidad de efectos, mi netbook tiene 128mb de video.
 
Saludos.

El tema de la barra negra debe ser que no tenés ningún compositor activado. La verdad que no sé cómo se activa en GNOME, tal vez alguien más te pueda ayudar ahí. La otra es prender compiz, pero no sé cómo ande en una netbook (aunque 128MB de video tendría que andar, dependiendo de la marca de la placa). ¿No te aparecía la barra negra con Kiba o AWN también? Porque estoy seguro que también necesitan un compositor.
Para ver qué se puede hacer, podrías abrir una terminal, escribir **lspci** y postear el resultado, para ver de qué placa se trata y si hay que hacer algo para que ande.

Por los plugins de Kiba, hace años que no veo alguien que mantenga paquetes para instalarlo. Yo las últimas veces que lo instalé lo compilé guiándome con esta guía:
[http://ubuntuforums.org/showthread.php?t=554127]("http://ubuntuforums.org/showthread.php?t=554127")
Igual te aclaro que (como dice arriba) está probada para Gutsy, Feisty y Hardy, y yo en Intrepid no la pude hacer andar (y en Jaunty ni probé).

Saludos!

---

### Post by ALEXEX on 2009-08-21
Gracias Santiago por tu ayuda, me a servido de mucho.
 
Por fin pude personalizar bien el kiba a detalle, y me a quedado muy bien :P

---

### Post by santiagoward2000 on 2009-08-21
> **ALEXEX said:**
> Gracias Santiago por tu ayuda, me a servido de mucho.
 
Por fin pude personalizar bien el kiba a detalle, y me a quedado muy bien :P

Me alegro que te haya servido! :)
Espero verlo en el thread de escritorios.

---

