---
title: "Usplash se paso a modo texto"
date: 2008-11-28
forum: Software
---

### Post by lega on 2008-11-28
Perdón si estoy diciendo una barbaridad, no estoy seguro si es Usplash a lo que me refiero, si no es así alguien me corregirá, es la pantalla con el logo de Ubuntu y la barra que va de un lado a otro :)

Resulta que hoy se me ocurrió instalar Kubuntu en un segundo disco rígido, el grub actualizo con los dos sistemas, eso esta todo bien, Kubuntu inicia normalmente, pero cuando quiero iniciar con Ubuntu, aparece el logo 2 segundos y luego se pasa a texto y hace toda la carga del sistema así, sin ningún error, solo en texto.

Alguien sabra como puedo solucionarlo?

---

### Post by ramiro_md on 2008-11-28
me parece que se te desinstaló una librería o alguna yerba de esas. A mi me pasó es una boludez, fijate si tenés isntalado "usplash" y "usplash-theme-ubuntu".

---

### Post by luks911 on 2008-11-29
También podrías revisar la línea del GRUB para que cargue Ubuntu, capaz que se eliminó o agregó algo que hace que se inicie sin el usplash.

---

### Post by lega on 2008-11-29
estan instalados, voy a revisar el grub, gracias

---

### Post by Hei Ku on 2008-11-29
Pone la linea que usa para cargar, probablemente le falta el splash o el quiet.

---

### Post by lega on 2008-11-29
pego boot/grub/menu.lst


```
title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		0c6e56e6-148b-4f41-ad60-7156a6f49dee
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=0c6e56e6-148b-4f41-ad60-7156a6f49dee ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		0c6e56e6-148b-4f41-ad60-7156a6f49dee
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=0c6e56e6-148b-4f41-ad60-7156a6f49dee ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		0c6e56e6-148b-4f41-ad60-7156a6f49dee
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=0c6e56e6-148b-4f41-ad60-7156a6f49dee ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		0c6e56e6-148b-4f41-ad60-7156a6f49dee
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=0c6e56e6-148b-4f41-ad60-7156a6f49dee ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		0c6e56e6-148b-4f41-ad60-7156a6f49dee
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:[COLOR="Red"]esta parte es la de Ubuntu[/COLOR]
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb5.
title		Ubuntu 8.10, kernel 2.6.27-9-generic (on /dev/sdb5)
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=5edfd76b-35e9-4d2d-9211-b8207a10db39 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb5.
title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode) (on /dev/sdb5)
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=5edfd76b-35e9-4d2d-9211-b8207a10db39 ro single 
initrd		/boot/initrd.img-2.6.27-9-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb5.
title		Ubuntu 8.10, kernel 2.6.27-7-generic (on /dev/sdb5)
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=5edfd76b-35e9-4d2d-9211-b8207a10db39 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb5.
title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode) (on /dev/sdb5)
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=5edfd76b-35e9-4d2d-9211-b8207a10db39 ro single 
initrd		/boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb5.
title		Ubuntu 8.10, memtest86+ (on /dev/sdb5)
root		(hd1,4)
kernel		/boot/memtest86+.bin  
savedefault
boot


```

---

### Post by hictio on 2008-11-29
Que raro, en el config no se ve nada raro (publicaste SOLO la seccion de kernels, verdad?)
Una pregunta, cuando booteas con Ubuntu, al finalizr el booteo en texto, te levanta el login grafico, o tenes que loggearte en consola y levantarlo?

---

### Post by lega on 2008-11-29
levanta lo más bien el modo gráfico sin hacer nada, pegue todo  el menu.lst menos la parte de ejemplos creo que es.

---

### Post by sajnox on 2008-11-30
Un buen programa para manejar todas las opciones de arranque del grub es el StartUp Manager, esta en los repositorios

```
sudo apt-get install startupmanager
```

Lo deja en Sistema > Administracion > Administrador de Arranque

---

### Post by lega on 2008-11-30
lo tengo instalado, y si bien no toque nada como para que haya pasado esto me fije y las opciones del splash, creo que están bien.

---

### Post by EnriqueK on 2008-11-30
Fijate si no tenés un respaldo del menu.list , seguramente no te a a servir para reemplazar por que seguramente indican kernel diferentes,  pero al menos puede que te sirva como guía , podrías imprimirlas a las dos y ver las discrepancias.
También tengo ese problema y estoy seguro que se presentó después de instalar otras distros y que después borré, la verdad es que ni intenté arreglarlo.

---

### Post by lega on 2008-11-30
La verdad es que no me preocupa demasiado, solo lo puse acá por si a alguien más le había pasado y lo había solucionado, también no es la primera que me pasa y siempre me paso al querer instalar otra distro en el segundo disco rígido, me paso teniendo Hardy, y ahora con Intrepid como ditro principal digamos.

Pero bueno si a nadie le pasó quedará asi, tampoco es tan grave.

---

### Post by pol666 on 2008-12-01
Toma Lega tu problema es este. aca explican como solucionarlo

[http://ubuntulife.wordpress.com/2008/11/30/ubuntu-usplash-smooth/]("http://ubuntulife.wordpress.com/2008/11/30/ubuntu-usplash-smooth/")

---

### Post by lega on 2008-12-01
Negativo :P eso es para que la barra avance progresivamente de acuerdo a como el sistema va cargando, ahora, para los que tienen la barra, avanza a los ponchazos, a mi, la barra me desaparece a los 2 segundos y sigue cargando en modo texto.

Gracias igual pol666

---

### Post by SLA_leandrin on 2008-12-01
Sip. Lo mismo me pasó a mi con el startupmanager.
Bah en definitiva ni tanto drama que me hice, al final de cuentas está bueno que se inicie en texto para poder ir viendo ahi nomás q es lo que se carga bien (o no)...

---

