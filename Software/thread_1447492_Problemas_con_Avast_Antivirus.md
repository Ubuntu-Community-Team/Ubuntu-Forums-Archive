---
title: "Problemas con Avast Antivirus"
date: 2010-04-05
forum: Software
---

### Post by asterix77 on 2010-04-05
Hace 8 meses aproximadamente, instalé avast antivirus en mi laptop AMD64 (con Ubuntu 9.10), siguiendo las instrucciones en el siguiente enlace: [http://www.tecnohispanos.com/principal/2010/01/25/como-instalar-avast-4-para-linux-en-ubuntu-9-10/](http://www.tecnohispanos.com/principal/2010/01/25/como-instalar-avast-4-para-linux-en-ubuntu-9-10/) . Todo esto porque solo está disponible para arquitecturas de 32 bit. 

No tuve mayores inconvenientes, se actualizaba en forma automática, y me funcionaba a la perfección, eso hasta ayer en que como de costumbre descargó actualizaciones y se cerró tras la actualziación. Ahora al ejecutarlo me aparece el siguiente mensaje "An error occured in avast! engine: Argumento inválido"

Al ejecutarlo por consola aparece lo siguiente:

#avastgui

/usr/lib/gio/modules/libgiogconf.so: clase ELF errónea: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgiogconf.so
/usr/lib/gio/modules/libgioremote-volume-monitor.so: clase ELF errónea: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgioremote-volume-monitor.so
/usr/lib/gio/modules/libgvfsdbus.so: clase ELF errónea: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgvfsdbus.so

Desinstalé todo y volví a reinstalarlo, pero sigue apareciendo el mensaje de error.


Alguna idea del porqué sucede esto?

---

### Post by Carlos C on 2010-04-05
Hola. Por favor recuerda publicar tus dudas en el subforo adecuado. Este problema debieras haberlo planteado en "Software", razón por la que lo he movido. Cuando tengas dudas puedes leer [esto]("http://ubuntuforums.org/showthread.php?t=1319475").

Creo que tu problema se relaciona con esto:

[http://ubuntuforums.org/showpost.php?p=9077547&postcount=40](http://ubuntuforums.org/showpost.php?p=9077547&postcount=40)

Saludos.

---

### Post by asterix77 on 2010-04-05
Carlos 

Intenté hacer lo sugerido, pero mi problema persiste.

Saludos

---

### Post by Carlos C on 2010-04-06
Disculpa que te lo pregunte, pero es para precisar bien lo que ocurre, lo que dices es que editaste el archivo, pero aún así el problema persiste, ¿verdad?, no es que tuvieras problemas para editar /etc/init.d/rcS.

---

### Post by asterix77 on 2010-04-06
Carlos
 
No tuve problemas en la edición del archivo. Agregué lo indicado, guardé los cambios, e intenté iniciar avast, pero me siguió arrojando el mismo error.
 
Saludos

---

### Post by asterix77 on 2010-08-11
Bueno con respecto a este tema, hace ya un buen rato que lo solucioné. No me acuerdo específicamente desde donde encontré la solución, pero si me acuerdo como realizarlo, simplemente se debe ejecutar en consola antes de ejecutar el programa lo siguiente:

#sudo sysctl -w kernel.shmmax=128000000

Y luego ejecutar avast:

Existe también una forma de que este proceso se realice en forma automática antes de lanzar avast, pero no recuerdo la página.

Saludos

---

