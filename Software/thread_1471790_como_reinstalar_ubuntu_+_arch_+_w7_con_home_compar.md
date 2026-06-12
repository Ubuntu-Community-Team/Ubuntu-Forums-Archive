---
title: "como reinstalar ubuntu + arch + w7 con /home compartida"
date: 2010-05-03
forum: Software
---

### Post by r@fitiiixxx on 2010-05-03
hola, hace mucho no venía por acá, puesto que mi forma de pensar difiere de la de muchos de acá en el foro, por tanto me he ausentado. Pero tengo un problema:

con la salida de Ubuntu 10.04 decidí pasarme de vuelta a GNOME puesto que está mejor soportado por la comunidad, menos buggeado y más estable.

 También decidí que quiero instalar Arch Linux puesto que me han contado maravillas y quiero aprender a usarlo, a esa distro en especifico.

 Además se me "murió" winXP que usaba para jugar juegos de importantes gráficos, y pagos, muy pocas veces, o cuando los programas lo ameritaban.

 Y la interfaz en Kubuntu es bastante inestable, así que lo que necesito es instalar 3 SO's en un disco de 300gb así:

> 
[I]
[LIST]
Instalar windows 7 ultimate 64 bits--------150gb puesto que los juegos pesan mucho (de esto me encargo por otros medios)
[/LIST]
[LIST]
Instalar Ubuntu 10.04 64 bits----------75gb (incluyendo la swap) para el sistema donde trabaje, juegue y haga mi vida
[/LIST]
[LIST]
Instalar Arch Linux 64 bits------------ 50gb (incluyendo la swap)
[/LIST]
[LIST]
Dejar 25 gb libres para datos o back up... podría ser NTFS o FAT
[/LIST]
[LIST]También necesito saber como hacer para tener /home compartido entre las dos distros
[/LIST]
[/I]

 Espero sepan ayudarme, gracias por su tiempo.

---

### Post by oktubrer on 2010-05-04
La introducción no parece la más acertada para pedir ayuda, pero no obstante ello, veamos que podemos hacer.
Para eso, ayudanos a ayudarte:  ¿En que parte del proceso necesitas ayuda? ¿Particionado? ¿Grub? ¿Avanzaste con el tema y te trabaste en algun lado?
Para el home compartido entre las dos distros, habría que hacer una partición aparte para montar /home.   Por lo que te recomendaría dejar menos espacio para los / de ambas distribuciones de linux, y generar un /home con buen tamaño.  La swap también es una partición aparte, y es compartida.

---

### Post by r@fitiiixxx on 2010-05-04
> **oktubrer said:**
> ...
Para el home compartido entre las dos distros, habría que hacer una partición aparte para montar /home.   Por lo que te recomendaría dejar menos espacio para los / de ambas distribuciones de linux, y generar un /home con buen tamaño.  La swap también es una partición aparte, y es compartida.

uhh claro, yo suelo usar mucho home para poner mis videos y mi musica lo cual pesa bastante... eso sería lo grueso del SO... así que podría hacer un home de 75gb y los otros 75 partirlos en 2 para la raíz y los swap de cada sistema...

Una pregunta, puedo usar el mismo swap para las dos distros? o tengo que hacer una para c/u?

lo que yo no se y no tengo idea de que buscar ni hacer de movida es:

[LIST]
Instalar dos distros más un win cosa de que salga en el grub las 3 opciones.
[/LIST]
[LIST]
Hacer /home/ por separado, no tengo idea de como hacerlo, y que se monte automaticamente en las dos distros, una pregunta con esto, varía la velocidad de transferencia? es decir, es más lento? porque he experimentado lentitud al mover archivos desde la partición de win a la de linux y viceversa en el pasado... o la velocidad es la misma como si home fuera uno por distro y sin montarla aparte?
[/LIST]

Eso nada más, de echo si sabés o encontrás en internet algo que me sirva para hacerlo es suficiente, puesto que no lo voy a hacer ni hoy ni mañana, pero si probablemente la semana que viene y quiero ir teniendo todo listo, como no se del tema me quiero orientar bien en el asunto del tema particionado...

 Por ahora lo que supuse como camino sería instalar primero win7 con NTFS formateado rapido (que opinión tenés al respecto del formateado rapido?), luego instalar Ubuntu 10.04 y hacer las particiones con Gparted, no se como y eso busco un poco, el tema de RE-particionar el disco una ves instalado ubuntu. Para poder modificar y luego instalar Arch tranqui.
 No se en que parte de la instalación necesito hacer el /home/ aparte... bueno eso es todo. Gracias por ayudarme.

---

