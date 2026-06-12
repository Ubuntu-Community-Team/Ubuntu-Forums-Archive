---
title: "Necesito guía para instalación"
date: 2013-06-17
forum: Software
---

### Post by Vero1 on 2013-06-17
Hola a todos,

Tengo un disco de 500 Gb donde está instalado Ubuntu 12.04 y otro disco donde está instalado Windows XP.
Como el disco de XP está dañado, quiero  re- instalar Windows en donde está Ubuntu.
Siempre se habla de instalar Ubuntu despues de Windows, pero aquí sería alrevés.
Quisiera me digan cuál es la situación.
En el disco donde está  Ubuntu están ocupadas las 4 particiones primarias y me han comentado que Windows debe instalarse en una primaria.
Otra cosa que me dijeron que Windows tiene que instalarse en la primera partición primaria, pero un amigo me dijo que eso no era fundamental, que podía instalarse en cualquier particion primaria. Dijo que se podría eliminar Swap y me quedaría una primaria libre y Swap pasaría a una partición secundaria.

Tengo mas de 300 Gb "sin asignar" por lo que no tendría problemas de espacio.

El Grub se recuperaría con el SuperGrub2 que tengo en un CD.

Agradecería una contestación lo más urgente posible, ya que temo que el disco dañado no me funcione más, ya que me está trayendo problemas de arranque.

Desde ya muchas gracias.

---

### Post by guillermolisi on 2013-06-17
Lo primero que haria en tu lugar es hacer backup de la particion Windows (idealmente un clonado seria tal vez lo mas practico).
Creo que antes de sugerir como hacer lo que queres hacer, seria importante saber como tenes particionado el disco, mas alla de tus comentarios. Para ello podes abrir una consola/temrinal e ingresar ```
sudo fdisk -l
``` pegando la salida para que la podamos ver.
A partir de ello veriamos que seria opciones hay.

---

### Post by Vero1 on 2013-06-17
Hola Guillermo Lisi, gracias por contestar.

Lo que me pedís:
Disco /dev/sda: 41.1 GB, 41110142976 bytes
255 cabezas, 63 sectores/pista, 4998 cilindros, 80293248 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes
Tamaño E/S (mínimo/óptimo): 512 bytes / 512 bytes
Identificador del disco: 0x4f744f74

Dispositivo Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *          63    77288714    38644326    7  HPFS/NTFS/exFAT
/dev/sda2        77288715    80292869     1502077+   5  Extendida
/dev/sda5        77288778    80292869     1502046    7  HPFS/NTFS/exFAT

Disco /dev/sdb: 500.1 GB, 500107862016 bytes
255 cabezas, 63 sectores/pista, 60801 cilindros, 976773168 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes
Tamaño E/S (mínimo/óptimo): 512 bytes / 512 bytes
Identificador del disco: 0x00042355

Dispositivo Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdb1            2048     3905535     1951744   83  Linux
/dev/sdb2         3905536    33202175    14648320   83  Linux
/dev/sdb3        33202176   169920511    68359168   83  Linux
/dev/sdb4       169920512   175779839     2929664   82  Linux swap / Solaris

Un amigo me comentó que tal vez gparted no querría clonar Windows por estar el disco dañado. A lo mejor vos me indicás otro programa para clonar, si hay que usar ese método, y no habría problemas.

Espero noticias y gracias.

---

### Post by guillermolisi on 2013-06-18
Gparted no clonara ese disco porque ese utilitario no clona, solo gestiona y administra particiones.

De minima asegurate de copiar lo que este en Documents and settings/<tu_usuario> (o todo Documents and settings, si tenes lugar donde copiar).

Y si en lugar de trabajar con las particiones del disco de 500Gb virtualizas Windows dentro de Ubuntu ?
Habitualmente que uso le das a esa maquina con Windows ?

Edit: Ventajas de correr Windows virtualizado:
No necesitas modificar las particiones del disco de 500Gb (con el trabajo y demora que ello significa).
Podes contar con los tus mismos archivos que estan en Mis documentos, por ejemplo, en tu /home y verlos tanto desde Ubuntu como desde Windows, en forma totalmente transparente y directa.
No vas a necesitar correr update-grub luego de instalar Windows (cosa que es obligatoria cada vez que instalas Windows en una maquina con dual-boot).
Podras correr Ubuntu y Windows en forma simultanea

Desventajas (posibles):
No podras usar juegos o aplicaciones que requieran aceleracion grafica de video en forma nativa.

---

### Post by Vero1 on 2013-06-18
Cuando hablás de virtualizar a qué programa te referís ? No será Wine no? Porque nunca lo pude utilizar ni me gusta.

Qué uso le doy a Windows? pues no mucho realmente. Lo tengo para cuando tengo algun problema con la impresora(en Ubuntu no puedo ver el nivel de tinta por ejemplo o ejecutar algún trabajo de mantenimiento. Tengo una Epson Stylus C_79.) Tambien para jugar a veces, ya que reconozcamos que Ubuntu no tiene tan buenos juegos y gráfica. Tambien cuando tengo algún problema con la conexión ADSL. En fin, lo tengo como "repuesto" digamos. A veces me ha sacado de problemas cuando se me empacó Ubuntu o el disco.
No tengo cosas importantes pero no quiero prescindir de él por lo que te acabo de mencionar.

"No podras usar juegos o aplicaciones que requieran aceleracion grafica de video en forma nativa. "
Qué quiere decir en forma nativa?

El resto me parece bastante tentador.

Espero tus noticias y gracias

---

### Post by Vero1 on 2013-06-18
Perdón me olvido de algo.
Si virtualizo Windows dentro de Ubuntu, se hace en base al disco donde está ahora o sea el disco queda como está pero no se usa en forma directa?
En tal caso, qué pasa con los sectores dañados y que según información SMART que me pidió mi amigo están justamente donde está instalado Windows?

Gracias

---

### Post by guillermolisi on 2013-06-19
> **Vero1 said:**
> Cuando hablás de virtualizar a qué programa te referís ? No será Wine no? Porque nunca lo pude utilizar ni me gusta.

Qué uso le doy a Windows? pues no mucho realmente. Lo tengo para cuando tengo algun problema con la impresora(en Ubuntu no puedo ver el nivel de tinta por ejemplo o ejecutar algún trabajo de mantenimiento. Tengo una Epson Stylus C_79.) Tambien para jugar a veces, ya que reconozcamos que Ubuntu no tiene tan buenos juegos y gráfica. Tambien cuando tengo algún problema con la conexión ADSL. En fin, lo tengo como "repuesto" digamos. A veces me ha sacado de problemas cuando se me empacó Ubuntu o el disco.
No tengo cosas importantes pero no quiero prescindir de él por lo que te acabo de mencionar.

"No podras usar juegos o aplicaciones que requieran aceleracion grafica de video en forma nativa. "
Qué quiere decir en forma nativa?

El resto me parece bastante tentador.

Espero tus noticias y gracias

Ok.
Considerando esa utilizacion tengo que decirte que si usas Windows virtualizado vas a depender de que Ubuntu funcione para que Windows funcione. Ejemplo: Si tenes problemas con la conexion ADSL y queres verificar si Windows se conecta, Ubuntu debera funcionar y poder conectarse a Internet.

La virtualizacion se logra a traves de software tal como VirtualBox, para mencionar uno, y lo que se obtiene es una maquina virtual, una pequeña PC que se "arma" reservando algunos recursos de hardware y compartiendo otros, cada vez que inicias esa maquina virtual.
Ejemplo: Si tu PC posee 2Gb RAM podrias contar con una maquina virtual con 1Gb para que use Windows y aun queda el resto de los 2Gb RAM para Ubuntu.

Una de las caracteristicas de la virtualizacion es la abstraccion que se genera respecto del hardware real que posee la PC (que aloja a esa maquina virtual). Por ello sucede que podrias tener una placa de video con aceleracion grafica, una nVidia para el caso, y la maquina virtual solo vera una placa de video generica con la cantidad de memoria que esa placa posea pero sin poder utilizar las caracteristicas nativas, propias, avanzadas, de ese tipo de placas. Es decir, va a funcionar muy bien pero no sera lo mismo que logras si Windows corre en forma real y usa el driver de video especifico para esa placa. Por eso algunos juegos no funcionan bajo virtualizacion, en general juegos avanzados con animacion y resoluciones que exigen el maximo de la placa de video (y su driver).

Con la impresora no tendras ningun problema, va a funcionar tal como lo hacia hasta ahora.

---

### Post by guillermolisi on 2013-06-19
> **Vero1 said:**
> Perdón me olvido de algo.
Si virtualizo Windows dentro de Ubuntu, se hace en base al disco donde está ahora o sea el disco queda como está pero no se usa en forma directa?
En tal caso, qué pasa con los sectores dañados y que según información SMART que me pidió mi amigo están justamente donde está instalado Windows?

Gracias

Dado que el disco donde ahora esta Windows no funciona confiablemente, mi recomendacion es hacer una instalacion nueva de Windows, tal como queres hacer reparticionando el disco de 500Gb.

Es instalacion se hace dentro del contexto de maquina virtual que creas con el software de virtualizacion que elijas usar (VirtualBox habia sugerido como ejemplo antes) y no utiliza el disco roto (lo podrias desconectar y retirar de la PC). Por eso mi sugerencia de que copies los contenidos de Documents and settings para recuperar tus documentos, fotos, etc., si los hay.

---

### Post by Vero1 on 2013-06-19
Hola de nuevo,

Mirá prefiero no virtualizar y reinstalar Windows directamente en el disco donde está Ubuntu, instalando luego algunos de los programas que me interesan, ya que utilizo Windows más que por programas por el hardware.
Ahora, hace falta reparticionar si tengo más de 300 Gb sin asignar?
Si opto por esta solución igual tendría que copiar Documents and Settings? Copiar o hacer un backup?
Disculpa tanta pregunta pero nunca hice nada parecido hasta ahora y me gusta ir a lo seguro, dentro de lo posible.

Espero tus comentarios y gracias.

---

### Post by guillermolisi on 2013-06-20
> **Vero1 said:**
> Hola de nuevo,

Mirá prefiero no virtualizar y reinstalar Windows directamente en el disco donde está Ubuntu, instalando luego algunos de los programas que me interesan, ya que utilizo Windows más que por programas por el hardware.
Ahora, hace falta reparticionar si tengo más de 300 Gb sin asignar?
Si opto por esta solución igual tendría que copiar Documents and Settings? Copiar o hacer un backup?
Disculpa tanta pregunta pero nunca hice nada parecido hasta ahora y me gusta ir a lo seguro, dentro de lo posible.

Espero tus comentarios y gracias.

Tenes que reparticionar para poder instalar Windows adecuadamente. Tambien es altamente posible que tengas que mover particiones para poder marcar la de Windows como primaria.

Luego de instalado Windows deberas correr ```
sudo update-grub
``` desde un live CD/USB para recuperar el inicio (boot) para la instalacion Ubuntu que tiene esa maquina (porque Windows pisa la informacion de Ubuntu en el Master Boot Record del disco y esto impide que Ubuntu inicie).

Salvo que en Windows no tengas contenidos de importancia personal, si, hace falta que copies lo que esta en Documents and settings.

---

### Post by Vero1 on 2013-06-20
Este amigo que te comenté me dijo que su idea era que elimine Swap de la cuarta partición primaria para poder ampliar esa partición para Windows. Dijo que probó el funcionamiento de Windows en la cuarta partición primaria y que no tuvo problemas. Te aclaro que él no es especialista en Ubuntu sino en Windows y por éso me sugiriò que confirmara con vos los pasos a dar.
Le haré copy & paste de lo que me indicas mas arriba.
Te agradezco sinceramente el tiempo invertido conmigo y una vez hecho el trabajo, te comunicaré el resultado.

Saludos :-)

---

### Post by guillermolisi on 2013-06-20
Si todos los sistemas instalan un archivo de intercambio y/o una particion swap, cual seria el criterio de aplicacion para no usarlo en forma corriente ?

Me recuerda a los "genios" que para que el motor no recaliente le quitaban el termostato (que obviamente habia sido diseñado e incluido de fabrica para lograr que el motor trabaje a temperatura estable).

Preguntale a tu amigo si usa Windows sin el archivo de intercambio y por que (sea cual sea la respuesta).

Tendria que volver a revisar las particiones de tu disco de 500Gb para decirte concretamente si hace falta o no mover alguna para alojar una primaria para Windows.

---

### Post by Vero1 on 2013-06-21
Guillermo, la idea no es eliminar Swap sino desplazarlo a otro lugar para que quede libre la partición 4.
Mi amigo está preparando un instructivo final y me lo va a enviar en cuanto lo tenga. Este amigo vive en España, por eso tantas idas y vueltas, pero le tengo mucha confianza y no es alguien que dice las cosas porque sí y tampoco cree saberlo todo, ya que él fue el que me dijo que consultara en el Foro Argentino, por si se le escapaba algun detalle.
Si te parece, te envío un image de mi disco de 500.

Gracias y saludos

---

### Post by Vero1 on 2013-06-21
Guillermo, la idea no es eliminar Swap sino desplazarlo a otro lugar para que quede libre la partición 4.
Mi amigo está preparando un instructivo final y me lo va a enviar en cuanto lo tenga. Este amigo vive en España, por eso tantas idas y vueltas, pero le tengo mucha confianza y no es alguien que dice las cosas porque sí y tampoco cree saberlo todo, ya que él fue el que me dijo que consultara en el Foro Argentino, por si se le escapaba algun detalle.
Si te parece, te envío un image de mi disco de 500.

Gracias y saludos

---

### Post by guillermolisi on 2013-06-21
La idea de desplazar la particion Swap es equivalente a desplazar cualquier otra, inclusive la que resulte de reducir una existente, asi que estaras mas o menos en la misma situacion que comente antes.

Siempre hay mas de una forma de lograr un objetivo. Entender pros y cons de cada una para luego decidir es el secreto, la clave.
Suerte con la tarea y ya sabes, aqui estamos para dar una mano.

---

### Post by guillermolisi on 2013-06-21
> Disco /dev/sdb: 500.1 GB, 500107862016 bytes
255 cabezas, 63 sectores/pista, 60801 cilindros, 976773168 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes
Tamaño E/S (mínimo/óptimo): 512 bytes / 512 bytes
Identificador del disco: 0x00042355

Dispositivo Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdb1            2048     3905535     1951744   83  Linux
/dev/sdb2         3905536    33202175    14648320   83  Linux
/dev/sdb3        33202176   169920511    68359168   83  Linux
/dev/sdb4       169920512   175779839     **2929664**   82  Linux swap / Solaris

La particion Swap esta creada con solo 2.9 Gb. No alcanzara por si sola para instalar Windows y contar con algo de espacio para contenidos personales. Vas a tener que reducir la /dev/sdb3 para crear la que alojara Windows y la que funcionara como Swap, con lo cual tendras un buen rato la maquina ocupada con estas tareas.

---

### Post by EnriqueK on 2013-06-21
Eliminá la partición swap , así se sumará al espacio no asignado y a ese total lo creás como extendida, dentro de ella podés crear las  particiones lógicas que quieras, inclusive podés poner allí la nueva swap . La idea es  crear todas las particiones que usa Ubuntu y usando gparted hacés un copy/ paste de esas particiones, borrás las partiones originales, editás el fstab cambiando los nuevos valores de UUID  de las nuevas particiones , de esa manera las tres primeras partiones quedarán disponibles para que instales windows,  lo malo es que así no vas a poder tener el mejor aprovechamiento del DD, por eso recomiendo el siguiente método si es que podés agenciarte de un DD externo.

[http://ubuntuforums.org/showthread.php?t=1759591](http://ubuntuforums.org/showthread.php?t=1759591)

---

### Post by guillermolisi on 2013-06-21
Vero

Podrias mostrarnos la salida del comando```
df -h
```?

---

### Post by Vero1 on 2013-06-21
Hola EnriqueK,
Gracias por tu aporte pero en estos momentos no puedo comprar un DD externo, aparte de que tengo "sin aprovechar" el espacio no asignado de 380 Mb. en este disco.

saludos

---

### Post by Vero1 on 2013-06-21
Si Guillermo:

/dev/sdb2         14G   6,4G  6,7G  49% /
udev             995M   4,0K  995M   1% /dev
tmpfs            401M   968K  400M   1% /run
none             5,0M      0  5,0M   0% /run/lock
none            1002M   384K 1002M   1% /run/shm
/dev/sdb1        1,9G   361M  1,4G  21% /boot
/dev/sdb3         65G   6,1G   55G  10% /home

---

### Post by guillermolisi on 2013-06-21
> **Vero1 said:**
> Si Guillermo:

/dev/sdb2         14G   6,4G  6,7G  49% /
udev             995M   4,0K  995M   1% /dev
tmpfs            401M   968K  400M   1% /run
none             5,0M      0  5,0M   0% /run/lock
none            1002M   384K 1002M   1% /run/shm
/dev/sdb1        1,9G   361M  1,4G  21% /boot
/dev/sdb3         65G   6,1G   55G  10% /home

Pero segun la salida de este comando no estas utilizando toda la capacidad del disco rigido con las particiones que tenes, con lo cual lo unico que habria que hacer es marcar una nueva particion para Windows e instalarlo ahi !

El disco es de 500Gb y actualmente estas ocupando:

1.9 Gb para /boot (/dev/sdb1)
14Gb para / (/dev/sdb2)
65Gb para /home (/dev/sdb3)
Total: aproximadamente unos 80Gb marcados en particiones ! Asi que te deberian quedar al final del disco unos 400 Gb aproximadamente para seguir marcando particiones.

Con marcar una extendida y dentro tres logicas (una para el disco C: con Windows, otra D: para Mis Documentos == /home y la ultima, E:, para alojar el archivo de intercambio de Windows == Swap) es lo que haria en tu lugar.

---

### Post by Vero1 on 2013-06-21
Entonces no necesariamente Windows se debe instalar en una primaria? Porque me habían dicho que sí, razón por la que mi amigo quería quitar de la cuarta primaria a Swap y colocarlo en otra partición, para instalar Windows en la cuarta partición primaria.
Le voy a enviar copy&paste de lo que recomiendas.

Gracias y te tendré al tanto.

---

### Post by guillermolisi on 2013-06-21
Si Windows requiere tener su disco C: en una particion primaria, entonces esta bien replantear la particion Swap y llevar a esta a una particion logica.

---

### Post by Vero1 on 2013-06-21
ok Guillermo, le comentaré lo que me decís.

Volveré en cuanto se haya hecho el trabajo.

Gracias :-)

---

### Post by EnriqueK on 2013-06-24
Creo que  tal vez la mejor alternativa es que eliminés la partición /boot , así tedrás la posibilidad de crear una primaria para instalar Xp, los pasos serían los siguientes
1.- sudo gedit /etc/fstab 
allí comentas la linea que hacer referencia a la partición /boot o sea le pones  # delante para que no la monte al inicio.
2.- arranca con el LiveCd de Ubuntu , ejecuta sudo gparted y allí le pones una etiqueta a las particiones /boot y a la partición /, por ejemplo le pones 
A --> partición sdb1
B --> partición sdb2
3.- monta esas dos particionesm por ejemplo entrandoo al panel lateral de nautilus
cuando estñen montadas, ejecuta siemore en live cd
sudo cp -ax /media/A/. /media/B/boot
no te olvidés de ponerle el punto en la expresión, tiene la finalidad de copiar todos los elementos tanto visibles como ocultos
compona que se hayan copiado los elementos y reiniciá
4.- Si reinicia bien, cosa que no dudo, entrá nuevamente a una sesión live cd para eliminar la swap, ese espacio se sumará como no reconocido , creás una primaria de 20 gb para Xp otra Extendida y dentro de esta creás la swap de tamaño igual a tu ram, unos 200Gb con EXT4 oara datos de Ubunt y el resto en NTFS para datos de Xp
Te va a quedar un espacio no asignado al comienzo del DD, eso se soluciona fácilemnte con gparted , pero eso lo puedes dejar así que no te va a afectar

---

