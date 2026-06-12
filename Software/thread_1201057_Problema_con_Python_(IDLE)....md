---
title: "Problema con Python (IDLE)..."
date: 2009-06-30
forum: Software
---

### Post by CarlosRuiz on 2009-06-30
Holap:
 
Instalé “IDLE” e hice el típico pequeño programa llamado “hola.py":


[I]#!/usr/bin/env python
print "Hola mundo!"[/I]



 Funciona perfectamente cuando lo corro desde IDLE, pero al escribir en la consola “./hola.py”, me dice (habiéndole dado los permisos):
**: No existe el fichero ó directorio**


Tampoco funciona haciendo doble-click sobre el archivo...


 Qué puedo hacer?
 

Saludooos :(

---

### Post by kamus on 2009-06-30
> **CarlosRuiz said:**
> Holap:
 
Instalé “IDLE” e hice el típico pequeño programa llamado “hola.py":


[I]#!/usr/bin/env python
print "Hola mundo!"[/I]



 Funciona perfectamente cuando lo corro desde IDLE, pero al escribir en la consola “./hola.py”, me dice (habiéndole dado los permisos):
**: No existe el fichero ó directorio**


Tampoco funciona haciendo doble-click sobre el archivo...


 Qué puedo hacer?
 

Saludooos :(

le diste permisos de ejecucion al script? chmod 755 hola.py y luego dale run, si no intenta con python hola.py .

---

### Post by CarlosRuiz on 2009-06-30
Holap:

Sí, precisamente esos permisos le di...

Escribiendo el comando **python hola.py** funciona perfectamente, pero lo que quiero es que funcione con **./hola.py**

Help, pliss... xD

Saludooos :p

---

### Post by moreback on 2009-06-30
Hice la prueba en mi sistema y no tuve ningún problema al ejecutarlo

1. vim hola.py
2. Escribir programa
3. chmod +x hola.py
4. ./hola.py

¿Qué te devuelve el comando **/usr/bin/env python**?

---

### Post by kamus on 2009-07-01
> **CarlosRuiz said:**
> Holap:

Sí, precisamente esos permisos le di...

Escribiendo el comando **python hola.py** funciona perfectamente, pero lo que quiero es que funcione con **./hola.py**

Help, pliss... xD

Saludooos :p

mmm dejalo directo con /usr/bin/python (sin env), lo otro es que ejecutes el /usr/bin/env python y ver que pasa..deberia abrir la terminal interactiva de python.

Saludos

---

### Post by CarlosRuiz on 2009-07-02
Holap:

@Kamus:
Si lo dejo directo con **/usr/bin/python**, me aparece en consola:
*bash: ./hola.py: /usr/bin/python^M: intérprete incorrecto: No existe el fichero ó directorio*

@Moreback:
Al escribir  **/usr/bin/env python**, se ejecuta en la consola el intérprete de Python, ese que al principio dice:
[I]Python 2.5.2 (r252:60911, Jul 31 2008, 17:28:52) 
[GCC 4.2.3 (Ubuntu 4.2.3-2ubuntu7)] on linux2
Type "help", "copyright", "credits" or "license" for more information.[/I]

...es lo mismo que escribir "python" xD

Todavía no entiendo que pasa... :confused:

Help, plissss...

Saludoooos :(

---

### Post by moreback on 2009-07-03
> **CarlosRuiz said:**
> Holap:

@Kamus:
Si lo dejo directo con **/usr/bin/python**, me aparece en consola:
*bash: ./hola.py: /usr/bin/python**^M**: intérprete incorrecto: No existe el fichero ó directorio*



Ese ^M me recuerda a los terminadores de línea de Macintosh para los archivos de texto, a lo mejor tu editor te lo está poniendo en ese formato. ¿Qué editor usas?

En Linux basta con un LF para terminar la línea, en DOS/Windows es un CR+LF y creo que en Mac era sólo con CR (distintas formas de interpretar el código ASCII).

No se me ocurre otra cosa ya que la ejecución en la consola de /usr/bin/env python está ok.

---

### Post by CarlosRuiz on 2009-07-03
Holap:

Estoy usando Mousepad... xD

Saludooos :P

---

### Post by moreback on 2009-07-03
¿Y si pruebas con vim o nano? Puede ser que tu editor tenga algo.

---

