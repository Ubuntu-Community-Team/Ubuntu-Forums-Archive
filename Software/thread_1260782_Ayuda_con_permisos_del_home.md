---
title: "Ayuda con permisos del home"
date: 2009-09-08
forum: Software
---

### Post by guisheca on 2009-09-08
Que tal comunidad, en otro post escribí que estoy pasando mis particiones a ext4. Ya hice respaldo de todos mis datos, pero tengo una duda y necesito por favor de su ayuda ya que en este tema siempre tuve problemas.

El tema de los permisos. Como root hice el respaldo de todos mis datos en una partición aparte. Luego de hacer esto todos los archivos y carpetas pasaron a pertenecer a root, como es de esperarse.

Como siempre anduve metiendole mano al tema de los permisos mi home siempre es un desastre en cuanto a permisos, y nunca hubo un comando que me solucionara las cosas, he leído todo acerca de chmod y demás pero siempre es un desastre. En fin, ya que voy a formatear mi home quisiera que sus permisos estén bien de entrada.

Cuando copie todo como root (como otro usuario no puedo copiarlos, ya que copié los archivos directamente sobre otra partición, es decir, las únicas carpetas que hay en esa partición son las de mi home y eso sólo lo podía hacer como root, y no me avivé de crear una carpeta con permisos de usuario común) supongo que los archivos conservarán sus permisos sólo para root, o no?

Que permisos es conveniente que tengan las carpetas y los archivos de mi home?

Saludos.

---

### Post by z37a on 2009-09-08
> **guisheca said:**
> Que tal comunidad, en otro post escribí que estoy pasando mis particiones a ext4. Ya hice respaldo de todos mis datos, pero tengo una duda y necesito por favor de su ayuda ya que en este tema siempre tuve problemas.

El tema de los permisos. Como root hice el respaldo de todos mis datos en una partición aparte. Luego de hacer esto todos los archivos y carpetas pasaron a pertenecer a root, como es de esperarse.

Como siempre anduve metiendole mano al tema de los permisos mi home siempre es un desastre en cuanto a permisos, y nunca hubo un comando que me solucionara las cosas, he leído todo acerca de chmod y demás pero siempre es un desastre. En fin, ya que voy a formatear mi home quisiera que sus permisos estén bien de entrada.

Cuando copie todo como root (como otro usuario no puedo copiarlos, ya que copié los archivos directamente sobre otra partición, es decir, las únicas carpetas que hay en esa partición son las de mi home y eso sólo lo podía hacer como root, y no me avivé de crear una carpeta con permisos de usuario común) supongo que los archivos conservarán sus permisos sólo para root, o no?

Que permisos es conveniente que tengan las carpetas y los archivos de mi home?

Saludos.

Mas importante que los permisos es quien es el propietario de las carpetas, tendrias que iniciar en init 1(el modo de recuperacion) e ir al /home y cambiarle el propietario a las carpetas(el owner) utilizando 
chmod -R {USUARIO}:{GRUPO} /home/{USUARIO}

con esto le estas dando todo lo necesario, ya que luego como usuario podrias cambiarle los permisos a los archivos que queden ahi adentro sin usar al root.

---

### Post by biale on 2009-09-08
Aparte de lo que ya mencionó z37a (fundamental).

Frente al problema, si haces un nuevo usuario "pruebas", los permisos del árbol /home/pruebas serían de cajón los permisos recomendados. Y acordate que también existen los directorios y archivos ocultos. De última también se pueden mirar los permisos del usuario root.

Para hacer backups del home completo he usado cp -axv  y  tar sin problemas.

Saludos.

---

### Post by guisheca on 2009-09-08
@z37a, muy interesante el tip que me pasaste, no lo conocía. Entiendo que de esa manera una ves copiados los archivos a mi home le podré cambiar los permisos por mas que sean solo para root?

@biale, yo podría crear otro usuario, tal como marcás, y luego cambiarle el nombre para que sea como el anterior? (previo borrado del anterior obvio). Porque me parece una buena opción esa. Otra cosa, como combino el comando de copia que me pasaste con el tar?

Gracias a ambos por la respuesta.

Saludos.

---

### Post by Mister X on 2009-09-08
podes usar el argumento -p para copiar archivos manteniendo el propietario, permisos, timestamp, o sea haces la copia como root y te queda todo tal cual estaba

---

### Post by EnriqueK on 2009-09-08
Para conservar todos los atributos como ser permisos , propietario, etc, usa el comando **cp .ax**.
En tu lugar haría lo siguiente.
1.- Arranca con el Live Cd de Ubuntu
2.- Monta la partición donde está tu /home y la partición que contendrá la copia de carpeta de usuario.
3.- Ejecutá el siguiente comando, siempre desde el Live CD
**sudo cp -ax ruta_a_tu_carèta_de_usuario ruta_carpeta_del_respaldo**
Vuelvo a reclacar que las rutas deben estar referenciadas al Live CD.
Una forma simple de hacer lo anterior y sin tener que estar escribiendo las rutas es la siguiente
Abre un terminal y pones **cp -ax**  dejas un espacio, luego navegas en forma gráfica hasta tu carpeta de usuario y la **arrastras al terminal**, seguidamente arrastra al terminal la carpeta que contendrá la copia en la otra partición ----->Enter y Ya.
4.- Siempre desde el Live Cd ejecuta Gparted y formatea la parición /home a EXT4
5.- Repite el proceso inverso al paso 3 , osea repones la copia a tu /home
6.- Siguiendo con el Live Cd , montá la partición raiz de tu sistema , abrí como administrador el archivo **/etc/fstab** , la forma simple de hacerlo es abrir terminal y pones sudo gedit dejas un espacio y arrastras al terminal el archivo **/etc/fstab ** , luego en la linea donde figura tu /home, cambia EXT3 por EXT4.
7.- Suerte

---

### Post by biale on 2009-09-08
Podes crear otro usuario y mirar como lo creó. Lo que en principio no podes hacer es renombrarlo en forma directa.

Sucede que algunos archivos ocultos podrían hacer una referencia dura al nombre del usuario, y en ese caso quedaría el nombre del usuario anterior. Se podría buscar y sustituir, pero ya se tenés un lío mas.

Este es el script que uso para copiar particiones, desde el SystemRescueCD:

```

#!/bin/sh
##
## Copiado de arboles con opciones especiales
## ... Preservando metadatos, links duros y simbólicos, etc
##

# Copiar la raiz

  mount -t ext3  /dev/sda2 /mnt/sda2		# Montar los discos!
  mount -t ext3  /dev/sda7 /mnt/sda7		
							
  sudo cp -axv   /mnt/sda2/*     /mnt/sda7       > 1		# Bajo SysRescueCd

# Copiar el home

  mount -t ext3  /dev/sda5 /mnt/sda5		# Montar los discos!
  mount -t ext3  /dev/sda8 /mnt/sda8		
							
  sudo cp -axv   /mnt/sda5/*     /mnt/sda8       > 2		# Bajo SysRescueCd


exit

#  Resuelve OK!
#  Si NO pienso copiar todos los datos del /home, recordar que aquota.group y aquota.user
#  pertenecen al file system!


```

Y la explicación de porque la opción "-p" no alcanzaría:

cp -pRv  "./Escritorio/Instalar - Clonar/"   "/home/C/Backups"

	-R 	Recursivo
	-p 	Preservar fechas/horas, owner y permisos
	-v	Verborragico
	(faltarían las opciones "d" y "x") <<<< ---- Ojo con esto

Y luego verifico con gparted que las particiones. Los totales de archivos deberían coincidir o acercarse mucho.

Si vas a formatear el home y antes de hacerlo verificaría la posibilidad de hacer login de root en modo gráfico. Es uno de los muy pocos casos en que lo justifico. 

Saludos.

---

