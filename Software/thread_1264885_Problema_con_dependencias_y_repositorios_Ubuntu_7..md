---
title: "Problema con dependencias y repositorios Ubuntu 7.04"
date: 2009-09-12
forum: Software
---

### Post by obedlink on 2009-09-12
hola

me han dado una laptop para que le reintale el windows, es algo vieja por lo que el unico ubuntu que corre desentemente es el Ubuntu 7.04, pero a la hora de instalar aplicaciones como Skype, Opera tengo problemas con las dependencias, y cuando hago un "sudo apt-get update" en consola, no puede actualizar la lista, porque algunas repositorios ya no existen o no se puede conectar.

hay alguna solución a mi problema?

---

### Post by Hei Ku on 2009-09-12
Los repositorios del 7.04 ya no estan. Por que no actualizas a algo como Xubuntu o OpenGEU?

Es cierto que el Ubuntu nuevo es un poco mas pesado, pero tenes alternativas para estar actualizado con una performance decente. El unico tema es que tenes que reinstalar, ya no podes actualizar.

---

### Post by juancarlospaco on 2009-09-12
Los Repos se mueven de Servidor estan por ahi igual pero hay que modificar todo el sources,
igualmente no vale la pena realmente.

Lo mejor es reinstalar usando el CD Minimal del 9.10, 
formateando en EXT4, 
con Kernel 2.6.31 que tiene una mejora muy importante para PC con poco recurso,
y ponerle algun desktop liviano como un gnome-core o xfce,
yo lo hice la semana pasada y me fue muy bien, 
anda mas rapido que el Windoze 98 que tenia.
:)

---

### Post by Hei Ku on 2009-09-12
Podrias postear la configuracion de tu PC para que te recomendemos la opcion mas conveniente.

---

### Post by gmunioz on 2009-09-13
Hola obe....:


Mientras piensas sobre poner una nueva 

distribución, te informo que:

Vencido el plazo de soporte, los repositorios

quedan en:

[http://old-releases.ubuntu.com](http://old-releases.ubuntu.com)

Por lo que para configurar tanto apt-get

como synaptic adept o aptitude, debes:

Editar el archivo de fuentes:

sudo gedit /etc/apt/sources.list

Cambiar el servidor por defecto para los repositorios

en tu caso serian:


```
deb http://old-releases.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://old-releases.ubuntu.com/ubuntu/ feisty-updates main restricted
deb http://old-releases.ubuntu.com/ubuntu/ feisty universe
deb-src http://old-releases.ubuntu.com/ubuntu/ feisty universe
deb http://old-releases.ubuntu.com/ubuntu/ feisty multiverse
deb-src http://old-releases.ubuntu.com/ubuntu/ feisty multiverse
deb http://old-releases.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
deb-src http://old-releases.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ feisty-security main restricted
deb-src http://old-releases.ubuntu.com/ubuntu/ feisty-security main restricted
deb http://old-releases.ubuntu.com/ubuntu/ feisty-security universe
deb-src http://old-releases.ubuntu.com/ubuntu/ feisty-security universe
deb http://old-releases.ubuntu.com/ubuntu/ feisty-security multiverse
deb-src http://old-releases.ubuntu.com/ubuntu/ feisty-security multiverse

```

Guardar y cerrar el archivo

Actualizar repositorios

sudo apt-get update

Instalar lo que se encuentre disponible

Esto sirve para todas las distribuciones de Ubuntu

obviamente hay que reemplazar feisty por lo que 

corresponda.

---

### Post by obedlink on 2009-09-13
la laptop es una HP

procesador Sempron +3000 de 800Mhz
RAM de 224MB
disco de 40GB

prove xubuntu 9.04 pero aun sigue siendo muy pesado, comparado con el ubuntu 7.04 que va como la seda.

---

### Post by josecuervo86 on 2009-09-13
Mira, una opción que se me viene a la mente es una instalación mínima con la versión Alternate de Jaunty y que luego le agregues LXDE o  en todo caso que pruebes la beta de Lubuntu.

---

