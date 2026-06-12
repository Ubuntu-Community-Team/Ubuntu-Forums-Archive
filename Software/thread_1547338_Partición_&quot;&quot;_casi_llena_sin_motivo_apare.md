---
title: "Partición &quot;/&quot; casi llena sin motivo aparente"
date: 2010-08-06
forum: Software
---

### Post by atari130xe on 2010-08-06
Hola gente, Tengo una duda que me gustaría poder evacuar:

Mi partición Root "/" muestra un 73 % de ocupación siendo que es de 20GB y no tengo tantos programas como para que me quede casi sin lugar en ella, no entiendo que puede ser. También noto que el sistema se puso lento (Por ejemplo Firefox 3.6.8 carga lentamente cualquier sitio), supongo que es por el mismo motivo (la partición / está muy llena)

ejecuté:
```
jose@jose-desktop:~$ df -h
S.ficheros            Tamaño Usado  Disp Uso% Montado en
/dev/sdb2              [COLOR="Black"]20G   14G  5,1G  73% /[/COLOR]
none                 1002M  300K 1002M   1% /dev
none                 1007M  756K 1006M   1% /dev/shm
none                 1007M  196K 1006M   1% /var/run
none                 1007M     0 1007M   0% /var/lock
none                 1007M     0 1007M   0% /lib/init/rw
/dev/sdb3             142G   22G  114G  16% /home
/dev/sdb1              69G   54G   16G  78% /media/BCB8E2F0B8E2A7DA
jose@jose-desktop:
```

que podrá ser?

---

### Post by beren.olvar on 2010-08-06
intenta con una aplicacion ke se llama xdiskusage
Muestra graficamente el espacio usado por cada directorio, asi puedes ir viendo kien puede ser el culpable

---

### Post by atari130xe on 2010-08-06
> **beren.olvar said:**
> intenta con una aplicacion ke se llama xdiskusage
Muestra graficamente el espacio usado por cada directorio, asi puedes ir viendo kien puede ser el culpable

Gracias lo instalé, y pasó algo "extraño" (al menos para mí)

encontre que xdiskusage me reporta 9.13GB de archivos en la siguiente ruta:
```
/root/.local/share/Trash/files
``` está lleno de canciones del programa Ultrastar Deluxe, procedo a "seleccionar todo" y eliminar y no solo se "cuelga" el proceso de borrado sino que si elimino cualquier archivo "automáticamente" vuelve a aparecer en el directorio. No comprendo. Ingreso con "sudo nautilus". alguna pista?

Aclaro que las canciones de ese programa se encuentran alojadas en el siguiente directorio:```
/home/usuario/.local/share/games/performous/songs
```
Creo que no deberian ocupar espacio alguno en la partición / siendo esta independiente de /home

---

### Post by beren.olvar on 2010-08-06
Intenta ejecutando el programa como:

xdiskusage /

para ke en vez de leer el directorio actual lea el directorio raiz.
El problema con los archivos en /root/.local/share/Trash/files es ke ese es el directorio de la papelera, entonces al eliminarlos lo ke haces en mandarlos al mismo directorio de vuelta. Para eliminarlos de verdad debes "vaciar la papelera".

suerte!

---

### Post by atari130xe on 2010-08-06
> **beren.olvar said:**
> Intenta ejecutando el programa como:

xdiskusage /

para ke en vez de leer el directorio actual lea el directorio raiz.
El problema con los archivos en /root/.local/share/Trash/files es ke ese es el directorio de la papelera, entonces al eliminarlos lo ke haces en mandarlos al mismo directorio de vuelta. Para eliminarlos de verdad debes "vaciar la papelera".

suerte!

Bueno "solucionado", por alguna razón que desconozo la papelera no quedó totalmente vacía (aún entrando en ella y revisando con "mostrar archivos ocultos" muestra que está VACIA, pero no es así, que hice?
simple borré la papelera desde /root y problema solucionado```
sudo rm -r /root/.local/share/Trash/*
``` alguien sabe (deb ser algo múy técnico) porque pasa esto? saludos y gracias!

---

### Post by beren.olvar on 2010-08-06
no entiendo a ke te refieres con: "muestra que está VACIA, pero no es así"
ke es lo ke keda dentro? pq piensas ke no esta vacia?

de todas formas, lo ke siempre se recomienda es no usar el usuario root para tareas comunes, si no ke dejarlo solo para mantenimiento, de otra forma se presta para problemas.

---

### Post by atari130xe on 2010-08-06
> **beren.olvar said:**
> no entiendo a ke te refieres con: "muestra que está VACIA, pero no es así"
ke es lo ke keda dentro? pq piensas ke no esta vacia?

de todas formas, lo ke siempre se recomienda es no usar el usuario root para tareas comunes, si no ke dejarlo solo para mantenimiento, de otra forma se presta para problemas.

A ver amigo, si voy al ícono de la papelera y veo que no tiene archivo alguno y además pongo "mostrar archivos ocultos" dentro de la misma papelera y sigue sin mostrar nada (completamente vacía) y luego corro xdiskusage y veo que en /root/.local/share/Trash/files tiene 9.13GB de datos es que NO está completamente vacía a eso me refiero, porque ocurre eso? no tengo idea, ahora por lo de SuperUserDO, es el único comando que me permitió borrarla y por consiguiente vaciarla realmente, no es que se use para todo (al menos en mi caso) ;) de todas formas gracias por tu consejo

---

### Post by beren.olvar on 2010-08-06
ok, ahora entiendo.

Primero, el consejo te lo di pensando en ke tu cuenta de root tiene 9Gb en su papelera, supuse ke era pq la habias estado usando para descargar musica o cosas similares. Parece ke no es asi y ke ya estabas al tanto de eso, pero nunca esta demas recordar ese tipo de cosas, por si acaso :P

ahora, CREO ke el problema puede ser el siguiente: en /root/.local/share/Trash/ hay dos directorios: "files" (donde se guardan los archivos borrados) e "info" (donde se guarda informacion para recuperarlos). Puede ser ke al borrar los archivos hayas podido borrar solo los ke hay en "info" y por alguna razon de permisos o algo similar los archivos en "files" aun esten ahi. La razon por la ke no se muestran en nautilus podria ser ke nautius lea la informacion desde "info" y no desde files. De cualkier forma podrias asegurarte haciendo en el terminal

```

sudo ls -a /root/.local/share/Trash/
sudo ls -a /root/.local/share/Trash/files/
sudo ls -a /root/.local/share/Trash/info/

```

eso te mostrara si es ke realmente kedan archivos ahi. En caso contrario, podria ser ke xdiskusage use algun tipo de cache en vez de correr todo de nuevo??
podrias volver a hacer un "df -h" o "du -sm /root/.local/share/Trash/" para ver cuanto espacio estan usando esos directorios realmente.

---

### Post by biale on 2010-08-06
Cuando activamos nautilus con sudo (o gksu) de alguna manera estamos abriendo una sesión de "root". Es lógico que que los archivos se muevan a la papelera de root...

Ahora bien, porque usar "sudo nautilus"? En principio no es una buena idea, salvo que administremos una máquina con múltiples usuarios.

Por la dudas conviene verificar que no exista alguna otra carpeta "Trash" dando vueltas.

---

### Post by atari130xe on 2010-08-06
> **biale said:**
> Cuando activamos nautilus con sudo (o gksu) de alguna manera estamos abriendo una sesión de "root". Es lógico que que los archivos se muevan a la papelera de root...

Ahora bien, porque usar "sudo nautilus"? En principio no es una buena idea, salvo que administremos una máquina con múltiples usuarios.

Por la dudas conviene verificar que no exista alguna otra carpeta "Trash" dando vueltas.

Asi es tengo 3 usuarios más en esta PC (la razón del sudo nautilus)

---

### Post by EnriqueK on 2010-08-06
Poné
sudo rm -Rf /root/.local/share/Trash
Esto va a borrar inclusive la papelera, pero no importa ya que se vuelve a generar cuando haga falta.
Esto te ocurre  por que estás intentando borrar como administrador en forma gráfica (sudo nautilus), en realidad te lo manda a la papelera oculta de root. para evitar esto en el futuro, haz una eliminación sin pasar por papelera mediamte la pulsacióm de las teclas Mayúsculas+Supr
Otra forma es poner en un terminal
sudo rm -Rf
dejas un espacio
arrastras al terminal todo lo que quieras eliminr--> Enter y son historia.

---

### Post by atari130xe on 2010-08-07
> **EnriqueK said:**
> Poné
sudo rm -Rf /root/.local/share/Trash
Esto va a borrar inclusive la papelera, pero no importa ya que se vuelve a generar cuando haga falta.
Esto te ocurre  por que estás intentando borrar como administrador en forma gráfica (sudo nautilus), en realidad te lo manda a la papelera oculta de root. para evitar esto en el futuro, haz una eliminación sin pasar por papelera mediamte la pulsacióm de las teclas Mayúsculas+Supr
Otra forma es poner en un terminal
sudo rm -Rf
dejas un espacio
arrastras al terminal todo lo que quieras eliminr--> Enter y son historia.

Gracias por el dato Enrique :)

---

