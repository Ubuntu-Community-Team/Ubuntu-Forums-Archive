---
title: "No me aparece el dual boot entre Windows 7 y Karmic Koala"
date: 2010-01-13
forum: Software
---

### Post by Yaguaron on 2010-01-13
Luego de instalar el Window$ Seven, instale Karmic Koala, pero no logro que al arrancar mi pc me aparezca ninguna manera de optar entre sistemas; probe re instalar Karmic, pero no pasa nada, e inexorablemente cuando mi PC arranca, lo hace derechito con Window$.

Si alguien sabe a que se debe esto, me sera de gran utilidad, ya que quiero probar Ubuntu y no puedo.

Saludos.

---

### Post by guillermolisi on 2010-01-13
> **Yaguaron said:**
> Luego de instalar el Window$ Seven, instale Karmic Koala, pero no logro que al arrancar mi pc me aparezca ninguna manera de optar entre sistemas; probe re instalar Karmic, pero no pasa nada, e inexorablemente cuando mi PC arranca, lo hace derechito con Window$.

Si alguien sabe a que se debe esto, me sera de gran utilidad, ya que quiero probar Ubuntu y no puedo.

Saludos.
La instalacion de Ubuntu se hizo en una particion sobre el mismo disco rigido o la PC posee dos discos y en uno esta Windows y en el otro Ubuntu ?

---

### Post by Yaguaron on 2010-01-14
> **guillermolisi said:**
> La instalacion de Ubuntu se hizo en una particion sobre el mismo disco rigido o la PC posee dos discos y en uno esta Windows y en el otro Ubuntu ?

Ambas cosas; o sea, tengo dos rigidos (un IDE de 80 gb y un SATa de 250 gb), configurados asi: 4 particiones en el SATA (una para Window$, otra destinada a guardar datos, otra que la tengo reservada para ubuntu y otra pequeña para el swap). El IDE lo deje para guardar datos, o en su defecto almacenar copias de seguridad.

---

### Post by guillermolisi on 2010-01-14
> **Yaguaron said:**
> Ambas cosas; o sea, tengo dos rigidos (un IDE de 80 gb y un SATa de 250 gb), configurados asi: 4 particiones en el SATA (una para Window$, otra destinada a guardar datos, otra que la tengo reservada para ubuntu y otra pequeña para el swap). El IDE lo deje para guardar datos, o en su defecto almacenar copias de seguridad.
O sea que en el disco SATA de 250Gb tenes los sistemas operativos, es asi ?
Podrias mostrarnos la salida del comando ```
fdisk /dev/sda
``` asi tenemos acceso a como esta particionado y en funcion de ello intenter deducir donde pudo haber ido a parar la informacion de booting que deberia grabar Grub para mantener la funcion de dual boot y asi elegir entre uno u otro SO ?

---

### Post by Yaguaron on 2010-01-14
> **guillermolisi said:**
> O sea que en el disco SATA de 250Gb tenes los sistemas operativos, es asi ?
Podrias mostrarnos la salida del comando ```
fdisk /dev/sda
``` asi tenemos acceso a como esta particionado y en funcion de ello intenter deducir donde pudo haber ido a parar la informacion de booting que deberia grabar Grub para mantener la funcion de dual boot y asi elegir entre uno u otro SO ?

Como hago eso? Sinceramente, yo no tengo mucha idea de todo lo que sean comandos o afines en linux; soy muy noob en eso.

---

### Post by guillermolisi on 2010-01-14
> **Yaguaron said:**
> Como hago eso? Sinceramente, yo no tengo mucha idea de todo lo que sean comandos o afines en linux; soy muy noob en eso.
Abris una consola/terminal y ahi ingresas esa linea de comando.
Para abrir una consola/terminal podes ir por el menu hasta la opcion Terminal, en Gnome, o Konsole en KDE.

---

### Post by Yaguaron on 2010-01-16
> **guillermolisi said:**
> Abris una consola/terminal y ahi ingresas esa linea de comando.
Para abrir una consola/terminal podes ir por el menu hasta la opcion Terminal, en Gnome, o Konsole en KDE.

Lo que pasa es que no me funciona el teclado ni el mouse. Intente manejarme con Alt+Tab, y ni siquiera eso.
No se si me explico, por mas que enchufo y desenchufo el teclado ni se mueve, y ni hablemos del raton.

---

### Post by guillermolisi on 2010-01-16
> **Yaguaron said:**
> Lo que pasa es que no me funciona el teclado ni el mouse. Intente manejarme con Alt+Tab, y ni siquiera eso.
No se si me explico, por mas que enchufo y desenchufo el teclado ni se mueve, y ni hablemos del raton.
Volvamos al principio. 

Cuando inicias la maquina con Ubuntu, funciona o directamente no arranca ?

Si funciona, te da algun mensaje de error o algun sintoma de anomalia ?

Si inicias desde el LiveCD, inicia y funciona bien toda la PC ?

---

### Post by Yaguaron on 2010-01-16
> **guillermolisi said:**
> Volvamos al principio. 

Cuando inicias la maquina con Ubuntu, funciona o directamente no arranca ?

Si funciona, te da algun mensaje de error o algun sintoma de anomalia ?

Si inicias desde el LiveCD, inicia y funciona bien toda la PC ?


Guillermo, la cosa es asi: yo solamente puedo entrar a Ubuntu usando el LiveCD, no tengo otra forma.
Con respecto a lo del teclado y el mouse, si bien el mouse sigue muerto (problema de controladores, supongo), el teclado anda. Nada mas tuve que conseguir los atajos de teclado respectivos.

Hice lo que vos me dijiste
Aplicaciones/Accesorios/Terminal
una vez que se me abrio esa ventana en blanco, escribi tal como vos me dijiste

fdisk/dev/sda

y me salió esto: no existe el fichero o directorio

por si acaso, probe con sdb, y me pasó lo mismo

Con respecto a lo que vos me preguntaste en su momento: los dos sistemas estan en el SATA. El IDE no tiene nada; son dos particiones FAT32 que estoy planeando unificar.

---

### Post by luks911 on 2010-01-16
Lo que pasa es que la línea que tenés que escribir es
```
fdsik /dev/sda
```
con un espacio entre el comando (fdisk) y el dispositivo (/dev/sda).

---

### Post by Yaguaron on 2010-01-16
Bueno, probe con
```
fdisk /dev/sda
```

y me salio esto:

no se puede abrir

lo mismo cuando intenté con sdb. Asi que probé (ya que estaba) separando todo, algo asi como:
```
 fdisk /dev /sda
```

y me salio:
El valor de DISCO tiene el formato /dev/hdb o dev/sda
Y el valor de PARTICION tiene el formato /dev/hda7


No se si hice algo mal, pero me salió eso. Ustedes diran...

---

### Post by z37a on 2010-01-16
> **Yaguaron said:**
> Bueno, probe con
```
fdisk /dev/sda
```

y me salio esto:

no se puede abrir

lo mismo cuando intenté con sdb. Asi que probé (ya que estaba) separando todo, algo asi como:
```
 fdisk /dev /sda
```

y me salio:
El valor de DISCO tiene el formato /dev/hdb o dev/sda
Y el valor de PARTICION tiene el formato /dev/hda7


No se si hice algo mal, pero me salió eso. Ustedes diran...


Cheeee!!! No se me olviden el sudo!!!!

El comando seria asi:

```
sudo fdisk /dev/sda -l
```

Esto para listar las particiones.

---

### Post by Tosh78 on 2010-01-21
Cuando yo instale windows 7, me paso algo similar. Antes tenia Vista + Ubuntu, pero despues decidi instalar w7. Ahi mi grub desaparecio y entraba directo al windows 7. Una vez recuperado el grub, tuve que modificar el archivo a mano porque no se habia actualizado con los datos de w7.

---

### Post by Yaguaron on 2010-03-12
[FONT="Verdana"][COLOR="DarkSlateBlue"]Bueno, al final -y mas que nada porque mi PC se quedaba corta- desinstalé 7 y volví a XP SP3.
Basandome en lo leido en un apunte que encontré por la red, decidi reinstalar Karmic Koala para ver que pasaba, y antes de poder instalarlo, me llevé la sorpresa de que mi equipo es 64-bits, asi que instalé la respectiva version del Koala, pero a la hora de arrancar, el GRUB no aparece y directamente arranca en modo Güindous.
Segun lo que veo en el CD, el sistema está instalado y el GRUB tambien, asi que ya directamente no se que ****** pasa.
Actualmente mi PC esta configurada asi:

Disco Principal (SATA 250 GB): 
Particion A (Wind)(NTFS)
Particion B (reservorio de archivos)(NTFS)
Particion C (Ubuntu)(ext4)(/)
Particion D (reservorio de archivos)(/home)
Particion E (swap) (intercambio)

Disco Secundario (IDE 80 GB):
Unica particion (reservorio de archivos)(NTFS)[/COLOR][/FONT]

---

### Post by Yaguaron on 2010-04-04
Bueno, les comento que hace unos dias cambié mi grabadora de DVD Samsung IDE por una Sony S-ATA, por lo que me quedaron dos unidades SATA y dos unidades IDE y me quedo un conector IDE vacio.
Luego de instalar y comprobar que las conexiones estaban OK, inicie mi PC y -oh sorpresa- me dice "GRUB loading..."
Y en efecto, desde ese momento tengo el Grub cada vez que arranco, inclusive con los dos kernel de ubuntu; lo que tengo como problema es que necesito desenchufar y enchufar el teclado PS/2 cada vez que inicio la compu.
Si alguno sabe que fue lo que me paso, me avisa. Saludos.

---

### Post by guillermolisi on 2010-04-04
> **Yaguaron said:**
> Bueno, les comento que hace unos dias cambié mi grabadora de DVD Samsung IDE por una Sony S-ATA, por lo que me quedaron dos unidades SATA y dos unidades IDE y me quedo un conector IDE vacio.
Luego de instalar y comprobar que las conexiones estaban OK, inicie mi PC y -oh sorpresa- me dice "GRUB loading..."
Y en efecto, desde ese momento tengo el Grub cada vez que arranco, inclusive con los dos kernel de ubuntu; lo que tengo como problema es que necesito desenchufar y enchufar el teclado PS/2 cada vez que inicio la compu.
Si alguno sabe que fue lo que me paso, me avisa. Saludos.
Y esto esta relacionado con dual boot entre Win 7 y Karmic de alguna forma o es un problema aparte ?

---

