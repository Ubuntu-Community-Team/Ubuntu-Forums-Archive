---
title: "Disco rígido  se va encogiendo"
date: 2009-05-26
forum: Software
---

### Post by aledruetta on 2009-05-26
"Cosa e' mandinga", dirían mis paisanos. El disco rígido de mi portátil se va encogiendo, poco a poco, durante la sesión. 

¿Qué quiero decir con eso? No que se va llenando, sino que el tamaño del disco va disminuyendo. Por ejemplo: inicio la sesión con 25,8 GB ocupados y 45 GB libres (el disco es de 80 GB, la suma no da, pero así es como comienza); a las dos horas tengo 25,8 GB ocupados y 31 GB libres; una hora después, 25 GB ocupados y 26,2 GB libres. Y así, hasta que queda con 0 B y ya no se puede correr ninguna aplicación y sólo resta reiniciar.

Al reiniciar, la carga del sistema llega hasta un 80%, más o menos, y se tilda. Tengo que apagar "a lo bruto" y volver a iniciar. Recién ahí se carga el sistema, y sigo trabajando hasta que otra vez no tengo disco libre.

Si voy a equipo-->Sistema de archivos-->Propiedades, dice:

Lugar: computer:///
Volumen: desconocido

En consola y sesión LiveCD, ejecuto lo siguiente:

```
sudo fdisk -l
```Me devuelve:

```
Disco /dev/sda: 80.0 GB, 80026361856 bytes
255 cabezas, 63 sectores/pista, 9729 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x97be5b6a

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1        9667    77650146   83  Linux
/dev/sda2            9668        9729      498015    f  W95 Ext'd (LBA)
/dev/sda5            9668        9729      497983+  82  Linux swap / Solaris
```y haciendo:

```
e2fsck -p /dev/sda1
```Obtengo, al instante:

```
ubuntu@ubuntu:~$ sudo e2fsck -p /dev/sda1
/dev/sda1: limpio, 180981/4857856 ficheros, 14729099/19412536 bloques
```

El sistema de archivos es Ext4. Ubuntu Jaunty es el SO.

¿Alguien tiene idea de qué está sucediendo?

Saludos y muchas gracias,
Alejandro.

---

### Post by AlexDDR on 2009-05-26
lo que se te aca es el espacio libre, no es que se este encgiendo la particion.

Seguramente alguna aplicacion esté haciendo eso, abre en Sistema --> Administración, el monitor de sistema y en la ultima pestaña "sistemas de archivo" puedes ver graficamente como va disminuyendo

trata de averiguar el peso de las carpetas como /home  o la /tmp, con boton derecho propiedades


Creo haber visto un comando que te dce que aplicaciones estan escribiendo en el disco duro, voy a ver si puedo averiguarlo y lo poste (espero que no este soñando)

Baja de aca el programa que se llama WATSUP

[http://kornelix.squarespace.com/packages/](http://kornelix.squarespace.com/packages/)

lo instalas y ejecutas ALT+F2 y escribes watsup

ahi te dice los procesos y cual es su I/O osea cuanto estan escribiendo al disco, en una de esas ves al que esta escribiendo

saludos

---

### Post by aledruetta on 2009-05-27
AlexDDR,

Intalé watsup, pero no me señala ningún proceso que esté escribiendo en disco.

Saludos y muchas gracias,
Alejandro.

---

### Post by gmunioz on 2009-05-27
Hola Alejandro:

Intenta con:

1- Cambiar el porcentaje de reserva del espacio de una partición para el

superusuario root que por defecto estará al 5% del tamaño total del

disco. En general con el 1% es suficiente, esto lo haces con la orden:

```
sudo tune2fs -m1 /dev/sda1
```

Donde debes cambiar /dev/sda1 por la que corresponde a tu instalación.

2- Si sigue consumiendose el espacio del disco, averigua que archivos

de por ejemplo, más de 300 megas se han creado, con la orden:

```
sudo find / -size +300M -print 2>/dev/null
```

Este comando te mostrará los archivos mayores de 300 megas, pudiendo asi 

investigar su origen y de ser innecesarios, basura o temporales, 

borrarlos.

Saludos

---

### Post by AlexDDR on 2009-05-29
YA LO ENCONTRE!!!


escribe en la consola

> iotop


si no esta instalado

 sudo apt-get install iotop


es lo mismo que "top", te ordena los procesos por su i/o  en el disco, asi veras facilmete el proceso que te esta escribiendo en el disco demasiado y la cantidad por segundo en que lo hace


saludos

---

### Post by aledruetta on 2009-05-29
Gracias AlexDDR y gmunioz,

Lo tendré en cuenta para la próxima. Lamentablemente, el problema se hizo cada vez más grave, sumado a que la papelera de reciclaje enloqueció, así que decidí formatear y volver a empezar. Necesitaba tener el equipo en condiciones porque trabajo con él.

Saludos,
Alejandro.

---

