---
title: "Instalar SO en segundo disco."
date: 2009-05-17
forum: Software
---

### Post by pol666 on 2009-05-17
Buenas, yo tengo dos discos, en el primero que bootea, esta WIndows 7, Fedora y Kubuntu. Como superé el limite de particiones primarias, mi idea es instalar Windows XP y algo más en particiones del otro disco. (si, espacio, tiempo y ganas me sobran :P)

Esto yo ya lo intente y les aseguro que por más que actualize el grub el sistema no aparece y no lo puedo cargar, a no ser qeu cambie las prioridades de booteo en la Bios y esa no es la idea.

Entonces, ¿Cuales son los pasos que deberia realizar para que los SO que instale en el segundo disco sean reconocidos en el grub (el grub pertenece a kubuntu).

PAra más info les dejo el menu.lst

> # This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows 7
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Fedora 
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.27.19-170.2.35.fc10.i686 ro root=UUID=75be6424-eaab-445d-8b24-bd7953f76d93 rhgb quiet 
initrd		/boot/initrd-2.6.27.19-170.2.35.fc10.i686.img
savedefault
boot


y por si necesitan el fdisk -l

> Disco /dev/sda: 250.0 GB, 250059350016 bytes
255 cabezas, 63 sectores/pista, 30401 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x000e5d03

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1        6527    52428096    7  HPFS/NTFS
/dev/sda2            6528        7180     5245222+  83  Linux
/dev/sda3            7181        7833     5245222+  83  Linux
/dev/sda4            7834       30401   181277460    5  Extendida
/dev/sda5            7834       30270   180225171   83  Linux
/dev/sda6           30271       30401     1052226   82  Linux swap / Solaris

Disco /dev/sdb: 160.0 GB, 160041885696 bytes
255 cabezas, 63 sectores/pista, 19457 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x04b504b5

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdb1               1       19457   156288321   83  Linux


---

### Post by hernan blau on 2009-05-17
¿Aún usas el privativo?  Con Kubuntu y Fedora te sobra, a menos que uses autocad. Cuando se ta haga bolsa por virus o te aparezca el pantallazo azul, como me ocurrió esta semana en el trabajo, querrás instalarlo en la papelera. Suerte. HB.

---

### Post by Hei Ku on 2009-05-17
> **hernan blau said:**
> ¿Aún usas el privativo?  Con Kubuntu y Fedora te sobra, a menos que uses autocad. Cuando se ta haga bolsa por virus o te aparezca el pantallazo azul, como me ocurrió esta semana en el trabajo, querrás instalarlo en la papelera. Suerte. HB.

Esto no tiene nada que ver con lo que pregunto. Dejemos los fanatismos de lado, y concentremonos en el soporte, que es la razon de ser de este foro. ):P

---

### Post by Mauro22 on 2009-05-17
Si vas a instalar xp (o ya lo hiciste) en otro disco tenes que agregar otra entrada

title Windows XP
rootnoverify (hd1,0)  <-- cambias el disco, en lugar de 0,0 va 1,0
savedefault
makeactive
chainloader 

Eso te llevaría al 2do disco que si luego instalas otras distros te aparece el 2do grub.

---

### Post by pol666 on 2009-05-17
la idea es siempre usar el grub de kubuntu por que el sistema que no voy a borrar por mucho tiempo. como no lo se configurar manual uso el supergrub, lo hago facil y selecciono que grub usar.

Hernan, me encanta probar sistemas, puse el Windows 7 pero quiero el Xp tambien, espacio, tiempo y ganas me sobran.

---

### Post by staar on 2009-05-17
agregar sistemas al grub es fácil, tenés que tener en cuenta que grub tiene otra nomenclatura, diferente, para nombrar los discos y particiones, así sda1 (primera partición '1' del primer disco 'a') en el grub es 'hd0,0' (primera partición '0' del primer disco '0'), es decir, a los números que les dá linux, restarles 1, y a las letras, seguir el abecedario, empezando de 0...

para agregar un sistema linux, se necesitan agregar, por lo menos, 4 líneas (algunas distros com fedora o ubuntu, usan algunas más), la primera 'title' indica el texto que va a aparecer en la entrada en el grub, la segunda, puede ser 'root' o 'uuid', e indica la partición raíz (/) del sistema que se quiere iniciar, si se pone 'root' se indica la partición de la forma hdX,Y, si se pone 'uuid' se da el uuid de la partición (algunas distros usan una forma, otros la otra, por ejemplo, ubuntu usa uuid, archlinux usa root), la tercera línea 'kernel' indica la ubicación del kernel y las opciones de inicio de este, generalmente la partición raíz, la opción quiet (para que solo muestre los mensajes de error, no los eventos comunes), el 'ro' y las opciones del framebuffer (vga=xxx), la cuarta línea 'initrd' es la ubicación de la imagen ram que se usa para tener un sistema mínimo, capaz de buscar la partición de inicio, y pasarle el mando al kernel...

estos son ejemplos, de un arch y de un ubuntu, como quedarían en el menu.lst```

title           Arch Linux
root            (hd0,5)
kernel          /boot/vmlinuz26 root=/dev/disk/by-uuid/d9cb3911-a82b-4d25-873f-de6a999ec931 ro vga=795 quiet
initrd          /boot/kernel26.img

title           Ubuntu 9.04
uuid            c7bca061-60b2-4fe2-a8aa-19ade6201585
kernel          /boot/vmlinuz-2.6.28-11-generic root=UUID=c7bca061-60b2-4fe2-a8aa-19ade6201585 ro quiet vga=795 splash
initrd          /boot/initrd.img-2.6.28-11-generic
quiet

``` los windos, por lo menos el XP, se agregan como te comentó Mauro, son bastante simples...

todo esto se hace modificando, como root, el archivo /boot/grub/menu.lst del kubuntu, el uso del supergrubdisk para estos casos no me parece confiable, porque cada pc es un mundo, el supergrub no es adivino, y es muy probable que se equivoque, en los números de particiones o en algo, y que el sistema no bootee...

un buen comando, a veces no es necesario, después de modificar el menu.lst, es el ```
sudo update-grub
``` que actualiza la MBR (donde está guardado GRUB) con la información actual del menu.lst...

AH!, ya que el GRUB está en ubuntu, es importante agregar los otros sistemas FUERA (arriba o abajo) de la debian automagic kernels list, y, además, nombrar las particiones según lo hace ubuntu, es decir, la misma partición puede que para ubuntu sea sdb2 (hd1,1) y para otra distro instalada en el segundo disco sea la sda2, en esos casos seguir los números que les asigna ubuntu, ya que GRUB está instalado en él...

saludos

---

