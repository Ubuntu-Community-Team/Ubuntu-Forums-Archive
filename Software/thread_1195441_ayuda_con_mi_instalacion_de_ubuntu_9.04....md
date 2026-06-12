---
title: "ayuda con mi instalacion de ubuntu 9.04..."
date: 2009-06-23
forum: Software
---

### Post by luica on 2009-06-23
Buenas tardes voy a instalar ubuntu 9.04 sobre las particiones que ya tengo de ubuntu 7.04 mis preguntas son, ¿como hago para nombrar las dos particiones /media/windows y /media/windows2 pero sin darles formato?, ¿a la particion de ubuntu 

(hda2                    Primaria         Linux ext3                       20053,24) como hago para dividirla en dos particiones una de 6 GB para "/" y otra de lo que resta para "/home"?, y por ultimo ¿ la particion correspondiente al swap la dejo como esta ?, adjunto mi disco y desde ya muchas gracias por su tiempo y perdon si la pregunta es muy basica pero no quiero correr el riesgo de perder la info que tengo en windows ya que ahi hice un buckup de todos mis archivos... saludos

 

                                            
[COLOR=#444444][FONT=Verdana, sans-serif][SIZE=1]
[/SIZE][/FONT][/COLOR]
  
   Unidad de disco: /dev/hda
 

                       Tamaño: 80026361856 bytes, 80.0 GB
 

             Cabezas: 255   Sectores por pista: 63   Cilindros: 9729
 

 

 

     Nombre      IndicadoresTipo       Tipo de S.F.     [Etiqueta]     Tamaño(MB
 

 )------------------------------------------------------------------------------
 

     hda1        Inicio    Primaria       NTFS             []                27266,81  
 

     hda2                    Primaria         Linux ext3                       20053,24
 

     hda5                    Lógica         Linux swap / Solaris               921,24
 

     hda3                    Primaria   W95 FAT32 (LBA)                  31774,26
 

                                                             Inutilizable                         8,23

---

### Post by pablo.s on 2009-06-23
> **luica said:**
> ¿como hago para nombrar las dos particiones /media/windows y /media/windows2 pero sin darles formato?, 

En el particionado manual
elegi cada partición, elegi que
tenga el mismo formato, abajo
de todo dale /media/loquequieras
y cerciorate que no la formatee.

> **luica said:**
> ¿a la particion de ubuntu  como hago para dividirla en dos particiones una de 6 GB para "/" y otra de lo que resta para "/home"?, y 

En el particionado manual borrala,
con el espacio libre hace las particiones
que quieras hacer.

> **luica said:**
> por ultimo ¿ la particion correspondiente al swap la dejo como esta ?, 

Por supuesto.

---

### Post by luica on 2009-06-24
muchas gracias pablo por ultimos solo para sacarme dudas ¿si yo dejo las particiones de wind como estan sin nombrarlas cuando arranca LILO no me lo reconoceria no? y ¿en el source.list podes agregar los mirrors de cualquier distribucion que este actualizada es decir sin sus repocitores caducados juntos con los que ya tenes?  bueno perdon si son algo tontas mis preguntas pero soy nuevo y creo que tocando y preguntando se aprende con velocidad... saludos

---

### Post by EnriqueK on 2009-06-24
Nada de mezclar lista de repositorios, lo que podrías hacer es una **"migración automatizada"** , para ello en tu instalación actual abre Synaptic-->Archivo--> Guardar selecciones como..... , marcas el casillero  "guardar el estado completo, no solo los cambios , le das un nombre y -->Guardar , esto va a generar en tu carpeta de usuario un archivo de textos plano con la lista de todos los paquetes instalados, el paso siguiente es instalar de cero Ununtu 9.04 , habilita los repositorios equivalentes a tu instalación anterior , normalmente con los habituales de Ubuntu y con los Medibuntu, es suficiente [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
Una vez recargados los índices de la nueva instalació, abre Synaptic --> Archivo --> Leer selecciones, busca y abre el archivo generado en el instalación anterior-->Pulsa Aplicar en Synaptic, acepta todo lo que te pida y comienza la descargas de paquetes para su posterior instalación , esto puede demorar bastante ya que normalmente son unos 1500 paquetes ( aprox 1.4 gigas).

---

### Post by luica on 2009-06-24
gracias enrique por la aclaracion y tu tiempo la verdad no se que tan peligroso es para tu sistema experimentar con las listas de repositorios tuve unos problemitas pero los solucione fijandome la linea del error y agregando o borrando caracteres pero como no sabia o no estaba muy seguro de lo que hacia opté por empezar a preguntar la mayoria de mis dudas antes de hacer alguna macana bueno saludos

---

### Post by luica on 2009-06-24
una ultima pregunta que se me paso... preferencia en sistema de archivo ext3 o ext4..? cual de las dos es la mas aconsejable?... gracias

---

### Post by EnriqueK on 2009-06-24
Nunca debés usar una lista de repositorios de una versióm diferente.
El método que expliqué es para una instalación de cero pero totalmente automatizada, si te fijás en el contenido del archivo generado, verás que solo diguran los nombres de los paquetes instalados sin especificar las versiones, esto es  lo que va a permitir que pueda usarse en otra versión para instalar en forma totalemte limpia y segura todos esos paquetes , siempre que los mismos figuren en los repositorios, por ejemplo si en la 7.04 tenés instalado el xmms, va a figurar en la lista de paquetes, pero no se -instalará en la 9.04 por que no figura en sus repositorios.
Usando este método ,igrçe de la 7.04 a la 8.04 y también instale ña 8.10 64 bits basado en una lista de paquetes extraída de 8.10 32 bits que me facilitó un amigo-
Todo se hace bajo el directo control de APT, por lo que el éxito está asegurado.

---

### Post by EnriqueK on 2009-06-24
Nunca debés usar una lista de repositorios de una versióm diferente.
El método que expliqué es para una instalación de cero pero totalmente automatizada, si te fijás en el contenido del archivo generado, verás que solo diguran los nombres de los paquetes instalados sin especificar las versiones, esto es  lo que va a permitir que pueda usarse en otra versión para instalar en forma totalemte limpia y segura todos esos paquetes , siempre que los mismos figuren en los repositorios, por ejemplo si en la 7.04 tenés instalado el xmms, va a figurar en la lista de paquetes, pero no se -instalará en la 9.04 por que no figura en sus repositorios.
Usando este método ,igrçe de la 7.04 a la 8.04 y también instale ña 8.10 64 bits basado en una lista de paquetes extraída de 8.10 32 bits que me facilitó un amigo-
Todo se hace bajo el directo control de APT, por lo que el éxito está asegurado.

---

### Post by luica on 2009-06-24
ya tengo mi archivo de txt plano  para mi futura **"migración automatizada"**2gb es lo maximo que soporta y las velocidades de la ram que so bueno ahora a instalar mi iso del 9.04 aproposito me tiro un error de lectura del cd al tratar de instalarlo lo grabe con brasero pero en un cd no regrabable no se usar el qemu para ver si boot bien pero con md5sum coincide todos los caracteres a si que supongo que es un error del cd lo grabare de nuevo en otro cd y pruebo saludos y nuevamente gracias    	 	 	 	 	 	 	 	 	 	  [COLOR=#000000][SIZE=3]**md5sum**[/SIZE][/COLOR]

---

### Post by luica on 2009-06-24
(2gb es lo maximo que soporta y las velocidades de la ram que so[COLOR=#000000][SIZE=3] ) perdon esto lo pegue sin querer de un texto de la facu y no me di cuenta por favor saltearlo[/SIZE][SIZE=3]
[/SIZE][/COLOR]

---

