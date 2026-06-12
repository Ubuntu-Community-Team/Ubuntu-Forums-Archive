---
title: "Disco rígido que encoge ¿¡!?"
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
```El sistema de archivos es Ext4. Ubuntu Jaunty es el SO.

¿Alguien tiene idea de qué está sucediendo?

Saludos y muchas gracias,
Alejandro.

---

### Post by Mauro22 on 2009-05-26
A me paso una vez, pero con Ext3

Usaba Intrepid y una noche deje la pc prendida bajando un juego (openarena si no me equivoco).


Una noche deberia bastar y sobrar, pero al despertar vi que se habia cancelado ¿? empecé a reviar y tenia 0 B disponibles en el disco de 160gb que a lo sumo, exagerando a la decima potencia, tendria ocupado unos 40 gb... o sea sobraban 120gb...


Pero lo mio fue distinto, ni reiniciando se fue, use el "analizador de discos" y daba datos erroneos, como un script en bash pesaba 1gb :S


Yo tuve que formatear... :S 
El problema nunca lo supe y no pregunte de vuelta porque me paso esa vez sola, habiendola dejado bajar el mismo juego a la otra noche...

---

