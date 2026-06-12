---
title: "Nuevo en Ubuntu"
date: 2009-09-25
forum: Software
---

### Post by ferlz on 2009-09-25
Bueno, acabo de instalar ubuntu, ahora estoy desde el, pero no entiendo nada todavía, se bien que no corren los mismo programas que en window, pero eso no me importa mucho, yo uso la pc mas que nada para navegar, chatear y escuchar musica.
Bueno, tengo un millon de dudas pero para no hacerla tan larga, necesito que alguien me pase un tutorial bien basico de como usar Ubuntu, porq todos los que vi por internet no te explican mucho, por ejemplo: Me descargue el Compiz desde el Gestor de paquetes pero no tengo idea de como ponerlo a andar.
Desde ya muchas gracias.

---

### Post by staar on 2009-09-25
pasate por estos threads (están como sticky en la parte inicial del foro)
[http://ubuntuforums.org/showthread.php?t=1222572]("http://ubuntuforums.org/showthread.php?t=1222572")
[http://ubuntuforums.org/showthread.php?t=1007750]("http://ubuntuforums.org/showthread.php?t=1007750")
pueden serte útiles...

desconozco si hay un tutorial así, bien básico, pero te recomiendo que aprendas como aprendimos la mayoría, con prueba y error, experimentando, creo que es la mejor forma, y de la que quedan más las cosas, siempre tenés el foro (o don google) para las partes en las que te trabes, solo es cuestión de usarlo, y de no rendirse ante el primer problema, a diferencia de Ventanas, la mayoría de los problemas en ubuntu son de fácil resolución por el usuario, y, si no es el caso, se puede reportar el bug y que lo arreglen los desarrolladores...

para compiz específicamente, primero tenés que tener la aceleración 3d de tu placa de video activada y andando. como lograr eso depende de la placa, si es una ati nueva o una nvidia, hay que instalar los drivers privativos (del fabricante), eso se hace desde Sistema > Administración > Controladores de hardware (el SO generalmente te avisa si hay drivers privativos disponibles para tu hard, y te ofrece instalarlos). si la placa es una ati vieja, o una intel, los drivers que ofrecen aceleración 3d son libres y vienen con ubuntu, activados desde el inicio. si la placa es una via o una sis vas muerto, porque dichas placas no tienen drivers con los que funcione la aceleracion 3d (este es un problema del fabricante, que no crea drivers, no de gnu/linux). si tu placa es otra, ya se verá el caso. si no tenés idea que placa tenés, hacé una cosa, andá a Aplicaciones > Accesorios > Terminal y corré el comando ```
lspci
``` este lista los dispositivos que hay en el bus pci de tu pc, y es de mucha ayuda para hacernos una idea del hardware que tiene esa pc, copiá lo que te salga, y pegalo en un mensaje acá, así te podemos indicar que hacer...

compiz en sí, ya viene instalado (activado si tenés una placa con buenos drivers libres) con ubuntu, lo que no viene es el gestor de opciones, que debe ser lo que instalaste desde Synaptic. después de tener aceleración 3d, para activarlo, andá a Sistema > Preferencias > Apariencia > Efectos de escritorio

saludos

---

### Post by juancarlospaco on 2009-09-25
***Bienvenido a la Libertad...***

---

### Post by ferlz on 2009-09-28
Bueno, cuando voy a Sistema>Preferencias>Pantalla, me salta esto:
[IMG]http://img18.imageshack.us/img18/4612/problemita.png[/IMG]

Me parece q se debe a la placa de video, es viejita pero creo que deberia correrlo.

---

### Post by josecuervo86 on 2009-09-28
Hola ferlz, antes que nada, como para tener una mejor idea del hardware de tu maquina abrí una terminal, para lo cual tenes que ir a **Aplicacions** > **Accesorios** > **Terminal**. Una vez en ella tipea lo siguiente:
```
lspci
```
Copia todo el resultado y pegalo aca. Luego vemos como seguimos

---

### Post by ferlz on 2009-09-28
[IMG]http://img12.imageshack.us/img12/9944/pantallazofo.png[/IMG]
[IMG]http://http://img12.imageshack.us/img12/9944/pantallazofo.png[/IMG]

---

### Post by staar on 2009-09-28
el driver privativo de nvidia para linux no es compatible con XRandr, por lo que para modificar las resoluciones se debe usar el NVIDIA X Server Settings, y no la herramienta de ubuntu...

si tenés problemas para poner la resolución que querés, fijate el post al respecto que está como sticky en la sección Hardware...

saludos

---

### Post by josecuervo86 on 2009-09-29
Anda a **Sistema** > **Administración** > **Controladores de Hardware**. Va a tartar de buscar los drivers para tu placa. Una vez que te los muestra, elegí el mas nuevo (número mas alto). Habilitalos (tarda un rato) y reiniciá la maquina.

Despues andá a **Sistema** > **Administración** > **Nvidia X Server settings** y configura la resolución desde ahí.

---

### Post by ferlz on 2009-09-29
Gracias gente, ya lo hice. La verdad que esta bueno Ubuntu, pero siempre cuesta hacer el cambio, voy a ir viendo que onda.

---

