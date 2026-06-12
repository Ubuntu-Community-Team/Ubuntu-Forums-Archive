---
title: "Presento F.lux un programa que cuida tu vista."
date: 2009-03-08
forum: Software
---

### Post by ubuntu27 on 2009-03-08
[F.lux]("http://stereopsis.com/flux/") o xflux es un programa que cambia la iluminación y la "temperatura del color" (así lo llaman) de acuerdo a tu ubicación y hora.

La idea es que si estamos de noche, no es natural para los ojos que recibamos demasiada iluminación con el monitor, es dañino para los ojos.

Aqui esta la pagina oficial:

[http://stereopsis.com/flux/]("http://stereopsis.com/flux/")

El autor ha creado binarios para GNU/Linux, WIndows, y MacOS X.




Sigue la siguiente instrucciones para instalar en cualquier distribución de Linux:

**1)** Bajar el archivo binario para Linux desde la pagina
[https://secure.herf.org/flux/xflux.tgz]("https://secure.herf.org/flux/xflux.tgz")
[B]
2)[/B] Extraer el archivo descargado

**3)** Mover el archivo extraído al directorio  **/usr/bin**


ya estamos llegando ya. Ahora lo que necesitamos hacer es saber la coordinación (Longitud y latitud) de donde vives. Como dije antes, este programa cambia la iluminación y temperatura del color de acuerdo a tu ubicación y hora. Asi que es necesario decir al programa donde te encuentras.

**4)** Para eso, visita [esta pagina]("http://stereopsis.com/flux/map.html"):
[http://stereopsis.com/flux/map.html]("http://stereopsis.com/flux/map.html")

y escribe donde te encuentras. Por ejemplo: "Santiago, Chile" o "Lima, Peru"
Al presionar enter o click en "Go" te proveerá la coordinación como en caso de Santiago, Chile: "-33.4253599, -70.5664659".

Si desean, puede ser mas preciso como "Lima, Lima, Peru" en vez de "Lima, Peru"

**5)** Bueno, una vez que tengan la coordinación abran El terminal y escriban

```
xflux -l **N, N**
```

Remplazan N, N con el numero que obtuvieron.

LISTO! El programa ya esta corriendo.


Si les han gustado, sigan lo siguiente:
Como hacer para que xflux se ejecute automaticamente al iniciar la computadora en GNOME

**6)** menu Sistemas/Preferencias/Sesiones

**7)** Click en "Agregar"

**8)** En el campo nombre, pongan lo que deseen. Yo le puse "xflux"

**9)** escriban "xflux -l -33.4253599, -70.5664659" (Remplacen con su numero de coordinación) en el campo "Comando"
[B]
10)[/B] Click en agregar


DISFRUTEN!!

---

### Post by Mauro22 on 2009-03-08
mmm...

Interesante se podria decir..


Ahora la pantalla se ve medio rojo :S será normal... ?

```
--------
Welcome to xflux (f.lux for X)
This will only work if you're running X on console.

Your latitude is -34.9

Your night-time color temperature is 3400
It's night time. Your screen is changing now.
Going to background: 'kill 6822' to turn off.

```

Salio eso y se empezo a poner rojo (no rojo rojo, con un tono rojizo)


No jode.. vamos a probar

---

### Post by ubuntu27 on 2009-03-08
Si, es normal que cambie de color asi. 
Te salio rojo? A mi me sale medio rosado...  una mezcla entre rosado y blanco.

Sera porque eres de Argentina. Depende de tu hubicacion (depende del sol)


De cierto, pusiste tu coordinacion (Latitud, longitud)  como mencione en paso 4?

---

### Post by staar on 2009-03-08
lo estoy usando desde hace unas horas y, la verdad, sirve un monton, la vista no se me canso como siempre, y una vez que te acostumbras al color parece hasta más 'natural'...

saludos

---

### Post by rubioo on 2009-03-09
Si, es verdad que se pone medio rojo jej
 Pero no es molesto, hay que probarlo


        Saludos y gracias por el progrma

---

### Post by ubuntu27 on 2009-03-09
Gracias muchachos por probar el programa :d

Yo no soy quien creo el programa pero me da gusto que la gente le guste o intenten usar programas que recomiendo que prueben :D


Asi que les parece natural ahora? ya se acostumbraron?

Como esta su vista? ya no se cansa como antes?

> **staar said:**
> lo estoy usando desde hace unas horas y, la verdad, sirve un monton, la vista no se me canso como siempre, y una vez que te acostumbras al color parece hasta más 'natural'...

saludos

Gracias Staar. Así que ya te acostumbraste :d

---

### Post by leonardo83 on 2009-03-14
a mi me funcioan barbaro hasta el domingo que se hizo el cambio de hora!
Ahora lo ejecuto y no me da bola, no cambia de color ni nada, aparece mi pantalla del mismo color de siempre.
A alguien le paso lo mismo?
Voy a probar instalandolo de neuvo pero no creo que sea la solucion ... en fin, saludos :(

---

### Post by mohave on 2009-11-03
Probándolo con éxito desde Ubuntu 9.10 Karmic Koala
Gacias por la página no lo re-encontraba ;-)

---

