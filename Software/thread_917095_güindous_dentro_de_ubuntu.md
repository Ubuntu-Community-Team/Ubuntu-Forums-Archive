---
title: "güindous dentro de ubuntu"
date: 2008-09-11
forum: Software
---

### Post by granjero on 2008-09-11
buenas, le comento cual es mi congoja. no encontre nada similar en el foro con el buscabusca...

comparto mi pc con mi pareja y ella se reusa a usar ubuntu. leyendo por ahi encontre este tutorial que me pareció piolisimo y queria saber, ya que es un post de un año de antigüedad, que onda??? funciona? hay una mejor manera de hacerlo?

[http://ayudalinux.wordpress.com/2007/02/01/instalar-windows-xp-sobre-ubuntu-con-vmware-parte-1/](http://ayudalinux.wordpress.com/2007/02/01/instalar-windows-xp-sobre-ubuntu-con-vmware-parte-1/)

mi idea es tener güindous en uno de lo escritorios del ubuntu para no tener que andar booteando la pc cada rato...

esto va a hacer que mi pc se convierta en una babosa embarazada?

desde ya muchas gracias por su tiempo...

salud!

pd: donde leo para saber como instalar juegos de güindous en ubuntu...

gracias de nuevo.

granjero

:-({|=

---

### Post by Kantier on 2008-09-11
y, si nos comentás qué PC tenés por ahi te vamos a poder decir si se va a arrastrar o no ^_^

para saber qué juegos de Win corren en Lin, fijate en [http://appdb.winehq.org](http://appdb.winehq.org)

---

### Post by ariel on 2008-09-11
> **granjero said:**
> buenas, le comento cual es mi congoja. no encontre nada similar en el foro con el buscabusca...

comparto mi pc con mi pareja y ella se reusa a usar ubuntu. leyendo por ahi encontre este tutorial que me pareció piolisimo y queria saber, ya que es un post de un año de antigüedad, que onda??? funciona? hay una mejor manera de hacerlo?

[http://ayudalinux.wordpress.com/2007/02/01/instalar-windows-xp-sobre-ubuntu-con-vmware-parte-1/](http://ayudalinux.wordpress.com/2007/02/01/instalar-windows-xp-sobre-ubuntu-con-vmware-parte-1/)

mi idea es tener güindous en uno de lo escritorios del ubuntu para no tener que andar booteando la pc cada rato...

esto va a hacer que mi pc se convierta en una babosa embarazada?

desde ya muchas gracias por su tiempo...

salud!

pd: donde leo para saber como instalar juegos de güindous en ubuntu...

gracias de nuevo.

granjero

:-({|=

Yo uso virtualbox en lugar de vmware. Es opensource, anda mas rapido y se esta volviendo muy activo ultimamente.

Lo instalas, creas una maquina virtual, e instalas windows en la maquina virtual.

---

### Post by granjero on 2008-09-11
Kantier mi pc es asi...

CPU AMD Athlon 64 X 2 dual core 5200+
RAM 2gb 
VIDEO MSI gforce 8600 GT
HD 320gb sata (NTFS 20gb para wxp) (XT3 20gb para ubuntu) (swap 4gb) (resto FAT32 para mis archivos) la xt3 y la swap estan en una particion extendida...
HD 80gb ide NTFS para downloads....

gracias por el dato de la pag de juegos


Ariel, con el yo quiero que uno de los escritorios sea wxp para mi novia.... es factible?

que recomiendan?

salud!

---

### Post by pol666 on 2008-09-11
Ni ahi te va a andar lento. te acanza y sobra.

---

### Post by granjero on 2008-09-12
instale el virtualbox y quiero saber si puedo usar el windows que ya esta isntalado o tengo que instalar un windows nuevo? 

ahi estoy bajando el winchiquito por las dudas


salud!

---

### Post by faktorqm on 2008-09-12
Si vas a instalar una maquina virtual para que queres el "instalado" realmente? borralo asi tenes mas espacio. 

La verdad creo que si se podia pasar de una particion a un archivo de maquina virtual, se comento en otro thread que la verdad no recuerdo. Si no se puede, pido disculpas, no soy muy ducho en el tema.

Lo ultimo y sin ánimos de ofender: ¿por que no le borras el xp y que se deje de hinchar? le gustan los virus? el spyware? la lentitud? los cuelgues? las pantallas azules? la defragmentacion de disco? una cosa es tener una pc virtual con xp, por supuesto, para hacer aquellas tareas imposibles en gnu/linux, o para mantener compatibilidad con alguien externo (tu jefe xD) pero de ahi a "me rehuso" hay una diferencia bastante grande. Salu2!!!

---

### Post by granjero on 2008-09-13
bueno, les cuento como viene la cosa...

hice una maquina virtual con el virtual box

para güindows XP con 256 de ram con un disco dinamico de 10gb en un disco rigido secundario ide formateado en ntfs (ahora que lo esribo sera ese el problema?)

cuando enciendo la maquina virtual con el disco de instalcion del SO metido en el cd (me baje un winchiquito) me tira el siguiente error

[B]
"VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel, e.g. virtualbox-ose-modules-generic..
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Código Resultado: 
0x80004005
Componente: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}"[/B] 

como sigo?

trate de instalar desde synaptic el paquete virtualbox-ose-modules pero no se cual es para mi kernel. hay miles de archivos 

les dejo la data de mi kerel para saber cual bajar

~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 8.04.1
Release:	8.04
Codename:	hardy

~$ uname -a
Linux jm 2.6.24-19-generic #1 SMP Wed Aug 20 22:56:21 UTC 2008 i686 GNU/Linux


gracias
y salud!

---

### Post by faktorqm on 2008-09-14
capaz el que te dice la misma version que uname -a?!?!?!?!

```
faktorqm@the-edge:~$ aptitude search virtualbox-ose-modules
v   virtualbox-ose-modules                                                                     -                                                                                                     
p   virtualbox-ose-modules-2.6.24-16-386                                                       - virtualbox-ose module for linux-image-2.6.24-16-386                                                 
p   virtualbox-ose-modules-2.6.24-16-generic                                                   - virtualbox-ose module for linux-image-2.6.24-16-generic                                             
p   virtualbox-ose-modules-2.6.24-16-openvz                                                    - virtualbox-ose module for linux-image-2.6.24-16-openvz                                              
p   virtualbox-ose-modules-2.6.24-16-rt                                                        - virtualbox-ose module for linux-image-2.6.24-16-rt                                                  
p   virtualbox-ose-modules-2.6.24-16-server                                                    - virtualbox-ose modules for linux-image-2.6.24-16-server                                             
p   virtualbox-ose-modules-2.6.24-16-virtual                                                   - virtualbox-ose module for linux-image-2.6.24-16-virtual                                             
p   virtualbox-ose-modules-2.6.24-18-386                                                       - virtualbox-ose module for linux-image-2.6.24-18-386                                                 
p   virtualbox-ose-modules-2.6.24-18-generic                                                   - virtualbox-ose module for linux-image-2.6.24-18-generic                                             
p   virtualbox-ose-modules-2.6.24-18-openvz                                                    - virtualbox-ose module for linux-image-2.6.24-18-openvz                                              
p   virtualbox-ose-modules-2.6.24-18-rt                                                        - virtualbox-ose module for linux-image-2.6.24-18-rt                                                  
p   virtualbox-ose-modules-2.6.24-18-server                                                    - virtualbox-ose modules for linux-image-2.6.24-18-server                                             
p   virtualbox-ose-modules-2.6.24-18-virtual                                                   - virtualbox-ose module for linux-image-2.6.24-18-virtual                                             
p   virtualbox-ose-modules-2.6.24-19-386                                                       - virtualbox-ose module for linux-image-2.6.24-19-386                                                 
[COLOR="Red"]**_[FONT="Arial Black"][SIZE="4"]p   virtualbox-ose-modules-2.6.24-19-generic                                                   - virtualbox-ose module for linux-image-2.6.24-19-generic[/SIZE][/FONT]_**[/COLOR]                                             
p   virtualbox-ose-modules-2.6.24-19-openvz                                                    - virtualbox-ose module for linux-image-2.6.24-19-openvz                                              
p   virtualbox-ose-modules-2.6.24-19-rt                                                        - virtualbox-ose module for linux-image-2.6.24-19-rt                                                  
p   virtualbox-ose-modules-2.6.24-19-server                                                    - virtualbox-ose modules for linux-image-2.6.24-19-server                                             
p   virtualbox-ose-modules-2.6.24-19-virtual                                                   - virtualbox-ose module for linux-image-2.6.24-19-virtual                                             
p   virtualbox-ose-modules-2.6.24-20-386                                                       - virtualbox-ose module for linux-image-2.6.24-20-386                                                 
p   virtualbox-ose-modules-2.6.24-20-generic                                                   - virtualbox-ose module for linux-image-2.6.24-20-generic                                             
p   virtualbox-ose-modules-2.6.24-20-openvz                                                    - virtualbox-ose module for linux-image-2.6.24-20-openvz                                              
p   virtualbox-ose-modules-2.6.24-20-rt                                                        - virtualbox-ose module for linux-image-2.6.24-20-rt                                                  
p   virtualbox-ose-modules-2.6.24-20-server                                                    - virtualbox-ose modules for linux-image-2.6.24-20-server                                             
p   virtualbox-ose-modules-2.6.24-20-virtual                                                   - virtualbox-ose module for linux-image-2.6.24-20-virtual                                             
p   virtualbox-ose-modules-386                                                                 - virtualbox-ose module for linux-image-386                                                           
p   virtualbox-ose-modules-generic                                                             - virtualbox-ose module for linux-image-generic                                                       
p   virtualbox-ose-modules-openvz                                                              - virtualbox-ose module for linux-image-openvz                                                        
p   virtualbox-ose-modules-rt                                                                  - virtualbox-ose module for linux-image-rt                                                            
p   virtualbox-ose-modules-server                                                              - virtualbox-ose module for linux-image-server                                                        
p   virtualbox-ose-modules-virtual                                                             - virtualbox-ose module for linux-image-virtual                                                       
faktorqm@the-edge:~$ 

```

---

### Post by zeroadrenaline on 2008-09-14
Fijate qeu antes de correr vbox tenes que asignarle un permiso a un archivo vbox.
Buscando en google, aparece lo sigiente [http://mispreguntasdelinux.blogspot.com/2007/11/fallo-virtualbox-vbox-status-code-1909.html](http://mispreguntasdelinux.blogspot.com/2007/11/fallo-virtualbox-vbox-status-code-1909.html)

Eso soluciona tu problema.
Un abraxo!

---

### Post by jpmorelli on 2008-09-15
Granjero, es como te dicen. Tenés que instalar el kernel de Virtualbox segun la versión de kernel de linux que usas. Como bien dice faktorqm lo sacás corriendo el comando:

uname -a

entonces lo instalas con:

sudo apt-get install virtualbox-ose-modules-2.6.lo_que_corresponda

Y luego de eso tenés que agregar a tu usario dentro del grupo vboxusers. Cerras sesión, volves a ingrear y listo. Ya podés armar tus máquinas virtuales.
Suerte !

---

### Post by granjero on 2008-09-16
hola, sigo con el mismo problema!

trate de darle el permiso a esa carpeta que dice en el tuto que me linkeó zeroadrenaline, pero no existe la carpeta /dev/vboxdvr en mi carpeta y ademas cuando pongo el comando su me pide pass y le doy la unica pass que tengo y me falla la autenticacion.

ya agregue mi usuario a vboxusers que era otra cosa que tenia que hacer. pero el problema persiste!

salud! y gracias!

---

### Post by granjero on 2008-09-17
bueno gente, logre hacerlo andar... lo que hice fue crear la carpeta que decia que faltaba en el error y darle sudo chmod 777 y ademas encontre un segundo archivo para mi SO en los repositorios de Synaptic. 

gracias por todo!

---

