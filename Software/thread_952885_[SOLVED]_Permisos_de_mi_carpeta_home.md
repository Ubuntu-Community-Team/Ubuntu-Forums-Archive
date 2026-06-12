---
title: "[SOLVED] Permisos de mi carpeta home"
date: 2008-10-19
forum: Software
---

### Post by guisheca on 2008-10-19
Que tal comunidad tengo una consulta o mas bien un pedido: Alguien me podría tirar el comando con el permiso que se supone que tiene que tener mi home?? me refiro a los permisos mas adecuados para esa carpeta, porque estuve jugando con esas cosas para obtener acceso desde otra distro que tengo en mi disco (mandriva, que lo instalé para poder disfrutar de KDE4 lo mas estable posible) y ahora no se como tiene que ser. Y desde Propiedades>Permisos no me se si me cambia, a veces no cambia o cambia lo que quiere. Pero se que mediante el comando chmod se cambia posta posta, pero no me acuerdo exactamente las opciones de chmod ni menos cual tendría que ser el número del permiso.
Si es una consulta media pavota disculpen muchachos, pero lo que pasa que me vuelvo un poco paranoico si no tengo los permisos adecuados en mi home.
Saludos.

---

### Post by Mauro22 on 2008-10-19
Lo mas normal es tener tu home con los permisos para vos y tu grupo...


Para cambiarlos, lo mas facil es por consola:

```
sudo chown usuario:grupo /home/usuario
```Supongamos que el usuario tuyo es guisheca y el grupo es familia (supongamos) y tu carpeta en home se llama guisheca:

```
sudo chown guisheca:familia /home/guisheca
```
Ahora, supuestamente eso cambia los permisos en un solo nivel o sea que no se aplica a subcarpetas ni subarchivos. Yo un dia cambie los permisos e hice un desastre.

El problema radia si tenes mas de un usuario, porque al hacer:

```
sudo chown -R usuario:grupo /home/usuario
```con el -R, le indicas que tiene que ser recursivo (meterse dentro de todas las carpetas). La cosa es que si bien cumplia con lo prometido me cambia los permisos de los demas usuarios a mi grupo (siendo el unico capaz de usar la PC)

:lolflag:


Es algo de experimentar jeje, sino mejor 

```
 man chown
```

---

### Post by eldragon on 2008-10-19
y falta los "permisos"jejej

asi que yo haria para garantizar compatibilidad:

```

$ chmod u+rw g+r o+r-w -R /home/user

```

eso asigna a todos tus archivos lectura/escritura para el dueño (vos), lectura para el grupo, y lectura / noescritura para todos los demas.

es recursivo (-R)

---

### Post by c4d0rn4 on 2008-10-19
En nautilus hay un gui para hacerlo y aplicar la configuración a todo los archivos dentro de la carpeta "madre".

sudo nautilus, buscas la carpeta, click derecho propiedades, pestaña permisos y cambias al root que debe ser el que está por defecto y ponés a tu usuario o grupo de usuarios.

Supongo que otros browsers tmb tendrán la opción de hacerlo.

---

### Post by guisheca on 2008-10-20
Gracias muchachos!! Mauro22 y eldragon, en realidad sus aportes no solucionaron nada en forma directa, pero me mostraron cual era el camino y creo que esa es la gracia no??
c4d0rn4 justamente en mi consulta aclaro que, no se porqué, manejar estos permisos de forma gráfica con nautilus no funciona, lo mejor es hacerlo desde consola, sin embargo gracias por compartir.
En fin, lo que estaba buscando al final era:

```
$ chmod 770 -R /home/guillermo

```
Acá va la explicación:

El comando chmod seguido de 3 números asigna permisos al usuario, al grupo y a otros.
Usuario: Permiso "7" el usuario puede leer, escribir y ejecutar el archivo o carpeta.
Grupo: Permiso "7" los miembros de este grupo pueden leer, escribir y ejecutar este archivo o carpeta.
Otros: Permiso "0" los "otros" no pueden hacer absolutamente nada, ni leer, ni escribir, ni ejecutar, ni nada.
Ya me siento mas tranqui con los permisos de mi /home.
Hasta mañana! me voy a dormir me muero de sueño.
Saludos

---

### Post by eldragon on 2008-10-20
> **guisheca said:**
> Gracias muchachos!! Mauro22 y eldragon, en realidad sus aportes no solucionaron nada en forma directa, pero me mostraron cual era el camino y creo que esa es la gracia no??
c4d0rn4 justamente en mi consulta aclaro que, no se porqué, manejar estos permisos de forma gráfica con nautilus no funciona, lo mejor es hacerlo desde consola, sin embargo gracias por compartir.
En fin, lo que estaba buscando al final era:

```
$ chmod 770 -R /home/guillermo

```
Acá va la explicación:

El comando chmod seguido de 3 números asigna permisos al usuario, al grupo y a otros.
Usuario: Permiso "7" el usuario puede leer, escribir y ejecutar el archivo o carpeta.
Grupo: Permiso "7" los miembros de este grupo pueden leer, escribir y ejecutar este archivo o carpeta.
Otros: Permiso "0" los "otros" no pueden hacer absolutamente nada, ni leer, ni escribir, ni ejecutar, ni nada.
Ya me siento mas tranqui con los permisos de mi /home.
Hasta mañana! me voy a dormir me muero de sueño.
Saludos

la diferencia entre tu solucion y la mia es que:

a) la tuya asigna +x a TODOS los archivos. ((( una mala idea )))
b) la tuya es una modificacion destructiva. con la forma octal, modificas TODOS los permisos. de mi manera solo agregas los permisos que y donde hacen falta, y quitas los permisos que no queres. (en este caso, escritura para el resto del mundo).

si no te funcionaba de 1 mi solucion, puede ser porque hayas modificado algunos archivos que SI requieren la propiedad de ejecutables.

---

### Post by faktorqm on 2008-10-20
> **guisheca said:**
> c4d0rn4 justamente en mi consulta aclaro que, no se porqué, manejar estos permisos de forma gráfica con nautilus no funciona, lo mejor es hacerlo desde consola, sin embargo gracias por compartir.

Hola, lo mejor es ejecutar nautilus para que éel pueda asignar permisos ;) Si lo ejecutas como usuario, nunca va a poder dar permisos por arriba de los permisos posibles para ese usuario. Podemos apretar alt + F2, escribir gksudo nautilus y poner la contraseña y ahi vas a ver como nautilus asigna permisitos ;)

> **guisheca said:**
> 
En fin, lo que estaba buscando al final era:

```
$ chmod 770 -R /home/guillermo

```
Acá va la explicación:

El comando chmod seguido de 3 números asigna permisos al usuario, al grupo y a otros.
Usuario: Permiso "7" el usuario puede leer, escribir y ejecutar el archivo o carpeta.
Grupo: Permiso "7" los miembros de este grupo pueden leer, escribir y ejecutar este archivo o carpeta.
Otros: Permiso "0" los "otros" no pueden hacer absolutamente nada, ni leer, ni escribir, ni ejecutar, ni nada.
Ya me siento mas tranqui con los permisos de mi /home.
Hasta mañana! me voy a dormir me muero de sueño.
Saludos

Voy a explicar rapidamente como es el tema de los permisos, sólo por que veo real interés en aprender.
Tenés 10 lugares, de izquierda a derecha, que se separan asi:

El primer lugar, te dice si es un enlace, un directorio o un archivo. Esto lo hace poniendo "l" (link, enlace), "d" (directory, directorio), o "-" cuando es un archivo.
En el segundo, tercer y cuarto lugar, tenes los permisos que son asignados al usuario que creo el archivo, y a su vez se hace un sub-orden que es, de izquierda a derecha, lectura, escritura, ejecucion o nada.

r (read, lectura)
w (write, escritura)
x (ejecucion)
- (nada)

En el quinto, sexto y septimo lugar, lo mismo que antes pero para el grupo al cual pertenece el usuario que creo el archivo. (owner)
En el octavo, noveno y decimo lugar, estan los permisos para el grupo "todo el mundo", que significa que cualquiera sea el usuario y el grupo, lo puede ver o no, o los permisos que le pongas.

Ejemplos (se obtienen con el comando ls -l <archivo>):

1) ```
drwx------
```

Esto es, un directorio (por la "d" en el primer lugar), con permisos de lectura, escritura y ejecucion (rwx, todo para el usuario, nada para el grupo, nada para el resto del mundo). Esto significa que SOLO tu usuario, puede hacer algo con ese archivo.

2) ```
-rw-r--r--
```

Esto es, un archivo (tiene un "-" en primer lugar), el usuario lo puede leer y modificar, no lo puede ejecutar, el grupo solo lo puede leer y el resto del mundo solo lo puede leer.

3) ```
faktorqm@the-edge:~$ ls -la /media
total 16
drwxr-xr-x  4 root root 4096 2008-10-20 07:24 .
drwxr-xr-x 20 root root 4096 2008-10-20 07:12 ..
lrwxrwxrwx  1 root root    6 2008-04-29 05:16 cdrom -> cdrom0
drwxr-xr-x  2 root root 4096 2008-04-29 05:16 cdrom0
lrwxrwxrwx  1 root root    7 2008-04-29 05:16 floppy -> floppy0
drwxr-xr-x  2 root root 4096 2008-04-29 05:16 floppy0
-rw-r--r--  1 root root    0 2008-10-20 07:19 .hal-mtab
faktorqm@the-edge:~$ 

```

Esta lista nos muestra, los primeros dos directorios ("." es un alias a la carpeta actual, ".." es un alias a la carpeta inmediatamente anterior) y luego nos muestra un link, con todos los permisos al directorio cdrom0. Pero estos permisos no son reales, es decir, los que importan cuando haces un link son los del destinatario, no los del link propiamente.

Permisos octales:

Obviamente como vi antes es bastante complejo andar escribiendo chmod ugo+rwx <usuario> o cosas peores.... como las que vi antes xD
Entonces que se invento? permisos octales. Esto funciona del mismo modo que las potencias 2, 2 a la cero, 1, 2 a la uno, 2 y 2 a la 2, 4. entonces cada permiso le corresponde un numero, y cada suma de numeros le corresponde la suma de permisos.

0: nada (-)
1: ejecución (x)
2: escritura (w)
3: ejecución y escritura (wx)
4: lectura (r)
5: lectura y ejecución (rx)
6: lectura y escritura (rw)
7: lectura, escritura y ejecucion (rwx)

Ahora bien, cada uno de estos numeros es para usuario, grupo o todos (others), entonces por ejemplo, el equivalente de este comando 

```
chmod ugo+rwx <archivo>
```

seria: ```
chmod 777 <archivo>
```

Por ejemplo, yo quiero, acceso total para mi usuario, no ejecucion para mi grupo, y solo lectura para el resto, deberia hacer:

```
chmod u+rwx g+rw o+r <archivo>
```

u es user (usuario), g es group (grupo) y o es others (otros, resto del mundo)

Utilizando permisos octales, seria:

```
chmod 752 <archivo>
```

mucho mas facil no?

Comentarios varios: 

1) ls -l muestra tambien como vimos arriba el usuario y el grupo al cual pertenece el archivo.
2) el permiso "x", no solo se usa para ejecucion, sino para las funciones de indexado y busqueda, por lo tanto, si no tengo permisos para verlo, ni para modificarlo, si no tiene la x tampoco lo voy a poder buscar.
3) el usuario root NO LEE permisos, es decir, el usuario root no revisa permisos cuando trabaja con archivos, siempre tiene acceso total y absoluto sobre la computadora, por eso es tan peligroso usarlo cuando se desconoce lo que se esta haciendo.
4) el famoso chmod 777 viene de asignarle permisos totales a todo el mundo y por eso tambien es tan criticado...
5) si se equivocan y por algun motivo hacen chmod 000 sobre un archivo, probablemente tengan que entrar como root a la terminal o hacer sudo ls -l para poder ver el archivo, cambiarle los permisos y volver a trabajar con el....

Salu2!!!!! Cualquier duda o error consulten. :KS

---

### Post by guisheca on 2008-10-20
Y que duda puede haber con semejante explicación!! muchísimas gracias faktorqm!!!
[I]
edit: puedo agregar esta info como tutorial a mi blog?? citando la fuente obviamente[/I]

---

### Post by eldragon on 2008-10-20
> **guisheca said:**
> Y que duda puede haber con semejante explicación!! muchísimas gracias faktorqm!!!
[I]
edit: puedo agregar esta info como tutorial a mi blog?? citando la fuente obviamente[/I]

otra cosa que cabe aclarar, que hay ciertas formas de manejo de permisos que no son tan directas como asignar 1 al que queres, y 0 al que no (en octal 7 = 111, 5 = 101, etcetera) donde se hace una pequeña operacion sobre una mascara (las famosas umask).

donde, si en fstab aparece por ejemplo umask=022 la operacion es
MAXIMO PERMISO POSIBLE AND NOT(umask)

si esto on queda claro, se considera maximo permiso posible de la siguiente manera:
si es un directorio: es 777 (esto se debe a que para ingresar a ellos, necesitan ser +x
si es un archivo: es 666 (lectura y escritura para todos)

por lo que con umask=022, al crear un directorio, los permisos se asginan como
777 AND -022 = 777 AND 755
que es: 111 111 111 x 111 101 101 = 755
pero si fuera un archivo: se hace
666 AND -022 = 110 110 110 x 111 101 101 = 644

es un tanto mas avanzado, me costo a mi entenderlo al principio por su discrepancia con chmod.

solo recordar que +x en un directorio implica poder ingresar a él. el AND es logico, por lo que es una multiplicacion binaria. 1 x 1 = 1, 1 x 0 = 0. y el not, invierte todos los bits: 101 = 010

---

### Post by faktorqm on 2008-10-21
> **guisheca said:**
> edit: puedo agregar esta info como tutorial a mi blog?? citando la fuente obviamente[/I]

Si, de todas maneras no me parece que esté super completo como para agregarlo, pero en un principio si. (y de paso podrias poner un link al foro asi se acerca mas gente a ubuntu argentina ;))

el dragon: ¡estan aprendiendo! :P soy partidario de que aprendan mas dia a dia pero tampoco pegarles un palazo en la kbza! jijijij

---

### Post by WanderingKnight on 2008-10-21
Hasta donde yo tengo entendido la configuracion default de todo lo que esta en el /home/usuario es (en octales) 644...

Me acuerdo porque la ultima vez que lo cambie (haciendo la gran cagada de asignar 777) se me rompio todo :D

---

### Post by faktorqm on 2008-10-21
no es 752 el default? o es 644 mas algun umask? Salu2!!

---

### Post by guisheca on 2008-10-21
> **faktorqm said:**
> de paso podrias poner un link al foro asi se acerca mas gente a ubuntu argentina ;))

Hecho!!! :)

---

### Post by WanderingKnight on 2008-10-21
> no es 752 el default? o es 644 mas algun umask? Salu2!!

Ojo que creo que el directorio en si mismo tiene otros permisos... 644 son los permisos para lo que va adentro.

---

### Post by guisheca on 2008-10-21
Lo permisos por defecto de los archivos creados por el sistema son:

[IMG]http://i38.tinypic.com/ljxhv.jpg[/IMG]

Y los de las carpetas creadas por el sistema son estos:

[IMG]http://i33.tinypic.com/x0uwds.jpg[/IMG]

No se que onda.

---

