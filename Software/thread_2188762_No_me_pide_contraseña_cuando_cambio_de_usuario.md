---
title: "No me pide contraseña cuando cambio de usuario"
date: 2013-11-18
forum: Software
---

### Post by autusgo on 2013-11-18
Resulta que estos días creé un nuevo usuario para un amigo que necesitaba usar mi PC bastante seguido, así que le puso una contraseña para poder tener privacidad en la información que manejaba. El asunto es que descubrímos que cuando cambio de usuario **no me pide la contraseña**.
Lo primero que pensé es que se debía a que yo soy administrador y tengo acceso a todo. Es así? Si es así creo que está bastante mal implementado porque más allá del acceso a los distintos archivos y directorios, poder ingresar a una sesión es poder entrar a mails, facebook o cualquier otra herramienta que el usuario haya decidido dejar logeada.

Sabes si esto funciona así realmente? Me estoy perdiendo de algo? Hay alguna solución?

Gracias!

---

### Post by gmunioz on 2013-11-23
Gnu/Linux es un sistema operatico diseñado fundamentalmente para trabajo en red, en el que la seguridad de la información que se almacena en los equipos es fundamental, ya que muchos usuarios tendrán o podrán tener acceso a parte de los recursos de software y hardware que están gestionados en estos ordenadores.
Los permisos o derechos que los usuarios pueden tener sobre determinados archivos contenidos en él se establecen en tres niveles claramente diferenciados. 
Estos tres niveles son los siguientes:
-- Permisos del propietario.
-- Permisos del grupo.
-- Permisos del resto de usuarios (otros).
En Gnu/Linux siempre existe la figura del administrador, superusuario o root. 
Este administrador es el encargado de crear y dar de baja a usuarios, así como también, de establecer los privilegios que cada uno de ellos tendrá en el sistema. 
Estos privilegios se establecen tanto para el directorio HOME de cada usuario como para los directorios y archivos a los que el administrador decida que el usuario pueda acceder.
Naturalmente el administrador tiene amplio y total acceso a todos y cada uno de los archivos.

-- Permisos del propietario
Propietario es el usuario que genera o crea un archivo, directorio dentro de su directorio de trabajo (home/usuario, o en algún otro directorio sobre el que tenga derechos. 
Cada usuario tiene la potestad de crear, por defecto, los archivos que quiera dentro de su directorio de trabajo. 
En principio, él y solamente él será el que tenga acceso a la información contenida en los archivos y directorios que hay en su directorio /home/usuario.

-- Permisos del grupo
En general cada usuario pertenece a un grupo de trabajo. De esta forma, cuando se gestiona un grupo, se gestionan todos los usuarios que pertenecen a éste. 
Es más sencillo para el administrador integrar varios usuarios en un grupo al que se le conceden determinados privilegios en el sistema, que asignar los privilegios de forma independiente a cada usuario.

-- Permisos del resto de usuarios
Los privilegios de los archivos contenidos en cualquier directorio, pueden tenerlos otros usuarios que no pertenezcan al grupo de trabajo en el que está integrado el archivo en cuestión. 
A los usuarios que no pertenecen al grupo de trabajo en el que está el archivo, que pertenecen a otros grupos de trabajo, se les denomina resto de usuarios.

Tipos de permisos en Gnu/Linux
Cada archivo queda identificado por 10 caracteres mismos a los que se les denomina máscara. 
De estos 10 caracteres, el primero (de izquierda a derecha) hace referencia al tipo de archivo. 
Los 9 siguientes, de izquierda a derecha y en bloques de 3, hacen referencia a los permisos que se le conceden, respectivamente:
Al propietario
Al grupo
A los otros

El primer carácter de los archivos puede ser el siguiente:
Permiso 	Identifica
- 	        Archivo
d 	        Directorio
b 	        Archivo de bloques especiales (Archivos especiales de dispositivo)
c 	        Archivo de caracteres especiales (Dispositivo tty, impresora&#8230;)
l 	        Archivo de vinculo o enlace (soft/symbolic link)
p 	        Archivo especial de cauce (pipe o tubería)

Los siguientes nueve caracteres son los permisos que se les concede a los usuarios del sistema.
Los caracteres que definen estos permisos son los siguientes:
Permiso 	Identifica
- 	        Sin permiso
r 	        Permiso de lectura
w 	        Permiso de escritura
x 	        Permiso de ejecución

Permisos para archivos
-- Lectura: permite, fundamentalmente, visualizar el contenido del archivo.
-- Escritura: permite modificar el contenido del archivo.
-- Ejecución: permite ejecutar el archivo como si de un programa ejecutable se tratase.

Permisos para directorios
-- Lectura: Permite saber qué archivos y directorios contiene el directorio que tiene este permiso.
-- Escritura: permite crear archivos en el directorio, bien sean archivos ordinarios o nuevos directorios.
-- Ejecución: permite situarse sobre el directorio para poder examinar su contenido, copiar archivos de o hacia él. 

Gestión de permisos en Gnu/Linux

Cuando se da de alta un usuario en el sistema, se le conceden de forma automática unos privilegios. Estos privilegios, no son totales, no dispondrán, normalmente, de los mismos permisos y derechos del superusuario. 
Cuando el usuario se crea, el sistema genera por defecto los privilegios del usuario para manejo de archivos y para manejo de directorios, que pueden ser modificados por el administrador, según lo considere conveniente.
Por lo general, son los siguientes permisos:
-- Para archivos: - rw- r-- r--
-- Para directorios: - rwx rwx rwx

Asignación de permisos
Mediante el comando chmod se pueden modificar la máscara para que se puedan realizar más o menos operaciones sobre archivos o directorios.

Parámetro 	Nivel 	   Descripción
u 	        dueño   dueño del archivo o directorio
g 	        grupo   grupo al que pertenece el archivo
o       	otros    los demás usuarios


Tipos de permiso:
Permiso 	Identifica
r 	        Permiso de lectura
w 	        Permiso de escritura
x 	        Permiso de ejecución

Dar permiso de ejecución al dueño:
$ chmod u+x archivo.sh

Quitar permiso de ejecución a todos los usuarios:
$ chmod -x archivo.sh

Dar permiso de lectura y escritura a los demás usuarios:
$ chmod o+r+w archivo.sh

Dejar solo permiso de lectura al grupo al que pertenece el archivo:
$ chmod g+r-w-x archivo.sh

Otra forma de utilizar el comando chmod, consiste en la combinación de valores de cada grupo de los usuarios forma un número octal
El bit x  es 20 es decir 1
El bit w es 21 es decir 2
El bit r  es 22 es decir 4
-- r  =  4
-- w =  2
-- x  =  1

La combinación de bits encendidos o apagados en cada grupo da ocho posibles combinaciones de valores:
Permiso 	Valor Octal 	Descripción
- - - 	0 	no se tiene ningún permiso
- - x 	1 	solo permiso de ejecución
- w - 	2 	solo permiso de escritura
- w x	3 	permisos de escritura y ejecución
r - - 	4 	solo permiso de lectura
r - x 	5 	permisos de lectura y ejecución
r w - 	6 	permisos de lectura y escritura
r w x 7 	todos los permisos establecidos, lectura, escritura y ejecución

Asi combinando los permisos del usuario, grupo y otros, se obtienen un número de tres cifras que conforman los permisos del archivo o del directorio.

Permiso 	  Valor 	Descripción
rw- --- -&#8211; 	  600  	El propietario tiene permisos de lectura y escritura
rwx --x --x   711  	El propietario lectura, escritura y ejecución, el grupo y otros solo ejecución
rwx r-x r-x   755 	        El propietario lectura, escritura y ejecución, el grupo y otros pueden leer y ejecutar el archivo
rwx rwx rwx 777 	        El archivo puede ser leído, escrito y ejecutado por quien sea
r-- --- -&#8211; 	  400   	Solo el propietario puede leer el archivo, pero ni el mismo puede modificarlo o ejecutarlo y por supuesto ni el grupo ni otros pueden hacer nada en el
rw- r-- --- 	  640  	El usuario propietario puede leer y escribir, el grupo puede leer el archivo y otros no pueden hacer nada

Expresado todo esto, se ve que es posible para un usuario establecer con cada uno de sus archivos y directorios, que es lo que pueden hacer otros usuarios.
Naturalmente, al usuario administrador nada le puede ser vedado, queda entonces, para el usuario común, cifrar sus datos, el cifrado de sus datos sería lo único que impediría al administrador tomar conocimiento de ellos, si puede disponer de ellos (moverlos, borrarlos) para eso es administrador del sistema, pero no podrá conocer su contenido.

---

