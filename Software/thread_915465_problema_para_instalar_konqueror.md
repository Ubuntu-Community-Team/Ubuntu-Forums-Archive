---
title: "problema para instalar konqueror"
date: 2008-09-09
forum: Software
---

### Post by Thalskarth on 2008-09-09
Hola gente, despues de leer tantos post sobre KDE me entró el gustito para probarlo...

asi que entre a la consola y puse 'sudo aptitude install kde'

y espere que termine todo, al terminal que tiro un error.... y note que no se habia instalado el konqueror (salia, junto a kdebase como paquete roto en synaptic).

y al poner sudo aptitude install konqueror, me devuelve este error:

```
thalskarth@thalskarth-desktop:~$ sudo aptitude install konqueror
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Leyendo la información de estado extendido       
Inicializando el estado de los paquetes... Hecho
Escribiendo información de estado extendido... Hecho
Construir la base de datos de etiquetas... Hecho     
Se instalarán los siguiente paquetes NUEVOS:
  konqueror 
Se configurarán los siguientes paquetes que están ahora parcialmente instalados:
  konqueror-nsplugins 
0 paquetes actualizados, 1 nuevos instalados, 0 para eliminar y 0 sin actualizar.
Necesito descargar 0B/1967kB de ficheros. Después de desempaquetar se usarán 5390kB.
Escribiendo información de estado extendido... Hecho
(Leyendo la base de datos ...  
164705 ficheros y directorios instalados actualmente.)
Desempaquetando konqueror (de .../konqueror_4%3a3.5.9-0ubuntu7.3_i386.deb) ...
dpkg: error al procesar /var/cache/apt/archives/konqueror_4%3a3.5.9-0ubuntu7.3_i386.deb (--unpack):
 intentando sobreescribir `/usr/share/apps/konqueror/servicemenus/media_safelyremove.desktop', que está también en el paquete kio-umountwrapper
dpkg-deb: el subproceso paste fue terminado por la señal (Tubería rota)
Se encontraron errores al procesar:
 /var/cache/apt/archives/konqueror_4%3a3.5.9-0ubuntu7.3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
Un paquete no se pudo instalar. Intentado recuperarse:
dpkg: problemas de dependencias impiden la configuración de konqueror-nsplugins:
 konqueror-nsplugins depende de konqueror; sin embargo:
  El paquete `konqueror' no está instalado.
dpkg: error al procesar konqueror-nsplugins (--configure):
 problemas de dependencias - se deja sin configurar
Se encontraron errores al procesar:
 konqueror-nsplugins
```

Como puedo hacer para solucionarlo??

---

### Post by WanderingKnight on 2008-09-09
Probá haciendo:

```
sudo aptitude dist-upgrade
```

No es nada seguro, pero el comando intenta resolver cualquier error de dependencias que se encuentre.

---

### Post by Thalskarth on 2008-09-09
> **WanderingKnight said:**
> Probá haciendo:

```
sudo aptitude dist-upgrade
```

No es nada seguro, pero el comando intenta resolver cualquier error de dependencias que se encuentre.

Me devolvio esto:```

thalskarth@thalskarth-desktop:~$ sudo aptitude dist-upgrade
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Leyendo la información de estado extendido      
Inicializando el estado de los paquetes... Hecho
Construir la base de datos de etiquetas... Hecho
Los siguientes paquetes no se usan y se ELIMINARÁN:
  kfind konqueror-nsplugins 
0 paquetes actualizados, 0 nuevos instalados, 2 para eliminar y 0 sin actualizar.
Necesito descargar 0B de ficheros. Después de desempaquetar se liberarán 1192kB.
¿Quiere continuar? [Y/n/?] y
(Leyendo la base de datos ...  
164703 ficheros y directorios instalados actualmente.)
Desinstalando konqueror-nsplugins ...
Desinstalando kfind ...
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Leyendo la información de estado extendido      
Inicializando el estado de los paquetes... Hecho
Escribiendo información de estado extendido... Hecho
Construir la base de datos de etiquetas... Hecho     
```
Solo desinstalo los paquetes que se habian instalado solos junto al itento fallido del konqueror...

---

### Post by WanderingKnight on 2008-09-09
Mm, entonces te recomiendo que vuelvas a instalar esas dos dependencias y después intentes una instalación manual del paquete ([clicky](http://packages.ubuntu.com/hardy/i386/konqueror/download)).

Se me ocurre que puede llegar a ser un problema de los repos particulares a los que apuntás (los de Argentina que en realidad no están en Argentina? xD).

---

### Post by Hei Ku on 2008-09-10
El kdebase te dio error?

Si el paquete kdebase te dio error, preocuparse porque no te instaló el konqueror (que es natural, porque toda aplicacion de kde depende de kdebase) es como que el motor del auto no arranque y te preocupes porque las gomas estan un poco bajas.

Fijate que error te da al querer instalar kdebase. Despues fijate el konqueror, que probablemente se arregle solo despues de eso.

---

### Post by WanderingKnight on 2008-09-10
Pero kdebase es un metapaquete... si falla un metapaquete es porque uno de los paquetes a los que apunta falló, y en este caso parece ser konqueror.

---

### Post by Thalskarth on 2008-09-10
> **WanderingKnight said:**
> Mm, entonces te recomiendo que vuelvas a instalar esas dos dependencias y después intentes una instalación manual del paquete ([clicky](http://packages.ubuntu.com/hardy/i386/konqueror/download)).

Se me ocurre que puede llegar a ser un problema de los repos particulares a los que apuntás (los de Argentina que en realidad no están en Argentina? xD).

He probado bajandolo 2 veces, al instalarlo por consola me devuelve el mismo error:```

thalskarth@thalskarth-desktop:~/Escritorio$ sudo dpkg -i konqueror_3.5.9-0ubuntu7_i386.deb
(Leyendo la base de datos ...  
164705 ficheros y directorios instalados actualmente.)
Desempaquetando konqueror (de konqueror_3.5.9-0ubuntu7_i386.deb) ...
dpkg: error al procesar konqueror_3.5.9-0ubuntu7_i386.deb (--install):
 intentando sobreescribir `/usr/share/apps/konqueror/servicemenus/media_safelyremove.desktop', que está también en el paquete kio-umountwrapper
dpkg-deb: el subproceso paste fue terminado por la señal (Tubería rota)
Se encontraron errores al procesar:
 konqueror_3.5.9-0ubuntu7_i386.deb
```

y al hacerle doble click encima, para intalrlo con Gdebi me dice que tengo dependencias rotas en el sistema y que ejecute el comando '*sudo apt-get install -f*' para solucionarlo.
A lo cual, me devuelve:```

thalskarth@thalskarth-desktop:~/Escritorio$ sudo apt-get install -f
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Corrigiendo dependencias... Listo
Se instalarán los siguientes paquetes extras:
  konqueror
Paquetes sugeridos:
  gij-4.1 khelpcenter konq-plugins ksvg libgcj7-awt libjessie-java
Se instalarán los siguientes paquetes NUEVOS:
  konqueror
0 actualizados, 1 se instalarán, 0 para eliminar y 0 no actualizados.
1 no instalados del todo o eliminados.
Se necesita descargar 0B/1967kB de archivos.
Se utilizarán 5390kB de espacio de disco adicional después de desempaquetar.
¿Desea continuar [S/n]? S
(Leyendo la base de datos ...  
164705 ficheros y directorios instalados actualmente.)
Desempaquetando konqueror (de .../konqueror_4%3a3.5.9-0ubuntu7.3_i386.deb) ...
dpkg: error al procesar /var/cache/apt/archives/konqueror_4%3a3.5.9-0ubuntu7.3_i386.deb (--unpack):
 intentando sobreescribir `/usr/share/apps/konqueror/servicemenus/media_safelyremove.desktop', que está también en el paquete kio-umountwrapper
dpkg-deb: el subproceso paste fue terminado por la señal (Tubería rota)
Se encontraron errores al procesar:
 /var/cache/apt/archives/konqueror_4%3a3.5.9-0ubuntu7.3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```


Y con respecto a lo del kdebase, al reinstalarlo tampoco anduvo, ya que me devolvio estos errores (ente medio habia mas líneas pero no decian errores):

```
Desempaquetando konqueror (de .../konqueror_4%3a3.5.9-0ubuntu7.3_i386.deb) ...
dpkg: error al procesar /var/cache/apt/archives/konqueror_4%3a3.5.9-0ubuntu7.3_i386.deb (--unpack):
 intentando sobreescribir `/usr/share/apps/konqueror/servicemenus/media_safelyremove.desktop', que está también en el paquete kio-umountwrapper
dpkg-deb: el subproceso paste fue terminado por la señal (Tubería rota)
Seleccionando el paquete kappfinder previamente no seleccionado.

Se encontraron errores al procesar:
 /var/cache/apt/archives/konqueror_4%3a3.5.9-0ubuntu7.3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
Un paquete no se pudo instalar. Intentado recuperarse:
Configurando kdepasswd (4:3.5.9-0ubuntu7.3) ...

Configurando ksysguardd (4:3.5.9-0ubuntu7.3) ...
dpkg: problemas de dependencias impiden la configuración de kdebase:
 kdebase depende de konqueror (>= 4:3.5.9-0ubuntu7.3); sin embargo:
  El paquete `konqueror' no está instalado.
dpkg: error al procesar kdebase (--configure):
 problemas de dependencias - se deja sin configurar

Configurando kdm (4:3.5.9-0ubuntu7.3) ...

dpkg: problemas de dependencias impiden la configuración de konqueror-nsplugins:
 konqueror-nsplugins depende de konqueror; sin embargo:
  El paquete `konqueror' no está instalado.
dpkg: error al procesar konqueror-nsplugins (--configure):
 problemas de dependencias - se deja sin configurar
Configurando ktip (4:3.5.9-0ubuntu7.3) ...

Configurando klipper (4:3.5.9-0ubuntu7.3) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Se encontraron errores al procesar:
 kdebase
 konqueror-nsplugins
```

O sea, siempre lo mismo :(

---

### Post by Thalskarth on 2008-09-11
Perdón por el doble post,

parece que estoy negado a poder probar el KDE :(


estuve buscando en google alguna alternativa, pero no pude encontrar nada que se solucione el drama...

---

### Post by Hei Ku on 2008-09-11
por alguna razon entraste en un dependency hell.

hace esto

sudo apt-get remove kio-umountwrapper

despues

sudo apt-get install konqueror

y despues

sudo apt-get install kio-umountwrapper

---

### Post by Thalskarth on 2008-09-12
> **Hei Ku said:**
> por alguna razon entraste en un dependency hell.

hace esto

sudo apt-get remove kio-umountwrapper

despues

sudo apt-get install konqueror

y despues

sudo apt-get install kio-umountwrapper
Probe con eso y no pude solucionarlo...


Pero les comento que mientras seguí buscando en google y al final encontré cual es el problema.

les comento que existe un bug conocido el cual impide la desinstalación del paquete kio-unmountwrapper y dicho bug todavia no fue solucionado.

Igualmente, en el mismo sitio, se comentaba una solucion práctica a fin de solucionar el inconveniente... y siguiendo eso que decian ahí, pude eliminar dicho apquete y asi podes instalar el konqueror (junto a todo el resto de KDE) sin inconvenientes.

el link directo es: [https://bugs.edge.launchpad.net/ubuntu/+source/kio-umountwrapper/+bug/186729](https://bugs.edge.launchpad.net/ubuntu/+source/kio-umountwrapper/+bug/186729)


Saludos y gracias a todos por la ayuda :)

---

