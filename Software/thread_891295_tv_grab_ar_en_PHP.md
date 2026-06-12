---
title: "tv_grab_ar en PHP"
date: 2008-08-15
forum: Software
---

### Post by gabardal on 2008-08-15
Hola a todos, estoy tratando de ejecutar este script:
[http://www.argenteam.net/soft/tv_grab_ar](http://www.argenteam.net/soft/tv_grab_ar)
y me da errores del tipo:

./tv_grab_ar: line 1: ?php: No existe el fichero ó directorio
./tv_grab_ar: line 3: //: es un directorio
./tv_grab_ar: line 5: error de sintaxis cerca de token no esperado `'MULTICANAL',0'
./tv_grab_ar: line 5: `define('MULTICANAL',0);'

Que paquetes necesito instalar para correrlo correctamente?, dentro del mismo dice que necesito php, xmltv y curl, pero ya los instale y sigue igual (a menos que me falte algo mas del php :-P), me gustaria saber como hago una instalacion estandar de php solo para correr scripts de este tipo.
Gracias x adelantado...:biggrin:

---

### Post by macaronij on 2009-11-02
cuando lo ejecutas tenes que avisarle que es php
en la carpeta donde tenes el archivo ejecuta
php tv_grab_ar | tv_sort > programacion.xml

---

