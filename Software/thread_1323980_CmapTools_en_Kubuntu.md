---
title: "CmapTools en Kubuntu"
date: 2009-11-12
forum: Software
---

### Post by aledruetta on 2009-11-12
Hola Comunidad!

Resulta que quiero instalar **CmapTools** en Kubuntu Karmic y no hay caso. En Gnome funciona perfectamente, tanto en versión 32 como 64 bits (bueno, en realidad, hay que cambiar Compiz por Metacity para que ande), pero en KDE, aparentemente se instala, pero al ejecutarlo, cuando pide los datos personales, la ventana de los datos se pone gris y ahí se queda "in eternum".

Para el que no conoce la aplicación, sirve para generar mapas conceptuales. Para mi gusto, es muy superior a Vym, Kdissert, Semantik, etc. Pero, lamentablemente, no está en los repositorios, hay que instalar un binario. En Gnome, todo bien, en KDE, problema...

¿Alguien tiene una idea de solución?

---

### Post by aperezb on 2010-04-03
No sé si te servirá para Kubuntu, a mi CmapTools no me funcionaba ni en Ubuntu Linux 64bits: El contenido de la ventana de edición no resultaba visible.

No he hecho nada con Compiz.

Gracias a "yothere" i "ollenotna" (a [http://ubuntuforums.org/showthread.php?t=879568](http://ubuntuforums.org/showthread.php?t=879568)) citando a "Markus" (a [https://answers.launchpad.net/ubuntu/+question/18055](https://answers.launchpad.net/ubuntu/+question/18055)) lo pude arreglar:

El CmapTools incorpora un jre en /(path_to_IHMC_CmapTools)/jre
Yo tengo el de sun java 6 instalado con synaptic, borrando (renombrando en mi caso) la carpeta jre de dentro del directorio de IHMC_CmapTools, el problema desapareció.

Sirve al menos en
CmapTools 4.16 en Ubuntu 7.10
CmapTools 5.03 and Ubuntu 9.10

Àngel Pérez

---

