---
title: "Ayuda con poder montar disco ext3 desde Win$"
date: 2010-01-10
forum: Software
---

### Post by guillermon on 2010-01-10
Hola, con el tema de poder montar el disco de Ubuntu desde Win$, en otra compu que hacía falta puede hacerlo... En la mía nunca lo había intentado, pues me parece inseguro; pero por una razón de espacio lo necesito hacer, y me dice que hay que formatear el disco. Leyendo sé que tiene que ver con incompatibilidad de algo que no entiendo bien (entre 128 y 256 bits...). Ahora, en un post alguien dijo que se puede; le he escrito un MP hace unos días, pero estoy algo apurado... he decidido pedir ayuda a toda la comunidad.

   Aquí "clasificado" dijo: "El acceso desde Ventanas al home ext3 se hace con el [http://www.ext2fsd.com/](http://www.ext2fsd.com/), que hace poco agregó el soporte para ext3 con inodes de 256, así que no hace falta hablar de eso"
Fuente:[http://ubuntuforums.org/showthread.php?t=1365281]("http://ubuntuforums.org/showthread.php?t=1365281")


 Lo he descargado, montado, y me sigue diciendo, al igual que ext2ifs, que quiere formatear el disco. Como soluciones leí de darle formato al disco para que tenga esas características... cuestión que físicamente es imposible para mí (o me llevaría muuucho tiempo, pues no tengo una memoria de 100 gigas externa).
[comentario extra, mi sistema está en ext4,que no tengo intención de montar; mi home está en ext3... al menos yo no he cambiado nada en él]
¿qué estoy haciendo mal o me falta?

Desde ya muchas gracias! Saludos!

Guillermo

---

### Post by juancarlospaco on 2010-01-10
Tas seguro que no sera el actual EXT4 ? :)

---

### Post by guillermon on 2010-01-10
> **juancarlospaco said:**
> Tas seguro que no sera el actual EXT4 ? :)

Lo que sí se, como dije, es que instalé 9.10, el sistema en ext4; el home durante la instalación no toqué nada, así que supongo que está en ext3... 
Hay alguna forma de saberlo? Si está en ext4 se puede hacer algo?

---

### Post by gmunioz on 2010-01-10
Hola gui....:

si lo que quieres es tener acceso a archivos alojados en particiones
linux para copiarlos a particiones windows, usa un live-cd

Desde una sesión live, monta las particiones y copia los archivos
desde linux a windows.

Si quieres hacerlo si o si desde windows, utiliza TotalCommander,.
[www.ghisler.com](www.ghisler.com), y su plugin para ext3 y reiserfs.

---

### Post by guillermon on 2010-01-10
> **gmunioz said:**
> 
Si quieres hacerlo si o si desde windows, utiliza TotalCommander,.
[www.ghisler.com](www.ghisler.com), y su plugin para ext3 y reiserfs.

Hola gmunioz:
     he estado mirando (y recordando), pues en mi primera pc lo tenía! Pero yo no necesito copiar archivos, sino más bien que el disco esté montado, para poder trabajar desde Win$ utilizando espacio de disco ext3 o ext4... En el sistema Win$ me quedé sin espacio, y la solución es usar el de Ubuntu (o encontrarme dinero y comprarme una memoria externa grande).
    Volviendo, ¿TotalCommander permite montar el disco, para luego trabajar con el software?
     Desde ya gracias por la ayuda y por la próxima respuesta...

Guillermo

---

### Post by juancarlospaco on 2010-01-10
> **guillermon said:**
> Lo que sí se, como dije, es que instalé 9.10, el sistema en ext4;  
Hay alguna forma de saberlo? 
[B]
mount | grep ext4[/B]

---

### Post by gmunioz on 2010-01-11
Hola gui......:

Hasta donde se, y hace muchos años que no uso windows, solo
se podía leer, en la actualidad no se.

En Windows, el archivo de swap se llama pagefile.sys. Asi como 
es posible usar este archivo como archivo de swap en Linux, es 
posible utilizar la swap de Linux como swap de Windows, esto te
dejaria espacio libre en tu partición Windows.

Aqui un tutorial:

[http://ubuntuforums.org/showthread.php?t=245393](http://ubuntuforums.org/showthread.php?t=245393)

---

### Post by guillermon on 2010-01-11
> **juancarlospaco said:**
> [B]
mount | grep ext4[/B]

Juan Carlos, perdón por mi ignorancia, pero este comando qué hace?, para qué lo hago?
Desde ya gracias!
Guillermo

---

### Post by guillermolisi on 2010-01-11
> **guillermon said:**
> Juan Carlos, perdón por mi ignorancia, pero este comando qué hace?, para qué lo hago?
Desde ya gracias!
Guillermo
Es la respuesta a tu pregunta sobre como averiguar que particion esta en Ext4 ("Hay alguna forma de saberlo ?")

Ese comando te muestra cuales estan montadas y con formato Ext4.

---

### Post by guillermon on 2010-01-12
> **juancarlospaco said:**
> [B]
mount | grep ext4[/B]

Bien, ahora entiendo (Gracias Guillermo). La respuesta al comando es:
```
/dev/sda2 on / type ext4 (rw,errors=remount-ro)

```
Donde sda2 es: (comando fdisk -l):
```
Disco /dev/sda: 120.0 GB, 120034123776 bytes
255 cabezas, 63 sectores/pista, 14593 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0xd1f0d1f0

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1        1307    10498446    7  HPFS/NTFS
/dev/sda2            1308        2582    10241437+  83  Linux
/dev/sda3            2583        2837     2048287+  82  Linux swap / Solaris
/dev/sda4            2838       14593    94430070   83  Linux

```

La partición que quiero montar es sda4, que es donde tengo mi /home.
Muchas gracias... ¿se podrá?

Guillermo

---

