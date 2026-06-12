---
title: "[SOLVED] Primera (y ultima?) experiencia con Ubuntu"
date: 2009-08-10
forum: Software
---

### Post by sebadov on 2009-08-10
Buenas, paso a relatar mi primera experiencia con el SO en custión.
LLevado por las ideas del software libre, las cuales me parecen geniales y estoy totalmente de acuerdo, hace 2 dias instale ubuntu 9.04 en mi disco duro.
Para preparar mi disco para eso (un disco nuevo de 160 GB), desfragmenté y pase el scan disk de windows xp, todo salió ok.
Mi idea era conservar, por el momento, windows xp y ubuntu, en 2 particiones separadas, todo esto facil de hacer con la partición guiada que venia con la intalación. Luego de probar el sistema en live cd, lo instalé, sin ningun problema, dejandole 90 gb a windows y el resto a linux ubuntu.
Aqui comienzan los inconvenientes: al entrar por priimera vez a ubuntu, instalo los drivers de la tarjeta de video, geforce FX 5200, y aparecieron los efectos graficos (geniales). Baje el paquete compiz-config, y hasta aqui todo bien, pero al querer entrar en "Apariencia" no hacia nada, no cargaba la pestaña, sino que salia el manager update.
Decidi instalar las actualizaciones (como 139 mb), luego de esperar un buen rato, se emepzaron a instalar, pero al poco de empezar se interrumpe el proceso diciendome que "No se pudieron instalar todas", y ahi queda colgado el update manager. Resete la maquina y no pude entrar mas a ubuntu, ni siquiera en safemode (aparecia Failed en rojo y un monton de preguntas que no pudieron solucionar nada). Entre al live cd, elimine las particiones e intente reinstalar, antes de terminar la instalación me dice "Error de escritura en el disco, puede deberse a que parte de su disco esta dañado". En un disco nuevo que antes no habia dado errores!! A la particion de windows xp entraba sin problemas.
Intente reinstalarlo hasta que finalmente pude, pero cuando iniciaba ubuntu no cargaba partes del escritorio (barra de abajo y fecha) y salian multiples errores en gnome. Luego al cerrar sesión y reiniciar, no me dejo entrar más a ubuntu, ni siquiera en safemode (igual que antes)
Al final decidi arreglar el MBR de windows y eliminar las particiones desde livecd, ubuntu incluido.
En que me equivoque? Realmente quiero probar nuevamente ubuntu, pero no me animo, y no se si el disco duro no habrá quedado dañado, en parte.

---

### Post by pol666 on 2009-08-10
No creo, que se dañe el disco. Cuando vos de decis que carga y te tira fail quedaba una linea de comandos para escribir terminada en $ o en # ?

si es así podias arreglarlo desde ahi, pero bueno probablemente actualizaste driver de videos y no arrancaba el entorno grafico. Opino que vuelvas a instarlo y le des el update ANTES de instalar los drivr.

---

### Post by sebadov on 2009-08-10
Gracias por tu respuesta. Si, luego de fallar el inicio en safe mode, quedaba una linea de comando que terminaba en #, que segun entiendo es el usuario root, pero a decir verdad,  ni idea que podia yo poner para que inicie en safe mode, que no haya podido hacerlo el propio programa de forma automatica.
Estoy bajando el seatools para scannear el HD, si no me da errores, trataré de darme animos para volver a probar ununtu, pero no estoy seguro.
Lei por ahi que problemas con el grub y las particiones pueden provocar daños en el disco, es cierto?

---

### Post by staar on 2009-08-10
es un disco nuevo nuevo? es ide o sata? porque puede que esté fallando en serio y sea necesario repararlo o cambiarlo, podrías hacerle un chequeo a la superficie?

salduso

---

### Post by sebadov on 2009-08-10
Es nuevo nuevo (me lo trajeron hace 1 semana), es SATA 160 GB, el scandisk de windows no larga ningun resumen, pero corre hasta el final.

---

### Post by guillermolisi on 2009-08-10
> **sebadov said:**
> Lei por ahi que problemas con el grub y las particiones pueden provocar daños en el disco, es cierto?
No, absoluta y totalmente falso. Sin ningun tipo de fundamento y totalmente incoherente.

Todos pero todos los discos necesitan ser particionados para que un SO funcione.

Grub tambien fue adoptado por Windows desde el Vista en adelante.

Te parece que alguien seguiria desarrollando tecnologia en base a esto y mas aun, tanta gente la estaria usando si fuera como leiste por ahi ?

---

### Post by sebadov on 2009-08-10
Me alegro de que sea así, mucho mejor. No me refería a la herramienta en si, sino a un mal manejo de la misma. Lamento no recordar exactamente donde lo leí, seguramente algun foro o pregunta en ingles, sino te lo referiría. 
Aprvecho para reiterar que intento pasar a linux y al open source, pues comulgo absolutamente con su filosofía.

---

### Post by josecuervo86 on 2009-08-10
Te aclaro que no es lo mismo open source que free software. Capaz que ya lo sabes, pero si es asi, mucha filosofia no hay en el open source.

---

### Post by sebadov on 2009-08-10
Si, se como se separaron los terminos, por cierto, un muy buen documental "Revolution OS", lo vi por youtube.

---

### Post by staar on 2009-08-10
> **sebadov said:**
> Es nuevo nuevo (me lo trajeron hace 1 semana), es SATA 160 GB, el scandisk de windows no larga ningun resumen, pero corre hasta el final.
justamente, cuando es nuevo es cuando se manifiestan las fallas de fabricación, scandisk era el de Ventanas 98, el de ahora es chkdsk (que nombrecito :-P), lo corriste con test de superficie (el que tarda mucho)? porque si no solo está verificando el sistema de archivos...

saludos

---

### Post by sebadov on 2009-08-10
> **staar said:**
> justamente, cuando es nuevo es cuando se manifiestan las fallas de fabricación, scandisk era el de Ventanas 98, el de ahora es chkdsk (que nombrecito :-P), lo corriste con test de superficie (el que tarda mucho)? porque si no solo está verificando el sistema de archivos...

saludos


Accedi mediante propiedades---->herramientas--->Comprobacion de errores

Me hizo un analisis en 4 etapas, la ultima de las cuales tardó bastante, asi que imagino que si hizo analisis de superficie, no me aparece la opcion de test de superficie. Gracias por tu respuesta.
A proposito, el scandisk de Ventanas 98 (como vos le decis jeje) parecia mucho mas serio y utilitario que este chkdsk de Ventanas XP, tiene mucha pinta de berreta, ni siquiera sale un resumen final como el otro.

---

### Post by nopersona on 2009-08-10
Hubiese sido interesante saber específicamente el fallo, "no se pudieron instalar todas" no ayuda mucho a diagnosticar el problema. Puede que hasta dejado algún kernel incompleto o quizás qué. 

Repito, lo mejor hubiese  sido conocer el problema, para dar palos ciegos sobran impotesis. Mi consejo, instalación limpia, posteo de pasos de instalación y atento para anotar ese posible fallo. :P

---

### Post by sebadov on 2009-08-10
Recien pase el Seatools y el disco no paso una sola prueba :(. 
Baje el HD Health y me da una salud del 64%. Asi que hasta aqui llego mi disco duro nuevo supongo, cabe la posibilidad, como decian mas arriba, de un defecto de fabricación.

PD: el mensaje de error en la instalación fallida de actualizacionens fue ese: "No se pudieron actualizar todos los componentes" al poco de iniciarse. No habia mas detalles.

---

### Post by staar on 2009-08-10
OJO, es un seagate, no? sino, pasale la herramienta que provee el fabricante del disco, no la de otro...

si es un seagate, lo lamento por tu disco nuevo, casi seguro es un defecto de fabricación (no puede romperse porque si a la semana), intentá que te lo cambien por uno nuevo...

saludos

---

### Post by sebadov on 2009-08-11
> **staar said:**
> OJO, es un seagate, no? sino, pasale la herramienta que provee el fabricante del disco, no la de otro...

si es un seagate, lo lamento por tu disco nuevo, casi seguro es un defecto de fabricación (no puede romperse porque si a la semana), intentá que te lo cambien por uno nuevo...

saludos

Si, la idientificacion del disico comienza con ST y la herramienta lo reconoció. Veré que puedo hacer. Gracias por tu ayuda Staar, y a los demás también.

---

