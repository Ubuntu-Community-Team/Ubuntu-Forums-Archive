---
title: "preguntas sobre usuarios, permisos y montar comparticiones SAMBA"
date: 2010-12-20
forum: Software
---

### Post by granjero on 2010-12-20
buenas...

estoy montando un server ubuntu 10.04 para compartir archivos.

como hay maquinas con win y ubuntu SAMBA me pareció la opción a utilizar.


armé un árbol de carpetas

    COMUN
    DTO-ACADEMICO
    DTO-TECNICO
    DTO-ALUMNOS
    TESORERIA

Creé en el server los grupos DTO-ACADEMICO, DTO-TECNICO, DTO-ALUMNOS, TESORERIA

Creé en el server todos todos los usuarios.

A los usuarios los hice pertenecer cada uno a al grupo que le corresponde. 

A cada usuario le di una clave samba con ```
smbpasswd -a usuariox
```

el smb.conf lo dejé así:

```

[global]
	workgroup = TODO
	server string = server
	dns proxy = No
	wins support = Yes
	usershare allow guests = Yes

[COMUN]
	path = /home/yo/COMPARTIDO/DATOS/COMUN
	valid users = @TODOS
	read list = @TODOS
	write list = @TODOS
	create mask = 0770
	directory mask = 0770

[DTO-ACADEMICO]
	path = /home/yo/COMPARTIDO/DATOS/DTO-ACADEMICO
	valid users = @DTO-ACADEMICO
	read list = @DTO-ACADEMICO
	write list = @DTO-ACADEMICO
	create mask = 0770
	directory mask = 0770

[DTO-ALUMNOS]
	path = /home/yo/COMPARTIDO/DATOS/DTO-ALUMNOS
	valid users = @DTO-ALUMNOS
	read list = @DTO-ALUMNOS
	write list = @DTO-ALUMNOS
	create mask = 0770
	directory mask = 0770

[DTO-TECNICO]
	path = /home/yo/COMPARTIDO/DATOS/DTO-TECNICO
	valid users = @DTO-TECNICO
	read list = @DTO-TECNICO
	write list = @DTO-TECNICO
	create mask = 0770
	directory mask = 0770

[TESORERIA]
	path = /home/yo/COMPARTIDO/DATOS/TESORERIA
	valid users = @TESORERIA
	read list = @TESORERIA
	write list = @TESORERIA
	create mask = 0770
	directory mask = 0770

```

Me aparece sin problemas en las máquinas tanto con ubuntu como con win las comparticiones. Puedo entrar y escribir con todos los usuarios.

Mi primer problema es que cuando user1 escribe algo en una carpeta a la cual tiene acceso el archivo queda guardado a su nombre y a su grupo (grupo=nombre)

yo quiero que cuando user1 escriba quede a su nombre, pero a nombre del grupo que le hice al cual pertenecen sus compañeros de área.

porque si no cuando user2 quiere escribir en la planilla que hizo user1 no lo deja.




El segundo tema es que quiero que en los escritorios de las pc con ubuntu aparezcan las comparticiones ya montadas.

pero no le encuentro la vuelta al fstab.

que me sugieren?

gracias de antemano.

granjero.
:D

---

### Post by gmunioz on 2010-12-20
Por defecto en Gnu/Linux, cuando se crea un usuario también se crea un grupo con ese usuario únicamente, entonces deberías a cada grupo nombre de usuario, agregarle los otros miembros que pueden interactuar con sus archivos, manteniendo su pertenencia al grupo de usuarios con permisos para acceder al recurso compartido.

Edita en cada ordenador cliente el archivo /etc/fstab para añadir una línea que defina cómo se montará esta unidad de red. 

//servidor/home/yo/COMPARTIDO/DATOS/loqueva /media/compartida smbfs ip=192.168.0.3, username=user, password=suclave, workgroup=loquesea, user, owner, auto 0 0

Cambia:

* servidor por el nombre de la máquina a la que se conectan

* /media/compartida por el nombre del directorio donde lo quieras montar al recurso

* la ip del servidor

* username, el usuario en samba

* password, la clave del usuario en samba

* loquesea por el nombre del grupo de trabajo

Ten la precaución de que el servidor este encendido un tiempo antes de los clientes
caso contrario cambia auto por noauto o los clientes no iniciaran.

---

### Post by granjero on 2010-12-21
muchas gracias grabriel por la respuesta!

ya he logrado montar. todavía me faltan hacer varias pruebas pero ya he dado un gran paso gracias a tu ayuda.

\\:D/

en estos días voy a seguir probando. y preguntando.

salud!

---

### Post by granjero on 2010-12-22
hola, acá vienen unas preguntas:

1.- ¿Hay forma para que la compartición en lugar de ser montada a nombre de un usuario sea montada a nombre de un grupo?

El tema es que en la misma pc van a trabajar varias personas pertenecientes al mismo grupo. Pero cada una va a tener una cuenta en esa pc con su correo configurado. Y si hago una linea del fstab para cada usuario, el escritorio termina con muchos iconos confundiendo al usuario.

Leyendo encontré que si cambio la opción "user" por "users" debería montar para los usuarios del grupo. Pero cuando me logueo como otro usuario del mismo grupo la compartición aparece montada en el escritorio, pero al intentar acceder me dice que no tengo privilegios suficientes, salvo que me loguee con el usuario que dice el fstab.

¿Cómo se puede hacer para que por ejemplo en el puesto de trabajo de tesorería se monte la carpeta de TESORERIA y no importa si inicio sesión con uno u otro usuario del grupo de los tesoreros y todos tengan acceso de escritura y lectura en los archivos de la carpeta...?


gracias de antemano.

salud!

---

### Post by gmunioz on 2010-12-22
Prueba cambiar por

smbfs ip=192.168.0.3 username=guest, password=,

La parte de la línea que dice:

smbfs ip=192.168.0.3, username=user, password=suclave,

---

### Post by granjero on 2010-12-22
Muchas gracias por responder gabriel , pero me da un error de permisos.

Igualmente te cuento que tuve una epifanía y solucioné el tema por otro lado.

Hice accesos directos yendo a Lugares > Conectar con el servidor...

```
Tipo de servicio: Compartido por Windows
Servidor: NombredelServidor
Compartido: NombredelaCompartición
Carpeta: Vacío
Nombre de Usuario: User
Nombre del Dominio: Vacío
Tilde en agregar marcador
Nombre del Marcador: NombredelaCompartición
```

Cuando "loguié" por primera vez le puse que recuerde para siempre la contraseña y listo el pollo pelada la gallina. En Lugares queda el acceso y con un simple click me abre la compartición samba sin tener que meter mano en el fstab.

Eso en mi caso esto cumple la misma función que lo que quería hacer antes.


Ahora me surge otra pregunta.

¿Es posible acceder al servidor samba estando fuera de la red interna?

o sea desde la internet.

:-k

salud y gracias por responder!

---

### Post by gmunioz on 2010-12-22
Sin dudas: El protocolo SSH es la aplicación que te permite conectarte en forma remota para realizar tareas administrativas dentro de un servidor.

Aqui uno de los manuales completitos:

[http://www2.linuxparatodos.net/web/comunidad/base-de-conocimiento/-/wiki/Base%20de%20Conocimiento/Secure+Shell+(SSH](http://www2.linuxparatodos.net/web/comunidad/base-de-conocimiento/-/wiki/Base%20de%20Conocimiento/Secure+Shell+(SSH))

---

### Post by granjero on 2010-12-22
ja parece un chat esto ;)

te cuento que para realizar tareas administrativas uso mucho ssh, cuando lo descubrí me encantó!

yo aprendí con esta guía:

[http://tuxpepino.wordpress.com/2007/05/11/ssh-el-dios-de-la-administracion-remota/](http://tuxpepino.wordpress.com/2007/05/11/ssh-el-dios-de-la-administracion-remota/)

el link que pasaste me dice que no tengo permisos =;

mi pregunta era si se pueden acceder a las comparticiones samba estando fuera de la red interna. para laburar un fin de semana o si en algún momento tengo que unir dos sedes o algo así!

salud!

---

### Post by gmunioz on 2010-12-22
No administro ningún sistema. pero por lo que se, que es bastante poco, si todo esta funcionando o lo inicias mediante ssh no tendrías que tener ningún problema para acceder a los recursos compartidos en red sean samba, o nfs, ¡eres el administrador!

En la págima cuando da error, pulsa a la derecha inicio

---

### Post by biale on 2010-12-22
"tesoreria"

Lo que vale para acceder a un servidor es tener "una cuenta", un usuario en el servidor. Esa cuenta es independiente de la que se tenga en la estación de trabajo. Podría ser "tesoreria", etc

Incluso hay archivos para configurar la correlacion de cuentas y claves en la estacion de trabajo. Pero en general es mas facil montar en forma dinámica que via fstab...

---

### Post by granjero on 2010-12-30
nueva consulta concerniente a permisos.

Estuve leyendo sobre el permiso STICKY

Por lo que entendí este permiso se usa para carpetas y una vez asignado todos los archivos de esa carpeta quedan "pegados" al dueño quien puede hacer lo que quiera con los archivos y los integrantes del grupo los pueden modificar pero no borrar.

Haciendo pruebas lo que me sucede es lo siguiente:

le doy permiso sticky a un directorio

```
chmod 1770 DIRECTORIO
```

Con una máquina con ubuntu 10.04 creo en ese directorio con un usuario que pertenece al grupo una hoja de cálculos.

todo bien. \\:D/

con otro usuario que también pertenece al grupo abro ese documento y si agrego cosas, todo ok.

pero si en ese archivo quiero borrar o modificar alguna celda que escribió el primer usuario, me tira un error al guardar.

tampoco otros usuarios que no sean el dueño pueden renombrar los archivos.

No encuentro una descripción bien clara y coherente sobre el permiso Sticky.

Yo quiero usar este permiso para que los archivos solamente puedan ser borrados por el dueño del mismo. Ya que no hay una papelera de reciclaje. Pero que los demás usuarios pertenecientes al grupo puedan modificarlo.

alguna idea o tuto o algo para leer?

salud!

---

### Post by gmunioz on 2010-12-30
Si el sticky bit está activo en un directorio, entonces un usuario sólo puede borrar archivos que son de su propiedad o para los que tiene permiso explícito de escritura, incluso cuando tiene habilitado el acceso de escritura al directorio. 
Esto está pensado para directorios que tienen permiso de escritura global, pero no es deseable permitir a cualquier usuario borrar los archivos que quiera.

---

### Post by granjero on 2011-01-05
gracias gabriel por la respuesta, ya entendí como funciona el bit sticky.

ahora otra pregunta sobre permisos.

cuando armé la compartición samba en las llaves de las "shares" puse por ejemplo

```

force group = SECRETARIA-GENERAL
create mask = 0770
directory mask = 0770
```


con eso logro que cuando alguien con los permisos suficientes escriba en las "shares" los archivos queden con permiso de escritura, lectura y ejecución tanto para los dueños de los archivos como para los que pertenecen al grupo.

mi problema surge cuando quiero que algún usuario escriba en esas "shares" desde fuera de la red local.

Desde otra locación con la opción de "Conectar con el Servidor..." que está en la pestaña lugares mediante ssh monto las comparticiones sin problemas. 

Pero el problema que me surge es que cuando alguien escribe de esa manera al grupo sólo le da permisos de lectura y no de escritura. 

Y necesito que el grupo tenga permisos de escritura también. 

No se por donde encarar el tema.

Desde ya muchas gracias por la buena onda!

Salud!

---

### Post by biale on 2011-01-06
La "umask" a nivel del login al servidor?  (Por decir algo, no se si serviría)

---

### Post by granjero on 2011-01-07
no se que es la "umask" pero ya me pongo a investigar.


muchas gracias!

---

### Post by granjero on 2011-01-18
estuve leyendo sobre el umask

el tema es que no teermino de entender como usarlo.

si como root escribo umask 0007

todos los usuarios deberían escribir con estos permisos

mask 0007   >   rwx rwx ---   

pero sin embargo cuando escriben por ssh escriben con estos permisos

-rw-r--r--

no se por que.

ya modifique el archivo /etc/profile a 0007 y sigo sin poder escribir con permisos de lectura para el grupo

alguna idea?

gracias!

---

### Post by biale on 2011-01-18
Hice una pequeña prueba. Monté un arbol via ssh (sftp) bajo nautilus. Y desde alli se pueden abrir dos consolas distintas, una "local" y la otra "remota". Ambas operan con usuarios y mascaras independientes. O sea que vas a tener que analizar como utilizas ssh...

Una posibilidad distinta que pienso ahora sería tunelear los ports de samba por ssh. No se si es viable, eficiente, etc.

Y ftp sobre ssh?

---

### Post by biale on 2011-01-18
Hice una pequeña prueba. Monté un arbol via ssh (sftp) bajo nautilus. Y desde alli se pueden abrir dos consolas distintas, una "local" y la otra "remota". Ambas operan con usuarios y mascaras independientes. O sea que vas a tener que analizar como utilizas ssh...

Una posibilidad distinta que pienso ahora sería tunelear los ports de samba por ssh. No se si es viable, eficiente, etc.

Y ftp sobre ssh?

---

### Post by biale on 2011-01-18
Hice una pequeña prueba. Monté un arbol via ssh (sftp) bajo nautilus. Y desde alli se pueden abrir dos consolas distintas, una "local" y la otra "remota". Ambas operan con usuarios y mascaras independientes. O sea que vas a tener que analizar como utilizas ssh...

Una posibilidad distinta que pienso ahora sería tunelear los ports de samba por ssh. No se si es viable, eficiente, etc.

Y ftp sobre ssh?

---

### Post by biale on 2011-01-18
Hice una pequeña prueba. Monté un arbol via ssh (sftp) bajo nautilus. Y desde alli se pueden abrir dos consolas distintas, una "local" y la otra "remota". Ambas operan con usuarios y mascaras independientes. O sea que vas a tener que analizar como utilizas ssh...

Una posibilidad distinta que pienso ahora sería tunelear los ports de samba por ssh. No se si es viable, eficiente, etc.

Y ftp sobre ssh?

---

### Post by guillermolisi on 2011-01-18
hoy estuvimos charlando brevemente sobre el tema con Granjero en IRC (brevemente porque yo estaba hasta las manos de cosas para hacer y me pedian resolver) y me quedo dando vueltas el tema de que cada entorno determina ciertas condiciones operativas.

Digo esto porque vi que en Samba se puede establecer con que mascara de permisos se crearan los archivos, tambien se pueden definir a nivel de perfil de usuario y lo equivalente para accesos por otras vias, tales como ssh (con o sin pam), FTP, etc.

A efectos de lograr literatura, solo en Google encontre mucho material con (por ejemplo) "linux global system umask" como palabras claves.

---

### Post by granjero on 2011-01-19
Toda la parte que es la red local que la manejo con samba no me genera ningún inconveniente.
Dejo una de las llaves de la compartición samba.

```
[Prensa & Relaciones Institucionales]
	path = /home/granjero/SERVER/prensa-relaciones
        valid users = @prensa
        read list = @prensa
        write list = @prensa
	create mask = 0770
        directory mask = 0770
	force group = prensa

```

Ahí lo que hice fue hacer que los usuarios vá&#314;idos para esta compartición sean los que pertenecen al grupo prensa, idem con los que pueden leer y escribir.
con create mask = 0770 todo lo que se escribe por samba tiene permisos de ejecución, lectura y escritura para el user y el grupo.
y con force group = prensa hago que aunque el grupo principal del que escribe no sea prensa, quede como prensa.

El tema es que hay unas computadoras que están fuera de la red local.

Primero pensé que una VPN era la solución pero me encontré que no era tan fácil de implementar como pensaba.

Después me acordé que nautilus permite hacer una conexión por ssh.

Hoy cuando llegue al laburo voy a sentarme frente a las computadoras que están fuera de la red local y voy a hacer pruebas.

Si cambio el umask en /etc/profile de las pcs remotas que pasará?

salud!

---

### Post by granjero on 2011-01-19
Toda la parte que es la red local que la manejo con samba no me genera ningún inconveniente.
Dejo una de las llaves de la compartición samba.

```
[Prensa & Relaciones Institucionales]
	path = /home/granjero/SERVER/prensa-relaciones
        valid users = @prensa
        read list = @prensa
        write list = @prensa
	create mask = 0770
        directory mask = 0770
	force group = prensa

```

Ahí lo que hice fue hacer que los usuarios vá&#314;idos para esta compartición sean los que pertenecen al grupo prensa, idem con los que pueden leer y escribir.
con create mask = 0770 todo lo que se escribe por samba tiene permisos de ejecución, lectura y escritura para el user y el grupo.
y con force group = prensa hago que aunque el grupo principal del que escribe no sea prensa, quede como prensa.

El tema es que hay unas computadoras que están fuera de la red local.

Primero pensé que una VPN era la solución pero me encontré que no era tan fácil de implementar como pensaba.

Después me acordé que nautilus permite hacer una conexión por ssh.

Hoy cuando llegue al laburo voy a sentarme frente a las computadoras que están fuera de la red local y voy a hacer pruebas.

Si cambio el umask en /etc/profile de las pcs remotas que pasará?

salud!

---

### Post by granjero on 2011-01-19
modifiqué el archivo .profile que está en el home de los users de las pcs remotas y le descomenté donde dice umask 022 y le cambie a umask 0007

ya escribo con permisos de escritura y lectura para user y grupos. 

pero debería escribir con permisos de escritura lectura y ejecución. no se por que no me da los de X pero ya me anda el asunto!

salud!

---

### Post by biale on 2011-01-20
Estaría "solved"

Fijate que a Linux no le gusta dar rapidamente los permisos de ejecución. Ej: creo un archivo vacio con umask 022 y queda con permisos 644.

A lo mejor conviene alguna pequeña aclaracion de como estas usando ssh, para alguien que lea este thread...

---

### Post by granjero on 2011-01-20
la forma en la uso ssh es la siguiente:

Voy a Lugares > Conectar con el servidor

Dejo imagen.

Eso abre un nautilus.

Y esa es la forma en la que uso las comparticiones.

Pero mi meta es lograr que usen samba de forma remota y no SSH.

Salud!

---

### Post by biale on 2011-01-20
> mi meta es lograr que usen samba de forma remota y no SSH

A esta altura habria que preguntarse "que tan remoto es el acceso".

Samba/smb sobre ssh existe. Solo googlea con “samba over ssh”. Hay que tener en cuenta los ports 445 y 139.

Contanos como te fué...

---

### Post by biale on 2011-01-20
> mi meta es lograr que usen samba de forma remota y no SSH

A esta altura habria que preguntarse "que tan remoto es el acceso".

Samba/smb sobre ssh existe. Solo googlea con “samba over ssh”. Hay que tener en cuenta los ports 445 y 139.

Contanos como te fué...

---

### Post by biale on 2011-01-20
> mi meta es lograr que usen samba de forma remota y no SSH

A esta altura habria que preguntarse "que tan remoto es el acceso".

Samba/smb sobre ssh existe. Solo googlea con “samba over ssh”. Hay que tener en cuenta los ports 445 y 139.

Contanos como te fué...

---

### Post by biale on 2011-01-20
> mi meta es lograr que usen samba de forma remota y no SSH

A esta altura habria que preguntarse "que tan remoto es el acceso".

Samba/smb sobre ssh existe. Solo googlea con “samba over ssh”. Hay que tener en cuenta los ports 445 y 139.

Contanos como te fué...

---

### Post by biale on 2011-01-20
> mi meta es lograr que usen samba de forma remota y no SSH

A esta altura habria que preguntarse "que tan remoto es el acceso".

Samba/smb sobre ssh existe. Solo googlea con “samba over ssh”. Hay que tener en cuenta los ports 445 y 139.

Contanos como te fué...

---

### Post by biale on 2011-01-20
> mi meta es lograr que usen samba de forma remota y no SSH

A esta altura habria que preguntarse "que tan remoto es el acceso".

Samba/smb sobre ssh existe. Solo googlea con “samba over ssh”. Hay que tener en cuenta los ports 445 y 139.

Contanos como te fué...

---

### Post by biale on 2011-01-20
> mi meta es lograr que usen samba de forma remota y no SSH

A esta altura habria que preguntarse "que tan remoto es el acceso".

Samba/smb sobre ssh existe. Solo googlea con “samba over ssh”. Hay que tener en cuenta los ports 445 y 139.

Contanos como te fué...

---

### Post by granjero on 2011-01-24
Les cuento algo sucede: 

Si alguno de los usuarios que se conectan al server desde fuera de la red local al guardar desde openoffice en la carpeta que monta nautilus con ssh  guarda con permisos de rw para el user, r para grupo y r para otros.

pero si en vez de guardar en la carpeta montada por red guardan en la carpeta personal guardan con rw para user y grupo como yo indica la umask que setié.

si luego mueven o copian a la carpeta montada montada por ssh  conserva los permisos de rw.

voy a ver las opciones de openoffice a ver si encuentro algo.

luego les comento.

salud!

---

### Post by felipemuriel on 2012-04-11
Hola granjero, llevo más de 1 mes investigando y no he podido solucionar mi problema, tengo un VPS donde he instalado un server samba, estoy intentando de ingresar desde mi casa donde es fuera de la red del servidor, pero no me he podido conectar, sera que me puedes ayudar por favor con alguna luz de el porque no me puedo conectar, yo pongo desde mi windows xp \\ipservidor y me dice que no se puede conectar, tengo configurado el samba de esta manera 
# Samba config file created using SWAT 
# from 0.0.0.0 (0.0.0.0) 
# Date: 2012/04/11 10:26:54  
[global]     
workgroup = CASA     
netbios name = 72.xxx.xxx.xxx     
server string = Servidor Casa     
security = SHARE     
passdb backend = tdbsam     
wins support = Yes     
remote announce = 190.xxx.xxx.xxx     
cups options = raw  
[homes]     
comment = Home Directories     
path = /home/viasdecali     
read only = No  [printers]     
comment = All Printers     
path = /var/spool/samba     
printable = Yes     
browseable = No  [Carpetass]     
path = /home/viasdecali/carpetas

Como hiciste para poder conectarte a los archivos del samba fuera de tu red local?
Muchas gracias por la ayuda, la verdad estoy bastante desesperado ya no se que hacer

---

### Post by granjero on 2012-04-11
felipemuriel, ¿cómo te va? al final por samba en si nunca logre ingresar a los archivos desde fuera de la red local. Lo que hice fue hacer un acceso directo con ssh a las carpetas compartidas. 

tenes que tener en cuenta que tenés que abrir en el router que conecta a internet el puerto sobre el que esta corriendo ssh.

yo nunca uso el puerto 22 para ssh 
eso lo cambias en 
/etc/ssh/sshd_config 

```
# What ports, IPs and protocols we listen for
Port 1234
```

el tema surge cuando querés acceder desde win$ a la compartición samba. hay un soft libre que corre en win que permite conecciones ssh.

winscp creo que se llama.

salud!

---

### Post by granjero on 2012-04-12
hoy me acorde de mi idea original que es la posta creo. 

hacer una VPN y listo! 

salud!

---

