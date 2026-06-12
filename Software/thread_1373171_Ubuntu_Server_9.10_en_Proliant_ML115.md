---
title: "Ubuntu Server 9.10 en Proliant ML115"
date: 2010-01-05
forum: Software
---

### Post by z37a on 2010-01-05
Gente, tengo algunos inconvenientes con esto, estoy intentando instalar en un Proliant ml115(con opteron) un Ubuntu server, se decidió utilizar 9.10 pro que era el que mejor tomaba la placa RAID, en realidad es una placa FAKE RAID, la cual tiene armado un RAID1 de 2 discos. El problema viene cuando se termina de instalar el ubuntu server, durante la instalación el particionado y todo funciono lo mas bien, pero al finalizar la instalación no pude instalarle ni Grub ni Lilo, y al intentar utilizar un livecd e instalar el grub1 tampoco pude, no me funciono el grub1, el grub2 ni el lilo, alguna idea de que puedo hacer?

---

### Post by guillermolisi on 2010-01-05
> **z37a said:**
> Gente, tengo algunos inconvenientes con esto, estoy intentando instalar en un Proliant ml115(con opteron) un Ubuntu server, se decidió utilizar 9.10 pro que era el que mejor tomaba la placa RAID, en realidad es una placa FAKE RAID, la cual tiene armado un RAID1 de 2 discos. El problema viene cuando se termina de instalar el ubuntu server, durante la instalación el particionado y todo funciono lo mas bien, pero al finalizar la instalación no pude instalarle ni Grub ni Lilo, y al intentar utilizar un livecd e instalar el grub1 tampoco pude, no me funciono el grub1, el grub2 ni el lilo, alguna idea de que puedo hacer?
Hasta donde se, las placas que administran arreglos de disco y que dependen de un driver, como el caso de las Fake SCSI/RAID, presentan problemas luego de terminada la instalacion.

Personalmente desaconsejo usar ese tipo de placas y mas considerando un server en produccion. O usas controladoras que administran todo por hardware (que en general son bien caras pero muy buenas) o usas administracion RAID por software prescindiendo del driver de la placa.

---

### Post by z37a on 2010-01-05
> **guillermolisi said:**
> Hasta donde se, las placas que administran arreglos de disco y que dependen de un driver, como el caso de las Fake SCSI/RAID, presentan problemas luego de terminada la instalacion.

Personalmente desaconsejo usar ese tipo de placas y mas considerando un server en produccion. O usas controladoras que administran todo por hardware (que en general son bien caras pero muy buenas) o usas administracion RAID por software prescindiendo del driver de la placa.

Al final fue a un SoftRAID, pero me dio pena, por que había quedado barbara la partición. Se muy bien que hay placas RAID posta, pero por si las dudas te comento que el ML115 es lo mas barato de HP(y uno de mi preferidos ese chiquitin jejejej). Pero me llamo la atención que reconociera el fake RAID de 1 y se instalara de 10 todo, solo la arruino al llegar al grub, no hubo forma!!!! Y como estoy corto de tiempo investigue algo y como vi mucha complicación tire un softRAID, igualmente estaría interesante saber si hay solución a esto o como esta el estado de esto.

---

### Post by guillermolisi on 2010-01-05
> **z37a said:**
> Al final fue a un SoftRAID, pero me dio pena, por que había quedado barbara la partición. Se muy bien que hay placas RAID posta, pero por si las dudas te comento que el ML115 es lo mas barato de HP(y uno de mi preferidos ese chiquitin jejejej). Pero me llamo la atención que reconociera el fake RAID de 1 y se instalara de 10 todo, solo la arruino al llegar al grub, no hubo forma!!!! Y como estoy corto de tiempo investigue algo y como vi mucha complicación tire un softRAID, igualmente estaría interesante saber si hay solución a esto o como esta el estado de esto.
Normalmente HP, IBM, Intel y marcas similares desarrollan ese tipo de hardware pensando en RedHat, Novell, Sun, etc. Es decir, desarrollan los drivers y certifican para esas plataformas. A veces tenes suerte y con Ubuntu andan barbaro pero otras, hasta aqui la gran mayoria para mi, no funcionan y no te dan soporte alguno.

---

### Post by z37a on 2010-01-05
> **guillermolisi said:**
> Normalmente HP, IBM, Intel y marcas similares desarrollan ese tipo de hardware pensando en RedHat, Novell, Sun, etc. Es decir, desarrollan los drivers y certifican para esas plataformas. A veces tenes suerte y con Ubuntu andan barbaro pero otras, hasta aqui la gran mayoria para mi, no funcionan y no te dan soporte alguno.

Si lo se, pero lo loco de esto es que andaba mejor con Ubuntu que con Suse, Suse tampoco detecta el fakeraid, el SLES10 no lo toma, el SLES11 se tilda en el proceso de verificación de instalación. RedHat ni idea, no puedo dar datos por que no lo se.

---

### Post by sebastianabate on 2010-01-05
> **z37a said:**
> Si lo se, pero lo loco de esto es que andaba mejor con Ubuntu que con Suse, Suse tampoco detecta el fakeraid, el SLES10 no lo toma, el SLES11 se tilda en el proceso de verificación de instalación. RedHat ni idea, no puedo dar datos por que no lo se.

En el sitio de HP están los RPM para RHEL5 y para SLES10, y aclaran que hay que usar esos porque tienen modificaciones específicas aunque la versión sea la misma que viene con las distribuciones.

Habría que probar convirtiéndolos con alien; o llamando a HP para pedirles el link donde poder bajar el código fuente y compilarlo (tienen la obligación de darte el código fuente).

Yo tengo un par de clientes con este servidor y la verdad que es un chiche, pero los raid los hago por soft porque funciona muy bien y no me quiero complicar la vida :-)

---

### Post by juancarlospaco on 2010-01-07
Tenes que instalar Grub pero no en la MBR, sino en la particion, anda perfecto.
Sino tambien te podes hacer un /boot fuera del RAID y metes todo ahi, 
algunos hacen la Swap por fuera del RAID tambien pero eso va en gustos, 
pero andar anda muy bien.
:)

---

### Post by guillermolisi on 2010-01-07
> **juancarlospaco said:**
> Tenes que instalar Grub pero no en la MBR, sino en la particion, anda perfecto.
Sino tambien te podes hacer un /boot fuera del RAID y metes todo ahi, 
algunos hacen la Swap por fuera del RAID tambien pero eso va en gustos, 
pero andar anda muy bien.
:)
Si, en estos casos normalmente se lo instala en una particion /boot.

Para mi gusto, incluir /swap dentro de arreglo no tiene mucho sentido, mas considerando que es un server (y que esta adecuadamente dimensionado para la prestacion requerida).

---

### Post by juancarlospaco on 2010-01-07
*mmm... *en realidad no existe /swap por que swap no tiene punto de montaje de esa manera.

Ademas si *"subitamente"* desaparece el Swap el equipo booteara igual, 
aunque con una perdida de Performance, tambien se pueden tener varias particiones Swap.

---

### Post by z37a on 2010-01-07
Si el SWAP fue algo que la pifie mal y mal enserio, pero como ya estaba instalado y con VMWare server ni me preocpue en volver a hacerlo, el SWAP esta dentro de un LVM que a su vez esta dentro de un SoftRAID 1(el mismo donde esta el / y un /mnt/vmware). La pifie mal, quien es tan bo.... de usar un RAID 1 para SWAP, Aqui esta el gran bol.... jajajajajajaj

---

### Post by juancarlospaco on 2010-01-07
Si queres hacerlo bien grosso bien chuck norris,
haces una particion en un disco solido chiquito y
despues todos los datos al soft-raid.
SSD, adaptadores SDcard-SATA, o algo de eso.

---

### Post by z37a on 2010-01-08
> **juancarlospaco said:**
> Si queres hacerlo bien grosso bien chuck norris,
haces una particion en un disco solido chiquito y
despues todos los datos al soft-raid.
SSD, adaptadores SDcard-SATA, o algo de eso.

Sin dudas haría eso, mas que el ML115 G5 adentro tiene un puerto USB, esta echo para las dateras, pero le va de 10 un pendrive!!!! Igualmente no es para mi, si lo fuese le metería muchas mas cosas, entre ellas un raid5 no un raid1, y con discos de 1TB, total con lo que HP te vende los discos de 250 te compras vos discos comunes de 1TB que son lo mismo que te venden ellos!!!! Como dije ese server no es para mi, es para un cliente de donde trabajo, así que no me calienta demasiado.

---

