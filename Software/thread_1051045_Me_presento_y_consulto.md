---
title: "Me presento y consulto"
date: 2009-01-26
forum: Software
---

### Post by enrimaiden on 2009-01-26
Hola a todos, soy completamente nuevo en Linux y ya me está gustando mucho, pero como es natural, hay muchos conceptos que aun no manejo. Para no molestar y agobiar a la comunidad de entrada voy a remitirme a hacer dos consultas.
Soy usuario de Ubuntu 8.10 AMD64 (sisi, estuve leyendo las ventajas y desventajas de esta arquitectura; pude hacer andar el plugin de flash, el de java todavia ni lo toque!)
Lo que me pasa son dos cosas distintas:
Numero 1: Una de las cosas que me atrajo de inmediato del sistema operativo es su GUI y la mulitiplicidad de configuraciones que ofrece sin consumir demasiados recursos (tengo 1gb de RAM asi que le pongo todos los chiches de efectitos y eso) Asi que ni bien pude instalar mi modem NDS1060USB siguiendo [esta utilísima guía]("http://ar.geocities.com/novatocba/doc/frame/modem-7-04.htm") que recomiendo a cualquier principiante como yo que necesite instalar un modem USB con el chipset eagle, ni bien hice eso digo, me puse a buscar temas de escritorio en Gnome Look, pero la verdad es que paquete que bajo de ese lugar, paquete que no puedo instalar de ningun modo: ni comprimido ni descomprimido. Vi que hay diferentes categorias a la izquierda segun la GUI que se use (creo que yo tengo que descargar los que son para GDE no?) Bueno, asi y todo no me funcan, agradezco si me explican o si me mandan a un thread o tutorial para hacerlo yo.

Numero 2 (y mas importante): Ni bien tuve conexion a internet el gestor de actualizaciones me pidio que descargar 235MB de actualizaciones! Mi pregunta es ¿es necesario descargar absolutamente todo lo que sugiere el gestor? Y, si no lo es, ¿que es lo esencial?
Despues de hacer semejante actualización, lo que me pasó fue que reinicie y ahora tengo dos kernels distintos para bootear, uno que 2.x.x.x.7 y el otro 2.x.x.x.9 (mas o menos) ¿Como hago para que haya solo un kernel para elegir? No quiero que mi lista de booteo se extienda ad infinitum con cada actualizacion de Kernel!.

Desde ya muchas gracias por su ayuda, y viva Linux y Ubuntu que cumple las mismas funciones que cualquier otro sistema operativo eficientemente y encima gratis! Linux debiera ser instalado por ley en todos los sistemas de organismos estatales, sobre todo en paises explotados como el nuestro! :D

---

### Post by staar on 2009-01-26
Hola, bienvenido a ubuntu!, te explico, ubuntu usa un entorno de escitorio que se llama gnome, lo que bajas de gnome-look son varias cosas, estan los temas Gtk, que cambian lo que seria el aspecto de las barras de herramientas, ventanas, cuadros de dialogo, controles, botones, etc, despues estan los paquetes de iconos, los temas gdm (que cambian el aspecto de la pantalla de login), los temas metacity y emerald (que cambian los bordes y la parte superior de las ventanas), y varias mas.
Para instalar los temas gtk, los paquetes de iconos, y las decoraciones metacity (no las emerald), tenes que ir a Sistema -> Preferencias -> Apariencia y arrastrar los archivos comprimidos (tar.gz o tar.bz2) sobre la ventana (si no, usar el boton instalar tema :P), las gdm se instalan desde Sistema -> Preferencias -> Ventana de Entrada

A las actualizaciones te recomiendo que las instales todas porque estan para corregir errores y agregar funciones a los programas, pero si queres podes saltearte las de los programas que no uses (ejemplo, yo no uso thunderbird y por eso ni me gasto en actualizarlo)

Lo de los kernels, instala el programa Startup Manager, buscalo en el Synaptic, que te permite editar la configuracion del inicio, principalmente Grub (bootloader de ubuntu, el menu ese que aparece al principio) y la usplash (la barrita que carga y dice ubuntu :D), en ese programa tenes una opcion para dejar tantos kernels como quieras en el grub

saludos

---

### Post by enrimaiden on 2009-01-26
> **staar said:**
> Hola, bienvenido a ubuntu!, te explico, ubuntu usa un entorno de escitorio que se llama gnome, lo que bajas de gnome-look son varias cosas, estan los temas Gtk, que cambian lo que seria el aspecto de las barras de herramientas, ventanas, cuadros de dialogo, controles, botones, etc, despues estan los paquetes de iconos, los temas gdm (que cambian el aspecto de la pantalla de login), los temas metacity y emerald (que cambian los bordes y la parte superior de las ventanas), y varias mas.
Para instalar los temas gtk, los paquetes de iconos, y las decoraciones metacity (no las emerald), tenes que ir a Sistema -> Preferencias -> Apariencia y arrastrar los archivos comprimidos (tar.gz o tar.bz2) sobre la ventana (si no, usar el boton instalar tema :P), las gdm se instalan desde Sistema -> Preferencias -> Ventana de Entrada

A las actualizaciones te recomiendo que las instales todas porque estan para corregir errores y agregar funciones a los programas, pero si queres podes saltearte las de los programas que no uses (ejemplo, yo no uso thunderbird y por eso ni me gasto en actualizarlo)

Lo de los kernels, instala el programa Startup Manager, buscalo en el Synaptic, que te permite editar la configuracion del inicio, principalmente Grub (bootloader de ubuntu, el menu ese que aparece al principio) y la usplash (la barrita que carga y dice ubuntu :D), en ese programa tenes una opcion para dejar tantos kernels como quieras en el grub

saludos

Loco buenisima onda! Me viene al pelo lo que me explicaste, ya me baje el Startup manager y acomode eso que necesitaba, ademas me da la opcion de poner por defecto el windows (eso me viene bien para cuando tiene que usar la maquina mi vieja que no la veo con muchas ganas de experimentar con un nuevo SO, sobre todo considerando que ni debe saber lo que es un SO jaja)
Lo de los temas, menos mal que me explicaste como se subdividen los paquetes porque era exactamente eso lo que necesitaba! Intuía algo por el estilo pero no terminaba de comprender, ahora tengo todo lo necesario para hacerlo.:p

Te dejo un abrazo de agradecimiento y o dudes en que estare por aqui en breve hinchando las bolas! JA!
Ah, miraste la guia que deje más arriba? Creo que puede ser util a usuarios newbies como yo!

Saludos!

---

### Post by staar on 2009-01-26
de nada che! ahora me fije en esa guia, la verdad que no conocia esa pagina, pero es muy buena, muy explicativa, y es de un cordobé :D, lastima que no la va a actualizar mas...

cuando termines de personalizar tu ubuntu, no dudes en mostrarnos tu escritorio en el thread del foro ;), esta en los stickys

saludos

---

### Post by enrimaiden on 2009-01-27
> **staar said:**
> de nada che! ahora me fije en esa guia, la verdad que no conocia esa pagina, pero es muy buena, muy explicativa, y es de un cordobé :D, lastima que no la va a actualizar mas...

cuando termines de personalizar tu ubuntu, no dudes en mostrarnos tu escritorio en el thread del foro ;), esta en los stickys

saludos

Bueno, ahi de a poco voy cambiando el look del escritorio :p pero tengo algunos inconvenientes. Lo que me pasa es que por mas que puedo instalar algunos temas se ven "de a pedazos". Quiero decir, por ahi me anda el metacity pero no los iconos, o la combinacion de colores y otras cosas no. En la ventana de "temas" tengo un aviso que dice que me falta el "motor de temas GTK+ <<aurora>> " asi que me baje unos paquetes que decian GTK engine pero hay tantos que estoy confundido. Encima la instalacion de ese paquete se me colgo a la mitad y no tiro ningun mensaje de error y el gestor lo marca como instalado correctamente. Esa es mi situación, ahora escucho sus sugerencias!

P.D: Adjunto pic de mi escritorio con lo que pude hacer hasta la fecha (combinando partes de temas distintos) y ademas una captura de los paquete GTK que tengo instalados.

Desde ya muchas gracias!

---

### Post by SLA_leandrin on 2009-01-27
> **enrimaiden said:**
> 
Despues de hacer semejante actualización, lo que me pasó fue que reinicie y ahora tengo dos kernels distintos para bootear, uno que 2.x.x.x.7 y el otro 2.x.x.x.9 (mas o menos) ¿Como hago para que haya solo un kernel para elegir? No quiero que mi lista de booteo se extienda ad infinitum con cada actualizacion de Kernel!

Para esto, lo mas fácil en vez de estar instalando el startupmanager, sería que edites manualmente la lista que te sale en el grub (el gestor de inicio). Para esto hacé lo siguiente;

```
sudo gedit /boot/grub/menu.lst
```

ahí se te abre el archivo que tiene la lista que muestra al iniciar la pc. Lo que no querés que te salga, simplemente le anteponés el # y listo.

---

### Post by staar on 2009-01-27
mmm... el motor que te pide no aparece como instalado en la captura (un consejo, no uses la busqueda rapida de Synaptic, no es muy buena, mejor usa el boton buscar) el paquete se llama gtk2-engines-aurora, fijate

OJO, a las aplicaciones de root (todas las que te piden pass al abrirlas, como Synaptic) no se les aplica el tema que tenes porque en realidad son aplicaciones de otro usuario, el root, para que tengan el mismo tema e iconos necesitas crear enlaces de las carpetas .icons y .themes (estan en tu home, pero ocultas, por eso el punto adelante) a lo que seria el home del root, la carpeta /root/, para eso tenes que correr en una consola estos tres comandos:

```
sudo ln -s ~/.themes /root/.themes 
sudo ln -s ~/.icons /root/.icons 
sudo ln -s ~/.fonts /root/.fonts
```

otro OJO, muchos de los paquetes de iconos de gnome-look estan incompletos, los iconos faltantes se suplantan con el tema por defecto de gnome (puaj :P), los packs completos, generalmente pesan, minimo, de 20 MB para arriba

saludos ;)

---

### Post by enrimaiden on 2009-01-28
> **SLA_leandrin said:**
> Para esto, lo mas fácil en vez de estar instalando el startupmanager, sería que edites manualmente la lista que te sale en el grub (el gestor de inicio). Para esto hacé lo siguiente;

```
sudo gedit /boot/grub/menu.lst
```

ahí se te abre el archivo que tiene la lista que muestra al iniciar la pc. Lo que no querés que te salga, simplemente le anteponés el # y listo.

Joya! Eso está muy bueno, te deja manejar la lista como en el manager que tiene el Win$$$s Muchas gracias!

[QUOTE=staar]mmm... el motor que te pide no aparece como instalado en la captura (un consejo, no uses la busqueda rapida de Synaptic, no es muy buena, mejor usa el boton buscar) el paquete se llama gtk2-engines-aurora, fijate
[/QUOTE]

Muchas gracias de nuevo, hice lo de los links al root y me quedo al pelo el skin en el gestor de paquetes. Pero así y todo, todavía no pude encontrar ese dichoso paquete "aurora" ni con el botón de búsqueda. Dejo un pantallazo de los engines que me aparecen a ver si me pueden dar una mano! jeje :D

---

### Post by staar on 2009-01-28
que raro, tenes activados todos los repositorios? en el Synaptic, configuracion, repositorios, origenes de terceros (o algo asi, no me acuerdo :P) activa los universe, multiverse, etc, despues actualizalos (recargar)

saludos

---

### Post by Air23 on 2009-01-28
> **staar said:**
> que raro, tenes activados todos los repositorios? en el Synaptic, configuracion, repositorios, origenes de terceros (o algo asi, no me acuerdo :P) activa los universe, multiverse, etc, despues actualizalos (recargar)

saludos

El engine aurora no esta en los repositorios de intrepid.

Hay que bajarlo de aca y compilarlo:

[http://gnome-look.org/content/download.php?content=56438&id=1&tan=8683849&PHPSESSID=e09ec167208658933219fc6315ad31f4](http://gnome-look.org/content/download.php?content=56438&id=1&tan=8683849&PHPSESSID=e09ec167208658933219fc6315ad31f4)

Las instrucciones estan en la mimsma pagina de gnome-look y mas info en:

[http://www.myscienceisbetter.info/2008/03/how-to-install-aurora-gtk-engine-14-ubuntu-hardy.html](http://www.myscienceisbetter.info/2008/03/how-to-install-aurora-gtk-engine-14-ubuntu-hardy.html)

---

### Post by staar on 2009-01-28
> **Air23 said:**
> El engine aurora no esta en los repositorios de intrepid.

Hay que bajarlo de aca y compilarlo:

[http://gnome-look.org/content/download.php?content=56438&id=1&tan=8683849&PHPSESSID=e09ec167208658933219fc6315ad31f4](http://gnome-look.org/content/download.php?content=56438&id=1&tan=8683849&PHPSESSID=e09ec167208658933219fc6315ad31f4)

Las instrucciones estan en la mimsma pagina de gnome-look y mas info en:

[http://www.myscienceisbetter.info/2008/03/how-to-install-aurora-gtk-engine-14-ubuntu-hardy.html](http://www.myscienceisbetter.info/2008/03/how-to-install-aurora-gtk-engine-14-ubuntu-hardy.html)

ah, mira vos, que loco :P, no tenia idea, pasa que yo uso linux mint, y viene instalado por defecto :D, todos los dias se aprende algo, gracias...

saludos

---

