---
title: "Problema ubuntu-tweaks"
date: 2009-09-16
forum: Software
---

### Post by yulianjose1981 on 2009-09-16
Hola chicos, soy gallego, y no encuentro ayuda entre los mios, asi que como se que estais muy volcados con el linux os pido ayuda.

Llevo unos meses usando ubuntu 9.04, y todo me iba genial lo puse todo a mi gusto y ya he quitado todos los windos de mis pcs, ayer intente instalar ubuntu-tweaks este y la he liado no se por que la instalacion no se ha realizado correctamente y el icono de actualizaciones ha sido sustituido por una señal de que algo va mal, jaja, y me dice que el paquete debe ser reinstalado, pero no puedo volver a instalarlo me vuelve a dar error con el paquete, y tampoco puedo instalar ningun otro paquete.

Ayuda por favor, estoy como loco, ruego clemencia a los expertos y que alguno me eche un cable, un saludo.

---

### Post by pablo.s on 2009-09-16
Si puedes postear el mensaje
de error exactamente como te
aparece nos será de mucha
utilidad para saber cómo ayudarte.

---

### Post by yulianjose1981 on 2009-09-16
Hola, muchas gracias, por ayudarme, esto es lo que me dice cuando no puede eliminar el paquete el gestor de actualizaciones:

El paquete «ubuntu-tweak» está en un estado inconsistente y debe reinstalarse, pero no se encuentra en ningún repositorio. Por favor, reinstale el paquete manualmente o desinstálelo del sistema.

y esto es lo que me pone cuando dejo el cursor sobre el icono del gestor de actualizaciones, donde esta la señal de trafico:

Ha ocurrido un error;por favor, ejecute el Gestor de paquetes desde el menu contextual o apt-get en una terminal para ver donde esta el problema.
El mensaje de error fue:' Error desconocido:<<<type'exceptions.SystemError''>>>(E:The package ubuntu-tweak needs to be reinstalled,but I can't find and archive for it.)'Normalmente,esto significa que ha instalado paquetes cuyas dependencias no se han podido satisfacer

Un saludo, espero vuestra respuesta

---

### Post by pablo.s on 2009-09-16
Te contesto muy simple,
debido a que tengo problemas
de conexión.

Primero debes desinstalar el
paquete ubuntu-tweak

```
sudo apt-get remove ubuntu-tweak
```
```
sudo apt-get purge ubuntu-tweak
```

y luego bajas el paquete de
donde lo habias conseguido y
lo instalas.

---

### Post by yulianjose1981 on 2009-09-16
Muchas gracias PABLO.S, pero no me deja, reporto lo que me dice:

desktop:~$ sudo apt-get remove ubuntu-tweak
[sudo] password for adri: 
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
E: El paquete ubuntu-tweak necesita ser reinstalado, pero no se encuentra un archivo para éste.

Con el otro comando da la misma respuesta, alguna idea de que hacer??

Muchas gracias

---

### Post by pablo.s on 2009-09-16
Prueba que sucede si
instalas [este paquete]("http://www.getdeb.net/app/Ubuntu+Tweak").

---

### Post by gmunioz on 2009-09-16
Hola yul....:

Esto es un poco complicado, pero estimo resultará:

1- Es en el archivo /var/lib/dpkg/status

Donde se guarda ¡¡el status!! de los paquetes instalados.

Es se guarda en forma de:

```
Package: kpartx
Status: install ok installed
Priority: extra
Section: admin
Installed-Size: 132
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Source: multipath-tools
Version: 0.4.8-14ubuntu2
Replaces: multipath-tools (<< 0.4.7-3)
Depends: libc6 (>= 2.4), libdevmapper1.02.1 (>= 2:1.02.20), udev (>> 136-1), dmsetup (>= 2:1.02.24)
Description: create device mappings for partitions
 Kpartx can be used to set up device mappings for the partitions of any
 partitioned block device. It is part of the Linux multipath-tools.
Original-Maintainer: Debian LVM Team <pkg-lvm-maintainers@lists.alioth.debian.org>

```

2- Entonces edita el archivo, previo hacer una copia
de respaldo, ejecutando en consola
(Aplicaciones - Accesorios - Terminal)

sudo cp /var/lib/dpkg/status /var/lib/dpkg/status.res

sudo gedit /var/lib/dpkg/status

Una vez abierto el archivo

Busca la línea que se refiera a tu aplicación

algo asi como:

Package: ubuntu-tweak

Elimina todas las líneas siguientes hasta el

próximo paquete:

Package: xxxxxx

Guarda el archivo

Cierra gedit

ejecuta:

sudo apt-get update

sudo apt-get upgrade

3- Si no hubo problemas, cierra la consola

baja el archivo del sitio donde te indica

el amable pablo.s

e instalalo desde nautilus, dandole click e

iniciando gdebi, quien se encargará de verificar

si hace falta descargar dependencias o si el

paquete no es instalable.

---

### Post by yulianjose1981 on 2009-09-16
Siiiiiiiiiiii, gracias a todos por ayudarme, pero sobre todo a ti ya que haciendo lo que has dicho se soluciono, y luego instale con el paquete que me dio el otro compañero, os debo unas cervezas, esto es lo que me gusta de Ubuntu, SU GENTE!!!!!!


Un saludo.

---

### Post by greenstar18 on 2009-09-30
Hola a to2!

Acabo de dar el salto a Ubuntu y la verdad es que me gusta el cambio. 
Tengo el mismo problema que yulianjose1981 y no consigo solucionarlo. Sigo vuestras instrucciones (en el paso dos me pierdo... je je) y una vez editado en el terminal y eliminado el paquete ubuntu-tweak no me deja guardar los cambios. Sale un error diciendo que no tengo permisos para guardar los cambios... y yo soy el unico usuario de mi equipo. 
No tengo ni idea de cómo solucionarlo. Ruego ayuda.
Gracias de antemano a todos vosotros!

---

### Post by pablo.s on 2009-09-30
> **greenstar18 said:**
> Sale un error diciendo que no tengo permisos para guardar los cambios... y yo soy el unico usuario de mi equipo. 

Verifica que esté presente el
comando sudo antes de editarlo.

---

### Post by greenstar18 on 2009-10-01
Gracias pablo.s!
Como digo soy nuevo en esto y de programación no tengo ni idea!! Sigo los pasos de [gmunioz]("http://ubuntuforums.org/member.php?u=252237") pero creo que hay algo que no hago bien. En el paso dos - Entonces edita el archivo, previo hacer una copia
de respaldo, ejecutando en consola
(Aplicaciones - Accesorios - Terminal)

sudo cp /var/lib/dpkg/status /var/lib/dpkg/status.res

si ejecuto esta orden desde el terminal no me deja. Pruebo con alt+F2 y tampoco. Si pruebo en alt+F2 con /var/lib/dpkg/status.res entonces sí, pero es cuando después de editar no me deja guardar los cambios.

A ver si se os ocurre algo. Muchas gracias por vuestro interes!

---

### Post by pablo.s on 2009-10-01
Bueno. Prueba escribir lo siguiente
en una terminal:

```
sudo su
```

Ahora estás utilizando el superusuario.
Ten MUCHO cuidado con lo que haces.
Luego escribe

```
cp /var/lib/dpkg/status /var/lib/dpkg/status.res
```
y continúa con los pasos que
ha escrito Gabriel.

---

### Post by greenstar18 on 2009-10-02
Muchas gracias pablo.s por tu ayuda. Creo que debo de tener un problema con el terminal. Pongo el codigo que me dices y esto es lo que aparece:

raul@raul-desktop:~$ sudo su
[sudo] password for raul: 

Le pongo mi password para el usuario raul, pero se queda en blanco. He probado de iniciar un nuevo terminal en blanco y poner "sudo su" en la primera linea pero sigo igual.

Supongo que seguramente no lo estoy haciendo bien con la terminal. Ya me dices.

Gracias de nuevo!

---

### Post by guillermolisi on 2009-10-02
> **greenstar18 said:**
> Muchas gracias pablo.s por tu ayuda. Creo que debo de tener un problema con el terminal. Pongo el codigo que me dices y esto es lo que aparece:

raul@raul-desktop:~$ sudo su
[sudo] password for raul: 

Le pongo mi password para el usuario raul, pero se queda en blanco. He probado de iniciar un nuevo terminal en blanco y poner "sudo su" en la primera linea pero sigo igual.

Supongo que seguramente no lo estoy haciendo bien con la terminal. Ya me dices.

Gracias de nuevo!
Por cuestiones de seguridad, cuando se tipea la password no se muestran los caracteres.

Repeti la operacion y apenas terminas de escribir la clave, presiona Enter y vas a ver que funciona.

---

### Post by greenstar18 on 2009-10-02
Muchisimas gracias Guillermo! ahora sí, funcionó... sois una gente estupenda! Ya me voy familiarizando con la terminal, jeje

---

