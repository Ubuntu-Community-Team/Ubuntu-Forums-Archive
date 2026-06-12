---
title: "Ayuda, Grub error: File not found"
date: 2010-01-14
forum: Software
---

### Post by Fran's.- on 2010-01-14
Bueno, por un problema en el inicio de Ubuntu, decidi formatear para instalar Kubuntu, pero ya anteriormente tenia Windows 7 en otra particion, resulta que ahora cuando inicio windows me aparece esto:

> GRUB Loading...
Error: File not found
grub rescue>

Antes el grub iniciaba perfectamente, ahora para que funcione tengo que reinstalar ubuntu (al **** porque no me funciona) para que funcione el grub pero quiero volver a W7 el cual sigo teniendo instalado.

Alguna ayuda? :(

---

### Post by Fran's.- on 2010-01-15
Bueno, re instale Ubuntu por el simple echo que sino no puedo correr Windows 7. Hay alguna forma de sacar Ubuntu y tambien sacar el Grub? Es decir que directamente me cargue Windows 7?

---

### Post by Fran's.- on 2010-01-16
Alguna ayuda?
Necesito sacar ubuntu de una vez.

---

### Post by guillermolisi on 2010-01-16
> **Fran's.- said:**
> Alguna ayuda?
Necesito sacar ubuntu de una vez.
Si no figura en el Grub de System7 no hay nada quitar ahi.

Si formateas la particion donde instalaste Ubuntu desaparece de tu maquina, pero antes tenes que pensar que tipo de file system alojara (si es para Win, NTFS; si es para otro Linux, cualquiera que soporte el que quieras usar). Si borras la particion tambien desaparece, no hay uninstall en Ubuntu.

---

### Post by Mauro22 on 2010-01-16
Primero lo primero.

Reestablece el Bootloader de Ventanas7:

[0] [http://www.heiser.net/posts/3256](http://www.heiser.net/posts/3256)

Ese esta en ingles, pero busca que hay.


Una vez hecho eso, instala Kubuntu.

---

### Post by brothe_r on 2010-01-28
Hola,

A mi me pasó más o menos lo mismo. Mi problema fue que instalé Windows 7 después de instalar Ubuntu 9.10, de modo que me desapareció el grub y se iniciaba directamente Windows 7. Entonces instalé el grub utilizando el live CD de Ubuntu (paso 2 i 3), de modo que volví a tener grub al inciar mi PC, pero cuando seleccionaba Windows me salía:

> 
                                                 GRUB Loading...
Error: File not found
grub rescue>                      
La solución que encontré fue (puedes pasar al paso 4 si te pasó lo mismo, yo explico todos los pasos porque no tenía ni idea):

1) Primero de todo, tal como dijo Mauro22, restauré el Bootloader de Windows 7. Lo hice (resumiendo) de la siguiente manera: arrancar desde el CD de Windows 7, entrar en modo recuperación, abrir la consola, y utilitzar los comandos (en este orden): ```
*bootrec /fixmbr*
*bootrec /fixboot*
*bootrec /rebuildbcd*
``` Ahora ya podrás iniciar Windows 7. Estamos en la misma situación inicial (sin grub e iniciando Windows 7 directamente), pero sabiendo que estamos ante una situación reversible (sin pérdida de datos). Entonces instalé el grub de la siguiente manera:

2) Arrancar desde el live CD de Ubuntu 9.10.

3) Abrir el terminal, y escribir: ```
*sudo fdisk -l*
``` Fíjate donde tienes instalado tu linux. En mi caso estaba a *sda5*, pero puede/suele ser distinto, en función de cómo tengas configuradas tus particiones. Ahora escribe: ```
*sudo mount /dev/sda5 /mnt*
```Donde *sda5* es tu partición de linux. Por último, escribe: ```
*sudo grub-install --root-directory=/mnt*/ /dev/sda
``` Reiniciar. Ahora ya tendrás el *grub* instalado de nuevo, y podrás acceder a Ubuntu. El problema, tal como he comentado al principio, era que cuando seleccionaba el Windows me salía "Error: file not found". Además, el grub me detectaba Windows 7 como si fuera Windows XP... Así que decidí actualizar el grub:

4) Arrancar Ubuntu desde el grub. Buscar *'grub2*' en el Synaptic Package Manager, e instalarlo (por supuesto vas a necesitar conexión a internet).

5) Desde el terminal, ejecutar:```
*sudo update-grub*
```Verás que te detecta Windows 7  correctamente. Con esto ya tienes todo listo, y podrás seleccionar el sistema operativo que quieras al iniciar.

Por lo que parece, el problema es que la versión de grub que viene en el CD de ubuntu (descargado de la web oficial a fecha 21/01/2010) no detecta bien Windows 7, y como ves tienes que utilizar su última versión.

Fran's, la solución que te muestro te permitirá tener tanto Ubuntu como Windows 7 en la misma máquina. No desistas en usar Ubuntu aunque a veces te dé problemas, cuando lo domines un poco verás que tiene más ventajas que inconvenientes ;)

Espero haber ayudado!

---

### Post by Fran's.- on 2010-02-23
Muchisimas gracias a todos, cambie el CD de Windows 7 por easyBCD y logre recuperar el Bootloader, no voy a desistir de usar Ubuntu, pero si en esta maquina debido a que es familiar y mis hermanas más chicas no se manejan mucho.

Gracias a todos, problema resuelto.

---

### Post by MSax on 2013-03-15
brothe_r, gracias por el post, me ha servido para volver a mi ubuntu 10.04 después de haber formateado una partición en la que tenía ubuntu 12.04 (no me gusta nada). Sólo un detalle, después de instalar el grub hay que hacerlo ejecutable 
sudo chmod +x /boot/grub
Salud

---

### Post by guillermolisi on 2013-03-15
Teniendo los dos (o "n" SOs) instalados y corriendo en una consola/terminal ```
sudo update-grub
```deberias poder hacer lo que vos queres/necesitas.

---

