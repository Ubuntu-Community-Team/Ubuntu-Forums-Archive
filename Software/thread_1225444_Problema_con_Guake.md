---
title: "Problema con Guake"
date: 2009-07-28
forum: Software
---

### Post by Fak89 on 2009-07-28
Es la primera vez que me pasa, y no pude encontrar el problema solo.
Resulta que estoy intentando instalar la version 4.0 de Guake pero cuando hago el ./configure me tira el siguiente error.

```
checking for DEPENDENCIES... configure: error: Package requirements (
    gtk+-2.0 >= 2.10.0
    pygtk-2.0
    x11
) were not met:

No package 'gtk+-2.0' found
No package 'pygtk-2.0' found
No package 'x11' found
```

A simple vista me parecio que no tenia los paquetes nombrados, pero al fijarme si los tengo instalados, salvo pygtk que directamente no me aparece en la lista de paquetes.
No intente reinstalarlos ya que no se del todo bien que son, asi que preferi acudir a ustedes..

Gracias por la ayuda

---

### Post by guillermolisi on 2009-07-28
No sera Quake ?

Luego, le debe estar faltando configuracion al archivo que contiene todas las especificaciones que luego utiliza el comando "configure" donde, entre otras cosas, le indicas donde se encuentran esos paquetes instalados en tu maquina.

---

### Post by Fak89 on 2009-07-28
No no, Guake. Es una terminal estilo consola, bastante comoda..
Y como podria configurar este archivo? o habra alguna forma de arreglarlo reinstalando o algo por el estilo?

---

### Post by pablo.s on 2009-07-28
Está el paquete en
el repositorio Universe.

---

### Post by guillermolisi on 2009-07-28
Lo que te dice Pablo es que no te "mates" instalandolo "a mano", salvo que lo quieras hacer por cuestiones de aprendizaje, practica, curiosidad, etc.

En los repositorios de Ubuntu esta el paquete binario que baja y se instala sin problemas de dependencias.

---

### Post by pablo.s on 2009-07-28
Y también está el
paquete [acá.]("http://www.getdeb.net/app/Guake")

---

### Post by Fak89 on 2009-07-28
oh!.. bueno, entonces descargare el paquete deb..
y si, preferiria instalar a mano para ir aprendiendome los comandos mas basicos por lo menos, pero si las cosas no funcionan bien y ustedes recomiendan esto.. prefiero no arriesgarme a hacer c*****s :P

me funciono perfectamente, muchas gracias pablo y guillermolisi. otra cosa, si no la usaron nunca tal vez les guste.. es bastante comoda, o por lo menos para mi.

---

### Post by pablo.s on 2009-07-28
Ah. O.K. entonces.
Si querés practicar a compilar
un programa te recomiendo
que bajes el código fuente de
VLC o Mplayer, que son muy 
fáciles de compilar (si bien no
es muy breve el proceso) y son
dos programas buenisimos.
Otra práctica puede ser la
compilación del núcleo, de la
cuál hay una pequeña guia
traducida y para mi es algo que
todo el mundo debería hacer
por lo menos una vez cada año.

---

### Post by Fak89 on 2009-07-28
> **pablo.s said:**
> Ah. O.K. entonces.
Si querés practicar a compilar
un programa te recomiendo
que bajes el código fuente de
VLC o Mplayer, que son muy 
fáciles de compilar (si bien no
es muy breve el proceso) y son
dos programas buenisimos.
[B]Otra práctica puede ser la
compilación del núcleo[/B], de la
cuál hay una pequeña guia
traducida y para mi es algo que
todo el mundo debería hacer
por lo menos una vez cada año.

No se porq me suena bastante arriesgado eso :P
De todas formas buscare sobre esto a ver bien de que se trata, gracias por la recomendacion!

---

### Post by guillermolisi on 2009-07-28
> **Fak89 said:**
> oh!.. bueno, entonces descargare el paquete deb..
y si, preferiria instalar a mano para ir aprendiendome los comandos mas basicos por lo menos, pero si las cosas no funcionan bien y ustedes recomiendan esto.. prefiero no arriesgarme a hacer c*****s :P

me funciono perfectamente, muchas gracias pablo y guillermolisi. otra cosa, si no la usaron nunca tal vez les guste.. es bastante comoda, o por lo menos para mi.
Compilar no esta dentro de lo que yo llamaria el juego de comandos basicos. Antes hay una buena cantidad de comandos que dominar para moverse comodo al momento de compilar, aprender el sistema de permisos, y algunas cosas mas que si son realmente basicas.

---

