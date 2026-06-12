---
title: "[SOLVED] Problema del para acceder a particion"
date: 2009-07-15
forum: Software
---

### Post by matias_tati on 2009-07-15
Hola bueno les cuento, tengo instalado el programa songbird para reproducir musica, este programa tiene una opcion interesante se puede elegir una carpeta y el programa actualiza automaticamente la biblioteca cuando se efectuan cambios en esta carpeta. Ahora que pasa cada vez que lo inicio me tira este cartel. 
[IMG]http://img352.imageshack.us/img352/3184/pantallazoerrorenvisord.png[/IMG]

Y cuando hago click en las canciones de la bibloteca no funcionan, pero que pasa lo que hago es abrir la particion con el navegador de archivos y cuando la cierro el programa comienza a funcionar. No se si me explique bien pero se debera a algun permiso de acceder a los discos rigidos? Saludos!!!!!

---

### Post by staar on 2009-07-16
me parece que es porque la partición no es montada automáticamente al inicio (por el nombre, intuyo que es una partición de Ventanas, con filesystem NTFS), podés usar el programa ntfs-config (está en los repos) para configurar el montado automático (OJO, que para que funcione tenés que tener desmontado el disco), solo especificá que el punto de montaje sea disk y el programa se encarga de crear el punto de montaje en /media y de agregar la línea al fstab...

saludos

---

### Post by matias_tati on 2009-07-16
Disculpame no entendi la parte de tener desmontado el disco. Es que soy medio paranoico pero tengo datios que me dolerian en el corazon perderlos. Y si es una particion NTFS que tenia de Windows. Que es lo recomendable en todo caso pq me da vuelta la idea por la cabeza de organizar distinto las particiones e instalar wi xp y Ubuntu de nuevo. Gracias.

---

### Post by staar on 2009-07-16
no no, nada de esto te va a afectar el contenido de las particiones...

al iniciar ubuntu, por defecto las particiones NTFS no son montadas, es decir que no son accesibles normalmente, están ahí, pero desmontadas, como un dvd fuera de la lectora, o un disquete fuera de la disquetera, al intentar acceder a ellas con el navegador de archivos, el sistema monta automáticamente esas unidades, por lo que se vuelven accesibles...

para que una partición (o cualquier filesystem) se monte al inicio, debe estar especificada en el archivo /etc/fstab, junto a varios datos más, nombre de la partición, punto de montaje (el directorio donde se monta la partición), tipo de sistema de archivos, etc.

como la sintaxis de ese archivo puede ser un poco confusa para novatos, te recomendé que uses ese programita, que lo que hace es agregar la línea correcta al fstab, la única condición que tiene es que, al momento de usarlo, la unidad tiene que estar desmontada...

para desmontar una unidad existen varias formas, por ejemplo en el navegador de archivos, en el panel lateral con los marcadores, al lado de la unidad hay un ícono de expulsar, lo presionás y se desmonta la unidad, o llendo a Equipo, haciendo click derecho sobre la unidad, y seleccionando Desmontar...

saludos

---

### Post by matias_tati on 2009-07-16
Ah buenisimo. racias lo voy a probra igual sigo creyendo que quizas me convenga reinstalar todo de cero para rganizar mejor mis particiones. No hay ningun post con recomendaciones de este tipo?

---

### Post by guillermolisi on 2009-07-16
> **matias_tati said:**
> Ah buenisimo. racias lo voy a probra igual sigo creyendo que quizas me convenga reinstalar todo de cero para rganizar mejor mis particiones. No hay ningun post con recomendaciones de este tipo?
Recomendaciones de que tipo ?

Sobre particionado tenes un thread cortito en 

[http://ubuntuforums.org/showthread.php?t=1183377&highlight=particion](http://ubuntuforums.org/showthread.php?t=1183377&highlight=particion)

y seguramente hay mas que conseguis con la funcion Search this Forum.

---

### Post by matias_tati on 2009-07-17
> **staar said:**
> me parece que es porque la partición no es montada automáticamente al inicio (por el nombre, intuyo que es una partición de Ventanas, con filesystem NTFS), podés usar el programa ntfs-config (está en los repos) para configurar el montado automático (OJO, que para que funcione tenés que tener desmontado el disco), solo especificá que el punto de montaje sea disk y el programa se encarga de crear el punto de montaje en /media y de agregar la línea al fstab...

saludos

Ntfs-config no me aparece, me aparece el mountmanager me servira ese?

---

### Post by staar on 2009-07-17
supongo que si, si el programa es para eso, pero fijate bien porque ntfs-config si está en los repos...

saludos

---

### Post by matias_tati on 2009-07-18
Este?

[IMG]http://img440.imageshack.us/img440/3985/pantallazoaadiryquitara.png[/IMG]

---

### Post by staar on 2009-07-18
ese mismo...

---

### Post by matias_tati on 2009-07-18
Me sirvio de 10 gracias!!!!

---

