---
title: "kernel panic error"
date: 2010-05-12
forum: Software
---

### Post by drazhe on 2010-05-12
Hola, anoche prendo mi PC de escritorio y selecciono mi querido Ubuntu 10.04 instalado hace poco y que prácticamente no usé, después de la instalación limpia y las actualizaciones (plugines, controladores de video, rar y demás cosas) no use mas el Ubuntu de esa máquina. y anoche cuando quiero encender la Pc me tira ese error.. que pudo haber pasado y como se soluciona? 

Nota aparte, como dije antes, ese Ubuntu, casi no se uso y tengo pensado reinstalar todo este fin de semana, pero me gustaría saber que pudo haber pasado para que me tire el error de Kernel Panic.

---

### Post by kmai on 2010-05-12
El kernel panic puede haber sido provocado (probablemente) por alguna cosa instalada en la actualizacion, o algun modulo nuevo (quiza de algun dispositivo como la placa de video)

Lo que podrias hacer es meterte con un live cd, y fijarte en el sistema de archivos si encontras algun log (cuando te pase algun error asi, anotate la fecha y hora asi podes buscar mas facil)

para ampliar:
[QUOTE=Wikipedia]
**kernel panic** (en español: **núcleo en pánico**) es un  mensaje mostrado por un [sistema operativo]("http://es.wikipedia.org/wiki/Sistema_operativo") una vez detectado un error interno de  sistema del cual no se puede recuperar. Los kernel panic usualmente  proveen información de depuración que es útil sólo para los  desarrolladores del sistema operativo.

Intentos del sistema operativo para leer una dirección de memoria  inválida o no permitida son una fuente común de kernel panics. El error  también puede ocurrir como resultado de un fallo de [hardware]("http://es.wikipedia.org/wiki/Hardware").
 Es probable también que se presente si falta algún módulo que deba ir  pegado al kernel dependiendo del hardware con el que se cuente.
[...]

Un kernel panic puede ser producto de una  vulnerabilidad en algún módulo del [núcleo]("http://es.wikipedia.org/wiki/N%C3%BAcleo_%28inform%C3%A1tica%29") de forma malintencionada,  logrando corromper la integridad del sistema.[/QUOTE]

Fijate si tenes algun modulo de memoria jodido haciendo un memtest desde un cd de ubuntu, pero es probable que sea o sobrecalentamiento de memoria/cpu o hardware defectuoso. Si no es ese el problema, entonces habria que ver qué instalaste/actualizaste y ver si puede entrar en conflicto con el kernel.

El kernel panic puede ser producido por accesos invalidos a memoria (ya sea a posiciones no permitidas o las cuales contengan datos corruptos), por eso sugiero el paso de arriba


Por ejemplo, un paquete para habilitar la aceleracion 3d de la placa de video, es una causa mas probable que instalar un paquete que isntale gimp o un editor de texto.

Quedo pendiente a tu respuesta!

---

### Post by drazhe on 2010-05-12
la verdad es que casi ni la use, después de instalar desde 0 Lucid Lynx, y ponerlo a punto (rar, drivers y cosas así, aun me faltan el k3b y otras cosas que quiero) pero casi casi lo tenia a punto. bueno estuve trabajando en otra maquina sin que nadie usara la PC de escritorio con Lucid, y ayer cuando me dispuse a terminar de instalar lo que faltaba me salto eso del kernel... si mal no recuerdo después de instalar ubuntu y drivers de video funciono bien un par de días, lo único que hacia era navegar en internet y ver videos de youtube ya que esa Pc no tenia nada aún. por eso me resulta raro lo del kernel panic...

---

