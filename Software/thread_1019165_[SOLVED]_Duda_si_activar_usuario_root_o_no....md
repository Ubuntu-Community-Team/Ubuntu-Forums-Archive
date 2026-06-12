---
title: "[SOLVED] Duda si activar usuario root o no..."
date: 2008-12-22
forum: Software
---

### Post by rodolfojavier1982 on 2008-12-22
Hola, tengo una duda existencial (bueno, creo que tanto no, pero...)
La cuestion es esta:
Tengo dos partciones para Ubuntu (aparte de la de intercambio, swap)
Una de 15 GB en donde estan todos los usuarios (la carpeta /home)
y
Otra de 10 GB en donde esta el resto de directorios, incluso la carpeta root

La cuestion es que quiero instalar aplicaciones (en gral juegos) bajadas de internet, que vienen con el instalador, pero al instalarlas, me ocupan disco del usuario actual, o sea siempre del /home, y me estoy quedando sin espacio.
Lo que quiero hacer es instalarlas pero como usuario root, que ocupen lugar de los 10 GB fuera de la carpeta /home ya que todavia me quedan como 5 GB y no de la carpeta de usuarios comunes, que me queda menos de 1 GB y ademas se instala solo para un usuario y no para todos. 

Debo activar al usuario root si o si o hay otra manera de hacerlo?
Es peligroso activar al usuario root? 
Alguna sugerencia?
:confused:

---

### Post by luks911 on 2008-12-22
Seguro alguien que sepa más que yo (que sobran :-P) podrá corregirme o ampliar lo que voy a decir, pero peligroso no es si sabés lo que estás haciendo. 
Ahora, el usuario root existe, no es algo que se tenga que activar. Hay algunas operaciones que deben ser realizadas con los permisos de ese usuario, como instalar un programa. Apt, aptitude o Synaptic no funcionan si no les das la contraseña de root.
En tu caso, deberías instalar los juegos en / (fijate de destinar una carpeta para ello, o usar /bin, pero siempre que sepas dónde lo hacés, sobre todo por una cuestión de orden) utilizando el comando que requiera cada uno de ellos precedido por sudo, lo que te va a dar permisos de superusuario.

---

### Post by Hei Ku on 2008-12-22
De hecho el usuario root viene desactivado. El mecanismo del sudo usa los permisos de root, pero de otra manera. Por defecto, el root no tiene password y no hay manera de loguearse como root salvo que expresamente le pongas el password y habilites el login.

yo crearia una carpeta en / y le daria permisos a tu usuario. Yo tengo un par de carpetas asi.

---

### Post by anarko on 2008-12-23
Tenes que usar el sudo para instalar los programas /usr/local de ahi tenes permisos de ejecucion con todo el resto de los usuarios, entonces te quedarian las cosas instaladas en la particion / y las podes ejecutar desde tu usuario comun y corrientes.

Si mal no recuerdo se hace asi si lo queres hacer bien, si me equivoco corriganme.

---

### Post by Hei Ku on 2008-12-23
Las aplicaciones que queres instalar son de Linux o windows?
Wine crea las carpetas en el home de tu usuario y no sé cómo se hace para moverlas a otro lado.
Si es linux, instalalas con sudo y eso te las instalas en el /

---

### Post by Hei Ku on 2008-12-23
Las aplicaciones que queres instalar son de Linux o windows?
Wine crea las carpetas en el home de tu usuario y no sé cómo se hace para moverlas a otro lado.
Si es linux, instalalas con sudo y eso te las instala en el /

---

### Post by sherwoodinc on 2008-12-23
EDIT: No había leído cómo tenés particionado.

Depende del tipo de juego/programa que te instales, hay opciones.

- Si el juego/programa es de linux, y se instala por paquete, en general los datos van a parar a alguna subcarpeta de /usr. En ese caso, no deberían comerte espacio del /home.

- Si el juego/programa es de windows, y lo corrés con el Wine, me imagino que tu carpeta .wine se está poniendo pesadita.
Yo en ese caso, movería my .wine a otra partición; un lugar sencillo que no requiere ponerte permisos de root es el /var/tmp (NO el /tmp porque se vacía en cada boot). 
Una vez movido el .wine a otro lado, basta con crear un enlace simbólico en tu home que apunte a la nueva ubicación:
```

mkdir /var/tmp/pepito
mv /home/pepito/.wine /var/tmp/pepito
ln -s /var/tmp/pepito/.wine /home/pepito/.wine

```

En ese ejemplo, válido para el usuario pepito, moví el .wine a una carpeta "pepito" que me hice en el /var/tmp.
IMPORTANTE: En una reinstalación, hay que tener en cuenta que en general el /var vuela entero...

---

### Post by rodolfojavier1982 on 2008-12-23
Gracias a todos los que respondieron.
Creo haberlo solucionado...
Lo que queria hacer era utilizar el espacio de la particion que no era de los usuarios /home , pero ningun usuario podia crear carpetas fuera del /home, salvo el root, pero no lo tengo activado por defecto.

Lo que hice fue entrar a la consola y crearme un directorio fuera de /home para que utilice los 10 GB asignados a esa particion.
Cree una carpeta JUEGOS en / (/JUEGOS) y le di todos los permisos para que cualquier usuario pueda crear,modificar y borrar el contenido de esta.
(Obviamente podria restringir un poco mas el acceso, pero por ahora me sirve asi).
Lo que hice:
//Cree la carpeta para los futuros juegos de Linux.
$sudo mkdir /JUEGOS
//Le di todos los permisos
$sudo chmod 777 /JUEGOS

Listo! Ya tengo una carpeta fuera de /home que use la otra particion y que los usuarios tengan acceso a esta! :)

Y ya que estaba hice lo mismo pero en /home, cree una carpeta /home/COMPARTIDOS, para depositar archivos comunes para todos los usuarios.

Bueno, todavia no instale el juego, porque lo estoy bajando con el torrent, pero supongo que va a solucionar lo que queria hacer.

Gracias a todos!
PD:Todavia no lo voy a poner como solved, en cuanto compruebe que soluciono mi problema, lo marco... ;)

---

### Post by rodolfojavier1982 on 2008-12-23
Bueno, solucione el problema con este metodo!
Instale el Savage 2 desde el instalador .bin (lo renombre a .run porque no me lo aceptaba como instalador) y le indique que lo instale en la carpeta /JUEGOS que habia creado antes, ahora me tomo espacio de la particion fuera de /home, asi que todo bien.

Saludos a todos, y gracias por responder...
:guitar:

---

