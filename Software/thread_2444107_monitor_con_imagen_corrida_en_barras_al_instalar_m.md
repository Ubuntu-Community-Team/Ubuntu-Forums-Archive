---
title: "monitor con imagen corrida en barras al instalar mate en ubuntu 20.04"
date: 2020-05-24
forum: Software
---

### Post by rmorales-sanjuan on 2020-05-24
hola, espero estar en el foro correcto y plantear la pregunta de modo que puedan ayudarme.

instalé ubuntu 20.04 en un equipo nuevo, con doble monitor.

googleando, encontré instrucciones variadas para instalar el entorno mate.

luego de instalar, en todos los casos, los monitores quedan con la imagen cortada en franjas horizontales, corridas hacia la derecha, una debajo de la otra, formando una escalera.

el cursor lo tema en la posición correcta, incluso mostrando la imagen corrida.

para salir, voy bajando el cursor con el mouse, viendo como cambia la imagen corrida, hasta ir marcando las opciones para apagar o reiniciar.

me siento mas cómodo con el entorno mate, aunque sea mas rudimentario, por varias opciones que tiene, y no encuentro o son incómodas en el que trae ubuntu.

supongo que podria usar mint, pero prefiero ubuntu, al que estoy regresando, con este equipo.

hice una captura de pantalla, pero no se ve el problema, ya que aparece como si estuviera bien.

saqué una foto de la pantalla, en la que si se nota el problema.

[ATTACH=CONFIG]286003[/ATTACH]

espero explicarme, y me dejen saber qué información adicional puede servir para ayudarme.

gracias desde ya, saludos cordiales, desde san juan, argentina :)

---

### Post by CelticWarrior on 2020-05-25
Bienvenido.

Por favor indicanos las especificaciones de hardware, particularmente la gráfica.

---

### Post by rmorales-sanjuan on 2020-05-25
Hola [**[COLOR=#000000]CelticWarrior:[/COLOR]**]("https://ubuntuforums.org/member.php?u=1826209")      

Procesador: AMD Ryzen 5 2400G with Radeon Vega Graphics × 8
Gráficos: AMD RAVEN (DRM 3.35.0, 5.4.0-31-generic, LLVM 9.0.1)

Es lo que indica el monitor de sistema.

Comento que, probando, se me ocurrió intentar cambios de resolución, y parece que, en el segundo monitor, la primera resolución da problemas (en Mate), pero la segunda funciona.

Con eso se ve bien, pero en menor resolución, y no lo termino de dar por resuelto, aunque si un avance, ya que al menos puedo usarlo.

El primer monitor es de mejor calidad y capacidad, conectado por HDMI, y permite:
**1920 x 1080**, 1680 x 1050, 1600 x 900, 1280 x 1024, ... y sigue, son 15 en total.

El segundo monitor es de menor calidad y capacidad, conectado por VGA, y permite:
1680 x 1050, **1280 x 1024**, ... y sigue, son 12 en total.

Resalto la resolución que está funcionando. Con el entorno original de Ubuntu, funcionan todas.

Gracias :)

---

### Post by CelticWarrior on 2020-05-25
En general la resolución a usar es la nativa del monitor y apenas esa. Pero también es verdad que múltiplos monitores complican esa regla. Es decir, depende siempre de se el entorno es extendido o en espejo y también depende de los controladores de la gráfica y de como esta funciona con dos o más monitores conectados. Además la vieja conexión analógica aún complica más pues frecuentemente el sistema no detecta su resolución ideal correctamente.

Personalmente tengo cero experiencia con gráficas AMD.

---

### Post by rmorales-sanjuan on 2020-05-25
eso pensaba, pero funciona con el otro entorno, por eso mi duda. gracias.

dejaré abierto unos pocos días mas, por si surge algún aporte para resolver ese detalle, antes de cerrar, dando por resuelto, aunque quede eso pendiente. :)

---

