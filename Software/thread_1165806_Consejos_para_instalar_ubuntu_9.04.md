---
title: "Consejos para instalar ubuntu 9.04"
date: 2009-05-21
forum: Software
---

### Post by RENGOdeDIA on 2009-05-21
Mi PC tiene un disco de 40 GB con xp en el cual también están mis archivos esta casi lleno, como conseguí otro de 80 GB voy a instalar JJ en este y queria hacerles algunas consultas:
Como me recomiendan que particione el disco mas grande(habia pensado en una para / en ext4, /home en ext4, otra con swap y otra en fat32 para documentos)?
La idea es tener dual boot con xp/ubuntu y tener acceso desde cualquiera de los 2 a la partición en fat32 del disco nuevo.
La pc es para uso hogareño, poco y nada de juegos, la usan algunas personas mas. Si necesitan mas datos me avisan.
Gracias y saludos.

---

### Post by juancarlospaco on 2009-05-21
Es buena tu idea si...

---

### Post by RENGOdeDIA on 2009-05-21
Mas dudas:

1. Que tamaño me aconsejan que le ponga a cada partición?

2. La partición en FAT32 la pongo al pricipio, al final o es indistinto?

3. Donde instalo GRUB?

Pido disculpas si son preguntas muy básicas pero no me quiero mandar macanas ya que es mi PC principal. La intención es mas adelante comprarme una nueva e instalarle solo linux y dejarle esta al resto de la familia con win.
gracias por la ayuda!

---

### Post by pol666 on 2009-05-21
fat32?, podes usar ntfs tranquilamente o incluso ext3 (no te aseguro nada con ext4), ya que ubuntu lee ntfs, y windows no lee ext3 PERO con el IFS driver las podes ver, y escribir tranquilamente, así lo tuve yo, (ahora con windows 7 y ext4 el IFS no funciona, no estoy seguro si es problema de ext4 o de windows 7.)

tampoco veo ningun motivo en mandarse errores en una instalación, mientras no metas mano en donde no corresponda.


> 1. Que tamaño me aconsejan que le ponga a cada partición?

proporcionalmente considero que la /home debe ocupar la mayor parte "/" unos 6 o 7gb mientras que la swap un tamaño comparable con tu memoria ram (la misma cantidad o el doble)

> 2. La partición en FAT32 la pongo al pricipio, al final o es indistinto?

Es indistinto mientras quede dentro de lo extendido, no tiene sentido desperdiciar en particiones primarias en ese caso

> 3. Donde instalo GRUB?

El grub se instala en "/" por defecto, salvo que especifiques una ubicacion para "/boot" cosa que no le veo mucho sentido. En ese caso no es necesario hacer nada, salvo que el grub no reconozca algunos de los sistemas y tengas que modificar el menu.lst.

Acordate que al usar dos discos, tenes que indicar en la BIOS que bootee el 2do disco, en el que esta instalado Ubuntu, de otra forma el Grub nunca aparecera.

---

### Post by pablo.s on 2009-05-21
> **pol666 said:**
> El grub se instala en "/" por defecto, salvo que especifiques una ubicacion para "/boot" cosa que no le veo mucho sentido

Mas sentido va a tener si
lo instala en la MBR.

---

### Post by guillermon on 2009-05-21
HOla, si me permiten opinar, respecto al formato fat32; yo lo tenía así en un momento, y eso me permitía tener un disco común a ambos sistemas. Alguien en este foro me comentó que este formato no es tan estable como los otros. Actualmente tengo solo 10 gigas para Win$ (y me arrepiento de no haberle dado un poco más... tal vez 15), Otros 10 para los ficheros de Ubuntu, el Swap y lo que queda Home.
    Como decía, con esto pierdo la facilidad de intercambiar (cuando parece que esto es útil), pero gano en estabilidad y seguridad. Pues si me ataca un virus en Win$ solo podrá hacer daño en ntfs. Sugiero que tengas en cuenta que si instalas el driver que te recomiendan, el virus hablará nuestro lenguaje, por así decir...
    En conclusión, para mí experiencia ya no es necesario un disco de intercambio, pues lo hago con mi datatravel; ya que Win$ está por las dudas (como mal necesario, como por ejemplo, tengo problemas con el editor de video... y quizás tenga que hacerlo desde Win$). Es mi opinión; por lo demás, lo que dices y te sugieren estoy de acuerdo. 
    Aprovecho para enviar un saludo. Hasta pronto

Guillermo

---

### Post by pablo.s on 2009-05-21
> **guillermon said:**
> En conclusión, para mí experiencia ya no es necesario un disco de intercambio, pues lo hago con mi datatravel

Una lástima utilizar un pendrive
para swap...

---

### Post by pol666 on 2009-05-21
> Sugiero que tengas en cuenta que si instalas el driver que te recomiendan, el virus hablará nuestro lenguaje, por así decir...

O_o? lo que quiso decir es que teniendo el driver IFS un virus es alojable en una particion ext. Si por supuesto, todos los archivos son alojables si la particion puede ser escrita, pero de que importa si esos virus no afectan a linux!

No te hagas problema, con excepcion de windows 7 y ext4, el driver IFS me funciono muy bien en Windows Xp y ext3

---

### Post by RENGOdeDIA on 2009-05-22
resumiendo un poco estas serian las opciones:

opción 1
/ en ext4  10 ó 15 Gb
/home en ext4 10 Gb
swap 1.5 Gb
el resto en ntfs para documentos

opción 2
/ en ext3 10 ó 15 Gb
swap 1.5 Gb
/home el resto en ext3
e instalar IFS driver en ventanas para poder ver /home

yo me inclinaría por la opc 1 pero cualquier sugerencia es bienvenida, igual cualquier cosa pruebo las dos y veo como funciona.
Si no se entiende o me falta algo me lo dicen que así se aprende

Saludos!!!!

---

### Post by guillermolisi on 2009-05-22
> **RENGOdeDIA said:**
> resumiendo un poco estas serian las opciones:

opción 1
/ en ext4  10 ó 15 Gb
/home en ext4 10 Gb
swap 1.5 Gb
el resto en ntfs para documentos

opción 2
/ en ext3 10 ó 15 Gb
swap 1.5 Gb
/home el resto en ext3
e instalar IFS driver en ventanas para poder ver /home

yo me inclinaría por la opc 1 pero cualquier sugerencia es bienvenida, igual cualquier cosa pruebo las dos y veo como funciona.
Si no se entiende o me falta algo me lo dicen que así se aprende

Saludos!!!!
Algo que no vi que te hayan dicho es que ext4 acaba de salir y no esta tan probado como ext3 con lo cual hay bastantes posibilidades de que en un futuro no muy lejano surja algun problemita y venga un parche para arreglarlo.

Apenas salio con las versiones previas de JJ, hubo varios problemas y algunos se cobraron el contenido de la particion del disco.

Todo esto no es para meter miedo sino para considerar ext4 como una opcion segun que se pretenda hacer con la maquina y ese file system.

En mi caso lo pruebo en una maquina virtual que, si se rompe, la recupero de un backup y sigo adelante, cero costo.

En mis maquinas de trabajo no lo uso, sigo con el viejo, querido y confiable ext3. Asi y todo JJ anda mas rapido que sus antecesores.

---

### Post by guillermon on 2009-05-23
> **RENGOdeDIA said:**
> 
opción 1
/ en ext4  10 ó 15 Gb
/home en ext4 10 Gb
swap 1.5 Gb
el resto en ntfs para documentos

yo me inclinaría por la opc 1 pero cualquier sugerencia es bienvenida,

 Hola, con esta opción, como veo que ya sabes, tu home no será legible desde Win$; pero sí ntfs para ambos sistemas. Con esto logras tener lo que yo mal llamé "intercambio" entre los dos. Ten en cuenta que allí tus archivos son vulnerables a los virus, y que el sentido de tu /home se amplia... Por otra parte, lo que dice Guillermo Lisi es para considerarlo... Yo me tenté, pero seguí ese consejo. Hay otros formatos además de ext3... he leido que Reiser tiene otras propiedades, si estás curioso.
  Un saludo

---

### Post by guillermolisi on 2009-05-23
> **guillermon said:**
> Hola, con esta opción, como veo que ya sabes, tu home no será legible desde Win$; pero sí ntfs para ambos sistemas. Con esto logras tener lo que yo mal llamé "intercambio" entre los dos. Ten en cuenta que allí tus archivos son vulnerables a los virus, y que el sentido de tu /home se amplia... Por otra parte, lo que dice Guillermo Lisi es para considerarlo... Yo me tenté, pero seguí ese consejo. Hay otros formatos además de ext3... he leido que Reiser tiene otras propiedades, si estás curioso.
  Un saludo
RaiserFS es muy aconsejable cuando se almacenan muchos archivos de tamaño pequeño ya que por sus caracteristicas se aprovecha al maxino la capacidad del disco y la rapidez del FS.

Un tema que puede llegar a preocupar es que su creador esta "out of order" porque parece que intento asesinar a su mujer y a menos que tenga la mente abstraida de eso hecho y disponga de una maquina, se complicara la evolucion de ese file system a futuro.

---

### Post by josecuervo86 on 2009-05-23
> **guillermolisi said:**
> RaiserFS es muy aconsejable cuando se almacenan muchos archivos de tamaño pequeño ya que por sus caracteristicas se aprovecha al maxino la capacidad del disco y la rapidez del FS.

Un tema que puede llegar a preocupar es que su creador esta "out of order" porque parece que intento asesinar a su mujer y a menos que tenga la mente abstraida de eso hecho y disponga de una maquina, se complicara la evolucion de ese file system a futuro.

Intento... y la mato nomas! 15 años le dieron en el 2008 por asesinato en 2do grado. Asique a no ser que pueda seguir desarrollando desde la carcel la veo bastante jodida :D

---

### Post by RENGOdeDIA on 2009-05-23
Me parece que entonces me voy a inclinar por ext3, como había leído que ext4 hace mas rápido el arranque y viene con el nuevo ubuntu pensé que era estable, pero dado que esta es la pc principal y siguiendo sus consejos lo dejo para probar mas adelante.



>  tu home no será legible desde Win$. 
Si no es necesario para que funcione bien cualquiera de los dos SO, no me interesa ver /home desde win, solo quiero tener acceso desde ambos a una partición donde estés mis archivos (lease fotos, musica, videos, documentos, etc)



> Ten en cuenta que allí tus archivos son vulnerables a los virus, y que el sentido de tu /home se amplia... 
Si me pueden explicar mejor lo del sentido del home se los voy a agradecer.



El tamaño de las particiones están bien? las puedo ampliar o reducir de tamaño mas adelante y una vez instalado JJ?

Gracias de nuevo, si me surge otra duda posteo pero ya se me va aclarando el panorama
Slds

---

### Post by guillermon on 2009-05-24
> **RENGOdeDIA said:**
> 
Si no es necesario para que funcione bien cualquiera de los dos SO, no me interesa ver /home desde win, solo quiero tener acceso desde ambos a una partición donde estés mis archivos (lease fotos, musica, videos, documentos, etc)
Si me pueden explicar mejor lo del sentido del home se los voy a agradecer.
El tamaño de las particiones están bien? las puedo ampliar o reducir de tamaño mas adelante y una vez instalado JJ?
Gracias de nuevo, si me surge otra duda posteo pero ya se me va aclarando el panorama
Slds
Me parece que por querer ayudarte te he confundido (me dedico a otra cosa, mi lenguaje no es el idóneo; intento ayudar de corazón), pero esta última hace aparecer una confusión previa, me parece. ¿qué es el home? Me parece que la respuesta  más sensata sería que equivale al Mis documentos de Win$... Lo clarificador sería que reflexiones porqué estás particionando, es decir, separando la raíz (/) del home (/home). Y luego porqué harías otra partición para tus fotos y música...
 Cito un manual: [I]El directorio home es el directorio asignado a cada usuario de un sistema Linux. En él, los usuarios
pueden crear archivos y directorios propios, a los que el usuario puede controlar el acceso de otros usuarios. La mayoría de los usuarios trabajan regularmente con los archivos y directorios que crean
bajo su directorio home.[/I] Lo que ubiques aquí, no podrás verlo desde Win$ (a menos que instales el driver). 
Entonces, con lo de "ampliar" -mal usado de mi parte- quise decirte que tendrás que pensar: "esto lo pongo en el home, o en el fat32", como me pasó a mi... 
  Luego tendrás que aprender la idea del propietario, grupos y permisos... No te desanimes. No dudes en pedir ayuda (yo tengo buena paciencia, pues me pasó a mi).
  No quiero extenderme más. Tu pregunta sobre las asignaciones de espacio depende de cuántas particiones; pero como lo vienes pensando está muy bien. Suerte, y hasta pronto

---

### Post by RENGOdeDIA on 2009-05-24
> **guillermon said:**
> Me parece que por querer ayudarte te he confundido (me dedico a otra cosa, mi lenguaje no es el idóneo; intento ayudar de corazón), pero esta última hace aparecer una confusión previa, me parece. ¿qué es el home? Me parece que la respuesta  más sensata sería que equivale al Mis documentos de Win$... Lo clarificador sería que reflexiones porqué estás particionando, es decir, separando la raíz (/) del home (/home). Y luego porqué harías otra partición para tus fotos y música...
 Cito un manual: [I]El directorio home es el directorio asignado a cada usuario de un sistema Linux. En él, los usuarios
pueden crear archivos y directorios propios, a los que el usuario puede controlar el acceso de otros usuarios. La mayoría de los usuarios trabajan regularmente con los archivos y directorios que crean
bajo su directorio home.[/I] Lo que ubiques aquí, no podrás verlo desde Win$ (a menos que instales el driver). 
Entonces, con lo de "ampliar" -mal usado de mi parte- quise decirte que tendrás que pensar: "esto lo pongo en el home, o en el fat32", como me pasó a mi... 
  Luego tendrás que aprender la idea del propietario, grupos y permisos... No te desanimes. No dudes en pedir ayuda (yo tengo buena paciencia, pues me pasó a mi).
  No quiero extenderme más. Tu pregunta sobre las asignaciones de espacio depende de cuántas particiones; pero como lo vienes pensando está muy bien. Suerte, y hasta pronto


Yo tengo entendido que en el /home, aparte de los archivos personales (fotos, música, etc), se guardan todas las configuraciones personales del SO y de las programas instalados para que en caso de reinstalar o actualizar no se tenga que configurar todo otra vez. A estas configuraciones no me interesa verlas desde xp, es por eso que los quiero poner en otra partición, una especie de "mis documentos" para ambos SO.
**Que diferencia hay para linux que los archivos personales estén en otra partición fuera de /home?**
Gracias por las sugerencias...

---

### Post by guillermolisi on 2009-05-24
> **RENGOdeDIA said:**
> Yo tengo entendido que en el /home, aparte de los archivos personales (fotos, música, etc), se guardan todas las configuraciones personales del SO y de las programas instalados para que en caso de reinstalar o actualizar no se tenga que configurar todo otra vez. A estas configuraciones no me interesa verlas desde xp, es por eso que los quiero poner en otra partición, una especie de "mis documentos" para ambos SO.
**Que diferencia hay para linux que los archivos personales estén en otra partición fuera de /home?**
Gracias por las sugerencias...
Si cuando hablas de archivos personales te referis a los archivos que generas y mantenes a partir de tu trabajo y actividad diaria a partir de programas utilitarios y aplicativos, ninguna.

Es cierto que en /home/<usuario> se guardan los archivos de configuracion personal para ese usuario por lo que en realidad la equivalencia con la estructura de Windows seria "Documents and Settings\<usuario>".

---

### Post by RENGOdeDIA on 2009-05-24
> **guillermolisi said:**
> Si cuando hablas de archivos personales te referis a los archivos que generas y mantenes a partir de tu trabajo y actividad diaria a partir de programas utilitarios y aplicativos, ninguna.

Es cierto que en /home/<usuario> se guardan los archivos de configuracion personal para ese usuario por lo que en realidad la equivalencia con la estructura de Windows seria "Documents and Settings\<usuario>".

Exacto guillermolisi a eso me refería. Bueno me pongo a instalarlo despues posteo como salio todo.
Gracias a todos

---

