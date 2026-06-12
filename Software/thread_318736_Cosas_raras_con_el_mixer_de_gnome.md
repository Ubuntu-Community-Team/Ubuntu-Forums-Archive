---
title: "Cosas raras con el mixer de gnome"
date: 2006-12-14
forum: Software
---

### Post by oberonking on 2006-12-14
La cosa va más o menos así, el volumen master no administra el volumen general de mi placa (Soundmax integrada a un Mother Intel) la toma como I810. :confused: 
Ahora lo raro lo que si me maneja el volumen es el headphones... pueden creerlo
Jamas encontré solución a esto, alguno puede echar un cable a tierra
No es que me saque el sueño, pero me tiene intrigado ](*,) 
Gracias de antemano ;)

---

### Post by spg76 on 2006-12-14
Podes probar lo siguiente. Hacé click derecho en el icono de volumen, anda "Preferencias", ahí podes elegir el dispostivo de sonido y que canal queres que controle.
Espero que te sirva.

---

### Post by oberonking on 2006-12-15
si, eso fue probado, pero nada
Creo que fue lo primero que hice al instalarlo
Gracias por la respuesta ;)

---

### Post by daniminas on 2006-12-16
y una cosa rara que me sucede a mi es que pongo al palo el mixer de ubuntu (y los parlantes) y siempre el sonido resultante es menor a que si pusiese todo al palo en Guindous,, :confused:

---

### Post by felipelerena on 2006-12-16
ajustalo en la configuracion grafica, escribiendo
```
alsa-mixer
```
y pone todo al palo.

Es un bug muy muy muy comun. le pasa a todo el mundo

---

### Post by daniminas on 2006-12-16
Gracias :D... ahora si me gusta!... :cool:

---

### Post by godzeus on 2007-01-17
a alguien le paso que a veces, el audio directamente no carga,o noemite sonido hasta reiniciar, Cosa e´ mandinga..:-k

---

### Post by felipelerena on 2007-01-18
si, a mi me pasa, tengo una placa que si bien es fantastica (creative audigy 2) es reconocida en la net como una placa que esta mas loca que mi tia la que tiene esquizofrenia.

pero me pasa muy de vez en cuando y con sacarla y volverla a poner o moviendo todos los cables para que se mueva la placa se arregla

---

### Post by tzulberti on 2007-01-18
> **godzeus said:**
> a alguien le paso que a veces, el audio directamente no carga,o noemite sonido hasta reiniciar, Cosa e´ mandinga..:-k

Si, a mi tambien me pasa eso....

---

### Post by MeduZa on 2007-01-19
> **felipelerena said:**
> si, a mi me pasa, tengo una placa que si bien es fantastica (creative audigy 2) es reconocida en la net como una placa que esta mas loca que mi tia la que tiene esquizofrenia.

pero me pasa muy de vez en cuando y con sacarla y volverla a poner o moviendo todos los cables para que se mueva la placa se arregla

yo tengo la misma y no me pasa nada raro, anda todo mas que bien, esta placa fue la solucion a lo que le pasa al que creo el 1er post XD es que es verdad es una bosta la que trae onboard y encima me andaba re mal el 5.1

---

### Post by felipelerena on 2007-01-19
> yo tengo la misma y no me pasa nada raro
Yo tengo la audigy 2 ZS una placa que , se sabe en los foros, tiene ese problema. ojo, es una vez cada 6 meses, pero algo jode.
en las nuevas versiones esta arreglado, pero al ser un problema de diseño del hardware no se puede arreglar con el firmware, jejej.

---

### Post by oberonking on 2007-01-19
Por favor si alguien sabe como arreglar mi problema del mixer, lo agradeceria
Refrezco memorias, mi problema es que el master no maneja el volumen si no que es el headphones el que maneja el volumen general del sonido de Ubuntu.....
Imaginen que no puedo bajar el volumen directamente desde el icono del tray, tengo que abrir el mixer y bajar el headphones.... quiciera saber la solucion pero estoy cansado de toquetear y buscar, nada me sirvio ](*,)  ... Espero algun mago de Linux para que me cuente como llegar a buen puerto.

Gracias Hermanos ;)

---

### Post by MeduZa on 2007-01-19
> **felipelerena said:**
> en las nuevas versiones esta arreglado, pero al ser un problema de diseño del hardware no se puede arreglar con el firmware, jejej.

entonces tuve suerte o tuve mas suerte aun y no me toco una de las malas :p 
espero siga asi andando

---

### Post by MeduZa on 2007-01-19
> **oberonking said:**
> Por favor si alguien sabe como arreglar mi problema del mixer, lo agradeceria
Refrezco memorias, mi problema es que el master no maneja el volumen si no que es el headphones el que maneja el volumen general del sonido de Ubuntu.....
Imaginen que no puedo bajar el volumen directamente desde el icono del tray, tengo que abrir el mixer y bajar el headphones.... quiciera saber la solucion pero estoy cansado de toquetear y buscar, nada me sirvio ](*,)  ... Espero algun mago de Linux para que me cuente como llegar a buen puerto.

Gracias Hermanos ;)

osea y ya probaste cambiando el pote de lugar (lo que te dijeron que hagas con el boton derecho sobre el icono del volumen) mmmm
abria q editar el archivo ese q esta en el home/user y poner algo ahi pero ni idea :S sale chequeo del foro de alsa

---

### Post by redboy on 2009-06-04
[FONT=Comic Sans MS][SIZE=3][COLOR=Red]Yo tenía el mismo problema, a mi el control que me funcionaba era el de PCM, en lugar de Master.
Apreta boton derecho sobre el icono del parlante de la barra superior, preferencias.
en el cuadro que te abre marcá el volumen que te funciona como master y aceptar, listo cambiaste tu Master.[/COLOR][/SIZE][/FONT]

---

