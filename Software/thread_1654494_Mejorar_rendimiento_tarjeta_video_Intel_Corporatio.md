---
title: "Mejorar rendimiento tarjeta video Intel Corporation 82845G/GL["
date: 2010-12-28
forum: Software
---

### Post by Maciett on 2010-12-28
Hola,

Quisiera saber como puedo mejorar el rendimiento de la tarjeta de video.

En este post [1] leí algo de eso, y aplicando los mismos pasos:

En Sistema----->Administración ------>Controladores de hardware sale una barra que dice buscando controladores disponibles y luego manda una ventana de "No se están usando controladores privativos en este sistema".

La tarjeta de video es:
```
$lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
$glxinfo | grep render
direct rendering: Yes
OpenGL renderer string: Software Rasterizer
    GL_NV_conditional_render, GL_NV_depth_clamp, GL_NV_fragment_program, 

```Cuando pruebo los engranes:
```
$glxgears
371 frames in 5.0 seconds = 74.034 FPS
380 frames in 5.0 seconds = 75.980 FPS
389 frames in 5.0 seconds = 77.779 FPS
388 frames in 5.0 seconds = 77.453 FPS
388 frames in 5.0 seconds = 77.509 FPS
357 frames in 5.0 seconds = 71.117 FPS
45 frames in 5.1 seconds =  8.778 FPS
46 frames in 5.1 seconds =  9.088 FPS
52 frames in 5.1 seconds = 10.207 FPS
52 frames in 5.1 seconds = 10.232 FPS
48 frames in 5.0 seconds =  9.518 FPS

```Donde los primeros son el pantalla chica y los últimos son en pantalla maximizada.

En Sistema---->Preferencias----->Apariencias------>Efectos Visuales
está en ninguno y si lo trato de cambiar a cualquiera de las otras dos opciones la pantalla parpadea y da el mensaje "buscando controladores disponibles", luego da otro mensaje de "No se han podido activar los efetos de escritorio" y vuelve a ninguno.

Espero sus respuestas.

Saludos

[1]http://ubuntuforums.org/showthread.php?t=1646170&highlight=aceleraci%F3n+gr%E1fica

---

### Post by moreback on 2010-12-28
Tarjeta en blacklist de compiz? prueba corriendo compiz de esta forma:

SKIP_CHECKS=yes compiz --replace

Hay otro post por aquí donde se discute lo mismo.

PD: [http://wiki.compiz.org/Hardware/Blacklist](http://wiki.compiz.org/Hardware/Blacklist)

---

### Post by Maciett on 2010-12-28
[SIZE=2]Si, el otro tema en que se toca esto es el que indique en el post anterior como [1], pero no entiendo como sacando la tarjeta de blacklist soluciona el problema (siendo que ya revisé el archivo [/SIZE][SIZE=2]blacklist.conf y no encontré ninguna parecida).

¿No existe algún instalable que mejore el rendimiento, como un driver para esa tarjeta o algo parecido?

También agrego que cuando veo un video en youtube el uso de cpu es 100%, y me parece mucho.

Espero puedan ayudarme.

Saludos
[/SIZE]

---

### Post by moreback on 2010-12-30
No sé que archivo blacklist.conf habrás revisado (¿ /etc/modprobe.d/blacklist.conf ?) pero creo que no tiene nada que ver con Compiz. Me parece que el blacklist del compiz estaba en otro archivo, pero no recuerdo cual.

Ahora creo que lo mejor que puedes hacer es crear ese archivo en tu $HOME que recomiendan al final del link [http://wiki.compiz.org/Hardware/Blacklist](http://wiki.compiz.org/Hardware/Blacklist)

Saludos.

PD: lo del 100% de la CPU al usar flash puede ser a que no estás usando aceleración de tu tarjeta y eso es porque compiz se niega a partir.

---

### Post by RafaelG on 2010-12-30
Maciett,

Lo que trata de indicar Moreback es que si tu tajerta de video estuviera en Blacklist de compiz puedes hacer lo indicado por moreback para ignorar la Blacklist y asi poder hacer correr los efectos de compiz, pero aun asi tendras inestabilidad con los efectos compiz.

Ahora mi consulta es si ya tienes activados los efectos compiz y lo que deseas es mejorar las graficas como por ejemplo adobe flash entonces ahi podrias revisar si tienes habilitado la aceleracion del hadware para eso hacer click derecho en el video de adobe flash presionar setting y seguidamente aparecera un cuadro  de dialogo donde deberia mostrar como primera opcion "Enable hadware acceleration".

Saludos,

---

### Post by Maciett on 2010-12-31
La verdad no me que da muy claro que es "compiz", sólo quiero poder correr un programa que en windows usaba la aceleración gráfica del sistema.

Si es algo que es bonito útil y no me comerá toda la cpu como el flash bienvenido.

Y eso de la inestabilidad, no me tinca, por eso no me atrevo a seguir el consejo de moreback de sacarlo de la lista negra.

RafaelG, ya revisé haciendo click derecho sobre un flash y está activada la opción de aceleración por hardware.

Espero sus respuestas.

Saludos

Feliz fin de año!

---

### Post by moreback on 2011-01-01
Yo que tu no tendría miedo a usar compiz sacando tu tarjeta, pruébalo por un tiempo y sólo si te da problemas la desactivas.

Cuando no se quiere usar compiz pero si se requiere un *gestor de composición (compositing manager*,  creo que de ahi viene el nombre de compiz) para tener algunos efectos,  se puede activar una opción en Metacity para que actúe como tal: abre el  Editor de Configuración (**gconf-editor**) y luego activa la clave **/apps/metacity/general/compositing_manager**.

Saludos.

---

### Post by Maciett on 2011-01-05
Bueno, como no me quiero arriesgar con eso de la lista negra, active eso que dijiste de la clave y la pantalla pestaño, quedó sólo el fondo de pantalla y cargó denuevo las barras y todo lo que estaba abierto, pero por ejemplo, si me voy a monitores, sigue siendo un desconocido para el equipo y me da una resolución de 1280x1024(5:4), que no puedo cambiar. Creo que si pudiera tener más opciones de resolución podría hacer lo que estoy tratando.
¿Cómo le digo para que reconozca el monitor que es y no un desconocido?

Saludos

---

### Post by Maciett on 2011-01-06
Moreback, hoy que prendo de nuevo el pc no se ve nada, se quedo la pantalla en negro, suena como cuando inicia, y logie el user de memoria, pero no veo nada, como revierto eso de la clave que active ayer?

Saludos

---

### Post by moreback on 2011-01-06
Te está pasando otra cosa, lo de la clave del metacity sólo se aplica cuando logueas a tu sesión.

---

### Post by Maciett on 2011-01-07
Si no es eso (que es lo único que había modificado antes de que no funcionara),  no se que es.

¿Qué crees que es lo que esta fallando?

¿Cómo lo arreglo?

Saludos

---

### Post by asterix77 on 2011-01-07
> **Maciett said:**
> La verdad no me que da muy claro que es "compiz", sólo quiero poder correr un programa que en windows usaba la aceleración gráfica del sistema.

Si es algo que es bonito útil y no me comerá toda la cpu como el flash bienvenido.



Tengo la sensación de que estamos asumiendo de que tiene compiz instalado, y tal vez no sea el caso.

Podrías postear la salida del siguiente comando en la terminal

$whereis compiz

La salida de esto te indicaría las rutas de donde lo tienes instalado.


Podrías intentar agregar el siguiente repositorio [COLOR=darkblue][B]

[/B][/COLOR]**deb [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) tu_distribución main **

Es un repositorio donde constantemente se actualizan driver para las distintas tarjetas gráficas.

Puede que esto te ayude a solucionar tu problema.

Yo con una tarjeta Ati tenía algunos problemas de aceleración gráfica que solucioné agregando este repositorio para actualizar mi driver de video.

Te dejo el siguiente enlace con más instrucciones, por cierto no veo donde mencionas la distro que usas.

[http://www.taringa.net/posts/linux/6144016/Instalar-el-driver-mas-reciente-de-Intel-en-Ubuntu-10_04.html](http://www.taringa.net/posts/linux/6144016/Instalar-el-driver-mas-reciente-de-Intel-en-Ubuntu-10_04.html)

Te recomiendo eso si, que si vas a usar este método, en vez de "sudo vim /etc/apt/sources.list", uses:

$sudo gedit /etc/apt/sources.list

Es más fácil de usar que vim[SIZE=2][COLOR=Black][FONT=Arial][SIZE=1][COLOR=darkblue][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][SIZE=2][COLOR=Black][FONT=Arial][SIZE=1][COLOR=darkblue]

[/COLOR][/SIZE][/FONT][/COLOR][/SIZE]Lo de la actualización del kernel no lo entiendo, ya que dice que actualices a la versión 2.6.35.6, siendo que la última versión del kernel que está en los repositorios es la 2.6.32.27, pero este paso no es necesario.


Saludos y suerte[SIZE=2][COLOR=Black][FONT=Arial][SIZE=1][COLOR=darkblue].
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE]

---

### Post by Maciett on 2011-01-07
No puedo, probar nada porque no veo nada después del grub, la pantalla se va a negro, se escucha como el login pero no puedo hacer nada, no veo.

Por favor, ¿cómo arreglo esto?


------
Olvídenlo, reinstale y no haré modificaciones de lo que viene.

---

