---
title: "Hardy como Backup y Virtualizacion"
date: 2009-10-13
forum: Software
---

### Post by sebabollatti on 2009-10-13
Hola a todos!
Les cuento que acabo de instalar Ubuntu 8.04 version 64 en un AMD 64 y mi intencion es utilizar este servidor como servidor de backup y con VMWare Server para trabajar con 4 VM (hay tutoriales en la web). ....y si me convencen   ....un gestor de email equivalente a Ms Exchange.
El esquema de red que este server estaria inmerso seria bajo un dominio "Tal" de un Win 2003 Standard funcionando con Active Directory mas Microsoft
 ISA Server haciendo de firewall y filtro de web. Todas las terminales tienen Win XP.
 
"La pregunta del millon":
¿como?      ¿.......que?                    ...si!!              ¡¿¡¿¡¿COMO!?!?!?
 
Encontre en la web muchisimos tutoriales muy bien explicados sobre muchisimas cosas, en español y en ingles.  Pero ninguno en como acceder a una red con dominio de Windows y que programa instalo y uso para crear todas las tareas de backup de las terminales y del servidor primario (Win 2003).
 
La instalacion actual del Hardy no tiene instalado ningun complemento y me ofrezco a reinstalarlo si esto lo amerita.
 
Seba
PD: ¿Vale la pena instalar algun escritorio como GNOME o otro en el Hardy?

---

### Post by guillermolisi on 2009-10-13
> **sebabollatti said:**
> Hola a todos!
Les cuento que acabo de instalar Ubuntu 8.04 version 64 en un AMD 64 y mi intencion es utilizar este servidor como servidor de backup y con VMWare Server para trabajar con 4 VM (hay tutoriales en la web). ....y si me convencen   ....un gestor de email equivalente a Ms Exchange.
El esquema de red que este server estaria inmerso seria bajo un dominio "Tal" de un Win 2003 Standard funcionando con Active Directory mas Microsoft
 ISA Server haciendo de firewall y filtro de web. Todas las terminales tienen Win XP.
 
"La pregunta del millon":
¿como?      ¿.......que?                    ...si!!              ¡¿¡¿¡¿COMO!?!?!?
 
Encontre en la web muchisimos tutoriales muy bien explicados sobre muchisimas cosas, en español y en ingles.  Pero ninguno en como acceder a una red con dominio de Windows y que programa instalo y uso para crear todas las tareas de backup de las terminales y del servidor primario (Win 2003).
 
La instalacion actual del Hardy no tiene instalado ningun complemento y me ofrezco a reinstalarlo si esto lo amerita.
 
Seba
PD: ¿Vale la pena instalar algun escritorio como GNOME o otro en el Hardy?
Disculpa pero ese server con HH sera de backup de algun otro server, como parte de un esquema de alta disponibilidad ?

Sera el encargado de recibir copias de resguardo de la informacion almacenada en otras maquinas ?
Si la respuesta a esta pregunta es "Si", mi recomendacion pasa por Bacula, pero hay muchos mas productos disponibles como Amanda, rSync, etc., etc.

Para que o por que ese servidor deberia estar dentro del dominio del Windows Server ?

Lo queres como Backup Domain Controller para que valide login de los usuarios y maquinas al dominio definido por el Windows server ?
Si la respuesta es "Si", entonces no necesitas otra cosa que Samba actuando como controlador de dominio. Si la queres mas sofisticada y dificil, LDAP (que es lo que MS tomo como base para inventar AD).

PD: Y .. depende de cada caso. Podria ser practico si eventualmente tenes que navegar en busca de algun tip, dato, informacion especifica para ese server y descargar archivos que no estan en los repos de Ubuntu. Una solucion de compromiso seria tener un escritorio grafico listo para que sea iniciado cuando se lo necesite estando el resto del tiempo parado. Ahora, si el server se encargara de virtualizar maquinas, seran mas importantes estas que el propio host a los efectos de administracion, con lo cual contar con un escritorio grafico ya pierde bastante sentido.

---

### Post by sebabollatti on 2009-10-13
Hola Guillermo y gracias por la pronta respuesta
 
[I]Disculpa pero ese server con HH sera de backup de algun otro server, como parte de un esquema de alta disponibilidad ?
[/I]
Si. La finalidad es tener un server de backup y no un server de redundancia (en un principio se penso en esto) pero el costo involucrado en soft ya que tenia que ir por el lado de Ms implicaba un costo alto que una Pyme "Argentina" en epoca de crisis no puede afrontar. Actualmente hago lo imposible para que me compren 4 licencias mas de Win XP y ni hablar si me miran el Server con sus U$D1000 del Win2003 mas otros tantos del Ms ISA Server.
 
[I]Sera el encargado de recibir copias de resguardo de la informacion almacenada en otras maquinas ?
Si la respuesta a esta pregunta es "Si", mi recomendacion pasa por Bacula, pero hay muchos mas productos disponibles como Amanda, rSync, etc., etc[/I]
 
Realmente en el Server actual un HP Proliant ML110 tengo corriendo el Cobian Backup que copia de las terminales y del mismo server los archivos de respaldo. Si Bacula, Amanda, rSync o cualquiera de estos da una solucion parecida al Cobian...  me inclino por uno de estos y avanzo tranquilo.
 
*Para que o por que ese servidor deberia estar dentro del dominio del Windows Server ?*
[I]Lo queres como Backup Domain Controller para que valide login de los usuarios y maquinas al dominio definido por el Windows server ?
Si la respuesta es "Si", entonces no necesitas otra cosa que Samba actuando como controlador de dominio. Si la queres mas sofisticada y dificil, LDAP (que es lo que MS tomo como base para inventar AD).[/I]

La necesidad de que el HH sea parte del dominio es para que los usuarios de las terminales puedan acceder al backup en cualquier momento ante una rotura de "SiAp" (me tiene bastante pel......, rompe las bases de datos mdb cada 2 x 3 seg) y por otro lado para tener la info en otro lugar fisico alejado del server primario.
Lamentablemente en las consultas de movimientos de paquetes que se puede hacer con el Ms ISA Server se puede ver que gran parte del trafico es SecureNAT y LDAP asi que no hay muchas opciones. ¿Samba es el camino adecuado?
 
...en este momento el server con HH no tiene conexion a Internet y solo tiene el CD de instalacion de 64bits que baje de la pagina oficial.
Este server no va a tener un monitor conectado sino que va a estar encerrado en un lugar blindado y anti-incendios para soportar cualquier contingencia dado el caso. ¿como administro el server remotamente si no tengo un entorno grafico?
 
¿Hay algun tutorial para que no sea de mucha molestia responder estas preguntas quizas un tanto obvias para uds?
 
Seba

---

### Post by z37a on 2009-10-14
> **sebabollatti said:**
>  
...en este momento el server con HH no tiene conexion a Internet y solo tiene el CD de instalacion de 64bits que baje de la pagina oficial.
Este server no va a tener un monitor conectado sino que va a estar encerrado en un lugar blindado y anti-incendios para soportar cualquier contingencia dado el caso. ¿como administro el server remotamente si no tengo un entorno grafico?

Podes hacerlo tranquilamente por ssh utilizando putty desde un Windows, otra herramienta que te recomiendo es el pscp, que te permite hacer scp(copia de archivos via ssh) desde windows a un linux. Ojo esto teniendo en cuenta que tengas buen dominio sobre la bash, pero es la mejor opcion tambien ya que las tranferencias viajan encriptadas y o consume grandes recursos.

---

### Post by guillermolisi on 2009-10-14
> **sebabollatti said:**
> Hola Guillermo y gracias por la pronta respuesta
 
*Para que o por que ese servidor deberia estar dentro del dominio del Windows Server ?*
[I]Lo queres como Backup Domain Controller para que valide login de los usuarios y maquinas al dominio definido por el Windows server ?
Si la respuesta es "Si", entonces no necesitas otra cosa que Samba actuando como controlador de dominio. Si la queres mas sofisticada y dificil, LDAP (que es lo que MS tomo como base para inventar AD).[/I]

La necesidad de que el HH sea parte del dominio es para que los usuarios de las terminales puedan acceder al backup en cualquier momento ante una rotura de "SiAp" (me tiene bastante pel......, rompe las bases de datos mdb cada 2 x 3 seg) y por otro lado para tener la info en otro lugar fisico alejado del server primario.
Lamentablemente en las consultas de movimientos de paquetes que se puede hacer con el Ms ISA Server se puede ver que gran parte del trafico es SecureNAT y LDAP asi que no hay muchas opciones. ¿Samba es el camino adecuado?
 
...en este momento el server con HH no tiene conexion a Internet y solo tiene el CD de instalacion de 64bits que baje de la pagina oficial.
Este server no va a tener un monitor conectado sino que va a estar encerrado en un lugar blindado y anti-incendios para soportar cualquier contingencia dado el caso. ¿como administro el server remotamente si no tengo un entorno grafico?
 
¿Hay algun tutorial para que no sea de mucha molestia responder estas preguntas quizas un tanto obvias para uds?
 
Seba
Para recuperar backups no hace falta que esa maquina forme parte de un dominio Windows. Tampoco hace falta Samba para ello.

Por otra parte, mi recomendacion es que alguien sea el administrador de esas copias y que no quede librada la operacion de recovery en el ambito de los usuarios.

Ese server deberia tener acceso controlado a Internet, detras del firewall de la red, para poder actualizar adecuadamente el sistema.

Lo que guardaria en ese lugar hiper seguro no es la maquina sino las copias de backup, o no van a usar medios removibles ? Seran copias solamente a disco ?

La administracion remota se pude lograr de varias formas: via un multiplexor KVM (Keyboard, Video, Mouse), via SSH, via Remote Desktop, via servidor dinamico X, via VNC, etc. Esto es independiente si tenes o no entorno grafico en ese server.

Tutoriales hay muchos, en varios idiomas, pero no creo que haya uno escrito a la medida de tus necesidades asi que la solucion la compones vos integrando partes.

Vos pregunta que cuando molestes te avisamos :)

---

### Post by juancarlospaco on 2009-10-14
Te diria que si no tenes otro Hardware para dividir y no meter tantas funciones en el mismo equipo fisico.

Tambien recorda que el lugar tiene que estar refrigerado adecuadamente, mas en Verano.

El servidor deberia poder bajar updates de internet, de forma segura, ajustar el UFW.
*(no se cual sera tu topologia y jerarquia de red, DMZ o no, etc.)*

Recordar que el SSH ES un entorno grafico tambien si lo sabes usar,
podes iniciar aplicaciones graficas de la maquina remota en la pc de admin local.

Yo usaria un Bacula, haciendo backup en varios HDD,
administracion por SSH con X-Redirect habilitado, y por si estas off-line...
mc, elinks2, smart-tool (estado de discos), acpi (estado temp), 
alien, traceroute, checkinstall, build-essentials.

Te diria que no te tires por armar RAID,
por que si no lo sabes manejar solo te va a traer dolor de cabeza.

El tema del Samba como controlador de dominio armalo en otro hardware *(si podes)*,
y virtualizado *(si podes)*, 
cosa que tenes Snapshots, Backup, VMs redundantes, etc.

---

### Post by sebabollatti on 2009-10-29
[SIZE=2]Vamos a presionar el boton de “reset” y volver a empezar[/SIZE]
[SIZE=2] [/SIZE]
[SIZE=2]Tengo que:[/SIZE]
[SIZE=2]Tener un Server de virtualizacion empezando con 4 VM y quizas llegue a 6 u 8 y a la vez hacer backup en horarios donde no existe la carga de red ni el uso de las VM (por la noche).[/SIZE]
[SIZE=2]El equipo es un Athlon 64 de 8gb de ram, 2 discos, 1 de 160 y el otro de 500.[/SIZE]
[SIZE=2] [/SIZE]
[SIZE=2]-Pueden recomendarme todo lo que quieran ya que no tengo problemas en volver a instalar el 8.04 LTS -[/SIZE]
[SIZE=2] [/SIZE]
[SIZE=2]Entonces:[/SIZE]
[SIZE=2]Me bajé el instalador de 8.04 LTS para AMD 64 y lo instalé particionando según:[/SIZE]
[SIZE=2]Disco 160[/SIZE]
[SIZE=2]140 gb de partición /ext primaria[/SIZE]
[SIZE=2]20 gb de /swap[/SIZE]
[SIZE=2] [/SIZE]
[SIZE=2]Disco 500[/SIZE]
[SIZE=2]200 gb de partición /ext[/SIZE]
[SIZE=2]300 gb de partición FAT32[/SIZE]
[SIZE=2] [/SIZE]
[SIZE=2]En la pantalla de instalación del Hardy que dice “Configurando apt” empezo con “Analizando la replica” y ahí se quedó. Ya hace como 2 horas que esta ahí y ni ni y ni nada.[/SIZE]
[SIZE=2] [/SIZE]
[SIZE=2]Le habia conectado antes de iniciar la instalacion el cable de red y detecto la configuración de red por dhcp sin problemas, supongo que lo de “Analizando la replica” tiene que ver con algo de Internet (de ultima vuelvo a instalar).[/SIZE]
[SIZE=2] [/SIZE]
[SIZE=2]Si en las proximas 2 horas no avanza reseteo y vuelvo a instalar y les sigo contando asi me ayudan con la linea de comando ya que no [/SIZE][SIZE=2]tiene desktop el 8.04 LTS o hay que instalar el paquete. Ahh  ya baje y grabe el VMware Server 2 para Linux AMD64 [/SIZE]
[SIZE=2]Seba[/SIZE]

---

### Post by sebabollatti on 2009-10-30
Al fin y al cabo instale de nuevo el Hardy
 
...como siempre con su linea de comando y yo con un DVD con la instalacion de VMware Serve 2 queriendolo instalarlo en este sistema operativo.
 
Bien, a esto: no tengo instalado el desktop, tampoco lo necesito porque come recursos asi que con la linea de comando es la solucion ideal.
 
Intente montar o hacer un "cd" a la lectora de DVD pero no tengo la mas remotisima idea de como acceder a esta para poder ejecutar la instalacion del VMware Server 2 (ayuda en esto por favor)
 
Bue
El mejor de los agradecimientos para los que me den una mano
Seba

---

### Post by guillermolisi on 2009-10-30
> **sebabollatti said:**
> Al fin y al cabo instale de nuevo el Hardy
 
...como siempre con su linea de comando y yo con un DVD con la instalacion de VMware Serve 2 queriendolo instalarlo en este sistema operativo.
 
Bien, a esto: no tengo instalado el desktop, tampoco lo necesito porque come recursos asi que con la linea de comando es la solucion ideal.
 
Intente montar o hacer un "cd" a la lectora de DVD pero no tengo la mas remotisima idea de como acceder a esta para poder ejecutar la instalacion del VMware Server 2 (ayuda en esto por favor)
 
Bue
El mejor de los agradecimientos para los que me den una mano
Seba
Para estos casos y considerando que estas usando VMware 2, mi mejor consejo pasa por administrar esa VM via interface web desde una maquina cualquiera de la misma red.
Asi no tenes que ni instalar escritorio grafico en el server ni lidiar con los comandos nativos de VMware para estos menesteres.

Fijate como es la configuracion de hardware de la VM, particularmente la referida a la unidad optica. Una vez verificado esto, inicias/conectas la VM en la consola de administracion web y en la linea de comando de esa maquina virtual emitis el mount corrspondiente para poder acceder al DVD.

Confirma si lo que queres hacer es acceder para lectura o iniciar la VM desde el DVD.

Si necesitas mas detalles, avisa.

---

