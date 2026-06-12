---
title: "Instalar Simusol: gcc y g77 en Ubuntu 8.10"
date: 2009-05-03
forum: Software
---

### Post by GGsalas on 2009-05-03
Hola, necesito usar el programa [Simusol]("http://www.simusol.org.ar") en Ubuntu 8.10. El programa posee las siguientes dependencias: **Dia, Gnuplot, gcc, g77, Sceptre**.

Para poder instalar **g77** tuve que instalar una versión antigua de **gcc**. Para hacer esto añadí momentaneamente los repositorios de Ubuntu Hardy Heron.

Ahora **tengo eror para actualizar el sistema**. Ubuntu quiere desinstalar **g77** y actualizar** gcc** a la última versión. 

Si le hago caso a Ubuntu, no puedo usar Simusol, si no le hago caso no puedo mantener actualizado mi sistema.

Ya se, puedo usar un LiveCD con Simusol instalado, pero desearía poder usar ese programa en mi instalación actual, no se si existe alguna posibilidad.

Muchas gracias.

---

### Post by luks911 on 2009-05-03
Se me ocurre lo siguiente: 1) deshabilitá el repositorio que no corresponde a tu sistema y que ya usaste y 2) bloquea el paquete gcc con la versión que necesitás (en synaptic lo hacés seleccionando el paquete y yendo a Paquete > Bloquear versión).
Ahora, esto no elimina la posibilidad de conflictos. Puede haber algún paquete que necesite, en su versión actual o en alguna actualización, una versión superior a la de gcc. Ahí ya me supera. Sí podés desbloquear gcc para que se actualice, con el mismo procedimiento de antes. Y volvés a donde estabas.

---

### Post by luks911 on 2009-05-03
También veo, desde Jaunty, que el paquete gcc está en su versión 4:4.3.3-1ubuntu1, pero en los repositorios también están disponibles los paquetes gcc-3.4, gcc-4.1, gcc-4.2. No sé si eso servirá de algo.

---

### Post by GGsalas on 2009-05-03
> **luks911 said:**
> Se me ocurre lo siguiente: 1) deshabilitá el repositorio que no corresponde a tu sistema y que ya usaste y 2) bloquea el paquete gcc con la versión que necesitás (en synaptic lo hacés seleccionando el paquete y yendo a Paquete > Bloquear versión).


Bien! Ahora no me da error al comprobar las actualizar el sistema. Para esto tuve que bloquear la versión de los siguientes paquetes:

• gcc-3.4
• gcc-3.4-base
• cpp-3.4
• g77
• gcc-3.4-base
• libg2c0

Espero no tener un problema posterior. ¿En realidad el programa debería actualizarse o es un error de Ubuntu no tener las librerías antigüas?

---

### Post by Hei Ku on 2009-05-03
Es que en el 8.10 esta el gcc3.4. Instalando ese, sin necesidad de bloquearlo, deberias poder instalar el resto. 

Capaz que pusieron mal las dependencias en el paquete del g77.

---

### Post by GGsalas on 2009-05-03
> **Hei Ku said:**
> Es que en el 8.10 esta el gcc3.4. Instalando ese, sin necesidad de bloquearlo, deberias poder instalar el resto. 

Capaz que pusieron mal las dependencias en el paquete del g77.

Ahora me perdí y no encuentro dónde leí que debía instalar gcc del repositorio de hardy. 

Lo que es seguro es que teniendo instalado gcc en la "última versión" (hice un aptitude para instalarlo y me dijo eso) cuando intentás instalar g77 te avisa que necesita la versión 3.4 de gcc.

Lo que me preocupa un poco es tener algún problema en mi sistema por haber bloqueado esos programas.

---

### Post by Hei Ku on 2009-05-03
En Intrepid y Jaunty tenes la gcc 3.4, podrías fijarte de desinstalar y desbloquear la que tenes instalada ahora e instalar directo de los repositorios de Intrepid.

El nombre del paquete es gcc-3.4
Una vez que instalas esta, proba de reinstalar el resto de los paquetes. Si esto anda, no tenes que bloquear nada y te quedas tranquilo.

---

### Post by GGsalas on 2009-05-03
> **Hei Ku said:**
> En Intrepid y Jaunty tenes la gcc 3.4, podrías fijarte de desinstalar y desbloquear la que tenes instalada ahora e instalar directo de los repositorios de Intrepid.

El nombre del paquete es gcc-3.4
Una vez que instalas esta, proba de reinstalar el resto de los paquetes. Si esto anda, no tenes que bloquear nada y te quedas tranquilo.

Ya quité el bloqueo a los programas y reparé ubuntu y ahora estoy por instalar g77 y te paso 2 capturas para que veas que no lo reconoce. Hay algo que no está bien.

---

### Post by Hei Ku on 2009-05-03
Que te tira si probas por la terminal con aptitude?

sudo aptitude install g77

El aptitude suele ser bastante bueno al momento de resolver dependencias.

---

### Post by josecuervo86 on 2009-05-03
Me parece que a vos te pasa lo mismo que a este:

[http://fixunix.com/ms-dos/22228-error-linking-g77-3-4-4-a.html]("http://fixunix.com/ms-dos/22228-error-linking-g77-3-4-4-a.html")

Fijate que ahi le dan una solución ;)

---

### Post by GGsalas on 2009-05-03
> **Hei Ku said:**
> Que te tira si probas por la terminal con aptitude?

sudo aptitude install g77

El aptitude suele ser bastante bueno al momento de resolver dependencias.

El error que da es que no encuentra el parquete, entiendo porque no existe para Intrepid.
```
gabi@gabi-laptop:~$ sudo aptitude install g77
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Leyendo la información de estado extendido      
Inicializando el estado de los paquetes... Hecho
No se encontró ninguna versión candidata para g77
No se encontró ninguna versión candidata para g77
```

En [esta página de Launchpad]("https://launchpad.net/ubuntu/intrepid/i386/g77-3.4/3.4.6-6ubuntu3") encontré una aparente solución, pero el .deb que me bajo para instalar es el que me pide la dependencia gcc-3.4 que a pesar de tenerla instalada la pide como si no estuviera.

---

### Post by GGsalas on 2009-05-03
Me bajé [g77-3.4]("http://packages.debian.org/etch/i386/g77-3.4/download") y [g77]("http://packages.debian.org/etch/i386/g77/download") de la página de Debian. g77 pide g77-3.4 y g77-3.4 pide gcc-3.4-base ¡que ya lo tengo instalado! como se puede ver en la siguiente captura.

---

### Post by Hei Ku on 2009-05-03
El problema es como estan armados los paquetes. Hay algo que no les gusta. 

En un caso así, yo me inclinaría por la solucion original, que era bloquear el paquete gcc 3.4, o por compilar los componentes que te faltan. 

Pero eso depende de que te sientas cómodo compilando o no.

---

### Post by GGsalas on 2009-05-03
> **Hei Ku said:**
> El problema es como estan armados los paquetes. Hay algo que no les gusta. 

En un caso así, yo me inclinaría por la solucion original, que era bloquear el paquete gcc 3.4, o por compilar los componentes que te faltan. 

Pero eso depende de que te sientas cómodo compilando o no.

No me siento cómodo compiando, pero ni siquiera se que debo compilar. No hay una solución paso a paso medianamente comprensible para mi, a menos donde he buscado.

---

### Post by Hei Ku on 2009-05-03
Entonces te conviene la opción de instalar el gcc de hardy y bloquear ese paquete.
Solo bloqueas ese paquete en particular, y como no compilas seguido, no te va a molestar. El resto de tu sistema se va a actualizar como siempre.

---

### Post by GGsalas on 2009-05-03
He llegado a la solución en la que estaba, que es bloquear algunos paquetes. Ahora voy a contar como hice y cómo quedó.

Primero agregué el repositorio de Hardy

Luego instalé g77 con aptitude y me propuso una solución:
```
gabi@gabi-laptop:~$ sudo aptitude install g77
[sudo] password for gabi: 
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Leyendo la información de estado extendido       
Inicializando el estado de los paquetes... Hecho
Escribiendo información de estado extendido... Hecho
Los siguientes paquetes están ROTOS:
  g77-3.4 libg2c0-dev 
Se instalarán los siguiente paquetes NUEVOS:
  g77 
0 paquetes actualizados, 3 nuevos instalados, 0 para eliminar y 0 sin actualizar.
Necesito descargar 0B/1980kB de ficheros. Después de desempaquetar se usarán 5362kB.
No se satisfacen las dependencias de los siguientes paquetes:
  libg2c0-dev: Depende: gcc-3.4-base (= 3.4.6-6ubuntu3) pero está instalado 3.4.6-8ubuntu2.
               Depende: libg2c0 (= 1:3.4.6-6ubuntu3) pero está instalado 1:3.4.6-8ubuntu2.
  g77-3.4: Depende: gcc-3.4 (= 3.4.6-6ubuntu3) pero está instalado 3.4.6-8ubuntu2.
           Depende: gcc-3.4-base (= 3.4.6-6ubuntu3) pero está instalado 3.4.6-8ubuntu2.
Las acciones siguientes resolverán estas dependencias

Desactualizar los paquetes siguientes:
cpp-3.4 [3.4.6-8ubuntu2 (intrepid, now) -> 3.4.6-6ubuntu3 (hardy)]
gcc-3.4 [3.4.6-8ubuntu2 (intrepid, now) -> 3.4.6-6ubuntu3 (hardy)]
gcc-3.4-base [3.4.6-8ubuntu2 (intrepid, now) -> 3.4.6-6ubuntu3 (hardy)]
libg2c0 [1:3.4.6-8ubuntu2 (intrepid, now) -> 1:3.4.6-6ubuntu3 (hardy)]

La puntuación es 50

¿Acepta esta solución? [Y/n/q/?] 
```

Acepté. Entonces ya tenía todo funcionando. Sin embargo cuando voy al Gestor de actualizaciones me da error y me fijo que son los 4 paquetes que tengo instalados de los repos de Hardy. 

Entonces lo que hago es ir a Synaptic, busco los paquetes actualizables y aparecen esos 4 (sino se pueden buscar individualmente). Los selecciono y pongo voy al menú paquete > bloquear versión.

Luego verifico y el gestor de actualizaciones dice que ya tengo mi sistema actualizado.

Agrego 2 capturas de pantalla. Espero que a alguien le sirva, he encontrado en varios foros este problema, asi que espero que esta solución sirva, y especialmente que no me traiga futuros problemas :P

Saludos y muchas gracias por la ayuda.

---

