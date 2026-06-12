---
title: "Problemas con JDownloader"
date: 2009-02-16
forum: Software
---

### Post by losoollenos on 2009-02-16
Hola buenas noches a tod@s....
Un problema es que cada vez que inicio JDownloader me pide seleccionar idioma y carpeta de descargas como la primera vez que lo instalás, y aunque selecciono español y así muestra en la parte de configuración queda en inglés.
Pero lo más molesto es que si por algún motivo apago la pc al volver a iniciar el programa ya no tiene ninguna de las tareas pendientes, o sea tengo que volver a copiarle los enlaces de los archivos que no se habían descargado (y muchas veces ni me acuerdo de dónde los bajé......jajaja).
Estoy usando Ubuntu 8.04 32 bit, la versión de java es la 6 update 7 (aunque java ya tiene el update 12 en su página, tendrá algo que ver?). Además, hizo estos mísmos problemas en las dos últimas veces que reinstalé el sistema operativo en las dos últimas semanas.
Muchísimas gracias por cualquier ayuda !!!!

saludos

---

### Post by c4d0rn4 on 2009-02-16
por curiosidad, como lo ejecutas y en donde está el programa (directorio y permisos)


Como opinión personal yo sugiero usar las cosas en ingles, hay *más* soporte. (es el mismo salvo que no hay que descocarse con las traducciones que aveces son medias *locas*)

---

### Post by losoollenos on 2009-02-17
Que tal, lo tengo en la carpeta Documentos, lo ejecuto con el acceso directo en el escritorio y los permisos no te sabría decir.
Lo de la traducción mucho no me importa aunque lo prefiero en castellano obviamente, las otras cuestiones sí son "complicantes"

saludos

---

### Post by Mauro22 on 2009-02-17
Estas abriendo el .exe mediante wine o .jar ??

---

### Post by losoollenos on 2009-02-17
El .jar

---

### Post by c4d0rn4 on 2009-02-17
el lanzador que tienes en el escritorio, que dice en la parte de comando?

la carpeta en la que está el jar, antes de darle doble click y abrirla, dale un click derecho y fijate los permisos que tiene.

Decinos en la posbile la ruta, solo cambía el nombre de usuario tuyo (si es que está)

---

### Post by losoollenos on 2009-02-17
Ésta es la ruta que figura en comando del acceso directo del escritorio:

java -jar /home/ubuntu/Documentos/JDownloader/jdownloader_v0.3668/JDownloader.jar

En los permisos que tiene la caroeta que contiene el jar está: 
Propietario: crear y borrar archivos
Acceso a archivo: ---
Después en grupo y otros tienen en acceso a carpeta ninguno y acceso a archivo ---.

La carpeta que contiene el programa: /home/ubuntu/Documentos/JDownloader/jdownloader_v0.3668

saludos

---

### Post by c4d0rn4 on 2009-02-17
se me ocurrió abrir jdownloader hoy (hace unos cuantos días que no lo usaba)

[[IMG]http://img517.imageshack.us/img517/7139/updatejdowndw0.th.png[/IMG]](http://img517.imageshack.us/my.php?image=updatejdowndw0.png)

[http://jdownloader.org/changes/index](http://jdownloader.org/changes/index)

En cuanto a la configuración, perdona que te la pedí; pensé que podía estar en una carpeta que no pudiera escribir el programa por falta de permisos.

---

### Post by losoollenos on 2009-02-17
Perdoná pero no entiendo mucho inglés, que me querés decir?

---

### Post by guillermolisi on 2009-02-17
> **losoollenos said:**
> Perdoná pero no entiendo mucho inglés, que me querés decir?
Rapidamente:

Que avisan que en la actualizacion a punto de comenzar piensan que han solucionado el bug de linklist.
Que a pesar de estar practicamente seguros de que esta solucionado, recomiendan interrumpir la actualizacion si el usuario posee links importantes en la linklist que no han sido exportados.
Para continuar con la actualziacion dar OK.

---

### Post by losoollenos on 2009-02-17
Gracias por la aclaración......bueno por lo que parece no se ha solucionado, no tendrá que ver con el hecho de tener instalado java update 7, siendo que la última disponible en la página de java es la 12?, quisiera probarlo pero no puedo encontrar cómo se actualiza.

Saludos y muchas gracias

---

### Post by hectok on 2009-03-15
Hola amigo!

Mira, yo tenía el mismo problema que tu hace mucho tiempo. Un día dije:
Haber si va a ser que no se me guarda la configuración por no ser root

Probé con el comando sudo pero no tuve éxito

Más tarde descubrí el problema y lo solucioné así:

1º) Es mejor que copies la carpeta del Jdownloader (la que te has descargado) a tu carpeta home 
2º)Escribe el siguiente comando (Donde dice aqui va tu nombre de usuario esbribes el que aparece justo despues de entrar en home)

gksudo -u root "java -jar -Xmx512m /home/Aqui va tu nombre de usuario/JDownloader/JDownloader.jar"

3º) Ya puedes inicarlo, eso sí, te pedirá la claave de usuario.

Nota: A mí no me funcionó las primeras veces,no sé por que. Creo que deberías actualizarlo.

Eso sí, sigue teniendo errores

---

### Post by losoollenos on 2009-03-15
Gracias hectok, el problema se ha ido solucionando en mi caso calculo que por las muchas actualizaciones que tiene el programa.
Igualmente agradezco tu gesto......que sigas muy bien !!!

saludos

---

### Post by faktorqm on 2009-03-16
Yo lo actualice y siempre me pedia mas actualizaciones. Le ponia y me seguian apareciendo. Hasta que me di cuenta que no terminaba de actualizar nunca, y lo dejaba, lo dejaba lo dejaba y adivinen que? No abrio nunca mas! No se que le paso, lo volvi a instalar y sin que me actualice nada anda, pero claro! los "cosos" para los sitios son viejos y entonces no anda... 
No hay alguna otra alternativa? Cuando andaba era bueno este, pero si no anda, adios! Saludos

---

### Post by losoollenos on 2009-03-16
Yo los otros que había probado no los pude hacer andar. Este en el ubuntu 8.04 tenía más complicaciones, en el 8.10 que instala java update 11 parece andar mejor.......es mi humilde experiencia.

saludos

---

### Post by tokis on 2011-04-29
Hola foreros :-)

hacer poco me he instalado ubuntu en un disco que comparte con windows 7.

En windows tengo instalado el Jdownloader y los archivos que me bajo van directamente a un disco duro que denomino BAJADAS.

Pretendo hacer lo mismo con UBUNTU y el Jdownloader (el cual ya he instalado) pero tengo un problema

Cuando trabajando con ubuntu abro la aplicacion Jdowloader, no me aparece ese dico BAJADAS que os comento.

Lo primero que pensé  es que ubuntu no monta ese disco, pero si que lo monta

lo segundo que intente es poner en el jdownloader la ruta del disco duro pero creo que esta mal..

he puesto lo siguiente:

/home/tokis/computer:/Disco%20duro%20de%20500%20GB-1.drive

¿alguien me dice como lo puedo hacer? me gusta bastante mas como trabaja jdownloader con ubuntu, las descargas se producen mas rápido y poco a poco estoy migrando hacia este S.O.

Esperando alguna contestación, me despido de vosotros afectuosamente.

---

### Post by juancarlospaco on 2011-04-29
Hola.

Si la ruta esta mal, debe ser algo como** /media/bajadas** buscalo en tu directorio /media

Te aviso por las dudas que en Ubuntu no es lo mismo bajadas que BAJADAS.

Probaste el Tucan?, es un soft muy similar a JDownloader pero mas integrado y mas liviano.

---

