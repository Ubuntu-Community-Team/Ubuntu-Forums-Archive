---
title: "Pregunta: Levantar XP desde Ubuntu"
date: 2008-05-05
forum: Software
---

### Post by eldani on 2008-05-05
Tengo Ubuntu y Windows XP funcionando en discos distintos. Quisiera poder virtualizar el XP desde Ubuntu pero no quiero reinstalarlo sino poder levantar el que ya tengo.

Muchas Gracias por adelantado

Daniel

---

### Post by pol666 on 2008-05-05
Segun mis leves conocimientos eso es imposible

---

### Post by Tosh78 on 2008-05-05
fijate si no te lo monta en la carpeta /host
Sino, podes instalar el ntfs-manager y desde ahi lo programas para que te monte el disco.

---

### Post by sajnox on 2008-05-05
> **eldani said:**
> Tengo Ubuntu y Windows XP funcionando en discos distintos. Quisiera poder virtualizar el XP desde Ubuntu pero no quiero reinstalarlo sino poder levantar el que ya tengo.

Muchas Gracias por adelantado

Daniel

No me animo a decir que imposible, pero estoy seguro que facil no es. 

Con que programa lo queres hacer?? Googleaste un poco el tema??

Probablemente tengas que hacer una instalacion del sistema desde cero para que te reconozca el hardware virtual, sino no creo que te levante y despues compartir las carpetas de tu particion con windos y copiarlas al disco virtual, pero eso si vas a estar duplicando la informacion. 

Lo que si es seguro (por lo menos usando Virtual Box que es el que conozco) que tenes que tener la informacion en el disco virtual que te crea el sistema

---

### Post by anarko on 2008-05-05
Proba con el cliente de VMWare, yo hice alrevez, va casi, instale dentro de vmware linux en un HDD aparte y despues lo levantate normalemtne en la PC, seguro se peude, hasta la ultima ves que me fije el cliente de vmware era free, sino tenes qemu pero no se si levanta un disco yo siempre trabaje en qemu con imagenes de discos virtuales.

Proba... que podes perder :p 
Nota: supongo que no esperaras que sea rapido ya que no lo va a ser,yo con 2.5GB de ram y compartiendole a la PC virtual 1GB de ram se arrastra, ahora si lo que queres es acceder a los archivos que tenes guaradados en el windows yo montaria la particion del disco de windows.

---

### Post by rovr138 on 2008-05-05
Si no tienes problemas usando VMware se puede hacer. VMware Converter es un programa que te permite crear de una instalacion existente de Windows una imagen para utilizar con los diferentes programas de VMware. (VMware Server, Player, Workstation...)

El enlace de descarga que encontre fue este, espero que te sirva.

```
http://download3.vmware.com/software/converter/VMware-converter-3.0.2u1-62456.exe
```

---

### Post by niko_3100 on 2008-05-06
Proba virtualbox que hay una version gratis.

---

### Post by pol666 on 2008-05-06
Par amuy pocos entendieron lo que quiere hacer...Quiere virtualizar un SO que tiene en otra particion (osea un SO ya instalado)

La manera inversa no es dificil ya que convertis el VDI en una particion y ya.

Lo que si "calculo" que se puede hacer es: Crear una copia de los datos de la particion con WIN...meterlos en un VDI creados por la virtual box y arrancaria el sistema pero que pasa... no seria dinamico osea los cambios se aplicarian solamente en la maquina virtual...


Te entiendo lo que queres hacer y es demasiado volado.

---

### Post by faktorqm on 2008-05-07
> **pol666 said:**
> Par amuy pocos entendieron lo que quiere hacer...Quiere virtualizar un SO que tiene en otra particion (osea un SO ya instalado)

La manera inversa no es dificil ya que convertis el VDI en una particion y ya.

Lo que si "calculo" que se puede hacer es: Crear una copia de los datos de la particion con WIN...meterlos en un VDI creados por la virtual box y arrancaria el sistema pero que pasa... no seria dinamico osea los cambios se aplicarian solamente en la maquina virtual...


Te entiendo lo que queres hacer y es demasiado volado.

Limaste con cualquiera. Lo que quiere hacer es levantar el mismo windows xp que tiene ahora en una particion, pero en un virtual box por que no quiere reinstalar todo, pasar los datos, configuraciones, drivers, etc, etc, etc.
Yo ni idea del tema, pero ahi nombraron ese converter que me parece lo mejor, pasar de particion a VDI, luego borrar particion, y estirar o reformatearla bajo ext3. Contanos como t fue. Salu2!

---

### Post by pol666 on 2008-05-07
a si entendi la inversa xD

---

### Post by eldragon on 2008-05-07
en algun momento estuve en tu iterrogante. no tengo la respuesta, porque poco despues directamente retome mi particion winxp, la hize ext3 y me manejo constantemente con VirtualBox.

pero no quiere decir que no se pueda. los pasos a seguir, segun lo que recompile en aquel tiempo son los siguientes:

1. bootear con Winxp. crear un nuevo perfil de hardware, y hacerlo pelado (esto inhabilita todos tus drivers para el perfil que vas a usar con virtual box).
2. modificar boot.ini para agregar una nueva instalacion, con el nuevo perfil de hardware
3. hacer que virtualbox bootee con la particion existente y elegir bootear con el nuevo perfil de hardware.
4. rezar.

dicen que puede fallar (dijo tusam), asi que siempre hace un backup de tu particion de winxp. 
fijate si averiguas mejor como hacer pasos 1-3. el paso 4 no es necesario.

el manual de virtualbox tiene que tener todo lo necesario para hacer paso 3.

---

### Post by sajnox on 2008-05-07
Releyendo el thread me acorde que en la revista fullcircle en algun numero hicieron una nota para hacer lo que vos queres.

[http://fullcirclemagazine.org/](http://fullcirclemagazine.org/)

---

### Post by clasificado on 2008-05-08
> **eldragon said:**
> dicen que puede fallar (dijo tusam)

La parte mas molesta es que a XP no le gusta andar cambiando de hardware.

Por lo que, si no tenes cuidado, el paso constante entre la PC real y la virtual te puede dejar sin XP. La mejor manera de solucionar este problema es hacer dos perfiles de hardware en el xp, uno para la real y otro para la virtual. Lo feo es que cada vez que levantas el xp te pregunta que perfil querés usar, y si lo elejis al reves, se desestabiliza todo.

Además, que los discos rígidos funcionan mejor cuando predomina el uso intensivo de una partición a la vez. Si vas a querer tener dos operativos funcionando en el mismo momento, es mejor tener dos discos separados. Salvo que no te moleste que los dos operativos se vuelvan leeeeentos (cuando los usas en serio, claro está)

---

### Post by MeduZa on 2008-05-08
poder se puede, el problema es que cuando windows levante y vea que le cambiaron todo el hardware se va a enojar y en el peor de los casos no va a querer andar.

Segun tengo entendido se puede con las herramientas vm pero nunca lo hice, solo uso mvplayer.

---

### Post by eldragon on 2008-05-08
> **clasificado said:**
> La parte mas molesta es que a XP no le gusta andar cambiando de hardware.

Por lo que, si no tenes cuidado, el paso constante entre la PC real y la virtual te puede dejar sin XP. La mejor manera de solucionar este problema es hacer dos perfiles de hardware en el xp, uno para la real y otro para la virtual. Lo feo es que cada vez que levantas el xp te pregunta que perfil querés usar, y si lo elejis al reves, se desestabiliza todo.

Además, que los discos rígidos funcionan mejor cuando predomina el uso intensivo de una partición a la vez. Si vas a querer tener dos operativos funcionando en el mismo momento, es mejor tener dos discos separados. Salvo que no te moleste que los dos operativos se vuelvan leeeeentos (cuando los usas en serio, claro está)

a eso me referi con crear 2 perfiles de hardware y modificar boot.ini para agregar la opcion con el nuevo perfil. de manera de hacer que la vm elija un perfil, y el boot comun elija el otro.

espero haber sido lo suficientemente claro.

---

### Post by faktorqm on 2008-05-08
yo las experiencias que tengo intentando hacer windows multi-hal son pesimas, pero lo de los perfiles de hardware funciona, el tema es que la primera vez que lo ararnques tenes que "instalar" el hard del virtual box digamos. no se igual, toco medio de oido. Sino agarra un ghost, sacale una imagen al disco a un archivo, backapealo en un dvd, si no entra decile que te lo corte cada 3.9gb, y listo, si de ultima tenes algun drama, restauras todo de vuelta con el mismo ghost, se ke es trabajoso, pero sale. salu2!

---

### Post by MeduZa on 2008-05-10
> **faktorqm said:**
> yo las experiencias que tengo intentando hacer windows multi-hal son pesimas, pero lo de los perfiles de hardware funciona, el tema es que la primera vez que lo ararnques tenes que "instalar" el hard del virtual box digamos. no se igual, toco medio de oido. Sino agarra un ghost, sacale una imagen al disco a un archivo, backapealo en un dvd, si no entra decile que te lo corte cada 3.9gb, y listo, si de ultima tenes algun drama, restauras todo de vuelta con el mismo ghost, se ke es trabajoso, pero sale. salu2!

yo habia una epoca que mi windows 95 me lo llevaba a la pc de un amigo y era "dual boot". andaba en uno o en el otro, pero parece que el xp es un poco mas quisquillo, si le cambias el micro palma de una por ejemplo. yo ya en mi pc no uso windows desde hace mas de 2 años casi y solo lo levanto en VM para probar como se verian las paginas en IE 6 y 7 y nada mas. si necesito correr algo lo corro con wine ;)

Saludos

---

### Post by Eduardo Natali on 2009-09-07
Hola,

Haces una imagen del sistema que tenés instalado, y luego en GNU/Linux con VMWare Player levantas la imagen, fijate que acá te dice que formatos de imagenes podes utilizar:

[http://www.vmware.com/products/player/features.html](http://www.vmware.com/products/player/features.html)

Use 3rd-party virtual machines and images

Open Microsoft virtual machines, Symantec Backup Exec System Recovery (formerly called Live State Recovery) images, Norton Ghost 10 images, Norton Save & Restore images, StorageCraft ShadowProtect images, and Acronis True Image images. In this process, the initial virtual machine or image is left untouched in its native format and any modifications are saved in a much smaller VMware-formatted file that is linked to the initial image.

Saludos Edu..

---

### Post by Eduardo Natali on 2009-09-07
Hola,

Haces una imagen del sistema que tenés instalado, y luego en GNU/Linux con VMWare Player levantas la imagen, fijate que acá te dice que formatos de imagenes podes utilizar:

[http://www.vmware.com/products/player/features.html](http://www.vmware.com/products/player/features.html)

Use 3rd-party virtual machines and images

Open Microsoft virtual machines, Symantec Backup Exec System Recovery (formerly called Live State Recovery) images, Norton Ghost 10 images, Norton Save & Restore images, StorageCraft ShadowProtect images, and Acronis True Image images. In this process, the initial virtual machine or image is left untouched in its native format and any modifications are saved in a much smaller VMware-formatted file that is linked to the initial image.

Saludos Edu..

---

