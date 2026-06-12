---
title: "[SOLVED] Crear un usuario con acceso restringido, como lo hago?"
date: 2008-06-09
forum: Software
---

### Post by atari130xe on 2008-06-09
Hola gente, tengo la pc con 2 usuarios (el mio -root-) y el de mi hna. la cual puede acceder a mi home si asi lo desea, el tema es que quiero crear un nuevo usuario para mi sobrinito (es chico) y no quiero que el si pueda entrar a determinados directorios (mi home o el de mi hna) cuales serian los pasos si es que se puede, para que el solo se mueva dentro de su home y no tenga acceso a otros directorios/carpetas del sistema? gracias!:)

---

### Post by fgl82 on 2008-06-09
Al crear el nuevo usuario fijate que deberías poder establecer ciertas restricciones para el mismo (por ejemplo, uso de impresoras, montado de unidades, etc).

En cuanto a no acceder a ciertas carpetas, si no me equivoco es un tema de permisos que corriendo el nautilus con "sudo" (sudo nautilus desde la consola) podes arreglar de manera gráfica, entrando a las propiedades de la/s carpeta/s a la/s que no quere que entre, y estableciendo los permisos necesarios.

Que alguien me corrija si me equivoco, soy muy nuevo en esto  y no quiero decir pavadas :D

pd: ah, y una cosa, pusiste "el mio -root-"... no deberías usar "root" como un usuario "normal" si vas a conectarte a internet.

---

### Post by Kantier on 2008-06-09
acá es donde explicar las cosas de la forma tradicional funciona mejor que la forma "ubuntu" (léase tirar los comandos que hay que correr)

la onda es así: en linux (y en cualquier unix) cada archivo (los directorios son archivos de un tipo especial) tiene 9 bits de permisos en grupos de tres

[ lectura | escritura | ejecución ] para el dueño, el grupo, y todos los demás. tres grupos de tres bits cada uno.

los permisos pueden estar representados en forma de flags o en forma octal.

[indent]
**_En forma de flags:_**
Tomemos como ejemplo **rwxr----**. R de Read (lectura), W de Write (escritura), X e eXecute (ejecución). Los primeros tres corresponden al dueño del archivo (rwx), los segundos tres corresponden al grupo de usuarios asignado al archivo (r-x) y los terceros tres a todos los demás (---). **Esto es lo que se ve cuando tiran un *ls -l* en consola.**

**_En forma octal:_** [COLOR="Red"](si no entienden esta parte, ignórenla)[/COLOR]
Usando el ejemplo anterior, pasamos a tener en los permisos en binario como 111101000. En sistema de numeración octal (cifras de 0 a 7 en vez de 0 a 9), se toman los bits de a tres y se convierten en una cifra.
```
0 = 000 = 0 -- nada
1 = 001 = 1 -- ejecución
2 = 010 = 2 -- escritura
3 = 011 = 2+1 -- escritura + ejecución
4 = 100 = 4 -- lectura
5 = 101 = 4+1 -- lectura + ejecución
6 = 110 = 4+2 -- lectura + escritura
7 = 111 = 4+2+1 -- lectura + escritura + ejecución
```
Terminamos teniendo que 111101000 en binario es 750 en octal.
[/indent]

Cabe mencionar que todo esto está presentado de forma bastante gráfica y entendible en sistemas como GNOME y KDE, así que la parte octal no es taaaan necesaria. lo importante es saber que hay tres permisos distintos para tres tipos de usuario distintos respecto del archivo en cuestión.

Los directorios necesitan permisos de ejecución para poder leer su contenido, pero sólo permisos de lectura para saber qué tienen adentro (sin ir a subdirectorios).


la forma de permitir al usuario "pepito" acceso al home de "fuanito" es poniendo a pepito en el grupo "fulanito" (si se fijan, el home de un usuario tiene los archivos asignados a un grupo que se llama igual que el usuario -- por lo menos en los ubuntu). Luego ir a las propiedades de **/home/fulanito/** y sacarle los permisos a "otros".
Si antes de esto no se tocó nada raro en los permisos, no va a haber problema.

---

### Post by atari130xe on 2008-06-09
> **fgl82 said:**
> Al crear el nuevo usuario fijate que deberías poder establecer ciertas restricciones para el mismo (por ejemplo, uso de impresoras, montado de unidades, etc).

En cuanto a no acceder a ciertas carpetas, si no me equivoco es un tema de permisos que corriendo el nautilus con "sudo" (sudo nautilus desde la consola) podes arreglar de manera gráfica, entrando a las propiedades de la/s carpeta/s a la/s que no quere que entre, y estableciendo los permisos necesarios.

Que alguien me corrija si me equivoco, soy muy nuevo en esto  y no quiero decir pavadas :D

pd: ah, y una cosa, pusiste "el mio -root-"... no deberías usar "root" como un usuario "normal" si vas a conectarte a internet. jejeje cuando escribí -root- lo que quise hacer entender es que soy el que puede instalar/modificar programas/parámetros en la PC, no uso la compu como root salvo para esas cosas.:)

---

### Post by atari130xe on 2008-06-09
muchas gracias! resuelto, la sencillez es increible!

```
sudo nautilus
```

Elegí el usuario, las carpetas y directorios y le asigné los permisos correspondientes, ingresé como otro usuario e intenté acceder por ej. a mi Home y que obtuve??: 

"el contenido de la carpeta no se pudo mostrar, no tiene los permisos suficientes para ver el contenido de...." 

EXCELENTE :)

---

### Post by fgl82 on 2008-06-09
Me alegro de que te haya servido la solución.

¡Saludos!

---

