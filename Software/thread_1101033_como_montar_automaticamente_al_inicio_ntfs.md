---
title: "como montar automaticamente al inicio ntfs"
date: 2009-03-19
forum: Software
---

### Post by tsueseres on 2009-03-19
tengo una particion ntfs la cual ubuntu la reconoce como sda1 la cual kiero que se monte automaticamente con cada inicio del sistema pero no ayo los comandos correctos para poner en el fstab

---

### Post by santiagoward2000 on 2009-03-19
> **tsueseres said:**
> tengo una particion ntfs la cual ubuntu la reconoce como sda1 la cual kiero que se monte automaticamente con cada inicio del sistema pero no ayo los comandos correctos para poner en el fstab

Hola!
La más simple, es instalar **ntfs-config**, después lo abrís, seleccionás el disco que querés que se automonte y listo!
Saludos!

---

### Post by tsueseres on 2009-03-20
> **santiagoward2000 said:**
> Hola!
La más simple, es instalar **ntfs-config**, después lo abrís, seleccionás el disco que querés que se automonte y listo!
Saludos!

gracias por la respuesta, ya lo instale pero tengo un problema cuando intento desmontarlo me sale que solo es usuario root puede desmontar y montarlo

---

### Post by santiagoward2000 on 2009-03-20
> **tsueseres said:**
> gracias por la respuesta, ya lo instale pero tengo un problema cuando intento desmontarlo me sale que solo es usuario root puede desmontar y montarlo

Mmm, ahora que lo decís, me pasa lo mismo. Creo que nunca traté de desmontarlo antes...

---

### Post by faktorqm on 2009-03-20
Abri una consola y pone "sudo umount /carpeta/donde/montaste" sin comillas y te va a pedir tu contraseña, la pones y listo. salu2!

---

### Post by santiagoward2000 on 2009-03-20
> **faktorqm said:**
> Abri una consola y pone "sudo umount /carpeta/donde/montaste" sin comillas y te va a pedir tu contraseña, la pones y listo. salu2!

Lo que me parece raro es que antes de configurar el automount con **ntfs-config** se podía montar y desmontar sin tener que usar sudo.

---

### Post by tsueseres on 2009-03-20
> **faktorqm said:**
> Abri una consola y pone "sudo umount /carpeta/donde/montaste" sin comillas y te va a pedir tu contraseña, la pones y listo. salu2!

se puede hacer automaticamente sin necesidad de estar abriendo una consola y usar sudo, es por medio de los comandos en el fstab pero no se cuales son esos comandos

---

### Post by NickCis on 2009-03-21
> **tsueseres said:**
> tengo una particion ntfs la cual ubuntu la reconoce como sda1 la cual kiero que se monte automaticamente con cada inicio del sistema pero no ayo los comandos correctos para poner en el fstab

No es mas facil editar el "/etc/fstab" ? Agregarle una linea al final asi:
```
/dev/sda1 /media/disk ntfs defaults,rw,users,auto,iocharset=utf8,umask=000 0 0
```

Creo que hace falta crear la carpeta /media/disk a mano... (90% seguro d esto...)

Saludos.

---

### Post by Hei Ku on 2009-03-21
si, la carpeta donde vas a montar un disco, imagen, lo que sea, tenes que crearla a mano.

---

### Post by tsueseres on 2009-04-04
> **Hei Ku said:**
> si, la carpeta donde vas a montar un disco, imagen, lo que sea, tenes que crearla a mano.

gracias por la respuesta me funciona pero solo a un 50% ya que si puedo desmontarla pero cuando intento mantarla denuevo no me deja, tengo que ser usuario root para poder vover a montarla, hay alguna manera de montar y demontar cuando quiera sin necesidad de root?

---

### Post by Mauro22 on 2009-04-04
Hola!!


mira, yo lo tengo asi:

```
/dev/sda2 /media/ACER ntfs auto,rw,exec,users,dmask=000,fmask=111,nls=utf8 0 0
```

Pero pasa lo mismo, se monta automaticamente al iniciar, pero si lo desmontas y lo volves a montar te pide contraseña.. Pero como yo no tengo motivo para desmontarlo, no me molesta!



El problema no es al montar un disco ntfs con mount, sino que el problema es FUSE NTFS-3G, ese te pide la contraseña.

---

### Post by Hei Ku on 2009-04-04
Ojo, no es que tenes que ser root, sino que tendrias que usar sudo para volver a montarla.

Vos queres que cualquier usuario pueda montar y desmontar la particion?

---

### Post by tsueseres on 2009-04-05
> **Hei Ku said:**
> Ojo, no es que tenes que ser root, sino que tendrias que usar sudo para volver a montarla.

Vos queres que cualquier usuario pueda montar y desmontar la particion?

si quiero que cualquier usuario pueda montar y desmontar la particion

---

### Post by Hei Ku on 2009-04-05
Como quedo tu fstab?
Agregando la opcion user deberian poder montar y desmontar sin problemas.
Les va a pedir la contraseña, pero es su contraseña la que tienen que poner. Eso tampoco queres?

---

### Post by tsueseres on 2009-04-05
> **Hei Ku said:**
> Como quedo tu fstab?
Agregando la opcion user deberian poder montar y desmontar sin problemas.
Les va a pedir la contraseña, pero es su contraseña la que tienen que poner. Eso tampoco queres?


quiero que sea libre de contraseña como cuando se pone un disco duro externo una vez dentro del sistema el cual se monta automaticamente una vez insertado y se puede desmontar por el usuario y volver a montar sin nececidad de contraseña

---

### Post by Hei Ku on 2009-04-05
Esto debería solucionar eso. Yo no lo recomiendo, pero es tu computadora.

```

sudo chmod 4755 /bin/ntfs-3g

```

---

### Post by tsueseres on 2009-04-06
> **Hei Ku said:**
> Esto debería solucionar eso. Yo no lo recomiendo, pero es tu computadora.

```

sudo chmod 4755 /bin/ntfs-3g

```

gracias, oye me podrias explicar como funciona (que es chmmod y el numero 4755)

---

### Post by faktorqm on 2009-04-07
En este thread hay una explicacion mia acerca de eso 

[http://ubuntuforums.org/showthread.php?t=952885](http://ubuntuforums.org/showthread.php?t=952885)

salu2!

---

### Post by sprop on 2012-04-30
A través de una GUI: Storage Device Manager. Simplemente fácil. Gracias Pablito.

[http://usemoslinux.blogspot.com/2011/11/como-auto-montar-particiones-al-inicio.html](http://usemoslinux.blogspot.com/2011/11/como-auto-montar-particiones-al-inicio.html)

---

