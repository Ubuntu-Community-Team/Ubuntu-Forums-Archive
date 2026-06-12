---
title: "Unity - Detalles de configuración"
date: 2011-04-07
forum: Software
---

### Post by pabloatilio on 2011-04-07
Hola Amigos,

Estoy probando Ubuntu Unity y tengo un par de cuestiones 
en la configuración que no puedo resolver, a ver si alguno tiene idea:

1) los botones maximizar, minimizar, cerrar otra vez se van a la izquiera
   y no encuentro forma de cambiarlos a la derecha. El método que usé para
   el gnome desktop no sirve.( el de ir a gconf-editor --> apps > metacity 
    > general> menu:minimize,maximize,close)

2) No puedo borrar el caché de elementos recientes como lo hago en gnome-  
   desktop tradicional, cuando despliego elementos recientes me sale una  
   lista de decenas de elementos que en desktop borrando elementos  
   recientes no aparecían más.

   Además, cuando voy a --> archivos y carpetas, en los apartados: imágenes,
   presentaciones, videos, documentos, carpetas me lista todos los contenidos,
   me gustaría poder personalizar que cosas muestra y cuales no. O por lo menos
   tener la opción como decía en el punto 2 de borrar todo el caché de elementos
   recientes y que empiece desde cero.

   Por último, lo noto un poco lento para cargar las listas de aplicaciones,
   por ej. si elijo "oficina" se toma un tiempo en cargar todas las herramientas
   disponibles, aún después de hacerlo repetidas veces (primero pensé que era 
   hasta que las ponía en algún tipo de caché) y no creo que sea una cuestión
   de las prestaciones de mi equipo. ¿ a uds cómo les fué con eso ?

¿ será que me falta instalar alguna herramienta de configuración específica para Unity ? 

Gracias a todos, saludos !

Pablo A

---

### Post by juancarlospaco on 2011-04-07
1) Cambiar los botones de maximizar, minimizar, cerrar a la Derecha, solo debes cambiar el tema de escritorio,
en *Apariencia*, elije otro tema, *Dust Sand *por ejemplo, y fijate que los botones vuelven al otro lado.

2) No hay "*elementos recientes*" en las Aplicaciones de Unity, no entendi; 
si recuerda los que usaste mas frecuentemente, que no son los mas recientes.

En archivos y carpetas si tiene los mas recientes, 
puedes deshabilitar el Zeigtgeist para que no recuerde todo eso.

Si instalas el *ccsm* y en el Dash pones "*about:config*" podes configurar el Unity a tu gusto,
sacale efectos al compiz y funcionara mas rapido en tu equipo, es cuestion de placa de video no de cpu.

Al ser un escritorio con aceleracion 3D, es mas importante la placa de video..., 
es decir podes tener un procesador de 4 nucleos, que si tenes una placa de video Via, andara lento igual.

...y pero que hacer si este es el caso?:  instalar Unity 2D

---

### Post by pabloatilio on 2011-04-07
Gracias por tu respuesta

Con "elementos recientes" es así, me refería a lo que hay cuando abris la cuestión de las carpetas.
Me voy a poner a investigar eso del Zeigtgeist y después les cuento si es lo que necesitaba.
Por lo que leí medio rápido parece que por ahí va la cosa. ¡ Asi que gracias ! De todos modos
pienso que podría traer alguna opción que borre todo ese historial de cosas de una forma mas fácil.
Estoy probando el Gnome Activity Journal a ver que onda.

Me sorprende un poco el rendimiento de Unity ya que a la porquería de WinBugs 7 mi equipo
la tira sin problemas con todos sus chiches activados y el ubuntu desktop con todos los efectos también.
Pensaba que Unity aún utilizando aceleración 3D no iba a necesitar muchos más recursos que los que
necesitan los escritorios que mencioné anteriormente. Voy a probar las opciones que me das y después
les cuento, al ccsm ya lo tengo instalado pero otra cosa que vi es que me aparece que el "silenciador"
está activado en la parte de efectos. ¿será entonces que el equipo no se la banca ? 
--> última actualización :  el Unity2D tiene un rendimiento perfecto en mi equipo, 
    pero se nota la diferencia :(((

Lo de cambiar de tema para que cambien de lugar los botones, nose si entendí bien, pero quiero
cambiar los botones sin cambiar de tema jaja.
Le voy a mandar un poco de garfio por ese lado a ver que puedo hacer.
--> última actualización : en Unity2D me conserva los botones como yo quiero, pero por encima pone
    los botones de maximizar, minimizar otra vez a la izquiera ja!


Bueno, gracias de nuevo, saludos
Pablo

---

### Post by juancarlospaco on 2011-04-07
> **pabloatilio said:**
> 
pienso que podría traer alguna opción que borre todo ese historial de cosas de una forma mas fácil.

Se puede, es 1 archivo SQLite, hace un lanzador con el comando:

```
**rm ~/.local/share/zeitgeist/activity.sqlite && zeitgeist-daemon --replace**
```

> **pabloatilio said:**
> 
Estoy probando el Gnome Activity Journal a ver que onda.

Tambien usa Zeitgeist !

Si queres despues te comento o posteo fotos de como configurar Compiz para que no te coma recursos,
lo que come recursos NO es Unity, que son 4 Daemons de como 6Mb de RAM C/U,
lo que come es el Compiz del que Depende.
Nada del otro mundo, solo ley la docu de Unity y con algo de conocimientos de 
*"que le cuesta mas procesar a una placa de video"* la config optima lo hace andar muy bien,
yo tengo una Notebook MSI Wind y anda barabaro :)

Fotos de lo que te comentaba que Unity no consume mucho y son 4 daemons:
[img]http://ubuntuforums.org/attachment.php?attachmentid=187934&d=1301810961[/img]

Consumo de mi Compiz, mucho mas que el de Unity, pero no es exagerado:
[img]http://ubuntuforums.org/attachment.php?attachmentid=187935&d=1301812161[/img]

:D

---

### Post by pabloatilio on 2011-04-07
Gracias por tus respuestas Juan Carlos !

Les comento que lo del Gnome Activity Journal es porque leí que era
una especie de administrador gráfico de Zeigtgeist y en efecto me
permite ir borrando el historial, pero de a grupos de cosas por vez,
no es el típico "borrar historial reciente" que barre con todo.

El compiz lo supe usar con todos los efectos y cosas que trae y la 
máquina no tuvo problemas, así que no sé, me tendré que poner a ver
detalladamente las configuraciones de todo, si consigo algo les aviso.

Con los botones no hay caso, si los configuro a la derecha, en algunas
ventanas queda bien y en otras los tira a la izquierda de nuevo o
le pone encima otra barra con los botones del lado izquierdo a la
vez, queda bastante fiero. Tal vez sea una cuestión de maduración
del proyecto para que todo funcione mejor, no tengo idea en que
etapa están pero por ej. si uso el lanzador del Firefox que está arriba
de todo en Unity, los botones aparecen a la izquiera, pero si uso 
el lanzador que está más abajo, aparecen a la derecha. :confused:

¿Alguien sabe si la cinta con los lanzadores de Unity se puede
configurar para que se oculte automáticamente ?

Saludos a todos
Pablo

---

### Post by juancarlospaco on 2011-04-07
> **pabloatilio said:**
> 
¿alguien sabe si la cinta con los lanzadores de unity se puede
configurar para que se oculte automáticamente ?


:p

---

### Post by pabloatilio on 2011-04-07
Bueno, parece que un problema grave es que en la versión de ubuntu 
que estoy usando (10.10) Unity usa mutter para las ventanas y además
no funciona el plugin de configuración para compiz, osea...](*,)

De acuerdo a las imagenes que dejó Juan Carlos veo que no me aparecen
el unity-window-decorator ni el unity-panel-service en la lista de procesos
ni el compiz (que si aparece en Ubuntu Desktop), osea que tampoco puedo
configurar nada de Unity. 

A cambiar de version y fin del asunto me parece. :neutral:

Gracias a todos, saludos

Pablo

---

### Post by juancarlospaco on 2011-04-07
Es para **Natty+**

---

### Post by aledruetta on 2011-09-05
> **pabloatilio said:**
> 2) No puedo borrar el caché de elementos recientes como lo hago en gnome-  
   desktop tradicional, cuando despliego elementos recientes me sale una  
   lista de decenas de elementos que en desktop borrando elementos  
   recientes no aparecían más.

   Además, cuando voy a --> archivos y carpetas, en los apartados: imágenes,
   presentaciones, videos, documentos, carpetas me lista todos los contenidos,
   me gustaría poder personalizar que cosas muestra y cuales no. O por lo menos
   tener la opción como decía en el punto 2 de borrar todo el caché de elementos
   recientes y que empiece desde cero.

Una solución que encontré es esta:

Es una herramienta de configuración gráfica que permite varias opciones según las necesidades particulares que tengas.

[http://www.webupd8.org/2011/05/zeitgeist-activity-log-manager-now.html](http://www.webupd8.org/2011/05/zeitgeist-activity-log-manager-now.html)

---

