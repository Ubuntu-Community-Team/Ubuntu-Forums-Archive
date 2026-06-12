---
title: "Aplicaciones i386 en x64"
date: 2009-05-15
forum: Software
---

### Post by JUTGtgRB7z on 2009-05-15
Hola a todos. Encontré una extensión del GIMP para emular el entorno gráfico del Photoshop. Pero cuando trato de instalar el .deb me da error de arquitectura. Lo que quería saber es que paquetes me recomiendan instalar antes de forzar la instalacion del deb. Es lo único que puedo hacer porque solo viene en esa arquitectura el paquete y no soporto tener que estar cambiando de ventana continuamente a la hora de dibujar. Gracias, espero sus respuestas.

---

### Post by guillermolisi on 2009-05-15
> **pmzerdan said:**
> Hola a todos. Encontré una extensión del GIMP para emular el entorno gráfico del Photoshop. Pero cuando trato de instalar el .deb me da error de arquitectura. Lo que quería saber es que paquetes me recomiendan instalar antes de forzar la instalacion del deb. Es lo único que puedo hacer porque solo viene en esa arquitectura el paquete y no soporto tener que estar cambiando de ventana continuamente a la hora de dibujar. Gracias, espero sus respuestas.
En teoria, maquina y SO de 64 bits deberian correr aplicaciones 32 bits sin problema alguno.

Podrias mostrarnos el mensaje que te sale al instalar ese paquete ?

Y el link de donde lo obtuviste tambien, por favor.

---

### Post by JUTGtgRB7z on 2009-05-15
> **guillermolisi said:**
> En teoria, maquina y SO de 64 bits deberian correr aplicaciones 32 bits sin problema alguno.

Podrias mostrarnos el mensaje que te sale al instalar ese paquete ?

Y el link de donde lo obtuviste tambien, por favor.

Lo bajé de la página oficial de GIMPShop, es esta:

[http://www.gimpshop.com/spanish/download.shtml]("http://www.gimpshop.com/spanish/download.shtml")

El error que me da dice exactamente esto: Error: Arquitectura incorrecta 'i386'

---

### Post by oktubrer on 2009-05-15
> **guillermolisi said:**
> En teoria, maquina y SO de 64 bits deberian correr aplicaciones 32 bits sin problema alguno.


Mmmm en mi caso al menos, con el SO de 64 bits, si quiero instalar un .deb compilado para i386 el dpkg (o el front-end gráfico de gnome que no me acuerdo como se llama) te avisa que no es compatible y aborta.

---

### Post by Hei Ku on 2009-05-15
No siempre funcionan. Tenes que instalarlos con la opcion --force-architecture

---

