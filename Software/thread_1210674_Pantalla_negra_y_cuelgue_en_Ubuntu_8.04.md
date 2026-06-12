---
title: "Pantalla negra y cuelgue en Ubuntu 8.04"
date: 2009-07-11
forum: Software
---

### Post by mujica on 2009-07-11
Hola, primero, no sé si este post corresponde aquí, pero no sabía dónde ponerlo :S

Bueno, tengo un problema en Ubuntu 8.04 desde hace algún tiempo, y no he podido solucionarlo. He buscado información en otros foros y no he encontrado nada que me ayude, algunos mencionan que es un bug, pero no dicen cómo arreglarlo.

Lo que ocurre es lo siguiente: de repente, sin previo aviso, la pantalla se pone negra y aparece el siguiente mensaje:

*Starting deferred execution scheduler atd     [Ok]
*Starting periodic command scheduler crond     [Ok]
*Checking battery state                        [OK]
*Running local boot scripts (/etc/rc.local)    [Ok]

Y ahí se queda, la única manera de salir de ahí es apagar el pc con el botón. Esto pasa en cualquier momento y, a veces, puede ocurrir hasta tres veces durante el mismo día o puede no ocurrir en semanas. Además, dice "Checking battery state [OK]" independientemente de si la batería está o no puesta en el notebook.

Ojalá alguien pueda ayudarme o darme alguna pista sobre lo que pasa. 

¡Muchas gracias!

---

### Post by flakojaime on 2009-07-12
HOla mujica

Prueba estas soluciones, hablan de ese problema cuando haces una actualización. Te dan tambien unas combinaciones de teclas que puedes usar para confirmar.

[SIZE=5][aqui]("http://foro.elhacker.net/gnulinux/ubuntu_se_cuelga-t236878.0.html;msg1133219")[/SIZE]  y  [SIZE=5][aca]("http://foro.portalhacker.net/index.php/topic,68049.5/wap2.html")[/SIZE]

Saludos):P

---

### Post by mujica on 2009-07-12
Hola, gracias por tu respuesta. Lamentablemente, ya había leído esos foros y si bien mencionan el problema, no dan ninguna solución verdadera. Se habla de desactivar Compiz, pero esto sucede con o sin Compiz.

Gracias de todas maneras.

---

### Post by Carlos C on 2009-07-15
Hola. Una opción es que actualices el sistema a 8.10 o 9.04. No es una buena respuesta, lo sé, pero no pierdes nada con probar.
Saludos.

---

### Post by moreback on 2009-07-16
Dala impresión que se cayeran las X, ¿Que tarjeta de video tienes? ¿lspci?

---

### Post by mujica on 2009-07-17
Hola, Carlos C, gracias por tu respuesta.Quizás debería actualizar, pero me da lata hacer una instalación limpia y perder todas las configuraciones, claro que si no encuentro otra solución, es lo que tendré que hacer. 

Gracias también por tu respuesta, moreback. Tengo una ATI Radeon Xpress 200M. ¿Qué son las X?

---

### Post by moreback on 2009-07-18
Las ATI tienen un driver mejor en Ubuntu 9.04, por lo que no es mala idea actualizar o por lo menos probar con el LiveCD.

La actualización no formatea nada, así que no perderás tus datos.

Saludos.


PD: "las X" es lo que se conoce como servidor X, que es el que maneja todos los gráficos en la pantalla.

---

### Post by Carlos C on 2009-07-18
mujica, respecto a lo que dice moreback, es posible actualizar el sistema sin volver a instalar todo desde cero, es diferente. Se puede hacer desde el panel superior, entrando en  Sistema > Administración > Gestor de actualizaciones. Yo tengo la misma tarjeta de video y en Jaunty se pueden usar los drivers libres, con compiz corriendo sin necesidad de cambio alguno.
Saludos.

---

### Post by kamus on 2009-07-18
> **mujica said:**
> Hola, Carlos C, gracias por tu respuesta.Quizás debería actualizar, pero me da lata hacer una instalación limpia y perder todas las configuraciones, claro que si no encuentro otra solución, es lo que tendré que hacer. 

Gracias también por tu respuesta, moreback. Tengo una ATI Radeon Xpress 200M. ¿Qué son las X?

Por casualidad anterior a este problema hiciste alguna actualizacion de kernel o controlador de video? puede que espere subir el X y no pueda aunque en algun momento se aburra y te envie a la terminal si no podrias probar con control + c para tratar de cancelar el inicio del demonio que esta tratando subir y no puede o lo otro es que intentes entrar a una terminal secundaria con control + alt + f2 (f3) y puedas tratar de ver los logs para tener un diagnostico mas certero del problema y puedas publicarlo en el foro ;)

Salu2

---

### Post by mujica on 2009-07-18
Hola, 


         Kamus, no he hecho ninguna actualización aparte de las automáticas.

Leí todas sus respuestas y he seguido investigando; he concluido que lo mejor que puedo hacer es actualizar. Pero no quiero hacer un upgrade a 8.10 y después a 9.04, lo intenté una vez y fue un desastre... Voy a tratar con una instalación desde cd, ¿hay alguna manera de guardar las configuraciones y recuperarlas después?

Muchas gracias por su ayuda.

---

### Post by Carlos C on 2009-07-20
Puedes mirar lo que hizo jorval:

[http://ubuntuforums.org/showthread.php?t=1200962](http://ubuntuforums.org/showthread.php?t=1200962)

Espero que te sirva.

---

