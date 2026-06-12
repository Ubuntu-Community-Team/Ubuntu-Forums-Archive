---
title: "[SOLVED] Problema con los permisos de usuario (¡¿drwxrwxrwx?!)"
date: 2008-08-11
forum: Software
---

### Post by v1ncent on 2008-08-11
La cosa es así: 
Se me ocurrió sólo por curiosidad hacer un symlink de /etc y /usr/bin y ponerlo en mi home (dentro de una carpeta llamada de cualquier manera), entonces inicié nautilus con sudo y lo hice, obviamente si quería poder cambiarle el nombre o borrarlo en otro momento, tenía que poner que yo era el dueño de dichos links, entonces en vez de cambiar los permisos de a uno, seleccioné la carpeta en donde los puse, le asigné los permisos y lo apliqué a todas las carpetas que tenía dentro ... inmediatamente después el nautilus (sin *sudo*) se quedó sin el theme de iconos, como si no los encontrara, todo comenzó a funcionar mal y luego no me dejaba acceder a mi home!!

Me fijé desde la consola los permisos que tenían mis archivos, y la la mayoría tenía estos permisos: **[COLOR="Red"]drwxrwxrwx[/COLOR]**
Jamás lo había visto, busqué pero realmente no encontré el significado, lo más raro es que no lo puedo cambiar de ninguna manera... he tratado desde nautilus con permisos de root, pero pareciera como si no se aplicaran los cambios.

Ahora cada vez que inicio sección se me avisa que algunos archivos esenciales tienen mal los permisos, así que supongo que e cualquier momento me causa más problemas... habla específicamente del archivo ~/.dmrc

Realmente espero que puedan ayudarme, porque no sé si es un bug o si hice algo mal.
Puede haber pasado que al aplicarle permisos a los links (ponerme como propietario de ellos), los permisos se hubieran aplicado también a las carpetas originales?
O tal vez al cambiarle los permisos y poner 'Apply permissions to enclosed files' hice algo que no debía?

Saludos!

---

### Post by Mauro22 on 2008-08-11
No habras cambiado el grupo tambien??

Que dicen las columnas de usuario/grupo cuando haces un ls -l  ??

---

### Post by v1ncent on 2008-08-11
Sí, me equivoqué creo al cambiarle los permisos a esa carpeta en donde estaban los symlinks, pero no tenía por qué aplicarse a otros archivos fuera de esa carpeta.
Efectivamente, algunas carpetas y archivos de mi home están dentro de mi usuario obviamente, pero de mi grupo también, en vez de estar en el grupo root.

Y no me permite cambiar el grupo de muchas carpetas/archivos a la vez, hacerlo uno por uno es muy tedioso.
Una forma fácil de hacerlo desde consola?

Gracias.

---

### Post by v1ncent on 2008-08-11
Nadie?
Si saben que hice algo tremendamente **** y no se quieren gastar en decirmelo, por favor, haganlo, sólo quiero saber la causa asi no me vuelve a pasar.

---

### Post by sergiom99 on 2008-08-11
vos queres poner todos los archivos dentro de una carpeta como propiedad de root?
```
chown root.root -R /home/tuusuario/lacarpeta
```

mas data:
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

ahi tiene que estar todo. (creo)

suerte.

---

### Post by v1ncent on 2008-08-11
Bueno, no exactamente, quería que todos mis archivos fueran de mi propiedad pero dentro del grupo root... De todas formas me ayudaste, porque sólo cambié el primer root por mi usuario (del comando que me diste) e hice lo que quería.
Pero de todas maneras la gran mayoría de mis archivos siguen siendo catalogados como *drwxrwxrwx*, cuando tendría que ser *drwxr-xr-x* y eso no sé como cambiarlo.

---

### Post by sergiom99 on 2008-08-11
fijate el link que te pase. esta bueno entender como se arman los permisos.

---

### Post by faktorqm on 2008-08-12
Y... eso que queres hacer vos ahi es 755... pero estas seguro que es asi?
podrias probar de hacer ```
sudo chmod 755 -R /carpeta/
``` a ver que pasa. 
Sino, hay un post mio que un dia estaba experimentando con permisos y rompi el sistema y wander knight me explico como se restablecian uno por uno jajaja creo que era el. salu2!!

---

### Post by v1ncent on 2008-08-13
Muchas gracias a todos, sobretodo a aktorqm, ya solucioné el problema con dicho comando.

---

