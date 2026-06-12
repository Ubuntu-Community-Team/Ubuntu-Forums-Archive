---
title: "Cómo instalo Ubuntu en mi Pc?"
date: 2009-06-19
forum: Software
---

### Post by car_cma on 2009-06-19
Buenas tardes. Mi nombre es Claudio y tengo la intención de instalar Ubuntu en mi PC: AMD Duron 1100, PCChips M825VXX, 352 MB Ram (una máquina de rejunte). Actualmente funciona con Windows 2000 PRO, así que estimo que no habría problema en usar Ubuntu. El uso es hogareño (navegación, e-mails, messenger, word, excel, etc.).
Para la instalación tengo un disco rígido libre de 20 GB que lo dejaría exclusivo para Ubuntu, el disco que ya esta instalado le dejo el win 2000 (ni me gasto en instalar el XP).
La internet la tengo via Movistar 3.5G (vivo casi en el campo, no hay Speedy o Fibertel), y dado que encontré un post que explica como instalar el modem, me decidí a dejar el Windows sólo para alguna cosa específica y utilizar algo mejor (seguro que mucho mejor) todos los días.
El problema que tengo es que mi pc no tiene para grabar CD, y quería preguntarles: hay alguna forma de bajar vía internet los instaladores de Ubuntu y, sin grabar un CD, hacer la instalación?
Muchas gracias.

---

### Post by pablo.s on 2009-06-19
Si, hay una manera de
instalar Ubuntu mediante
un pendrive.
Vas a necesitar [esta imagen]("http://releases.ubuntu.com/9.04/ubuntu-9.04-desktop-i386.iso.torrent")
.ISO y además este [programa]("http://unetbootin.sourceforge.net/unetbootin-windows-latest.exe").
Cuando los tengas, con el
programita transferis la
imagen a un pendrive
(minimo 1 GB de capacidad)
y ponés en la BIOS que
arranque desde los puertos USB.

El link de la imagen ISO lo
tenés que bajar con Bit Torrent.

---

### Post by car_cma on 2009-06-19
> **pablo.s said:**
> Si, hay una manera de
instalar Ubuntu mediante
un pendrive.
Vas a necesitar [esta imagen]("http://releases.ubuntu.com/9.04/ubuntu-9.04-desktop-i386.iso.torrent")
.ISO y además este [programa]("http://unetbootin.sourceforge.net/unetbootin-windows-latest.exe").
Cuando los tengas, con el
programita transferis la
imagen a un pendrive
(minimo 1 GB de capacidad)
y ponés en la BIOS que
arranque desde los puertos USB.

El link de la imagen ISO lo
tenés que bajar con Bit Torrent.

Gracias Pablo: Acabo de chequear que mi placa me deja bootear desde el pen drive, así que no habría problema, aunque no tengo pendrive (no te olvides que vivo en el campo y mi pc es un rejunte), así que le pido a mi hermano que venga con su pendrive y listo.
Tengo varias preguntas a Pablo y extensiva al resto de los foristas:
1) La versión que me pasaste, hay posibilidad de bajarla directamente y no por .torrent? Es la más optima que hay?
2) Estuve estudiado varios post y veo que habría que particionar el disco rígido, te lo hace automáticamente el instalador o hay que hacerlo manualmente? Y en ese caso, como divido los 20 GB?
3) El Ubuntu lee datos en particiones FAT y NTFS? No es primordial, ya que para eso dejo el Win 2000, pero no deja de ser importante.
4) Con esta pregunta me van a odiar: Vi también que hay una opción de instalar desde Windows, llamada WUBI, en algunos post dicen que anda bien y en otros no la recomiendan... a tu entender, sirve??? Es muy limitada? Instalando desde el WUBI, evito instalar desde el pendrive y queda la Pc con los dos sistemas operativos instalados? Debe botearse el windows para despúes ir al Ubuntu?
Nada más por el momento y desde ya muchas gracias.

---

### Post by pablo.s on 2009-06-19
> **car_cma said:**
> 1) La versión que me pasaste, hay posibilidad de bajarla directamente y no por .torrent? Es la más optima que hay?

Si, se puede bajar por descarga
directa. Pero no se si con el
proveedor de internet 3G que tenés
la estabilidad es buena. Por mi
propia experiencia con 3G de Claro,
que corta la señal cuando pía un
pajaro, te recomiendo que lo bajes
de ser posible por bit torrent.
La razón 1 es que si cortás la bajada
(o te la corta el proveedor) no
perdés lo bajado, se puede resumir.
La razón 2 es que el protocolo
permite que los datos se chequeen al
finalizar la descarga, dando más
seguridad de que la imagen está 
integra.

> **car_cma said:**
> 2) Estuve estudiado varios post y veo que habría que particionar el disco rígido, te lo hace automáticamente el instalador o hay que hacerlo manualmente? Y en ese caso, como divido los 20 GB?

Los podés dividir asi:
para swap = 1 GB
para / = 7 GB
para /home = el resto
Y recomiendo el particionado
manual.

> **car_cma said:**
> 3) El Ubuntu lee datos en particiones FAT y NTFS? No es primordial, ya que para eso dejo el Win 2000, pero no deja de ser importante.

Si, lee de particiones FAT
de forma nativa y de NTFS
mediante un programita que
monta la partición al inicio.

> **car_cma said:**
> 4) Con esta pregunta me van a odiar: Vi también que hay una opción de instalar desde Windows, llamada WUBI, en algunos post dicen que anda bien y en otros no la recomiendan... a tu entender, sirve??? Es muy limitada? Instalando desde el WUBI, evito instalar desde el pendrive y queda la Pc con los dos sistemas operativos instalados? Debe botearse el windows para despúes ir al Ubuntu?
Nada más por el momento y desde ya muchas gracias.

No, no te vamos a odiar.
A mi entender no refleja la
verdadera esencia de Linux.
Es equivalente a andar en una
bici con rueditas. Si instalás
desde pendrive lo que evitás es
instalar desde CD o DVD.
De las dos formas quedan los 
dos sistema instalados.
Saludos y adelante!

---

### Post by car_cma on 2009-06-19
> **pablo.s said:**
> Si, se puede bajar por descarga
directa. Pero no se si con el
proveedor de internet 3G que tenés
la estabilidad es buena. Por mi
propia experiencia con 3G de Claro,
que corta la señal cuando pía un
pajaro, te recomiendo que lo bajes
de ser posible por bit torrent.
La razón 1 es que si cortás la bajada
(o te la corta el proveedor) no
perdés lo bajado, se puede resumir.
La razón 2 es que el protocolo
permite que los datos se chequeen al
finalizar la descarga, dando más
seguridad de que la imagen está 
integra.



Los podés dividir asi:
para swap = 1 GB
para / = 7 GB
para /home = el resto
Y recomiendo el particionado
manual.



Si, lee de particiones FAT
de forma nativa y de NTFS
mediante un programita que
monta la partición al inicio.



No, no te vamos a odiar.
A mi entender no refleja la
verdadera esencia de Linux.
Es equivalente a andar en una
bici con rueditas. Si instalás
desde pendrive lo que evitás es
instalar desde CD o DVD.
De las dos formas quedan los 
dos sistema instalados.
Saludos y adelante!



Te comento que tuve Claro, y acá (Pontevedra-Merlo-GBA) era malísimo. Ahora con Movistar mejoró un montón, a veces se conecta sólo Edge, pero el 90 % del tiempo anda muy bien (3.5G). Es más, tuve una notebook con Windows Vista y con Claro nunca pude actualizarla (doble castigo... el Vista y Claro)... esa Notebook se la pasé a mi cuñada (docente) y me armé esta Pc, ya que lo hago es un uso hogareño, no tenía sentido tener una notebook "de escritorio".
Por las descargas directas, en Win existen los "gestores de descarga" que aceleran, chequean integridad y hacen que no pierdas lo bajado (yo uso FlashGet).

Gracias por la aclaración, ya le escribo a mi hermano para que me traiga un pendrive y a probar. Calculo que este fin de semana lo instalo. Luego comento como fué el experimento.
Gracias.

---

