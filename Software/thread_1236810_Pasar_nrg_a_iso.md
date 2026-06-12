---
title: "Pasar nrg a iso"
date: 2009-08-10
forum: Software
---

### Post by harryscode on 2009-08-10
Hola, baje unos archivos rar que terminaron por darme un archivo .nrg Estuve buscando info y encontré el nrg2iso. Lo instalé a traves de Synaptic y lo hice correr en un terminal. El problema es que cuando le daba la orden para cambiar a iso (nrg2iso xxx xxx.nrg xxx xxx.iso) salia la descripción del programa y ahi quedaba la cosa.. No cambiaba nada. Cambié el nombre del archivo pensando que como tiene espacio entre dos palabras, y lo mismo. Hasta que en un momento me puso que el archivo ya se habia cambiado a .iso, pero en las propiedades del mismo no se habia cambiado nada. Quise probar con brasero para grabarlo y tampoco lo reconoció como .iso. Pregunta... sirve el nrg2iso?.. Hay otro soft para hacer ese cambio?. Gracias por la ayuda.

---

### Post by staar on 2009-08-10
buscá por el foro que hace no mucho alguien tuvo tu mismo problema y logró solucionarlo (creo que con otro programa similar que también estaba en los repos)

saludos

---

### Post by guillermolisi on 2009-08-10
> **harryscode said:**
> Hola, baje unos archivos rar que terminaron por darme un archivo .nrg Estuve buscando info y encontré el nrg2iso. Lo instalé a traves de Synaptic y lo hice correr en un terminal. El problema es que cuando le daba la orden para cambiar a iso (nrg2iso xxx xxx.nrg xxx xxx.iso) salia la descripción del programa y ahi quedaba la cosa.. No cambiaba nada. Cambié el nombre del archivo pensando que como tiene espacio entre dos palabras, y lo mismo. Hasta que en un momento me puso que el archivo ya se habia cambiado a .iso, pero en las propiedades del mismo no se habia cambiado nada. Quise probar con brasero para grabarlo y tampoco lo reconoció como .iso. Pregunta... sirve el nrg2iso?.. Hay otro soft para hacer ese cambio?. Gracias por la ayuda.
Podrias exponer literalmente la linea de comando que usaste ?

Los espacios en una linea de comando son significativos en Linux, separan argumentos en una lista. Por lo cual si usas xxx xxx.nrg el interprete de comandos (shell) intentara leer el primer argumento xxx y tomara xxx.nrg como el destino.

---

### Post by harryscode on 2009-08-11
Gracias por las respuestas... Si, después de tanto leer, aprendí que los espacios son importantes. La línea de comando textual era "nrg2iso Piñon Fijo.nrg Piñon Fijo.iso". Después de renegar bastante cambie el nombre del archivo por pinon.nrg pero me siguio tirando lo mismo, la descripcion del programa, desarrollador y versión. Después no se que hice de raro pero empezó a decir que el archivo .nrg parecia que ya tenia formato ISO9660. Intenté montarlo pero me tira que el archivo no existe. 
Gracias.

---

### Post by guillermolisi on 2009-08-11
> **harryscode said:**
> Gracias por las respuestas... Si, después de tanto leer, aprendí que los espacios son importantes. La línea de comando textual era "nrg2iso Piñon Fijo.nrg Piñon Fijo.iso". Después de renegar bastante cambie el nombre del archivo por pinon.nrg pero me siguio tirando lo mismo, la descripcion del programa, desarrollador y versión. Después no se que hice de raro pero empezó a decir que el archivo .nrg parecia que ya tenia formato ISO9660. Intenté montarlo pero me tira que el archivo no existe. 
Gracias.
Es que el parsing de "Piñon Fijo.nrg" resulta en un primer argumento "Piñon" y otro segundo "Fijo.nrg".

A eso me referia con lo de los espacios.

Proba con piñon_fijo.nrg o piñonfijo.nrg, tanto en el argumento del archivo de entrada como en el de salida del comando (adecuando el sufijo a .iso para este ultimo).

---

### Post by harryscode on 2009-08-11
Gracias Guillermo. Intenté ayer lo que me pusiste, con minúsculas, sin espacio, una palabra sola, en fin, y no obtuve resultados. Hoy voy a ponerme con paciencia de nuevo a ver que es lo que estaba haciendo mal y les comento que tal me va.

---

### Post by Mister X on 2009-08-11
Hola, linux es sensible a mayúsculas o sea que debes respetar exactamente el nombre del archivo, si tenes espacios en blanco debes usar un caracter de escape que es la barra invertida, o bien encerrar el nombre de archivo entre comillas ej:
```
Piñon Fijo.nrg

nrg2iso Piñon\ Fijo.nrg Piñon\ Fijo.iso

o

nrg2iso "Piñon Fijo.nrg" "Piñon Fijo.iso"
```

---

### Post by EnriqueK on 2009-08-11
Probá usando "AcetoneISO", lo podés descargar de la página de GetDeb [http://www.getdeb.net/](http://www.getdeb.net/)

---

### Post by guillermolisi on 2009-08-11
> **harryscode said:**
> Gracias Guillermo. Intenté ayer lo que me pusiste, con minúsculas, sin espacio, una palabra sola, en fin, y no obtuve resultados. Hoy voy a ponerme con paciencia de nuevo a ver que es lo que estaba haciendo mal y les comento que tal me va.
Algo que no comente porque me parecio obvio es que el nombre que uses para los archivos en la linea de comando debe coincidir con los nombres reales de los archivos, el .nrg, basicamente.

Ademas, Linux hace diferencia entre minusculas y mayusculas, es decir son significativas.

---

### Post by alfplayer on 2009-08-11
Si el programa crea un archivo nuevo (el .iso), puede tardar varios minutos en terminar, y tarda más cuanto más grande es el tamaño del archivo .nrg

---

