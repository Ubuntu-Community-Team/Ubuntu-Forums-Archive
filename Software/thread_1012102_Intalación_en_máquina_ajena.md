---
title: "Intalación en máquina ajena"
date: 2008-12-15
forum: Software
---

### Post by fgl82 on 2008-12-15
¡Hola!

Estoy por volarle el Windows lleno de spyware y demás bichos dañinos a mi hermano de su PC (con su consentimiento, por supuesto) y hay dos cosas que me interesaría saber si puede hacer en Linux:

1) Jugar al Counter Strike 1.6 con Wine sin problemas
2) Utilizar algún programa del estilo del guitar pro (¿existe alguno? Tener en cuenta que es apenas un aficionado)

¡Gracias!

---

### Post by Mauro22 on 2008-12-15
1) Yo lo he jugado por varias horas y ningun problema :D

2) No te puedo ayudar, pero si mal no recuerdo, se hizo un post.

---

### Post by c4d0rn4 on 2008-12-15
frets on fire es el guitar hero de pc que es opensource y esta para todos los OS

[http://fretsonfire.sourceforge.net/](http://fretsonfire.sourceforge.net/)

Si agregas playdeb a los source lo podes instalar con apt-get o synaptic.

---

### Post by fgl82 on 2008-12-15
> **c4d0rn4 said:**
> frets on fire es el guitar hero de pc que es opensource y esta para todos los OS

[http://fretsonfire.sourceforge.net/](http://fretsonfire.sourceforge.net/)

Si agregas playdeb a los source lo podes instalar con apt-get o synaptic.

No, no Guitar Hero, Guitar Pro :P

Al frets lo conozco y lo he jugado.

---

### Post by NickCis on 2008-12-15
Parecidos al guitar pro, hay varios, el tuxguitar y el Kguitar.
Al Kguitar ([http://kguitar.sourceforge.net/](http://kguitar.sourceforge.net/)) le falta mucho, lo probe y deja que desear.
El mejor es el Tuxguitar ([http://www.tuxguitar.com.ar/](http://www.tuxguitar.com.ar/)), que si lo usas solo para ver tabs del guitar pro (*.gp3 *.gp4 *.gp5), se podria decir que no tiene nada de envidiarle al Guitar Pro, salvo el RSE. Pero si lo usas para componer, puede a llegar a ser MUY molesto.
Claro, siempre tenes la opcion de emular el guitar pro con el wine + timidity, seguirias sin tener el RSE, pero tenes todas las funciones del Guitar Pro. 
Ak tenes info de como hacer el Gp: [http://appdb.winehq.org/objectManager.php?sClass=application&iId=246](http://appdb.winehq.org/objectManager.php?sClass=application&iId=246)

Y de yapa, te dejo una muy buena pagina para las tabs: [www.911tabs.com](www.911tabs.com).

Saludos.

---

### Post by NickCis on 2008-12-15
Recien probe hacer andar el guitar Pro con el wine, y la verdad me sorprendio, hasta anda el RSE.
Lo que yo hice es ya que lo tenia instalado en la particion de windows, abria la consola ponia "cd /media/disk/Archivos\ de\ programa/Guitar\ Pro\ 5" y ahi "wine GP5.exe". Ahi andaba todo bien, se escuchaba sin la nececidad del Timidity, y podia usar el RSE. Los problemas eran que se tildaba a los 5 segundos de abrirlo y que no podia ver las las notas en la seccion de partituras (si ponia que me muestre el puente de la guitarra, o el tecladito podia ver las notas).
Para solucionar lo que se tildaba, simplemente tuve que tocar control+c (en la terminal que esta ejecutando el GP5.exe), el Guitar Pro me tiraba un par de errores, le daba todo Ok, hasta que se destildaba magicamente (xD).
******
Y copiando el guitar pro del windows a la carpeta del wine (reemplazando el recien instalado), tengo guitar pro con Rse y que se ve bien :D.
Lo unico malo de esto, es que siempre lo tenes que abrir por consola y tocar control+c, pero tenes RSE, y creo que te ahorras instalar el Timidity.

Saludos.

P.D.: Pregunta mas si te resulto confusa la explicacion. Ahh y me olvidaba tengo el wine 1.1.9, que simula el windows Xp.

Offtopic: Si te interesa, con el wine tambien podes hacer andar el Band In a Box, pero si vas a nececitar el Timidity.

Edit: Si es necesario el Timidity, pero el Rse anda igual.

---

### Post by fgl82 on 2008-12-16
Gracias por la info.

Yo no entiendo nada, supongo que mi hermano sabrá lo que es timidity y demás.

Hei Ku, muy correcta tu advertencia, si querés borrá los links.

---

### Post by NickCis on 2008-12-16
Bueno, perdonen por lo de los links.
El timidity es un secuenciador midi, lo que hace es que el Guitar Pro, ya que el wine no puede hacer sonar sus sonidos, los transmite por midi al Timidity.
Si buscas en google como instalarlo vas a encontra mucha informacion, por que la mayoria de programas de musica (band in a box, guitar pro, etc), nececitan de este para que hagan musica...

Saludos.

---

### Post by User21 on 2008-12-17
Es muy factible que hagas funcionar Counter Strike con wine, con una buena guia, googleando.. pero **NO FUNCIONAN** los anticheats, por lo que** NO SE PUEDE JUGAR ONLINE**, por lo menos, en servidores seguros o con tecnologia anticheat. En aquellos donde no se exija anticheat, podes entrar libremente, pero son los menos y estan infectados de tramposos!

---

### Post by fgl82 on 2008-12-17
Eso! Eso! Eso queria saber! El Cheating Death tampoco?

---

