---
title: "help de /home viejo a nuevo"
date: 2009-05-01
forum: Software
---

### Post by cartos on 2009-05-01
hola gente como va? nesecito de su ayuda,

acabo de instalar el 9.04 y en la istalacion cuando me hablaba de las particiones no le puse que en la particion donde esta todo el /home sea la misma ni que la queria formatear es que tenia miedo que me lo borre... ahora mi preguta es como ubuco mi viejo /home en el nuevo y que quede este en la particion en que está.

disculpen mi pregunta pero cuando es tema de particiones me da panico cuando no conosco del sistema.


saludos a la banda!!!

---

### Post by gmunioz on 2009-05-02
Hola car.....:

Algo confuso tu post.

Puede que tu problema sea:

Tenias /home en partición separada.

Instalaste sin montar la partición, con /home dentro de /

Estas usando el mismo usuario y contraseña.

Quieres que tu antigua partición /home vuelva a ser /home.

Si esto es asi.

Debes iniciar en modo recuperación con la opción del submenu root 

o netroot, lo haras como administrador sin contraseña en consola.

Debes renombrar /home a /oldhome

Debes crear un nuevo /home

Debes montar, editando fstab la partición antigua /home en /home

Reiniciar, mover lo de /oldhome que necesites a /home y borrar /oldhome.

Saludos.

---

### Post by z37a on 2009-05-02
> **gmunioz said:**
> Hola car.....:

Algo confuso tu post.

Puede que tu problema sea:

Tenias /home en partición separada.

Instalaste sin montar la partición, con /home dentro de /

Estas usando el mismo usuario y contraseña.

Quieres que tu antigua partición /home vuelva a ser /home.

Si esto es asi.

Debes iniciar en modo recuperación con la opción del submenu root 

o netroot, lo haras como administrador sin contraseña en consola.

Debes renombrar /home a /oldhome

Debes crear un nuevo /home

Debes montar, editando fstab la partición antigua /home en /home

Reiniciar, mover lo de /oldhome que necesites a /home y borrar /oldhome.

Saludos.

Me parece que seria mas rapido y facil si va al gparted, lee el UUID de la particion y edita con el gedit el archiv /etc/fstab para montar su viejo home en el /home, los datos que estan ahi adentro quedan sin ser vistos, si bien son un par de megas al dope tiene un backup mas rapido asi y no necesita star usando la consola de recuperacion.

---

### Post by Hei Ku on 2009-05-02
Es cierto, con cambiar el fstab para que monte la vieja particion home y reiniciar, deberia ser suficiente. Yo lo hice así una vez que reinstale.

---

### Post by infernus92 on 2009-05-02
o sea que lo que hice yo de hacer backup en otro disco y despues de la instalacion volver a copiar los archivos fue al dope... lo que uno se entera en el foro... pero bueno... por lo menos tengo de consuelo que anduvo sin problemas :P

Saludos

---

### Post by z37a on 2009-05-02
> **infernus92 said:**
> o sea que lo que hice yo de hacer backup en otro disco y despues de la instalacion volver a copiar los archivos fue al dope... lo que uno se entera en el foro... pero bueno... por lo menos tengo de consuelo que anduvo sin problemas :P

Saludos

En realidad si, por que durante la instalacion dejas destildado el formatear y pones utilizar como... en la particion vieja y fue.

---

