---
title: "Internet va más lento en la consola"
date: 2009-03-27
forum: Software
---

### Post by Andyvec on 2009-03-27
Hola

He instalado recientemente Ubuntu 8.10 (Un maravilla viniendo de Vista), y tengo el problema de que cuando quiero realizar actualizaciones o usar cualquier comando que requiera Internet desde la consola baja a velocidades muy inferiores a las normales en mi equipo.

Por ejemplo ahora estoy descargando el archivo [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) intrepid/multiverse sun-java6-bin 6-10-0ubuntu2 [28,1MB] de los repositorias oficiales mediante APT-GET y lo esta descargando a un promedio de 5079B/s, cuando mediante firefox puedo descargar coas a 360 Kbp/s

¿Alguien sabe que puede estar pasando?

El problema se mantiene al intentar descargar desde otros repositorios diferentes desde la consola.

Desde ya muchas gracias.

---

### Post by sherwoodinc on 2009-03-27
No debería ir más lento. 
¿Va lento también al instalar paquetes con el Synaptic?

EDIT: Recién leo lo de la prueba con otros repositorios.

Probá bajarte el mismo paquete que tratás de bajar desde consola, pero desde el firefox, poniendo la URL de donde se baja el paquete. Así vemos que no es problema de la conexión con el repositorio en sí.

---

### Post by gmunioz on 2009-03-27
Hola and...:

Nada tiene que ver Ubuntu, la consola o las gráficas.
Es un problema de los repositorios.
Puedes intentar cambiarlos por otros, en mi caso siempre uso los originales de Ubuntu, sin nada antepuesto:

En vez de:
[http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) intrepid/multiverse

Usaría:
[http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/multiverse

Saludos.

---

### Post by Andyvec on 2009-03-27
Primero que nada, gracias por sus respuestas.

Cambié el repositorio a el internacional, la velocidad subió hasta 150 kps, pero sólo por unos segundos, ahora volvió a los míseros valores de siempre. No creo que tenga que ver con los repositorios porque desde lo de launchpad, también baja a esa velocidad.

Probé bajar con Firefox los mismos archivos y los baja a 360 kps (mi velocidad esperada) pero desde la consola no puede.

Realmente es raro, sigo a la espera de alguna solución :(.

Saludos

---

### Post by Andyvec on 2009-03-28
La cuestión se ha solucionado sola, ahora baja a la misma velocidad desde Firefox que desde las aplicaciones de consola y las de actualización/paquetes.

Les agradezco a todos por su ayuda, la verdad es que era algo raro.

---

### Post by pedromagnus on 2009-04-15
Hola, yo tengo el mismo problema. Podrías aclarar algo más de cómo se arregló? En computación los milagros no existen, así que puede que hayas actualizado/instalado algo que puede haber corregido alguna dependencia o configuración...

Por mi parte tenía los repositorios de Argentina puestos. Cambié por los originales (sin el 'ar.' adelante pero funcionan igual o más lentos que los anteriores (entre 2100 B/s y 45 kB/s aprox, tengo banda ancha de 2Mb). Puede ser una mala configuración de... algo??
Tengo ubuntu 8.04 en una notebook HP, con el router y demás correctamente configurados (me costó bastante) y es una lástima no poder aprovechar el ancho de banda...

Gracias al que pueda echar algo de luz encima de mi oscura consola :P
Saludos

---

### Post by josecuervo86 on 2009-04-15
Elijan los repositorios de brasil, son los mas rapidos, lejos!!

---

### Post by Andyvec on 2009-04-15
Esto no tienen nada que ver con los repositorios.

A mi se me solucionó sin que haga nada en particular, en realidad hize muchas cosas que no lograron nada, pero un día empezó a andar bien.

Sin envargo cada vez que pruebo con un Live CD, me vuelve a pasar los mismo.

En princpio volví a intalar Ubuntu, pero esta vez la versión 9.04 BETA (mañana sale la RC) y me pasaba lo mismo, sin embargo cuando terminó de actualizar y reincicié la velocidad fué la esperada y pude continuar bajando a 370 kb/s que es lo que mi porveedor me permite (Fibertel 3MB).

Espero no poder aclarar bien esto, es verdad que en computación no hay magia, sin embargo esto no parece muy "lógico".

Saludos y éxitos

---

### Post by NICOC77 on 2009-04-19
hola yo tengo el mismo problema, despues de instalar ubuntu 8.10 cuando voy a realizar las actualizaciones, la velocidad de descarga es muuuy lenta 2000-3000B/s aprox con picos de no mas de 12Kb/s (Fibertel 2Mb) con lo cual demoraria mas de un dia en actualizar. como soy muy principiante en el mundo linux creia que era algun problema de configuracion del modem (un motorola) pero leyendo esto me parece que no. alguien pudo o sabe como solucionarlo? gracias.

off: es normal que la instalacion tarde tanto? se queda en 82% "actualizando apt" y demora muchisimo... me acuerdo q con distros anteriores no demoraba tanto, o puede que este relacionado con el problema de velocidad?

---

### Post by sajnox on 2009-04-19
Perdon, pero si tiene que ver con los repositorios. Dependiendo de cual elijan la velocidad que tendran. En Argentina el servidor no es de lo mas rapido, y generalmente se instala ese por defecto debido a que es el pais que indicamos nosotros.

La mejor manera es abrir Sistema > Adminiluego Administracion > Origenes del Software y elegir "Descargar Desde" y elegir "Otro" para usar la opcion del mejor servidor, y ahi pinguea a todos los servidores de ubuntu y elige el que mejor conexion tenga

---

### Post by Andyvec on 2009-04-19
Normalmente la velocidad si tiene que ver con los repositorios, pero en este caso no.

Estamos hablando de un error que hay en la distribución que es muy dificil de identificar y señalar.

Yo tenía este error y tube que actualizar a 9.04 donde ya no ocurre más, pero cada vez que uso 8.10 auqnue sea desde el LiveCD el error reaparece, independiente del repositorio que elija.

A todos los afectados les recomiendo que actualizen a Ubuntu 9.04 según las indiciaciones de: [http://www.ubuntu.com/getubuntu/releasenotes/904overview]("http://www.ubuntu.com/getubuntu/releasenotes/904overview")

---

### Post by Hei Ku on 2009-04-19
> **Andyvec said:**
> Normalmente la velocidad si tiene que ver con los repositorios, pero en este caso no.

Estamos hablando de un error que hay en la distribución que es muy dificil de identificar y señalar.

Yo tenía este error y tube que actualizar a 9.04 donde ya no ocurre más, pero cada vez que uso 8.10 auqnue sea desde el LiveCD el error reaparece, independiente del repositorio que elija.

A todos los afectados les recomiendo que actualizen a Ubuntu 9.04 según las indiciaciones de: [http://www.ubuntu.com/getubuntu/releasenotes/904overview]("http://www.ubuntu.com/getubuntu/releasenotes/904overview")

Hay algun bug, reporte o lo que sea que respalde esto, o estamos hablando de evidencia anectodica?

---

