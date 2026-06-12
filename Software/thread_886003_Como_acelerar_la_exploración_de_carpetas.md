---
title: "Como acelerar la exploración de carpetas?"
date: 2008-08-10
forum: Software
---

### Post by caparral on 2008-08-10
[I]Bueno mi pregunta es, cómo puedo acelerar la exploración de carpetas? Ya que se me hace lenta la velocidad de exploración de carpetas, más lenta que en windows, me agradaría que estuviera al toque. Por ahí en otro foro ví la recomendación de cambiar de explorador (Nautilus) pero no sé si sea una buena alternativa; más que nada esta pregunta va para saber quién ha cambiado de explorador y ha experimentado una mejora en la velocidad de exploración, o si alguien sabe de algun truco para reducir el tiempo de espera al abrir una carpeta, cabe recalcar que no ejecuto casi ningún programa y/o aplicación, una de las que si ejecuto es Compiz, no sé si esa aplicación disminuya la velocidad de navegación entre carperas de manera importante, sino afecta demasiado en el rendimiento, entonces quisiera saber que puedo hacer, porque noto lenta la navegación entre carpetas, no demasiado lenta pero si quisiera que estuviera al toque como en windows!! 

Algunos componentes de mi máquina (HP Pavilion DV6646us):

[B]Processor: AMD Turion 64x2 1.9 ghz 
System Memory (RAM): 2 GB 667 Mhz
Graphics Card: Nvidia Geforce 7150M (1200x800)
Hard Drive:160 GB SATA II (5200rpm)[/B]

Saludos y muchas gracias de antemano!!![/I]

---

### Post by [P]oli on 2008-08-10
Cuál es el sistema de ficheros de la partición? (NTFS, FAT(16 o 32), EXT3, etc etc)
Seguramente eso esté molestando

---

### Post by caparral on 2008-08-10
*El sistema de ficheros es obviamente ext3, es en la misma partición de Ubuntu en la que noto lentitud al abrir las carpetas!!!*

---

### Post by [P]oli on 2008-08-10
La verdad no se me ocurre nada, las carpetas son muy "pesadas"?, por ejemplo de fotos en alta resolución, etc etc

---

### Post by faktorqm on 2008-08-10
Capaz lo que te esta pasando ahi es que tenes muchos archivos que son pre-visualizables, y la configuracion predeterminada de nautilus te los muestra a todos. Yo lo que hice para solucionar eso, fueron varias cosas, la primera, leer todo en modo lista. resultaba un poco incomodo a veces, y entonces fui a editar -> preferencias y ahi tenes para jugar. Dentro de toooodas las opciones tenes para quitar la pre-visualizacion de archivos de tipo conocidos. tambien te recuerdo que gnu/linux no reconoce los archivos por su extension, sino por su formato, es decir, vos podes tener un archivo zip que se llama "foto.jpg" pero el nautilus te va a mostrar que se abre con el gestor de archivadores. 
tema medio al margen: desactivaste tracker? es la causa del 70% de los relentizamientos de pc's en la ultima version de ubuntu... me parece que vamos a tener que levantar un sticky con eso, por que los que tienen compus medio lentejas como la mia la diferencia se siente y mucho...
Salu2!

---

### Post by caparral on 2008-08-11
*Hola faktorqm antes que nada gracias por tu respuesta, de lo que me dices sí lo he realizado, el detalle de la visualización en modo lista, al igual que en cualquier otro SO el tener archivos configurados para que sean visualizados en iconos, mosaicos o en otra vista que no sea en el listado de archivos es bien sabido que ralentiza el despliegue de la exploración de ventanas, aunque con la capacidad de mi laptop tanto en windows xp como en windows vista la tengo en modo iconos, y no afecta casi en nada la navegación, aunque si mejora un poco en modo lista, pero muy poco, de hecho en Ubuntu al navegar en las carpetas de mi usuario principal (en modo pre-visualización) es rápido (no tan rápido como en los windows) pero en carpetas de sistema de Ubuntu a veces exagera en cargar, recalco que no estoy a favor de windows en ese aspecto y prueba de ello es que pregunto porque quiero optimizar al máximo Ubuntu para sacarle el mayor provecho y poco a poco dejar de lado windows. Respecto a lo que me comentas si desactivé el tracker, la verdad no, no lo he desactivado, como tengo apenas 1 semana de usar al máximo Ubuntu apenas me estoy metiendo en la optimización del sistema, he ahí el porqué de la pregunta, si me pudieras explicar un poco lo del tracker y como desactivarlo te agradecería mucho, saludos*!!!

---

### Post by javier-2714 on 2008-08-11
Mira yo tenia ese problema y lo solucione instalando " thunar " es el explorador  de xforce es muchísimo mas rápido cambio un 100 % la rapidez al explorar carpetas y archivos los podes instalar desde añadir y quitar o synaptic no entiendo mucho pero ubuntu con gnome trae nautiluz para la exploración que es bastante pesadito  sino proba instalando xubuntu te ba a ser la maquina muchísimo mas rápida saludos.

---

### Post by caparral on 2008-08-11
*Hola javier-2714 antes que nada gracias por responder, mi pregunta para ti es: ¿tienes Ubuntu o Xubuntu? ¿Has probado thunar en Ubuntu? tengo entendido que la versión Xubuntu es mucho más ligera y optimizada que Ubuntu pero no trae tantas aplicaciones interesantes al igual que en Ubuntu además de tener un entorno gráfico diferente, por eso es más eficiente, el detalle es que me agrada mucho Gnome, ya le he tomado la jugada y en este caso me gustaría seguir con él, lo que mencionas del explorador "thunar" ciertamente esta en los respositorios de Ubuntu, más sin embargo antes de instarlo me gustaría saber si en verdad me lo recomiendas ya que no quiero echar a perder el SO instalando algo de lo que no conozca y pueda perjudicar, pero en este caso si es una recomendación tuya me arriesgaré al cambio de explorador, de cualquier manera algo había leído en relación al cambio de un explorador xforce, porque es verdad que nautilus es tremendamente pesado, de antemano muchas gracias!!!*

---

### Post by javier-2714 on 2008-08-11
Actualmente estoy usando ubuntu feisty 7.04 con gnome y le instale thunar cambio notablemente xubuntu es diferente pero se pueden instalar y personalizar e incluso poner muchas cosas de gnome sin problemas yo te diría primero instala thunar aver que pasa por ahí no es necesario que cambies abri 
añadir y quitar escribí thunar en es buscador y lo instalas luego lo buscas en aplicaciones/accesorios haber como te ba saludos.

---

### Post by faktorqm on 2008-08-11
El thunar anda hasta ahi no mas.... Yo en casa tengo una red y para empezar a hablar thunar no trae soporte para eso...... y creo que tampoco trae para ponerle el arbol a la izquierda... o al menos yo no lo encontre. Al menos para mi, thunar no cumple con mis expectativas de navegador de archivos. 
xubuntu anda mas rapido, trae xfce (NO xforce como alguien dijo por ahi) como escritorio por defecto, pero no trae tantas funcionalidades como gnome. Ahora, si para lo que vos necesitas, xubuntu te sirve, adelante!
Salu2!

---

### Post by caparral on 2008-08-11
[I]Tienes razón es xfce, como yo no conocía y vi algo similar pensé que si era xforce xD, pero ya me informé y sí es xfce. La intención no es cambiarme a Xubuntu, en el caso que comenta javier-2714 por eso le pregunté si lo tenía instalado en Ubuntu y ya lo localicé para instalar pero me he topado con una página la cual da varias opciones junto con otra que ví por ahí respecto a performance, se las dejo:

[Como mejorar el rendimiento de Ubuntu/Gnome]("http://my.opera.com/suribe/blog/2007/05/04/como-mejorar-el-rendimiento-de-ubuntu-gnome") En esta página nos dan opciones de instalar otro explorador de archivos sin necesidad de cambiar de Distro, conservando Ubuntu y no metiendo Xubuntu.

[Ubuntu Performance Guides]("http://blog.lxpages.com/2007/04/24/ubuntu-performance-guides/")

Seguiré indagando en el tema, de cualquier manera gracias a todos por sus respuestas!!! 

¿Qué opinan de Pcman file manager? He visto en varios lados que lo recomiendan más que nautilus y tiene una interfaz muy similar a la de nautilus, ojalá puedan brindarme sus opinones quienes lo utilizan o lo han probado[/I]

---

### Post by javier-2714 on 2008-08-11
Perdón tiene razón faktorqm se escribe xfce y lo único contrario es no trae para navegar por la red si se puede poner el árbol igual es una opción para navegar por los archivos mas usados yo lo uso y es mucho mas ágil que nautilus es mucho mas completo pero es cuestión de gustos saludos.

---

### Post by caparral on 2008-08-11
[I]Les dejo esta información extraida de Bak.com, como no se puede entrar sin ser usuario les cito la información:

**Dlinx** 

Pues yo a lo mucho he probado 3, el primero es nautilus que como ya sabrán muchos es el que viene por defecto en gnome, y tal vez sea el que muchos usuarios de Ubuntu vayan a conocer. Tiene sus ventajas en cuanto a red se refiere, lo de que no te deje entrar a las particiones pues puede que sea por los permisos que tiene dicha partición, y si quieres entrar como usuario normal no te deja verla. ¿Has tratado a entrar como root?.
También nautilus tiene la posibilidad de ampliarse con Scripts o funciones personalizadas, a mi me va muy bien y es el que uso hasta ahora.

El que sigue es Thunar, no se si ya lo habrás probado, es un poco simple en apariencia pero al tener opciones personalizadas que puedes añadi, puedes hacer que cambie de formatos a imagenes o que abra una terminal como root, entre muchas cosas más.
Hay plugins de thunar para poder compartir achivos. Actualmente thunar es el gestor de archivos del entorno de escritorio XFCE.
Aquí tienes unas capturas de pantalla:

[http://thunar.xfce.org/screenshots.html](http://thunar.xfce.org/screenshots.html)

Nota: por algun motivo los iconos en gnome se ven muy gigantes.
Por lo que he investigado thunar si soporta particiones de windows pero nunca lo he hecho ya que ya no queda nada de ese SO en mi PC (bueno solo la etiqueta del serial de windows ).

Por último no se si te habrás equivocado y en vez de decir pacman quisiste decir PCman File manager.
Este es otro que he probado y me ha gustado en varios aspectos, pero un pequeño detalle me hizo quitarlo y es que no puedes obtener miniaturas de archivos como imágenes o como documentos de PDF u ODF.
De este si no conozco mucho así que simplemente les dejo la pagina oficial.

[http://pcmanfm.sourceforge.net/](http://pcmanfm.sourceforge.net/)

En cuanto a las otras opciones, pues son de KDE, dependiendo de tu entorno si es Gnome o KDE creo que tu deberías de decir con cual quedarte, Dolphin trabaja muy bien en las versiones estables hasta ahora de KDE 4 pero si lo usas en Gnome será muy lento y puede que te de problemas y se cierre inesperadamente.

De la mayoría de las alternativas a nautilus se me paso decirles que excepto por PCman File manager ningún otro tiene soporte para mostrar iconos en el escritorio, por lo que puede que necesiten de nautilus para eso.

Por ahora yo me quedo con nautilus, sería bueno que dijeras que otras cosas le hacen falta para ver si te podemos ayudar y que no extrañes más al explorer.[/I]

---

### Post by caparral on 2008-08-11
> **javier-2714 said:**
> Perdón tiene razón faktorqm se escribe xfce y lo único contrario es no trae para navegar por la red si se puede poner el árbol igual es una opción para navegar por los archivos mas usados yo lo uso y es mucho mas ágil que nautilus es mucho mas completo pero es cuestión de gustos saludos.

*Me agrada el paquete de iconos que tienes aplicado en tu explorador, ¿Habría la posibilidad de que me lo pasaras javier?*

---

### Post by javier-2714 on 2008-08-11
Lo baje de : [http://www.gnome-look.org/index.php?xsortmode=down&page=0&xcontentmode=100](http://www.gnome-look.org/index.php?xsortmode=down&page=0&xcontentmode=100)

Los bordes de la ventana :  LiNsta-Black-plastic
Iconos                   :  Aero
Controles                :  LiNsta-GTK2

Si no encontras te los paso por acá voy a probar el pcman no lo conocía saludos.

---

### Post by caparral on 2008-08-11
*Te agradezco tu amabilidad Javier, de hecho me he pasado por esa web y de ahí me descargué el paquete de iconos que actualmente uso pero no ví como el tuyo, no terminé de ver todos los paquetes por flojera xD, cambiando de tema, he leído Pcman File Manager y dicen que es muy buen explorador, el único inconveniente que tendría sería la falta de visualización previa de imágenes y pdf's (los odf's los desconozco la verdad xD) como dice el post de arriba, por lo demás se ve excelente, prácticamente igual a Nautilus, pero mucho más eficiente.*

---

