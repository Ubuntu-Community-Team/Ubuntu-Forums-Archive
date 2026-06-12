---
title: "No inicia el administrador de red"
date: 2009-09-11
forum: Software
---

### Post by JUTGtgRB7z on 2009-09-11
Entre el título y la imagen lo digo todo :P. Es Ubuntu recién instalado, la segunda vez que inició me mostró este mensaje. Si alguien me dice que paquetes tengo que instalar me viene bién. Gracias.:)
[IMG]http://i437.photobucket.com/albums/qq94/pmzerdan/Varios/Pantallazo-1.png[/IMG]

---

### Post by Hei Ku on 2009-09-14
Pudiste resolver esto? Podes arrancarlo desde la terminal, asi nos tira mas pistas?

---

### Post by pablo.s on 2009-09-14
Gestor de la Red?
Network Manager...

```
sudo apt-get install network-manager network-manager-gnome
```

---

### Post by JUTGtgRB7z on 2009-09-26
Perdón me colgué con este tema. La cosa es que no lo puedo instalar como vos dices pablo xq directamente no tengo conexion desde ubuntu.

---

### Post by pablo.s on 2009-09-26
Desde Windows podés bajar los
archivos [acá]("http://packages.ubuntu.com/jaunty/network-manager") y [acá]("http://packages.ubuntu.com/jaunty/network-manager-gnome"). Luego los
instalas en Ubuntu con GDebi.

---

### Post by emiliano_raso on 2009-09-26
> **pablo.s said:**
> Desde Windows podés bajar los
archivos [acá]("http://packages.ubuntu.com/jaunty/network-manager") y [acá]("http://packages.ubuntu.com/jaunty/network-manager-gnome"). Luego los
instalas en Ubuntu con GDebi.

Si eso no te funciona, entonces probá conectarte por consola. Si no recuerdo mal era:
```
sudo pppoeconf
```

---

### Post by JUTGtgRB7z on 2009-09-27
Problema parcialmente resuelto :P Ahora se conecta pero me sigue apareciendo el mensaje ese. Eso que reinstalé ubuntu ¿puede ser que se deba a conflictos con el home de xubuntu? Porque antes tenía xubuntu y al home no lo toqué directamente se lo asigné al ubuntu.

---

