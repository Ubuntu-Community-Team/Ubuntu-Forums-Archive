---
title: "Problema con llave publica"
date: 2009-02-04
forum: Software
---

### Post by Tosh78 on 2009-02-04
Hola!
Recien arranque con Ubuntu y me tiro esto error despues de buscar actualizaciones:
W: Error de GPG: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY 60D11217247D1CFF
Alguien puede decirme como solucionar esto y que significa?

---

### Post by rojojuan on 2009-02-04
> **Tosh78 said:**
> Hola!
Recien arranque con Ubuntu y me tiro esto error despues de buscar actualizaciones:
W: Error de GPG: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY 60D11217247D1CFF
Alguien puede decirme como solucionar esto y que significa?

Esa clave corresponde al Openoffice. Fijate que aquí, en Software. esta tratado el tema "Conviene actualizar..."
Es un problema de Launchpad, que estan solucionando. Hasta aquí es lo que conozco.

---

### Post by sergiom99 on 2009-02-04
Fijate si este es tu caso:
[http://b2dbuntu.wordpress.com/2009/01/29/solucion-actualizar-las-llaves-publicas-gpg-de-launchpad-en-ubuntu/](http://b2dbuntu.wordpress.com/2009/01/29/solucion-actualizar-las-llaves-publicas-gpg-de-launchpad-en-ubuntu/)

---

### Post by Tosh78 on 2009-02-04
Gracias Sergio! Parece ser la solucion. En este momento no estoy en casa pero lo voy a probar y te cuento!

---

### Post by dox_drum on 2009-02-04
Hola, a mi me paso lo mismo y encontre la solucion en otro post que no pude encontrar nuevamente, pero aca te mando mi referencia personal

[[COLOR="Blue"]Pagina[/COLOR]]("http://sites.google.com/site/ocastillofelisola/Home/linux-stuff/updatingtherepository-list")

Espero que te sirva de ayuda.

Enjoy!

---

### Post by dox_drum on 2009-02-04
Por cierto, en el script que encontraras en mi pagina, debes cambiar donde dice ``[COLOR="Red"]intrepid[/COLOR]'' por ``[COLOR="Red"]hardy[/COLOR]'', antes de ejecutarlo, si estas corriendo Hardy en tu maquina.

Enjoy!

---

### Post by sergiom99 on 2009-02-04
> **Tosh78 said:**
> Gracias Sergio! Parece ser la solucion. En este momento no estoy en casa pero lo voy a probar y te cuento!
El link lo posteo ayer Sajnox en la lista de correos.
Yo todavia no fui para casa como para probarlo. Avisame si funca.

---

### Post by Tosh78 on 2009-02-05
Hola! Recien probe con el script que me paso Sergio, pero me da un mensaje que dice: 
cat: fullsourceslist: No existe el fichero ó directorio
cat: keyss: No existe el fichero ó directorio
rm: no se puede borrar «keyss»: No existe el fichero ó directorio
rm: no se puede borrar «fullsourceslist»: No existe el fichero ó directorio



Con el de Dox, tiro lo siguiente:

Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Paquetes recomendados
  ca-certificate
Se instalarán los siguientes paquetes NUEVOS:
  curl
0 actualizados, 1 se instalarán, 0 para eliminar y 0 no actualizados.
Necesito descargar 209kB de archivos.
Se utilizarán 324kB de espacio de disco adicional después de desempaquetar.
Des:1 [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid/main curl 7.18.2-1ubuntu4 [209kB]
Descargados 209kB en 0s (730kB/s)
Seleccionando el paquete curl previamente no seleccionado.
(Leyendo la base de datos ...  
141667 ficheros y directorios instalados actualmente.)
Desempaquetando curl (de .../curl_7.18.2-1ubuntu4_i386.deb) ...
Procesando activadores para man-db ...
Configurando curl (7.18.2-1ubuntu4) ...
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
  0     0    0     0    0     0      0      0 --:--:--  0:00:01 --:--:--     0
curl: try 'curl --help' or 'curl --manual' for more information
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
  0     0    0     0    0     0      0      0 --:--:--  0:00:01 --:--:--     0
curl: try 'curl --help' or 'curl --manual' for more information
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
  0     0    0     0    0     0      0      0 --:--:--  0:00:01 --:--:--     0
curl: try 'curl --help' or 'curl --manual' for more information

Pero hice un update un sigue tirando el mismo error de la llave publica. Alguna otra idea?
Gracias por la ayuda y la buena onda.

---

### Post by Hei Ku on 2009-02-05
tenes que correrlo desde tu home, o desde algun lugar que tengas permiso de escritura, porque crea algunos archivos temporales. Por eso los errores que tuviste y que el programa en realidad no hizo nada.

---

### Post by Tosh78 on 2009-02-08
Gracias Hei Ku, pero lo estoy corriendo desde mi home, tambien probe desde el escritorio. Alguna otra idea?

---

### Post by Hei Ku on 2009-02-08
Ese error solo deberia dartelo si en tus repos no tenes ninguno que sea launchpad. Podes postear el /etc/apt/sources.list?

---

### Post by sergiom99 on 2009-02-08
> **Hei Ku said:**
> Ese error solo deberia dartelo si en tus repos no tenes ninguno que sea launchpad. Podes postear el /etc/apt/sources.list?
Es cierto. En la laptop (Kubuntu HH) corrió sin problemas y estaba seguro que tenía repos de LP.
Ahora lo probé en la desktop (Xubuntu HH) y me tira el error que te da a vos, y comprobé que no tengo repos de LP en el sources.list.

---

### Post by Tosh78 on 2009-02-09
Si, obvio!
Aca esta el archivo:

# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid main restricted #Added by software-properties
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) intrepid main restricted
deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) intrepid restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted
deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) intrepid-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main
deb [http://ppa.launchpad.net/team-xbmc-intrepid/ubuntu](http://ppa.launchpad.net/team-xbmc-intrepid/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/team-xbmc-intrepid/ubuntu](http://ppa.launchpad.net/team-xbmc-intrepid/ubuntu) intrepid main
deb [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) intrepid main

Mil gracias por la ayuda que me estan dando!!

---

### Post by Tosh78 on 2009-02-11
Alguna idea o ayuda, gente? No me olviden! :)

---

### Post by sergiom99 on 2009-02-11
> **Tosh78 said:**
> Alguna idea o ayuda, gente? No me olviden! :)

No me olvido, pero no se que decirte. Solo llegue a la comprobación empírica de lo que habia dicho Hei Ku (Si no tenes repos de LP te da ese error)
Si lo pones en post original? (del foro en ingles, esta el link mas arriba)

---

### Post by Tosh78 on 2009-02-13
Pero en mi lista hay repositorios de launchpad. No? O estoy equivocado (que puede ser muy posible porque no hace mucho que arranque con Ubuntu).

---

### Post by sergiom99 on 2009-02-13
> **Tosh78 said:**
> Pero en mi lista hay repositorios de launchpad. No? O estoy equivocado (que puede ser muy posible porque no hace mucho que arranque con Ubuntu).

si, los ultimos 4 son de LP.

---

### Post by Tosh78 on 2009-03-06
Bueno, finalmente encontre la solucion al error de la llave publica. La posteo por si a alguien mas le sirve. Esto lo saque de una pagina que encontre googleando.

Lo único que necesitamos son los últimos 8 dígitos de la llave que nos ha dado error y utilizar el siguiente comando para agregar la llave:

gpg --keyserver subkeys.pgp.net --recv-key $Llave && gpg -a --export $PUBKRY | sudo apt-key add -

Donde $Llave son los últimos 8 dígitos de la llave errónea, por ejemplo, pongo mi propio caso:

Yo tuve los siguientes errores:

W: Error de GPG: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY 28A8205077558DD0

Entonces, solo debo fijarme en los últimos 8 dígitos de cada llave y colocarlos en el comando anterior, quedando algo como:

gpg --keyserver subkeys.pgp.net --recv-key 77558DD0 && gpg -a --export $PUBKRY | sudo apt-key add -

Para el primer repositorio y así consecutivamente hasta terminar todos, al final solo un simple

sudo apt-get update

y listo...

---

