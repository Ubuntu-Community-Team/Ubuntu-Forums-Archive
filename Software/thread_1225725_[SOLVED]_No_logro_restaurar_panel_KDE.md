---
title: "[SOLVED] No logro restaurar panel KDE"
date: 2009-07-28
forum: Software
---

### Post by Cajuma on 2009-07-28
Hola:
Elimine el panel por que no podía reacomodar los iconos de aplicaciones y al agregar un nuevo panel me lo coloca arriba, agrego otro abajo, elimino el superior, y no puedo agregar aplicaciones, boton secundario>añadir elementos graficos , pantallazo y nada.... lo había hecho en U-JJ y pude quitar y restaurar el superior y el inferior, pero en K-JJ no encuentro la forma, alguna sugerencia ?
Desde ya muchas gracias.

---

### Post by Hei Ku on 2009-07-28
Anda al cashew (la nuez en la esquina superior derecha) y pone Add Widgets. Busca en la lista y ahi tenes el panel.

---

### Post by Cajuma on 2009-07-28
Gracias por la respuesta, pero al hacerlo, salta el siguiente error:

No ha sido posible crear este objeto por el siguiente motivo:
No se puede encontrar el componente solicitado:
**Kgetpanelbar**

---

### Post by guillermolisi on 2009-07-28
Version de KDE 4 ?

---

### Post by Cajuma on 2009-07-28
Kde 4.2 Kernel 13.......

---

### Post by Hei Ku on 2009-07-28
Hmmm, me parece que tenes un problema más general. Yo probaría volviendo la configuración de plasma al default, y arrancar de vuelta desde ahí a ver qué pasa.

---

### Post by Cajuma on 2009-07-28
Ok volví a la configuración por default, añadí el lanzador de aplicaciones y cuando intento añadir otro componente, me duplica el lanzador de aplicaciones en el panel, ah y en añadir componentes figura dos veces el dichoso lanzador y el primero de la lista con un 2 (dos) al lado, me perdi....

---

### Post by Cajuma on 2009-07-29
Para embarrarla aun mas desactive compiz y en opciones de escritorio puse la opción de 1 
y adios lanzador de aplicaciones.....

---

### Post by SLA_leandrin on 2009-07-29
Proba renombrando el directorio 

```
 /home/usuario/.kde 
``` por algún otro nombre, como ```
/home/usuario/.kde-old
```
donde "usuario" es el nombre de tu usuario.

Deslogueate y logueate de nuevo a ver que pasa...

---

### Post by Cajuma on 2009-07-29
No hay caso, me voy a dormir, me tengo que levantar temprano. 
Mañana les cuento.
Gracias por su preocupación.............:(

---

### Post by Cajuma on 2009-07-29
Volví a la carga después de un a larga jornada laboral, arrastre las aplicaciones desde
añadir componentes, botón secundario y fui armando el panel, hasta que.........
Ha ocurrido un error fatal (al estilo ventanas)

 p, li { white-space: pre-wrap; }  Aplicación: Área de trabajo de Plasma (plasma), señal SIGSEGV
 [Current thread is 0 (LWP 3669)]
 
 Thread 3 (Thread 0xa482eb90 (LWP 3670)):
 #0  0xb7fd7430 in __kernel_vsyscall ()
 #1  0xb51180e5 in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/tls/i686/cmov/libpthread.so.0
 #2  0xb63272ed in pthread_cond_wait () from /lib/tls/i686/cmov/libc.so.6
 #3  0xb65139b2 in QWaitCondition::wait () from /usr/lib/libQtCore.so.4
 #4  0xa8840b9a in ?? () from /usr/lib/kde4/plasma_wallpaper_image.so
 #5  0xb651296e in ?? () from /usr/lib/libQtCore.so.4
 #6  0xb51144ff in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
 #7  0xb631849e in clone () from /lib/tls/i686/cmov/libc.so.6
 
 Thread 2 (Thread 0xa38eeb90 (LWP 4819)):
 #0  0xb7fd7430 in __kernel_vsyscall ()
 #1  0xb51180e5 in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/tls/i686/cmov/libpthread.so.0
 #2  0xb63272ed in pthread_cond_wait () from /lib/tls/i686/cmov/libc.so.6
 #3  0xb65139b2 in QWaitCondition::wait () from /usr/lib/libQtCore.so.4
 #4  0xb7994152 in ?? () from /usr/lib/libQtNetwork.so.4
 #5  0xb651296e in ?? () from /usr/lib/libQtCore.so.4
 #6  0xb51144ff in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
 #7  0xb631849e in clone () from /lib/tls/i686/cmov/libc.so.6
 
 Thread 1 (Thread 0xb3cfe730 (LWP 3669)):
 [KCrash Handler]
 #6  0x00000003 in ?? ()
 #7  0xb7e08233 in Plasma::Applet::focusInEvent () from /usr/lib/libplasma.so.3
 #8  0xb6ee9cc2 in QGraphicsItem::sceneEvent () from /usr/lib/libQtGui.so.4
 #9  0xb6f36f9f in QGraphicsWidget::sceneEvent () from /usr/lib/libQtGui.so.4
 #10 0xb6f0e1cc in ?? () from /usr/lib/libQtGui.so.4
 #11 0xb6f0ec50 in QGraphicsScene::setFocusItem () from /usr/lib/libQtGui.so.4
 #12 0xb6f18a14 in ?? () from /usr/lib/libQtGui.so.4
 #13 0xb6f1756a in QGraphicsScene::event () from /usr/lib/libQtGui.so.4
 #14 0xb68b3e9c in QApplicationPrivate::notify_helper () from /usr/lib/libQtGui.so.4
 #15 0xb68bc19e in QApplication::notify () from /usr/lib/libQtGui.so.4
 #16 0xb770b94d in KApplication::notify () from /usr/lib/libkdeui.so.5
 #17 0xb6606a3b in QCoreApplication::notifyInternal () from /usr/lib/libQtCore.so.4
 #18 0xb6f2693b in QGraphicsView::mousePressEvent () from /usr/lib/libQtGui.so.4
 #19 0xb690ac46 in QWidget::event () from /usr/lib/libQtGui.so.4
 #20 0xb6ce4993 in QFrame::event () from /usr/lib/libQtGui.so.4
 #21 0xb6d8494f in QAbstractScrollArea::viewportEvent () from /usr/lib/libQtGui.so.4
 #22 0xb6f28102 in QGraphicsView::viewportEvent () from /usr/lib/libQtGui.so.4
 #23 0xb6d86f55 in ?? () from /usr/lib/libQtGui.so.4
 #24 0xb6605c5a in QCoreApplicationPrivate::sendThroughObjectEventFilters () from /usr/lib/libQtCore.so.4
 #25 0xb68b3e7a in QApplicationPrivate::notify_helper () from /usr/lib/libQtGui.so.4
 #26 0xb68bcb11 in QApplication::notify () from /usr/lib/libQtGui.so.4
 #27 0xb770b94d in KApplication::notify () from /usr/lib/libkdeui.so.5
 #28 0xb6606a3b in QCoreApplication::notifyInternal () from /usr/lib/libQtCore.so.4
 #29 0xb68bbb7e in QApplicationPrivate::sendMouseEvent () from /usr/lib/libQtGui.so.4
 #30 0xb692b97e in ?? () from /usr/lib/libQtGui.so.4
 #31 0xb692aca7 in QApplication::x11ProcessEvent () from /usr/lib/libQtGui.so.4
 #32 0xb6955c6a in ?? () from /usr/lib/libQtGui.so.4
 #33 0xb4f12b88 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
 #34 0xb4f160eb in ?? () from /usr/lib/libglib-2.0.so.0
 #35 0xb4f16268 in g_main_context_iteration () from /usr/lib/libglib-2.0.so.0
 #36 0xb6632438 in QEventDispatcherGlib::processEvents () from /usr/lib/libQtCore.so.4
 #37 0xb6955365 in ?? () from /usr/lib/libQtGui.so.4
 #38 0xb660506a in QEventLoop::processEvents () from /usr/lib/libQtCore.so.4
 #39 0xb66054aa in QEventLoop::exec () from /usr/lib/libQtCore.so.4
 #40 0xb6607959 in QCoreApplication::exec () from /usr/lib/libQtCore.so.4
 #41 0xb68b3d17 in QApplication::exec () from /usr/lib/libQtGui.so.4
 #42 0xb7f81b56 in kdemain () from /usr/lib/libkdeinit4_plasma.so
 #43 0x08048712 in _start ()


 
Alguna idea de que estamos hablando ?, gracias !!!!! [IMG]http://ubuntuforums.org/images/icons/icon8.gif[/IMG]

---

### Post by SLA_leandrin on 2009-07-30
Que garrón, ni idea...

Solución alternativa, reinstlar KDE o mejor, actualizar a KDE4.3 RC2??

No es lo mejor pero bue

---

### Post by Cajuma on 2009-07-30
Creo que voy a reinstalar el So (K-JJ) de nuevo; el live cd que esta para bajar actualmente, es el mismo que el de Abril del 2009 ? o se le aplicaron las actualizaciones y el nuevo Kernel; viene con el Grub2 o el anterior ?. pregunto
esto porque tengo tres SO en la pc y no me quiero complicar mas.
Gracias.

---

### Post by SLA_leandrin on 2009-07-31
Yo te recomendaría que actualices a KDE 4.3 RC2 sin reinstalar el sistema.

Yo lo tengo así, tiene varias mejoras y cuando salga el KDE4.3 definitivo lo actualizas de nuevo y listo.

Para actualizarlo hay varias guías, por ejemplo,

[http://miranda23.wordpress.com/2009/07/10/kde-4-3-rc2/]("http://miranda23.wordpress.com/2009/07/10/kde-4-3-rc2/")

[URL="http://tuxarena.blogspot.com/2009/07/how-to-install-kde-43-rc1-in-kubuntu.html"]http://tuxarena.blogspot.com/2009/07/how-to-install-kde-43-rc1-in-kubuntu.html
[/URL]



El segundo link está en inglés, mejor explicado, es para el RC1, pero es lo mismo porque te va a actualizar a la úlitma versión disponible.

Metele con confianza, cualquier cosa preguntá...

Saludos.

---

### Post by guillermolisi on 2009-07-31
Reinstalar KDE es un paso intermedio previo a reinstalar todo, asi que nada vas a perder si sale mal.

---

### Post by Cajuma on 2009-07-31
Gracias Leandrin y Guille ( te puedo llamar asi ?), les voy a hacer caso y el fin de semana pruebo (trabajo de Lunes a Sabado hasta las 21.00hs.)
Actualizo KDE y les cuento.
Saludos.

---

### Post by jpoeta on 2009-07-31
Hola a mi me paso algo similar en Gnome y encontre solucion talves si en vez de gnome escribes kde se soluciona suerte y lee mi caso

[http://ubuntuforums.org/showthread.php?t=1206467&highlight=jpoeta](http://ubuntuforums.org/showthread.php?t=1206467&highlight=jpoeta)

Saludos:P

---

### Post by guillermolisi on 2009-07-31
> **Cajuma said:**
> Gracias Leandrin y Guille ( te puedo llamar asi ?), les voy a hacer caso y el fin de semana pruebo (trabajo de Lunes a Sabado hasta las 21.00hs.)
Actualizo KDE y les cuento.
Saludos.
Of course, my friend :D

Adelante y suerte (como dicen en el Golf).

---

### Post by Cajuma on 2009-07-31
Nuevamente gracias por la data, a Leandrin, Guille y Poeta (¿ te gusta Garcia Marquez ?)
si puedo hoy a la noche  pongo a prueba las posibles soluciones, sino el Domingo le robo
un ratito a mis cuatro hijos, y lo veo.
Voy a probar reestablecer la configuración original y despues actualizar, a ver que sale.
Saludos.....:D

---

### Post by SLA_leandrin on 2009-07-31
Buenísimo, ojalá que te salga todo bien y fácil... cualquier cosa, pegá el grito te ayudaré con lo poco que pueda!! y los demás también claro.

Y de nada por supuesto, para eso estamos aquí!

Saludos.

---

### Post by Cajuma on 2009-08-01
Hola muchachos, malas noticias......
Primero hice esto
[http://ubuntuforums.org/showthread.php?t=1206467&highlight=jpoeta](http://ubuntuforums.org/showthread.php?t=1206467&highlight=jpoeta)
Puse Kde en lugar de gnome y nada....
Despues hice esto otro....
[http://tuxarena.blogspot.com/2009/07/how-to-install-kde-43-rc1-in-kubuntu.html](http://tuxarena.blogspot.com/2009/07/how-to-install-kde-43-rc1-in-kubuntu.html)
Actualice al kernel 14 y Kde 4.3 y el panel de m...... sigue igual que antes, solo que
ahora tengo nuevos themes y un montón de juegos......
Cuando minimizo varias aplicaciones se superponen con los iconos del panel, compiz
no funka y si agrego escritorios se ponen en linea y se superponen con los iconos del
panel, se me quemaron los papeles !!, hace recién tres meses que tome contacto con
Linux y no tengo los conocimientos necesarios para solucionar semejante lío, cosa que
me saca de las casillas, ya que no me gusta andar jorobando tanto y no poder aportar
nada, creo que lo mas acertado es reinstalar Kubuntu, o seguir con U-JJ hasta que tenga
mas herramientas para poder solucionar este tipo de problemas.
No se que opinan ustedes, yo estoy bastante decepcionado al no poder solucionar este
problema.
Un abrazo y nuevamente mil gracias por la paciencia.

---

### Post by staar on 2009-08-01
a ver, primero cerrá plasma con Alt+F2 *kquitapp plasma*, después abrí dolphin, Alt + F2 *dolphin*, y andá a /home/*tuusuario*/.kde4/share/config/ y mové (o cambiá de nombre) lo que empieze con plasma (por ejemplo, yo tengo plasma-desktop-applets-rc, plasma-desktoprc y plasmarc, pero es KDEmod 4.3 rc3 así que supongo vos tendrás otras), después reiniciá plasma, Alt + F2 *plasma*, el escritorio va a haber vuelto a los valores por defecto...

si no funca, podés reiniciar la configuración de todo KDE moviendo o cambiando el nombre de la carpeta .kde4 en tu home y ver que pasa...

saludos

---

### Post by Cajuma on 2009-08-01
Gracias Staar, pero lo que hice despues de tragarme la bronca y pensar un poco (no mucho a esta hora) fue desinstalar Compiz y Emerald y volver a instalarlos.
Creo que eso fue todo, aparentemente esta funcionando ok,  (hasta ahora).
A gallego me iba a ganar.
Graciassss Boys un abrazo y apt-get install Cabernet Sauvignon !!!!!!

---

### Post by Hei Ku on 2009-08-01
Por que tenes Compiz y Emerald andando en KDE? 
se superponen con KWin, y Compiz siempre tuvo problemas con KDE.

---

### Post by guillermolisi on 2009-08-01
Si, es cierto, siempre fue conflictivo ya desde la version 3. Ademas, los efectos que incluye kwin en la 4 no tienen nada que envidiarle a Compiz con lo cual te ahorras un paquete en la instalacion y consumiendo memoria, procesador y tu tiempo y paciencia.

---

### Post by Cajuma on 2009-08-01
Hei Ku, Guille, la respuesta es sencilla, _por que no lo sabia,_ cuando instale 
k-jj y U-jj en mi pc hace menos de tres meses fue mi primer contacto con 
Linux y lo que hice fue seguir los pasos de instalación que recomendaban
en algun blog; ahora lo se, y no voy a cometer el mismo error dos veces.
Pido disculpas a los foreros por hacerle perder el tiempo en algo tan obvio.
Saludos.

---

### Post by guillermolisi on 2009-08-01
> **Cajuma said:**
> Hei Ku, Guille, la respuesta es sencilla, _por que no lo sabia,_ cuando instale 
k-jj y U-jj en mi pc hace menos de tres meses fue mi primer contacto con 
Linux y lo que hice fue seguir los pasos de instalación que recomendaban
en algun blog; ahora lo se, y no voy a cometer el mismo error dos veces.
Pido disculpas a los foreros por hacerle perder el tiempo en algo tan obvio.
Saludos.
Relax, my friend, relax and take it easy.

Solo fueron comentarios informativos, complementarios, nothing else.

---

### Post by Cajuma on 2009-08-01
Todo bien Guille, se que deben estar cansados 
de contestar mil veces lo mismo....
Gracias, Tema cerrado.

---

### Post by Hei Ku on 2009-08-01
En serio que no te quisimos retar. Fue sorpresa solamente. Y si realmente fue ese el problema, mejor. Todo tranqui.

---

