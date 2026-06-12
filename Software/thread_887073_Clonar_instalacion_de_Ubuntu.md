---
title: "Clonar instalacion de Ubuntu"
date: 2008-08-11
forum: Software
---

### Post by sdm_cacto on 2008-08-11
Una pregunta para los que saben.

Quiero instalar Ubuntu en la Laptop de un amigo, que es completamente distinta a la mia. Pero seria mucho mas facil para mi copiar la instalacion en un dvd/disco externo o lo q sea, para que la instalacion de paquetes sea minima.

Hay alguna manera de clonar mi instalacion?? sirve copiar y pegar asi nomas?? posteen experiencias por favor.

PD:tambien quiero saber si se puede hacer con Win XP (siempre es bueno tener ambos hasta despegarse)

---

### Post by Mauro22 on 2008-08-11
Si son hardware diferentes, ubuntu va a andar mal (Experiencia) y XP no va ni a arrancar (Experiencia tambien).


Lo mejor es una instalacion de cero por no ser iguales.

---

### Post by lega on 2008-08-11
lo que podes, si bien no es lo mismo, es generar una lista de tus paquetes instalados paara despues en la maquina de tu amigo instalarlos con deselect

El procedimiento es muy sencillo, primero instalas en tu máquina el dselect:
```
sudo apt-get install dselect
```

Ahora generamos una lista con todos los paquetes instalados en el archivo “paquetes"

```
dpkg –get-selections | grep -v deinstall > paquetes
```
El siguiente paso es guardar a buen recaudo nuestra lista de paquetes, para que la próxima vez que demos formato a nuestro disco duro, la tengamos disponible.

Por último, sobre la máquina ya formateada, tendremos una instalación base de nuestro Ubuntu (o cualquier otra distribución basada en Debian) en la que primero actualizaremos los paquetes, luego instalamos dselect, actualizamos la distribución y después instalaremos los paquetes de la lista.
Esto se hace con los siguientes comandos:

```
sudo apt-get update
sudo apt-get install dselect
sudo apt-get dist-upgrade
sudo dpkg –set-selections < paquetes
sudo dselect install
```

esto te instala todos los paquetes que esten en los repositorios, si tenias alguna aplicación con repositorio de tercero no te lo va a instalar o te va a instalar la version que haya en el repo de Ubuntu, yo lo hice cuando pase de gutsy a hardy y salio todo bien.

espero te sirva 
Saludos

---

### Post by sergiom99 on 2008-08-11
lo voy a tener en cuenta este tip. Gracias!

---

### Post by EnriqueK on 2008-08-11
Remastersys project
Con esta herramienta creás un live DVD de tu instalación que podés usarlo como tal y/o para instalar en otro equipo , el proceso no puede ser mas simple, solo un par de detalles, usá la opción sin datos personales (no guarda nada de la carpeta de usuario) y la otra es que antes de iniciar el proceso desmontá todas las otras particiones y conexiones de red. Una última recomendación es que entrés al foro del proyecto que se accede también desde el siguiente enlace.
[http://www.remastersys.klikit-linux.com/](http://www.remastersys.klikit-linux.com/)

---

### Post by ubuntu27 on 2008-08-11
Que buen truco, donde aprendiste Lega? :guitar:

---

### Post by lega on 2008-08-12
lo vi en [este blog]("http://www.maty1206linuxeando.com/archives/979") hace un tiempo y tengo guardado el artículo para hacerlo en cada lanzamiento de Ubuntu :wink:

---

### Post by ubuntu27 on 2008-08-12
> **lega said:**
> lo vi en [este blog]("http://www.maty1206linuxeando.com/archives/979") hace un tiempo y tengo guardado el artículo para hacerlo en cada lanzamiento de Ubuntu :wink:

Ah! Que chevere esta esa pagina web, ese blog! Nunca lo vi..
Bueno, yo solo leo paginas en Ingles ><;

Pero, que buen blog que has encontrado. Voy a compartir esa pagina con todos mis amigos de latinoamerica :)


Gracias lega :KS

---

### Post by darkarcangel_sam on 2008-08-12
yo quiero saber si puedo guardar todos los cambios q le he hecho a mi ubuntu , recientemente instale ubuntu 8.04.1 hardy heron desde win xp desde wubi , y ahora q ya lo probe , quiero formatear mi pc y dejar de base ubuntu , pero quiero dejar todo cmo ya lo deje , no se si m expllico , para poder formatear y conservar todos los cambios q le he hecho a ubuntu 

de antemano gracias

---

### Post by faktorqm on 2008-08-12
PAra mi, alcanza con levantar un live cd, y copiar (si, copiar) las carpetas de un disco a otro... ni siquiera clonar hace falta. 
Lo unico que no les va a andar es el grub por que no podes escribir en el mbr pero nada, es poner el cd en la otra copmpu, poner el disco :P, hacer el procedimiento de instalar grub desde un live cd... y listo.
El dselect es super copado cuando queres reinstalar y no queres bajarte 115000 paquetes, pero para llevar a cabo un proceso de "clonacion" alcanza con copiar.
Ubuntu en distintas pc's anda mal por que le tenes que dar unos mimitos en realidad, a veces te conviene compilar el kernel con lo que va para que no vaya lento, pegarle un tiro en la kbza al tracker, mirar si algo levanta y no se usa (todos aquellos que no usen bluetooth por ejemplo) y asi un par de cosas y listo, anda como si lo hubieras instalado de cero.
Salu2!

---

### Post by sajnox on 2008-08-12
Si bien no soy de los que saben, me parece que para el problema que tenes lo podes solucionar con aptoncd.

Haces una instalacion limpita y normal en la maquina "nueva", asi no tenes problemas de hard y esas cosas.

En tu maquina instalas aptoncd que te hace un backup de todos los paquetes descargados y generas un cd que lo llevas a la maquina nueva con los paquetes que descargaste y lo agregar como un repositorio al cd.

Listo!!

---

### Post by sdm_cacto on 2008-08-15
OK, voy a probar con APTONCD, copiar mis sources.list y copiar un par de configuraciones.

vamos a ver pasa

---

### Post by totolinux on 2008-09-01
yo copio los paquetes bajados de var\cache\apt\archives en una llave usb o cd. Hago una inst. limpia y luego agrego los paquetes con synaptic con  agregar paquetes descargados :KS y queda mas o menos como mi pc luego a configurar.

---

