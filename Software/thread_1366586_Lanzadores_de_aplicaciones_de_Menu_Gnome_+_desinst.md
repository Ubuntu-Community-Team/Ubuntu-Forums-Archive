---
title: "Lanzadores de aplicaciones de Menu Gnome + desinstalar programas de raíz"
date: 2009-12-28
forum: Software
---

### Post by condes on 2009-12-28
INstalé el Google Earth en Ubuntu. Luego lei que para instalarlo bien no había que ejecutarlo desde el programa de instalación. Porque sino, después, tenes que ejecutarlo como super usuario. Lo desinstalé. Sin embargo, me percaté que la configuración del panel de control queda como estaba antes; lo que significa que no se desinstala todo. 
Aclaro que utilicé el comando unisntall del google para desinstalarlo (es la única forma). 

Sin embargo lo he comprobado  hay programas que, aun siendo paquetes, no se desisntalan de una forma completa; aun usando aptitude purge. Un caso es por ejemplo el Wine. Que hay que tipear el comando rm. 

POr eso quisiera que alguien explique cuales son los directorios y archivos que Ubuntu toca para instalar programas. Modicando el panel de control y la configuración del sistema. También como se hace para sacar de raíz esos programas, y como sabemos que archivos instala en el directorio Home; u otro directorio que utilice. 

Mi pregunta apunta a colaborar con Ubuntu para la estabilidad del sistema; que se nota es bastante superior a WIndows.

GRACIAS

---

### Post by moreback on 2009-12-28
No sabía que Ubuntu traía un "panel de control"... ¿cuál es ese? ¿tienes una imagen?

---

### Post by condes on 2009-12-28
Ubuntu denomina panel a lo que se encuentra por encima del escritorio. Yo agregue la palabra control. Pero me parece que se entiende. No hay necesidad de aclarar nada.

SAludos

---

### Post by juancarlospaco on 2009-12-28
Si las carpetas contienen datos algunas instalaciones no las borran,
por que asumen que pueden tener datos del usuario y no del programa,
suele ocurrir con programas propietarios, como el Google Earth,
es asi y no se puede modificar, pues no hay codigo fuente del programa para editarlo.

:)

---

### Post by condes on 2009-12-29
ESta bien. Pero mi pregunta es: ¿Que otras carpetas toca Ubuntu?

Yo instalé el google. Y la configuración del ponel no había cambiado. LO que evidencia que algo me dejó en el sector configuración (probablemente el sector etc u otro similar). ¿COmo puedo hacer para resolverlo? ¿A donde está el archivo que configura al panel?

SAludos

---

### Post by Carlos C on 2009-12-29
> Lo desinstalé. Sin embargo, me percaté que la configuración del panel de control queda como estaba antes; lo que significa que no se desinstala todo.

Creo que voy a apoyar lo que dijo moreback y también te voy a pedir una imagen, así todos entendemos lo que pasa en tu equipo y te damos un consejo rápidamente.

Saludos!

---

### Post by condes on 2009-12-29
> **Carlos C said:**
> Creo que voy a apoyar lo que dijo moreback y también te voy a pedir una imagen, así todos entendemos lo que pasa en tu equipo y te damos un consejo rápidamente.

Saludos!



[ATTACH]141663[/ATTACH]


Cuando había instalado el google me pedía instalarlo en el directorio Home. Yo quería ponerlo en OPT -que es el directorio para guardar programas privados- y lo hice. El problema fue que luego, cada vez que habría el google, instalaba los temporales en el directorio Home. Claro, no tenía autorización para hacerlo en Opt u otra carpeta. Entonces lo resolví agregando el comando sudo adelante y ejecutándolo por terminal. Escribiendo mi clave lo ejecutaba donde debía.
 Luego leí en un foro: *EL problema del Google es que no puede ejecutarse desde el instalador. Hay que salir del mismo y luego ejecutarlo normalmente. SIno se configuara mal. Y cada vez que se abre te pide  permisos de superusuario. Si el google ya está instalado hay que desinstalarlo*.
Luego, el foro, daba algunos consejos para desinstalarlo. Los seguí y funcionó. EL google trae un desinstalador propio que borra la mayoría de los archivos. AUqnue algunos tenes que borrarlos manualmente.

¿Que sucedió?

Reinstalé el google. AHora, cuando voy a configurar la pantalla principal, me encuentro con con el término sudo (que yo agregué) delante del ejecutable del google; tal como yo lo había configurado. O sea, ¿Borró todo? Evidentemente no. 

Al final, sigo ejecutándolo con el comando sudo. Lo anterior no es un problema grave. Sin embargo, me gustaría saber como eliminarlo del todo. Porque puede servir para otro programa que cause un problema similar. 
Además, y ya un poco fuera de este tema, me gustaría saber que archivos modifican los paquetes que instalas de Ubuntu. Y donde se instalan. 

GRacias

---

### Post by moreback on 2009-12-29
Los lanzadores de aplicaciones que están en los menús de GNOME están guardados en un directorio en /usr para todos los usuarios y también en el directorio /home de cada uno. Si modificas uno de los que están disponibles para todos los usuarios (como lo hiciste con el de Google Earth), entonces se guarda como copia en tu /home y prevalece sobre el primero. La cosa es que si desinstalas la aplicación de todas formas quedará el lanzador que modificaste y lo seguirás viendo.

Saludos.

---

### Post by condes on 2009-12-30
ESta bien. ESo signfica que tendría que eliminarlo de la carpeta home y usr?

QUe se guarda en esas carpetas? ¿LA configuracion de mi panel?

SAludos

---

### Post by moreback on 2009-12-30
La idea es que lo borres con el editor de menús (**Sistema -> Preferencias -> Menú principal**).

---

### Post by moreback on 2009-12-30
Por si quisieras modificar el menú de todos los usuarios ejecuta esto con Alt + F2 (primero pulsa esta combinación de teclas)

```
gksu alacarte
```

Te va a pedir confirmación con tu contraseña.

Saludos.

---

### Post by condes on 2010-01-20
Estuve de vacaciones....

Mil gracias... Ya lo solucione

---

### Post by RafaelG on 2010-01-24
Seria bueno que los Moderadores del Foro por favor Modifiquen el titulo de este Thread para futuras consultas sobre Lanzadores de aplicaciones de Menu Gnome sea mas claro conseguir una respuesta en el buscador. si no es mucha Molestia digo yo....

---

### Post by Carlos C on 2010-01-26
> **RafaelG said:**
> Seria bueno que los Moderadores del Foro por favor Modifiquen el titulo de este Thread para futuras consultas sobre Lanzadores de aplicaciones de Menu Gnome sea mas claro conseguir una respuesta en el buscador. si no es mucha Molestia digo yo....
Editado el título.

Saludos.

---

