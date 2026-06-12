---
title: "Como mober una carpeta a un directorio de sistema !!!"
date: 2009-08-01
forum: Software
---

### Post by pelaolinux on 2009-08-01
Hola a todos !!! 
Ahora tengo otro problema ...  resulta que quiero mover una carpeta que tengo al directorio 

> /usr/share/amsn/skins

pero al mover la calpeta me aparese una ventana que dice:

Hubo un error al mover el archivo a /usr/share/amsn/skins.

y en detalles, dice:

Error al mover el archivo: Permiso denegado


.........................................

como puedo solucionar eso, para mover la carpeta sin ningún problema .... 

saludos!!!

---

### Post by robertor on 2009-08-01
Podrias hacer:

```
sudo mv /usr/share/amsn/skins /home/usuario/skins/
```

Pero OJO, no creo que sea muy recomendado hacer eso. Probablemente se te corromperá el amsn o dejara de mostrar los skins.
¿Por qué quieres mover ese directorio? ¿Que estás tratando de hacer?

Saludos!
Roberto


PD: trata de cuidar tu ortografía ;)

---

### Post by pelaolinux on 2009-08-01
> **robertor said:**
> Podrias hacer:

```
sudo mv /usr/share/amsn/skins /home/usuario/skins/
```Pero OJO, no creo que sea muy recomendado hacer eso. Probablemente se te corromperá el amsn o dejara de mostrar los skins.
¿Por qué quieres mover ese directorio? ¿Que estás tratando de hacer?

Saludos!
Roberto


PD: trata de cuidar tu ortografía ;)

 no no lo quiero mover .... lo que sucede es que quiero agregar unos skins y tengo que grabar la carpeta del skins en ese directorio !!! 
eso es lo que necesito !!! 
saludos!!!

---

### Post by moreback on 2009-08-01
En ese caso en vez de **mv** usa **cp -R**

---

### Post by pelaolinux on 2009-08-01
> **moreback said:**
> En ese caso en vez de **mv** usa **cp -R**

no me funciona nada loco !!! :/

---

### Post by augias on 2009-08-02
especificamente, el caballero quiso decir:
```
sudo cp -R /home/usuario/carpeta/donde/estan/tus/archivos/ /usr/share/amsn/skins
```


cp es para copiar 
mv es para mover
sudo te da permisos de superusuario para poder hacer cosas en /
-R es recursivo, incluye todos los archivos y subcarpetas dentro de la carpeta en cuestion. 

Eso te ayudó?

---

