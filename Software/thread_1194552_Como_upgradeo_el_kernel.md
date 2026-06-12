---
title: "Como upgradeo el kernel?"
date: 2009-06-22
forum: Software
---

### Post by Just64 on 2009-06-22
Tengo el kernel viejo:

```
pato@pato-desktop:~$ uname -r
2.6.27-14-generic

```

Y las actualizaciones no me lo instalan.
Como hago para compilar un nuevo kernel? Si es el 2.6.30 mejor, sino el 2.6.28

---

### Post by pablo.s on 2009-06-22
Mas que compilar, te va a
ser mas facil instalar el
kernel 2.6.30-8 que viene
con [Karmic Koala]("http://packages.ubuntu.com/search?keywords=kernel&searchon=names&suite=karmic&section=all").

---

### Post by guillermolisi on 2009-06-22
Pero hay una aviso bien grande que dice: 
   > **debian-installer udeb package**

 Warning: This package is intended for the use in building [debian-installer]("http://www.debian.org/devel/debian-installer") images only. Do not install it on a normal Ubuntu system.

O sea que no es un paquete .deb cualquiera.

---

### Post by juancarlospaco on 2009-06-22
*Acme Versionitis Sensor :*

-------------------------------------**V**----
Low------Medium------High-------Warning!!!

---

### Post by pablo.s on 2009-06-22
Hay un [PPA que tiene]("https://launchpad.net/%7Eapw/+archive/jaunty-kernel") un
2.6.30. Espero que te sirva.

---

### Post by guillermolisi on 2009-06-22
Bueno, tambien encontre el siguiente link con .deb [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30/)

---

### Post by pablo.s on 2009-06-22
Si, estaba buscando ese
PPA... bueno, muchas
opciones hay. (Diria Yoda)

---

### Post by santiagoward2000 on 2009-06-23
¿Pero hay alguna razón especial para actualizar el kernel? A veces puede causar más problemas de los que arregla. ¿Hay algo que ande mal con el que tenés instalado?
Saludos!

---

### Post by guillermolisi on 2009-06-23
> **santiagoward2000 said:**
> ¿Pero hay alguna razón especial para actualizar el kernel? A veces puede causar más problemas de los que arregla. ¿Hay algo que ande mal con el que tenés instalado?
Saludos!
Aparentemente la duda es "por que no se actualizo el kernel al 2.6.28-13 ?", nada mas.

Lo que aun no se pregunto es "que version de Ubuntu estas corriendo ?"

---

### Post by pablo.s on 2009-06-23
> **guillermolisi said:**
> Lo que aun no se pregunto es "que version de Ubuntu estas corriendo ?"

Tiene un 2.6.27-14. 
Estimo a ojimetro que
es Intrepid... por ahi
andaria.

---

### Post by gmunioz on 2009-06-23
Hola:

Si es Intrepid, el 2.6.30 no se podrá instalar como paquete deb

deberá ser compilado.

Si es Jaunty, Si, mas si se estan utilizando módulos para nvidia,

estos no son compatibles, es necesario usar los nuevos drivers

bajados desde nvidia.

---

### Post by pablo.s on 2009-06-23
No se si va a saber
compilar un kernel...
Podríamos armar un
COMO y marcarlo como
Sticky para futuras
consultas.

---

### Post by Dan_Dranath999 on 2009-06-23
como no haya una cuestión de "soporte específico para hardware" o alguna otra cuestión crítica, no veo razones de peso de compilar un kernel.  

(ahora, que venga uno a decirme que lo quiere compilar simplemente porque le apetece hacerlo, pues también es buena razón)

---

### Post by EnriqueK on 2009-06-23
En el siguiente enlace explican la forma de compilar un kernel al "estilo" Ubuntu, aparentemente sería la forma mas simple (no lo probé)
[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

---

### Post by pablo.s on 2009-06-23
> **EnriqueK said:**
> En el siguiente enlace explican la forma de compilar un kernel al "estilo" Ubuntu, aparentemente sería la forma mas simple (no lo probé)
[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

Estoy haciendo la traducción
de ese documento ahora mismo,
para que quede como post.

---

### Post by gmunioz on 2009-06-23
Hola Pablo:

Resumidamente el procedimiento es:

Para comenzar, instalar las aplicaciones imprescindibles:

sudo apt-get install build-essential kernel-package libncurses5-dev fakeroot wget bzip2

Elegir la fuente del kernel

Las fuentes mas actualizadas de kernel.org

[http://www.kernel.org/](http://www.kernel.org/)

Fuentes oficiales

El kernel en uso:

sudo apt-get install linux-source

Otros kernels

[http://packages.ubuntu.com](http://packages.ubuntu.com)

Los ultimos mainline, sin los patchs de Ubuntu

[http://kernel.ubuntu.com/~kernel-ppa/mainline](http://kernel.ubuntu.com/~kernel-ppa/mainline)

Una vez instados los sources:

Si es .deb

sudo dpkg -i *.deb

Si es .tar.bz2

cd /usr/src

sudo wget [http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.xxxx.tar.bz2](http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.xxxx.tar.bz2)

sudo tar xfjv linux-2.6.xxxx.tar.bz2

sudo ln -s linux-2.6.xxxx linux

cd /usr/src/linux
       
sudo cp /boot/config-uname -r ./.config

sudo make menuconfig

Para utilizar los parámetros de configuración del kernel modelo

ir a la opción:

Load an Alternate Configuration File

Dar enter dos veces

Ahora, segun lo que se sepa, y/o se haya leido queda elegir opciones

Terminada la personalización pulsar exit repetidas veces, hasta que se

nos pregunte sobre guardar la configuracion, lo que se acepta

Compilar

sudo make-kpkg clean

sudo fakeroot make-kpkg --initrd --append-to-version=-custom kernel_image kernel_headers
   
Instalar el kernel

sudo dpkg -i linux-image-2.6.xxxx.deb

sudo dpkg -i linux-headers-2.6.xxxx.deb
  
dkms, posiblemente compile los modulos de vbox, nvidia y ati, requeridos

a menos que se necesiten mas nuevos que los instalados, y entonces se 

deberan instalar en forma manual, previa descarga de sus sitios de origen

Espero que te sirva como para armar el howto.

---

### Post by pablo.s on 2009-06-23
> **gmunioz said:**
> Espero que te sirva como para armar el howto.

Si, bueno, que decir, mas
que sumimasen! Ya no sé
si con esta explicación vale
que traduzca el tutorial...

---

### Post by gmunioz on 2009-06-23
Hola Pablo:

Absolutamente si.

Esto esta resumido.

Si bien te puede parecer

una guia, para alguien no

avanzado estimo que es

totalmente críptico.

Faltan todas las aclaraciones

de los pasos y muchas otras opciones.

---

### Post by leonardomdq on 2009-06-24
Bueno ya que estan con el hilo aprobecho.
Tengo JJ con el kernel 2.6.28-13-generic y por lo que estube leyendo del kernel que trae KK soluciona aparentemente el problema con el video Intel (tengo en la notebook video Intel 965).

Quisiera saber como tendria que hacer para actualizar al[B] kernel 2.6.30 

[/B]Agradesco al que me pueda explicar como tengo que hacer.Gracias

---

### Post by gmunioz on 2009-06-24
Hola Leonardo:

Debes bajar los archivos .deb desde este link:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30/)

Los archivos son:

```
linux-headers-2.6.30-020630-generic_2.6.30-020630_amd64.deb
linux-headers-2.6.30-020630-generic_2.6.30-020630_i386.deb	
linux-headers-2.6.30-020630_2.6.30-020630_all.deb
linux-image-2.6.30-020630-generic_2.6.30-020630_amd64.deb
linux-image-2.6.30-020630-generic_2.6.30-020630_i386.deb
linux-source-2.6.30_2.6.30-020630_all.deb

```

Si usas una versión amd64 no descargues los _i386

Si usas la versión no amd64, no descargues los _amd64

Una vez descargados los colocas en un directorio, (carpeta)

te cambias a ese directorio y en una consola (Aplicaciones -

Accesorios - Terminal) ejecutas:

```
sudo dpkg -i *.deb
```

Y para el próximo reinicio tendrás la opción de iniciar

desde el Grub con este kernel.

---

### Post by leonardomdq on 2009-06-24
gmunioz muchas gracias por contestar.

serian estos dos o me faltaria alguno?
```

linux-headers-2.6.30-020630-generic_2.6.30-020630_i386.deb
linux-image-2.6.30-020630-generic_2.6.30-020630_i386.deb

```

Ya lo estoy haciendo.

Salu2

---

### Post by gmunioz on 2009-06-24
Son estos 4 paquetes:

```
linux-headers-2.6.30-020630-generic_2.6.30-020630_i386.deb	
linux-headers-2.6.30-020630_2.6.30-020630_all.deb
linux-image-2.6.30-020630-generic_2.6.30-020630_i386.deb
linux-source-2.6.30_2.6.30-020630_all.deb
```

---

