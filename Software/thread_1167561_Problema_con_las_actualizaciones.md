---
title: "Problema con las actualizaciones"
date: 2009-05-23
forum: Software
---

### Post by DarkTemplarMark on 2009-05-23
Hola!
Resulta que inicié en modo de recuperación para ver si había algún problema con paquetes rotos y cosas así, y resulta que mientras hice dicha operación, el computador se reinició como si nada. Lo ignoré, pensando que no sería algo de cuidado, e inicié normalmente. Para mi sorpresa, resulta que al iniciar, aparece un símbolo de no entrar como esos que se ven en Europa
Imagen:
 [[IMG]http://img521.imageshack.us/img521/850/pantallazod.th.png[/IMG]]("http://img521.imageshack.us/my.php?image=pantallazod.png")
Quedé desconcertado, así que fui a ver qué decia:
"Ocurrió un problema al comprobar las actualizaciones"
Hice dobleclick sobre el ícono, y este abrió y cerró automáticamente el gestor de actualizaciones.
Probé por terminal  'sudo aptitude update' y me tiró el siguiente chiste 
Fallo de segmentación
Cosa que me dejó con cara de D: ya que no sé qué diantres significa, y aún así sé que suena feo.
Por ende recurro a vustra ayuda, ya que no puedo instalar nada, no puedo abrir Synaptic, no puedo actualizar, y no puedo iniciar con recovery mode

Datos técnicos:
Ubuntu Jaunty Jackalope
Procesador Pentium 4 3.00 GHz
Tarjeta de Video... omitamos comentarios xD
Y eso... SOS!

---

### Post by Patriciologico on 2009-05-23
Mira esta [Solucion]("http://sistemasoperativos.wordpress.com/2006/12/25/fallo-de-segmentacion-con-apt/") No la he probado, pero lei comentarios positivos. Fijate que en los comentarios de esa solucion, hay otras opciones como clean y autoclean, Jaunty trae una utilidad que se llama "encargado de limpieza" que hara lo mismo. Parte probando el encargado de limpieza, sino funciona, continua con las otras.

Saludos!

---

### Post by DarkTemplarMark on 2009-05-23
Al iniciar el computador otra vez, me topé con una sorpresita bastante fea
(Tuve que sacar fotos con la cámara de mi celular, porque la captura de pantalla no lo reconoce)

Imgs:
[[IMG]http://img206.imageshack.us/img206/8872/dsc00028n.th.jpg[/IMG]]("http://img206.imageshack.us/my.php?image=dsc00028n.jpg")
[[IMG]http://img521.imageshack.us/img521/3482/dsc00029q.th.jpg[/IMG]]("http://img521.imageshack.us/my.php?image=dsc00029q.jpg")

Y cuando me muevo a los extremos con el cursor, se pone aún más feo -.-

[[IMG]http://img136.imageshack.us/img136/2410/dsc00030g.th.jpg[/IMG]]("http://img136.imageshack.us/my.php?image=dsc00030g.jpg")
[[IMG]http://img521.imageshack.us/img521/8602/dsc00031f.th.jpg[/IMG]]("http://img521.imageshack.us/my.php?image=dsc00031f.jpg")

Lo ignoré por un rato, y traté de ver qué iba mal con el encargado de limpieza, y me sacó el símbolito, pero ahora quedo con este chistecito -.-
Qué sucede?

---

### Post by moreback on 2009-05-23
> **DarkTemplarMark said:**
> (...)
Datos técnicos:
Ubuntu Jaunty Jackalope
Procesador Pentium 4 3.00 GHz
** Tarjeta de Video... omitamos comentarios xD**
Y eso... SOS!

Viendo las fotos posteadas creo que se hace imprescindible que nos des detalles de tu tarjeta de video.

Gracias.

---

### Post by mcisternas on 2009-05-23
He leído que las Intel en Jaunty Jackalope dan problemas así. Para verificar qué tarjeta de video tienes, sólo debes escribir en la consola:

> sudo lspci | grep VGAUn abrazo.

---

### Post by DarkTemplarMark on 2009-05-23
> **mcisternas said:**
> He leído que las Intel en Jaunty Jackalope dan problemas así. Para verificar qué tarjeta de video tienes, sólo debes escribir en la consola:

Un abrazo.

Terminal nos revela:
01:00.0 VGA compatible controller: VIA Technologies, Inc. P4M890 [S3 UniChrome Pro] (rev 01)

(See, me da vergüenza semejante tarjeta -.-)
Puede ser la tarjeta la que dé problemas?

---

### Post by Carlos C on 2009-05-24
> **DarkTemplarMark said:**
> Terminal nos revela:
01:00.0 VGA compatible controller: VIA Technologies, Inc. P4M890 [S3 UniChrome Pro] (rev 01)

(See, me da vergüenza semejante tarjeta -.-)
Puede ser la tarjeta la que dé problemas?

mmm esa tarjeta de verdad tiene problemas con los efectos gráficos:

[https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome)

Existe un driver oficial y puedes darle una oportunidad, pero es una tarjeta bien complicada:

[http://linux.via.com.tw/support/downloadFiles.action](http://linux.via.com.tw/support/downloadFiles.action)

---

### Post by kamus on 2009-05-24
> **DarkTemplarMark said:**
> Terminal nos revela:
01:00.0 VGA compatible controller: VIA Technologies, Inc. P4M890 [S3 UniChrome Pro] (rev 01)

(See, me da vergüenza semejante tarjeta -.-)
Puede ser la tarjeta la que dé problemas?

Lo otro para reparar dpkg, instalaste algun paquete a mano o simplemente se chingo de la 'nada'? Es una version final de jaunty?

Saludos

---

### Post by Iced_R on 2009-05-25
> **DarkTemplarMark said:**
> Terminal nos revela:
01:00.0 VGA compatible controller: VIA Technologies, Inc. P4M890 [S3 UniChrome Pro] (rev 01)

(See, me da vergüenza semejante tarjeta -.-)
Puede ser la tarjeta la que dé problemas?

Que no te dé verguenza, yo tengo la misma, pero para AMD (el chipset K8M890 xD).

Ahora, la pregunta del millón: Tenías tu tarjeta configurada? Si era así, y arrancaste la consola de recuperación, trataste de arreglar el X server? Si hiciste eso, puedes decir que se fue al diablo tu configuración, y tendrás que recompilar tu driver. Hay un driver en [http://linux.via.com.tw/support/downloadFiles.action](http://linux.via.com.tw/support/downloadFiles.action) , pero el mismo código dice que PUEDE ser que funcione en tu chipset.


Saludos.

---

### Post by guillermolisi on 2009-05-25
> **Iced_R said:**
> Que no te dé verguenza, yo tengo la misma, pero para AMD (el chipset K8M890 xD).

Ahora, la pregunta del millón: Tenías tu tarjeta configurada? Si era así, y arrancaste la consola de recuperación, trataste de arreglar el X server? Si hiciste eso, puedes decir que se fue al diablo tu configuración, y tendrás que recompilar tu driver. Hay un driver en [http://linux.via.com.tw/support/downloadFiles.action](http://linux.via.com.tw/support/downloadFiles.action) , pero el mismo código dice que PUEDE ser que funcione en tu chipset.


Saludos.
Hace mas de dos años que estoy usando dos maquinas con esa placa de video.
Bah, usando es un decir porque en distintas oportunidades intente hacerlas funcionar con los drivers de OpenChrome y UniChrome, inclusive siguiendo procedimientos encontrados en UbuntuForums, otros via Google y los que figuran en Via Arena ... y nada, nunca logra que funcione ni siquiera con aceleracion 2D.

He leido que quienes lograron algun avance han manifestado experimentar un rendimiento desastrozo por lo que han vuelto al driver Vesa.

En definitiva, no perdi mas tiempo y dado que ATI aun no habia liberado su tecnologia, reemplace las VIA por nVidia y resuelto el problema definitivamente.

Desde mi punto de vista, hoy, intentaria el reemplazo por placas ATI ya que esta marca posee un perfil mas amigable con SL/OS que nVidia (que sigue con drivers cerrados).
Hay que elegir muy bien el modelo de placa ATI a utilizar ya que algunos drivers no estan suficientemente pulidos y no funcionan bien.

PS: Con las placas SIS sucede algo similar que con las VIA con la diferencia de que SIS se ha retirado del mercado.

---

### Post by DarkTemplarMark on 2009-05-25
Intenté aplicar una de las soluciones que me dieron, pero cuando estaba modificando el archivo xorg.conf, se me cortó la electricidad.
Resultado: Cuando inicié otra vez, podríamos decir... funó la interfaz visual, el cursor se movía desde un lugar a otro con velocidad cámara lenta, y el hecho de intentar solucionar el chiste devolviendo el archivo original respaldado, resultó en un epic fail horrendo por cuanto se quedaba pegado. Apagué el ordenador por las buenas (Tenía el botón de encendido configurado para apagado por las buenas de antemano), y dejé el ordenador porque tenía cosas importantes que hacer.
Volvi de la facultad ahora, y de mal en peor, ahora el cursor ni siquiera se mueve. Intenté reparar el problema gráfico a través del recovery mode, pero me dice que el archivo respaldado está en /etc/x11/xorg.conf.20090525172841
Viendo que no había mucho con qué lidiar, inicié con el CD de Ubuntu 9.04 que tengo, y desde la Live Session estoy posteando ahora. Al menos funciona correctamente, y no tengo problemas de lag.
Ahora, como puedo acceder al sistema de archivos desde aquí, pero no puedo modificar los archivos de este, por lo que no puedo arreglar el archivo dañado.
La pregunta de los 120 millones es: Qué se puede hacer con todos estos antecedentes? (Antes de hacer una reinstalación de Ubuntu, claro está -.- Hay 4 gigas en archivos que tengo que saber rescatar sí o sí)

---

### Post by Carlos C on 2009-05-26
uff, estimado, que lío. El peor momento para que se te corte la luz. De todas maneras si quieres modificar el archivo xorg.conf de tu sistema puedes hacerlo. Lo que debes hacer es crear una carpeta y luego montar en ella tu partición "/". Puedes mirar acá como hacerlo:

[http://ubuntuforums.org/showpost.php?p=7321465&postcount=19](http://ubuntuforums.org/showpost.php?p=7321465&postcount=19)

---

### Post by DarkTemplarMark on 2009-05-26
Lo he hecho al pié de la letra, pero el gran detalle es el siguiente:
[[IMG]http://img297.imageshack.us/img297/2863/pantallazoa.th.png[/IMG]]("http://img297.imageshack.us/my.php?image=pantallazoa.png")

Sí, a lo menos una docena de respaldos del xorg.conf, todos exactamente iguales, y lo peor de todo, es que no he podido eliminar ninguno, porque alega:

> 
No puede mover el archivo a la papelera. ¿Quiere borrarlo inmediatamente?
El archivo «xorg.conf» no se puede mover a la papelera.
Y al borrar:
> 
Error al borrar.
Hubo un error al borrar xorg.conf.
Error al eliminar el archivo: Permiso denegado
O sea, la tapa del año.

Por tanto, qué hago? Estoy barajando seriamente instalar Ubuntu 7.10 en lo que queda de disco duro, y poder rescatar mis archivos para formatear de nuevo y comenzar desde el principio, porque ya no encuentro solución.
Esperaré hasta mañana para ver si alguien más puede ver otra solución menos radical.

Os agradezco a todos vosotros por vuestra ayuda y posibles soluciones, he aprendido bastante con todos vosotros.

---

### Post by Carlos C on 2009-05-26
¿Probaste ejecutar nautilus con permisos de administrador? Puedes abrir el terminal y escribir:
```
sudo nautilus
```

---

