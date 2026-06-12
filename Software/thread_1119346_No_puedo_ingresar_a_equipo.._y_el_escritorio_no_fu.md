---
title: "No puedo ingresar a equipo.. y el escritorio no funciona"
date: 2009-04-07
forum: Software
---

### Post by ArielUsh on 2009-04-07
Buenas.. soy nuevo en esto de linux.. hace poco instale el Ubuntu 8.10.. corria todo perfecto hasta que el contenido del escritorio se borro, no funca, y cuando intento entrar a equipo, o cualquier lugar sea "carpeta persona, documentos, musica, imagenes, etc" me salta un cartel de error con el siguiente texto:

"No se puede abrir el lugar «file:///home/ariel/Im%C3%A1genes»"
(El texto entre "<< >>" varia segun la carpeta a ingresar) 
Si alguien sabe como solucionarlo porfavor una respuesta... desde ya muchas gracias

---

### Post by ArielUsh on 2009-04-07
Buenas.. soy nuevo en esto de Linux.. Tengo instalado Ubuntu 8.10 y luego de instalar por medio de wine un programa se borraron todos los iconos del escritorio, no funciona, y tampoco puedo ingresar a equipo, documentos, imagenes, musica, videos, etc. porque me salta un cartel con el siguiente texto: 

No se puede abrir el lugar «file:///home/ariel/Im%C3%A1genes»
el texto entre "<< >>" varia segun la carpeta a la que quiero ingresar

Tengo instalado ubuntu y windows xp en dos particiones. 

Por favor si alguien me puede decir como solucionarlo.. desde ya muchas gracias.. Salu2

PD: Intel P4 2.66, 512 Ram, HD 80gb, Nvidia 5200 fx.

---

### Post by sdennie on 2009-04-07
Hola Ariel.

Puse tu thread en el foro de Argentina porque es muy activo y escribiendo en castellano, no vas a recibir muchas respuestas en General Help.

Saludos.

---

### Post by juancarlospaco on 2009-04-07
Do you need... quiero decir, create un nuevo usuario y borra el anterior.
Sistema--->Administracion--->usuarios y grupos.

La proxima hace backup!

---

### Post by guisheca on 2009-04-07
Es raro lo tuyo ariel, que programa fué el que trataste de instalar mediante wine? Si fue eso lo que lo provoco tendría que arreglarse borrando el directorio .wine que está en tu carpeta personal. Fijate que tiene un punto delante del nombre, esto quiere decir que es una carpeta oculta, para poder verla tenés que apretar ctrl+H en el explorador.

Al borrar la carpeta .wine van a desaparecer todos los programas que hayas instalado mediante él, tené en cuenta eso. Por otra parte, los menús que wine te generó en Aplicaciones>Wine van a permanecer, pero, obviamente, no van a funcionar.

---

### Post by sdennie on 2009-04-08
Estoy casi seguro que el problema es entra la diferencia de UTF-8 y ISO-8859.  Pero no se arreglarlo sin mas informacion.  Capaz que alguien aca sabe.  Por lo menos, quedate tranquilo que lo mas probable es que tus datos todavia estan.

---

### Post by Hei Ku on 2009-04-08
tambien puede ser un tema de permisos.
Abri una ventana de terminal y escribi:
```

cd /home/ariel
ls -ls

```

Postea el resultado, que eso nos va a decir los permisos de las carpetas.

PD: Fusione los dos threads en uno.

---

