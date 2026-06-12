---
title: "Ubufox"
date: 2011-07-05
forum: Software
---

### Post by Lutho on 2011-07-05
Estimados, hace días que tengo un pequeño problema, relacionado con 

ubufox_0.9.1-0ubuntu0.10.04.1~mfn3_all.deb

bueno les explico, normalmente pasado unos días por medio de la consola realizo un 

$sudo aptitude upgrade

por consiguiente he estado preocupado por que me arroja el siguiente error


Desempaquetando el reemplazo de ubufox ...
dpkg: error al procesar /var/cache/apt/archives/ubufox_0.9.1-0ubuntu0.10.04.1~mfn3_all.deb (--unpack):
 intentando sobreescribir `/etc/xul-ext/ubufox.js', que está también en el paquete xul-ext-ubufox 0:0.9-0ubuntu1~mfs~lucid1


aun no he averiguado a fondo, por razón de tiempo pero esta semana trate ver a que se debe.
Expongo este tema para ver si alguien mas le ha pasado y dar una pronta solución..
saluds

---

### Post by Lutho on 2011-07-12
Cuando actualicé los repositorios en Ubuntu 10.04, Firefox pasó de la versión 4 a la 5 y con esto dejó de funcionar el paquete ubufox

Para corregir esto solo hay que eliminar el paquete xul-ext-ubufox

$sudo aptitude remove xul-ext-ubufox

esa una de las soluciones que he encontrado.

-----------------------------------------------------------------

Editando:
He seguido leyendo y he encontrado esta otra solución:
1.- busca dentro de la caché de tu sistema el paquete ubufox:
find /var/cache/apt/ -name "ubufox*"

2.- instálalo con este comando:
sudo dpkg -i --force-overwrite _path_to_ubufox_package

3.- repara las dependencias:
sudo apt-get install -f

Y listo!!

-----------------------------------------------------------------

el ultimo texto lo copie :D

saludos espero que les sirva a quienes tengan este problema
saludos!

---

