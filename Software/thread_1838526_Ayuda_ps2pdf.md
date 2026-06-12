---
title: "Ayuda ps2pdf"
date: 2011-09-03
forum: Software
---

### Post by l_amadei on 2011-09-03
Hola, como están? Hoy es el primer día que uso Ubuntu 11.04 y tengo  3944849 dudas. La más importante es como puedo convertir un archivo ps a  pdf (o jpg, o alguno que pueda usar en el libreoffice)? Leí que usando  ps2pdf, pero cuando uso ese comando me sale:
 Error: /undefinedfilename in (xxx.ps)
 Operand stack:
 Execution stack:
   %interp_exit   .runexec2   --nostringval--   --nostringval--    --nostringval--   2   %stopped_push   --nostringval--   --nostringval--    --nostringval--   false   1   %stopped_push
Dictionary stack:
   --dict:1160/1684(ro)(G)--   --dict:0/20(G)--   --dict:77/200(L)--
Current allocation mode is local
Last OS error: 2
GPL Ghostscript 9.01: Unrecoverable error, exit code 1
 lo que no sé es si estoy escribiendo el comando mal (muy posible) u otra cosa
 Gracias por leer, abrazo.

---

### Post by guillermolisi on 2011-09-03
Y como es la linea de comando que escribis para convertir el archivo ?

Tambien se puede convertir de ps a otro formato aceptable por LO usando Gimp o Inkscape, por ejemplo.

---

### Post by l_amadei on 2011-09-03
Escribo ps2pdf xxxx.ps xxxx.pdf

Como sería la otra opción? 

Tengo q aclarar q totalmente perdido en esto, por si alguno que quedó dando vueltas por ahi no se dió cuenta je...

---

### Post by guillermolisi on 2011-09-03
El archivo en formato ps esta en el directorio donde esta "parado" cuando emitis la orden en la linea de comando ? Te pregunto porque el primer mensaje que aparece dice > Error: /undefinedfilename in (xxx.ps) es decir, o no existe con ese nombre o no lo encuentra porque esta en otro directorio.

Ojo con el uso de mayusculas y minusculas porque en Linux se diferencian (no como sucede en Windows que le da lo mismo y reconoce "A" y "a" como caracteres iguales para el nombre de archivo).

---

### Post by l_amadei on 2011-09-03
Si! Era eso, estaba en cualquier carpeta, ahí pude hacerlo, muchísimas gracias che, un abrazo

---

