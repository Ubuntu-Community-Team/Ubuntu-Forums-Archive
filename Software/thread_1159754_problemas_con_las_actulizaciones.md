---
title: "problemas con las actulizaciones"
date: 2009-05-15
forum: Software
---

### Post by Sargento_Loco on 2009-05-15
Hola ):P gente soy EXTREMADAMENTE nuevo y tengo problemas con las actualizaciones y con la descarga de de los componentes, directamente no pasa nada, me pide la contraseña y siguiente paso me da un informe de error o simplemente vuelve a la pantalla y no hace nada, tampoco puedo bajar los codecs para ver las películas en toten. alguien sabe porque pasa esto y como lo soluciono??

---

### Post by staar on 2009-05-15
no puede 'no pasar nada', que dice el informe de error? que te sale si ejecutas ```
sudo apt-get update
``` en una Terminal (Aplicaciones > Accesorios > Terminal)?

saludos

---

### Post by Tosh78 on 2009-05-15
Postea el error que te tira y vemos como ayudarte, pero asi a ciegas es un poco dificil que alguien te pueda ayudar a encontrar la solucion.

---

### Post by Sargento_Loco on 2009-05-15
ok tratare de ser mas preciso cuando intento descargar los codecs dice:"LA INSTALACION DEL SOFTWARE A FALLADO ocurrio un problema durante la instalacion de los siguientes programas" y da una lista de los 3 codec que intente bajar.

cuando intento actualizar el S.O. sigo los pasos hasta que me aparece una ventana que me pide que confirme la contraseña cuando lo hago se ve que en la barra de tareas se abre una nueva ventana que dice inicializando... luego se cierra pero nada aparece en el monitor fuera de eso.

hice los que me pediste (no estoy seguro de si lo hce bien) esto es lo que dice:
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

personal@personal-desktop:~$ sudo apt-get update
[sudo] password for personal: 
personal@personal-desktop:~$  apt-get update
E: No se pudo abrir el fichero de bloqueo '/var/lib/apt/lists/lock' - open (13 Permiso denegado)
E: No se pudo bloquear el directorio de listas
personal@personal-desktop:~$ 


puede ser un problema de contraseña?

---

### Post by Hei Ku on 2009-05-15
Cuando escribis en una terminal:

```

sudo apt-get update

```

Despues de pedirte la contraseña no te aparece nada mas?

Podes postear tu archivo /etc/apt/sources.list?

---

### Post by guillermolisi on 2009-05-15
Que contraseña ingresas cuando te la pide ?
La que usas para el login a Ubuntu del usuario que habitualmente utilizas ? Otra distinta ?

NO hace falta que nos digas contraseña en si misma sino indicarnos si corresponde a alguna que utilices y para que circunstancias o si es una que solamente usas para estos casos.

Me adelanto un poco a tu respuesta y te digo que la contraseña que tenes que ingresar deberia ser la misma que usas cuando te identificas con Ubuntu para comenzar a usar la maquina, luego de encenderla (login password), y que te permite iniciar la sesion de usuario (ver el escritorio grafico).

---

### Post by Sargento_Loco on 2009-05-15
En realidad no tengo ninguna contraseña (no puse ninguna cuando instale el SO) asi que solo le doy enter, pero no, después que me pide la contraseña no pasa nada (me refiero en la terminal) y en la actualizacion simplemente se cierra la actualización, cuando le doy enter o dice que hay un error como lo describí antes, tampoco me pide una contraseña cuando ingreso al sistema. tengo 306 actualizaciones y me dice que la versión 9.04 esta disponible pero no puedo hacer ninguna actualización como tampoco puedo descargar los codec para los programas por cierto el adobe flash para firefox (que SI se descarga) no funciona y me sigue diciendo que faltan pluguins para ver ciertas paginas (como la de la universidad) que es lo que esta pasando?

---

### Post by Hei Ku on 2009-05-15
Podes postear el archivo /etc/apt/sources.list?

---

### Post by Sargento_Loco on 2009-05-16
bueno busque el archivo, en la carpeta con el nombre sources.list.d no hay nada y el archivo source.list al intentar abrirlo me pide la contraseña pero no se abre nada cuando le doy enter solo se quede buscando un rato y se renueva la pantalla. luego probe abrirla con el editor de texto y esto es lo que consegui:
---------------------------------------------------------------------------------------------------------------------------------
#deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) intrepid main restricted
deb-src [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted
deb-src [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) intrepid universe
deb-src [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) intrepid-updates universe
deb-src [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb-src [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse
deb-src [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse

------------------------------------------------------------------------------------------------------------------------------
espero que sea util no se que mas hacer como dije soy bastante nuevo con este SO

---

### Post by staar on 2009-05-16
el problema es tu password en blanco, no es algo que se haga así como hiciste vos, se necesitan retocar algunos archivos, además sería una grave falla de seguridad si ubuntu permitiera crear un usuario sudoer (que pueda obtener permisos de administrador del sistema) con password en blanco...

no se si creandole una contraseña al usuario que tenés (en realidad, no se si vas a poder crear la contraseña, probá) vas a poder usar sudo, si no, tendrías que crear otro usuario, que si tenga un password, y que pueda obtener permisos de administrador...

ya que sos nuevo, te explico, en GNU/Linux no es como en Ventanas, acá los permisos, los usuarios, los passwords, si son importantes, en Ventanas, la mayoría de la gente, usa una cuenta de administrador todo el tiempo, acá eso es bastante peligroso (bueno en Ventanas también, pero bueh) se usa la mayoría del tiempo una cuenta de usuario normal, y, cuando se quiere tocar algo importante en el SO, se loguea como root, o, concretamente en ubuntu, ni siquiera eso, se usa sudo para elevarle los permisos al usuario y listo...

saludos

---

### Post by Sargento_Loco on 2009-05-16
bueno entonces tengo grabes problemas porque no solo no puedo cambiar la contraseña tampoco puedo crear un nuevo usuario, parece que estuviera bloqueado (abajo dice desbloquear pero pide contraseña y caigo en lo mismo) temo preguntar pero.... tengo que formatear y hacer la instalación de nuevo?

Bueno entonces, ya intente ponerle una contraseña y no puedo, tampoco puedo agregar otro usuario esta bloqueado y para desbloquear se necesita la contraseña....
Con "ventanas" eso no parecía importar demasiado.....
Temo preguntar pero debo hacerlo....... tengo que formatear y empezar de nuevo?

---

### Post by Hei Ku on 2009-05-16
Proba en la terminal poniendo:

```

passwd

```

Y despues pones tu clave 2 veces.

Si esto no funciona, veo una reinstalacion en tu futuro.

---

### Post by Sargento_Loco on 2009-05-16
:(
personal@personal-desktop:~$ passwd
Cambiando la contraseña para personal.
(actual) contraseña de UNIX: (al no tener una solo doy enter)
passwd: Error de manipulación del testigo de autenticación
passwd: password unchanged

---

### Post by staar on 2009-05-16
primero, para tu problema, mepa que no te va a quedar otra que reinstalar :-|

segundo, por curiosidad, una pregunta, el instalador no te aviso algo (algún cartelito, una notificación) al no poner una password? porque sino habría que reportarlo como bug...

saludos

---

### Post by Sargento_Loco on 2009-05-16
noup, no me aviso nada al menos que yo recuerde....

---

### Post by staar on 2009-05-16
mmm, eso está mal, voy a buscar a ver si está reportado y voy a ver si lo reproduzco yo...

saludos

EDIT: según esto [https://bugs.launchpad.net/ubuntu/+source/user-setup/+bug/280014]("https://bugs.launchpad.net/ubuntu/+source/user-setup/+bug/280014") parece que antes no te dejaba, alguien lo reportó como bug, y lo cambiaron para que se pudiera :-|

no sé, estoy confundido, alguien que sepa más, que corresponde?, abrir un bug?

---

### Post by Hei Ku on 2009-05-16
Si, corresponde abrir un bug por el problema del apt-get.

lo unico que se me ocurre es probar loguearse como root, y tratar de corregirlo desde ahi, porque parece que el sudo va para atras sin contraseña.

Ya hace mucho que no hago esto, asi que el que quiera corregir, dele nomas.

```

sudo passwd

```

primero Enter, y despues una contraseña nueva (ni se te ocurra ponerla en blanco :lolflag: ) Si eso no anda, la otra posibilidad es desde un LiveCD modificar el archivo de contraseñas. Pero llegado ese punto, yo reinstalaria.

---

### Post by Sargento_Loco on 2009-05-17
personal@personal-desktop:~$ sudo passwd
[sudo] password for personal: 
Sorry, try again.
 se ve que me queda reinstalar no mas me duele perder la info pero no es mucha lo que si una pregunta cuando haga la reinstalación que opción de partición debo elegir?? por que si elijo la guiada no estoy seguro de que estaría haciendo ( dice que ocuparia el 18 % de sd1 o algo similar) y la otra opcion es completa y no puedo hacerlo proque borraria el windows que necesito para la facu hasta que me adapte por completo a ubuntu al menos. que me aconsejan ???
devo aclarar que en estos pasos me ayudo un amigo la vez anterior pero el no esta y quiero probar para ver como sale

por cierto perdonen que fuera tan jodido el tema y mas aun que los moleste con todas estas dudas quizas algun dia pueda yo ayudar a otros jeje pero falta mucho aun.

---

### Post by staar on 2009-05-17
si elegis guiada, te va a crear otra partición, además de la que tenés ahora, para instalar ubuntu, y vas a terminar con dos ubuntus instalados...

mejor elegí particionado manual, usa la partición que tiene ubuntu ahora con punto de montaje / (una barra) y la partición que tenés ahora de intercambio nuevamente como intercambio (o swap), para que ubuntu se instale de nuevo en las mismas particiones de antes, acordate de tildar para que se formateen esas dos particiones para no generar problemas (obviamente a alguna otra partición, donde tengas instalado windos u otras cosas, NO la formatees)

> **Hei Ku said:**
> Si, corresponde abrir un bug por el problema del apt-get.

yo me refería al problema con el instalador, que no te avisa que al dejar el password en blanco, y obtenés un sistema virtualmente inusable (para un usuario medio, que no sepa recuperarlo)

por lo que entendí en el reporte del 'bug' que pasé, antes el instalador no te dejaba instalar sino especificabas una contraseña, alguien reportó ese comportamiento como 'bug', se le hizo un fix al instalador, y ahora si te deja, pero vemos que resultados trae...

por eso no estoy seguro de qué hacer, abrir un nuevo bug, yo no podría, por varias cosas, no puedo reproducirlo ya que no me queda espacio en el disco para instalar otro ubuntu, tampoco tengo cuenta en launchpad (bueno, eso es fácil de arreglar), asi que no sé...

saludos




EDIT: chee, sargento, como hiciste para instalar sin contraseña?, porque acabo de probar con el livecd y no puedo, no me deja seguir si no especifico una, no tendrás una contraseña y no te la acordás, no? porque parece que escribí todo lo de arriba al pepe...

---

### Post by Hei Ku on 2009-05-17
Alguna version parece que te deja, o el error seria otro.
Y mi enfoque fue que si te dejan instalar sin contraseña, entonces que arreglen el sudo para que funcione sin contraseña. Aunque obviamente me parece mejor la primera opcion, que es no dejar instalar con password en blanco.

---

### Post by Sargento_Loco on 2009-05-17
anoche probe con la version que descargue de la pagina y si me deja y con la version que me mandaron no me deja que se yo porque seria eso la verdad que como dije mucho no entiendo, si no hace mas de un mes que uso ubuntu (y lo lelegi proque me lo recomendaron para la transcion de win a linux) pero parece que he cometido varios errores de aficionado, aunque como todo me sirvio para aprender algo mas. gracias a los dos por todo.-

---

### Post by staar on 2009-05-17
que versión es la que descargaste, alguna beta o rc? cuando la descargaste?

la que te mandaron es la final, la que te manda canonical, con cajita y toda la cosa?

saludos

---

### Post by Sargento_Loco on 2009-05-24
si si la que viene en el cartón con las calcos pero ya esta lo resolví formateando el disco y volviendo a instalar todo. por cierto que ahora quedo bárbaro y se actualizo a una nueva versión, lo que si ya no me figura como antes el agregar y quitar aplicaciones y no se donde encontrarlo jeje

---

