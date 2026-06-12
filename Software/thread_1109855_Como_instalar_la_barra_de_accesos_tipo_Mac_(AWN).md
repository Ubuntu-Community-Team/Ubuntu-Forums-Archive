---
title: "Como instalar la barra de accesos tipo Mac? (AWN)"
date: 2009-03-27
forum: Software
---

### Post by Nikolopulus on 2009-03-27
Soy demasiado nuevo en Ubuntu, pero estoy en vías de solucionarlo, mientras tanto ¿me pueden ayudar a poner la barrita con accesos directos tipo mac y a activar el efecto del cubo para el cambio de escitorios?
Gracias che

---

### Post by staar on 2009-03-27
> **Nikolopulus said:**
> Soy demasiado nuevo en Ubuntu, pero estoy en vías de solucionarlo, mientras tanto ¿me pueden ayudar a poner la barrita con accesos directos tipo mac y a activar el efecto del cubo para el cambio de escitorios?
Gracias che

hola, la barrita 'tipo mac' es un dock ;-), hay varios, pero el más famoso es el Avant Window Navigator (AWN), hay una versión en los repositorios, pero es bastante vieja, últimamente se esta trabajando mucho en ese proyecto (OFF: parece que para la proxima versión, 0.4 va ha haber muchos cambios, y va a poder moverse la barra :-) :-) ) te recomiendo agregar estos repositorios de la versión en desarrollo, en 'Origenes de Software -> Software de terceros'```
deb http://ppa.launchpad.net/awn-testing/ubuntu/ intrepid main
deb-src http://ppa.launchpad.net/awn-testing/ubuntu/ intrepid main
```
e instalar AWN desde ellos: en una terminal ```
sudo aptitude install avant-window-navigator-trunk
```

el efecto del cubo de escritorio requiere que tengas instalados los drivers de tu tarjeta de video y andando la aceleración grafica, despues tenes dos configuradores par compiz, el simple-ccsm ```
sudo aptitude install simple-ccsm
```y el ccsm ```
sudo aptitude install compizconfig-settings-manager
```(uno es más simple que el otro :-P :lolflag:) instala el que te guste, si sos novato te recomiendo el simple, el otro tiene una abrumadora cantidad de opciones (compiz rules! :-P :-D), despues activar el cubo es muy facil :-D...

---

### Post by Nikolopulus on 2009-03-28
Traté de instalar el AWN y la consola me tiró lo siguiente

```
nikolopulus@nikolopulus:~$ sudo aptitude install avant-window-navigator-trunk
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Inicializando el estado de los paquetes... Hecho
Escribiendo información de estado extendido... Hecho
No se pudo encontrar ningún paquete cuyo nombre o descripción coincida con "avant-window-navigator-trunk"
No se pudo encontrar ningún paquete cuyo nombre o descripción coincida con "avant-window-navigator-trunk"
No se instalará, actualizará o eliminará ningún paquete.
0 paquetes actualizados, 0 nuevos instalados, 0 para eliminar y 0 sin actualizar.
Necesito descargar 0B de ficheros. Después de desempaquetar se usarán 0B.
Escribiendo información de estado extendido... Hecho
Leyendo lista de paquetes... Hecho                   
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Leyendo la información de estado extendido      
Inicializando el estado de los paquetes... Hecho
```

El otro lo instalé bien, ahora estoy leyendo una guía para aprender a usarlo. 
Gracias Staar

---

### Post by staar on 2009-03-29
> **Nikolopulus said:**
> Traté de instalar el AWN y la consola me tiró lo siguiente

```
nikolopulus@nikolopulus:~$ sudo aptitude install avant-window-navigator-trunk
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Inicializando el estado de los paquetes... Hecho
Escribiendo información de estado extendido... Hecho
No se pudo encontrar ningún paquete cuyo nombre o descripción coincida con "avant-window-navigator-trunk"
No se pudo encontrar ningún paquete cuyo nombre o descripción coincida con "avant-window-navigator-trunk"
No se instalará, actualizará o eliminará ningún paquete.
0 paquetes actualizados, 0 nuevos instalados, 0 para eliminar y 0 sin actualizar.
Necesito descargar 0B de ficheros. Después de desempaquetar se usarán 0B.
Escribiendo información de estado extendido... Hecho
Leyendo lista de paquetes... Hecho                   
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Leyendo la información de estado extendido      
Inicializando el estado de los paquetes... Hecho
```

El otro lo instalé bien, ahora estoy leyendo una guía para aprender a usarlo. 
Gracias Staar

actualizaste los repositoros? ```
sudo aptitude update
``` sino buscalo en Synaptic e instalalo desde ahi ;-)...

saludos

---

### Post by Hei Ku on 2009-03-29
Puse todo esto en un thread por sí mismo, para que le presten mas atencion y no desvirtuar el otro que es largo ya de por sí.

---

### Post by SLA_leandrin on 2009-03-29
> **Hei Ku said:**
> Puse todo esto en un thread por sí mismo, para que le presten mas atencion y no desvirtuar el otro que es largo ya de por sí.

Hei Ku, cual todo esto pusiste??? :confused:

---

### Post by Hei Ku on 2009-03-29
> **SLA_leandrin said:**
> Hei Ku, cual todo esto pusiste??? :confused:
 Arreglado.

---

### Post by exegeses on 2009-05-09
buenas, paso a preguntar:

como en esta versión de AWN no hay un APPLET "lanzador", me creé un lanzador para el quanta (software para programar). el tema es, cómo cornex lo agrego al dock!!!??
seguro es una pavada, pero no lo encuentro.

desde ya muchas gracias
saludos

P.S.: ah, y ya que estamos, ¿cómo configuro la posición del dock para quye esté unos 10 pixeles sobre la parte inferior del desktop?

---

### Post by Skywalker hack on 2009-05-09
Arrastra hasta el dock ;)

Saludos

---

### Post by staar on 2009-05-09
podés simplemente arrastar el lanzador desde el menú hasta la barra, o sino usar el AWN manager, creo que en Jaunty está por Sistema > Administración...

AWN aún no puede despegarse del borde del escritorio, ni moverse del borde inferior, es una característica que está planeada para la próxima versión (la 0.4, si mal no recuerdo), lo que podés hacer es usar el AWN manager para subir los íconos, pero el fondo se te va a estirar hacia arriba lo necesario...

saludos

---

### Post by exegeses on 2009-05-09
> **Skywalker hack said:**
> Arrastra hasta el dock ;)

Saludos

muchas gracias por la sugerencia, pero luego del vigésimotercer intento decidí que no se podía... :(

> **staar said:**
> podés simplemente arrastar el lanzador desde el menú hasta la barra, o sino usar el AWN manager, creo que en Jaunty está por Sistema > Administración...

AWN aún no puede despegarse del borde del escritorio, ni moverse del borde inferior, es una característica que está planeada para la próxima versión (la 0.4, si mal no recuerdo), lo que podés hacer es usar el AWN manager para subir los íconos, pero el fondo se te va a estirar hacia arriba lo necesario...

saludos
muchas gracias por la sugerencia. 
en el AWN, click derecho y Dock Preferences, eso hace aparecer la configuración sin necesidad de ir a Sistema > Administración...
ya me creé launchers con el menú y se me mueren de risa...

lo de arrastrar, imposible. simplemente no funciona.

he creado un lanzador y los he puesto en /usr/share/avant-window-navigator/applets y tampoco, nada.
he copiado alguno de los applets y modificado parte del código y nada.
simplemente no puedo, seguro es una pavada, pero bueno, no me funciona.
si alguien ha podido crear un icono adicional personalizado en el AWN, me avisa please así le pregunto.

juro que si hubiese un archivo de configuración de los lanzadores donde escribir en xml, sarasaml o loqueseteocurra.py lo sacaba más rápido.

desde ya, muchas gracias

---

### Post by juancarlospaco on 2009-05-10
Mirate Cairo Dock** 2**.
*esta en BerliOS, Googlealo no te vas a arrepentir...*

---

### Post by exegeses on 2009-05-11
> **juancarlospaco said:**
> Mirate Cairo Dock** 2**.
*esta en BerliOS, Googlealo no te vas a arrepentir...*

pinta muy bien, ahora...
sabés cuales son los repositorios para Jaunty?

porque este NO es
deb [http://repository.cairo-dock.org/ubuntu](http://repository.cairo-dock.org/ubuntu) jaunty cairo-dock


bueno, ya lo instalé...
ahora la configuración... por algún motivo me bloquea la posición de los íconos...
ya lo iré sacando
muchas gracias.

---

### Post by emal011 on 2009-06-23
una vez instalado, como lo ejecuto?

---

### Post by santiagoward2000 on 2009-06-23
> **emal011 said:**
> una vez instalado, como lo ejecuto?

Depende de cuál hayas instalado. Sé que el thread es sobre AWN, pero al final se habló un poco sobre Cairo, entonces por las dudas pregunto. En cualquiera de los casos, te tendría que haber creado un lanzador en el menú (para Cairo está en Aplicaciones > Sistema, calculo que AWN debe estar ahí también, pero no me acuerdo).
Si no los encontrás, probá abrir una Terminal y correr **avant-window-navigator** (creo que este era el comando) o **cairo-dock**. Eso tendría que abrirlo.
Saludos!

---

