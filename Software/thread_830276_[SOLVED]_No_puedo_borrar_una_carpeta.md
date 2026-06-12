---
title: "[SOLVED] No puedo borrar una carpeta"
date: 2008-06-15
forum: Software
---

### Post by Gpafundi on 2008-06-15
Hola a todos. Bueno, tengo un problema quizá estúpido o no... No se, ustedes me dirán. La cosa es así. Soy nuevo en esto del ubuntu y la verdad cada vez me gusta más. Por primera vez (y después de tantos intentos frustrados) pude instalar todos los controladores de mi pc correctamente. Acá viene mi situación:

Instalé los controladores de mi impresora HP Photosmart C6280 con un driver que se llama "hplip-2.8.5" que descargué en el escritorio y ejecuté desde terminal. Se instaló correctamente, la impresora anda bien pero... La instalación me creo una carpeta en el escritorio llamada "hplip-2.8.5" y que no la puedo borrar. Tiene un candado arriba a la derecha. Cuando la quiero borrar me pone un mensaje de error que dice "La carpeta <<hplip-2.8.5>> no se puede gestionar porque no tiene permisos para leerla.". Tampoco puedo abrirla porque dice que no tengo los permisos suficientes para ver el contenido.

Bueno. Espero haber sido claro.

---

### Post by ramiro_md on 2008-06-15
Ese cartel aparece porque tenes que ser "superusuario" para borrar archivos y carpetas. Lo que tenes que hace res lo siguiente:
!) Abre una terminal.
2) Teclea $sudo chmod 777 /home/escritorio/nombredelacarpeta
3) Introduce contraseña
4) Vas al escritorio y borras la carpeta que queria suprimir.
Si en vez de gnome unas kde, en el punto 2, en vez de escritorio es desktop.

Te doy un sonsejo. No elimines el instalador de lo drivers o la carpeta que esta en el escritorio. Guardala en un backup te puede servir mas adelante.

---

### Post by Gpafundi on 2008-06-19
Gracias. Pude borrarla.

---

### Post by ramiro_md on 2008-06-19
de nada, pone  thread tool > solved ;)

---

### Post by santiagoward2000 on 2008-06-19
> **ramiro_md said:**
> de nada, pone  thread tool > solved ;)

Uhh, pero ya no existe eso! :lolflag:
Sacaron esa opcion la ultima vez que actualizaron el foro. Lo que se puede hacer ahora es cambiar el titulo....

---

### Post by ramiro_md on 2008-06-19
DEsconocia !!! hasta hace 2 dias lo hice asi ¬¬..xq actualizan cada 2 x 3 ??

---

### Post by firepic on 2008-06-19
Ramiro, no conocía esa opción, gracias!
Yo lo hago entrando a la consola y escribiendo "su" y luego coloco contraseña de superusuario... entonces me cambia a modo "root" y puedo escribir y borrar lo que desee jeje...:)
Ok saludos!

---

### Post by santiagoward2000 on 2008-06-19
> **ramiro_md said:**
> DEsconocia !!! hasta hace 2 dias lo hice asi ¬¬..xq actualizan cada 2 x 3 ??

Ahhh!!! Lo pusieron de nuevo!!! No sabia!! Perdon!!
Si, ahora esta, pero hace un tiempo lo habian sacado....
El que se quedo fui yo :oops:

---

### Post by ramiro_md on 2008-06-22
EL comando chmod es mas amplio, para el que lo necesite aca dejo un link interesante...
[http://www.desarrolloweb.com/articulos/tutorial-comando-chmod.html](http://www.desarrolloweb.com/articulos/tutorial-comando-chmod.html)

Espero que te sirva firepic...un saludo.
pd: santiago ya me parecia lo del solved jejeje....

---

### Post by N1C0142 on 2008-08-24
yo tengo el mismo problema no puedo borrar nada de nada de mi pc .

tengo un pc viejo que me sirve de servidor y  tiene edubuntu  y me conecto a el atraves de ssh hasta ahi todo bien. 
pero cuando entro a los discos duros de la vieja maquina por ssh  no me deja borrar las carpetas ni ningun otro archivo intente cambiar los permisos como root pero no los cambia ,los discos estas en Vfat 32  tiene algo que ver esto.

---

