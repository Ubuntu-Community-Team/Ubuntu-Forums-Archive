---
title: "ayuda con el menu.lst para booteo"
date: 2008-06-25
forum: Software
---

### Post by Blacho on 2008-06-25
hola... tengo un problemita con mi booteo....
tengo un hdd como primarymaster con ubuntu
y otro hdd como primaryslave con windows
en el archivo menu.lst agregue la opcion para que en la lista de boot tenga windows.. pero cuando selecciono windows dice "starting up" y no pasa nada.... no se si esta bien mi comando en el archivo menu.lst... sera eso nomas?

esto es lo q le agregue al archivo... no cambie el default porq quiero mantenerlo en ubuntu... pero de vez en cuando tengo q entrar a windows y no pasa nada... tengo q desconectar mi hdd primarymaster para poder entrar

title Microsoft Windows XP Professional
root (hd1,0)
savedefault
makeactive
chainloader +1


cualquier ayuda sera bienvenida!

---

### Post by faktorqm on 2008-06-25
Busca dentro de este mismo sub-foro que el tema se hablo 1500 veces... Salu2!

---

### Post by Blacho on 2008-06-25
eh! perdon viejo... busque muchisimo y no encontre el caso en el q estan en dos hdd diferentes... voy a seguir buscando

---

### Post by faktorqm on 2008-06-26
Todos estos tienen 2 discos, el primer link lo dice en el titulo...

[http://ubuntuforums.org/showthread.php?t=837351](http://ubuntuforums.org/showthread.php?t=837351)
[http://ubuntuforums.org/showthread.php?t=807524](http://ubuntuforums.org/showthread.php?t=807524)
[http://ubuntuforums.org/showthread.php?t=785336](http://ubuntuforums.org/showthread.php?t=785336)
[http://ubuntuforums.org/showthread.php?t=758672](http://ubuntuforums.org/showthread.php?t=758672)
[http://ubuntuforums.org/showthread.php?t=743142](http://ubuntuforums.org/showthread.php?t=743142)

Postea el menu.lst completo. Vos ahi pusiste la parte de windows no mas, digo, si es (hd1,0) el linux deberia ser (hd1,1), el numero de la derecha es el numero de disco segun como te los toma linux. para eso tambien podes hacer "sudo fdisk -l" y grub en lugar de empezar con 1 la numeracion la empieza con cero, asi /dev/hda2 va a ser (hd0,0) por ejemplo, y /dev/hdc3 va a ser (hd2,2). Salu2!

---

