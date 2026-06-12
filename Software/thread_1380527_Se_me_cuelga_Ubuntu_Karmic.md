---
title: "Se me cuelga Ubuntu Karmic"
date: 2010-01-13
forum: Software
---

### Post by matias_tati on 2010-01-13
Hola! La cosa es asi: Uso Inkscape un programa para dibujar en la pc nunca me habia dado problemas pero estos ultimos dias se me cuelga siempre y he perdido partes de mi trabajo, es muy frustrante.
La version es la de los repositorios 0.47
Tengo una Dual core 2G
Con 1G de RAM
Uso compiz pero cuando lo desactivo el resultado es el mismo.
Ademas escucho un ruido en mi CPU como que le cuesta trabajo.
Solo cuando uso Inkscape se me cuelga, sera un problema de RAM o de CPU?
Gracias!!

---

### Post by guillermolisi on 2010-01-14
> **matias_tati said:**
> Hola! La cosa es asi: Uso Inkscape un programa para dibujar en la pc nunca me habia dado problemas pero estos ultimos dias se me cuelga siempre y he perdido partes de mi trabajo, es muy frustrante.
La version es la de los repositorios 0.47
Tengo una Dual core 2G
Con 1G de RAM
Uso compiz pero cuando lo desactivo el resultado es el mismo.
Ademas escucho un ruido en mi CPU como que le cuesta trabajo.
Solo cuando uso Inkscape se me cuelga, sera un problema de RAM o de CPU?
Gracias!!
Cuando se "cuelga" tampoco podes pasar a una consola con Ctrl+Alt+F1 ?

Ese ruido que mencionas podria ser el ventilador de la CPU que se va al maximo de vueltas porque el procesador esta sobreexigido y levanta temperatura. Esto podria deberse a algun proceso que consume el 100% de CPU de ambos nucleos.

Cuando hace calor se evidencia problemas de ventilacion: Fuentes con circulacion de aire defectuosa por suciedad acumulada, mala ventilacion del gabinete tambien por suciedad acumulada en el disipador de la CPU, falta de ventiladores adecuados, ventiladores que giran mas lentos porque estan llegando al final de su ciclo de vida, etc.

Tenes monitores de temperatura en el conky que usas ? Que te dicen ?
Si incluiste monitoreo de uso de CPU, que valores acusa ?
Que placa de video estas usando ?

Si vas a limpiar el interior de la PC, nada como aire comprimido. La aspiradora no llega a remover acumulacion de polvo y hollin en ciertos lugares criticos.

---

### Post by matias_tati on 2010-01-14
Cuando se cuelga no me deja hacer nada y en ocaciones se reinicia la sesion y no tengo conky monitoreando la temp los voy a poner a ver que pasa y posteo los resultados. Mi placa es una geforce 8400. Gracias...

---

### Post by matias_tati on 2010-01-14
> **guillermolisi said:**
> Cuando se "cuelga" tampoco podes pasar a una consola con Ctrl+Alt+F1 ?

Ese ruido que mencionas podria ser el ventilador de la CPU que se va al maximo de vueltas porque el procesador esta sobreexigido y levanta temperatura. Esto podria deberse a algun proceso que consume el 100% de CPU de ambos nucleos.

Cuando hace calor se evidencia problemas de ventilacion: Fuentes con circulacion de aire defectuosa por suciedad acumulada, mala ventilacion del gabinete tambien por suciedad acumulada en el disipador de la CPU, falta de ventiladores adecuados, ventiladores que giran mas lentos porque estan llegando al final de su ciclo de vida, etc.

Tenes monitores de temperatura en el conky que usas ? Que te dicen ?
Si incluiste monitoreo de uso de CPU, que valores acusa ?
Que placa de video estas usando ?

Si vas a limpiar el interior de la PC, nada como aire comprimido. La aspiradora no llega a remover acumulacion de polvo y hollin en ciertos lugares criticos.

EDITO: Aca dejo una captura mientras estoy usando el programa me llama poderosamente la atenmcion que el proceso xorg me consuma casi la mitad de la RAM en cuanto a las temperaturas no se si seran normales. Bueno ahi estan mas datos.

[[img]http://g.imagehost.org/t/0854/Pantallazo.jpg[/img]](http://g.imagehost.org/view/0854/Pantallazo)

---

### Post by guillermolisi on 2010-01-14
> **matias_tati said:**
> EDITO: Aca dejo una captura mientras estoy usando el programa me llama poderosamente la atenmcion que el proceso xorg me consuma casi la mitad de la RAM en cuanto a las temperaturas no se si seran normales. Bueno ahi estan mas datos.

[[IMG]http://g.imagehost.org/t/0854/Pantallazo.jpg[/IMG]]("http://g.imagehost.org/view/0854/Pantallazo")
Las temperaturas de ambos nucleos me parecen algo elevadas considerando que usas procesador Intel.
Coincido con vos en que el consumo de procesador por parte del X server es alto y si esa lectura es permanente, algo malo esta pasando.

Para mi, valores normales podrian ser 55/60º para el procesador para verano y si el ambiente no esta refrigerado y alrededor del 5/7% (como mucho) de CPU para el X-Server.

---

### Post by matias_tati on 2010-01-14
> **guillermolisi said:**
> Las temperaturas de ambos nucleos me parecen algo elevadas considerando que usas procesador Intel.
Coincido con vos en que el consumo de procesador por parte del X server es alto y si esa lectura es permanente, algo malo esta pasando.

Para mi, valores normales podrian ser 55/60º para el procesador para verano y si el ambiente no esta refrigerado y alrededor del 5/7% (como mucho) de CPU para el X-Server.
Y entonces que hago?

---

### Post by matias_tati on 2010-01-14
Note que con Gimp pasa lo mismo una vez que lo abro y empiezo a trabajar el xorg empieza a subir hasta que se come toda la RAM cuando lo cierro, tanto Gimp comp Inkscape la RAM queda en unos 30% como mucho, el xorg llega hasta los 70 y monedas mas o menos.
Para que sirve el xorg????

---

### Post by guillermolisi on 2010-01-14
> **matias_tati said:**
> Note que con Gimp pasa lo mismo una vez que lo abro y empiezo a trabajar el xorg empieza a subir hasta que se come toda la RAM cuando lo cierro, tanto Gimp comp Inkscape la RAM queda en unos 30% como mucho, el xorg llega hasta los 70 y monedas mas o menos.
Para que sirve el xorg????
El Xorg es el servidor X, la base que permite funcionar los escritorios graficos como Gnome y KDE, entre otros. Si deshabilitas/removes Gnome (o el que estes usando) te queda una interface grafica dura, aspera. Eso es la interface X (X11 para ser mas precisos).

---

### Post by matias_tati on 2010-01-14
> **guillermolisi said:**
> El Xorg es el servidor X, la base que permite funcionar los escritorios graficos como Gnome y KDE, entre otros. Si deshabilitas/removes Gnome (o el que estes usando) te queda una interface grafica dura, aspera. Eso es la interface X (X11 para ser mas precisos).

Y entonces que debo hacer Guille?

---

### Post by guillermolisi on 2010-01-14
> **matias_tati said:**
> Y entonces que debo hacer Guille?
Si tuviera en claro por donde viene el problema ya te hubiera tirado una sugerencia.

Si estuviera en tu lugar, lo primero que haria es llevar a cabo todo ese proceso de limpieza y revision del hardware, como para que no juegue mas en este asunto.

Luego, me llama mucho la atencion que con la placa de video que usas el servidor X se dispare consumiendo mas CPU de lo que deberia cuando inicias los programas que mencionaste.

Si no usas esos programas, en que porcentaje de uso de CPU se mueve Xorg ?
Cuando no usas esos programas, que temperaturas de CPU lees ?

---

### Post by matias_tati on 2010-01-14
> **guillermolisi said:**
> Si tuviera en claro por donde viene el problema ya te hubiera tirado una sugerencia.

Si estuviera en tu lugar, lo primero que haria es llevar a cabo todo ese proceso de limpieza y revision del hardware, como para que no juegue mas en este asunto.

Luego, me llama mucho la atencion que con la placa de video que usas el servidor X se dispare consumiendo mas CPU de lo que deberia cuando inicias los programas que mencionaste.

Si no usas esos programas, en que porcentaje de uso de CPU se mueve Xorg ?
Cuando no usas esos programas, que temperaturas de CPU lees ?

Las temperaturas son las mismas pero el Xorg baja notablemente ahora por ej esta en 3.43 contra 70 y pico que me tira cuando abro GIMP o Inkscape (pero va subiendo gradualmente).
Voy a googleaer un poco y traigo info para que la revisemos todos a ver si asi nos orientamos. Gracias.

---

### Post by matias_tati on 2010-01-15
Aca encontre algo parecido pero no manejo tan bien el ingles.

[https://bugs.launchpad.net/ubuntu/+source/gimp/+bug/436506](https://bugs.launchpad.net/ubuntu/+source/gimp/+bug/436506)

---

### Post by guillermolisi on 2010-01-15
> **matias_tati said:**
> Aca encontre algo parecido pero no manejo tan bien el ingles.

[https://bugs.launchpad.net/ubuntu/+source/gimp/+bug/436506](https://bugs.launchpad.net/ubuntu/+source/gimp/+bug/436506)
> [Bryce Harrington]("https://launchpad.net/%7Ebryceharrington")             wrote             on 2009-10-29:                                                             [ #2]("https://bugs.launchpad.net/ubuntu/+source/gimp/+bug/436506/comments/2")                                                        X is a server which responds to client requests. If the client is posting a lot of requests it will drive up the CPU usage on X; this is not an X bug but rather an issue in whatever client application is driving X too hard. In this case, GIMP or one of its libraries most likely. For assistance in troubleshooting issues with high CPU loads for X, see this troubleshooting guide: [http://wiki.ubuntu.com/X/Troubleshooting/HighCPU](http://wiki.ubuntu.com/X/Troubleshooting/HighCPU)

        
                                       Changed in gimp (Ubuntu):                                  **status**:                       Confirmed &#8594; New       
Traduccion:
X es un servidor que responde a los requerimientos del cliente. Si el cliente coloca un monton de ellos elevara la utilizacion de la CPU por parte de X; esto no es un bug de X sino que es un tema relacionado con el uso extremo de X por parte de la aplicacion. En este caso GIMP o una de sus librerias mas apropiadamente. Por asistencia en resolucion de temas de alta carga de CPU por parte de X, ver esta guia de resolucion [http://wiki.ubuntu.com/X/Troubleshooting/HighCPU](http://wiki.ubuntu.com/X/Troubleshooting/HighCPU)

Al pie el status del bug indica que se lo clasifico como confirmado pero para Gimp.

---

### Post by matias_tati on 2010-01-15
Estoy perdido
Tengo que solucionar esto si o si. Son vitales estos dos programas para mi.

---

### Post by matias_tati on 2010-01-15
No se puede cambiar por una version anterior? Recuerdo que hace poco se actualizo. Y creo que ahi vinieron los problemas. Como se que version de xorg tengo?

---

### Post by matias_tati on 2010-01-15
Encontre esto.
[http://www.forosuse.org/forosuse/showthread.php?t=12794](http://www.forosuse.org/forosuse/showthread.php?t=12794)
Vendra por ahi la mano?

---

### Post by guillermolisi on 2010-01-15
> **matias_tati said:**
> Encontre esto.
[http://www.forosuse.org/forosuse/showthread.php?t=12794](http://www.forosuse.org/forosuse/showthread.php?t=12794)
Vendra por ahi la mano?
Ese thread es algo viejo.

La version de Xorg que estoy usando en las dos PCs que habitualmente utilizo con Kubuntu KK pareceria ser la 7.4. Digo pareceria porque lo que hice fue fijarme en la version instalada a traves de Synaptic.

---

### Post by matias_tati on 2010-01-15
> **guillermolisi said:**
> Ese thread es algo viejo.

La version de Xorg que estoy usando en las dos PCs que habitualmente utilizo con Kubuntu KK pareceria ser la 7.4. Digo pareceria porque lo que hice fue fijarme en la version instalada a traves de Synaptic.

Si yo tambien tengo esa version, no puede ser que me pase esto...necesito imperiosamente usar estos dos programas.

---

### Post by guillermolisi on 2010-01-16
> **matias_tati said:**
> Si yo tambien tengo esa version, no puede ser que me pase esto...necesito imperiosamente usar estos dos programas.
Matias, igualmente me parece que tenes mas de un tema para resolver.

Que el procesador se caliente hasta los 74/75° me parece mucho considerando la marca y modelo que usas. Aun con trabajos de CPU intensivos no deberia pasar de los 60/65°.
Tambien seria interesante saber a que temperatura llega la GPU de tu placa de video, que por mas que este refrigerada por liquido, puede tambien ser la causa de ese congelamiento general.

---

### Post by matias_tati on 2010-01-16
> **guillermolisi said:**
> Matias, igualmente me parece que tenes mas de un tema para resolver.

Que el procesador se caliente hasta los 74/75° me parece mucho considerando la marca y modelo que usas. Aun con trabajos de CPU intensivos no deberia pasar de los 60/65°.
Tambien seria interesante saber a que temperatura llega la GPU de tu placa de video, que por mas que este refrigerada por liquido, puede tambien ser la causa de ese congelamiento general.

Hola, en este momento estoy en ventanas e instale GIMP e Inkscape, tengo los dos programas abiertos y todo marcha de diez incluso tengo mas programas abiertos. Asi que no creo que sea por la temp del CPU.

---

### Post by guillermolisi on 2010-01-16
> **matias_tati said:**
> Hola, en este momento estoy en ventanas e instale GIMP e Inkscape, tengo los dos programas abiertos y todo marcha de diez incluso tengo mas programas abiertos. Asi que no creo que sea por la temp del CPU.
No es una comparacion valida porque cambiaste totalmente el entorno operativo y el hardware se comporta diferente.

Anyway, que temperaturas tenes usando Windows con y sin esos programas ?

---

### Post by Mauro22 on 2010-01-16
Vengo medio enganchado del tema...


Pero cuelgue con temperatura no van de la mano...

Si hay calor, se reinicia o se apaga... Si algo deja de andar, se cuelga.

---

### Post by matias_tati on 2010-01-18
> **guillermolisi said:**
> No es una comparacion valida porque cambiaste totalmente el entorno operativo y el hardware se comporta diferente.

Anyway, que temperaturas tenes usando Windows con y sin esos programas ?

[[img]http://f.imagehost.org/t/0171/sshot-1.jpg[/img]](http://f.imagehost.org/view/0171/sshot-1)

Con los programas abiertos o sin ellos son las mismas temperaturas.

---

### Post by guillermolisi on 2010-01-18
> **matias_tati said:**
> [[IMG]http://f.imagehost.org/t/0171/sshot-1.jpg[/IMG]]("http://f.imagehost.org/view/0171/sshot-1")

Con los programas abiertos o sin ellos son las mismas temperaturas.
Ok. Entonces el tema se circunscribe a software en Ubuntu, lamentablemente.

---

### Post by matias_tati on 2010-01-18
> **guillermolisi said:**
> Ok. Entonces el tema se circunscribe a software en Ubuntu, lamentablemente.
Esperare alguna actualizacion o no se que mas hacer mientras tanto tendre que usar al tio Bill

---

### Post by LuisMiguel85 on 2010-05-24
POR QUE? alguien podria darme una solucion por favor!
la verdad no entiendo, y despues de tantas visitas a San google me he fijado que es un problema que le ha surgido a muchos pero en ningun foro dan la solucion.
espero que ustedes me ayuden... Gracias     [IMG]http://foro.powers.cl/images/smilies/icon_neutral.gif[/IMG]

---

### Post by kornykyano on 2010-05-25
Ese problema que tenes se debe exclusivamente al driver nvidia, lamentablemente es así, a mi ocurre exactamente los mismo aunque me da tiempo para guardar y si son imágenes grandes es peor. Como es un programa que no uso habitualmente no me preocupa y no me preocupe mucho. También me ha ocurrido con Skype aunque no me ha pasado con Gimp. Actualmente uso Ubuntu 8.04.4 y la versión de driver nvidia es 162.12. Quizás habría que probar instalando la última versión desde la pagina oficial o desactivandolo, pero no lo he probado dado que no uso esos programas. Otra hipótesis que tengo es que la RAM sea muy poca (yo tbn tengo 1 GB). Habria que probar y consultar al foro de nvidia.

Saludos

---

