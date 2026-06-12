---
title: "Fallo en el conteo de inodes y de sectores"
date: 2012-01-05
forum: Software
---

### Post by EnriqueK on 2012-01-05
Uso Ubuntu 10.04 y funciona perfectamente, solo hay una cosa que me intriga un poco y es que cuando hago una imagen de respaldo usando Clonezilla, siempre me indica que falla el conteo de inodes y de sectores, le doy que los corrija y la imagen se realiza sin mas problemas.
Si arranco con un LiveCd y luego ejecuto
sudo -i
fsck -a /dev/sda1 y me sale la siguiente leyenda
·"recuperando el fichero de transacciones" y luego me indica que está limpio. .
este fenómeno se presenta siempre después de usar Ubuntu, es como que Ubuntu borra el fichero de transacciones. También noto que luego de usar el fsck desde un Live, cuando arranco Ununtu hace un nuevo chequeo y al parecer es este chequeo el que causa el problema, ya que si luego realizo un fsck desde un Live, me vuelve a mostrar el fallo de conteo de inodes y de sectores, es como que la herramienta de fsck de  Ubuntu no está bien.

---

### Post by guillermolisi on 2012-01-05
fsck puede tener bugs pero esta mas probado que la humedad :)

Hay varias razones para que pase lo que decis, algunas pueden ser:

[LIST]
[*]Particiones no alineadas a cilindros
[*]Disco con problemas de superficie/sectores fallutos
[*]En general y si tu instalacion se mantiene actualizada al dia, usar un live CD tiene el riesgo de usar una version de software, en este caso fsck, mas antigua y bugosa.
[/LIST]

---

### Post by EnriqueK on 2012-01-05
No creo que sean problemasde las particiones ni del HDD, esto lo aseguro por que tengo una imagen creada con Clonezilla de PCLinuxOS y la vuelco a la partición y no se me presenta este problema.
Además tambié probé hacer el fsck desde un Live DVD creado con Remastersys y este está actualizado

---

### Post by guillermolisi on 2012-01-05
Smarmontools que dice respecto del disco ?

La imagen que usas de PCLinuxOS es fisica (todas las particiones, track by track) o logica (particion por particion) ?

Corriste badblocks, como para terminar de descartar que sea una cuestion de superficie del disco ?

Estaba pensando que cuando se inicia Linux con particiones con journal y los filesystems quedan mal cerrados siempre se inicia una constatacion de sus estructuras, considerando lo registrado en el journal. Es decir, hay alguna maniobra que origina esta situacion.

Que dicen los logs de Ubuntu despues de haberlo utilizado varias horas, paricularmente con aplicaciones disco intensivas ?

---

### Post by EnriqueK on 2012-01-05
Me olvidabab comentar que tengo lo siguiente
sda1 -----> Ubuntu 10.04
sda2 -----> Debian 6

Intercambié las instalaciones  siguiendo el siguiente método
[http://ubuntuforums.org/showthread.php?t=1759591](http://ubuntuforums.org/showthread.php?t=1759591)
Las particiones quedaron
sda1 -----> Debian 6
sda2 -----> Ubuntu 10.04

Todo salió perfecto, solo que el problema del conteo de inodes y sectores los tiene la partición sda2, o sea para mi está claro que el problema está en la instalación de Ubuntu , no se, a mi se me da que por alguna razón falla el fsck al inicio, supongo que el fsck lo realiza por alguna orden dada desde el grub, antes que el sistema se monte, un misterio.

---

