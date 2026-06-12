---
title: "Problemas de video en general en Ubuntu Studio 10.04"
date: 2010-06-15
forum: Software
---

### Post by cordaxter2.0 on 2010-06-15
Hola. 

Tengo un Intel Core Duo 2 E8200 2.66Ghz, de 2 gb de memoria y una tarjeta Nvidia Geforce 8500GT de 512mb.

Me he pasado de Ubuntu Studio 9.10 a 10.04 sin ningún tipo de inconveniente, salvo la falta del Plymouth. Que de hecho no le presté mucha atención.
EL gran problema comenzó cuando actualicé el kernel a través del Gestor de Actualizaciones, pasándome al Kernel 2.6.32-22-generic.

Fué allí cuando comencé a tener problemas con el video:

- Reproducción de video entre cortado, tanto en totem como en firefox (Youtube).
Estuve buscando información, y una de las soluciones era este comando:

**sudo gstreamer-properties**

Eligiendo en la ventana que se abre: video/salida predeterminada/Complemento/X Windows System (sin Xv).
La cual no me dio resultado.
También intenté desactivando el Compiz, e igual seguí teniendo problemas.

- Otro problemas era el entorno gráfico. Cuando abría ventanas o menús, y luego los cerraba, sus contornos seguían sobre las otras ventanas. Como le pasa a windows a menudo cuando está "sobrecargado". 

Seguí buscando y me encontré con esto:  [B][http://www.taringa.net/posts/linux/5325548/Solucionar-problema-driver-NVIDIA-en-Ubuntu-Lucid-10_04.html](http://www.taringa.net/posts/linux/5325548/Solucionar-problema-driver-NVIDIA-en-Ubuntu-Lucid-10_04.html)

[/B]Lo hice sin mayores inconvenientes, instalando la última versión del driver privativo (195.36.24).

Apenas lo instalé estuve probando totem y compiz, y parecía que se había solucionado, pero al otro día todo volvió a comenzar. 

A estas alturas ya no sé que hacer. 
Agradecería mucho si alguien me puede dar una mano.

---

### Post by cordaxter2.0 on 2010-06-15
Otro dato a tener en cuenta es que en el enlace que dejé en el primer post, dice que hay que desinstalar todos los archivos nvidia, nv y nouveau. Algo que hice, salvo el archivo **libdrm-nouveau1**, ya que al desinstalar este, también me desinstalaría una cantidad importante de archivos, entre los que había 3 esenciales.

---

### Post by leonardomdq on 2010-06-15
Hola cordaxter, tengo un placa Nvidia 9500GT de 1gb y la verdad no tuve problemas en Ubuntu Lucid Lynx.
Instale el driver de esta manera quizás te sirva y sin tantas complicaciones.
Vas al menú **Sistema -> Controladores de Hardware** e instalas el driver **nvidia recomendado** y después reinicias.
Luego vas a la consola y ejecutas **nvidia-xconfig **para que te cree un nuevo xorg.conf .
Por ultimo vas a **Sistema -> Administración -> Nvidia X Server Setting** , configuras resolución y demás parámetros.

---

### Post by guillermolisi on 2010-06-15
Ubuntu Studio debe usar kernel Real Time, no Generic.

Mas info en [https://help.ubuntu.com/community/UbuntuStudio](https://help.ubuntu.com/community/UbuntuStudio), ver link sobre Real Time kernel.

---

### Post by cordaxter2.0 on 2010-06-16
Hola leonardomdq. Luego de seguir ese tutorial, en la ventana de Controladores de Hardware, me aparece este texto: [B]No se están usando controladores privativos en este momento.
[/B]Pese a que sí lo estoy usando, ya que puedo usar Nvidia X Server Setting, y si quisiera, podría activar compiz, aunque me funcionaría con problemas. 

Si te sirve de dato, cuando ejecuto **nvidia-xconfig **me aparece esto: 
[B]Using X configuration file: "/etc/X11/xorg.conf".

ERROR: Unable to write to directory '/etc/X11'.
[/B]
Guillermolisi, en cuanto a lo que me dices del real time, al instalar ubuntu studio, me dio las dos opciones (generic y rt). Siempre usé generic, por el hecho de que tenía entendido que se usaba mas para la captura de sonido/video y su manipulación en tiempo real, cosa que no hago. 
De todas formas probaré como me va en rt.

---

### Post by leonardomdq on 2010-06-16
> **cordaxter2.0 said:**
> Hola leonardomdq. Luego de seguir ese tutorial, en la ventana de Controladores de Hardware, me aparece este texto: [B]No se están usando controladores privativos en este momento.
[/B]Pese a que sí lo estoy usando, ya que puedo usar Nvidia X Server Setting, y si quisiera, podría activar compiz, aunque me funcionaría con problemas. 

Si te sirve de dato, cuando ejecuto **nvidia-xconfig **me aparece esto: 
[B]Using X configuration file: "/etc/X11/xorg.conf".

ERROR: Unable to write to directory '/etc/X11'.
[/B]
Guillermolisi, en cuanto a lo que me dices del real time, al instalar ubuntu studio, me dio las dos opciones (generic y rt). Siempre usé generic, por el hecho de que tenía entendido que se usaba mas para la captura de sonido/video y su manipulación en tiempo real, cosa que no hago. 
De todas formas probaré como me va en rt.
Como decis vos, si estas usando un driver privativo pero no las versiones que te salen en Controladores de Hardware.
Probaste desinstalando el driver que bajaste de la pagina de nvidia e instalar el driver que recomienda desde controladores de Hardware?

---

### Post by cordaxter2.0 on 2010-06-16
Aún no he probado, pero creo que una de las razones es porque tengo desinstalado **nvidia-common, **que según el tutorial es el que detecta los drivers nvidia en  controladores de hardware. 
De todas formas, antes tenía instalado el recomendado y me daba los mismos problemas. Por eso fue que hice esos cambios.

---

### Post by cordaxter2.0 on 2010-06-16
Ya volví a instalar la versión recomendada a través de **Controladores de Hardware**. Pero sigo teniendo el mismo problema. Estuve leyendo por un foro, que lo que respecta a la mala reproducción de video, a veces puede ser causada por tener instalado los motores gstreamer y xine a la vez. Yo desinstalé **totem-xine**, pero dejé unos cuantos **libxine**, porque desconozco si tendré problemas al desinstalarlos.

---

