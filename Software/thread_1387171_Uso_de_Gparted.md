---
title: "Uso de Gparted"
date: 2010-01-21
forum: Software
---

### Post by Iced1 on 2010-01-21
Hola me gustaria redimensionar la particion de ubuntu, pero gparted no me deja, antes tenia instalado windows xp pero lo borre y quedo espacio en blanco, tengo que desmontar la particion de ubuntu, aqui ahy un imagen de como tengo mi disco duro en forma grafica

[http://img191.imageshack.us/img191/9468/pantallazoj.png](http://img191.imageshack.us/img191/9468/pantallazoj.png)

Lo que quiero hacer es aumentar la particion de ubuntu en 40gb de los 54,2 libres y los 14,2 gb libres que quedan dejarlos sin asignar para una futura instalacion de windows...

Como tendria que hacer esto? o tendre que crear una nueva tabla de particiones, si tengo que hacer eso como lo tendria que hacer para guardar la configuracion que tengo ahora en ubuntu

---

### Post by moreback on 2010-01-21
Para que puedas editar las particiones de una unidad montada (si está montada no se puede editar ya que tienes que desmontarla para hacerlo, el problema es que como tienes el / montado finalmente no podrás desmontarlo, se entiende?) tienes que iniciar con el Live CD de Ubuntu correr Gparted (en menú Sistema -> Administración) desde ahí.

Saludos.

---

### Post by Carlos C on 2010-01-26
Salió una nueva versión de Gparted que parece arregla algunos problemas que había al redimensionar las particiones:

[http://www.gnomefiles.org/app.php?soft_id=396#0.5.1](http://www.gnomefiles.org/app.php?soft_id=396#0.5.1)

Tendrías que compilarlo o probar el paquete que acabo de hacer, aunque viene sin garantía ;)

[http://dl.dropbox.com/u/3697948/gparted_0.5.1_i386.deb](http://dl.dropbox.com/u/3697948/gparted_0.5.1_i386.deb)


Saludos.

---

