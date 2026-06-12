---
title: "Intalación de Ubunty y XP en un disco"
date: 2008-09-10
forum: Software
---

### Post by polaco109 on 2008-09-10
Mi consulta es para los que tiene experiencia en la intalación de los dos sistemas en un disco.
Tengo un disco de 320GB con la 1er partición de 50 Gb donde está instalado el XP. 
Mi idea era crear una partición de 20 Gb para instalar Ubuntu. Fue lo que hice, elegí intalar manualmente, cree la partición de 20 Gb. Primero me advierte q no estoy eligiendo un sector de intercambio. Continué igual y cuando está por finalizar la instalación me tira un error fatal, no puede instalar el grub.

Mi pregunta es, cual es la opción de instalación mas recomendable? Pq creando la partición manualmente no pude hacerlo.
Tampoco quiero que me ocupe mucho espacio del disco.
Mi disco en este momento está particionado:
1-50gb donde está XP.
2-150Gb en NTFS para los datos de XP.
Es decir que me quedan más de 100 gb de los cuales quisiera destinar 20 para Ubuntu. Debería unir lo sobrante con la partición 2? Ubuntu requiere 2 particiones por la de swap?

Bue, espero q me asesoren! Saludos

---

### Post by Afkael on 2008-09-10
A mi criterio (seguramente alguien que sepa más te aconsejará mejor), en la partición de 100gb, desde la instalación manual, haria un partición de 20GB para el sistema raiz (/) y la formatearia a Ext3 y otra de 512Mb (no se de cuánta ram dispones pero para mi con 512Mb está bien tanto si tuvieras 256Mb o 2Gb) y la asignaria como swap (el formato es automático)... la partición que sobra (de casi 80Gb), o bien, la asigno a /home (también en Ext3) o la formateo a NTFS para acceder a el tanto de Windows como de linux.
Te quedaria asi:

1) 50Gb WinXP NTFS
2) 150Gb Datos NTFS
3) 20Gb Linux root Ext3
4) 512Mb Linux swap
5) 79Gb Datos NTFS/Ext3

o hacerlo más limpio:

1) 50Gb WinXP NTFS
2) 229Gb Datos NTFS
3) 20Gb Linux root Ext3
4) 512Mb Linux swap

Saludos

---

### Post by Afkael on 2008-09-10
Ah!! se me chispotio!!

---

### Post by orlyyan on 2008-09-11
Hola amigos soy de Ecuador y tambien tengo el mismo problema pero con un disco de 250 la verdad no se como realizar las particiones.

ahy algun manaul aqui para realizarlo? de ser asi podrian facilitar el link .

---

### Post by ariel on 2008-09-11
> **orlyyan said:**
> Hola amigos soy de Ecuador y tambien tengo el mismo problema pero con un disco de 250 la verdad no se como realizar las particiones.

ahy algun manaul aqui para realizarlo? de ser asi podrian facilitar el link .

Es facil, bootea con el LiveCD de ubuntu, y en el menu principal de ubuntu, anda a: System > Administration > Partition Editor.

---

### Post by Afkael on 2008-09-12
> **orlyyan said:**
> Hola amigos soy de Ecuador y tambien tengo el mismo problema pero con un disco de 250 la verdad no se como realizar las particiones.

ahy algun manaul aqui para realizarlo? de ser asi podrian facilitar el link .

creo que es el primer paso en la instalación, ahi debes elegir el particionamiento manual... si tu disco está limpio:
Ubuntu te exige por lo menos dos particiones.. la memoria de intercambio (swap) y para el sistema en si (/).
Osea, en tu disco, una partición de 512Mb para swap y 249Gb para el sistema.
También recomiendan hacer particiones separadas para /boot y /home. Para boot, depende de los kerneles que vayas a poner ahi, pero estimo que serán suficientes 100Mb, en cuanto a /home (que es el "Mis Documentos" de linux) es util por si toqueteando inutilizas el sistema y debes formatear tus datos permanecerán...
En ese caso:
/= 49Gb ext3 (yo le pongo mucho porque instalo muchos programas)
swap= 512Mb (nomás tienes que especificar que será para swap)
/home= 200Gb
hay más "carpetas" que podrian tener particiones para ellas, pero para una PC de escritorio no tendria mucha utilidad..
En la instalación encontrarás tu disco (por ejemplo sda) y tienes que poner "crear partición nueva" y en la ventanita especificas el tamaño y el formato que vas a usar para la partición).. y na más..

Saludos

PD: me faltó /boot... generalmente se usa el formato ext2

---

### Post by Ulairion on 2008-09-13
Yo tengo una inquietud similar. La cosa es asi:

Tengo dos HDs, uno de 40gb con WXP, archivos de sistema y las instalaciones de los programas; y otro de 140gb con todos los documentos, musica, pelis, etcs. Me gustaría probar Ubuntu pero manteniendo al XP instalado transitoriamente, y pudiendo acceder al disco de documentos desde ambos OS.

¿Es posible? ¿Es muy complicado? ¿Cómo hago? Soy absolutamente nuevo en este tema, asi que si pueden explicarlo como para que lo entienda la abuela mejor :P

---

### Post by Afkael on 2008-09-13
Lo que necesitas es hacer un espacio en el disco para ubuntu...
Si usas windows para juegos y esos programas que ocupan muuucho espacio te conviene dejar los 40gb como están (la instalación de juegos como CoD4, Assasine Creed y Gears of Wars juntos consumen como 20GB de tu disco).
Entonces, yo lo haria particionando el otro disco.. por ejemplo 40gb..
(siempre haz respaldos de tus datos antes de hacer nada..) esa partición la puedes hacer con Partition Magic, Acronis o desde el mismo Administración de discos de Windows (quizá te resulte más cómodo hacerlo asi). Otra opción es que lo hagas desde el LiveCD de ubuntu con Gparted, tienes que configurar la pc para que haga boot desde el cd (como cuando instalas Win) y se cargará un sistama completo sin modificar absolutamente nada de tu HDD, entre los programas instalados en ese sistema está Gparted.
Después de hacer el lugar para Ubuntu inicias el liveCD y ya puedes elegir si instalar o probar (desde donde también puedes instalar también).
Una vez lanzado el instalador eliges la partición que hiciste para instalar Ubuntu (puedes elegir guiado o manual, en estre último caso harás una pequeña partición para swap y el resto para /root como se explica arriba)
A las particiones NTFS puedes "verlas" sin problemas desde Ubuntu (pero desde Win no verás las particiones de linux) por lo que podrás acceder a los datos de tu partición de 100Gb (o el tamaño que le hayas asignado) sólo si le mantienes el formato en NTFS.
Bueno.. no se si fui muy claro.. pero es más sencillo de lo que parece. Saludos

---

