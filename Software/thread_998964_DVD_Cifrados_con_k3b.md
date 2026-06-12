---
title: "DVD Cifrados con k3b"
date: 2008-12-01
forum: Software
---

### Post by Mauro22 on 2008-12-01
Hola!!


Como andan?

A ver si me pueden dar un mano... el otro dia quise grabar un dvd y el k3b me ponia que es  un dvd cifrado y no me lo dejaba copiar. Como no tenia tiempo lo grabe con el clonedvd en winxp....


Alguien sabe? google no me pudo ayudar!!



saludos y gracias!!!

---

### Post by Hernán-Amaya on 2008-12-01
> **Mauro22 said:**
> Hola!!


Como andan?

A ver si me pueden dar un mano... el otro dia quise grabar un dvd y el k3b me ponia que es  un dvd cifrado y no me lo dejaba copiar. Como no tenia tiempo lo grabe con el clonedvd en winxp....


Alguien sabe? google no me pudo ayudar!!



saludos y gracias!!!

La mayoría de los DVD comerciales están cifrados con CSS (Content Scrambling System) para poder verlos y grabarlos tenes que instalar este paquete libdvdcss2 pero creo que no estaba en los repo

---

### Post by santiagoward2000 on 2008-12-01
> **Hernán-Amaya said:**
> La mayoría de los DVD comerciales están cifrados con CSS (Content Scrambling System) para poder verlos y grabarlos tenes que instalar este paquete libdvdcss2 pero creo que no estaba en los repo

Es verdad. Pero podés instalarlo desde los repos de Medibuntu.

---

### Post by Mauro22 on 2008-12-01
Gracias!


hice una busqueda y me da:

```

sudo apt-cache search libdvdcss2
kubuntu-restricted-extras - Commonly used restricted packages
ubuntu-restricted-extras - Commonly used restricted packages
xubuntu-restricted-extras - Commonly used restricted packages

```

El restricted lo tengo, seguire buscando...

---

### Post by juanman on 2008-12-01
libdvdcss2 sirve para ver dvds cifrados, segun tengo entendido...
K3b solo permite extraer y copiar dvds q no esten protegidos...
Para hacer una "copia de seguridad" de tus discos orginales podes usar k9copy (aunque algunas barreras de discos nuevos no las salta) o algun programa para windows con wine, como el dvdshrink (tenes q copiar algunos dll, busca en el foro q hay data), el dvdfab, etc...

Saludos

---

### Post by pachux on 2008-12-20
Estuve viendo las siguientes alrtenativas linux para clonedvd o dvdshrink que estarian en el repositorio:
k9Copy 
DVD95
OGMRip
Thoggen
qVamps
Acidrip
Kmediafactory
Todavía no probé ninguna. Si alguien tiene un dato bienvenido sea.

---

### Post by c4d0rn4 on 2008-12-20
probé dvd95 y la verdad quede disconforme.
No así con k9copy. Un dato muy importante es que debes tener instalado libdvdcss2.

Hasta donde tengo entendido, una de las últimas barreras que no salta el k9copy fue, algo así como, prohibida dado que no solo afectaba a estos programas sino también la reproducción en ciertos dvd players normales.

[http://en.wikipedia.org/wiki/ARccOS_Protection](http://en.wikipedia.org/wiki/ARccOS_Protection)

---

