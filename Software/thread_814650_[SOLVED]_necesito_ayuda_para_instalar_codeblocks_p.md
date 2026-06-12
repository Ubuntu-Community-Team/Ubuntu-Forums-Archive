---
title: "[SOLVED] necesito ayuda para instalar code:blocks para la facu !!"
date: 2008-05-31
forum: Software
---

### Post by leonardo83 on 2008-05-31
Buenas !! estoy desesperado hace como 3 dias que vengo peleando cotra esto y la verdad ya no se que hacer, tengan en cuenta que hace poco que uso linux y no se mucho de las librearias y esas cosas.
Bue, tengo que instalar codeblocks en ubuntu 7.10, para usarlo en la facu, ya probe todo, hasta use wine (pero tenia errores) y pense en virtualbox (pero mas errores), entonces vuelvo a ver si lo puedo instalar en ubuntu :(.
segui los pasos de esta pagina [http://blog.nykc.net/?p=10]("http://blog.nykc.net/?p=10") y les digo hasta donde llegue, descargue los binarios, el paquete tar.gz al escritorio, lo descomprimi y me aparecen todos los archivitos .deb, perfecto.
Despues como hay una libreria o algo asi llamada wxWidgets descargue esos dos archivos que dice en la pagina , wxbase2.8-0_2.8.7.1-0_intel386.deb & libwxgtk2.8-0_2.8.7.1-0_intel386.deb.
El priemro lo instale ok, pero el segundo cuando quiero instalarlo me da este error
```
error: dependency is not satisfiable: libpango1.0-0
```
WTF???
como no se que pasa fui a synaptic a descargar todo loq ue se llame de esa manera, .dev,.doc, etc.
Sigue el mismo mensaje y no me deja seguir los pasos para instalar los .deb que baje.
ah, me olvide, ya habia agregado en los repositorios de codeblocks y habia activado algo parecido a una llave, que necesitaba para que funcione, y me dio OK.
Por los pasos que me aparece en esa pagina, si puedo instalar ese paquete que me da error puedo instalar despues el archivo libcodeblocks0_8.02-0ubuntu1_i386.deb, pero obviamente eso me sda error ahora pq me falta instalar wxwigets , aAAAAAAAH !!! :confused:

me pueden decir si me falta instalar algo? ya hice tantas cosas que me maree, si alguno lo tiene instalado o lo usa si me puede tirar una mano, o decirme si falta instalar algo mas, ni idea y quiero usar esta IDe en ubuntu. :(

Saludos y espero respuesta !

---

### Post by Kantier on 2008-06-01
mirando [en la página de code:blocks]("http://www.codeblocks.org/downloads/5"), lo que encuentro es que:

**1.** te tenés que bajar un *.tar.gz* con los .deb para ubuntu
**2.** hay una aclaración abajo diciendo que esos .deb necesitan la versión 2.8.7 de wxGTK la cual, según esa nota, no se encuenta en los repos de ubuntu. esa nota no está actualizada para hardy (8.04), en apt encontré esa versión de wxGTK, pero sí se aplica para gutsy (7.10) que es la versión que tenés.


**Solución 1: conseguir los paquetes de wxGTK-2.8.7**
Desde la página de downloads de wxwidgets se llega a [esta explicación (link)]("http://wiki.wxpython.org/InstallingOnUbuntuOrDebian"), que adapto (para tu caso en particular) a continuación:

1) bajar la clave criptográfica del repositorio de wxwidgets
```
wget http://apt.wxwidgets.org/key.asc | sudo apt-key add - 
```
2) agregar las siguientes líneas a **/etc/apt/sources.list**
```
# wxWidgets/wxPython repository at apt.wxwidgets.org
deb http://apt.wxwidgets.org/ gutsy-wx main
deb-src http://apt.wxwidgets.org/ gutsy-wx main
```
3) actualizar apt
```
sudo aptitude update
```
4) instalar el paquete **libwxgtk2.8-0**
```
aptitude install libwxgtk2.8-0
```
5) instalar los .deb que te bajaste de la página de code:blocks


**Solución 2: actualizar a hardy**, que no necesita nada extra para poder instalar los .deb de code:blocks (**_*OJO:*_** esta solución tiene menos palabras, pero es MUCHO más larga que la otra)



disclaimer: lo que escribí en este post es asumiendo que no hay ninguna otra dependencia molesta que no esté en los repos de gutsy. si ese es el caso, te va a saltar cuando tengas que instalar.

---

### Post by leonardo83 on 2008-06-02
gracias man!
paso lo siguiente, hice los pasos que me decis hasta donde dice 
```
aptitude install libwxgtk2.8-0
```

entionces se queda cargando y me aparece el error que tenia antes, que es...
```
root@tormentor-desktop:/home/tormentor# aptitude install libwxgtk2.8-0
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Leyendo la información de estado extendido      
Inicializando el estado de los paquetes... Hecho
Construir la base de datos de etiquetas... Hecho
Los siguientes paquetes están ROTOS:
  libwxgtk2.8-0 
1 paquetes actualizados, 0 nuevos instalados, 0 para eliminar y 0 sin actualizar.
Necesito descargar 3525kB de ficheros. Después de desempaquetar se usarán 4096B.
No se satisfacen las dependencias de los siguientes paquetes:
  libwxgtk2.8-0: Depende: libpango1.0-0 (>= 1.18.3) pero está instalado 1.18.2-0ubuntu1.
Resolving dependencies...
Las acciones siguientes resolverán estas dependencias

Desactualizar los paquetes siguientes:
libwxgtk2.8-0 [2.8.6.1-0 (gutsy-wx, now) -> 2.8.4.0-0ubuntu3 (gutsy)]

La puntuación es -9980

¿Acepta esta solución? [Y/n/q/?] n
Resolving dependencies...
Las acciones siguientes resolverán estas dependencias

Eliminar los paquetes siguientes:
amule
libwxgtk2.8-0

La puntuación es -10172

¿Acepta esta solución? [Y/n/q/?] n
Resolving dependencies...

*** No hay más soluciones disponibles ***

Las acciones siguientes resolverán estas dependencias

Eliminar los paquetes siguientes:
amule
libwxgtk2.8-0

La puntuación es -10172

¿Acepta esta solución? [Y/n/q/?] y
Los siguientes paquetes no se usan y se ELIMINARÁN:
  amule-common libcrypto++6 
Se ELIMINARÁN automáticamente los siguientes paquetes:
  amule libwxgtk2.8-0 
Se ELIMINARÁN los siguientes paquetes:
  amule libwxgtk2.8-0 
0 paquetes actualizados, 0 nuevos instalados, 4 para eliminar y 0 sin actualizar.
Necesito descargar 0B de ficheros. Después de desempaquetar se liberarán 22,2MB.
¿Quiere continuar? [Y/n/?] y
Escribiendo información de estado extendido... Hecho
(Leyendo la base de datos ...  
125150 ficheros y directorios instalados actualmente.)
Desinstalando amule ...
Desinstalando amule-common ...
Desinstalando libcrypto++6 ...
Desinstalando libwxgtk2.8-0 ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Leyendo lista de paquetes... Hecho                   
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Leyendo la información de estado extendido      
Inicializando el estado de los paquetes... Hecho
Escribiendo información de estado extendido... Hecho
Construir la base de datos de etiquetas... Hecho     
root@tormentor-desktop:/home/tormentor# 

```

voy a instalar los .deb, y charaaaaa

```
root@tormentor-desktop:/home/tormentor/Escritorio# dpkg -i codeblocks_8.02-0ubuntu1.deb
dpkg-split: error al leer codeblocks_8.02-0ubuntu1.deb: Es un directorio
dpkg: error al procesar codeblocks_8.02-0ubuntu1.deb (--install):
 el subproceso dpkg-split devolvió el código de salida de error 2
Se encontraron errores al procesar:
 codeblocks_8.02-0ubuntu1.deb

```


y ahora???????
what???
 :confused::confused::confused::confused::confused::confused: :(

---

### Post by faktorqm on 2008-06-03
Hola, primero para solucionar el desastre hacé ```
sudo apt-get install -f
``` eso te repara todos los paquetes. Te recomiendo (no recuerdo la opcion de memoria) que desinstales todo si te pregunta.

Luego de eso, proba esto a ver si te lo hace (puede ser que no):

```
sudo apt-get build-dep /ruta/a/codeblocks_8.02-0ubuntu1.deb
```

Si no anda, ahora simplemente proba de instalar el paquete que te pedia anteriormente....

```
sudo apt-get install libpango1.0-0
```

y luego instalas el .deb y nos contas como te fue. (Dale doble click al archivo para instalarlo graficamente) Salu2!!

---

### Post by leonardo83 on 2008-06-04
No se si mi pc esta realmente ****** o si no se para donde arrancar porque aun asi no se me imstala, parece que me falta un archivo, pero la carpeta que tengo en el escritorio es la descomprimida del .tar.gz!!
cuando probe las dos maneras, me aparece lo siguiente:

```
xxxx@xxxx-desktop:~$ sudo apt-get install -f
[sudo] password for xxxx:
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
0 actualizados, 0 se instalarán, 0 para eliminar y 0 no actualizados.
tormentor@tormentor-desktop:~$ sudo apt-get build-dep /Escritorio/codeblocks_8.02-0ubuntu1.deb
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
E: No se pudo encontrar un paquete de fuentes para /Escritorio/codeblocks_8.02-0ubuntu1.deb

xxxx@xxxx-desktop:~$ sudo apt-get install libpango1.0-0
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
libpango1.0-0 ya está en su versión más reciente.
0 actualizados, 0 se instalarán, 0 para eliminar y 0 no actualizados.

```

es decir, me parece que libpango ya esta, pero no encunetra un archivo...cual??????

Gracias, saludos gente :(:(:(

---

### Post by faktorqm on 2008-06-04
Esta linea esta mal:

```
sudo apt-get build-dep /Escritorio/codeblocks_8.02-0ubuntu1.deb
```

por que no existe esa ubicacion. Para ser mas correcto:

```
sudo apt-get build-dep ~/Escritorio/codeblocks_8.02-0ubuntu1.deb
```

Eso si deberia funcionarte. Si no lo hace, y como veo que ya tenes el paquete libpango, y ya ejecutaste el -f dale sin miedo al .deb a ver que pasa. Si te sigue preguntando por lo mismo, el paquete es para debian y no para ubuntu, la verdad no tengo idea de como indicarle un path al dpkg para un .deb, pero creo que seria cuestion de leer un poco el man dpkg :P

Si no lo que podés hacer (última instancia) es compilar el codeblocks vos a mano. 

Para encontrar un archivo/paquete o lo que sea podes usar:

```
whereis libpango
```

y ya. Lo mas probable es que te tire a /usr/lib, pero bueno.... Salu2!!

---

### Post by leonardo83 on 2008-06-08
Bueno, perdon por la demora, modifique esa linea como me decis y sigue igual, y al querer compilar de una tambien me aparece errro, que no encuentra dependencioa con libpango.
cuando pongo whereis libpango responde libpango: :confused:




Lamentablemente me parece que lo voy a tener que instalar en Win ME... es el unico programa que fracase estrepitosamente en instalarlo!!!
Debe ser por culpa de que usa muchas librerias o algo asi, una compañeraq ue usa Suse me dijo teclear ldconfig, pero lo aplico y la terminal no responde nada.... saludos, les dejo un abrazo a todos los que trataron de darme una mano.Gracias :(:(:(

---

### Post by faktorqm on 2008-06-08
Me instale el code blocks para ver si me pasaba lo mismo, y obviamente no ocurrio. 

Te cuento lo que me bajé yo, a ver si te ayuda.

1) Estos son los paquetes en un solo tar.gz

```
wget http://ufpr.dl.sourceforge.net/sourceforge/codeblocks/codeblocks_8.02-0ubuntu1.deb.tar.gz
```

pesa 20.2 MB.

2) Lo descomprimi en una carpeta (click derecho -> extraer aqui...)

3) Fui a la carpeta y habia varios archivos. Hice doble click sobre el que dice "libcodeblocks0_8.02-0ubuntu1_i386.deb", lo instalé. Luego sobre el que dice "codeblocks_8.02-0ubuntu1_i386.deb" y listo!! ya tenia el codeblocks instalado. Los otros supongo que seran pra hacer otras cosas, pero el "base" ya lo tenes. Tengo ubuntu 8.04. Salu2!

---

### Post by leonardo83 on 2008-06-08
1) que queres decir con que obviamente NO OCURRIO??? :mad:

2) como dije,no tengo Hardy, sino que uso Gutsy porque me la re banco y ni pienso/quiero actualizar....

3) esos son los pasos clasicos que deberia haber pasado, pero la primera libreria me tiraba esos errores que postie

4) igual YA lo instale, descargue los paquetes separados y quien sabe porque se instalo de toque, o sea, descargie libpango common, libpango no se que, wxwidgets 1.0. zarazazaza y no se que mas, al querer instalar me daba un mensaje como "hay una version mas nueva en los repositorios" o alguna pavada asi que ni me fije, le daba OK y se instaloi finalmenete desde synaptic, y no tiro mas errores de dependencias ni nada, GROSSO.

asi que igual gracias, pero que mala onda, asi no se puede, venite a tomar unos mates mientras pongo Sadus y todo bien ... eso si, trae facturas :)

Saludos..... como se pone solved?? :confused:

---

### Post by Kantier on 2008-06-08
para poner el **[solved]** tenés que editar el título del primer post... o mandarle un mensaje privado a algún mod para que edite el título del thread.

---

### Post by sajnox on 2008-06-08
Afortunadamente lo arreglaron y ya tenemos de vuelta el "Mark this thread as solved"

---

### Post by leonardo83 on 2008-06-08
gracias sax! ya lo marque de esa manera.

Un abrazo a todos. :)

---

