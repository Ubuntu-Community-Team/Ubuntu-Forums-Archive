---
title: "despioles con grub y win"
date: 2010-10-21
forum: Software
---

### Post by joseluis on 2010-10-21
hola...
no se qué pasó...porque en verdad no hubo ningún cambio salvo apagar la notebook, pero el caso es que al volver a prenderla se me perdió que grub reconozca la partición de windows.
Use el SGD y cuando me restauró me sacó el grub y pude entrar a win.
Cuando reinstalé el grub grub2 otra vez desapareció la particion win, la cual está, porque puedo entrar a ella por SGD.
El caso es que no se qué pasó pero no toma esta partición.
El famoso Administrador de Arranque no ve esa partición.
mi fdisk es:


Disco /dev/sda: 30.0 GB, 30005821440 bytes
255 cabezas, 63 sectores/pista, 3648 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes
Tamaño E/S (mínimo/óptimo): 512 bytes / 512 bytes
Identificador de disco: 0x000cd67c

Dispositivo Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1        2746    22057213+   7  HPFS/NTFS
/dev/sda2            3549        3648      803250   82  Linux swap / Solaris
/dev/sda3            2747        3548     6442065   83  Linux

Las entradas de la tabla de particiones no están en el orden del disco

Como ven, el fdisk reconoce la particiòn pero el grub2 no lo hace.
¿qué hago? gracias

---

### Post by joseluis on 2010-10-22
se que puede sonar a impaciente, pero en verdad necesito saber si se puede resolver este planteo mio.
gracias y disculpen.

---

### Post by alfplayer on 2010-10-22
Qué significa que no la reconoce o desapareció?

---

### Post by joseluis on 2010-10-22
significa que cuando butea la maquina, aparece el grub solamente con las opciones de kernel de linux (lubuntu en este caso) y no aparece la opción de arrancar con win.
Si arreglo esto desde SGD, me desaparece el grub.
Si reinstalo el grub2, me vuelve a  desaparecer la opción de ver a win en el buteo inicial.

---

### Post by biale on 2010-10-23
Fijate si agregando a mano las lineas para Win funciona. Hay que editar el archivo de configuracion de Grub2:

sudo gedit /etc/grub.d/40_custom

Y agregar algo así:

menuentry “Windows 7&#8243; {
insmod ntfs
set root=(hd0,1)
chainloader +1
}

Y ahora regenerar el archivo grub.cfg

sudo update-grub

"Reiniciar y probar"

---

### Post by joseluis on 2010-10-24
seguí tal cual los pasos, pero la pantalla de inicio del grub sigue  sin indicar el winxp.

EDITO: hice un cambio: en lugar de poner  "Windows 7" o "windows xp" (como puse en mi caso), puse solamente "windows". Me parece que el espacio entre 7 o xp j**e algo. Una vez hecho esto, el grub ahora muestra el listado. Gracias biale!!!!

---

