---
title: "Quota por directorios"
date: 2009-02-02
forum: Software
---

### Post by FlyerDie on 2009-02-02
Buenas, despues de mucho tiempo vuelvo a pegarme una vueltita por aca :)

Resulta que con unos amigos tenemos un seedbox, y por como es la configuracion que tenemos con el Utorrent (una instancia por cada uno de nosotros), todo lo que se baja es atravez de una misma cuenta...pero en diferentes carpetas.

Ahora bien, para que sea justo para todos, quiero que cada carpeta tenga un limite de quota.

Todo lo que encontre (y tuvimos puesto) es en relacion a /home de cada cuenta que tengamos creada, pero solo tenemos una cuenta global (no necesitamos usuarios).

Como puedo poner limites como por ejemplo:

/home/flyerdie/download1 ------> 30gb quota
/home/flyerdie/download2 ------> 20gb quota
/home/flyerdie/download3 ------> 50gb quota

(tengan en cuenta que es dentro del /home de un solo user)


Gracias mil gente!!!:popcorn:

---

### Post by gmunioz on 2009-02-04
Hola fly....:

Respecto de asignar cuotas de disco, se debe arbitrar antes de instalar el operativo, en general se usa en servidores y requiere de varias medidas a tomar previas a la instalación, el procedimiento es en línes generales:

  Durante la instalación, debes crear una partición dedicada para /var y otra para /home.

  Debes instalar quota quotatool

  Sudo apt-get install quota quotatool

  Debes iniciar Ubuntu en runlevel 1, modo de recuperación.

  Debes activar el soporte para cuotas en las particiones mencionadas, agregando en el fichero /etc/fstab
  los parámetros usrquota y grpquota a las líneas que definen la configuración de las particiones /var y /home:

      ........	/var	reiserfs	defaults,usrquota,grpquota	1 2
      ........ 	/home	reiserfs	defaults,usrquota,grpquota	1 2

  Debes remontar las particiones para que surtan efecto los cambios:

      mount -o remount /var
      mount -o remount /home

  Debes crear los ficheros aquota.user, aquota.group, quota.user y quota.group, 
   
  Los cuales se utilizarán almacenar la información y estado de las cuotas en cada partición.

      cd /var
      touch aquota.user aquota.group quota.user quota.group
      cd /home
      touch aquota.user aquota.group quota.user quota.group

   
  Debes ejecutar:

      quotacheck -avug

      
  Debes activar las cuotas de disco recién configuradas ejecutando:

      quotaon /var
      quotaon /home

   Reinicia a fin de aplicar cuota de disco a algunos usuarios.

      
Edquota.

Cada columna mostrada por edquota significa:

Blocks: Bloques. Corresponde a la cantidad de bloques de 1 Kb que está utilizando el usuario.

Inodes: Inodos. Corresponde al número de ficheros que está utilizando el usuario. .

Soft: Limite de gracia. 

Hard: Limite absoluto. 

Para asignar cuotas de disco a cualquier usuario o grupo utiliza edquota  nombre del usuario:

edquota usuario

Lo anterior deberá devolver algo como lo siguiente a través de vi u otro editor de texto simple:

Disk quotas for user usuario (uid 501):
Filesystem    blocks     soft     hard   inodes     soft     hard
/dev/hda7          0        0        0        0        0        0
/dev/hda5         24        0        0       10        0        0

Cuota absoluta.

Suponiendo que se quiere asignar una cuota de disco de 6 MB para el usuario «usuario» en en /dev/hda7 y /dev/hda5, se utilizaría lo siguiente:

Disk quotas for user usuario (uid 501):
Filesystem    blocks     soft     hard   inodes     soft     hard
/dev/hda7          0        0     6144        0        0        0
/dev/hda5         24        0     6144       10        0        0

Saludos.
Gabriel.
**Solo doy soporte para Ubuntu - 22 Mad Jaunty User**

---

### Post by Hei Ku on 2009-02-04
El tema es poder hacerlo por carpeta

---

### Post by FlyerDie on 2009-02-04
Exacto...es como dice Rei Ku lo que quiero :)

No me interesa dar quota por usuario, sino dar quota a una carpeta...que no puedas copiar mas de N cantidad de Gb.

Como dije mas arriba, mi problema se encuentra en que todas las instancias de Utorrent corren bajo el mismo usuario de linux (dentro de la webUI tengo un usuario independiente para cada instancia, pero el usuario es generado para instancias nada mas) y cada instancia SI la tengo asignada a un directorio en particular, ej:

Utorrent1 -------> /home/flyerdie/download1
Utorrent2 -------> /home/flyerdie/download2
Utorrent3 -------> /home/flyerdie/download3

Ahora bien...yo quiero asignarle diferente quota a CADA carpeta y no quota global a /home ... se entiende?

Estaba pensando (divagando) en que si se podria hacer algo con mountpoints, pero en vez de a dispositivos que sean a carpetas ya existentes...eso es posible?? (ignorancia pura..acepto que me digan burro :P)
ya que de ser asi, podria hacer algo desde el fstab y asignarle quota asi..no?

Gracias!!

---

### Post by FlyerDie on 2009-02-05
Bueno genchi...por lo visto el tema de quota por diretorio en el ambiente linuxero es TABOO.
Rascando un poco mas sobre la herida encontre que mucha gente ha hecho esta consulta en diferentes foros y siempre obtuvieron la misma respuesta automatica, que utilice QUOTA y  que la asigne por usuario (como si no explicaran claramente que la asignacion de quota no la quieren hacer por usuario, sino por carpeta solamente). 
Y cuando vuelven a realizar esta aclaracion, el interrogante cae en el /dev/null.
Me refiero a este como tema taboo, ya que por lo visto desde hace mucho tiempo, mas precisamente desde M$ Windows 2000, ese sistema operativo posee quota manejable de la manera que sea siemdo ampliamente superior al arcaico y reducido manejo de quota que demuestra tener linux :(

Osea, en resumidas cuentas, para que en linux tengas quota lo modes hacerlo sobre dispositivos (mountpoints) y no sobre directorios especificos que no sean especificamente dispositivos.
y la asignacion de las quotas no son globales sobre ALGO, sino sobre QUIEN accede. Cosa que la verdad deja muchisimo que desear.

Estoy contestando no porque realmente haya encontrado una solucion, sino simplemente porque no la hay, al menos dentro del mundo linux.

Asi que lo que tuve que hacer, cosa que no queria era, tener que correr cada instancia desde su propio usuario (que no queria llegar a usar usuarios!!) y ahi si tengo disposicion de quota sobre el /home para cada uno.

Ahora quisiera saber como evitar la tarea engorrosa de tener que ir entrando usuario por usuario a la X y levantar Utorrent?
Se puede levantar desde consola desde un solo usuario, pero que el proceso sea asignado a otro (asi los torrent que sean bajados bajo esa instancia esten relacionas a la quota).

Les dejo como es que figura el link del desktop que ejecuto dentro de cada usuario para que tengan una idea de que manera se ejecuta:
```
env WINEPREFIX="/home/USER/.wine" wine "C:\Program Files\uTorrent\uTorrent.exe"
```

Lo que he probado es:
```

**usuario1**@servidor:~$sudo -u **usuario2** wine "C:\Program Files\uTorrent\uTorrent.exe"
```

lo cual, luego de poner la pass me dice:

```
wine: /home/usuario1/.wine is not owned by you
``` ???

No se supone que -u me da la posibilidad de correr un proceso en nombre de otro usuario?

Otras de las veces (no recuerdo como recrearlo ya que hice muchas pruebas...) me entro como en loop y haciendo top veia multiples procesos **utorrent <defunct>**, que quedaban en estado zombie

tambien he probado:
```
sudo -u usuario2 wine /home/usuario2/.wine/drive_c/Program\ Files/utorrent/uTorrent.exe **>/dev/null 2>&1 &**
```

pero no pasa nada..

---

### Post by sebastianabate on 2009-02-07
> **FlyerDie said:**
> 
```

**usuario1**@servidor:~$sudo -u **usuario2** wine "C:\Program Files\uTorrent\uTorrent.exe"
```lo cual, luego de poner la pass me dice:

```
wine: /home/usuario1/.wine is not owned by you
``` ???

No se supone que -u me da la posibilidad de correr un proceso en nombre de otro usuario?



Probá con el modificador de sudo -H, es para cambiar el home al del usuario que definis con -u. Por defecto sudo usa las variables de entorno del usuario que lo está ejecutando, por eso te tira el error de premisos, porque usa el direcorio .wine que está en el home de usuario1 y no el del home de usuario2.

Otra opción que se me ocurre para hacer lo que necesitás sin necesidad de varios usuarios ni quotas es usar archivos montados como filesystems (con la opción loop); de esa forma podés tener un archivo de 20 GB montado en /home/flyerdie/download1 y uno de 50 GB montado en /home/flyerdie/download2, de esa forma cada directorio tiene asignado un espacio para ocupar. El problema con esto es que aunque en el directorio /home/flyerdie/download1 tengas solamente un archivo de 5 MB el archivo que contiene el filesystem va a coupar los 20 GB que le asignaste, pero si tenés el espacio en disco disponible no habría drama.

---

### Post by faktorqm on 2009-02-09
Lo unico que se me ocurre asi como para salir del paso, es que hagas un script que pregunte cuando espacio ocupa una carpeta y que cuando ese espacio supere tal cantidad cambie los permisos para que no se pueda escribir mas en esa carpeta. Lo tiras al cron cada 5 minutos y listo.
En el mismo script le pones que si el espacio ocupado es menor le asigne los permisos de escritura de vuelta, cosa que cuando tu amigo/a se pase los datos a su compu o simplemente borre lo que no le sirvio a los 5 min (como maximo) ya empieza a andar todo normalmente.
Salu2!

---

### Post by ToniWiki on 2009-03-25
Creo que la mejor forma de hacer lo que quereis es la siguiente:

- Crear un grupo que utilizaremos solamente para controlar la cuota (tamaño) de un directorio.

- Establecer como grupo propietario del directorio cuyo tamaño queremos controlar, el anteriormente creado. Y lo más importante: activar el bit setgid para esa carpeta.

- Hecho esto establecer el tamaño máximo asignando la cuota al grupo creado. Todo ello con la gestión normal de cuotas.


Espero sirva de ayuda.

Un saludo

---

