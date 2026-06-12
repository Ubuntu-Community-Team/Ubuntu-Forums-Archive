---
title: "problemas con la partición swap"
date: 2012-10-30
forum: Software
---

### Post by aledruetta on 2012-10-30
Hola comunidad!

Les dejo unas capturas de pantalla de las aplicaciones de disco mostrando cómo aparece mi partición swap. Estoy usando Ubuntu 12.04.1 LTS y ya probé eliminar, formatear y crear nuevamente, varias veces esa partición, pero el problema subsiste. 

Si alguien me puede dar una mano...

Gracias!

---

### Post by jerrrys on 2012-10-30
Acabo de comenzar completamente sobre otra vez si esto es instalaciones sólo nuevas de ubuntu. 

Utilice la opción para utilizar el impulsor de discos entero y usted tendrá ubuntu instaló a una división primaria y el intercambio debe acabar en la división prolongada. Entonces puede hacer modificaciones adicionales con gparted. 

Si usted no piensa que esto es un soulition bueno para usted, explica por favor. 

Yo no hablo español, esta traducción proporcionado por Google.  :)

---

### Post by guillermolisi on 2012-10-30
> **aledruetta said:**
> Hola comunidad!

Les dejo unas capturas de pantalla de las aplicaciones de disco mostrando cómo aparece mi partición swap. Estoy usando Ubuntu 12.04.1 LTS y ya probé eliminar, formatear y crear nuevamente, varias veces esa partición, pero el problema subsiste. 

Si alguien me puede dar una mano...

Gracias!
Ale

La particion Swap no deberia estar marcada como boot partition.
La particion Swap NO se formatea. Se marca y usa.

Para recrearla aconsejo iniciar desde un LiveCD/USB, con gParted eliminar la particion que queres funcione como swap y marcar la particion que aloja a / como booteable (en lugar de la Swap). Crear nuevamente la particion Swap (tipo de sistema de archivos -> Area de Intercambio / Swap partition), aplicar los cambios y reiniciar normalmente.

Proba y conta como te fue.

---

### Post by aledruetta on 2012-10-31
Gracias Guillermo!:popcorn:

Solucionado!

Lo extraño es que no había hecho nada distinto de lo que hago siempre cuando instalo Ubuntu: preparo las particiones con gparted, tres particiones ext4 de distinto tamaño, y después las asigno a swap, / y /home en el instalador. Nunca había pasado eso... La decisión de que la swap fuera booteable fue del instalador... Pero ya está solucionado!

Jerry, no te entendí nada, pero gracias igualmente! :)

---

### Post by jerrrys on 2012-10-31
Creo que sería mejor dar en google traductor y quedarse con el inglés  :)

---

### Post by guillermolisi on 2012-10-31
> **jerrrys said:**
> Creo que sería mejor dar en google traductor y quedarse con el inglés  :)

Hi, Jerrrys

We read and write in Spanish because this is the Argentina LoCo Team subforum and many many people here do not know English.
Google translator is a good help but sometimes gives confusing translation when go from Spanish to English.

Sorry for the inconvenience, thank you for your help and best regards.

---

### Post by EnriqueK on 2012-10-31
Después de modificar la swap debes seguir estos pasos para que sa se active  al inicio del sistema y para que esté usable en caso de hibernar
1.- Ejecuta
     sudo blkid 
     copiar el valor de la UUID de la swap y reeplazarlo en
     sudo gedit /etc/fstab
     y en 
     sudo gedit /etc/initramfs-tools/conf.d/resume
2.- sudo /usr/sbin/update-initramfs -u
3.- sudo init 6
Otra  cosa, si tienes la swap en una partición extendida y si has editado otra particón lógica, el valor de la UUID de la swap va a cambiar, por lo que también debes seguir los pasos indicados antes, en definitiva debes comprobar si es correcto el nalor de la UUID de la swap.

---

### Post by aledruetta on 2012-10-31
EnriqueK, una duda con el punto 3: el 6 identifica una partición? Ese número va independientemente de que yo haya cambiado el orden de las particiones?

Gracias

---

### Post by aledruetta on 2012-10-31
> **aledruetta said:**
> EnriqueK, una duda con el punto 3: el 6 identifica una partición? Ese número va independientemente de que yo haya cambiado el orden de las particiones?

Gracias

EnriqueK, no me respondas, ya me di cuenta de que no.

---

### Post by aledruetta on 2012-10-31
Será que tiene algo que ver que yo haya encriptado mi carpeta de usuario cuando instalé?

me sale este error:

cryptsetup: WARNING: target cryptswap1 has a random key, skipped

---

### Post by aledruetta on 2012-10-31
Y en realidad no se resolvió :(
Sigue apareciendo como desconocida la partición Swap...

---

### Post by guillermolisi on 2012-10-31
Gente inquieta, que mueve las particiones en medio de los problemas que alcanzan a las particiones mismas logrando esa entropia propia del caos universal ;)

Disculpas, no me pude contener :D

---

### Post by aledruetta on 2012-11-01
> **guillermolisi said:**
> Gente inquieta, que mueve las particiones en medio de los problemas que alcanzan a las particiones mismas logrando esa entropia propia del caos universal ;)

Disculpas, no me pude contener :D

Jaja! Espero que esto no provoque un huracán en el Mar de la China...

Pero, en realidad no moví las particiones antiguas, sino que fue más radical el asunto, eliminé todas las particiones, particioné nuevamente e instalé Ubuntu de nuevo. Y el problema continúa...

Pasé la Swap al final porque pensé que podía tener que ver con que estuviese dañado el disco en ese sector, pero evidentemente no era eso...

Lo único diferente a todas las instalaciones que ya había hecho es que esta vez decidí cifrar la carpeta personal por tratarse de una notebook que anda de acá para allá... Pero qué tendrá que ver la Swap con el cifrado, no???

Funcionar, está funcionando todo, pero soy de esas personas que no duermen tranquilo si aparece un error en su sistema operativo, por más inocuo que sea... porque uno no sabe en qué momento deja de ser inocuo...

---

### Post by guillermolisi on 2012-11-01
Ok. Vayamos a la fuente: ```
sudo fdisk -l
```en una consola/terminal y ahi vemos si coincide con gParted.

Linux puede funcionar aun sin Swap partition/file, pero es como vos decis, nunca se sabe cuando se necesitara ese extra de memoria.

---

### Post by EnriqueK on 2012-11-01
También podés crear un archvo swap en una partición en la que tengas espacio, supongamos que la querés crear en /home , pero fuera de tu carpeta persomal y que este archivo sea de 2 Gb, pones en un terminal
sudo su
dd if=/dev/zero of=/home/swapfile bs=1M count=2000
 mkswap /home/swapfile
 swapon /home/swapfile

Si ejecutás top podrás ver que está activada
Si la querés desctivar ponés 
sudo su
 swapoff /home/swapfile
Si la querés eliminar, primero debés desactivarla y luego ejecutá 
sudo su
rm /home/swapfile
Si querés que qude activada al inicio del sistema, ponés la siguiente linea después de ejecutar
sudo /etc/fstab
agregás esto
/home/swapfile	swap	swap	defaults	0	0

---

### Post by aledruetta on 2012-11-01
> **guillermolisi said:**
> Ok. Vayamos a la fuente: ```
sudo fdisk -l
```en una consola/terminal y ahi vemos si coincide con gParted.

Linux puede funcionar aun sin Swap partition/file, pero es como vos decis, nunca se sabe cuando se necesitara ese extra de memoria.

Bueno, ahí va el resultado de fdisk -l. Y aparecen algunas cosas bien extrañas... :confused:

[HTML]Disco /dev/sda: 320.1 GB, 320072933376 bytes
255 cabezas, 63 sectores/pista, 38913 cilindros, 625142448 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes
Tamaño E/S (mínimo/óptimo): 512 bytes / 512 bytes
Identificador del disco: @@@@@@@@(editado)

Dispositivo Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *        2048    62916607    31457280   83  Linux
/dev/sda2       620947456   625141759     2097152   82  Linux swap / Solaris
/dev/sda3        62916608   620947455   279015424   83  Linux

Las entradas de la tabla de particiones no están en el orden del disco

Disco /dev/mapper/cryptswap1: 2147 MB, 2147483648 bytes
255 cabezas, 63 sectores/pista, 261 cilindros, 4194304 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes
Tamaño E/S (mínimo/óptimo): 512 bytes / 512 bytes
Identificador del disco: @@@@@@@@(editado)

El disco /dev/mapper/cryptswap1 no contiene una tabla de particiones válida[/HTML]

---

### Post by guillermolisi on 2012-11-01
Salvo esa mencion al final sobre un supuesto disco /dev/mapper/cryptswap1, la tabla de particiones que muestra fdisk esta perfecta.

Para saber el orden fisico de las particiones tenes que mirar en que bloque comienza una particion y en cual finaliza. La siguiente comenzara en el proximo bloque ... y asi hasta el final del disco.
Es decir, tu particion Swap esta al final, como la habias definido y la particion que aloja a / al principio con la etiqueta de boot.

Tal vez alguien con mas experiencia en discos encriptados pueda aportar algo mas.

---

### Post by aledruetta on 2012-11-02
> **guillermolisi said:**
> Salvo esa mencion al final sobre un supuesto disco /dev/mapper/cryptswap1, la tabla de particiones que muestra fdisk esta perfecta.

Para saber el orden fisico de las particiones tenes que mirar en que bloque comienza una particion y en cual finaliza. La siguiente comenzara en el proximo bloque ... y asi hasta el final del disco.
Es decir, tu particion Swap esta al final, como la habias definido y la particion que aloja a / al principio con la etiqueta de boot.

Tal vez alguien con mas experiencia en discos encriptados pueda aportar algo mas.

Al final, parece ser que sí tenía que ver con la encriptación. A lo mejor es normal y yo me estoy preocupando sin motivo... pero, si alguien sabe algo del tema y nos puede contar, mejor.

Googlenado "/dev/mapper/cryptswap1" aparece información, pero en inglés y, si bien estoy haciendo mi cursito en duolingo.com (que se los recomiendo) todavía estoy en el básico de los básicos. Y google translate me confunde más de lo que me ayuda.

Pregunta: Ustedes cifran su carpeta personal cuando instalan Ubuntu? Cuál ha sido la experiencia?

---

### Post by biale on 2012-11-05
Sobre experiencias con particiones encriptadas...

Hice algunas pruebas a mediados del 2010 y confirme las generales de la ley: donde tengas que hacer alguna tarea de mantenimiento, todo se complica y aparecen problemas dificiles de preveer y manejar. Sumale la posiblidad de un bug nuevo y asi siguiendo.

En definitiva se cumple el principio básico, "siempre es preferible que se pierda antes de que los datos queden expuestos" O sea que a la larga, es necesario tener un backup no encriptado y estar dispuesto a usarlo mas que de costumbre.

Una mejor idea puede ser "Truecrypt". Para el sistema operativo es un archivo mas, que es procesado por un programa producto. Programa multiplataforma y que eventualmente puede ser portable. Pero aun así aparecía un problema menor cuando el contenedor era generado bajo Linux y luego desencriptado bajo W$

---

### Post by guillermolisi on 2012-11-05
> **aledruetta said:**
> 
Pregunta: Ustedes cifran su carpeta personal cuando instalan Ubuntu? Cuál ha sido la experiencia?
No, jamas, casualmente por lo que menciono Biale.
Prefiero utilizar contraseñas de cierta complejidad a volverme loco cuando tenga que hacer tareas de mantenimiento.

En las notebooks: clave para el boot del BIOS, clave para iniciar sesion, clave para el repositorio de contraseñas de Ubuntu, claves a morir pero cuando tengo que lidiar con mantenimiento, todo franco, liso, sin cosas raras en el medio. Home Banking, nada en la maquina, nunca, ni cache siquiera.

Despues de todo no creo que los contenidos que puedan llevarse sean mas interesantes que la oportunidad de hacerse un hardware sin mucho esfuerzo.

---

