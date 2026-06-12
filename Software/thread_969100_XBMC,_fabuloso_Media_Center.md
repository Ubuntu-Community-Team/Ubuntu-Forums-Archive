---
title: "XBMC, fabuloso Media Center"
date: 2008-11-03
forum: Software
---

### Post by User21 on 2008-11-03
[CENTER][IMG]http://xbmc.org/gfx/features/rect_xbmc.jpg[/IMG]
[/CENTER]

[XBMC Media Center]("http://xbmc.org/") (XBMC) superó mis espectativas. No solo se ve bien, sino que funciona con casi cualquier formato que haya probado. Es MUY FACIL de usar, tiene un acabado casi profesional y es muy amigable con Ubuntu. En mi busqueda por el **ultimate media center**, puedo decir que XBMC está casi al limite de ser perfecto. Pruebenlo! :)
Incluso, lo puedo instalar en una particion de mi disco externo usb, y usarlo como un SO. Aparte, cuenta no solo con la instalación en Ubuntu, sino que tambien tiene un LIVE CD basado en Hardy Heron 8.04.1. Tan solo inserta el cd live, y convierte tu PC en un fabuloso centro multimedia. Este soporta particiones EXT3, FAT32, NTFS, VFAT, entre otras. Además,  trae pre instalado los drivers de Nvidia, ATI e Intel. 
Imperdible :) 

[**Ver Screenshots**]("http://www.flickr.com/photos/29133065@N05/")
[**Mas información**]("http://xbmc.org/about/")

---

### Post by niko_3100 on 2008-11-03
Ya lo estoy bajando... 77 megas?? debe ser muy groso el programita jeje!

---

### Post by User21 on 2008-11-03
Solo debes agregar los siguientes repositorios:

**GUTSY PPA :**
```
deb [http://ppa.launchpad.net/team-xbmc-gutsy/ubuntu](http://ppa.launchpad.net/team-xbmc-gutsy/ubuntu) gutsy main
deb-src [http://ppa.launchpad.net/team-xbmc-gutsy/ubuntu](http://ppa.launchpad.net/team-xbmc-gutsy/ubuntu) gutsy main 
```
**HARDY PPA :**
```
deb [http://ppa.launchpad.net/team-xbmc-hardy/ubuntu](http://ppa.launchpad.net/team-xbmc-hardy/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/team-xbmc-hardy/ubuntu](http://ppa.launchpad.net/team-xbmc-hardy/ubuntu) hardy main 
```
y luego, ejecuta:
```
sudo apt-get install xbmc
```

A la espera de los repos de Intrepid! u_U

---

### Post by vk-cdg on 2008-11-03
Yo lo probé y tanto en la note como en la desktop anda medio como raro, el cursor se mueve como con un delay y no me reconce bien algunos comandos, pero debe ser algo particular imagino.

---

### Post by vk-cdg on 2008-11-03
Yo lo probé y tanto en la note como en la desktop anda medio como raro, el cursor se mueve como con un delay y no me reconce bien algunos comandos, pero debe ser algo particular imagino.

---

### Post by niko_3100 on 2008-11-04
a mi tambien me paso, pero lo probe en una pentium 4 del laburo que se arrastra... no entiendo como puede ser tan malo un procesador asi..

---

### Post by spg76 on 2008-11-05
La última versión (XBMC &#8216;Atlantis&#8217; Beta 2) mejoro muchisimo el rendimiento y el skin [Mediastream]("http://www.teamrazorfish.co.uk/mediastream.html") es sencillamente hermoso.
Igual sigo teniendo algunos pequeños problemas que calculo tendrán que ver con que estoy corriendo la versión de Hardy en Intrepid y que es una versión Beta.

---

### Post by Applelnx on 2008-11-05
Disculpame, como era para agregar el repositorio? :S

---

### Post by spg76 on 2008-11-05
Acaba de salir el repositorio para Intrepid.

```
deb http://ppa.launchpad.net/team-xbmc-intrepid/ubuntu intrepid main
deb-src http://ppa.launchpad.net/team-xbmc-intrepid/ubuntu intrepid main
```

> **Applelnx said:**
> Disculpame, como era para agregar el repositorio? :S
Las dos opciones más fáciles son:
1."Sistema>Administración>Orígenes del software". Una vez abierto, "Software de terceros>Añadir..." y agregas el repositorio.
2."Sistema>Administración>Gestor de Paquetes Synaptic". Una vez abierto, "Configuración>Repositorios>Software de terceros>Añadir..." y agregas el repositorio.
Espero que te sirva.

---

### Post by MeduZa on 2008-11-06
> **spg76 said:**
> Acaba de salir el repositorio para Intrepid.

```
deb http://ppa.launchpad.net/team-xbmc-intrepid/ubuntu intrepid main
deb-src http://ppa.launchpad.net/team-xbmc-intrepid/ubuntu intrepid main
```


Las dos opciones más fáciles son:
1."Sistema>Administración>Orígenes del software". Una vez abierto, "Software de terceros>Añadir..." y agregas el repositorio.
2."Sistema>Administración>Gestor de Paquetes Synaptic". Una vez abierto, "Configuración>Repositorios>Software de terceros>Añadir..." y agregas el repositorio.
Espero que te sirva.

y la forma dificil y pro:
sudo gedit /etc/apt/sources.list
y pegas 
deb [http://ppa.launchpad.net/team-xbmc-intrepid/ubuntu](http://ppa.launchpad.net/team-xbmc-intrepid/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/team-xbmc-intrepid/ubuntu](http://ppa.launchpad.net/team-xbmc-intrepid/ubuntu) intrepid main
al final de todo guardas y haces update en los paquetes.
xD

---

### Post by niko_3100 on 2008-11-06
la forma dificil?? creo que es la forma mas facil y la adecuada, sin abrir tantas ventanitas ni buscar donde esta esa opcion... que mejor que un archivo de texto plano,bien sencillo y facil y mas linuxero.

---

### Post by User21 on 2008-11-06
A mi me salió como cachetada la version Beta y la sigo usando sin problemas!!! 
Estoy enamorado del XBMC :P

AMD X2 4600+  
2 GB RAM DDR2 
Nvidia 8500 GT
MB ASUS M2N-VM DVI

---

### Post by Tosh78 on 2008-11-06
Gente, cuando quiero intentar instalarlo me dice que no encuentra el paquete XBMC, a pesar de haber recargado una vez que agregue el repositorio, a alguno le paso?

---

### Post by Applelnx on 2008-11-06
No lo encuentra puede ser? Me fije en los repositorios y los pegue bien. 
:confused:

Edit: no dije nada, me olvide de racargar :P

Gracias, probando....

---

### Post by Tosh78 on 2008-11-07
Ahi me funciono. No se por que, pero tuve que sacar los repositorios, recargar, agregarlos otra vez, recarga y ahi pude instalarlo. Me gusta mucho, pero como que se me traba todo, alguna idea de como hacerlo funcionar mas rapido? Otra cosa es que no pude ver un archivo .avi hay que hacer algo en especial para eso?

---

### Post by Applelnx on 2008-11-07
Digamos que me "funciona", imaginense que tengo una placa de video integrada de 64 mb y los drivers de ati no funcionan. tendre que esperar una maquina mas potente.

---

### Post by majatu on 2008-11-07
Simplemete FANTASTICO! muy lindo a la vista, bien logrado y funcional!

Me encanto! super recomendable!

---

### Post by sartrejp on 2008-11-09
Ya lo pruebo. Tuve problemas con el audacious y estoy escuchando música con xmms, una reliquia jejej

---

### Post by lega on 2008-11-16
salio la version final anda mucho mejor, al menos el puntero del mouse no se arrastra como me pasaba en otra version que habia instalado en Hardy :)

---

### Post by User21 on 2008-11-17
See, la nueva versión está DE LUJO! :D  Aunque me gustaba más el anterior juego de iconos...

---

### Post by sartrejp on 2008-11-17
Ahora si da gusto, la beta me andaba más o menos. Muy bueno la verdad (aunque para la música insisto con el xmms)

---

### Post by User21 on 2008-11-18
Finalmente, un verdadero Media Center! :P Ayer, en un ataque de locura, me compré un [**home theatre**]("http://www.eurocase.com/version3/archivos/productos2/20/eup5_02_nilo_5.jpg") [Euro Case]("http://www.eurocase.com/version3/index.php?productos=si&nivel=3&id_producto=329&id_rubro=6&id_subrubro=10") por unos 300 manguitos. Sin duda, un módico precio para este tipo de equipos. Me sorprendió el desempeño y fidelidad de los chiquitines. Si alguien anda en vista de comprarse un HT y como yo, siempre anda regañando presupuesto, es una MUY BUENA OPCION ! Se lleva de lujo con el Ubuntin y XBMC hace de fantastico intermediario cuando solo quiero disfrutar de mi multimedia. :)
 
Si les interesa, [puse un post de sonido 5.1]("http://ubuntuforums.org/showthread.php?goto=newpost&t=984681"), por las dudas...

---

