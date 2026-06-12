---
title: "[SOLVED] Problema con Grub y WinVista al iniciarse"
date: 2009-08-02
forum: Software
---

### Post by Slay_ on 2009-08-02
AYUDA URGENTE.
Hoy me compre un portatil Samsung.
Estuve trasteando con el Vista, instalando cosas y eso y todo perfecto.
Entonces instale el Ubuntu 9.04 y lo mismo, estuve navegando, instalando cosas y bien.
Modifique el GRUB para que iniciara por defeto el Vista, reinicio, se inicia el vista, pero resulta que inicie el Recovery de Samsung, no el SO.
Reinicio el ordenador, llega a la pantalla que te permite entrar al SETUP y esas cosas, pasa, llega a un pantalla que dice que esta mirando si puede inicirse desde un CD y aqui viene el problema, vuelve a la pantalla del SETUP y se repite el ciclo infinitas veces.
Solo puede inicirlo si le meto el Live CD de Ubuntu.

¿QUE PASA?
AYUDA!

---

### Post by staar on 2009-08-02
no hace falta que grites, ni que pidas ayuda (este es un foro de soporte, es medio redundante)

con > Modifique el GRUB para que iniciara por defeto el Vista, a que te referís exactamente? que pasos seguiste?

saludos

---

### Post by Slay_ on 2009-08-02
Pues desde una terminal introduje sudo gedit /boot/grub/menu.lst
Y modifique el defualt 0 por default 4 (que se supone que era el win vista)
Y lo siento por gritar, pero es que el ordenador es nuevo de hoy y me fastidia muchisimo.

---

### Post by staar on 2009-08-02
por lo que describís, parece como que el recovery de samsung hubiera borrado el grub de la mbr, hacé lo siguiente:

- iniciá con el livecd
- abrí una terminal
- corré ```
sudo grub-install /dev/sda
```
- reiniciá y vas a tener el grub de nuevo para poder acceder a ubuntu...

la entrada de Ventanas en el grub la hizo el instalador de ubuntu automáticamente, si es así, me parece que puso la partición de recovery en vez de la que corresponde, habría que modificar el menu.lst para que apunte a la partición que tiene Ventanas, si necesitas ayuda con eso posteá la salida de ```
sudo fdisk -l
``` y el contenido del menu.lst para que te ayudemos a modificarlo...

saludos

---

### Post by Slay_ on 2009-08-02
Cuando corro lo que me has discho sale lo siguiente:
```
Probing devices to guess BIOS drives. This may take a long time.
Could not find device for /boot: Not foundm or not a block device.
```
:S

---

### Post by Slay_ on 2009-08-02
Arreglado, me habia cargado el GRUB pero ya lo reinstale completando el comando que me dijiste con la rusta donde estaba el /boot/
 
Muchas gracias

---

