---
title: "Carpetas compartidas con Virtualbox entre UbuntuS?"
date: 2008-12-09
forum: Software
---

### Post by alberto71 on 2008-12-09
Hola. Si, un poco rara mi pregunta verdad? ya que normalmente se virtualiza XP o en el peor (muy peor) de los casos, Vista. En realidad, uso un Ubuntu virtualizado para probar programas y demás o comparar funcionamiento de las versiones, etc. 

Tengo Intrepid Ibex en mi pc y Hardy Heron en la maquina virtual. El problema se presentó al querer compartir un carpeta; con Vbox todo perfecto pero mi ignorancia me impidió "encontrar" la carpeta compartida desde mi Heron virtual. Por lo que leí, creo que "mount -t" es lo que necesito, el problema es que no sé como indicarle la ubicación de la carpeta compartida por el host (Intrepid Ibex).

Agradezco cualquier ayuda que puedan brindarme.

Saludos.

---

### Post by c4d0rn4 on 2008-12-10
primero instalá las guest tools
[http://ubuntu-tutorials.com/2007/10/13/installing-guest-additions-for-ubuntu-guests-in-virtualbox/](http://ubuntu-tutorials.com/2007/10/13/installing-guest-additions-for-ubuntu-guests-in-virtualbox/)

y después como montar la carpeta previamente selecionada y elegida como compartida en virtual box.

[http://forums.virtualbox.org/viewtopic.php?p=41160](http://forums.virtualbox.org/viewtopic.php?p=41160)

---

### Post by faktorqm on 2008-12-10
recien le pregunte a fmsismo y me dijo que con nfs salis andando. Salu2!

---

### Post by alberto71 on 2008-12-10
Hola de nuevo, gracias por las respuestas.

Siguiendo lo que leí en la pág 62 del manual de VBox decidí tomar el camino propuesto por c4d0rn4, aprovechando que ya tengo instaladas las Guests Aditions. Hice lo siguiente:

* En el host ejecuté: 

```
VBoxManage sharedfolder add "Ubuntu" -name **shared** -hostpath "**/media/Capturas/VMs/Share**"
```

donde **shared **es el nombre de la carpeta compartida y **/media/Capturas/VMs/Share** la ruta de la carpeta a compartir.

* Luego en la consola de la máquina virtual, ejecuté:

```
sudo mount -t  vboxsf shared "/media/Capturas/VMs/Share" 
```

y me devolvió:

```
sbin/mount.vboxsf: mounting failed with the error: No such file or directory
```

La carpeta a compartir, existe y tiene archivos y sub carpetas. Imagino que la pc virtual no puede acceder a la carpeta pero no comprendo porqué. 

Toy re perdido! :confused:

faktorqm: no sé a que te referís exactamente con nfs, si podés, por favor desasname. Por cierto, hace un tiempo usé tu manual para conectar pcs en red con Samba y logré hacer andar  mi Ubuntu + 1 XP + 1 Hackintosh a la perfección, de hecho, la que mejor anda en red es mi Ubuntu :p

Saludos.

---

### Post by faktorqm on 2008-12-10
Que es: [http://es.wikipedia.org/wiki/NFS](http://es.wikipedia.org/wiki/NFS)

Como instalarlo en la que comparte:

```
sudo apt-get install nfs-common nfs-server
```


Como instalarlo en la que se conecta:

```
sudo apt-get install nfs-common nfs-client
```

Como configurarlo:

El archivo /etc/exports contiene una lista de entradas, cada entrada indica que carpeta esta compartida y cómo. Para una descripcion mas completa podes usar "man exports" ;)

Un /etc/exports se ve mas o menos asi:

/home        192.168.0.1(rw)

Eso comparte el /home en modo lectura/escritura SOLO para la ip 192.168.0.1.

Si queres compartir la subred entera, en lugar de la ip va red/mascara asi:

/home        192.168.0.0/255.255.255.0(rw)

Eso te comparte desde la 0.1 hasta la 0.254 en modo lectura/escritura.

Bueno, cuando terminas de compartir lo que queres, le das a 

```
sudo /etc/init.d/nfs restart
```

para que tome los cambios y ahora editamos /etc/hosts.allow y ponemos

portmap: 192.168.0.1

de vuelta, si queres toda la subred corresponde

portmap: 192.168.

No olvides el punto al final. Teoricamente en el sitio de NFS dice que se banca la misma nomenclatura que el hosts.allow, pero el man portmap dice que va a asi. Si queres probarlo, adelante!

Lo que no me acuerdo si hice o no cuando lo levante el serer nfs es poner portmap:ALL en el /etc/hosts.deny. Probalo sin eso y sino agregalo :P

En el cliente tenes que poner: 

```
sudo mount 192.168.0.1:/home /mnt/home
```

y deberias salir andando. Cualquier duda consulta. Salu2!!!

sitio de nfs: [http://nfs.sourceforge.net/nfs-howto/](http://nfs.sourceforge.net/nfs-howto/)

---

### Post by alberto71 on 2009-04-05
Hola de nuevo. Mil perdones por la demora en responder. Fui padre en diciembre :p :p :p y no pude sentarme a escribir este post hasta ahora.

El problema que tenía con HH virtual no se repitió en una máquina virtual nueva, por lo que asumo que tocando algo la estropeé como para que la compartición de carpetas no funcionara.

La solución de faktorqm la verdad intenté implementarla y no me funcionó pero se debe exclusivamente a que soy bastante ***papafrita*** en Linux.

Igualmente, muchas gracias. Ahora que estoy de vuelta, veo la causa de mi problema y es que la línea de comandos:

```
sudo mount -t  vboxsf *shared *"/media/Capturas/VMs/Share"
```


tenía un error, a saber:

* El nombre del recurso compartido no es *shared *sino **Share** y es por esa causa que el mensaje del sistema decía: 

```
sbin/mount.vboxsf: mounting failed with the error: No such file or directory
```

Como sea, es bueno estar de vuelta y espero que la experiencia le sirva a alguien. 

Saludos.

---

