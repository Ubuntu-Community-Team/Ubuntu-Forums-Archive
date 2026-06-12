---
title: "Paquetes retenidos"
date: 2008-05-31
forum: Software
---

### Post by atatiducken on 2008-05-31
hola amigos, una pequeña duda estuve buscando y no encontre porq ubuntu me retiene ciertos paquetes, miren
```
atatai@RiverPlate:~$ sudo aptitude safe-upgrade
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Leyendo la información de estado extendido      
Inicializando el estado de los paquetes... Hecho
Construir la base de datos de etiquetas... Hecho
Se han retenido los siguientes paquetes:
  openoffice.org-base-core openoffice.org-calc openoffice.org-common openoffice.org-core 
  openoffice.org-draw openoffice.org-gnome openoffice.org-gtk openoffice.org-impress 
  openoffice.org-math openoffice.org-style-human openoffice.org-writer python-uno 
0 paquetes actualizados, 0 nuevos instalados, 0 para eliminar y 12 sin actualizar.
Necesito descargar 0B de ficheros. Después de desempaquetar se usarán 0B.
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Leyendo la información de estado extendido      
Inicializando el estado de los paquetes... Hecho
Construir la base de datos de etiquetas... Hecho
```

Quisiera saber porq los retiene, si es por problemas de dependencias, por conflictos, etc, y como hago para q no me los retenga y poder instalarlos, sigo googleando, espero su ayuda
saludos y gracias

---

### Post by atatiducken on 2008-05-31
busque un poco y son problemas de dependencia, tb debe desinstalar otras cosas para poder hacerlo, con un ```
sudo aptitude full-upgrade
```  me tira esto
```
atatai@RiverPlate:~$ sudo aptitude full-upgrade
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Leyendo la información de estado extendido      
Inicializando el estado de los paquetes... Hecho
Construir la base de datos de etiquetas... Hecho
Los siguientes paquetes están ROTOS:
  openoffice.org-l10n-en-gb openoffice.org-l10n-en-za openoffice.org-l10n-es 
Se actualizarán los siguientes paquetes:
  openoffice.org-base-core openoffice.org-calc openoffice.org-common openoffice.org-core openoffice.org-draw 
  openoffice.org-gnome openoffice.org-gtk openoffice.org-impress openoffice.org-math openoffice.org-style-human 
  openoffice.org-writer python-uno 
12 paquetes actualizados, 0 nuevos instalados, 0 para eliminar y 0 sin actualizar.
Necesito descargar 53,5MB de ficheros. Después de desempaquetar se liberarán 791kB.
No se satisfacen las dependencias de los siguientes paquetes:
  openoffice.org-l10n-en-gb: Entra en conflicto: openoffice.org-core (>= 1:2.4.0.1) pero se va a instalar 1:2.4.1~rc1-1ubuntu1.
  openoffice.org-l10n-en-za: Entra en conflicto: openoffice.org-core (>= 1:2.4.0.1) pero se va a instalar 1:2.4.1~rc1-1ubuntu1.
  openoffice.org-l10n-es: Depende: openoffice.org-common (< 1:2.4.0.1) pero se va a instalar 1:2.4.1~rc1-1ubuntu1. o
                                   language-support-translations-es pero no es instalable
                          Entra en conflicto: openoffice.org-core (>= 1:2.4.0.1) pero se va a instalar 1:2.4.1~rc1-1ubuntu1.
Resolving dependencies...
Las acciones siguientes resolverán estas dependencias

Eliminar los paquetes siguientes:
language-pack-en
language-pack-en-base
language-pack-gnome-en
language-pack-gnome-en-base
language-support-en
language-support-translations-en
openoffice.org-help-en-gb
openoffice.org-l10n-en-gb
openoffice.org-l10n-en-za
openoffice.org-l10n-es
thunderbird-locale-en-gb

La puntuación es 809

¿Acepta esta solución? [Y/n/q/?]
```

que hago? procedo o no, me desinstala unos pack de lenguaje en ingles asi q poco importa

---

### Post by Kantier on 2008-06-01
Lo que te pasó es que aptitude tuvo que resolver unas dependencias de paquetes (tal depende de tal, tal colisiona con tal otro y hay que desinstalarlo, pero otros dependen de ese y también hay que desinstalarlos, etc.) y hay cosas que te trató de desinstalar.

Mi consejo: mandá
```
sudo aptitude
```
en la consola y manejate con la "interfaz" del aptitude, es mucho más cómoda para resolver este tipo de temas.

---

### Post by vk-cdg on 2008-06-01
> **atatiducken said:**
> busque un poco y son problemas de dependencia, tb debe desinstalar otras cosas para poder hacerlo, con un ```
sudo aptitude full-upgrade
```  me tira esto
```
atatai@RiverPlate:~$ sudo aptitude full-upgrade
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Leyendo la información de estado extendido      
Inicializando el estado de los paquetes... Hecho
Construir la base de datos de etiquetas... Hecho
Los siguientes paquetes están ROTOS:
  openoffice.org-l10n-en-gb openoffice.org-l10n-en-za openoffice.org-l10n-es 
Se actualizarán los siguientes paquetes:
  openoffice.org-base-core openoffice.org-calc openoffice.org-common openoffice.org-core openoffice.org-draw 
  openoffice.org-gnome openoffice.org-gtk openoffice.org-impress openoffice.org-math openoffice.org-style-human 
  openoffice.org-writer python-uno 
12 paquetes actualizados, 0 nuevos instalados, 0 para eliminar y 0 sin actualizar.
Necesito descargar 53,5MB de ficheros. Después de desempaquetar se liberarán 791kB.
No se satisfacen las dependencias de los siguientes paquetes:
  openoffice.org-l10n-en-gb: Entra en conflicto: openoffice.org-core (>= 1:2.4.0.1) pero se va a instalar 1:2.4.1~rc1-1ubuntu1.
  openoffice.org-l10n-en-za: Entra en conflicto: openoffice.org-core (>= 1:2.4.0.1) pero se va a instalar 1:2.4.1~rc1-1ubuntu1.
  openoffice.org-l10n-es: Depende: openoffice.org-common (< 1:2.4.0.1) pero se va a instalar 1:2.4.1~rc1-1ubuntu1. o
                                   language-support-translations-es pero no es instalable
                          Entra en conflicto: openoffice.org-core (>= 1:2.4.0.1) pero se va a instalar 1:2.4.1~rc1-1ubuntu1.
Resolving dependencies...
Las acciones siguientes resolverán estas dependencias

Eliminar los paquetes siguientes:
language-pack-en
language-pack-en-base
language-pack-gnome-en
language-pack-gnome-en-base
language-support-en
language-support-translations-en
openoffice.org-help-en-gb
openoffice.org-l10n-en-gb
openoffice.org-l10n-en-za
openoffice.org-l10n-es
thunderbird-locale-en-gb

La puntuación es 809

¿Acepta esta solución? [Y/n/q/?]
```

que hago? procedo o no, me desinstala unos pack de lenguaje en ingles asi q poco importa


No te lo aconsejo, yo hice lo que vos mencionás arriba y me quedó todo en inglés. Cuando voy a language support me dice que no puede bajar los paquetes de español. :(

---

### Post by atatiducken on 2008-06-01
gracias kantier y vk-cdg, pero ya lo hice y tengo el mismo problema jeje, quedo todo en ingles, pero no importa.
Alguien sabe como hacer para q me remarque los errores openoffice, porq no lo hace, saludos

---

### Post by faktorqm on 2008-06-01
Yo creo que lo mejor es hacer ```
sudo apt-get install -f
``` y una vez todo solucionado, hacer ```
sudo apt-get autoremove
``` y luego, instalar los paquetes que queres. Salu2!

---

### Post by atatiducken on 2008-06-01
Acaban de actualizar los paquetes y ya se puede instalar los idiomas, asi q todo joya, gracias faktorqm igual :D
Para los q tenian problema con la revision de ortografia como yo en openoffice la solucion es instalar el paquete **myspell-es** y listo, ya te marca los errores en rojo
```
sudo aptitude install myspell-es
```
saludos

---

