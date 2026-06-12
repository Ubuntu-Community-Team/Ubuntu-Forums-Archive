---
title: "Problema con grub"
date: 2012-09-25
forum: Software
---

### Post by FranciscoJose96 on 2012-09-25
Buenas buenas, soy nuevo en esto. Había instalado Linux Ubuntu 12.04, me anduvo PERFECTO. Un día ingrese al gestor de actualización y encontré una versión nueva Ubuntu 12.10, la descargue, la instale y he aquí que me fallo, no andaba, así que decidí no darle mas vueltas al asunto y restaurar el sistema al Ubuntu 10. (no me acuerdo el otro numero, sepan perdonarme). La restauración funciono de maravilla, así que decidí volver al Ubuntu 12.04 que me había funcionado perfecto, ese mismo día ingrese al gestor de actualización y estaba la misma versión pero con algo diferente: Ubuntu LTS 12.04. La descargue, la instale. Todo joya hasta que tuve que reiniciarla. No tenia el menú para elegir el sistema operativo, y prácticamente no se mucho de eso. Necesito ayuda con dos cosas. Me sale una especie de consola grub. 
1. Quiero volver a tener la lista de sistemas operativos que tenia antes de actualizar a 12.10
2. Quiero tener esa versión del Ubuntu 12.04 que me funcionaba bien y no era LTS
AYUDA ES URGENTE!!

---

### Post by reLlene on 2012-10-04
ejecuta como root  "update-grub2" 
reincia y fijate que tul...

---

### Post by infernus92 on 2012-10-20
Primero, para sacarte la confusion... ubuntu 12.04 es una version LTS (de soporte extendido). Lo es la que tenes ahora y la que tenias antes, en definitiva la misma...
Por otro lado con lo de grub...lo que yo te recomiendo seria una reinstalacion de grub, tarea bastante sencilla si tenes un cd/dvd/USB con cualquier version de ubuntu desde 10.04 o cualquier distribución que use grub2 (recomiendo 12.04 ya que es la que vas a seguir usando)
Inicias el sistema LIVE desde el cd/dvd/USB y vas a tener el entorno de ubuntu listo para usar... para esto te va a hacer falta solamente la terminal.
Abris una terminal (ctrl+alt+T) y escribis lo siguiente en orden

```

sudo su
fdisk -l (esto te va a devolver una lista de particiones, es necesario para ver cual es la de linux... supongamos que es /dev/sda3)
mkdir /mnt/ubuntu
chmod -Rf 777 /mnt/ubuntu
mount /dev/sda3 /mnt/ubuntu (recorda que supusimos sda3... si es otra pone la que corresponda)
chmod -Rf 777 /mnt/ubuntu/dev
mount --bind /dev/ /mnt/ubuntu/dev
chroot /mnt/ubuntu
grub-install --root-directory=/ /dev/sda
grub-install --recheck /dev/sda (si te dice que hubo un error repeti el paso anterior)
update-grub2

```

Hecho esto deberia quedar funcionando.
En el caso de que tengas particiones con otros sistemas operativos y no te las detecte hace lo siguiente, sino ignora esto:

Inicia tu ubuntu (no el del cd/dvd/USB)
Abri una terminal (ctrl+alt+T) e ingresa los siguientes comandos en orden

```

sudo su (te pide contraseña)
chmod +x /etc/grub.d/30_os-prober
update-grub2

```

Luego deberia aparecer algo como lo siguiente:

```

# update-grub2
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-16-generic
Found initrd image: /boot/initrd.img-2.6.31-16-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /memtest86+.bin
**Found Microsoft Windows XP Professional on /dev/sda1**
done

```

despues de esto te deberia quedar andando joya :)

---

