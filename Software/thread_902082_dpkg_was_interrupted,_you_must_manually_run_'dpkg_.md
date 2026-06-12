---
title: "dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the prob"
date: 2008-08-27
forum: Software
---

### Post by Drjoaqui on 2008-08-27
el titulo de esta nuevo thread es el problema que estoy teniendo, y se originò despues de que intentè instalar google earth en ubuntu 8.04, lo hice siguiendo unos pasos de un tutorial, al parecer estaba todo bien pero el programa no iniciaba, segui leyendo el tutorial y probè algo. la maquina se reinicio sola. luego intente corregir un problema con el amsn (no puedo conectarme) y ahi me di cuenta de que habia un problema. Cuando ubuntu me indica que hay actualizaciones disponibles, al darle la orden para instalarlas me aparece lo que pegue en el titulo:

dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

Ojala me puedan ayudar, soy nuevo en GNU/LINUX y la verdad es que estoy muy contento, es muchisimo mejor de lo que me imaginaba. La version que uso es la 8.04 de 64 bits.
Desde ya muchisimas gracias, Joaquin.

---

### Post by pablo atheist on 2008-08-27
la respuesta esta ante tus ojos
***dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. ***

escribi esto:

```
sudo dpkg --configure -a
```

---

### Post by wolfis on 2008-08-30
> **pablo atheist said:**
> la respuesta esta ante tus ojos
***dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. ***

escribi esto:

```
sudo dpkg --configure -a
```

A mi me paso algo muy similar, tenia instalado el ubuntu 7.10, y cuando decidi hacer el upgrade al 8.04 algo no quedo bien. 
a partir de alli no tenia acceso a internet, y no aparecia cargada la configuracion.
cuando ejecute la orden de mas arriba, la respuesta fue:
Configularndo locales (2.7.9-4) ...
Generating locales ...
 en AU.UTF-8 ...
y alli se quedo durante horas (literalmente, hasta que lo corte.

que me sugieren hacer?

muchas gracias
slds

---

### Post by pol666 on 2008-08-30
Linux es tu amigo ahi mismo te dijo lo que tenias que hacer

---

### Post by WanderingKnight on 2008-08-30
Voy a iniciar una mocion para que en el upstream de dpkg traduzcan ese mensaje.

En serio.

EDIT: [Dicho y hecho](https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/263089).

---

