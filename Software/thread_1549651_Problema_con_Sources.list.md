---
title: "Problema con Sources.list"
date: 2010-08-10
forum: Software
---

### Post by Simontero on 2010-08-10
Bueno buscando por internet y como todo novato, comenze a colocar comandos pensando que me servian, el problema es que puse este comando:

sudo sed -i s/universe// /etc/apt/sources.list
 
    Y me tiro problemas con el Sources.list, me tira problemas con estas lineas:

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security

   me puedrian explicar por qué y como la arreglo porfavor.

---

### Post by Patriciologico on 2010-08-10
Que version de Ubuntu usas?

esas lineas indican, que son para feisty, que es una version antigua deal año 2007 y sin soporte actual. Seguro copiaste de alguna informacion antigua.

Donde dice feisty debes sustituirlo por...... Dinos la version de tu sistema para terminar la ayuda.

Saludos

---

### Post by Simontero on 2010-08-10
la ultima, la 10.04 lts

---

### Post by Patriciologico on 2010-08-10
donde dice feisty, escribe lucid

---

### Post by themasterdark on 2010-08-11
Claro todos los feisty, reemplazalos por lucid y deberia funcionar es decir...

en un terminal:

sudo gedit /etc/apt/sources.list

y cambias feisty por lucid en todas las lineas que aparezca.

luego guardas y en la misma terminal:

sudo apt-get update

si todo va bien instala lo que quieras =)

---

### Post by Simontero on 2010-08-11
Gracias por la ayuda, luego de reemplazarlo me sale esto:

Imposible obtener [http://ubuntu.tecnostore.cl/ubuntu/dists/lucid/Release.gpg](http://ubuntu.tecnostore.cl/ubuntu/dists/lucid/Release.gpg)  Algo malo sucedió resolviendo «'ubuntu.tecnostore.cl:http» (-5 - No hay dirección asociada con el nombre de host)
Imposible obtener [http://ubuntu.tecnostore.cl/ubuntu/dists/lucid/main/i18n/Translation-es.bz2](http://ubuntu.tecnostore.cl/ubuntu/dists/lucid/main/i18n/Translation-es.bz2)  Algo malo sucedió resolviendo «'ubuntu.tecnostore.cl:http» (-5 - No hay dirección asociada con el nombre de host)
Imposible obtener [http://ubuntu.tecnostore.cl/ubuntu/dists/lucid/restricted/i18n/Translation-es.bz2](http://ubuntu.tecnostore.cl/ubuntu/dists/lucid/restricted/i18n/Translation-es.bz2)  Algo malo sucedió resolviendo «'ubuntu.tecnostore.cl:http» (-5 - No hay dirección asociada con el nombre de host)
Imposible obtener [http://ubuntu.tecnostore.cl/ubuntu/dists/lucid-updates/Release.gpg](http://ubuntu.tecnostore.cl/ubuntu/dists/lucid-updates/Release.gpg)  Algo malo sucedió resolviendo «'ubuntu.tecnostore.cl:http» (-5 - No hay dirección asociada con el nombre de host)
Imposible obtener [http://ubuntu.tecnostore.cl/ubuntu/dists/lucid-updates/main/i18n/Translation-es.bz2](http://ubuntu.tecnostore.cl/ubuntu/dists/lucid-updates/main/i18n/Translation-es.bz2)  Algo malo sucedió resolviendo «'ubuntu.tecnostore.cl:http» (-5 - No hay dirección asociada con el nombre de host)
Imposible obtener [http://ubuntu.tecnostore.cl/ubuntu/dists/lucid-updates/restricted/i18n/Translation-es.bz2](http://ubuntu.tecnostore.cl/ubuntu/dists/lucid-updates/restricted/i18n/Translation-es.bz2)  Algo malo sucedió resolviendo «'ubuntu.tecnostore.cl:http» (-5 - No hay dirección asociada con el nombre de host)
Imposible obtener [http://www.getautomatix.com/apt/dists/lucid/Release.gpg](http://www.getautomatix.com/apt/dists/lucid/Release.gpg)  Algo malo sucedió resolviendo «'www.getautomatix.com:http» (-5 - No hay dirección asociada con el nombre de host)
Imposible obtener [http://www.getautomatix.com/apt/dists/lucid/main/i18n/Translation-es.bz2](http://www.getautomatix.com/apt/dists/lucid/main/i18n/Translation-es.bz2)  Algo malo sucedió resolviendo «'www.getautomatix.com:http» (-5 - No hay dirección asociada con el nombre de host)
Imposible obtener [http://ubuntu.tecnostore.cl/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ubuntu.tecnostore.cl/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  Algo malo sucedió resolviendo «'ubuntu.tecnostore.cl:http» (-5 - No hay dirección asociada con el nombre de host)
Imposible obtener [http://ubuntu.tecnostore.cl/ubuntu/dists/lucid/restricted/binary-i386/Packages.gz](http://ubuntu.tecnostore.cl/ubuntu/dists/lucid/restricted/binary-i386/Packages.gz)  Algo malo sucedió resolviendo «'ubuntu.tecnostore.cl:http» (-5 - No hay dirección asociada con el nombre de host)
Imposible obtener [http://ubuntu.tecnostore.cl/ubuntu/dists/lucid-updates/main/binary-i386/Packages.gz](http://ubuntu.tecnostore.cl/ubuntu/dists/lucid-updates/main/binary-i386/Packages.gz)  Algo malo sucedió resolviendo «'ubuntu.tecnostore.cl:http» (-5 - No hay dirección asociada con el nombre de host)
Imposible obtener [http://ubuntu.tecnostore.cl/ubuntu/dists/lucid-updates/restricted/binary-i386/Packages.gz](http://ubuntu.tecnostore.cl/ubuntu/dists/lucid-updates/restricted/binary-i386/Packages.gz)  Algo malo sucedió resolviendo «'ubuntu.tecnostore.cl:http» (-5 - No hay dirección asociada con el nombre de host)
Imposible obtener [http://archive.canonical.com/ubuntu/dists/lucid-commercial/main/binary-i386/Packages.gz](http://archive.canonical.com/ubuntu/dists/lucid-commercial/main/binary-i386/Packages.gz)  404  Not Found
Imposible obtener [http://www.getautomatix.com/apt/dists/lucid/main/binary-i386/Packages.gz](http://www.getautomatix.com/apt/dists/lucid/main/binary-i386/Packages.gz)  Algo malo sucedió resolviendo «'www.getautomatix.com:http» (-5 - No hay dirección asociada con el nombre de host)
Algunos archivos de índice no se han podido descargar, se han ignorado,
o se ha utilizado unos antiguos en su lugar.

De todas maneras cambie las lineas:

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security


 y me sigue tirando error con esas lineas.

---

### Post by themasterdark on 2010-08-11
Hola bueno mira lo mejor será que partas con sources.list limpio, con solo los repositorios oficiales de ubuntu, te lo deje adjunto.

1° Baja el documento adjunto sorces.list.txt y renombralo a sources.list 

2° copialo a /etc/apt con el siguiente comando:

sudo cp sources.list /etc/apt

3° En terminal actualiza tus repositorios

sudo apt-get update

luego instala lo que quieras

PD: el sources.list que te dejo solo tiene los repositorios de ubuntu oficiales nada más.
A medida que vallas conociendo más del sistema iras agregando mas seguro pero no copies documentos que sean muy antiguos ya que Ubuntu se actualiza dos veces por año.
Otro punto es que el documento tiene los repositorios de ubuntu de  mirror de Chile de gnucv que están funcionando muy bien.


Saludos cuentame si te fue bien saludos =)

---

### Post by Simontero on 2010-08-11
[IMG]http://a.imageshack.us/img85/5711/jesuscolega.jpg[/IMG]


No podía explicarlo de mejor manera... Muchas gracias, me sirvio caleta, ahora tengo aprender mas sobre la Sources.list y saber cuando se actualizan y donde buscarlos...

---

### Post by Fi2di2 on 2010-12-04
Saludos Muchas gracias por el post ami me sirvio de mucho :P

---

### Post by Patriciologico on 2010-12-04
> **Fi2di2 said:**
> Saludos Muchas gracias por el post ami me sirvio de mucho :P


Que bien Fi2di2 me alegro, y por cierto bienvenido a la comunidad!


Saludos!

---

