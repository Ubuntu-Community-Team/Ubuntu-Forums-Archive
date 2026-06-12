---
title: "Jdownloader"
date: 2009-01-26
forum: Software
---

### Post by NickCis on 2009-01-26
Bueno, instale este programa como dice la guia de ubuntu [http://ubuntu-ar.org/node/210](http://ubuntu-ar.org/node/210)
Y el problema que tengo es que no me abre la pantalla para configurar, en vez de eso me abre una pantalla toda gris con el titulo "Configuration".
Ademas cuando maximizo la ventana, el tamaño de jdownloader sigue siendo el mismo, rellena el resto de ese mismo color gris (qe la ventana de configuracion).

Alguien sabe como arreglarlo?

Saludos.

---

### Post by Hei Ku on 2009-01-26
que jvm de java estas usando? Me parece que va por ahi la cosa.

---

### Post by NickCis on 2009-01-26
> **Hei Ku said:**
> que jvm de java estas usando? Me parece que va por ahi la cosa.

Perdon por mi ignorancia, pero no se como fijarme eso :S,,, Puede ser el 6 (en sistemas / Preferencias/ aparece Sun Java 6 plugin control panel)

Pd.: Jvm, es la sigla de java virtual machine, no?

Saludos.

---

### Post by Hei Ku on 2009-01-27
Pone esto, a ver qué te tira:
```

sudo update-java-alternatives -l

```

---

### Post by NickCis on 2009-01-27
Al  poner ese comando me devuelve esto

```
newpc@ubuntu-newpc:~$ sudo update-java-alternatives -l
sudo: unable to resolve host ubuntu-newpc
java-6-sun 63 /usr/lib/jvm/java-6-sun
```

Saludos.

---

### Post by EnriqueK on 2009-01-27
Primero habilitá los repositorios de medibuntu para tu versión de Ubuntu.
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
 luego ponés
sudo apt-get update
sudo apt-get install ubuntu-restricted-extras
Esto te va a instalar el java y varias otros

---

### Post by NickCis on 2009-01-27
Pero ya tengo instalados los Ubuntu-restricted extras, los instale el primer dia que instale ubuntu, y lo hice por agregar/quitar programas. Lo tengo que volver a hacer?.

Saludos.

---

### Post by Air23 on 2009-01-27
> **NickCis said:**
> Al  poner ese comando me devuelve esto

```
newpc@ubuntu-newpc:~$ sudo update-java-alternatives -l
sudo: unable to resolve host ubuntu-newpc
java-6-sun 63 /usr/lib/jvm/java-6-sun
```

Saludos.

Me parece que tenes otro problema mas alla de java. No parece muy normal el "unable to resolve host" (Si alguien que sabe mas que yo en el foro lee esto, diga si me equivoco). ¿Te salta lo mismo cuando siempre que usas sudo? Si es asi, pegale una ojeada a estos temas en los cuales esta la solucion:

[http://ubuntuforums.org/showthread.php?t=936387&highlight=unable+resolve+host](http://ubuntuforums.org/showthread.php?t=936387&highlight=unable+resolve+host)
[http://ubuntuforums.org/showthread.php?t=845815&highlight=unable+resolve+host](http://ubuntuforums.org/showthread.php?t=845815&highlight=unable+resolve+host)
[http://ubuntuforums.org/showthread.php?t=723361](http://ubuntuforums.org/showthread.php?t=723361)

---

### Post by guillermolisi on 2009-01-27
> **Air23 said:**
> Me parece que tenes otro problema mas alla de java. No parece muy normal el "unable to resolve host" (Si alguien que sabe mas que yo en el foro lee esto, diga si me equivoco). ¿Te salta lo mismo cuando siempre que usas sudo? Si es asi, pegale una ojeada a estos temas en los cuales esta la solucion:

[http://ubuntuforums.org/showthread.php?t=936387&highlight=unable+resolve+host](http://ubuntuforums.org/showthread.php?t=936387&highlight=unable+resolve+host)
[http://ubuntuforums.org/showthread.php?t=845815&highlight=unable+resolve+host](http://ubuntuforums.org/showthread.php?t=845815&highlight=unable+resolve+host)
[http://ubuntuforums.org/showthread.php?t=723361](http://ubuntuforums.org/showthread.php?t=723361)

Coincido en que es parte del problema o es otro problema que se suma.
Arreglaria primero ese del "unable to resolve host" y despues de confirmar que todo funcione bien seguiria con el resto.

---

### Post by NickCis on 2009-01-27
Listo, ya arregle el problema de "unable to...", solo pasaba cuando se usaba sudo. Link para arreglarlo: [http://mundogeek.net/archivos/2008/04/27/ubuntu-sudo-unable-to-resolve-host/](http://mundogeek.net/archivos/2008/04/27/ubuntu-sudo-unable-to-resolve-host/)

Bueno, volviendo al tema del Jdownloader, sigo sin poder usar la configuracion ni maximizar la ventana. Si hago click en configuracion, se abre una ventana con un fondo gris, que tiene el titulo "Configuration", y no hay nada, la puedo cerrar, mover, como si fuese otra ventana.

Ademas, cuando maximizo, la ventana del Jdownloader se agranda, pero el jdownloader sigue teniedo el mismo tamaño, y lo rellena con un gris.

Adjunto fotos del problema.

Edit: si ejecuto esto "sudo update-java-alternatives -l" :

```
newpc@ubuntu-newpc:~$ sudo update-java-alternatives -l
java-6-sun 63 /usr/lib/jvm/java-6-sun
newpc@ubuntu-newpc:~$
```

---

### Post by Hei Ku on 2009-01-27
Usas compiz por casualidad? Si es asi, probaste desactivarlo y ver qué pasa?

---

### Post by NickCis on 2009-01-28
> **Hei Ku said:**
> Usas compiz por casualidad? Si es asi, probaste desactivarlo y ver qué pasa?

Si, tenia los efectos visuales en normal (Sistema / preferencias / Apariencia / efectos visuales), cuando los desactivo anda perfectamente, si estan en normal o extra no anda :S, parece un bug del Jdownloader.

Desde ya muchas gracias :P.

Saludos.

---

### Post by Hei Ku on 2009-01-28
Bug de compiz en realidad. Lo mismo sucede con videos y juegos.

---

### Post by nazrysamaratin on 2009-02-11
[http://ubuntu-ar.org/node/210](http://ubuntu-ar.org/node/210) nice job, thank you
but anyone can tranlate to english.

---

