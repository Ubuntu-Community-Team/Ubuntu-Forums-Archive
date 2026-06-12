---
title: "sistema y home separados. Pregunta"
date: 2009-09-15
forum: Software
---

### Post by joseluis on 2009-09-15
Hola, instalé ubuntu usando dos particiones. Una para el Sistema de archivos y otra para la Home, justamente para no perder datos cuando actualice el Sistema.
La pregunta viene ahora que se viene la actualización a ubuntu 9.10 y pienso instalar desde cero, formateando la partición del Sistema de ARchivos.
La pregunta, amigos, es ¿como hacer para que no me borre la particion home? No voy a instalar todo en la particion del sistema, sino mantener la particion home tal como está. ¿como se hace?
Espero que me haya podido explicar bien. Gracias

---

### Post by pol666 on 2009-09-15
seleccionas particionado manual, en el momento que te presenta las particiones tenes que reconocer la partición en la que instalaste ubuntu, doble click o editar partición y pones el sistema de archivos (ext4) y "/" en punto de montaje, ademas tildas la opción para formatear.

Por otro lado, buscas la partición que usas como home, y en punto de montaje usas "/home", en sistema de archivos dejas el que estabas usando antes (por ejemplo, si la tenes en ext3 NO pases a ext4 por que se va a borrar) y obviamente NO TILDAS la opción para formatear.

O sea, al ver la tabla ves que se usan 3 particiones (/, /home y swap) solo que sola una partición ("/") es la que se tiene que formatear,

---

### Post by joseluis on 2009-09-15
GRACIAS!!
pensaba que debía ser así, pero necesitaba esta confirmación, tan clara, sencilla, brever y pedagogíca. EXCELENTE EXPLICACIÓN

---

### Post by pol666 on 2009-09-15
De nada, despues conta como te fue en la instalación ;)

---

