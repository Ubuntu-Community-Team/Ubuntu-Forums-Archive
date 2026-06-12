---
title: "Instalación de Scilab 5.1.1 Ubuntu 8.10"
date: 2009-06-13
forum: Software
---

### Post by Fisaulerod on 2009-06-13
Hasta Ubuntu 8.10, en los repositorios sólo hay una versión de Scilab antigua (4.x.x), no sé cual habrá en Jaunty pero acá pongo como instalarlo manualmente:

En la terminal ponen lo siguiente:

```
wget http://www.scilab.org/download/5.1.1/scilab-5.1.1.bin.linux-i686.tar.gz

tar xzvf scilab-5.1.1.bin.linux-i686.tar.gz

sudo mv scilab-5.1.1/ /opt/

rm  scilab-5.1.1.bin.linux-i686.tar.gz
```

Para agregar Scilab al menu de Gnome vamos a Sistema, preferencias, menu principal (donde se editan los menús) y en educación ponemos elemento nuevo. Rellenamos cómo sigue:

Tipo: Aplicación

Nombre: Scilab 5.1.1

Comando: opt/scilab-5.1.1/bin/scilab

Para ponerle icono ponen la ruta /opt/scilab-5.1.1/share/scilab/icons/scilab.xpm. Eso.

---

### Post by moreback on 2009-06-13
En Jaunty aparece un **Scilab 5.1** con el Synaptic, por lo que es llegar e instalar!

---

### Post by Patriciologico on 2009-06-14
Para los que no sepan de que se habla (como me paso a mi) Scilab es un lenguaje de programación de alto nivel para cálculo científico.

Saludos!

---

### Post by moreback on 2009-06-14
El otro software libre que se usa es el Octave!

---

### Post by Fisaulerod on 2009-06-14
> **Patriciologico said:**
> Para los que no sepan de que se habla (como me paso a mi) Scilab es un lenguaje de programación de alto nivel para cálculo científico.

Saludos!

Sí, olvidé poner una descripción xD. Es un programa muy similar a Matlab.

---

