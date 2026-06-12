---
title: "Instalar Genius Eye 310"
date: 2008-10-13
forum: Software
---

### Post by echi24 on 2008-10-13
Buenas a todos, 

Soy nuevo en el SO Ubuntu, ya son 2 dias desde la instalaciòn. Cada vez estoy mas satisfecho con mi cambio de Win a Linux. Uno de los problemas que tengo y ya asumi es que no puedo syncronizar mi IPOD TOUCH, pero eso es otro tema.
Por lo que va el post, el problema que tengo es que no puedo instalar mi webcam genius eye 310. 
Primero descargue los drivers (creo que son estos) gspcav1-20071224.tar.gz, descomprimi, edité el archivo para agregarle datos, etc. 
Todo siguiendo pasos de [http://lalo-linux-systems.blogspot.com/2007/07/ubuntu-y-webcam-genius-eye-310.html](http://lalo-linux-systems.blogspot.com/2007/07/ubuntu-y-webcam-genius-eye-310.html)

Ahora cuando le doy make install me aparece el siguiente error:

exequiel@linex:~/Descargas/gspcav1-20071224$ sudo make install
mkdir -p /lib/modules/`uname -r`/kernel/drivers/usb/media/
rm -f /lib/modules/`uname -r`/kernel/drivers/usb/media/spca5xx.ko
rm -f /lib/modules/`uname -r`/kernel/drivers/media/video/gspca.ko
install -c -m 0644 gspca.ko /lib/modules/`uname -r`/kernel/drivers/usb/media/
install: no se puede efectuar `stat' sobre «gspca.ko»: No existe el fichero ó directorio
make: *** [install] Error 1


Por lo cual no me genera un /dev/video o algo similar.

Espero puedan ayudarme....
Saludos
Exequiel

---

### Post by Mauro22 on 2008-10-13
De la webcam ni idea, pero te dejo esto para el iPod

[http://magarto.com/blog/archivo/2007/12/31/iphone-ipod-touch-ubuntu-gtkpod-amarok/](http://magarto.com/blog/archivo/2007/12/31/iphone-ipod-touch-ubuntu-gtkpod-amarok/)

---

### Post by Hei Ku on 2008-10-13
> **echi24 said:**
> Buenas a todos, 

Soy nuevo en el SO Ubuntu, ya son 2 dias desde la instalaciòn. Cada vez estoy mas satisfecho con mi cambio de Win a Linux. Uno de los problemas que tengo y ya asumi es que no puedo syncronizar mi IPOD TOUCH, pero eso es otro tema.
Por lo que va el post, el problema que tengo es que no puedo instalar mi webcam genius eye 310. 
Primero descargue los drivers (creo que son estos) gspcav1-20071224.tar.gz, descomprimi, edité el archivo para agregarle datos, etc. 
Todo siguiendo pasos de [http://lalo-linux-systems.blogspot.com/2007/07/ubuntu-y-webcam-genius-eye-310.html](http://lalo-linux-systems.blogspot.com/2007/07/ubuntu-y-webcam-genius-eye-310.html)

Ahora cuando le doy make install me aparece el siguiente error:

exequiel@linex:~/Descargas/gspcav1-20071224$ sudo make install
mkdir -p /lib/modules/`uname -r`/kernel/drivers/usb/media/
rm -f /lib/modules/`uname -r`/kernel/drivers/usb/media/spca5xx.ko
rm -f /lib/modules/`uname -r`/kernel/drivers/media/video/gspca.ko
install -c -m 0644 gspca.ko /lib/modules/`uname -r`/kernel/drivers/usb/media/
install: no se puede efectuar `stat' sobre «gspca.ko»: No existe el fichero ó directorio
make: *** [install] Error 1


Por lo cual no me genera un /dev/video o algo similar.

Espero puedan ayudarme....
Saludos
Exequiel

No hay una versión mas nueva de los drivers? Esos ya deben estar en Hardy.
Y por otro lado, poné todos los comandos que escribiste, porque me parece que le chingaste al uname-r

---

### Post by ramiro_md on 2008-10-13
Un par de hojas más atrás abrí un post sobre esa cam. Ahí te dicen como compilar los drivers.
Si lográs que ande, avisame ;). Un saludete pibe.

---

### Post by faktorqm on 2008-10-14
Se, lo acabo de contestar, fijate por que creo que es lo mismo. 

Dato curioso:

```

faktorqm@the-edge:~$ aptitude search gspca
p   gspca-source                    - source for the gspca v4l kernel module    
faktorqm@the-edge:~$ 
```

para que servira? por las dudas lee igual el otro thread. Salu2!

---

