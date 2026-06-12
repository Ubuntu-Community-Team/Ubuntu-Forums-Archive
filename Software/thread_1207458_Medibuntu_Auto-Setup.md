---
title: "Medibuntu Auto-Setup"
date: 2009-07-08
forum: Software
---

### Post by juancarlospaco on 2009-07-08
[B][CENTER][SIZE="6"][COLOR="Sienna"]Medibuntu Auto-Setup
[/COLOR][/SIZE][/CENTER][/B]
**[SIZE="3"]Instala automaticamente los Repositorios y las llaves de Medibuntu_ para todas _las versiones de Ubuntu.[/SIZE]**

Usa Scripts y Internet para descargar el sources.list y llaves Oficiales,
*[SIZE="1"]No toca el /etc/apt/sources.list del sistema, por defecto no instala ningun programa, solo agrega el Repositorio.[/SIZE]*

Luego usa el Icono MEDIBUNTU del menu de programas para terminar la instalacion.

[LIST]
[*]**Aplicaciones--->Otras--->Medibuntu **
[/LIST]

[CENTER][[IMG]http://www.medibuntu.org/img/medibuntu-logo.png[/IMG]]("http://tecnicoslinux.com.ar/livecd/medibuntu-repo-all-ubuntus_1_all.deb")[/CENTER]


*[SIZE="1"]Por que el procedimiento en la web esta en Ingles, requiere Linea de Comandos, es diferente para cada version, esto es mas facil.[/SIZE]*
:p

---

### Post by Cajuma on 2009-07-08
[COLOR=#444444][FONT=Verdana]Hola:[/FONT][/COLOR]
[COLOR=#444444][FONT=Verdana]Yo lo instale de la siguiente manera:[/FONT][/COLOR]
[COLOR=#444444][FONT=Verdana][/FONT][/COLOR] 
[COLOR=#444444][FONT=Verdana]Añadimos el repositorio de MEDIBUNTU:[/FONT][/COLOR]
[COLOR=#444444]sudo wget [http://www.medibuntu.org/sources.list.d/jaunty.list](http://www.medibuntu.org/sources.list.d/jaunty.list) --output-document=/etc/apt/sources.list.d/medibuntu.list[/COLOR]
[COLOR=#444444][/COLOR] 
[COLOR=#444444][COLOR=#444444][FONT=Verdana]Añadimos la clave del repositorio:
[/FONT][/COLOR][COLOR=#444444]sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update[/COLOR][/COLOR]
[COLOR=#444444][COLOR=#444444][/COLOR][/COLOR] 
[COLOR=#444444][COLOR=#444444]y desde el siguiente enlace la lista de aplicaciones disponibles. [/COLOR][/COLOR]
[COLOR=#444444][COLOR=#444444][FONT=Times New Roman][COLOR=#000000][http://packages.medibuntu.org/jaunty/index.html](http://packages.medibuntu.org/jaunty/index.html)[/COLOR][/FONT][/COLOR][/COLOR]
[COLOR=#444444][COLOR=#444444][FONT=Times New Roman][COLOR=#000000][/COLOR][/FONT][/COLOR][/COLOR] 
[COLOR=#444444][COLOR=#444444][FONT=Times New Roman][COLOR=#000000]¿ cual es la diferencia ?[/COLOR][/FONT][/COLOR][/COLOR]
[COLOR=#444444][COLOR=#444444][FONT=Times New Roman][COLOR=#000000]Gracias, por la respuesta.[/COLOR][/FONT][/COLOR][/COLOR]
[COLOR=#444444][COLOR=#444444][FONT=Times New Roman][COLOR=#000000][/COLOR][/FONT][/COLOR][/COLOR] 
[COLOR=#444444][COLOR=#444444][FONT=Times New Roman][COLOR=#000000][/COLOR][/FONT][/COLOR][/COLOR]

---

### Post by guillermolisi on 2009-07-08
> No toca el /etc/apt/sources.list del sistema, por defecto no instala ningun programa, solo agrega el Repositorio.
Si no modifica /etc/apt/sources.list, donde agrega el repositorio ?

---

### Post by staar on 2009-07-08
> **guillermolisi said:**
> Si no modifica /etc/apt/sources.list, donde agrega el repositorio ?
debe agregar algún archivo .list a la carpeta /etc/apt/sources.list.d

aunque no modifica el archivo sources.list en sí, en la práctica la lista de repositorios si cambia, es decir apt no hace diferenciación (más que en el orden de lectura) entre leer los repos desde el archivo o desde la carpeta...

saludos

---

### Post by juancarlospaco on 2009-07-08
> **guillermolisi said:**
> Si no modifica /etc/apt/sources.list, donde agrega el repositorio ?

Es como dice Staar, es un *"Best Practice" en* Linux,
tiene algunas ventajas, 
como que por ejemplo no da errores de Repo Duplicado entre otros,
o al Desinstalar, el Repo se borra limpio, 
si tocan el principal puede hacer lio, en breve es eso, 
cualquier cosa chequea la documentacion de APT.

:p

---

### Post by guillermolisi on 2009-07-08
> **juancarlospaco said:**
> Es como dice Staar, es un *"Best Practice" en* Linux,
tiene algunas ventajas, 
como que por ejemplo no da errores de Repo Duplicado entre otros,
o al Desinstalar, el Repo se borra limpio, 
si tocan el principal puede hacer lio, en breve es eso, 
cualquier cosa chequea la documentacion de APT.

:p
Excelente !

Ya agregue a mi Best Practices no solo ver el contenido de /etc/apt/sources.list sino tambien el del directorio (cuando alguien dice tener problemas de actualizaciones) por si hay archivos de repositorios que utilicen este criterio para funcionar.

Gracias !

---

### Post by juancarlospaco on 2009-07-17
[Agregado al *"Medibuntu Repository How To"* en la Wiki de Ubuntu. ]("https://help.ubuntu.com/community/Medibuntu#Links")

:)

---

### Post by User21 on 2009-07-24
En [http://appnr.com](http://appnr.com) te permiten instalar los codecs de Medibuntu mediante apt-url, como asi tambien otras aplicaciones del mismo repositorio, y de los oficiales.

---

### Post by juancarlospaco on 2009-07-25
Claro, pero tenes que hacer los mismos pasos para tener el Repositorio previamente instalado,
sino el apt:url te dice *"no se encuentra el paquete"*, 
y aunque no lo crean, mucha gente no sabe hacerlos correctamente.

---

