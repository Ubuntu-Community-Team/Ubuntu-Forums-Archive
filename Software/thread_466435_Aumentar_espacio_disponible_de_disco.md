---
title: "Aumentar espacio disponible de disco"
date: 2007-06-06
forum: Software
---

### Post by agrelot on 2007-06-06
En mi "carpeta personal" hay solo 2G asignado y ya me quedé sin lugar, pero es paritición del disco tiene 9G... ¿Cómo puedo hacer para aumentarme el disco disponible para mi usuario ppal?.
Uso Feisty Fawn

---

### Post by fetova on 2007-06-07
Ejecuta
```
sudo aptitude clean
```

Te va a dar como un gb, dependiendo...

Saludos

---

### Post by MrJaco on 2007-06-07
a mi me pasa lo mismo, pero el tema es en /home...
hice lo que dijiste vos y me saco 200 megas del disco conde tengo instalado ubuntu..

el home es de 21.3 gb, estoy usando 2.8 gb y tengo libres 17.3 gb...
21.3 - 2.8 = 18.5 :(
no se de que puede ser lo que falta de espacio, pero bue... si alguien sabe que puedo hacer, se lo agradesco.

---

### Post by fetova on 2007-06-07
> **MrJaco said:**
> a mi me pasa lo mismo, pero el tema es en /home...
hice lo que dijiste vos y me saco 200 megas del disco conde tengo instalado ubuntu..

el home es de 21.3 gb, estoy usando 2.8 gb y tengo libres 17.3 gb...
21.3 - 2.8 = 18.5 :(
no se de que puede ser lo que falta de espacio, pero bue... si alguien sabe que puedo hacer, se lo agradesco.

usa: ```
baobab
``` y analiza tu carpeta personal, ve lo que no te sirva y y con eso te vas liberando... es un analizador de espacio en disco

---

### Post by agrelot on 2007-06-08
Perdón amigos , quizás no me supe expresar claramente.
Lo que quiero hacer NO es hacer lugar borrando cosas. Lo que quiero es AUMENTAR la cantidad de disco asignada a este usuario, porque en la partición aún hay mucho lugar libre al que no tengo acceso. ¿Se puede hacer esto?

---

### Post by Vampirus on 2008-10-17
hola, tengo el mismo problema y queria saber como lo solucionaste, ya que estuve buscando pero no encuentro nada. Saludos

---

### Post by victor_nesta on 2008-10-17
mmmm, no se si entendí bien pero, si lo que queres hacer es sacarle espacio a una partición para dársela a otra, podes probar instalándote el gparted que esta en los repositorios.

Yo no tuve problema, pero te recomiendo googlea un poco y fíjate si puede haber algun problema o fallo, si modificas particiones de sistema.
Te repito yo no tuve problema, pero...

---

### Post by EnriqueK on 2008-10-17
Se me ocurre que lo que podés hacer es mover archivos y carpetas pesadas desde la del usuario a otra partición con formato propio de linux (EXT3, Reiserfs, etc )y seguidamente en la carpeta de usuario le ponés enlaces simbólicos a esos archivos y carpetas que has movido, así todo queda casi igual, osea con acceso desde la carpeta del usuario, pero la ubicación real en otra partición, de esta manera te evitás el estar redimensionado particiones que puede llegar a ser hasta imposible por la dispononibilidad física de las mismas. Recuerdo que una vez hice la prueba moviendo la carpeta .wine que puede llegar a pesar bastante por que allí se alojan los programas instalados con Wine, funcionó muy bien, Wine ni se enteró que su carpeta fué movida de lugar .

---

### Post by Thalskarth on 2008-10-17
Una pregunta... les asignaste cuotas de espacio a los usuarios estableciendoles un limite máximo de espacio disponible a usar por cada uno?? 

Porque, por defecto, en ubuntu... el usuario siemrpe tiene disponible el total del espacio de la particion donde este el home para usar...


Si lo hiciste con cuotas, editando las cuotas podes agrandar el espacio. [Aca podes leer como hacerlo]("http://doc.ubuntu-es.org/Gesti%C3%B3n_de_usuarios_y_grupos")

---

### Post by guisheca on 2008-10-18
Agrlot, me parece que no te entienden un pomo jajajaja, pero creo que se lo que querés decir, pero para no meter la pata quiero que me digas una cosa: Que tamaño tiene tu disco rígido??

---

### Post by GoodByeBlueSky on 2008-10-20
yo tengo el mismo problema,tengo el disco de 100gb utilizado tengo 30 y pico y libre 60  pico,el tema es que quiero instalar por darles un ejemplo,el lineage II y me dice que no tengo espacio en el disco cuando tengo mas de 60gb libres,es el mismo problema que tiene el usuario que creo este thread,cuando entro a las propiedades de una carpeta me dice que tengo 2gb y pico libres nomas cuando en realidad no es asi,vengo hace dias googleando hice miles de cosas y no pasa nada si me podrian ayduar se los agradeceria!!!
adios!!

---

### Post by sebastianabate on 2008-10-20
Los que tengan el problema del espacio en disco (les dice que tienen menos espacio libre que el que tienen en realidad), podrían postear el contenido del archivo /etc/fstab?

---

### Post by GoodByeBlueSky on 2008-10-20
> **sebastianabate said:**
> Los que tengan el problema del espacio en disco (les dice que tienen menos espacio libre que el que tienen en realidad), podrían postear el contenido del archivo /etc/fstab?

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext3    loop,errors=remount-ro 0       1
/host/ubuntu/disks/boot /boot           none    bind            0       0
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0




ese es el contenido de /etc/fstab que tengo yo y tengo el mismo problema.
gracias y adios.

---

### Post by c4d0rn4 on 2008-10-21
solo por curiosidad, alguno se fijó en gparted como está distribuido el rigido?

dejo como ejemplo el mio.

[http://img249.imageshack.us/img249/9279/gpartedmv0.png](http://img249.imageshack.us/img249/9279/gpartedmv0.png)

hay una parte que dice unallocated con 1.88mb, esa parte del rigido no pertenece a ninguna partición, no tiene formato y es como disco muerto.

Por si las dudas, la idea es descartar que esten sin asignar esos gigas que dicen, y la otra es que esten como X partición y que no la tengan montada.


-----------

off:

> **guisheca said:**
> Agrlot, me parece que no te entienden un pomo jajajaja, pero creo que se lo que querés decir, pero para no meter la pata quiero que me digas una cosa: Que tamaño tiene tu disco rígido??
el mio tiene a ojo unos 12x30cm (fruta) xD
jajaj xD

perdón, fue más fuerte que yo.

---

### Post by chalito on 2008-10-22
Podrían postear acá el resultado del comando:

```
df -Th
```

Así vemos como se está usando el espacio. Recuerden que puede haber archivos en la papelera, y además ext3 reserva por default 5% del espacio en cada particion para root (se usa para que el administrador pueda loguearse en el sistema incluso en caso de tener el sistema lleno).
Esto se puede cambiar con tune2fs, pero no recomendaría hacerlo en la partición root (/). Sí es seguro hacerlo en /home.

---

### Post by Kabezon on 2008-10-22
A mí me pasa exactamente lo mismo... Veamos, yo tengo la partición /home de 360.89GB y tengo en ella sólo 42.8GB ocupados (Viendo sus propiedades). Sin embargo, sale que me quedan 299.90GB libres... 

360.89 - 042.80 = 318.09     
318.09 - 299.09 = 019.00

Entonces, la gran pregunta es: ¿Qué está ocupando esos otros 19GB?

Miren esto, 0 sentido o.O
> kabezon@Alheli:~$ df -Th
S.ficheros    Tipo    Tamaño Usado  Disp Uso% Montado en
/dev/sda1     ext3    7.0G  3.7G  3.0G  55% /
varrun       tmpfs    950M  108K  950M   1% /var/run
varlock      tmpfs    950M     0  950M   0% /var/lock
udev         tmpfs    950M   60K  950M   1% /dev
devshm       tmpfs    950M  832K  949M   1% /dev/shm
lrm          tmpfs    950M   39M  911M   5% /lib/modules/2.6.24-21-generic/volatile
**/dev/sda3     ext3    361G   44G  300G  13% /home**


Hasta el día de hoy pensaba que era normal, porque fijense que pasa con todas las particiones. Es normal ¿No? o.O

---

### Post by chalito on 2008-10-22
Como dije más arriba, Ext3 por default te reserva 5% del disco para uso exclusivo de root.

si tenes un disco de 361GB, el 5% de eso son 18GB.
300 + 44 + 18 = 362 (errores de redondeo).

esta todo ahi.

Si queres que no te saque ese 5% en /home, podes usar el comando:
tune2fs -m 0 /dev/sda3

pero no lo hagas sobre / porque si un dia se tellena el disco puede traer problemas. bah tendrias que bootear desde un livecd y borrar algo, ponele, pero mas facil dejarle el 5% disponible y ya.. o si queres reducilo a 1% o algo asi.

---

### Post by rodolfojavier1982 on 2008-10-23
Lo que a mi me pasaba era que para mi usuario tenia menos de 1GB libre en un momento, y entrando como root tenia como 7 GB libres, como nunca o casi nunca entraba como root lo que hice fue tratar de utilizar esos GB libres de root.
Desde root entre a la carpeta principal (/) y me cree una carpeta que llame (no importa el nombre) prsnl_usrs, alli cree una carpeta para cada usuario del sistema, por ej usr1 usr2 usr3, (menos para root) y en cada una le puse como propietario al correspondiente. Ahora cada usuario tiene la posibilidad de escribir en esas carpetas, usando el espacio que tenia solo el usuario root.
Espero que les sirva.
Saludos.

---

