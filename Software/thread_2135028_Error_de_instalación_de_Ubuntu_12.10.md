---
title: "Error de instalación de Ubuntu 12.10"
date: 2013-04-12
forum: Software
---

### Post by floooreeen on 2013-04-12
Hola! Soy usuaria nueva en Ubuntu, tengo instalada la versión 12.10 en una notebook junto con Windows 7. Recientemente adquiri una netbook y decidi instalar ubuntu 12.10 en esta maquina tambien, pero ahora de forma definitiva, sin Windows 7. Realizé la instalación por medio de un USB y  seguí los pasos del asistente de instalaicón, el problema es que cuando quise reiniciar el sistema no puedo hacerlo! se pone la pantalla violeta y me aparece una pantalla negra donde dice:
Unlocking the disk /dev/disk/by-uuid/f8f70465-1db1-4455-a9de-3ff770322677 (sda5_crypt)
Enter passphtase: (ingreso el código)
y me salta un error que dice: dev maper ubuntu root: not such file was found
Lo hice una segunda vez y  despues de pedirme la contraseña como dije antes me salto: comprobando el disco en busca de errores, se ve como que hace un proceso y la pantalla se pone en negro con la linea pequeña para escribir titilando
No se que hacer porque no tengo ya instalado el windows y no puedo usar Ubuntu tampoco! estoy desasperada! Muchas gracias por la ayuda!

---

### Post by gmunioz on 2013-04-13
Mi sugerencia es:
Inicia con el live-usb.
Inicia la instalación.
Al llegar a particionamiento elige manual.
Elimina todas las particiones.
Crea las siguientes:
Una partición primaria, activa, sistema de archivos ext4, de 25 gigas, punto de montaje /
Una partición lógica, de 2 gigas uso normal, el triple de la ram si piensas hibernar y/o suspender, sistema de intercambio, montaje por defecto. (swap)
Una partición lógica, del resto libre, sistema ext4, punto de montaje /home
El Grub en el mbr de /dev/sda
No cifres las particiones, para poner la información delicada a resguardo, cifra la información cuando sea necesario.

---

