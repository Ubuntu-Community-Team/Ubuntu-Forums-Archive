---
title: "Ubuntu 9.04 Problema conectar servidor XP"
date: 2009-08-28
forum: Software
---

### Post by Sokotroko001 on 2009-08-28
Buenas tardes,

Estoy incursionando en el Ubuntu e instale el 9.04, y si todo va bien, pienso instalarlo en la empresa ya que Software Legal mandó su famosa declaración jurada, y es dificil comprar todas las licencias del XP.

Pero el sistema contable si o si necesita xp y no queda otra. Aun asi, vengo bien. Pero tengo el siguiente problema:

Quiero acceder a una  unidad compartida que esta en la máquina con xp. Entonces voy a Lugares, Conectar con el Servidor, Tipo de Servicio: "Compartido por WIndows" y en Servidor pongo la dirección de ip de la máquina que es 192.168.1.102, al darle conectar aparece el error:

No se puede mostrar el lugar «smb://192.168.1.102/»
No hay ninguna aplicación registrada para manejar este archivo

Ahora bien, abro el Firefox, y en la barra de direccion escribo smb://192.168.1.102 y veo el contenido, pero claro, al acceder a los archivos, tengo que descargarlos a la pc como si fuera un archivo de internet.


Agradecería que me ayuden con este problemita.

Gracias

---

### Post by Sokotroko001 on 2009-08-28
Me contesto solo, Acabo de darme cuenta que si bien dice, Información opcional tenía que poner el nombre de la carpeta, en este caso e (Que es el nombre de recurso compartido) O sea, no es tan opcional si no pongo la letra E no conecta.

Ahora bien, otra pregunta, como puedo hacer para que sea automático en cada inicio de Ubuntu? Se que se puede hacer un script o algo asi, pero no se como,,,

En Lugares me aparece como "e en 192.168.1.102" ¿no hay forma de ponerle otro nombre, tipo Servidor o Z: ? Puedo mapearlo como se hacia en windows, haciendo que esa ubicacion sea como una unidad?

Gracias,

---

