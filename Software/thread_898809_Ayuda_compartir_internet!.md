---
title: "Ayuda compartir internet!"
date: 2008-08-23
forum: Software
---

### Post by fernando.ffff on 2008-08-23
Hola! soy nuevo en esto :lolflag: &#8230; En mi casa hay dos computadores, la mia tiene dos placas de red ( una que va al modem y otra que va a la otra compu) tengo ubuntu 8 y xp que le comparte internet a la otra que tiene nada mas que xp ( la otra no la uso yo)&#8230; De xp a xp es re facil se configura todo solo con el asistente de configuracion de red&#8230; Pero yo quiero usar ubuntu 8!!!! por que no trae un asistente que te facilite las cosas???!!! :confused: &#8230; Les cuento que hice como 3 tutoriales diferentes con scrips samba etc etc y ninguno funciono por ejemplo cuando uso la opcion de el firestarter, este me da a elegir entre eth0, eth1 y ppp0 cuando me pregunta la tarjeta que recibe internet, como hago para saber cual es???  al configurar manualmente las ip dns etc en el xp de la otra compu deja de decir &#8220;conexion limitada o nula&#8221; y aparecen las dos computardorcitas en la barra de estado como que esta conectado, pero no navega!&#8230; a y también al ultimo, el firestarter, dice que no puede iniciar el cortafuegos que no esta listo el dispositivo que "compruebe la conexión" esto es normal? por que en ubuntu navego perfecto y la conexión la activo y configuro con &#8220;sudo pppoeconf&#8221;&#8230; Si no logro darle internet al xp pronto voy a tenes que desisntalar ubuntu y no quiero :( &#8230; Algun genio que me ayude porfa!&#8230; Saludos! :)

---

### Post by pol666 on 2008-08-23
para che que no tengo ni astigmatismo ni daltonismo

---

### Post by pablo atheist on 2008-08-23
para lo del firestarter abrí una terminal y escribi

```
 sudo gedit /etc/firestarter/firestarter.sh
```

después tenes que cambiar la linea

```
MASK=`/sbin/ifconfig $IF | grep Mas | cut -d : -f 4`
```

le tenes que agregar el tilde al mas o sea que quede

```
MASK=`/sbin/ifconfig $IF | grep Más | cut -d : -f 4`
```

ahora acá dejo un guía para configurar firestarter

[http://siemprelinux.wordpress.com/2007/04/12/como-instalar-y-configurar-firestarter/](http://siemprelinux.wordpress.com/2007/04/12/como-instalar-y-configurar-firestarter/)

yo después lo que hago para compartir es escribir 
```
sudo nautilus
```
después elijo la carpeta a compartir y le doy click derecho y elijo "opciones de compartición" y después marcas "compartir esta carpeta" y también "acceso de invitado"

Otra cosa recomendable es en la barra de direcciones del nautilus poner directamente la dirección ip de la pc que queres acceder, o sea poner
```
smb://dir-ip/
```

Finalmente si queres compartir una carpeta ntfs tenes que hacer bocha de cosas mas como compilar fuse y editar el fstab , asi que si queres después te explico mas en detalle como compartir una carpeta ntfs...

saludos

---

