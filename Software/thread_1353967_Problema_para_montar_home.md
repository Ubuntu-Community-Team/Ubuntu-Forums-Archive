---
title: "Problema para montar /home"
date: 2009-12-13
forum: Software
---

### Post by feche_mza on 2009-12-13
bueno la cosa es asi, cuando arranco el linux en el booteo me tira este error, que no puede montar la particion /home.
tengo un kubuntu 9.10 y en la instalacion lo dividi para poder probar otras distros sin tener que andar haciendo backup de datos cada ves, asique tengo una particion de 10Gb con el punto de montaje / ,y otra de 130Gb con el punto de montaje /home , todo venia andando bien hasta ayer que quise entrar y me tiro este error , trate de montarla manualmente pero no me deja, me dice que no exixte la particion, lo mas lindo es que con un live cd si puedo entrar y la monta lo mas bien.
porfa tirenme algun consejo por que se me acaban las ideas :S

---

### Post by alfplayer on 2009-12-13
/home está en buen estado? Se puede intentar hacer chequeo y reparación con fsck desde el live cd.

---

### Post by juancarlospaco on 2009-12-13
**sudo fsck -v**

---

### Post by feche_mza on 2009-12-19
ahi probe y nada... 
aparentemente esria todo ok , no entiendo por que no lo monta

---

### Post by alfplayer on 2009-12-19
No existe la partición... es raro. Seguro que se está usando el comando mount correctamente? Haciendo referencia al dispositivo correcto (por ejemplo /dev/sdb2)?

---

### Post by feche_mza on 2010-01-21
bueno aver, despues de mucho renegar llegue al fondo del problema
aunque no entiendo por que el error, la cosa es que tengo una particion con win7 (una porong..)
y para poder jugar al gears tengo que retrasar la fecha de la pc hasta el 2007.
al parecer cuando cambio la fecha y antes de reiniciar no la pongo al dia no me monta la particion /home ..... :confused: :confused: rarisimo

---

