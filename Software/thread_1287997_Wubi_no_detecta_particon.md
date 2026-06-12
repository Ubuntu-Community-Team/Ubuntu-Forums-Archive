---
title: "Wubi no detecta particon"
date: 2009-10-10
forum: Software
---

### Post by Mauro22 on 2009-10-10
Holas


Tengo un consulta, hoy instalé ubuntu en un PC de amigo, lo instalé con Wubi para hacer mas rapido por una cuestion de tiempo..


El problema es el siguiente... En Xp hay dos particiones C y D... Wubi se instaló en C en donde esta el sistema xp (otra no dejaba instalar). Lo raro es que, una vez en ubuntu, el "D" no aparece, solo la particion donde esta el xp, lo que no me sirve porque los datos los tiene en el D...


Que puede ser? problemas de Wubi? o algo que hay que tocar?? Es lo que me falta, lo demas joya, y si se convence un Ubuntero mas...



:guitar:

---

### Post by gmunioz on 2009-10-11
Hola mau....:

Debes montar la partición.

Crea el directorio

```
sudo mkdir /media/discoD
```

Dale permisos de lectura escritura

```
sudo chmod -Rf 777 /media/discoD
```

Monta la partición

```
sudo mount /dev/sda**?**   /media/discoD
```

---

### Post by Mauro22 on 2009-10-11
Que bola, me olvidé de hacer eso...


Pero yendo al caso, es "normal" que detecte una particion si y una no? 

Voy a probar eso cuando pueda y te aviso! Grax!

---

