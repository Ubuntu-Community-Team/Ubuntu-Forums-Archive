---
title: "xserver-common-lts-raring"
date: 2014-01-11
forum: Software
---

### Post by matachito on 2014-01-11
Hola a todos. Espero haya ubicado este post en el tema correcto.
Quiero consultarles si alguno tiene idea cómo resolver mi problema:

Actualice a Ubuntu 13.10 y desde entonces no he podido ni instalar ni remover ningún paquete/programa y constantemente tiene fallos de todo tipo. Siempre al querer hacer alguna acción (por ejemplo, sudo-apt-get autoremove), el mismo problema me aparece:
"Se encontraron errores al procesar:
 xserver-common-lts-raring"

He buscado en otros foros e intentado un par de cosas pero nada me ha funcionado. Alguno tiene idea con qué puede estar relacionado este problema y cómo lo resuelvo?

Muchas gracias a todos.

---

### Post by gmunioz on 2014-01-25
Prueba ejecutar

apt-get -f install
apt-get purge xserver-common-lts-raring

---

### Post by matachito on 2014-02-13
Hola Gabriel.
Muchas gracias por tu respuesta.
Ejecuto eso y el problema sigue sin resolverse: 

matachito@matachito-Satellite-Pro-A120:~$ sudo apt-get -f install
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Los siguientes paquetes se ELIMINARÁN:
  xserver-common-lts-raring
0 actualizados, 0 se instalarán, 1 para eliminar y 355 no actualizados.
1 no instalados del todo o eliminados.
Se liberarán 1.646 kB después de esta operación.
¿Desea continuar? [S/n] S
(Leyendo la base de datos ... 232693 ficheros o directorios instalados actualmente.)
Removing xserver-common-lts-raring (2:1.13.3-0ubuntu6~precise3) ...
Eliminando `desviación de /usr/lib/xorg/protocol.txt a /usr/lib/xorg/protocol-precise.txt por xserver-common-lts-raring'
dpkg-divert: error: renombrar obliga a sobreescribir `/usr/lib/xorg/protocol.txt' con
  un fichero distinto `/usr/lib/xorg/protocol-precise.txt', no está permitido.
dpkg: error processing package xserver-common-lts-raring (--remove):
 el subproceso instalado el script post-removal devolvió el código de salida de error 2
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by WHK on 2014-06-15
Same problem after update from ubuntu 12 to 13
```
Leyendo lista de paquetes...
Creando árbol de dependencias...
Leyendo la información de estado...
No es posible reinstalar el paquete xserver-common-lts-raring, no se puede descargar.
Los siguientes paquetes se ELIMINARÁN:
  xserver-common-lts-raring
0 actualizados, 0 se instalarán, 1 para eliminar y 1 no actualizados.
1 no instalados del todo o eliminados.
Se liberarán 1.646 kB después de esta operación.
¿Desea continuar [S/n]? (Leyendo la base de datos ...  (Leyendo la base de datos ... 5% (Leyendo la base de datos ... 10% (Leyendo la base de datos ... 15% (Leyendo la base de datos ... 20% (Leyendo la base de datos ... 25% (Leyendo la base de datos ... 30% (Leyendo la base de datos ... 35% (Leyendo la base de datos ... 40% (Leyendo la base de datos ... 45% (Leyendo la base de datos ... 50% (Leyendo la base de datos ... 55% (Leyendo la base de datos ... 60% (Leyendo la base de datos ... 65% (Leyendo la base de datos ... 70% (Leyendo la base de datos ... 75% (Leyendo la base de datos ... 80% (Leyendo la base de datos ... 85% (Leyendo la base de datos ... 90% (Leyendo la base de datos ... 95% (Leyendo la base de datos ... 100% (Leyendo la base de datos ... 309918 ficheros o directorios instalados actualmente.) 
Desinstalando xserver-common-lts-raring ... 
Eliminando `desviación de /usr/lib/xorg/protocol.txt a /usr/lib/xorg/protocol-precise.txt por xserver-common-lts-raring' 
dpkg-divert: error: renombrar obliga a sobreescribir `/usr/lib/xorg/protocol.txt' con 
  un fichero distinto `/usr/lib/xorg/protocol-precise.txt', no está permitido. 
dpkg: error al procesar xserver-common-lts-raring (--remove): 
 el subproceso instalado el script post-removal devolvió el código de salida de error 2 
Se encontraron errores al procesar: 
 xserver-common-lts-raring
```

---

### Post by WHK on 2014-06-15
Solution found in:
[https://bugs.launchpad.net/ubuntu/+source/xorg-server-lts-raring/+bug/1246384](https://bugs.launchpad.net/ubuntu/+source/xorg-server-lts-raring/+bug/1246384)

Edit as root:
/var/usr/dpkg/info/xserver-common-lts-raring.postrm or
/var/lib/dpkg/info/xserver-common-lts-raring.postrm

Comment all lines from "if" to "fi" with "#", save and run:
sudo apt-get autoremove

:)

---

