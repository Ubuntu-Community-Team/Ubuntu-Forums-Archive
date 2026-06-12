---
title: "Error despues de instalar driver en ubuntu 9.4"
date: 2009-07-25
forum: Software
---

### Post by dcorrea on 2009-07-25
Hola a todos!!!
Resulta que quize probar "Envy" para instalar los driver de mi tarjeta de video ATI (ATI Radeon™ Xpress 200) y asi poder habilitar los efectos graficos...
Instale el driver....al parecer no era el correcto y ahora no se incia ubuntu de manera grafica...me sale video no soportado y pantalla negra...como lo puedo normalizar???

Se agradece su ayuda!!!

---

### Post by armagedonc on 2009-07-25
pone este comando.

dpkg-reconfigure xserver-xorg

---

### Post by pagondel on 2009-07-25
Tambien puedes probar iniciar en "recovery mode" (la segunda opcion en tu grub (generalmente) y una vez q haya cargado seleccionar la opcion "xfix" que intentara arreglar todo de forma automatica 8).

---

### Post by dcorrea on 2009-07-25
Hola!!
Intente la segunda opcion entrando al "recovery mode" opcion XFIX
...pero sigo con el mismo problema...
y como solo me salen algunas lineas ...no me da la opcion de escribir algun comando como me dicen en la primera opcion...

que mas puedo hacer?
Otra cosa....puedo volver a instalar ubuntu...pero solo en la particion ROOT y dejar intacta la opcion HOME???

---

### Post by aledruetta on 2009-07-26
> **dcorrea said:**
> y como solo me salen algunas lineas ...no me da la opcion de escribir algun comando como me dicen en la primera opcion...

que mas puedo hacer?
No estoy muy seguro, pero, ¿si entras en recovery mode y ejecutas ahí el comando que te dio armagedonc?

> **dcorrea said:**
> Otra cosa....puedo volver a instalar ubuntu...pero solo en la particion ROOT y dejar intacta la opcion HOME???
Todo depende de si ya tenías el "/home" separado de "/". Busca en search información sobre "/home" que hay mucho escrito sobre eso.

Saludos y suerte.

---

### Post by dcorrea on 2009-07-28
....opte por lo más conocido para mi...e instale ubuntu nuevamente...:-k

---

