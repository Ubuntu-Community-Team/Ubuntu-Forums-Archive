---
title: "Norton Ghost"
date: 2009-09-16
forum: Software
---

### Post by z37a on 2009-09-16
Gente, necesito hacerles una consulta, se que Ghost no es la herramienta indicada, pero es lo que debo utilizar, también se que me van a decir que lo que pido es medio desubicado, pero bueno, hay atrás algo que tarde o temprano voy a comentar y va a dar que hablar un poco por acá.

Me dieron una imagen hecha en ghost, la cual tiene un disco en Dual boot con Windows XP home y Edubuntu(desconozco la version), dicha imagen esta corrupta y solo pude recuperar el boot loader, la swap y el windows. Asi que bueno por razones extrañas, la instalación original no existe mas, y esta semana van a ubicar al tipo que la hizo(Esta en Costa Rica) para que yo haga esa instalación, una vez echa la instalación se va a crear una imagen de la misma para replicar a 30 PCs en una prueba previa.

En primer lugar lo que se que hay que hacer es reemplazar en el GRUB y el fstab los UUIDs por las particiones(sda1, sda2, etc....). Con eso no tendría que haber problema alguno. Y de acá viene mi gran duda y consulta, Como se comporta el Norton Ghost para realizar dicha tarea? Se muy bien que lo idea seria usar Clonezilla, pero esto si bien lo comente no quieren saber nada, y lo que quiero es saber si alguno ya uso Ghost para Linux y Windows.

---

### Post by gmunioz on 2009-09-16
Hola z37....:

En este sitio:

[http://www.linuxparatodos.net/portal/staticpages/index.php?page=ghost-linux](http://www.linuxparatodos.net/portal/staticpages/index.php?page=ghost-linux)

Tienes un excelente manual sobre el uso de ghost for linux

---

### Post by z37a on 2009-09-16
> **gmunioz said:**
> Hola z37....:

En este sitio:

[http://www.linuxparatodos.net/portal/staticpages/index.php?page=ghost-linux](http://www.linuxparatodos.net/portal/staticpages/index.php?page=ghost-linux)

Tienes un excelente manual sobre el uso de ghost for linux

Ahí esta el inconveniente, tengo que usar si o si Norton Ghost Enterprise(o algo así, la versión grosa del Ghost de Symantec). El tema es que por lo que leí en la pagina oficial dice soportar EXT2/3 y SWAP, pero no me confio que esto funcione bien(ya que trabaja en base a DOS/WIN).

---

### Post by EnriqueK on 2009-09-16
Para mi el mayor problema va a ser la replicacióm de Xp en las otras PCs , por mas que las máquinas sean idénticas, vas a tener el problema de identificación de cada equipo y esto es mucho mas importante si estos van a operar en red en donde el número identificatorio debe ser distinto para cada equipo. Para solucionar esto conozco el programa "Acronis Snap Deploy" , desconozco si el N.Ghost permite hacerlo, seguramente que si, tendrías que tomar muy en cuenta este detalle.
Respecto a la replicación de xbuntu, no deberías tener problemas, salvo que  esté instalado en EXT4 ya que ni Acronis ni N.Ghost reconocen este sistema de archivos, al menos por ahora.

---

### Post by z37a on 2009-09-16
> **EnriqueK said:**
> Para mi el mayor problema va a ser la replicacióm de Xp en las otras PCs , por mas que las máquinas sean idénticas, vas a tener el problema de identificación de cada equipo y esto es mucho mas importante si estos van a operar en red en donde el número identificatorio debe ser distinto para cada equipo. Para solucionar esto conozco el programa "Acronis Snap Deploy" , desconozco si el N.Ghost permite hacerlo, seguramente que si, tendrías que tomar muy en cuenta este detalle.
Respecto a la replicación de xbuntu, no deberías tener problemas, salvo que  esté instalado en EXT4 ya que ni Acronis ni N.Ghost reconocen este sistema de archivos, al menos por ahora.

Por suerte ese no es drama, como comente es Home y bueno... mejor ni sigo, no es lugar para hablar de la ventana jajajaja.

O sea que no hay inconvenientes si se utiliza EXT3? Como dije le tengo algo de miedo a esto, preferiría usar CloneZilla pero bue....

---

### Post by anarko on 2009-09-16
Proba, al crear una imagen ghost y replicarla en otra PC no perdes nada mas que tiempo y despejas tus dudas.

---

### Post by z37a on 2009-09-19
> **anarko said:**
> Proba, al crear una imagen ghost y replicarla en otra PC no perdes nada mas que tiempo y despejas tus dudas.

Ya esta echo el master en EXT3(una pena no poder usar EXT4), así que una vez que se replique les comento que onda como funciono el Norton Ghost, y de paso comento algo mas de esto si puedo por que es una buena noticia.

---

### Post by z37a on 2009-09-26
Resultado final de la prueba:

Symantec Ghost NO FUNCIONA, deja al grub corrupto, haciendo necesario reinstalarlo en cada PC ghosteada, y si hablamos de mas de 1000 PC es inútil, por suerte tras intento de mi jefe que confirmo lo que decia de utilizar CloneZilla convencimos a las personas que debíamos para utilizarlo.

PD: Perdón por doble post! Lo crei necesario comentar aparte.

---

### Post by faktorqm on 2009-09-29
Que lastima que no vi antes este post, asi te evitaba un par de pruebas. El ghost despues de no se que version no sirve mas para clonar linux's justamente por que se rompe el grub. No se que cambios habran hecho, pero la cosa es que no anda. 

Fijate si haces disco a disco que pasa, y no te olvides de tirarle antes al xp el sysprep si es que necesitas subir a dominio. Salu2!

---

