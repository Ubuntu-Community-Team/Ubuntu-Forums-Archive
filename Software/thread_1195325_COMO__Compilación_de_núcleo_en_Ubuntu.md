---
title: "COMO : Compilación de núcleo en Ubuntu"
date: 2009-06-23
forum: Software
---

### Post by pablo.s on 2009-06-23
[SIZE=4]**Compilación de núcleo en Ubuntu**[/SIZE]

[COLOR=DarkGreen]**Advertencia**[/COLOR]
Construir y utilizar un núcleo a medida puede lograr que le sea muy dificil
conseguir soporte para su sistema. Aunque es una experiencia muy educativa
el compilar su propio núcleo, no se le permitirá el enviar informes de bugs 
en base a su núcleo compilado (de hecho, si lo hace, los informes serán 
rechazados sin más explicación)
Si usted tiene un contrato de soporte comercial con Canonical, hacer esto
anulará ese soporte. También tenga en cuenta que este documento describe
un método válido para el núcleo de Edgy (2.6.17) en adelante! Hasta este núcleo,
no teníamos un mecanismo preparado para permitir a la gente el compilar sus
propios núcleos con facilidad. Esto era intencional.
Este documento NO describe cómo compilar núcleos de subida desde kernel.org.
Aqui describimos cómo reconstruir las fuentes del núcleo actual de Ubuntu.

[SIZE=2]**[COLOR=DarkGreen]Razones por las que necesita compilar un núcleo a medida[/COLOR]**[/SIZE]

-Usted es un desarrollador del núcleo.
-Necesita compilar al núcleo de una manera especial, distinta a la manera que
el núcleo oficial está compilada (por ejemplo, habilitando alguna caracteristica
experimental)
-Está intentando solucionar un bug en el núcleo oficial, para el cual ha completado
un informe de bug y lo ha presentado.
-Tiene hardware que el núcleo oficial de Ubuntu no soporta.

[SIZE=2]**[COLOR=DarkGreen]Razones por las que NO necesita compilar un núcleo a medida[/COLOR]**[/SIZE]

-Necesita solamente compilar un driver en especial. Para eso, lo que necesita es
instalar los paquetes linux-headers.
-Usted no tiene la más palida idea de lo que está haciendo, y si rompe algo, seguro
que va a precisar ayuda para arreglarlo. Depende de lo que haga mal, puede tener
que terminar reinstalando todo el sistema desde cero.
-Usted llegó a este documento por equivocación, lo leyó porque parecía interesante,
pero en realidad no quiere aprender mucho sobre núcleos.

Si quiere instalar un nuevo núcleo sin tener que compilar, puede utilizar Synaptic,
buscando por "linux-image" y seleccionando la versión del núcleo que desee.
Una forma más facil es hacer click en Sistema - Administración - Gestor de
Actualizaciones. Luego haga click en el botón Chequear - Aplicar todas las actualizaciones
incluyendo el núcleo.

[SIZE=2]**[COLOR=DarkGreen]Herramientas que necesitará[/COLOR]**[/SIZE]

Para comenzar, necesitará instalar unos cuantos paquetes.

**[COLOR=DarkGreen]sudo apt-get install linux-kernel-devel fakeroot build-essential makedumpfile[/COLOR]**

Nota: el paquete linux-kernel-devel no existe en Intrepid. Para compilar el núcleo en
Intrepid, también necesitará de

**[COLOR=DarkGreen]sudo apt-get build-dep linux[/COLOR]**

Esto instalará todos los paquetes relacionados con el compilador y herramientas de
empaquetado del núcleo. También va a instalar el paquete git-core, que es la mejor
manera de interactuar con las fuentes del núcleo de Ubuntu

[SIZE=2]Obteniendo las fuentes del núcleo[/SIZE]
Hay muchas maneras de obtener las fuentes del núcleo de Ubuntu:
1) Usar git (instrucciones detalladas de uso se pueden encontrar en la Guia Git del Núcleo)
Esto sirve para usuarios que quieran estar sincronizados con las últimas fuentes.
2) Descargar del archivo de fuentes - Válido para usuarios que quieran reconstruir los
paquetes standard de Ubuntu con parches adicionales. Notese que éstos van a estar
desactualizados en comparación con las últimas fuentes de desarrollo, asi que debería
utilizar git (opción 1) si necesita los últimos parches. Para instalar las dependencias de
compilación y extraer las fuentes (al directorio en uso): 
 
[B][COLOR=DarkGreen]sudo apt-get build-dep linux-source
apt-get source linux-source[/COLOR][/B]

A partir de Hardy (8.04)  esto ha sido cambiado a: 
sudo apt-get build-dep linux-image-$(uname -r)
apt-get source linux-image-$(uname -r)

Las fuentes de los módulos de Ubuntu pueden hacer falta si piensa habilitar PAE y el
soporte de 64 GB en el núcleo para Hardy de 32 bits. Los módulos de Ubuntu suministrados
pueden no ser compatibles con el núcleo con PAE habilitado.

[B][COLOR=DarkGreen]sudo apt-get build-dep linux-ubuntu-modules-$(uname -r)
apt-get source linux-ubuntu-modules-$(uname -r)[/COLOR][/B]

3) Descargar el paquete de fuentes. Esto es para los usuarios que solamente quieren modificar,
o chusmear con las fuentes del núcleo parcheado Ubuntu. Conste que estas fuentes no son las
fuentes más actuales (sirvase de la opción número 1/git si precisa las fuentes más recientes).
Aclaramos que esta opción no es igual a la número 2. 

Modifique las fuentes en la medida de sus necesidades.
Para mucha gente, con solo modificar el archivo config es suficiente. Si lo que necesita es
instalar un parche, lea las instrucciones de la persona que le provee el parche sobre como
aplicarlo.
Los archivos config de Ubuntu se localizan en debian/config/ARCH/ donde ARCH significa la
arquitectura para la que usted está compilando. En este directorio hay muchos archivos. El
archivo config es la base para todos los objetivos de esa arquitectura. Tambien hay varios
archivos config.SABOR que contienen opciones especificas para ese objetivo. Por ejemplo,
aqui tiene los archivos de 2.6.20 para i386 :

```
ls -l debian/config/i386/
total 108
-rw-r--r-- 1 root src  73962 2007-08-13 01:29 config
-rw-r--r-- 1 root root  1369 2007-08-13 01:29 config.386
-rw-r--r-- 1 root root  1330 2007-08-13 01:29 config.generic
-rw-r--r-- 1 root root  1395 2007-08-13 01:29 config.server
-rw-r--r-- 1 root root  1756 2007-08-13 01:29 config.server-bigiron
-rw-r--r-- 1 root root     8 2007-08-13 01:25 lowlatency
-rw-r--r-- 1 root root   194 2007-08-13 01:25 vars.386
-rw-r--r-- 1 root root   218 2007-08-13 01:25 vars.server-bigiron
```

Si no encuentra a los archivos config en el directorio debian/config, los puede encontrar en su
directorio /boot, por ejemplo /boot/config-2.6.22-14-generic. 
Si  precisa cambiar una opción de config, simplemente modifique al archivo que contiene a la
opción. Si modifica solamente al archivo config, afectará a todos los objetivos de esa arquitectura.
Pero si solo modifica uno de los archivos de objetivo, solo afecta a ese objetivo.
Después de aplicar un parche, o de ajustar los config, es una buena práctica regenerar los archivos
config para asegurarse que siguen siendo consistentes. Hay un comando que ayuda a constatar esto.
Para regenerar todas las arquitecturas ejecute:

**[COLOR=DarkGreen]debian/rules updateconfigs[/COLOR]**
Si solo quiere actualizar una sola arquitectura, ejecute
[COLOR=DarkGreen]**debian/scripts/misc/oldconfig ARCH**[/COLOR]

Para que esos dos comandos funcionen, es necesario que le otorgue permisos de escritura a los scripts
en el directorio debian/scripts/misc con el siguiente comando:
**[COLOR=DarkGreen]chmod a+x *[/COLOR]**

Compile el núcleo (cuando las fuentes son de un repositorio git, o desde apt-get source)

Compilar el núcleo es muy fácil. Dependiendo de sus necesidades, puede necesitar la compilación de
todos los objetivos del núcleo, o solo uno específico a sus sistema. Sin embargo, debe asegurarse que
la compilación no va a competir con los núcleos instalados.

Estas instrucciones son específicas para el arbol-git y para las fuentes descargadas mediante apt-get,
pero no para las descargadas del paquete linux-source de kernel.org.
Utilice este comando para compilar todos los objetivos para la arquitectura que está compilando:
**[COLOR=DarkGreen]AUTOBUILD=1 fakeroot debian/rules binary-debs[/COLOR]**

La variable de entorno AUTOBUILD dispara caracteristicas especiales en la compilación del núcleo.
Primero, se saltea a los chequeos normales de ABI (la compatibilidad binaria). Puede hacer esto porque
también crea un ID único de ABI. Si ha utilizado un repositorio git, este ID único es generado desde la
HEAD SHA de git. Si no, es generado desde el programa uuidgen (lo que significa que cada vez que
usted ejecute la compilación debian/rules, el UUID será diferente!) Sus paquetes serán nombrados
usando este ID. (Sepa que en Intrepid y más modernos, necesitará "skipabi=true" para saltearse los
chequeos de ABI.

Para compilar un objetivo específico, utilice el comando:
**[COLOR=DarkGreen]AUTOBUILD=1 NOEXTRAS=1 fakeroot debian/rules binary-SABOR[/COLOR]**
Donde SABOR es uno de los sabores del núcleo (por ejemplo: genérico)
Para compilar uno de los sabores a medida (se encuentran en debian/binary-custom.d/), use: 
**[COLOR=DarkGreen]AUTOBUILD=1 NOEXTRAS=1 fakeroot debian/rules custom-binary-SABOR[/COLOR]**

Los sabores a medida incluyen a xen y rt.
Si tiene más de un procesador o un procesador multicore, puede acelerar la compilación ejecutando
comandos concurrentes. Anteponga CONCURRENCY_LEVEL=2 para dos procesadores o dos cores;
reemplace el 2 por cuál sea el número que se ajusta a su hardware. (En Gutsy y posteriores, puede
utilizar también DEB_BUILD_OPTIONS=parallel=2). 
CONCURRENCY_LEVEL=2 AUTOBUILD=1 NOEXTRAS=1 fakeroot debian/rules binary-generic

Si obtiene errores de ABI, puede evitar el chequeo de ABI con skipabi=true. Por ejemplo, 
**[COLOR=DarkGreen]CONCURRENCY_LEVEL=2 AUTOBUILD=1 NOEXTRAS=1 skipabi=true fakeroot debian/rules binary-generic[/COLOR]**

Para ejecutar un recompilado, borre el archivo de estampa apropiado de debian/stamps 
(por ejemplo stamp-build-server para el sabor de servidor, etc.). 
Los paquetes deb se ubican en el directorio principal de su núcleo.
Por si los llega a necesitar, las fuentes de módulos de Ubuntu para Hardy pueden ser compiladas de una
forma similar. 
[B][COLOR=DarkGreen]cd linux-ubuntu-modules-2.6.24-2.6.24
AUTOBUILD=1 fakeroot debian/rules binary-debs[/COLOR][/B]

Tambien, si necesita especificar un núcleo diferente que el que se está ejecutando, use
[B][COLOR=DarkGreen]cd linux-ubuntu-modules-2.6.24-2.6.24
AUTOBUILD=1 fakeroot debian/rules binary-debs KDIR=/path/to/kerneldir
[/COLOR][/B]
Si obtiene un error, pruebe ejecutar esto en el directorio del núcleo: (ejemplo para el sabor "generico")
[B][COLOR=DarkGreen]cat debian/config/i386/config debian/config/i386/config.generic > .config
make prepare[/COLOR][/B]

[SIZE=3]**Método alternativo de Compilación: La manera Debian**[/SIZE]
El nuevo sistema de compilación Ubuntu es maravilloso para desarrolladores, para gente que precisa el
últimisimo núcleo y para gente que necesita compilar un juego surtido de núcleos (varios "sabores").
Sin embargo puede ser un poquito complejo para usuarios ordinarios. Si usted no necesita las últimas
fuentes de desarrollo, hay una manera más simple de compilar su núcleo desde el paquete linux-source.
Como se ha sugerido más arriba, lo que usted necesita es: 

[B][COLOR=DarkGreen]sudo apt-get install linux-source
mkdir ~/src
cd ~/src
tar xjvf /usr/src/linux-source-<número de versión aqui>.tar.bz2
cd linux-source-<número de versión aqui>[/COLOR][/B]

Ahora usted está en el directorio principal del árbol de las fuentes del núcleo. Antes de compilar el núcleo,
tiene que configurarlo. Si desea reutilizar la configuración del núcleo que está ejecutando, comience con:
**[COLOR=DarkGreen]cp -vi /boot/config-`uname -r` .config[/COLOR]**

Pero antes que ejecute 'make menuconfig' o 'make xconfig' (que es el próximo paso a realizar), asegurese
que tiene los paquetes necesarios:
**[COLOR=DarkGreen]sudo apt-get install qt3-dev-tools libqt3-mt-dev [/COLOR]**
Si quiere usar 'make xconfig'
[COLOR=DarkGreen]**sudo apt-get install libncurses5 libncurses5-dev **[/COLOR]
Si quiere usar 'make menuconfig'
Si quiere ver qué hay de diferente entre el config original de su núcleo y el nuevo config (asi puede decidir
si quiere alguna de las caracteristicas nuevas), puede ejecutar:
**[COLOR=DarkGreen]make oldconfig[/COLOR]**
Entonces, sin importar de si usted está reutilizando una configuración existente o empezando de cero:
**[COLOR=DarkGreen]make menuconfig [/COLOR]**
o "make xconfig" si es lo que desea hacer.
Si ha reutilizado la configuración existente, vea que los núcleos Ubuntu se compilan con información de
depuración incorporada, lo cual resulta en que los módulos del núcleo resultantes (archivos *.ko) sean mucho
más grandes  de lo que serían normalmente. Para desactivar esto, vaya a "Kernel hacking"; ahi, bajo 
"Kernel debugging", desactive "Compile the kernel with debug info". 
Ahora puede compilar el núcleo y crear los paquetes:
**[COLOR=DarkGreen]make-kpkg clean [/COLOR]**
**[COLOR=DarkGreen]fakeroot make-kpkg --initrd --append-to-version=-some-string-here kernel-image kernel-headers[/COLOR]**
Puede habilitar make paralelo (parecido a make -j) definiendo la variable de entorno
CONCURRENCY_LEVEL . No trate de añadir la opción -j a make-kpkg. Pruebe agregar 1+número de cores
del procesador, por ejemplo si tiene un dual core: export CONCURRENCY_LEVEL=3
Los paquetes deb van a ser creados en el directorio principal del directorio de las fuentes de Linux.

[SIZE=3]Instale el nuevo núcleo[/SIZE]
Si desea ver una pantalla de presentación de Ubuntu  (o utilizar modo texto) antes de pasar al servidor X en
lugar de una pantalla vacia, asegurese que el controlador de framebuffer carga: 
[B][COLOR=DarkGreen]echo vesafb | sudo tee -a /etc/initramfs-tools/modules
echo fbcon | sudo tee -a /etc/initramfs-tools/modules[/COLOR][/B]
Ahora que le ha dicho a initramfs-tools los módulos que debe incluir y la compilación está completa, puede instalar
los paquetes deb generados utilizando dpkg:
[COLOR=DarkGreen][B]sudo dpkg -i linux-image-2.6.20-16-2be-k7_2.6.20-16_i386.deb
sudo dpkg -i linux-headers-2.6.20-16-2be-k7_2.6.20-16_i386.deb[/B][/COLOR]
Si usa módulos de linux-restricted-modules, necesitará recompilar estos con el nuevo paquete linux-headers.

[SIZE=3]Recompilando''linux-restricted-modules''[/SIZE]
El paquete Linux-Restricted-Modules contiene gran cantidad de controladores privativos (además de algún
firmware y el daemon de red inalambrico ipw3945), los cuales, en un mundo perfecto no habria que empaquetar
separadamente, pero lamentablemente no están disponibles bajo una licencia compatible con la GPL. Si usted
utiliza algún hardware soportado por el paquete linux-restricted-modules, es muy seguro que vaya a descubrir que
su sistema no funciona correctamente después de pasarse a un núcleo a medida. Si este es el caso podría probar
a compilar el paquete linux-restricted-modules.
Nota: Precisará de alrededor de 8 horas compilando y mas o menos 10 GB de espacio en disco para compilar
todos los sabores el núcleo y los módulos restringidos.

---

