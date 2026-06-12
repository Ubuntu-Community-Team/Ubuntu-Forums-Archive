---
title: "Que &quot;maquina virtual&quot; me recomiendan para Ubuntu?"
date: 2008-08-17
forum: Software
---

### Post by PeTTi on 2008-08-17
[FONT=Century Gothic]El tema es asi, yo quiero instalar Windows Xp en una maquina virtual, que programa me recomiendan ?

Tengo Ubuntu 8.04[/FONT]

---

### Post by pol666 on 2008-08-17
Virtual Box? VMWare?

este ultimo no lo probe, uso virtual box

---

### Post by PeTTi on 2008-08-17
[FONT=Century Gothic]me descargue el Virtual Box para Ubuntu, y lo instale todo bien, lo pongo para usar Windows Xp, puse el cd en la lectora de cd (el cd de Windows [original]) y me sale este error:
 [IMG]http://i36.tinypic.com/2qwls41.png[/IMG]
¿qué hago?[/FONT]

---

### Post by lega on 2008-08-17
fijate en synaptic sino tenes un paquete que se llame como el que dice el error que te falta instalar, **virtualbox-ose-modules-generic** o algo parecido.

---

### Post by PeTTi on 2008-08-17
> **lega said:**
> fijate en synaptic sino tenes un paquete que se llame como el que dice el error que te falta instalar, **virtualbox-ose-modules-generic** o algo parecido.
sigue igual...

> 
The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).


Código Resultado: 
0x80004005
Componente: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

 

---

### Post by lega on 2008-08-17
Probá con esto 
```
 sudo gpasswd -a nombre_de_tu_cuenta vboxusers
```

…borramos el módulo de VirtualBox y lo volvemos a cargar:

```
sudo rmmod vboxdrv && sudo modprobe vboxdrv
```


Lo saque de acá, es un tutorial muy completo, [Virtualbox: Windows en Ubuntu]("http://tuxpepino.wordpress.com/2007/05/29/virtualbox-windows-en-ubuntu-linux/")

---

### Post by fiddler616 on 2008-08-17
Hay un articulo excelente aqui:
[http://www.freesoftwaremagazine.com/articles/using_virtualbox_to_run_ubuntu](http://www.freesoftwaremagazine.com/articles/using_virtualbox_to_run_ubuntu)
pero est'a in ingle's--si quieres, lo puedo traducir a espa~nol (y ojal'a que arregle mi teclado para que puedo teclar con tildes)

---

### Post by pol666 on 2008-08-17
Hay un articulo muy simplificado en mi blog

[http://tuxear.wordpress.com]("http://tuxear.wordpress.com")

Es la  pentultima entrada, la que dice "¿windows para que?"

Basicamente lo que tenes que hacer es instalar el ose-guest-module de acuerdo a tu kernel, y despues darle permiso de administracion a tu usuario en el grupo virtual box

---

### Post by victor_nesta on 2008-08-17
Pol666, no sabia que era tu blog, Te felicito!

PeTTi, mepa que la de Pol666 es mas completa, pero yo lo instale según esta guía (no había visto la de tuxear :lolflag:)
```
http://tuxpepino.wordpress.com/2007/05/29/virtualbox-windows-en-ubuntu-linux/
```

---

### Post by sajnox on 2008-08-17
Hola, si mal no recuerdo yo tambien lo instale la primera vez con el tutorial de entre tuxes y pepinos, pero ya esta un poco viejo.

Por lo que dicen lo bajaste de la pagina de virtual box, probaste con instalarlo desde los repositorios?

Estas seguro que el que bajaste es el de tu version de Ubuntu, el de la 7.10 no funciona en la 8.04 y viceversa, y ademas tenes que estar seguro que tu user esta dentro del grupo de usuarios vbox, esto lo podes hacer desde la opcion de usuarios y grupos

Saludos

---

### Post by victor_nesta on 2008-08-17
es verdad, y vale la aclaración de mi parte que lo baje desde la pagina oficial de virtualbox 1.6.4 en un .deb hermoso

---

### Post by pol666 on 2008-08-17
Cabe aclarar que obvié lo de los repositorios. No se como se comportara al version de la pagina oficial, solo esta asegurado en la version de repositorios.

---

