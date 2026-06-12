---
title: "Problemas de Asociación de archivos Firefox"
date: 2011-08-29
forum: Software
---

### Post by asterix77 on 2011-08-29
Estimados.

Tengo el siguiente inconveniente; para visualizar bien y poder editar algunos libros de excel en mi trabajo (.xmls por ejemplo)y que no me funcionan con libreoffice, instalé a través de wine microsoft office 2007.  Todo bien, excepto que algunos de esos libros de excel los descargo con firefox desde servidores web, y me los abre en el 100% de los casos con office. Pero hay libros excel que descargo sin macros y si se pueden ver bien libreoffice, sin embargo al irme en firefox a editar----->preferencias----->Aplicaciones---->Hoja de cálculo excel me aparecen las siguientes opciones:

a) Preguntar siempre
b) Guardar archivo
c) Usar Microsoft Excel (por defecto)
d) Usar Otra ....

No veo por ningún lado la alternativa de libreoffice calc, y al escoger d) se me abre un cuadro de diálogo preguntándome el programa que quiero el cual se abre en mi /home/usuario.

He navegado por /usr/bin/ buscando la aplicación, y solo he encontrado una que dice libreoffice, el cual he escogido. Pero al descargar el archivo se abre en libreoffice writer

Por favor si alguien me puede ayudar a solucionar esto, se lo agradecería.

Uso lucid 32 bit, y firefox 6.0

Saludos

---

### Post by asterix77 on 2011-08-29
Algo que había estado realizando, era que cuando preguntaba por que programa usar, le indicada que use /usr/bin/libreoffice3.4. Pero al descargar el archivo me abría una hoja vacía sin el contenido descargado.... al menos estaba cerca.

Finalmente para solucionar en parte el tema (y no sé si realmente es poco técnico), lo que hice fue crear un archivo con gedit en mi home al que le di por nombre Calc con el siguiente contenido:

#!/bin/sh

libreoffice3.4 --calc $1

Luego cerré el editor y le dí permisos de ejecución

$chmod +x Calc


Lo que hace este script, es pasar el primer argumento (nombre del archivo excel en este caso), a libreoffice calc para abrirlo.

Me fui luego a Fierfox editar----->preferencias----->Aplicaciones---->Hoja de cálculo excel Y seleccioné Calc ......... y me funcionó.


Así es que hasta que no encuentre una solución más técnica, me quedaré con esta.


Saludos

---

### Post by alfplayer on 2011-08-29
Los ejecutables de LibreOffice empiezan con **lo**. LibreOffice Calc es **localc**. Podés ejecutar esto para saber dónde está ese archivo ejecutable:

> which localc

---

### Post by asterix77 on 2011-09-02
Estimado:

Ese comando no me arroja ningún resultado

~$ which localc
~$ 


Saludos

---

### Post by alfplayer on 2011-09-02
En 10.04 estaba OpenOffice, no LibreOffice. ¿No tenés OpenOffice? Si es así, el ejecutable es **oocalc**.

---

