---
title: "Cambiar disco mantenienfo la configuración de Ubuntu"
date: 2010-06-17
forum: Software
---

### Post by dam1977 on 2010-06-17
Estoy por reemplazar el viejo disco duro por uno nuevo. Pero me tomó bastante trabajo configurar el SO con toooodas las cosas que instalé (Virtualbox, Evolution, Openoffice, Elisa, etc.) ¿Hay modo de pasar la configuración de Ubuntu de un disco a otro? Creo q no, pero por las dudas pregunto....

---

### Post by luks911 on 2010-06-17
Sin saber demasiado se me ocurren dos opciones:
1) Podés usar Remastersys[0] y [1] para crear un disco de tu instalación. Luego instalar ese sistema, ya con todas las aplicaciones, en el nuevo disco y después copiar todos los datos de tu home a la nueva home.
2) La otra alternativa es Clonezilla, que te sirve para generar una imagen de tu disco actual que después pasás al nuevo disco.
Y seguro debe haber más opciones.

[0] [http://sourceforge.net/projects/remastersys/](http://sourceforge.net/projects/remastersys/)
[1] [http://www.guia-ubuntu.org/index.php?title=Remastersys](http://www.guia-ubuntu.org/index.php?title=Remastersys)
[2] [http://clonezilla.org/](http://clonezilla.org/)

---

### Post by alfplayer on 2010-06-17
Se puede usar algo como Clonezilla para pasar todo al disco nuevo.

También se puede pasar solo "la configuración" copiando /etc y los directorios home de los usuarios, pero después hay que reinstalar los programas.

Con las dos formas puede ser necesario hacer unos ajustes para que quede funcionando.

---

### Post by leonardomdq on 2010-06-17
No es por nada pero si me comprara un HD nuevo me quedaría mas tranquilo haciendo una instalación limpia del sistema y luego hago el backup de disco a disco.

---

### Post by alfplayer on 2010-06-17
Hacer la transferencia con Clonezilla no es inseguro.

---

### Post by dam1977 on 2010-07-01
Gracias a todos. Al final preferí ser drástico (aunque me llevó un poco más de tiempo): Dejé en la PC el disco viejo (solo para copiar después las fotos, la música y los archivos), configuré el BIOS para arrancar del nuevo, hice una instalación limpia en el disco nuevo, y luego con paciencia instalé y configuré todo de nuevo. Copié todos los archivos del disco viejo y listo, tutti contenti!!!! Nuevamente: gracias a todos!!

---

