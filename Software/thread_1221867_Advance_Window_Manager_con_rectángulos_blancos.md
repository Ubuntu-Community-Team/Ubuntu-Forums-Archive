---
title: "Advance Window Manager con rectángulos blancos"
date: 2009-07-24
forum: Software
---

### Post by aledruetta on 2009-07-24
Hola Comunidad!

Tengo mi Ubuntu Jaunty con un bonito escritorio (para mí gusto) con el theme Bamboo Zen del proyecto Bisigi, el dock Advance Window Manager, y un detallecito...

Cuando el AWM se actualiza, por ejemplo, porque se habre una nueva aplicación o ventana, el espacio que va a ocupar el ícono y el cuadro de diálogo en la barra, antes de que estos aparezcan, se ve ocupado, por breves instantes, con un "bastante antiestético" rectángulo blanco parpadeante. No puedo dejar una captura porque es cosa de fracción de segundos, pero lo suficiente para estropear el trabajo de personalización realizado.

Probé con el docky de gnome-do y eso no acontece, pero me gusta más AWM.

Cualquier sugerencia será eternamente agradecida,
Saludos,
Alejandro.

---

### Post by Patriciologico on 2009-07-24
Hola Aledruetta

¿Estas concompiz activado? ¿que version de AWN usas? ¿Te pasa con todos los efectos de AWN?

Agrego preguntas, por que con los datos que datos, no alcanzo a hacerme una idea de que puede ser.

Saludos!

---

### Post by aledruetta on 2009-07-24
> **Patriciologico said:**
> Hola Aledruetta

¿Estas concompiz activado? ¿que version de AWN usas? ¿Te pasa con todos los efectos de AWN?

Agrego preguntas, por que con los datos que datos, no alcanzo a hacerme una idea de que puede ser.

Saludos!

Sí, compiz está activado. Y si no entendí mal en lo que leí, ese es un requisito para que funcione AWM.

La versión que estoy usando (ayer y hoy) es la 0.3.3, pero hasta hace dos días atrás usaba la versión que está en los repositorios de Jaunty, que es la 0.3.2 o 0.3.1, no recuerdo; y el problema era el mismo. Justamente me actualizé a esta versión para ver si se resolvía.

Quizá es un problema de Compiz y no AWM, porque, por ejemplo, hace un rato descargué un par de PDF en el escritorio, se me acabó la batería y no me dí cuenta, entonces la máquina se apagó. Cuando encendí nuevamente, observé que lo mismo que hacía con AWM, lo hizo con las imágenes en miniatura de los documentos en el escritorio.

Pero no lo hace siempre. A veces sí y a veces no. Ahora, que estoy haciendo pruebas para ver si puedo dar más información, no lo está haciendo. Pero estoy seguro que si reinicio las X, cuando vuelve a entrar en la seción y se abre AWM, aparecen los rectángulos blancos antes de aparecer los íconos.

Disculpen, pero no sé cómo explicarlo mejor.

---

### Post by nopersona on 2009-07-24
Recomiendo [cairo-dock]("http://www.cairo-dock.org/"), la version 2.0.8 es insuperable! dale un ojito al tema mac, los efectos son increíbles. Además, el soporte glx es excelente :P 

Lo siento, pero no se mucho dede AWN, lo probé una vez, pero no me gustó, los efectos eran muuyyy leeeentos :popcorn:

---

### Post by aledruetta on 2009-07-24
> **nopersona said:**
> Recomiendo [cairo-dock]("http://www.cairo-dock.org/"), la version 2.0.8 es insuperable! dale un ojito al tema mac, los efectos son increíbles. Además, el soporte glx es excelente :P 

Lo siento, pero no se mucho dede AWN, lo probé una vez, pero no me gustó, los efectos eran muuyyy leeeentos :popcorn:

Ahí probé cairo-dock. Realmente muy buena aplicación, los efectos, los íconos, todo. Pero en modo OpenGL me funciona peor que AWM, en el sentido que directamente aparece sobre un fondo negro. En el modo no-OpenGL no me trae ese problema.

Por eso, y por lo que comentaba antes, sospecho que el problema puede estar en Compiz o algo relacionado con OpenGL o la placa de video. Si las dos tienen problemas, debe haber algo en mi sistema que está funcionando mal.

¿Se les ocurre algo?

---

### Post by nopersona on 2009-07-24
En el caso de que tu aceleración ed funcione correctamente, seguro que tu usuario tiene los permisos necesarios? Sistema>administración>usuarios, revisa los permisos del tuyo

P.S.: Qué tarjeta es?

---

### Post by aledruetta on 2009-07-24
> **nopersona said:**
> seguro que tu usuario tiene los permisos necesarios? Sistema>administración>usuarios, revisa los permisos del tuyo

¿Cuáles serían esos permisos necesarios? El que dice "capturar video de webcam y tv, y usar aceleración 3D" está desmarcado ¿Es ese?

> **nopersona said:**
> P.S.: Qué tarjeta es?

Es la "Intel Corporation Mobile 945GM/GMS, 943/940 GML Express Integrated Graphic Controler (rev 03)", según Sysinfo.

---

### Post by nopersona on 2009-07-24
> **aledruetta said:**
> ¿Cuáles serían esos permisos necesarios? El que dice "capturar video de webcam y tv, y usar aceleración 3D" está desmarcado ¿Es ese?

Justamente, marcalos, cierra sesión y pruebas.

---

### Post by aledruetta on 2009-07-24
Bien, por las dudas, marqué todos los permisos, reinicié la sesión, pero sigue comportándose de la misma manera.

¿Alguna otra idea?

---

### Post by aledruetta on 2009-07-25
Por las dudas, pego la información que me da FUCH sobre video. Ahí marca varios errores, incluso relacionados con AWN, pero no sé interpretarlos:

```
ESCRITORIO:    GNOME
[code]
$lspci|grep -i vga
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)

```
```

$cat /var/log/Xorg.0.log|grep EE
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER
(EE) intel(0): Failed to set tiling on front buffer: rejected by kernel
(EE) intel(0): Failed to set tiling on back buffer: rejected by kernel
(EE) intel(0): Failed to set tiling on depth buffer: rejected by kernel

```
```

$cat /var/log/messages |grep error
Jul 24 10:11:20 alejandro-laptop kernel: [ 8629.180241] awn-applet-acti[6629]: segfault at 0 ip b79ac078 sp bfbbbe3c error 4 in libc-2.9.so[b7935000+15c000]
Jul 24 12:29:28 alejandro-laptop kernel: [16917.386729] indicator-apple[6490]: segfault at 10 ip b6a96226 sp bf930500 error 4 in libmessaging.so[b6a92000+6000]

```
```

$cat /var/log/syslog |grep error
Jul 24 10:11:20 alejandro-laptop kernel: [ 8629.180241] awn-applet-acti[6629]: segfault at 0 ip b79ac078 sp bfbbbe3c error 4 in libc-2.9.so[b7935000+15c000]
Jul 24 12:29:28 alejandro-laptop kernel: [16917.386729] indicator-apple[6490]: segfault at 10 ip b6a96226 sp bf930500 error 4 in libmessaging.so[b6a92000+6000]
Jul 24 14:21:37 alejandro-laptop NetworkManager: <WARN>  check_one_route(): (wlan0) error -34 returned from rtnl_route_del(): Sucess  
Jul 24 14:23:00 alejandro-laptop x-session-manager[3538]: WARNING: Could not launch application 'gnome-do.desktop': Unable to start application: Ha ocurrido un error al ejecutar el proceso hijo «gnome-do» (No existe el fichero ó directorio) 
Jul 24 18:17:54 alejandro-laptop gdm[3102]: WARNING: gdm_slave_xioerror_handler: ha ocurrido un error fatal de X - Reiniciando :0 
Jul 24 18:17:56 alejandro-laptop NetworkManager: <WARN>  check_one_route(): (wlan0) error -34 returned from rtnl_route_del(): Sucess  
Jul 24 18:18:25 alejandro-laptop x-session-manager[9939]: WARNING: Could not launch application 'gnome-do.desktop': Unable to start application: Ha ocurrido un error al ejecutar el proceso hijo «gnome-do» (No existe el fichero ó directorio) 
Jul 24 20:03:10 alejandro-laptop NetworkManager: <WARN>  check_one_route(): (wlan0) error -34 returned from rtnl_route_del(): Sucess  
Jul 24 20:03:26 alejandro-laptop x-session-manager[18161]: WARNING: Could not launch application 'gnome-do.desktop': Unable to start application: Ha ocurrido un error al ejecutar el proceso hijo «gnome-do» (No existe el fichero ó directorio) 
Jul 24 20:10:51 alejandro-laptop NetworkManager: <WARN>  check_one_route(): (wlan0) error -34 returned from rtnl_route_del(): Sucess  
Jul 24 20:11:08 alejandro-laptop x-session-manager[18994]: WARNING: Could not launch application 'gnome-do.desktop': Unable to start application: Ha ocurrido un error al ejecutar el proceso hijo «gnome-do» (No existe el fichero ó directorio) 
Jul 25 00:57:10 alejandro-laptop NetworkManager: <WARN>  check_one_route(): (wlan0) error -34 returned from rtnl_route_del(): Sucess  
Jul 25 07:42:11 alejandro-laptop x-session-manager[3504]: WARNING: Could not launch application 'gnome-do.desktop': Unable to start application: Ha ocurrido un error al ejecutar el proceso hijo «gnome-do» (No existe el fichero ó directorio) 

```
```

$lsmod |grep drm
drm                    96296  3 i915
agpgart                42696  3 drm,intel_agp

```
```

$lsmod |grep agp
intel_agp              34108  1 
agpgart                42696  3 drm,intel_agp

```
```

$glxinfo |grep direct
direct rendering: Yes

```
```

$

```
[/code]

---

### Post by bunglestone on 2009-07-26
aledruetta, a mi también me sucedieron errores con mi cairo-dock y con conky cuando estos iniciaban antes de compiz, para solucionarlo hice un script que retarda el inicio de mi cairo-dick, para dejarle tiempo a compiz para iniciar, quizás te pueda ser de ayuda, te dejo el codigo que tendrias que insertar en tu propio launch_awn.sh.

```

#!/bin/bash
sleep 40
awn &
exit 0

```Los Guardas y le das permisos de ejecucion

```

chmod +x launch_awn.sh

```Y finalmente reemplazas en tus "Aplicaciones de inicio" el antiguo llamado a awn por tu nuevo launch_awn.sh.

Saludos, espero que te sirva.

---

### Post by aledruetta on 2009-07-26
Muchas gracias, bunglestone, por tu aporte, pero no resultó, la barra sigue comportándose de la misma forma. Por otro lado, el problema no es sólo al inicio.

Gracias igual, y sigo buscando alguna solución.

---

### Post by AlexDDR on 2009-08-01
de hecho a mi tambien me socede algo parecido pero solo al inicio de AWN , en el que antes de que se carguen los plugins aparecen dos lineas largar paralelas en varias partes mientras la barra va creciendo.

Me parece que awn no es 100% perfecto, pero funciona, en la version de actualizada tambien despues de un rato me vuelve lento compiz hasat que lo cierro.

Talvez podrias ver en los settings de compiz aplicar algunos de los hack que se pueden aplicar (workarounds) y ver si te sirve alguno, osea jugar con la configuracion de compiz o tambien con la del driver en el XORG.conf porque hace un tiempo habia varias opciones "option" que solucionaban pequeños problemas cuando compiz estaba en un estado mas incipiente.


bueno espero mi comentarios puedan ayudar aunque sea un poco


saludos

---

### Post by aledruetta on 2009-08-02
> **AlexDDR said:**
> Talvez podrias ver en los settings de compiz aplicar algunos de los hack que se pueden aplicar (workarounds) y ver si te sirve alguno, osea jugar con la configuracion de compiz o tambien con la del driver en el XORG.conf porque hace un tiempo habia varias opciones "option" que solucionaban pequeños problemas cuando compiz estaba en un estado mas incipiente.
Gracias AlexDDR,

Voy a probar con lo que me decís. Me pierdo bastante con las configuraciones de compiz, es que son muchas y la mayoría no entiendo para qué sirven. Pero voy a jugar un poco a ver qué pasa.

Lo de las líneas paralelas a mí también me pasa.

Te pregunto ¿no notaste que ocurre algo parecido con, por dar un ejemplo, el ícono en el escritorio de una unidad montada al inicio? Te pregunto eso, porque es lo que me hace sospechar que más que un problema de AWN podría ser un problema de Compiz mismo. No sé, ¿qué opinás?

---

### Post by AlexDDR on 2009-08-02
Lo que me pasa es que cuando cambio de usuario con el cambiador de usuario rapido del panel , al volver (cerrar sesion) con el 2do usuario queda un cruadrado blanco en el icono de las aplicaciones abiertas, hasta que alguna aplicacion se abre o se cierra y se actualiza AWN  y vuelve a animar la barra completa

Tengo la impresion de que es una falla de AWN, mas que de compiz, pero mi video es nvidia y al cambiar de usuario tiene problemas con compiz activado pero es un comportamiento similar

talvez todos son culpables de algun modo (algun porcentaje)

saludos

---

