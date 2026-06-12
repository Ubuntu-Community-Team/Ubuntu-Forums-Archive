---
title: "Duda al reinstalar"
date: 2008-08-13
forum: Software
---

### Post by Skyfilms on 2008-08-13
Hola, estuve toqueteando y anda todo mal. (Como ven, todavia no entiendo nada.) Puse el kubuntu, intente desinstalarlo por aplicaciones, y ahora tengo ubuntu. Lo quiero reinstalar, para empezar todo desde cero pero mi duda es la siguiente:

- Tengo instalado win xp en C:
- Instale ubuntu (automaticamente) en G:
- Alli tengo carpetas de datos importantes a las que accedo desde windows (y ubuntu) y no quiero perderlas.
El tema es que cuando me pide hacer las particiones me dice que se borraran los discos de las particiones no eliminadas. como hago para instalar nuevamente ubuntu en G: sobre la vieja instalacion sin borrar los demas datos del mismo disco?
Gracias!

---

### Post by faktorqm on 2008-08-13
Para hacer eso tendrias que haber puesto el /home en otra particion, si pusiste todo junto en "/" no podes. arranca el ubuntu, move los datos a la particion de windows, y ahi si arranca la instalacion del nuevo en el mismo lugar. a proposito, "g:" no existe, instalaste windows en una particion, y gnu/linux en otras dos. ("/" y swap)
Te recomiendo que busques aca mismo en este subforo todas las recomendaciones sobre como instalar ubuntu de la mejor manera que se han discutido hasta el cansancio, mas guias de instalacion que tambien se postearon mucho. Salu2!!!

---

### Post by Skyfilms on 2008-08-13
> **faktorqm said:**
> ... a proposito, "g:" no existe, instalaste windows en una particion, y gnu/linux en otras dos. ("/" y swap)

Si, tengo varios discos, uno particionado en 2 (C: y D:) y 3 mas (E: F: y G: mas el DVD que es H:,  pero no puedo instalar Ubuntu en C: porque alli tengo poco espacio, destinado unicamente a windows. En los tutoriales de instalación no encontre cómo proteger mis datos al hacer las particiones de ubuntu en el mismo disco donde tengo esos datos. O quizás yo no se si hacer una partición significa que se borran todos los datos del disco entero que estoy particionando, o simplemente formatea solo el espacio que reserva esa partición y deja libre el resto del disco. Pero insistiré en la busqueda. Gracias por responder. Saludos.

---

### Post by [P]oli on 2008-08-13
> **Skyfilms said:**
> Si, tengo varios discos, uno particionado en 2 (C: y D:) y 3 mas (E: F: y G: mas el DVD que es H:,  pero no puedo instalar Ubuntu en C: porque alli tengo poco espacio, destinado unicamente a windows. En los tutoriales de instalación no encontre cómo proteger mis datos al hacer las particiones de ubuntu en el mismo disco donde tengo esos datos. O quizás yo no se si hacer una partición significa que se borran todos los datos del disco entero que estoy particionando, o simplemente formatea solo el espacio que reserva esa partición y deja libre el resto del disco. Pero insistiré en la busqueda. Gracias por responder. Saludos.

Lo que te está diciendo es que dejes de llamarlo por letras, porque estás mezclando Windows y Gnu/Linux en su forma de "llamar" a las particiones.

Si formateas una partición, perdés TODO lo que esté en ESA partición, nada más, no se te formatea todo el disco ni nada de eso. Si querés salvar una carpeta, pasala a otra partición que sepas que no vas a formatear o bajala a un cd/pen-drive/etc etc.. 
Si vas a cambiarle el tamaño/hacer/borrar una partición casi seguro te formatea TODO el disco, guarda con eso..
Creo que ahí te contesté todas las preguntas, cualquier cosa seguí preguntando :lolflag:

---

### Post by pol666 on 2008-08-13
Nah no seas fatalista, osea podes cambiarle el tamaño a una particion, tambien borrar, pero no andes jugando mucho con las particiones, Te doy un consejo?pór que no entidimos nada...

Anda a ubuntu, y ejecuta Gparted (editor de particiones) sino lo tenes
sudo apt-get install gparted, y despues abrilo, no toques nada solo sacale una cap y subila para ver que queres hacer

---

### Post by faktorqm on 2008-08-14
mas rapido y mas facil, postea la salida de este comando:

```
sudo fdisk -l
```

salu2!!

---

### Post by Skyfilms on 2008-08-14
> **faktorqm said:**
> mas rapido y mas facil, postea la salida de este comando:

```
sudo fdisk -l
```

salu2!!

Bueno, gracias a todos los que respondieron, y a que lei un poquito mas de esto de las particiones linux, voy entendiendo mas, y teniendole mas confianza de apoco. Igualmente no me quiero jugar todavía ja ja.. aca va el resultado de **sudo fdisk -l**
(aclaro que desconecte 2 discos que solo eran de datos de windows y los deje para archivar)
.........................................................................
Disco /dev/sda: 163.9 GB, 163928604672 bytes
255 cabezas, 63 sectores/pista, 19929 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x77877787

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1        3187    25599546    7  HPFS/NTFS
/dev/sda2            3188       19929   134480115    f  W95 Ext'd (LBA)
/dev/sda5            3188       19929   134480083+   7  HPFS/NTFS

Disco /dev/sdb: 320.0 GB, 320072933376 bytes
255 cabezas, 63 sectores/pista, 38913 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x77d977d9

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdb1               1       38913   312568641    7  HPFS/NTFS
.........................................................................
Gracias Mil!

---

### Post by Skyfilms on 2008-08-15
Si alguien tiene la paciencia de guiarme paso por paso, para instalar ubuntu en el disco de 300 gb, y no borrar los datos que tengo alli, estaría muy agradecido, ya que por ahora esto es muy nuevo para mi y es una pc que uso para trabajar.
  Realmente estoy copado con la filosofia linux y quiero de a poco ir dejando el win, ademas de difundir linux lo maximo que pueda. Desde ya, mil gracias.

---

### Post by faktorqm on 2008-08-15
Bueno, mete el cd de ubuntu, y llega hasta la parte de particionado manual. Luego de eso redimensiona la particion que esta ahora al tamaño de, no se, por ejemplo 100gb. Entonces poné, una particion de 15gb para "/" (que es una bestialidad de espacio pero esta bien igual), 183gb para tu /home, y 2gb para swap. tonces te quedan 4 particiones, todas PRIMARIAS te conviene, (solo si vas a hacer 4, si queres mas vas a tener que hacer extendidas) y ya. Si esto no era lo que querias hacer, o yo entendi mal, avisa. salu2!

---

### Post by Skyfilms on 2008-08-15
Bue, ya reinstalé. Hice las 3 particiones en el espacio libre en el segundo HD (dev/hdb). Aparentemente todo bien.
Pero ahora no veo el resto del disco donde tenia los datos. Incluso entro desde windows y ese disco en Mipc no existe.
(Menos mal q hice backup de la mayoria de los arch. a otro disco!).
Aunque cuando entro al administrador de discos lo veo y están las 3 particiones de ubuntu (dice: particion desconocida) y tengo el resto (218 gb) que dice NO ASIGNADO. Igual con ubuntu, en gpart me aparece no asignado.
¿Estaran los datos alli? 
¿Tengo que hacer una particion nueva? Con que caracteristicas?
¿tengo que formatear ese espacio para poder usarlo? con windows o ubuntu?
¿o quizás darle desde windows a "convertir a disco dinámico" ?
???

---

### Post by sajnox on 2008-08-16
Windows no lo ve al disco por que nativamente no lee particiones en ext3, si en Ubuntu lo ve, no te preocupes que esta todo bien.

Si queres acceder a tus datos desde windows tenes que instalar un driver que permite hacerlo. Googlea por ifs2 driver o "particiones ext3 en windows"

Saludos

---

### Post by Skyfilms on 2008-08-16
> **sajnox said:**
> Windows no lo ve al disco por que nativamente no lee particiones en ext3, si en Ubuntu lo ve, no te preocupes que esta todo bien.

[B]No, Ubuntu no ve ese resto del disco. Antes (en la anterior instalación) lo veía adentro de la carpeta "host".
Ahora nada.... solo aparece en gpart como espacio sin asignar (igual que en windows)[/B] podre recuperar los datos?

---

### Post by pol666 on 2008-08-16
¿? eliminaste la particion?

---

### Post by Skyfilms on 2008-08-16
> **pol666 said:**
> ¿? eliminaste la particion?

Lo que hice fue crear las 3 particiones manualmente desde el live cd de ubuntu, al inicio de la instalacion, en donde decia espacio libre, en el disco mas grande. Solo puse formatear las nuevas no el espacio libre. Que fue lo que paso al hacer eso, no se... ...si se eliminaron los datos o estan alli. el tema es que no tengo acceso y no se como ver los datos, o aunque sea poder usar ese tramo del disco para guardar datos nuevos.
Ah! Lo que recuerdo es que el crear las particiones desde el install de ubuntu, habian 2 casillas que decian al principio o al final, y yo deje lo que decia por defecto, al principio. Quizas fue eso? :confused::confused::confused:

---

### Post by Skyfilms on 2008-08-18
Bueno, ya está todo OK: Formatie la particion que no veia desde windows. Ahora la veo tambien en Ubuntu. Gracias a todos por responder. Voy a jugar un rato con los pluguins del Compiz, que usaré 1 semana o 2 hasta cansarme, pero igual estan impresionantes, mas siendo en un sistema libre, y luego me voy a poner a estudiar las guias, que recien descubro, antes de seguir "urgando" en lo que no se. :)
Salu2.

---

