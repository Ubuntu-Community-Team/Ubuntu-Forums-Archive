---
title: "Falta libncurses4"
date: 2009-11-26
forum: Software
---

### Post by madbyte on 2009-11-26
Buenas,

Me compre una UPS y viene con un software para monitoreo, seguí las instrucciones pero el comando de estado me tira el siguiente error:

*./upsdisp: error while loading shared libraries: libncurses.so.4: cannot open shared object file: No such file or directory*

Versión de libncurses instalada:
*ls -l /lib | grep libncurse*
[I]lrwxrwxrwx  1 root root      17 2009-10-29 22:12 libncurses.so.5 -> libncurses.so.5.7
-rw-r--r--  1 root root  274360 2009-10-12 10:14 libncurses.so.5.7
lrwxrwxrwx  1 root root      18 2009-10-29 22:12 libncursesw.so.5 -> libncursesw.so.5.7
-rw-r--r--  1 root root  323640 2009-10-12 10:14 libncursesw.so.5.7[/I]

En otro post encontré que se podía solucionar haciendo:
*sudo ln -vs /lib/libncurses.so.{5,4}*

Pero me sigue dando el mismo error. Y si hago un sudo apt-get install libncurses4
me dice que no encuentra el paquete... donde puedo conseguir la librería? Viene para 64 bits?

Saludos

---

### Post by guillermolisi on 2009-11-26
Si sigue dando el mismo error luego del link, el software/script para la UPS debe estar buscando la libreria en otro path. Si pudieramos saber en que lugar la busca con hacer el mismo link pero al path correcto deberia alcanzar.

---

### Post by madbyte on 2009-11-26
No se si sirve pero este es el Readme del cd (la parte de la instalación):

   **Installation step must use root LOGIN:**
  [I]Copy upsmon.tar to /etc directory.
Use “tar xvf upsmon.tar “ to install software.
It will be created a upsmon directory.
Change to upsmon directory.

[/I]Dspues detalla como usar upsmon y upsdisp
Adjunte el archivo tar que viene en el cd.

Saludos

---

### Post by guillermolisi on 2009-11-26
Abri el tarball y tiene un script para hacer el shutdown y dos archivos binarios ejecutables.

Alguna URL del fabricante de la UPS o del software de monitoreo ?

---

### Post by madbyte on 2009-11-26
La UPS es una TRV, [http://www.trv.com.ar/](http://www.trv.com.ar/) ya entre para ver si habia alguna actualización y no tienen descarga de software, solo de manuales. El software se llama UPSMON Plus, lo usan varios fabricantes de UPS, en otro sitio encontré una versión más nueva, a ver como me va...

Saludos

Agrego:
Me funcionó la versión que encontré! Gracias!

---

### Post by madbyte on 2009-11-27
Bien... ahora estoy en otro baile... la UPS tiene una conexión serie a USB... jejeje culquier cosa posteo en hardware.

Saludos

---

