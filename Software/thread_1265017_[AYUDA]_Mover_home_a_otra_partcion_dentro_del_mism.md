---
title: "[AYUDA] Mover /home a otra partcion dentro del mismo disco duro"
date: 2009-09-12
forum: Software
---

### Post by andres2420 on 2009-09-12
Que tal gente, mi nombre es Andrés y tengo una duda que practicamente queda descripta en el titulo.

Tengo un disco duro de 160 gb que esta asi:

[[IMG]http://img44.imageshack.us/img44/9969/particiones.jpg[/IMG]]("http://img44.imageshack.us/i/particiones.jpg/")

Me gustaria que la particion de windows, pase a ser /home, se claro esta que primero debo darle formato etx4, pero despues de ahi como hacer todo lo demas no se para donde disparar.

Estoy leyendo guias para hacerlo ( san google al toque me respondio sobre mi duda) pero me trabo en el tema de montar la particion nuevo o crear una nueva para que ahi se aloge el nuevo /home...realmente estoy comenzando con esto y cometi el grabe error de no separar /home de lo demas...

En fin si alguien me puede pasar una date se lo agradesco

Andrés

---

### Post by gmunioz on 2009-09-13
Hola and...:

Una vez que tengas formateada la partición debes 

montarla en un directorio de nombre temporario
 
para poder copiar a ella los archivos de  /home 

En consola ejecutas:

```
sudo -i

Te logueas como root
```


```
mkdir /media/hometemp

Creas un directorio de montaje temporal
```


```
mount /dev/sda1 /media/hometemp

Montas la partición en el directorio temporal
```


```
cd /home

cp -ax . /media/hometemp

[I]Esta linea es la única que sirve para clonar
presta atención al "." que sigue a -ax[/I]

Clonas tu directorio /home
```


```
cd /

mv /home /home.old

mkdir /home

mount /dev/sda1 /home

Renombras /home antiguo, montas el nuevo /home

```


```
vol_id -uuid /dev/sda1

*copia la salida*

gedit /etc/fstab

Añade estas lineas al final del archivo

#/dev/sda1 
            
UUID=**aqui la salida de vol_id** /home ext4 defaults 0 2

Averiguas la UUID de la partición y editas el archivo/etc/fstab, 
para montar la partición al inicio
```


Al reiniciar tendrás todo funcionando exactamente igual, pero con particiones separadas.

Una vez que todo esta funcionando bien, ejecutas

```
sudo -i

rm /home.old

rm /media/hometemp

```

---

### Post by andres2420 on 2009-09-14
AMigo mas que todo te agradesco los TREMENDAMENTE EXPLICADO QUE ESTA ESTO.Realmente cuando lei esa respuesta al toque copiar y pegar en un documento nuevo...JUSNTO CON MIS OTROS MILES DE MANUALES.Muchas gracias posta.

AHora te hago una consulta; puedo remplazar este que me decis en el paso 4

```

cd /home

cp -ax . /media/hometemp
```

por esto otro que lei tambien?

```
 
cd /home

find . -depth -print0 | cpio –-null –-sparse -pvd /media/hometemp
```

Y una cosa más por si a alguein mas le sirve, vos sabes que haciendo este paso:

```
vol_id -uuid /dev/sda1
```

Me daba este error **vol_id: invalid option -- 'i'**

Por lo que use esto:

```
blkid /dev/sdb1
```

Obteniendo como resultado esto:

**/dev/sdb1: UUID="D8A8CB4BA8CB26BA" LABEL="AOP" TYPE="ntfs"**

Bueno loco te agradesco y mañana cuando tenga la pc lo hago y te comento muchas gracias.

Andrés

---

### Post by gmunioz on 2009-09-14
Hola...:

1 - Si, se puede reemplazar:

```
cp -ax . /media/hometemp

con

find . -depth -print0 | cpio –-null –-sparse -pvd /media/hometemp

```


2- en karmic, vol_id ya desapareció y se debe usar blkid,

respecto de vol_id la orden es:

sudo vol_id - -uuid /partición (con dos guiones)

---

### Post by andres2420 on 2009-09-14
Che amigo vos sabes que no me funciono?

Cuando termine de hacer todo los pasos menos el ultimo de reiniicar y vorrar los directorios, quise crear una carpeta pero me dijo que no tenia permisos.Despues me fui al nuevo /home y con chmod le di permisos y ahi si me dejo crear y borrar.

Despues reinicie la pc y cuando iniece secion me decia que no podia entronctrar /home/andres que es mi usuario y me decia de si queria cargar entonces el de root.

Lo que hice fue entonces borrar el nuevo home y renombrar a home.old a home y borrar la entrada de fstab y ahi levanto de nuevo.

Me parece que el problema es con los permisos de los directorios que voy creando...realmente no se como sera eso.

---

### Post by gmunioz on 2009-09-14
Hola Andrés:

El procedimiento lo he usado varias veces y siempre

funcionó.

¿Has usado cp -ax . /media/hometemp?

Esta es la orden que siempre usé.

---

### Post by EnriqueK on 2009-09-14
Francamente hay dos cosas que no me guastan de tu tabla de particiones, una que que tenés a Ubuntu instalado en una partición lógica y pretenderías mover tu /home a una partici&#7765;m primaria y lo otro es que la partición de Ubuntu quedará con mucho espacio disponible que jamás va a opcupar, obligándote a particionarla para poder aprovechar el espacio de disco.
Para mi lo mejor es que reinstalés el sistema redefiniendo una adecuada tabla de particiones, pero previo respaldo de tu carpeta de usuario y muchísimo mejor si tenés todos los paquetes descargados en el caché (/var/cache/apt/archives), si nunca aplicaste sudo apt-get clean, vas a tener tu caché intacto y la reinstalación de todos los paquetes es cuestión de minutos una vez hecha la instalación básica, si querés te puedo dar mas detalles de como hacer todo esto .
Cualquiera sea la alternativa que emplees, es altamente recomendable que hagas un respaldo completo de tu carpeta de usuario, una buena forma de hacerlo es empleando los siguientes comados

> cd /tmp
sudo tar zcvf casa.tar.gz /home/usuario
Esto creará en el directorio temporal /tmp el archivo comprimido casa.tar.gz que será el respaldo de tu carpeta de usuario , pero debes grabarla a un DVD por que al estar en /tmp se perderá en el próxino reinicio.

---

### Post by anarko on 2009-09-14
> **andres2420 said:**
> Che amigo vos sabes que no me funciono?

Cuando termine de hacer todo los pasos menos el ultimo de reiniicar y vorrar los directorios, quise crear una carpeta pero me dijo que no tenia permisos.Despues me fui al nuevo /home y con chmod le di permisos y ahi si me dejo crear y borrar.

Despues reinicie la pc y cuando iniece secion me decia que no podia entronctrar /home/andres que es mi usuario y me decia de si queria cargar entonces el de root.

Lo que hice fue entonces borrar el nuevo home y renombrar a home.old a home y borrar la entrada de fstab y ahi levanto de nuevo.

Me parece que el problema es con los permisos de los directorios que voy creando...realmente no se como sera eso.


Te fijaste si se habia montado el /dev/sda1 /home?
para ver esto el comando "mount" te describe donde esta montada cada particion de cada cosa que tenes.
Te deberia mostrar algo como : 
```
/dev/sda3 on /home type ext3 (rw,relatime)
```
Por ahi le pifiaste en el ssuid en la linea del fstab, para ver si el fstab esta todo bien podes probar con el comando "mount -a" este remonta todo lo que tengas en el fstab, si hay algo mal te va a decir que.
Error comun es no dejar una linea en blanco al final del archivo, me pasa siempre :p.
Si todo esta bien montado fijate los permisos con los que te quedaron las carpetas /home 
Yo tengo as: 
```

anarko@Marcos:~$ ls -l /
...
drwxr-xr-x   5 root root  4096 2009-08-05 11:28 home
...
anarko@Marcos:~$ ls -l /home
total 36
drwxr-xr-x  63 anarko anarko  4096 2009-09-14 16:10 anarko
...

```

---

### Post by andres2420 on 2009-09-15
Antes que nada GRACIAS POR RESPONDER.

**gmunioz**

Nop realmente no uses el comando que me decias...para seguir probando me voy a fijar en eso.Apenas llegue a casa, pruebo dicho opcion.

**EnriqueK**

Amigo. exactamente a mi tambien NO ME GUSTA lo que comentas.El porque de eso, es simple...tube windows 3 años y este años instale ubuntu es la mitad del disco que quedaba.Ahora chau widnows, pero sigue siendo la particion asi...

El problema de resintalar todo es que me da muchas cosa, porque como te comente hace meses que lo tengo a ubuntu Y ANDA MEJOR QUE NUNCA, lo eh "toqueteado", configurado, modificado,instale,a gusto Y QUE TODO SE PIERDA REALMENTE NO TENGO GANAS.
Tengo una copia exacta del home en un disco aparte que genere cuando se me ocurrio borrar windows y poner ahi home, pero como no se mucho, no se donde se aloja todo lo que "toquetee" o mejore, realmente instalar todo de nuevo y empesar desde 0 no me agrada mucho PERO SERIA LO IDEAL. ( lo del cache me gusta la idea de que se conserve ( no eh echo apt-get clean...si el apt-get autoremove....NO ES LO MISMO NO?) pero me gusrdara las cantidad de cosas que tengo descargadas e instaladas?)

Voy a intentar hacer de todos modos, de pasar a la otra particion...de ultima me voy a empesar a poner una lista de lo que eh echo y reinstalo todo...

( mas que todo me preocupa no en si lo programas que instalo, si no por decirte un ejemplo nada mas, las cosas que puse que inicien, las que no, que ni me acuerdo o que ni me aucerdo que configure pero que me mejoro tal o cual cosa).


**anarko**

Si, che me fije al toque que estubieses montada la particion.Tanto por comandos como por la interfaz fgrafica...posta se que estaba montada

Por el tema del uuid lo revise 20 VESES porque digo...si el mando cualquiera a esto ****.Si lo recontra copie 20 veses.

Por el tema de los permisos ahi si que me genera la duda, por ejemplo ahora cuando quiere ver los permisos del directorio /home
me tira:

drwxrwxrwx en lugar de como vos drwxr-xr-x...soy nuevo en esto CAPAS QUE ES LO MISMO Y YO TE LO PONGO COMO ALGO IMPORTANTE...no se.

En serio gente gracias por ayudar.

Tengo una duda de que poner en el archivo fstab luego del uuid-punto de montaje-formato a partir de ahi no se que es 

defaults 0 2

Algunos eh visto ponen un 1 en lugar de un 2 otros en lugar de un defaults le ponen notail,defaults o nodev,nosuid 0 2 NO TENGO IDEA DE QUE QUIERE DECIR ESOS PARAMENTROS y cual poner.Para mi radida ahi el problema porque el cartel que me sale en el centro de la pantalla cuando inicia es que no "encontro el $HOME/andres...quiere usar el del / root? " y me da SI NO...como que no lo monta al /home al inicio, entonces no encuentra donde cargar mis cosas y palma.

Un abrazo gente

---

### Post by Hei Ku on 2009-09-15
Andres, por favor moderá tu lenguaje, y tratá de evitar las mayusculas. Gracias.

---

### Post by gmunioz on 2009-09-15
Hola andrés:

1- Puede que ese sea el problema de los permisos, si bien

los comandos hacen cosas similares, copiar directorios con

sus subdirectorios y archivos ocultos, son distintos y quizás

ahi esta el problema.

2- Respecto de /etc/fstab:

Es el archivo donde se guardan los diferentes datos sobre 

el montaje de los dispositivos físicos.

El fstab se compone de 6 secciones:

file system: 
Es el lugar donde se encuentra el dispositivo físico a montar,
como por ejemplo /dev/hda1, /dev/sda, etc.

mount point: Es el punto de montaje donde sera montado el 
dispositivo físico.

type: Es el tipo de archivo con el que sera montado el 
dispositivo físico, ext*, swap, reiserf, etc.

options: Son las opciones con las que sera montado el 
dispositivo físico.

dump: Esta opcion solo puede poseer el valor 0 o 1, en 
ella se guardan los errores en tiempo de sistema que ha 
reportado el sistema de archivos lo normal es tenerlo 
desactivado (0), ya que rara vez se produce un error.

pass: Si la activamos (1) el sistema realizara una pasada 
cada X desmontadas o si el dispositivo a sido desmontado
incorrectamente para comprobar su integridad. 
Es recomendable tener la partición root con un 1 y poner 
un 2 a las restantes por si el kernel puede usar el 
paralelismo del hardware,


Las opciones mas usadas son:

defaults: Es la suma de rw,suid,dev,exec,auto,nouser y async.

rw: Read-Write. Con esto montamos la partición para que sea 
posible tanto leer como escribir en el dispositivo físico, 
esta opción es muy usada con dispositivos que permiten la 
escritura como por ejemplo los pendrives o los disquetes, 
ya que sin esta opción, no podríamos guardar datos en ellos.

ro: Read-Only. Con esta opción hacemos que no se pueda 
escribir en el dispositivo, que tan solo se pueda leer.

noexec: Impide la ejecución de cualquier archivo en el 
dispositivo en el que esta opción sea activada, esta 
opción suele ser muy útil cuando en una misma maquina diversos 
usuarios tienen acceso a un mismo dispositivo y no queremos 
que estos puedan ejecutar archivos en los dispositivos.

nodev:  con esta opción impedimos que se interpreten los 
dispositivos especiales de bloques y de caracteres presentes 
en el dispositivo.

dev: Opción contraria a nodev, es decir, al activar esta opción
 permitimos que puedan usarse nodos de dispositivo en el sistema 
de archivos.

auto: Con esta opción hacemos que el dispositivo que la contenga
sea iniciado SIEMPRE que se inicie el sistema.

no auto: Con ella hacemos que el dispositivo no sea montado al 
iniciarse el sistema, y tan solo sera montado en el momento en 
el que le vayamos a dar uso, 

user: Permite a cualquier usuario del sistema montar o desmontar 
un dispositivo físico sin necesidad de ser root, esta opción es 
muy útil para dispositivos de uso frecuente, como cd-roms o disquetes.

uid=X: Con esta opción indicamos que tan solo el usuario o 
el grupo con el uid especificado tiene el control sobre los archivos
del dispositivo.

async: Con esto hacemos que las operaciones que realicemos no 
se hagan de forma asíncrona, es decir, en el mismo momento en 
que las realizamos, si nos que pueden ser realizada mas adelante.

sync: Con esta opción conseguimos que todas las modificaciones
que hagamos sean síncrona es decir, realizadas en el mismo 
momento en que sean realizadas.

---

### Post by andres2420 on 2009-09-15
Primero que nada...

**Hei Ku**

el mensaje original fue: [I]Andres, por favor moderá tu tono y tu lenguaje. 
Simplemente te hicieron una apreciación sobre cómo quedaría, recomendandote que estarías desperdiciando espacio. 
Si lo vas a tomar mal, quizas necesites tomarte un poco mas de tiempo al responder, y asumir que la gente tiene buena intencion, y no critica de gusto.[/I]

Que critica hise?, capas que me di a entender mal pero **tiene toda la razon** el amigo EnriqueK en cuanto a los espacios y demas. Y yo tambien pienso lo mismo, no me gusta ni el tema de la particion primaria ni del mucho espacio que asi tendra el /.Cpas que quedo mal expresado **pero no critique a nadie**, todo lo contrario.

Puedo interpretar que al editar tu mensaje ahi si te tomaste el tiempo para moderar lo que dije eh interpretarlo...nunca critique a nadie y si se que la gente de aca tiene buenas intenciones. O acaso las comunicades se basan en no ayudar? al amigo gmunioz alguien le paga para ayudarme? no el loco lo hace porque le gusta...

Espero aclarar esto y si por el tema del lenguaje que veo los **** tenes razon loco, no te hagas drama.

**gmunioz**

Me saco el sombrero...ahi mismo le agregue al documento que hice con tu explicacion, le agregue los detalles del fstab **posta que muchas gracias amigo**.Lo pude solucionar tal cual como me dijieste salvo que lo hice desde el mismo live cd.

Simplemente inicie el live-cd monte la particion / y comense tal cual los pasos del segundo post con las modificasiones minimas por estar claro esta trabajando con una particion montado.En definitiva quedo asi:

```
sudo -i

Te logueas como root
```

```
mkdir /media/disk/media/hometemp

Creas un directorio de montaje temporal.
Lo que cambia de hacerlo desde el live-cd es que la particion / la monta en /media/disk y adentro de eso si esta el /
```

```
mount /dev/sda1 /media/disk/media/hometemp

Montas la partición en el directorio temporal que esta dentro del disk ubicado en media...
siempre recordando que estoy desde el cd no desde el propio sistema operativo
```

```
cd /media/disk/home

cp -ax . /media/hometemp

Esta linea es la única que sirve para clonar
presta atención al "." que sigue a -ax

Clonas tu directorio /home,
 que a su vez esta montado en /media/disk
```

```
cd /media/disk

mv /media/disk/home /media/disk/home.old

mkdir /media/disk/home

mount /dev/sda1 /media/disk/home

Renombras /home antiguo, montas el nuevo /home.
Nuevamente aclaro que este es el home de la particion no del propio live-cd.
```

```
vol_id --uuid /dev/sda1

copia la salida

gedit media/disk/etc/fstab

Añade estas lineas al final del archivo

#/dev/sda1 
            
UUID=**aqui la salida de vol_id** /home ext4 defaults 0 2

Averiguas la UUID de la partición y editas el archivo /etc/fstab que esta dentro de /media/disk, para montar la partición al inicio
```

Ahora solo resta reiniciar,sacar el live-cd y listo.En lo particular hice tal cual lo descripto por gmunioz y me andubo sin dramas.Comprobe que todo estubiese bien, que todo me funcionara como antes...y despues hice tal cual esto:

```
sudo -i

rm /home.old

rm /media/hometemp

Claro está, ya no se trabajo sobre un disco montado por un live-cd por lo que directamente se trabaja sobre el /
```.

Bueno muchas gracias y ahora edito el titulo como solucionado.Gracias posta.Un abrazo

Andrés

---

### Post by Hei Ku on 2009-09-15
Por algo edite el mensaje original. Me tomo 10 minutos releerlo y entender el sentido que le querias dar. Tus signos de puntuacion (o la falta de) y el uso de mayusculas no ayudan, que fue lo que deje en el mensaje editado.

Me alegro que hayas solucionado el tema. gmunioz y enriquek son de los que mejores ayudas dan por aca.

---

### Post by andres2420 on 2009-09-15
Se nota posta que los pibes la tienen clara.Da gusto entrar a comunidades asi.

Por el tema de la ortografia, falta de puntos y demas, nunca me hice problema alguno porque no es de mi interes.

Nuevamente gracias.

---

### Post by gmunioz on 2009-09-15
Andrés:

¡¡Gracias por la expresión pibes!! 

En algun rincón aún algo debe quedar. 8)

---

### Post by andres2420 on 2009-09-15
JAJAJJAJ, tengo 21...pero el dia que tenga 95 tambien voy a seguir siendo uno.Un Abrazo loco.

---

### Post by josecuervo86 on 2009-09-15
> **Hei Ku said:**
> Me alegro que hayas solucionado el tema. gmunioz y enriquek son de los que mejores ayudas dan por aca.

Me cuelgo de este comentario, porque la verdad la respuestas que da gmunioz son excelentes! Realmente se luce con cada post y eso merece, al menos, reconocimiento. Saludos!

---

