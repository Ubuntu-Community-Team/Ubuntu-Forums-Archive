---
title: "Silent Hill 2 en WIne"
date: 2009-06-17
forum: Software
---

### Post by Psycopatologic on 2009-06-17
Les cuento amigazos, de aburrido de estudiar anoche instale Silent Hill 2 mediante Wine y el resultado fue la imagen que muestro aqui.

[IMG]http://img197.imageshack.us/i/screenshot1b.png/[/IMG][[IMG]http://img197.imageshack.us/img197/4876/screenshot1b.png[/IMG]]("http://img197.imageshack.us/i/screenshot1b.png/")


Trate activando y desactivando opciones de video en el juego y en la configuracion de wine. El juego corre excelente hasta el video de la introduccion pero al iniciar se ve asi. Probe en resoluciones desde 600x480 hacia arriba y ningun resultado. Este bug no esta documentado en los "known issues de wine" y con project64 me pasaba lo mismo pero para wine existe un plugin de video que funciona de maravilla.

Existira una cfg especial para wine al correr estos juegos? algun driver en especial?...que puede estar ocacionando este bug?

Mi hardware es un Athlon 64 3000+, 1.5 Gb DDR PC3200, Nvidia GeForce 5200 256mb DDR y monitor Samsung SyncMaster 940BW a 1400x900 (50Hz), uso wine 1.0 y Ubuntu Hardy 64 bits con los drivers de video libres.

De antemano gracias.

PD:  Al actualizar wine a 1.0.1 hay conflictos con los exe, estare viendo eso.

---

### Post by zhelo on 2009-06-17
has probado con otrosd juegos que es lo que pasa??
puede que no te corra el juego por la targeta de video

---

### Post by Psycopatologic on 2009-06-17
Ya termine ese juego en windows...el problema es en Ubuntu

---

### Post by zhelo on 2009-06-17
toma en cuenta que estas motando un juego en un emulador de windows en un sistema operativo que es ubuntu... ubuntu chupa memoria grafica no meparece extraño que te corra mal en wine... prueba un juego mas liviano que pida menos memoria grafica y dime que onda... o baja la resolucion al minimo al silent hill2

---

### Post by moreback on 2009-06-18
> **zhelo said:**
> toma en cuenta que estas motando un juego en un emulador de windows en un sistema operativo que es ubuntu... ubuntu chupa memoria grafica no meparece extraño que te corra mal en wine... prueba un juego mas liviano que pida menos memoria grafica y dime que onda... o baja la resolucion al minimo al silent hill2

1. Wine no es un emulador, son bibliotecas desarrolladas para correr aplicaciones win32 en Linux.

2. Corre mal porque ese juego está programado y optimizado para ejecutarse en Windows, me temo que usando bibliotecas cerradas como DirectX desarrolladas por la misma Microsoft, por lo que no extraña que se ejecute con problemas bajo Wine.

3. Me gustaría que te informaras más ya que con suposiciones vagas no ayudas mucho al resto.

Gracias.

---

### Post by Carlos C on 2009-06-18
No conozco el juego así que no tengo claro cuál es el problema. ¿Es que no tienes una resolución adecuada? Perdón por preguntar algo tan básico, pero es que nunca lo he jugado.

---

### Post by zhelo on 2009-06-19
descarga virtual box, ahi te instalas windows xp y juegas de lujo y sin dramas

---

### Post by CdK1 on 2009-06-19
Usa la última version de wine, agrega esto a tus repos;

deb [http://www.lamaresh.net/apt](http://www.lamaresh.net/apt) sid main

---

### Post by Psycopatologic on 2009-06-19
mmm...me dice que esta offline ese software source amigo cdk1.

e instalar windows en virtualbox. prefiero igual destinar unos 10 mb a una particion con windows y me ahorro problemas de compatibilidad y otros dilemas que puedan surgir. igual gracias por la idea.

probare con la ultima version de wine, si no, no importa...jajaja

---

### Post by kuboode on 2011-08-13
Me parece problema de directx, un poco tarde no? jajaja, bueno la noticia te va interesar, existe una nueva version llamada Dx Wine donde instala y ejecuta correctamente directx, sin tanta configuracion solo instala y listo, podes bajarlo en los siguientes links:

[http://kuboosoft.blogspot.com/](http://kuboosoft.blogspot.com/)

o

[http://www.taringa.net/posts/linux/1...-VERSION_.html](http://www.taringa.net/posts/linux/1...-VERSION_.html)

¿Quieren ayudar? pues necesita mas servidores donde subir, ya que tiene un gran congestionamiento del programa, si lo subes enviale el link para incluirlo como mirrors...

---

### Post by c3959 on 2011-08-25
kuboode... como que este hilo era de hace dos años (junio,2009)



Saludos

---

