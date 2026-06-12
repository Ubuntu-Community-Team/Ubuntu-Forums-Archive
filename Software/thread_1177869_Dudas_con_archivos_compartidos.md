---
title: "Dudas con archivos compartidos"
date: 2009-06-03
forum: Software
---

### Post by totos69 on 2009-06-03
Hola. Como se imaginarán soy nuevo en el uso de Ubuntu, pero conozco mucho de Mac OS y Windows. Trabajo en una empresa chica con algunas computadoras en red, las cuales manejan archivos de oficina que residen físicamente en unas y otras. Más concretamente, hay una oficina de Pagos con sus respectivos archivos, los cuales aleatoriamente sos abiertos y modificados por la persona que está en la oficina de atención al cliente, y viceversa. Con este esquema, tenemos 4 computadoras.
El problema es que al abrir desde una computadora un archivo que reside en otra computadora, luego de modificarlo, el archivo en cuestión queda con un "candado" en la computadora que lo hospeda, impidiendo la apertura normal del mismo. Después de esto, el archivo sólo se puede abrir como "sólo lectura" o se puede hacer una copia del mismo.
Los permisos del archivo no los puedo modificar a menos que active el usuario Administrador (esto lo hago a través de un lanzador que he creado en el escritorio). Tengo entendido que el usuario Administrador queda "desactivado" por defecto como un principio básico de la seguridad de Ubuntu, y no se si existe una forma de trabajar de manera transparente como lo hacíamos con Windows, donde los archivos eran abiertos y modificados libremente por cualquier computadora.
Los archivos son .xls y .doc, pero sucede lo mismo con los nativos de OpenOffice.

He revisado la documentación de la página de Ubuntu, pero no consigo información que me ayude con este tema puntualmente (quizás no haya sabido buscar correctamente), pero la verdad es que necesitaría solucionar esto porque no nos está dejando trabajar de manera ágil como lo veníamos haciendo hasta ahora.

Desde ya muchísimas gracias por cualquier ayuda que me puedan brindar.

---

### Post by guillermolisi on 2009-06-03
> **totos69 said:**
> Hola. Como se imaginarán soy nuevo en el uso de Ubuntu, pero conozco mucho de Mac OS y Windows. Trabajo en una empresa chica con algunas computadoras en red, las cuales manejan archivos de oficina que residen físicamente en unas y otras. Más concretamente, hay una oficina de Pagos con sus respectivos archivos, los cuales aleatoriamente sos abiertos y modificados por la persona que está en la oficina de atención al cliente, y viceversa. Con este esquema, tenemos 4 computadoras.
El problema es que al abrir desde una computadora un archivo que reside en otra computadora, luego de modificarlo, el archivo en cuestión queda con un "candado" en la computadora que lo hospeda, impidiendo la apertura normal del mismo. Después de esto, el archivo sólo se puede abrir como "sólo lectura" o se puede hacer una copia del mismo.
Los permisos del archivo no los puedo modificar a menos que active el usuario Administrador (esto lo hago a través de un lanzador que he creado en el escritorio). Tengo entendido que el usuario Administrador queda "desactivado" por defecto como un principio básico de la seguridad de Ubuntu, y no se si existe una forma de trabajar de manera transparente como lo hacíamos con Windows, donde los archivos eran abiertos y modificados libremente por cualquier computadora.
Los archivos son .xls y .doc, pero sucede lo mismo con los nativos de OpenOffice.

He revisado la documentación de la página de Ubuntu, pero no consigo información que me ayude con este tema puntualmente (quizás no haya sabido buscar correctamente), pero la verdad es que necesitaría solucionar esto porque no nos está dejando trabajar de manera ágil como lo veníamos haciendo hasta ahora.

Desde ya muchísimas gracias por cualquier ayuda que me puedan brindar.
Algunas preguntas para confirmar como es el entorno de trabajo:
[LIST]
[*] Todas las PCs que mencionas corren Ubuntu ?
[*] Que version de Ubuntu tienen ? (Ubuntu, Xubuntu, Kubuntu, etc. 8.10, 904, 32 bits, 64bits)
[*] Usan Samba o NFS para compartir esos archivos ? (O como hacen para compartir esos archivos ?)
[*] Los usuarios poseen una cuenta personalizada que reside en una de las PCs de la red o esa cuenta tambien existe en todas las PCs ?
[/LIST]

---

### Post by juancarlospaco on 2009-06-03
**...Y si ponen una como Servidor de Archivos?**,
de paso podes asignarle tareas de backup, redundancia y mas disponibilidad, 
a futuro RAID o backup en Cloud Storage.

Simplemente esta mal configurado el Share.

*Que pasa si algun dia se muere el disco de esa PC ?*

---

### Post by totos69 on 2009-06-04
> **guillermolisi said:**
> Algunas preguntas para confirmar como es el entorno de trabajo:
[LIST]
[*] Todas las PCs que mencionas corren Ubuntu ?
[*] Que version de Ubuntu tienen ? (Ubuntu, Xubuntu, Kubuntu, etc. 8.10, 904, 32 bits, 64bits)
[*] Usan Samba o NFS para compartir esos archivos ? (O como hacen para compartir esos archivos ?)
[*] Los usuarios poseen una cuenta personalizada que reside en una de las PCs de la red o esa cuenta tambien existe en todas las PCs ?
[/LIST]


Hola Guillermo, gracias por contestar. 
Son todas PCs con Ubuntu 9.04 32 bits. Eventualmente habría PCs con Windows pero no por ahora. Los archivos se comparten mediante Samba, ya que si veo la ruta, la misma comienza con smb://. Además ese servicio está activado.
Yo instalé Ubuntu en cada máquina. Cada una tiene un nombre diferente (el que le di en la instalación). No se crearon nuevos usuarios ni grupos de usuarios.

> **juancarlospaco said:**
> **...Y si ponen una como Servidor de Archivos?**,
de paso podes asignarle tareas de backup, redundancia y mas disponibilidad, 
a futuro RAID o backup en Cloud Storage.

Simplemente esta mal configurado el Share.

*Que pasa si algun dia se muere el disco de esa PC ?*


Tenés toda la razón, cuando era todo Windows hacíamos backups automáticos en un Western Digital ethernet. Pero para ser sincero todavía estoy muy verde con Ubuntu como para configurar lo que vos me recomendás.

Pido disculpas a los moderadores por haber posteado en el foro principal y no el el subforo correspondiente.

Gracias a todos.

---

### Post by juancarlospaco on 2009-06-04
Por hay te conviene instalar uno de Servidor de archivos y lo manejas por Web,
con[ el Webmin,]("http://www.webmin.com/") fijate los links de abajo:
[B]
[Creando un Share Samba]("http://www.webmin.com/screenshots/chapter43/figure2.png")[/B]

**[Creando un Backup Automatico]("http://www.webmin.com/screenshots/chapterfs/figure2.png")**

Esta en Español tambien no te preocupes, es como un panel de control web,
no es muy dificil de instalar, tenes para configurar de todo desde ahi.


Para mi tendrias que chequear los permisos de los archivos.
Fijarte que el owner o Propietario no sea root.
Para probar asignale todos los permisos menos el de Ejecucion.
:p

---

### Post by totos69 on 2009-06-04
Gracias Juan Carlos!
Voy a chequear bien lo que me pasaste. Si hay más data, será bienvenida (no hay problemas con el inglés).
Luego contaré cual es el resultado.

---

### Post by guillermolisi on 2009-06-04
> **juancarlospaco said:**
> Por hay te conviene instalar uno de Servidor de archivos y lo manejas por Web,
con[ el Webmin,]("http://www.webmin.com/") fijate los links de abajo:
[B]
[Creando un Share Samba]("http://www.webmin.com/screenshots/chapter43/figure2.png")[/B]

**[Creando un Backup Automatico]("http://www.webmin.com/screenshots/chapterfs/figure2.png")**

Esta en Español tambien no te preocupes, es como un panel de control web,
no es muy dificil de instalar, tenes para configurar de todo desde ahi.


Para mi tendrias que chequear los permisos de los archivos.
Fijarte que el owner o Propietario no sea root.
Para probar asignale todos los permisos menos el de Ejecucion.
:p
Adicionalmente y si no se agregan maquinas con Windows, es mucho mas practico, facil y funcional utilizar NFS para hacer esta tarea de file sharing.

Totos69, podrias mostrarnos la salida, aunque sea parcial, del siguiente comando en una consola/terminal, en la maquina que contiene los archivos que se comparten ? ```
ls -al /directorio_donde_estan_los_archivos_compartidos
```

reemplazando "directorio_donde_estan_los_archivos_compartidos" por el path o camino que lleva a esos archivos (es como el viejo DIR en DOS).

---

### Post by juancarlospaco on 2009-06-04
La ventaja Tecnica de NFS sobre SMB 
es que este ultimo protocolo Windowsero 
llena la red de un spamm de paquetes IP, 
Broadcastea para todos lados a toda ahora todo el dia,
en una red pequeña no se nota..., 
pero en una mediana/grande puede dejarla con 
una performance reducida a la mitad o menos.

La unica salida es VLAN*ar* todo, *si es que existe esa palabra.*
Ademas NFS me parece mas seguro, 
sino ver lo que pasaba con los Shares y los Confiker*es*.

---

### Post by guillermolisi on 2009-06-05
> **juancarlospaco said:**
> La ventaja Tecnica de NFS sobre SMB 
es que este ultimo protocolo Windowsero 
llena la red de un spamm de paquetes IP, 
Broadcastea para todos lados a toda ahora todo el dia,
en una red pequeña no se nota..., 
pero en una mediana/grande puede dejarla con 
una performance reducida a la mitad o menos.

La unica salida es VLAN*ar* todo, *si es que existe esa palabra.*
Ademas NFS me parece mas seguro, 
sino ver lo que pasaba con los Shares y los Confiker*es*.
Todo esto sin mencionar que muchisimo mas facil de configurar que Samba ya que exportas lo que quieras compartir (editando un archivo de texto), le das los permisos que se necesiten dentro del ambito Linux y montas los que cada PC precise usar. La instalacion es una pavada-

Tiene otras limitaciones, que habria que evaluar, como el sistema de file locking cuando hay acceso concurrente para modificar archivos en el recurso compartido. Pero esto podria resolverse leyendo las diferencias en este sentido entre las distintas versiones de NFS disponibles e implementar la que mejor se adecue a los requerimientos funcionales.

---

### Post by biale on 2009-06-05
gente: ahora me entro la duda de como trabaja NFS.

El spam que mensiona juancarlospaco es el resultado del protocolo para browser de red. O sea lo que permite ver todo mas o menos rapidamente en "mis sitios de red". En principio ni siquiera son paquetes de Ip pero igual pesan mas de lo que parece. Afortunadamente los paquetes no pasan los routers

Novell ipx/spx hacía mas o menos lo mismo, pero apoyandose en las funciones del servidor dedicado para publicar sus servicios.

Ahora bien, para direccionar las máquinas basicamente habría tres métodos. Consultamos al master browser, consultamos al servidor dns o simplemente conocemos la dirección de Ip. Entonces (me) pregunto: como resuelve NFS?

Terminado el semi-offtopic, salvo mejor opcinión esta vez apostaría por SMB. Desgraciadamente es mucho mas probable que algún día caiga de visita una notebook W$ que una linux. Si mal no recuerdo hay que instalar cosas sobre un equipo W$ para que acceda por NFS. ¿Dije bolazo o sigue siendo así? Y si fuera así cuando a la semana reviente W$ como un sapo la culpa la tendrá...

Un saludo a todos.

---

### Post by juancarlospaco on 2009-06-05
Si cae un windows SSHfs y SCP con WinSCP.
Si cae un Mac se puede conectar lo mas bien.
:)

---

### Post by totos69 on 2009-06-16
Hola. Una vez más, gracias por sus respuestas.
Les cuento como terminó la cosa: vino gente que se dedica a la instalación y mantenimiento de servidores linux (lo cual vamos a implementar en breve) y me dieron una solución temporaria poniendo una de las máquinas con linux como server, alojando todos los archivos ahí dentro y permitiendo que las demás máquinas vean y modifiquen esos archivos autentificándose contra ese servidor.
Alguien había sugerido esto mismo en este thread.

Cuando le comenté a esta gente que yo venía generando un grupo de trabajo en donde estaba incluyendo las máquinas con linux, además de activar todos los permisos de compartición como usuario root en las carpetas en cuestión, me dijeron que ellos no lo sabían hacer desde la interfase de linux y que cuando lo habían intentado parecía no resultar...
Obviamente, lo hicieron todo desde comandos (algo que para mi todavía es imposible debido a mi poco conocimiento)
Todo se hizo a través de samba, porque hay algunos windows en la red y estos tienen que poder ver y ser vistos. ¿Por qué no linux en todos lados? simplemente porque Pro Tools no corre en linux, y eso es lo que hay en esas otras PCs. En 15 días, todas macs...

Proximamente se vendrá el servidor linux con discos en RAID y backup para recuperación de datos.

Una vez más, gracias a todos por su aporte.

---

