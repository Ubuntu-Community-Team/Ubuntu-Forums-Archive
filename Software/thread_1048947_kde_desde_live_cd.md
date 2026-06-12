---
title: "kde desde live cd"
date: 2009-01-24
forum: Software
---

### Post by tsueseres on 2009-01-24
hola. tengo kde 3 en un live cd(kubuntu) 
y en la computadora tengo gnome instalado de un disco de ubuntu 

lo que quiero hacer es instalar el kde que viene en el disco de kubuntu

pero no ayo como lograrlo

---

### Post by Hei Ku on 2009-01-24
agrega primero el cd a tus repositorios, y despues lo instalas de ahi.
El tema es que si no son los ultimos igual los va a descargar de internet.

---

### Post by sergiom99 on 2009-01-24
> **Hei Ku said:**
> agrega primero el cd a tus repositorios, y despues lo instalas de ahi.
El tema es que si no son los ultimos igual los va a descargar de internet.

Creo que sino podes instalar directamente el escritorio kubuntu desde los repos. (pone los de brazil que van rapidisimo)
```
sudo apt-get install kubuntu-desktop
```

Suerte

---

### Post by tsueseres on 2009-01-25
hola gracias por la ayuda

pero degamos que no tuviera internet como le aria y porcierto como agrego el disco a los repocitorios

---

### Post by Hei Ku on 2009-01-25
Yo tengo KDE, asi que uso Adept, pero en Synaptics debe ser similar.
En la parte de gestionar repositorios, en Software de terceros, tiene una opcion que dice agregar CD-ROM. Ahi le pones el CD que tiene los paquetes y te lo toma como uno mas. Si tiene que instalar algo desde ahi, te lo pide.
Si Synaptics no tiene esa opcion, me fijo como agregarlo directo en el sources.list.

---

### Post by tsueseres on 2009-01-25
> **Hei Ku said:**
> Yo tengo KDE, asi que uso Adept, pero en Synaptics debe ser similar.
En la parte de gestionar repositorios, en Software de terceros, tiene una opcion que dice agregar CD-ROM. Ahi le pones el CD que tiene los paquetes y te lo toma como uno mas. Si tiene que instalar algo desde ahi, te lo pide.
Si Synaptics no tiene esa opcion, me fijo como agregarlo directo en el sources.list.

ha ok gracias

---

