---
title: "[PROBLEMAS VARIOS] Wine, Reproductores de Audio  Firefox"
date: 2008-12-20
forum: Software
---

### Post by &lt;Mary&gt; on 2008-12-20
Hola a todos/as!! Soy Mary, muy nueva en Ubuntu. Hace un mes que lo estoy usando, ya antes había probado con Kubuntu y terminé desinstalándolo porque me formateo no solo la partición que le había asignado sino un hd completo y jamás pude hacer que me reconozca la red con la conexión a internet.
Después de un año estoy con Hardy Heron y no pienso pasarme a Intrepid, mi máquina no da para tanto y con este estoy mas que bien... hasta ahora.
Conseguir la dichosa conexión a internet con mi modem amigo la logré gracias a que me leí casi todos los tutoriales que andan dando vueltas por ahí.
El problema que me trae hoy a consulta es: instale wine, necesito tener photoshop aquí, seguí paso por paso todos los tutoriales de este foro y los de la página de wine y no me gustaron los resultados, quiero probar con wirtualbox, ya desinstalé wine, borré la carpeta .wine de home/user (en este caso user = mary) antes de esto desintalé los programas, al photoshop jamás lo pude desinstalar, ni todos los programas complementarios como bridge, extendedscript toolkit, imageready, etc. Esta es la segunda vez que me pasa, ahora tengo que sumar que estuve probando con otros programas como winrar y yahoo messenger y oh! caramba! tampoco se van. Se me sumaron a la lista de programas fantasmas. No esta wine, no estan los programas, borré la carpeta de wine, pero cada vez que voy a aplicaciones la carpeta de wine (ya sin las opciones drive c: o uninstall software) sigue ahí con el photoshop, sus complementos, el winrar y yahoo msn. Mi pregunta ¿cómo los puedo eliminar? Me jode que este ahí.
Problema 2: escucho radio del plata y la rock & pop. Si escucho la radio, gralmente uso Rhythmbox para esto, y quiero ver un video de youtube, el video no suena, a este problema ya me acostumbre, pero ahora se le sumó uno nuevo, ayer se actualizaron algunos programas, y oh! caramba! hoy cada vez que se conecta rhythmbox con alguna radio (cualquier radio) suena por un rato y después se queda mudo, como si se cortara el buffer. Me pasa con rhythmbox, con totem y con mplayer. Es muy, muy, muy molesto tener que abrir la url de la radio a cada rato.
Problema 3: flash + firefox + ubuntu, es todo un dolor de cabeza, que hasta ahora lo puedo solucionar, pero hay detalles que me crispan los pelos, cada vez que quiero reproducir mi playlist de youtube a pantalla completa, a los 10 min (esta es la configuración que le dí al monitor para que se apague solo) se pone negra la pantalla, el sistema inactivo y tengo que volver a poner a pantalla completa otra vez mi playlist, esto en winxp no me lo hacía flash, si bien el sistema pasaba a inactivo despues de 10 min, no lo hacía cuando algún video en flash  estaba a pantalla completa, esto ¿tiene alguna solución?
Problema 4: mas que un problema es un trabajo que me quiero evitar, crear la interfaz nas0 todas las veces que quiero conectarme a internet es molesto. Se que hay un script que puede funcionar, ya probé varios de este foro y varios blogs y ninguno me funcionó. Si alguien tiene uno que funcione, Mary agradecida.:)
Desde ya muchas gracias!!

---

### Post by KrossX on 2008-12-21
[COLOR="Navy"]Bienvenida!

Problema1: Deberías haber desinstalado los programas antes de quitar Wine. XD
Para quitar las entradas en el menú, haz click derecho sobre "Aplicaciones?" y luego en "Editar Menus". Eso debería ser suficiente. (lo uso en inglés, los nombres podrían variar)

Problema2: Probá usando PulseAudio como dispositivo de audio por defecto.... o si está en uso, lo contrario, prueba terminando el proceso pulseaudio (ALSA entra en acción).

Problema3: Últimamente, los screensaver me han traído problemas... mejor desactívalos y apaga el monitor cuando no vayas a usarlo por un buen rato.

Problema4: Si lo puedes hacer en una sóla línea, puedes agregarla al inicio de sesión.
Sistema => Preferencia => Sesiones (nombres pueden variar).[/COLOR]

---

### Post by faktorqm on 2008-12-22
Hola y bienvenida al foro!

Para el problema 2 lo mejor que podrias probar (luego de la recomendacion de usar pulseaudio) es escuchar con VLC. Yo tambien escucho radio del plata e incluso guardo algunos programas en ogg.

Salu2!

---

### Post by &lt;Mary&gt; on 2008-12-22
Muchas Gracias Chicos!!!!:):)

Problema 1: Solucionado. Si, debería haber desinstalado el photoshop desde wine, y lo intenté, el problema es que no se quiso ir. Por lo que leí googleando por ahí es porque photoshop usa un programa que es installshield program, una herramienta que utiliza photoshop para instalarse en so windows.:mad:
Problema 2: Solucionado. Ya puse todo en PulseAudio Sound Server, eventos de sonido, música y películas, reproducción de sonido, captura de sonido, me queda la duda en pista determinada del mezclador, lo deje en **Playback: ALSA PCM on front :0 (SiS Sl7012) via DMA(PulseAudio Mixer)**
Pero de PulseAudio me salen 2 opciones mas **Capture: Monitor Source of ALSA** y **Capture: ALSA PCM on front**, no se ni lo que estoy haciendo aquí, asi que lo dejé en playback.
De todas formas, parece que es un problema común de Hardy, los reproductores de música con el plugin de flash player de Firefox, aclaro que yo tengo la versión 10 que la descargué de Adobe, el paquete nonfree de Synaptic nunca anduvo como la gente, tenía imagen pero no sonido, no me quedo otra que instalar el paquete .deb de Adobe. 
Esta discusión sobre flash player + problemas de audio está por aquí>> [http://ubuntuforums.org/showthread.php?t=965888](http://ubuntuforums.org/showthread.php?t=965888)
Problema 3: Solucionado. :)
Problema 4: sigo buscando el script.
Muchas Muchas Gracias por contestarme!!!
FELICES FIESTAS PARA TODOS!!:biggrin:

---

### Post by Hei Ku on 2008-12-22
Por qué no abrís una thread aparte para ese problema de red? Parece algo bastante específico y con un thread mas acotado podés lograr la atención de la gente correcta.

---

### Post by &lt;Mary&gt; on 2008-12-22
Porque ya debe estar este tema tratado en el foro, lo tengo que buscar mejor. 
No voy a abrir un thread para tratar algo que ya debe estar resuelto, cuando lo encuentre edito este.
Gracias igual.;)

---

### Post by c4d0rn4 on 2008-12-22
> **<Mary> said:**
> Problema 4: sigo buscando el script.

actualmente lo haces de manera manual, porque no ponés todos los comandos que usas y nos fijamos.

ojo, fijate si usas algo tipo usuario y contraseña dentro de los comandos de no publicar las tuyas en el foro.

---

