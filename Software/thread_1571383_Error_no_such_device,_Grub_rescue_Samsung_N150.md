---
title: "Error: no such device, Grub rescue Samsung N150"
date: 2010-09-09
forum: Software
---

### Post by r4zi3l on 2010-09-09
Hola chic@S

He estado revisando con tito google y nada, no me ayuda. Mucha jerga pero ningun tutorial. Os pongo en antecedentes.

Anoche, viendo que el maldito Samsung N150 tiene W7 starter y no tiene opcion de boot from usb, meti ubuntu netbook remix i386...

Anoche todo bien, actualizo y zas, booteo hoy y tengo este mensajito:

[I]error: no such device 3919a0f0-1b6c-47cd-a329-607dd95293c7
grub rescue>[/I]

Iluso de mi, pense en usar comandos para solucionarlo, pero na de na. No responde. Pruebo el F4 para iniciar recovery... nada...

Como puedo bootear desde el usb en esa consola? Tengo el universal usb installer metido en el usb, pero claro no puedo bootear al tener una bios tan restrictiva que no me permite hacer boot from usb...

Asi pues estoy perdido. Si alguien sabe como corregir el problema se lo agradeceria.

(**insmod /boot/grub/linux.mod** da *error:unknown filesystem*)

---

### Post by guillermolisi on 2010-09-09
Estuve en una situacion similar luego de instalar descuidadamente MM beta en un disco portable en mi notebook.

Lo que hice fue iniciar la maquina con SuperGrub2 disk para revisar que la configuracion del Grub estuviese intacta, esto incluye que se reconozcan otros sistemas operativos instalados en modo dual boot. Luego con el mismo SuperGrub2 inicie la notebook con Kubuntu y salio funcionando perfecto. Conclusion: se reescribio el MBR del disco con informacion referida al disco removible, mas precisamente con su UUID como direccion de busqueda del Grub.

Cuando ese disco no estaba conectado, salia el mismo error que recibis vos. Y cuando lo estaba, iniciaba solamente con Kubuntu 10.10 beta.

Por que paso esto ? Porque cuando confirme el particionado olvide cambiar sobre que disco queria que grabara el MBR con la nueva instalacion y lo grabo sobre el fijo (/dev/sda)

Como reestableci/recupere el MBR del disco rigido de la notebook ? Asi:


[LIST]
[*]Inicias la maquina con un LiveCD
[*]Ingresas en consola/terminal:
[/LIST]
```
sudo mkdir /mnt/dev /mnt/proc
sudo mount /dev/sda2 /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo chroot /mnt
grub-install --recheck /dev/sda
reboot
sudo update-grub2
```Nota: en mi caso la particion que aloja /boot y / es la 2 y la maquina posee un solo disco (identificado como "a", de ahi que la particion a utilizar es la /dev/sda2 (disco a, particion 2). Para otros casos hay que verificar con Gparted o equivalente.
Nota 2: El MBR se graba sobre la unidad de disco fisica, no sobre una particion, por eso la reinstalacion del Grub se hace sobre /dev/sda (sin mencionar particion alguna)

---

### Post by r4zi3l on 2010-09-10
Gracias por la información Guillermo.

Creo que voy entendiendo el error. Yo instalé desde Windows on un pendrive. Creo que aun no he iniciado con el pendrive, veré si lo puedo hacer...

Mira que he estado horas intentando cargar la terminal a posteriori sin hacer boot desde 0.

Lo que me ha pasado a mi es instalar desde Pen y luego actualizar. A ver en qué paso se ha roto la UUID.

:)

---

### Post by Brath-ga on 2010-09-10
Estimado amigo.
Ese mismo problema acaba de sucederme a mi después de cambiar la tarjeta gráfica.
Como supuse que el Grub no encontraba el disco en donde estaba instalado, inicié con un Live de Ubuntu y comprobé con fdisk -l y "voilá", solo estaba el "sda", es "sdb" había desaparecido.
Abrí el equipo y vi que el cable de alimentación de uno de los discos estaba suelto.
Estoy seguro que no lo tocara, pero al mover algún otro cable, ese se desconectó.
Pues eso, lo conecté, cerré todo, arranqué y perfecto, todo en su sitio.
A veces un pequeño golpe, o una mano torpe puede hacer que nos rompamos la cabeza pensando en errores del sistema operativo.
Un saludo

---

### Post by guillermolisi on 2010-09-10
> **r4zi3l said:**
> Gracias por la información Guillermo.

Creo que voy entendiendo el error. Yo instalé desde Windows on un pendrive. Creo que aun no he iniciado con el pendrive, veré si lo puedo hacer...

Mira que he estado horas intentando cargar la terminal a posteriori sin hacer boot desde 0.

Lo que me ha pasado a mi es instalar desde Pen y luego actualizar. A ver en qué paso se ha roto la UUID.

:)
Haber instalado en un pendrive es equivalente a instalar en otro disco como por ejemplo un portable USB. El tema esta en cual de ellos se grabo el MBR y creo que en tu caso fue en el fijo de la maquina.

Si es una desktop, no estaria nada mal verificar lo que indica Brath-ga. Si es eso es mucho mas simple la solucion pero creo que si el disco estuviera desconectado te daria el mensaje de que no encuentra ningun medio booteable (si es que solo tenes un disco rigido fijo).

---

### Post by Brath-ga on 2010-09-11
Estimado guillermolisi

El error que me apareció al tener desconectado el disco fué:

error: no such device bdfb6764-708f-4cle-9723-350f60-6deb14

grub rescue>

Es decir, el mismo error, por eso posteé en este hilo, no fuese a ocurrirle el mismo error al compañero.

Un saludo.

---

### Post by r4zi3l on 2010-09-11
Gracias por la info chicos.

Es un netbook con solo un HD. LS me indica HD0 y HD1. He probado a cargar con el pendrive en cada puerto para ver si es eso, pero no. He formateado el pendrive en ext2 y ext3 y nada.

El disco parece estar bien, lo que no esta bien es el grub. Seguramente grub.cfg dirige a uuid's erroneas (ya se sabe que un 0 en vez de un 1 es mortal).

En grub rescue no puedo o no se cargar el LiveCD. La BIOS no tiene boot desde USB.

LS HD0 = unknown filesystem.
LS HD1 = unknown filesystem.

insmod parece funcionar pero no se que cargar (linux.mod da unknown filesystem).

Me da a mi que todo es NTFS y grub no entiende nada.

---

### Post by guillermolisi on 2010-09-11
Probaste de llevar a cabo el procedimiento que sugeri ?

Podrias, utilizando un LiveCD, pasarnos la salida de ```
sudo fdisk -l
```

---

