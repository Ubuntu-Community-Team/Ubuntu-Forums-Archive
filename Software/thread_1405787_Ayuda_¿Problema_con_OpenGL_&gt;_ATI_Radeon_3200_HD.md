---
title: "Ayuda: ¿Problema con OpenGL? &gt; ATI Radeon 3200 HD"
date: 2010-02-13
forum: Software
---

### Post by de-troit on 2010-02-13
Hola colegas:

Tengo un problema que desde hace tiempo me viene rompiendo las pelotas. Lo que pasa es que uso el driver privativo para la Tarjeta Gráfica ATI Radeon 3200 HD pero tengo un problema, no estoy seguro de que esto sea, pero creo que es el OpenGL o algo relacionado con eso. Esta es mi hipótesis ya que al ejecutar Cairo Dock con OpenGL ocurre lo de la imágen:

[IMG]http://img42.imageshack.us/img42/7607/pantallazobf.png[/IMG]

También en mi Panel inferior donde tengo la lista de ventanas (con transparencia) ocurre esto:

[IMG]http://img200.imageshack.us/img200/9458/pantallazo1m.png[/IMG]

Creo que Ubuntu saca una foto del fondo de pantalla que abarca el panel inferior y se la pone como fondo para simular la transparencia. Esto me consume más RAM debido a que al abrir o cerrar una nueva ventana y por ende refrescar o actualizar el panel, hace que este demore más en hacerlo como consecuencia de este "proceso adicional" para simular la transparencia.

Los efectos del Compiz andan bien (no perfectos).

También tengo ioQuake 3 instalado (usa OpenGL) y anda bien.

A veces dudo que sea algo relacionado con el OpenGL, por eso hago las consultas.

También probé instalando la última versión del driver original echo por ATI para mi tarjeta (la versión 10.1) en donde no tenía este problema, pero la verdad es que me andaba pésimo, hice un test para ver los frames en 5 segundos con el comando "glxgears" y me marcaba 600 promedio, en cambio con el driver privativo me marca 4500 promedio, además los efectos del Compiz andan bastante mejor. Queda claro la diferencia de rendimiento. Esto es raro porque a otros usuarios que tienen la misma Tarjeta Gráfica que yo les funciona mejor el driver de ATI, en mi caso es lo contrario.

Otra cosa que quiero mencionar es que cuando visualizo una página web con muchas imágenes al bajar el scrollbar esta lo hace como si se saltara fotogramas, como pegada, a veces mientras voy moviendo el scrollbar las imágenes se salen de su lugar y luego se acomodan (al detener el movimiento del scrollbar).

Ojalá que con todo este problema que les describí me puedan ayudar a averiguar cual es el problema, qué es lo que falta y como podría solucionarlo.

Por si acaso soy usuario de la versión Karmic Koala.

Muchas gracias por su atención.
Saludos!

---

### Post by Carlos C on 2010-02-13
Hola. Tengo una duda, cuando recién instalaste karmic, antes de instalar el driver de ATI, ¿no te funcionaban bien los efectos? Te lo pregunto porque en mi caso tengo una ATI (no es el mismo modelo) y no es necesario que instale nada.

---

### Post by de-troit on 2010-02-13
> **Carlos C said:**
> Hola. Tengo una duda, cuando recién instalaste karmic, antes de instalar el driver de ATI, ¿no te funcionaban bien los efectos? Te lo pregunto porque en mi caso tengo una ATI (no es el mismo modelo) y no es necesario que instale nada.

Sí, los efectos andan bien desde que instalé Karmic Koala (no tuve que instalar nada). Tengo que mencionar que antes tenía Jaunty Jackalope (formatié el disco al instalar este), en el cuál funcionó de inmediato el driver, pero el privativo de Ubuntu, luego de eso actualizé a Karmic pero el problema que les muestro viene desde que instalé Jaunty.

Saludos!

---

### Post by Carlos C on 2010-02-14
> **de-troit said:**
> Sí, los efectos andan bien desde que instalé Karmic Koala (no tuve que instalar nada). Tengo que mencionar que antes tenía Jaunty Jackalope (formatié el disco al instalar este), en el cuál funcionó de inmediato el driver, pero el privativo de Ubuntu, luego de eso actualizé a Karmic pero el problema que les muestro viene desde que instalé Jaunty.

Saludos!
Estimado, estoy un poco confundido, en el post original dices que usas Karmic, pero ahora entiendo que es Jaunty ¿Qué versión es la que te presenta el problema ahora?

---

### Post by de-troit on 2010-02-14
> **Carlos C said:**
> Estimado, estoy un poco confundido, en el post original dices que usas Karmic, pero ahora entiendo que es Jaunty ¿Qué versión es la que te presenta el problema ahora?

**Tenía Jaunty** con ese problema, luego actualizé a Karmic y el problema seguía. **Actualmente tengo Karmic**.

Se entiende?

Saludos! ;)

---

### Post by andreselsuave on 2010-03-03
Yo no consigo activar efectos, ni composición, ni opengl, ni nada... tengo ati x300 (rv370) y uso el driver libre (radeon) ¿Me echais un cable?

andreselsuave

---

### Post by Carlos C on 2010-03-05
de-troit, disculpa por preguntar, entendí que ahora tienes karmic jajaja, pero ahora tengo la duda si acaso continuas con problemas.

andreselsuave, hola. Por favor abre un thread nuevo y nos presentas tu problema con toda la información necesaria (modelo de tarjeta y versión de Ubuntu). Trataremos de ayudarte.

Saludos.

---

