---
title: "Liberar Espacio"
date: 2009-01-31
forum: Software
---

### Post by NickCis on 2009-01-31
Hola, tengo instalado ubuntu 8.04, en una aprticion de mas o menos 60gb, de los cuales home ocupa 10gb, me estoy qedando con poco espacio. Que esta ocupando los otros 40gb? (me qedan 7gb libres,,,).

Como podria liberar un poco el espacio? (soy un ex usuario de win, estoy acostumbrado que mis documentos pese mas que todo el resto de las carpetas ...)

Saludos. :P

---

### Post by Air23 on 2009-01-31
Me parece algo extraño. En mi caso siempre tuve una partición para root y una independiente para el home.

Ubuntu recién instalado ocupa alrededor de 2-3 Gb segun recuerdo y aunque le instales muchos programas es difícil que root ocupe mucho mas de 10 Gb (instalando muchas cosas)

¿Cuando decís que home ocupa 10 Gb, te fijaste en propiedades de la carpeta /home/usuario, no? Se me ocurre que te fijes cuanto ocupan las carpetas visibles de tu home (seleccionándolas todas y luego botón derecho>propiedades) para descartar que haya alguna carpeta o archivo oculto que te este comiendo todo el espacio

---

### Post by Hei Ku on 2009-01-31
Fijate en el /tmp si no hay nada extraño.
Si hubiera sido en el home, apostaba por el Tracker.

---

### Post by NickCis on 2009-02-01
Cuando digo la carpeta home, es dandole propieades a la carpeta que se llama "home" que esta en "/", esta me dice 3.376 archivos 9,6 GiB en total.

Y si le doy propiedades a "/" (sistema de archivos como sea, segundo boton sin seleccionar ninguna carpeta), me dice esto: 243.190 elementos, 50,1 GiB en total

La carpeta /tmp : me da esta info: 42 elementos, 2,9 MiB en total.

Osea, qe esta ocupando esos 40 GiB?!

Saludos...

---

### Post by SLA_leandrin on 2009-02-01
Andá a

Accesorios --> Aplicaciones --> Analizador de uso en disco

Es una herramienta excelente, te va a dar el detalle de lo que ocupa cada directorio y subdirectorio.

---

### Post by NickCis on 2009-02-01
Bueno, ahi use esa herramienta.
El problema que tengo es que esa herramienta me muestra distintas cosas que el nautilus...

Yo tengo un disco de 160gb, de los cuales una particion de 60gb esta para ubuntu,,, (es tan chica,,, por mi hermano qe me incha que le deje windows :(...) y el resto para win...

Si uso el analizador de uso del disco, sin la aprticion de win montada, me da que mi disco es de 160gb de los cuales tengo 27gb libres...

Pero si lo uso con la particion montada me da que mi disco es de 200gb, con 40gb libres...

Si veo cuanto espacio libre tengo (usando el nautilus), me dice qe en mi sistema de archivos (la partion de ubuntu) tengo 6.5Gib de espacio libre,,, y en la de Win 22.3Gib.

Osea, no se a que creerle, el nautilus me dice que tengo poco espacio libre,, mientras el otro me dice que mi aprticion tiene como 20Gib libres,, es un bug del nautilus?...

Saludos.

---

### Post by NickCis on 2009-02-01
Alguna idea?, a que le tengo que confiar?, como se realemtene cuando espacio tengo libre?....

Saludos.

---

### Post by Hei Ku on 2009-02-01
En la terminal:

df -h

---

### Post by EnriqueK on 2009-02-01
Hay varias razones que podrían explicar el incremento del espacio ocupado, el caso es que es francamente mucho, una razón que se me ocurre es que hayas estado borrado usando el entorno gráfico mediante sudo nautilus, esta operación no te borra los archivos (salvo que mantengas pulsada la tecla Shift), sino que los mada a unha papelera oculta dentro de /root.
Hacé una prueba abrí un terminal y poné separadamente
sudo rm -Rf /root/.local/share/Trash/files/*
sudo rm -Rf /root/.local/share/Trash/info/*

Sería conveniente veas como están las otras papeleras, hay varias, inclusive encontré una en directorio raíz (/.Trash) y tambén encontré otra dentro del directorio /home (/home/.Trash)

---

### Post by NickCis on 2009-02-01
Me da esto:
```
newpc@ubuntu-newpc:~$ df -h
S.ficheros            Tamaño Usado  Disp Uso% Montado en
/dev/sda2              54G   45G  6,7G  87% /
varrun                506M  124K  505M   1% /var/run
varlock               506M     0  506M   0% /var/lock
udev                  506M   44K  505M   1% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   39M  467M   8% /lib/modules/2.6.24-19-generic/volatile
gvfs-fuse-daemon       54G   45G  6,7G  87% /home/newpc/.gvfs
/dev/sda1              98G   76G   23G  78% /media/disk
newpc@ubuntu-newpc:~$ 

```

Entonces verdaderamente tengo mi particion de linux ocupada, sin saber por que, ya que mi /home pesa 8.1Gib.
Como podria liberar espacio?, o al menos saber que esta ocupando esos 30Gib?, es tan pesado ubuntu? :S

Saludos.

---

### Post by NickCis on 2009-02-02
> **EnriqueK said:**
> Hay varias razones que podrían explicar el incremento del espacio ocupado, el caso es que es francamente mucho, una razón que se me ocurre es que hayas estado borrado usando el entorno gráfico mediante sudo nautilus, esta operación no te borra los archivos (salvo que mantengas pulsada la tecla Shift), sino que los mada a unha papelera oculta dentro de /root.
Hacé una prueba abrí un terminal y poné separadamente
sudo rm -Rf /root/.local/share/Trash/files/*
sudo rm -Rf /root/.local/share/Trash/info/*

Sería conveniente veas como están las otras papeleras, hay varias, inclusive encontré una en directorio raíz (/.Trash) y tambén encontré otra dentro del directorio /home (/home/.Trash)

Era exactamente por eso,,, borre archivos siendo root (por nautilus) y lo peor era que era una pelicula de como 7 gib (los rars,,, y la peli :S),,, ahora tengo 37 Gib disponibles en el disco...

Gracias :P

---

