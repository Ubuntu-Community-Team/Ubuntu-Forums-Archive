---
title: "Desinstalar Compiz---"
date: 2008-10-23
forum: Software
---

### Post by erdosain9 on 2008-10-23
Hola a todos.  Bueno, les comento que estoy usando el ubuntu 8.04 y quería poner lo de compiz... sin leer mucho al respecto me guié por una página y en la misma decía cómo instalarlo... el tema es que luego leí que hardy ya lo trae y creo que cometí un par de ******... porque al configurar un par de efectos funciona bien, pero por ejemplo me ha sacado la barra de...ehhh... como se dice, el título de ¿ventana? donde figuran los minimizar, maximizar y cerrar (toda la barra)... y por ejemplo si quiero iniciar una terminal no funciona, no me da mensaje de error sólo que pareciera cargarse pero deja una hoja en blanco sin bordes ni nada...

Por eso quería desinstalarlo para luego en limpio volver a ponerlo...

Un saludo y gracias
Erdosain9

---

### Post by erdosain9 on 2008-10-23
Bueno, voy contestándome a medias... encontré esta página:
[http://compizfusionrevolution.es/2008/06/22/compiz-fusion-git-ubuntu-hardy/](http://compizfusionrevolution.es/2008/06/22/compiz-fusion-git-ubuntu-hardy/)

Seguí los pasos... el tema es que acá

"Descarga los paquetes, el código fuente e instala (ejecútalos uno a uno):

    cd ~/Compiz
    ./makefusion packages
    ./makefusion clone
    ./makefusion install"

pues que al poner esto de: 

    cd ~/Compiz
    ./makefusion packages
    ./makefusion clone
    ./makefusion install"
la terminal me dice esto:"You must have GIT installed in order to run this script. Install git-core package".

No se supone que ya se instaló con los pasos anteriores???

de hecho si pongo "sudo apt-get install git-core libX11-xcb-dev"
la maquinola me dice:

:~/Compiz$ sudo apt-get install git-core
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
git-core ya está en su versión más reciente.
0 actualizados, 0 se instalarán, 0 para eliminar 

Saludos y gracias

---

### Post by hictio on 2008-10-23
Probaste de desinstalarlo usando Synaptic?
"System -> Administration -> Synaptic Package Manager"

Buscalo con la funcion, en la cajita de Search, y desinstalo.

Otra cosa, no probaste de deshabilitarlo? Digo, antes de desintalarlo...
"System -> Preferences -> Appareance -> Visual Effects -> None"

---

### Post by erdosain9 on 2008-10-23
Si, ya pude desinstalarlo con la guia de la página que comento... que bueno, es buscar en synaptic... y si, también lo había sacado en sistema/preferencias/apariencia... pero ahora para volver a instalarlo estoy teniendo esos problemas...

---

### Post by guisheca on 2008-10-23
Mmmmm me parece que te complicaste mal master. Pero no te preocupes, vamos a ir limpiando la cosa.
Verás, lo que estas tratando de instalar es una versión de desarrollo del compiz, es decir, inestable, por lo tanto no se recomienda para el uso diario a menos que estes dispuesto a lidiar con todos los posibles errores que pueda tener por estar verde ahún.
Hardy ya tiene todo lo necesario para usar compiz, lo único que hace falta es descargar un programita que sirve para configurarlo.
Olvidate de todo lo del git y demás, mejor nomas que no haya funcionado la instalación.
Primero que nada creo que lo mejor es desinstalar todo lo que tenga que ver con compiz. Para eso entrá al synaptic y en buscar poné compiz y desinstalá todo lo que diga "compiz".
Después de eso, marcá para la instalación estos paquetes:

[IMG]http://i36.tinypic.com/f9gv8w.jpg[/IMG]

Con eso tendrías que tener el compiz de hardy que no tendrá todos los geniales efectos de la versión en desarrollo, pero funcionará muy bien.
Una ves instalado, para ejecutarlo, apretá alt+F2 y escribí: compiz --replace

Espero te sirva lo que te puse.
Saludos.

---

### Post by erdosain9 on 2008-10-23
ups!!! la cosa es que ahora si, se instaló y no sé cómo sacarlo... y quiero sacarlo porque me da los mismo errores e incluso peor...
como hago para desinstalarlo...
se me instaló en una carpeta llamada 
.compiz-git

donde me fijé para instalarlo decía que escribieras esto para desinstalarlo "./compiz-git uninstall " y oh! buena suerte no funciona!!!
Me dice esto:
"bash: ./compiz-git: No existe el fichero ó directorio"  y si que existe porque lo veo con nautilus..

ayuda

---

### Post by santiagoward2000 on 2008-10-23
> **erdosain9 said:**
> ups!!! la cosa es que ahora si, se instaló y no sé cómo sacarlo... y quiero sacarlo porque me da los mismo errores e incluso peor...
como hago para desinstalarlo...
se me instaló en una carpeta llamada 
.compiz-git

donde me fijé para instalarlo decía que escribieras esto para desinstalarlo "./compiz-git uninstall " y oh! buena suerte no funciona!!!
Me dice esto:
"bash: ./compiz-git: No existe el fichero ó directorio"  y si que existe porque lo veo con nautilus..

ayuda

Hola!
Probá en una terminal meter:
```
cd .compiz-git
./compiz-git uninstall
```
una fila por vez y contá si anda.
Suerte!

---

### Post by erdosain9 on 2008-10-23
mmm... pues la primer línea todo bien... me refiero a "cd .compiz-git"
pero la siguiente me dice "bash: ./compiz-git: No existe el fichero ó directorio"
ma'perqué

---

### Post by santiagoward2000 on 2008-10-23
UPS! Ahí me equivoqué yo!
La carpeta es Compiz, por lo que veo de cómo lo instalaste (y si no la moviste después) entonces sería:
```
cd ~/Compiz
./compiz-git uninstall
```

---

### Post by sajnox on 2008-10-23
En mi experiencia la mejor forma de tener compiz mas actualizado es utilizar el repositorio que hay en launchpad (en mi caso anda perfecto en dos maquinas)

Para agregarlo:

Via consola

1) Editar el sources.list

```
sudo gedit /etc/apt/sources.list

```
Al final del archivo agregar esta linea (aconsejo copiar/pegar)

```
#Compiz Fusion en Launchpad
deb http://ppa.launchpad.net/compiz/ubuntu hardy main

```

Guardas y cerras

Actualizas repositorios

```
sudo apt-get update

```
Upgrade para la ultima version

```
sudo apt-get upgrade
```

con eso solo ya deberia andar

---

### Post by evilkastel on 2008-10-23
primo, de verdad te has complicado sin necesidad. desde el principio. intentaste buscar Git en synaptic y desinstalar por ese lado? o no aperece? tenes que deshacerte de todo lo que hiciste y dejar el sistema sin efectos antes de poder montar de nuevo el compiz-fusion y el manager estables.

---

### Post by erdosain9 on 2008-10-23
mmm... creo que está funcionando (lo estoy eliminando creo)... 

Al hacer la instalación yo había creado un directorio llamado "compiz" en home/xxx/ luego entré a ese directorio y seguí los pasos sin darme cuenta de otra página... está me hizo crear un directorio compiz-git y sin darme cuenta lo hice dentro del anterior... cuando no especificaban siquiera que tenía que ser en el home... yo pensé que igual para desisntalarlo tenía que ir al .compiz-git que si existe fuera del home... (se ve que la instalación lo creó)... y bueno para que funcione el uninstall lo tenia que hacer en la primer carpeta...

no sé si se entiende algo...

bueno, ahora probaré a instalar el que viene con hardy

---

### Post by santiagoward2000 on 2008-10-23
> **evilkastel said:**
> primo, de verdad te has complicado sin necesidad. desde el principio. intentaste buscar Git en synaptic y desinstalar por ese lado? o no aperece? tenes que deshacerte de todo lo que hiciste y dejar el sistema sin efectos antes de poder montar de nuevo el compiz-fusion y el manager estables.

Es que como compiló Compiz-Fusion desde git, no va a aparecer en Synaptic (o sea, aparece la versión que está en los repositorios, no la que él instaló). Si desinstala git, lo único que va a borrar es el git (el programa que te deja bajar el código para después compilarlo) no Compiz.
(Igual sí, se complicó un poquito desde el principio, ¿pero qué gracia tiene hacer las cosas de la forma simple? ;))

---

### Post by erdosain9 on 2008-10-23
para no quedarme con dudas de que borré todo... en qué sección tengo que buscar el Git...???
saludos

ouch! estoy leyendo tarde...

Entonces lo dejo así???

---

### Post by santiagoward2000 on 2008-10-23
> **erdosain9 said:**
> mmm... creo que está funcionando (lo estoy eliminando creo)... 

Al hacer la instalación yo había creado un directorio llamado "compiz" en home/xxx/ luego entré a ese directorio y seguí los pasos sin darme cuenta de otra página... está me hizo crear un directorio compiz-git y sin darme cuenta lo hice dentro del anterior... cuando no especificaban siquiera que tenía que ser en el home... yo pensé que igual para desisntalarlo tenía que ir al .compiz-git que si existe fuera del home... (se ve que la instalación lo creó)... y bueno para que funcione el uninstall lo tenia que hacer en la primer carpeta...

no sé si se entiende algo...

bueno, ahora probaré a instalar el que viene con hardy

Mmm, no estoy del todo seguro porque no probé esa versión, pero seguro que el código estaba en la carpeta Compiz, y creo que la carpeta .compiz-git debe ser de configuraciones o algo así... (normalmente las carpetas con un punto antes son de configuraciones).

---

### Post by erdosain9 on 2008-10-23
si, se entendió entonces... pero... qué pensas... ya entonces se desinstaló... porque resulta que para instalarse estuvo bastante tiempo... y ahora para desinstalarse fue en un toque.. (pero bueno, puede ser por compilación y demases supongo)....
ustedes qué piensan??? ya intento la instalación del compiz... y por sobre todo... habrá quedado todo limpio (o más o menos)???

---

### Post by santiagoward2000 on 2008-10-23
> **erdosain9 said:**
> para no quedarme con dudas de que borré todo... en qué sección tengo que buscar el Git...???
saludos

ouch! estoy leyendo tarde...

Entonces lo dejo así???

Como quieras. Si no vas a instalar otra cosa desde git podés borrarlo sin problemas. Abrí Synaptic y desinstalalo desde ahí.

---

### Post by santiagoward2000 on 2008-10-23
> **erdosain9 said:**
> si, se entendió entonces... pero... qué pensas... ya entonces se desinstaló... porque resulta que para instalarse estuvo bastante tiempo... y ahora para desinstalarse fue en un toque.. (pero bueno, puede ser por compilación y demases supongo)....
ustedes qué piensan??? ya intento la instalación del compiz... y por sobre todo... habrá quedado todo limpio (o más o menos)???

Si, ya tendría que estar limpio. Probá de instalarlo desde los repositorios (que seguro va a andar mejor).
PS: Estamos re atrasados con las respuestas!! :lolflag:

---

### Post by erdosain9 on 2008-10-23
en qué sección lo busco... porque si pongo git en sección todo... saltan cosas que seguro no son git (el que tengo que borrar)... por ejemplo hay un git que tiene esta descripción "Interactive Tools, a file browser/viewer and process viewer/killer"
un git-score que dice esto "fast, scalable, distributed revision control system"... son esos???

y por cierto, puedo instalar el compiz desde acá "http://appnr.com/?search=compiz" ???  sería compiz fusión icon??

Por cierto en Aplicaciones/herramientas del sistema tengo un feo icono que dice compiz fusión icon (que no funciona) cómo lo borro???

---

### Post by santiagoward2000 on 2008-10-23
> **erdosain9 said:**
> en qué sección lo busco... porque si pongo git en sección todo... saltan cosas que seguro no son git (el que tengo que borrar)... por ejemplo hay un git que tiene esta descripción "Interactive Tools, a file browser/viewer and process viewer/killer"
un git-score que dice esto "fast, scalable, distributed revision control system"... son esos???

El que instalaste es **git-core**. Ponele que lo borre completamente. (Igual fijate si tenés alguno más instalado, con un cuadradito verde al lado).

> **erdosain9 said:**
> y por cierto, puedo instalar el compiz desde acá "http://appnr.com/?search=compiz" ???  sería compiz fusión icon??

La verdad que no sé qué es esa página... Parece que son los paquetes para compiz, pero yo no me animaría a bajarlos de ahí. Mejor instalalo desde Synaptic. Buscá el paquete Compiz y decile que lo instale.

---

### Post by erdosain9 on 2008-10-23
che, que bronca... al intentar sacar el git-core desde synaptic me dice esto:
"E: fusion-icon: el subproceso post-installation script devolvió el código de salida de error 1"

y esto qué es??? ahhhh!!!

De cualquier manera al volver a buscarlo en el synaptic me lo ofrece para instalar así que supongo que está desisntalado... pero el icono en aplicaciones/herramientas del sistema que dice compiz fusion sigue estando!!!

---

### Post by erdosain9 on 2008-10-23
Victoria!!!!!!!!!!!!!!!!!!!!!! Busqué fusion-icon en synaptic... Lo borré y ya se fueeee

genial!!!

Gracias a todos

---

