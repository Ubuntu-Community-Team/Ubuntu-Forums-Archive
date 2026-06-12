---
title: "Flash hunde a Firefox"
date: 2008-12-19
forum: Software
---

### Post by hictio on 2008-12-19
Hoy instale estos updates:

```

2008-12-19 12:27:10 status installed man-db 2.5.2-2
2008-12-19 12:27:10 status installed doc-base 0.8.16
2008-12-19 12:27:11 status installed ufw 0.23.2
2008-12-19 12:27:12 status installed avahi-autoipd 0.6.23-2ubuntu2.1
2008-12-19 12:27:12 status installed libavahi-common-data 0.6.23-2ubuntu2.1
2008-12-19 12:27:12 status installed libavahi-common3 0.6.23-2ubuntu2.1
2008-12-19 12:27:13 status installed libavahi-core5 0.6.23-2ubuntu2.1
2008-12-19 12:27:13 status installed avahi-daemon 0.6.23-2ubuntu2.1
2008-12-19 12:27:13 status installed libavahi-client3 0.6.23-2ubuntu2.1
2008-12-19 12:27:13 status installed avahi-utils 0.6.23-2ubuntu2.1
2008-12-19 12:27:13 status installed libavahi-compat-libdnssd1 0.6.23-2ubuntu2.1
2008-12-19 12:27:13 status installed libcups2 1.3.9-2ubuntu4
2008-12-19 12:27:13 status installed libcupsimage2 1.3.9-2ubuntu4
2008-12-19 12:27:13 status installed cups-common 1.3.9-2ubuntu4
2008-12-19 12:27:16 status installed cups 1.3.9-2ubuntu4
2008-12-19 12:27:16 status installed cups-client 1.3.9-2ubuntu4
2008-12-19 12:27:17 status installed cups-bsd 1.3.9-2ubuntu4
2008-12-19 12:27:17 status installed xulrunner-1.9 1.9.0.5+nobinonly-0ubuntu0.8.10.1
2008-12-19 12:27:17 status installed xulrunner-1.9-gnome-support 1.9.0.5+nobinonly-0ubuntu0.8.10.1
2008-12-19 12:27:44 status installed flashplugin-nonfree 10.0.15.3ubuntu1~intrepid1
2008-12-19 12:27:45 status installed libavahi-glib1 0.6.23-2ubuntu2.1
2008-12-19 12:27:45 status installed libavahi-gobject0 0.6.23-2ubuntu2.1
2008-12-19 12:27:45 status installed libavahi-ui0 0.6.23-2ubuntu2.1
2008-12-19 12:27:45 status installed libgadu3 1:1.8.0+r592-1ubuntu0.1
2008-12-19 12:27:45 status installed liblcms1 1.16-10ubuntu0.1
2008-12-19 12:27:45 status installed firefox-3.0-branding 3.0.5+nobinonly-0ubuntu0.8.10.1
2008-12-19 12:27:45 status installed firefox-3.0 3.0.5+nobinonly-0ubuntu0.8.10.1
2008-12-19 12:27:45 status installed firefox-3.0-gnome-support 3.0.5+nobinonly-0ubuntu0.8.10.1
2008-12-19 12:27:45 status installed firefox 3.0.5+nobinonly-0ubuntu0.8.10.1
2008-12-19 12:27:45 status installed firefox-gnome-support 3.0.5+nobinonly-0ubuntu0.8.10.1
2008-12-19 12:27:45 status installed libc6 2.8~20080505-0ubuntu7

```

Rebootee, para estar seguro de aplicar el update de login, y ademas, por lo general, en la laptop la rebooteo despues de casi todos los updates... En fin, segui usando la maq.
Flash no me gusta y lo bloqueo con la extension de Firefox, pero tenia que ver un site por trabajo, y note que despues que cargo Ok, Firefox se murio, solo se podia minizar la ventana.
Pense que era algo de ese site en particular o un prblema pasajero.

Segui usando la maquina, y tuve que ver otro site con Flash, la misma cosa; la unica solucion, hacer un Force Quit de Firefox.

Todo indica que hay un problema con 'flashplugin-nonfree 10.0.15.3ubuntu1~intrepid1'...

A alguien mas le esta pasando?

---

### Post by luks911 on 2008-12-19
Tuve esas actualizaciones, pero no me acuerdo si llegué a reiniciar Firefox, mmm.... Llego a casa, me fijo y cuento, por lo pronto podes forzar el paquete a la versión anterior.

---

### Post by hictio on 2008-12-19
Mhmhh... Preferiria no tener que forzar la instalacion de nada que no esta "empujando" oficialmente Ubuntu para Intrepid.

Este seria el segundo problema que tengo con Intrepid, y el primero que aparece a raiz de un update, el primer porblema es constante, y lo [vengo arrastrando](http://ubuntuforums.org/archive/index.php/t-969646.html) desde el dia uno de la instalacion.

---

### Post by KrossX on 2008-12-20
Podrías colocar la dirección del sito que provoca el problema con Firefox?

Estoy usando Firefox 3.0.5 con Flash 10 x86-64 (prueba) y no he tenido problemas grandes con flash.

---

### Post by totolinux on 2008-12-20
hola mi problema es que luego de agregar flash los sites con flash me apagan directamente firefox ( con mensaje de error)o no veo las paginas completas

---

### Post by totolinux on 2008-12-20
perdon agrego [www.personal.com.ar](www.personal.com.ar) (incompleta)
[www.youtube.com](www.youtube.com) (salida abrupta mensaje de error fue violación de segmento)
mi sistema es amd sempron, ram 512, ubuntu 8.04, firefox actualizado

---

### Post by KrossX on 2008-12-20
Ningún problema aquí, en absoluto. (y eso que Flash64 es alpha)

Prueba con un perfil nuevo del Firefox.

---

### Post by totolinux on 2008-12-20
solucionados mis cierres frecuentes y puedo ver los sites completos.
encontre la solución en este blog [http://labs.adobe.com/technologies/flashplayer10/](http://labs.adobe.com/technologies/flashplayer10/)
y luego descargar desde aca [http://get.adobe.com/es/flashplayer/](http://get.adobe.com/es/flashplayer/)           el paquete .deb para ubuntu 8.04 luego reinicié Firefox y listo.
gracias por ayudarme.:)

---

### Post by KrossX on 2008-12-20
Que bién! Sólo había que reinstalar/actualizar el plugin flash? 
A veces uno se olvida de lo básico. XD

---

### Post by lucasfava on 2008-12-20
Mi problema es con youtube, yo puedo ver la pagina de personal, pero cuando voy a youtube,tardan mucho en aparecer y habeces se escucha es sonido que la imagen esta parada

---

### Post by luks911 on 2008-12-20
> **hictio said:**
> Mhmhh... Preferiria no tener que forzar la instalacion de nada que no esta "empujando" oficialmente Ubuntu para Intrepid.

Este seria el segundo problema que tengo con Intrepid, y el primero que aparece a raiz de un update, el primer porblema es constante, y lo [vengo arrastrando](http://ubuntuforums.org/archive/index.php/t-969646.html) desde el dia uno de la instalacion.

Bien, pude probarlo y sigue todo bien. Con forzar me refiero a decirle a ubuntu que se quede con la versión anterior del paquete, que es la que funciona bien. Yo lo había hecho justo con flash en hardy porque algunas páginas no las veía bien después de una actualización.
Vas a Synaptic, buscás flashplugin-nonfree, das un click sobre el paquete para seleccionarlo y vas al menú Paquete > Forzar versión (o Ctrl+E) y en el menú desplegable que te aparece elegís la versión anterior a la última. Luego, click al botón Forzar versión: lo que hace es desinstalar la última versión, instalar la previa e ignora próximas actualizaciones. Por supuesto, cuando quieras podés desbloquear el paquete para actualizarlo. Por ejemplo, en caso de que con una versión más nueva funcione bien.

---

### Post by hictio on 2008-12-20
No entiendo... Ahora no pasa mas, esta funcionando perfectamente (perfectamente para lo que es Flash, verdad? El CPU se lo sigue comiendo como un caramelito) pero no hay crash, ni nada raro.

Lo mas raro, a la laptop no la rebooteo desde es el reboot luego de la instalacion de los updates, asi que por ahi no viene el problema/ solucion; el Firefox si lo cerre y abri varias veces; pero al parecer, recien ahora esta andando correctamente.

Uno de los sitios que me daba problemas era la pagina de Warner Channel, wbla.com, pero ahora me esta andando todo Ok...

---

### Post by sergiom99 on 2008-12-20
> **totolinux said:**
> solucionados mis cierres frecuentes y puedo ver los sites completos.
encontre la solución en este blog [http://labs.adobe.com/technologies/flashplayer10/](http://labs.adobe.com/technologies/flashplayer10/)
y luego descargar desde aca [http://get.adobe.com/es/flashplayer/](http://get.adobe.com/es/flashplayer/)           el paquete .deb para ubuntu 8.04 luego reinicié Firefox y listo.
gracias por ayudarme.:)

voy a pegarle una mirada. gracias!

PS: vos sos veterinario? yo casi!

---

### Post by totolinux on 2009-01-04
si soy vet desde hace 5 años.y ubuntero desde hace 2
contà si se solucionó el problema :D.

---

### Post by andy_91 on 2009-01-04
a mi en ubuntu hardy con kazehakase me anda inestable el flash, de vez en cuando se me cuerra solo el explorador(eso tambien me paso un par de veces con el firefox) y no puedo visualizar algunas webs completas.

tambien tengo problemas con el gmail, la vercion es la 10 creo la ultima que esta en los repos de hardy

---

### Post by MeduZa on 2009-01-05
a mi me empezo a hacer que todo anda pero en youtube si paso a pantalla completa se cierra el seamonkey (hermano del FF 3.0)

---

