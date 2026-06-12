---
title: "[SOLUCIONADO]ubuntu 9.04 no me detecta audio via VT1708/A"
date: 2009-08-16
forum: Software
---

### Post by davo0 on 2009-08-16
movi el driver de mi tarjeta de audio y ahora ya no funciona
mi tarjeta de audio es VIA Technologies, Inc. VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller) (rev 10)
bueno ubuntu si me la detectaba en un principio pero siempre tenia pequeños fallos aveces el sonido se paraba de la nada y otras veces se reproducia un sonido extraño y molesto, y se entrecortaba el audio cuando por ejemplo minimizaba o maximizaba el firefox(sin estar viendo una pagina con flash) entonses investigue y resulta que el problema era de pulseaudio
el punto es que hize tantas tonterias que al final me baje el driver de la pagina de via pero parece que solo es para ubuntu 7.04 que no incluye el driver ya estube googleando y todo pero nada me resuelve el problema
quiero saber si hay algun modo de regresar al driver por defecto es decir el que ubuntu instala ya que ese funcionaba aunque con algunos errores pero era por el pulseaudio ya que, lo cambie a alsa y funcionaba perfectamente a exepcion que no reproducia audio de youtube
ahora entro a la configuracion de sonido y no me sale ningun hadware y el icono del altavoz le aparece una tacha como si estubiera en mudo pero cuando le doy click apararece un error de que no encontro ningun dispositivo que encontrar.
espero me puedan ayudar
que ya me desespere llevo mas de medio dia probando soluciones y nada
por eso recurro a lo ultimo que me gusta usar: el foro 
saludos

---

### Post by davo0 on 2009-08-16
bien pues ya resolvi mi problema por si alguien tiene el mismo problema
lo que hize fue volver al kernel 28.13 ya que tenia el 28.14
aunque no me dejo instalado el pulseaudio pero mejor ya que por lo visto solo sabe causar problemas ahora mi sonido trabaja con alsa y va a la perfeccion ya no se corta el audio al maximizar el firefox.
me parece mas un remedio que una solucion puesto que ahora si inicio en la 28.14 no me detecta audio pero personalmente creo que la 28.14 me causaba otros problemas.
espero y la comunidad mejore el pulseaudio y tambien el flash si se solucionarian esos problemas yo creo que todos se pasarian a linux a pesar de ser un poco mas dificil de manejar es el mejor s.o

---

