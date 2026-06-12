---
title: "GRUB no aparece"
date: 2009-02-17
forum: Software
---

### Post by unsigned on 2009-02-17
Holaa, que tal?
El asunto empezó cuando estaba instalando Ubuntu 8.10 en un disco compartido con Windows. Después de creada la partición correspondiente para esta distribución de GNU/Linux, luego de comenzado el copiado de archivos, se cortó la luz. Como era de esperarse, Windows hizo una verificación de archivos automaticamente despues de prender el equipo. Ningún problema.

Inicié nuevamente el Live CD decidido a continuar la instalación. Esta vez seleccioné la forma "Manual" para reutilizar las particiones creadas antes del corte de luz (ext3 y la swap). Todo muy bien, termina de copiar los archivos sin problema, reinicio y... ¡No aparece el GRUB! ¡Arranca directamente Windows! ¿Cómo puedo reparar mi gestor de arranque?
Muchas gracias.

---

### Post by guillermolisi on 2009-02-18
> **unsigned said:**
> Holaa, que tal?
El asunto empezó cuando estaba instalando Ubuntu 8.10 en un disco compartido con Windows. Después de creada la partición correspondiente para esta distribución de GNU/Linux, luego de comenzado el copiado de archivos, se cortó la luz. Como era de esperarse, Windows hizo una verificación de archivos automaticamente despues de prender el equipo. Ningún problema.

Inicié nuevamente el Live CD decidido a continuar la instalación. Esta vez seleccioné la forma "Manual" para reutilizar las particiones creadas antes del corte de luz (ext3 y la swap). Todo muy bien, termina de copiar los archivos sin problema, reinicio y... ¡No aparece el GRUB! ¡Arranca directamente Windows! ¿Cómo puedo reparar mi gestor de arranque?
Muchas gracias.
Que version de WIndows estas usando ?
Cuantos discos tiene la PC donde estas instalando Ubuntu ?

---

### Post by unsigned on 2009-02-18
Estoy usando Windows XP SP3, y tengo 2 discos instalados; un SATA como principal y un IDE como secundario.

---

### Post by pabloatilio on 2009-02-18
> **unsigned said:**
> Holaa, que tal?
El asunto empezó cuando estaba instalando Ubuntu 8.10 en un disco compartido con Windows. Después de creada la partición correspondiente para esta distribución de GNU/Linux, luego de comenzado el copiado de archivos, se cortó la luz. Como era de esperarse, Windows hizo una verificación de archivos automaticamente despues de prender el equipo. Ningún problema.

Inicié nuevamente el Live CD decidido a continuar la instalación. Esta vez seleccioné la forma "Manual" para reutilizar las particiones creadas antes del corte de luz (ext3 y la swap). Todo muy bien, termina de copiar los archivos sin problema, reinicio y... ¡No aparece el GRUB! ¡Arranca directamente Windows! ¿Cómo puedo reparar mi gestor de arranque?
Muchas gracias.


Hay algunas formas de recuperar el GRUB por consola mediante el uso de un live CD, vas a encontrar un montón de guías con eso.

Otra opción que yo probé una vez, con un problema parecido (instalé windows 7 para probarlo por cuestiones profesionales) es utilizar auto super grub , el enlace es  : [http://www.supergrubdisk.org/wiki/AutoSuperGrubDisk](http://www.supergrubdisk.org/wiki/AutoSuperGrubDisk) , en mi caso anduvo perfecto.

Saludos

Pablo

---

### Post by guillermolisi on 2009-02-18
> **unsigned said:**
> Estoy usando Windows XP SP3, y tengo 2 discos instalados; un SATA como principal y un IDE como secundario.
Y en cual de los dos llevaste a cabo la instalacion de Ubuntu ?

---

### Post by unsigned on 2009-02-18
Ok Pablo, ahora investigo un poco.

> **guillermolisi said:**
> Y en cual de los dos llevaste a cabo la instalacion de Ubuntu ?

En el SATA

**EDITADO:** Lo pude solucionar siguiendo estos pasos: [http://mundogeek.net/archivos/2008/12/03/recuperar-grub-manualmente/](http://mundogeek.net/archivos/2008/12/03/recuperar-grub-manualmente/)
Gracias a todos

---

