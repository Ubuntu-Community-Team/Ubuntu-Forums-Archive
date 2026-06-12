---
title: "Armar servidor para virtualizacion"
date: 2009-02-05
forum: Software
---

### Post by eamgoo on 2009-02-05
Quiero utilizar Ubuntu para virtualizar, es decir que sea el SO host para alojar varios windows dentro.
Me gustaria saber como se encara este proceso
Gracias

---

### Post by sergiom99 on 2009-02-06
Con qué queres armarlo?

Yo lo hice con VMWare Server (en un CentOS 5.2) porque accedo desde varias PCs a las Virtuales que corren en el VMWare Server.

Si vos queres usar varias VM en tu PC, podés usar VMWare workstation o Virtualbox. Este nunca lo usé, pero hay varios threads en el foro y en la lista de correos.

Por Vmware: [http://www.vmware.com/products/server/](http://www.vmware.com/products/server/)
Aca hay un thread, aunque nunca supimos si el OP lo pudo instalar o no:
[http://ubuntuforums.org/showthread.php?t=902083](http://ubuntuforums.org/showthread.php?t=902083)

---

### Post by BlackHero on 2009-02-06
Hola chamigo como va,
Bueno antes que nada te recomiendo ubuntu server, o simil debian server y que instales xen.
Para esto podes buscar info en ingles y las mejores info acerca de esto la vas a encontrar en [www.howtoforge.com](www.howtoforge.com) aca te paso el link de un lindo [howto]("http://www.howtoforge.com/creating-virtual-machines-for-xen-kvm-vmware-workstation-6-vmware-server-with-vmbuilder-on-ubuntu-8.10")


suerte y cualquier problema consulta saludos Raul

---

### Post by marianom on 2009-02-07
Xen es buena opción como indica el amigo BlackHero (hola BlackHero, tanto tiempo!!!). Mi recomendación personal también va por el lado de Qemu que incluso ahora tiene GUI (qemu-launcher) y da muy buena respuesta.

En conslusión: a nivel de soft de virtualización hay muchas opciones disponibles y todas están parejas a nivel de rendimiento, probalas y opta por la tuya. Si tenés dudas, traelas con confianza al foro donde te podremos orientar.

---

### Post by marianom on 2009-02-07
Me olvidé de las instrucciones... pasa que no es muy complicado.
Con Qemu creas primero los archivos donde se van a alojar los windows (se usa una intrucción qemu-img que si usas el qemu-launcher es tan simple como presionar "New" y ponerle un nombre a cada archivo). Debes elegir el tamaño de cada archivo donde quedará el SO (si usas el tipo de archivo qcow2 le ponés un tamaño máximo pero el archivo irá creciendo a medida que lo necesites, si haces una imagen raw tendrá el tamaño definitivo pero a favor tiene que podrás dimensionarla luego agregando otro archivo raw, con qcow no podes hacer eso).
Luego de tener las imagenes, le indicas al programa con cuanta memoria debe iniciar , que bootee de CD (por ejemplo si usas un CD para instalar) o podés montar una imagen ISO también y lo instalas en el disco que deseas indicandole opcionalmente si habrá carpetas samba para compartir con el host y cuestiones de hardware y red para setear como se conectarán a internet y entre ellas. 
[Aca]("http://www.saghul.net/blog/2007/06/03/howto-virtualizacion-en-linux-con-qemu-kqemu-qemu-launcher/") tenés un paso a paso.
Eso sí, el qemu-launcher es más fiero que yo cuando me levanto a la mañana (y me dura el resto del día). Estás advertido.

---

### Post by z37a on 2009-02-08
Actualmnente me encuentro armando un XEN-Cluster, un cluster de virtualizacion para que si se cae un equipo lebante el otro enseguida, no creo que esto sea esactamnete lo que buscas, pero en mi recorrido aprendiendo a armarlo aprendi y probe algunas cosas, lastima que en mi caso lo hago en SLES10 y no en ubuntu, pero probe algo similar en Ubuntu.

Si lo que queres es server enserio tenes que optar por XEN o KVM, a lo sumo VmWare Server(que es gratuito). Yo te diria que alguno de los primeros 2 es el indicado(para mi gusto). Ubuntu pro defecto trabaja con KVM, va prefiere KVM pero trambien trabaja en XEN. Si vos vas a utilizar una maquina dedicada a virtualizar lo ideal seria que instales ubuntu server 8.10, al instalarlo justamente llega un momenmtno donde te pregunta si deseas instalar las funciones de virtualizacion, igualmente en el menu de booteo del cd tenes una opcion que es para instalar lo MINIMO necesario para crear el servidor de virtualizacion!!! (Esto jamas lo utilize pero seguramente es ssolo KVM y no XEN). No se si con estas opciones se configura solo todo lo de red, siempre lo instale aparte, si no habria que seguir algun tuto de instalacion de KVM en Ubuntu.

Una vez que tenes el server mi otro consejo es que para crear las maquinas virtuales lo hagas desde otra pc, una terminal con linux(SI O SI deve ser linux!!!!) utilizando el virt-manager de redhat(que viene por defecto en ubuntu tambien), desde alli conectas via ssh al server y luego gestionas y creas todas las maquinas virtuales.

PD: Si tu intencion es clusterizar(que no seria nada loco hoy en dia!!!) ya tenes que recurrir a algo un poco mas complejo, pero te tiro algunos datos para que investigues si estas con ganas. Investigate un poco sobre DRBD(con esto no necesitarioas un iSCSI y trabajas con PC normales asi) luego OCFS y heartbeat, esto sirve para xen y kvm!! no tengo idea si para vmware funcara.

---

### Post by sergiom99 on 2009-02-08
Un aviso: En el último CentOS 5.2 que instalé para host de virtuales, tenía una opción para Virtualización. Lo marqué por las dudas y me instaló un kernel XEN en vez del SMP. Despues cuando traté de compilar el VMWare Server, me enteré de que no corre en este tipo de kernels. Asi que como recién estaba instalado sin configurar nada, hice mas rápido reinstalando de cero.
Suerte!

---

### Post by angelza on 2010-11-03
ola "sergiom99" me intereso eso que lograstes:
 
""Yo lo hice con VMWare Server (en un CentOS 5.2) porque accedo desde varias PCs a las Virtuales que corren en el VMWare Server.""
 
me gustaria que me ayudaras,me gustaria compartir un sistema operativo entre varias makinas en red.

---

### Post by guillermolisi on 2010-11-03
> **angelza said:**
>  
me gustaria que me ayudaras,me gustaria compartir un sistema operativo entre varias makinas en red.

Para lograr eso no hace falta virtualizar nada, solo configurar las maquinas y definir de que forma estas consumiran servicios del server con Ubuntu (o el SO que sea, mientras sea multiusuario).

Tendrias que ser algo mas explicito respecto de lo que queres lograr para que podamos orientarte mejor.

---

### Post by angelza on 2010-11-04
ok, te explico mejor para que asi puedas ayudarme, kiero levantar un servidor(estoy un poko indeciso en que es mejor linux o windows?),aparte kiero instalar un linux y un windows como O.S. invitado en el servidor y por ultimo que el servidor preste alas makinas que estan en red tanto como el sistema operativo como las aplicaciones.
 
espero averme explicado mejor para que me puedas ayudar. me gustaria contactarme mejor contigo, claro si no ay incovenientes
mi E-mail: [EMAIL="dark_boy_soad@hotmail.com"]dark_boy_soad@hotmail.com[/EMAIL]

---

### Post by hectorivand on 2010-11-04
> **angelza said:**
> ok, te explico mejor para que asi puedas ayudarme, kiero levantar un servidor(estoy un poko indeciso en que es mejor linux o windows?),aparte kiero instalar un linux y un windows como O.S. invitado en el servidor y por ultimo que el servidor preste alas makinas que estan en red tanto como el sistema operativo como las aplicaciones.
 
espero averme explicado mejor para que me puedas ayudar. me gustaria contactarme mejor contigo, claro si no ay incovenientes
mi E-mail: [EMAIL="dark_boy_soad@hotmail.com"]dark_boy_soad@hotmail.com[/EMAIL]

Perdón que me meta, ¿Qué queres hacer una especie de Streaming de aplicaciones pero incluyendo el sistema operativo?

Saludos
Nacho

---

### Post by Wiredfixer on 2010-11-04
Pues bueno, te pongo una lista de cosas que podrias hacer y nos dices cual es la correcta:

- Usar un Servidor Fisico para Alojar distinos SO Virtuales, para ahorrar en hardware.

- Usar un Servidor Fisico con Terminal Services y compartir aplicaciones a Thin Clients (Terminales Tontas)

- Usar Ambas Opciones, es decir, Virtualizar un Windows, Levantar un Servidor LTSP para gestionar Thin Clients y compartir aplicaciones desde el Windows via SeamlessRDP.

Cualquiera de los escenarios es factible, pero depende cuales sean tus necesidades reales.

---

### Post by angelza on 2010-11-04
pues la opcion que me parece mas adecuada es la tres, la del servidor LTSP,acabo de leer algo sobre ese tipo de servidores y eso es lo que necesito, me gustaria saber si me podrian ayudar???

---

### Post by Wiredfixer on 2010-11-04
Pues bueno, tengo poca experiencia con LTSP, es relativamente sencillo de instalar y solo requieres Edubuntu o el Alternate Iso de Ubuntu, el esquema seria asi:


 Servidor Ubuntu (DHCP, LTSP, PXE) ----- Terminales PXE Diskless

El Servidor Ubuntu, proporciona IP por DHCP, arranque por PXE y los servicios que decidas darle, basicamente, las aplicaciones corren desde el Servidor y el arranque es por red.

Para hacerlo un poco mas completo, puedes poner OTRO servidor con Windows 2003, Terminal Services habilitado y las aplicaciones que requieras "compartir" instaladas, si no tienes una red bajo Active Directory, vas a requerir dar los usuarios de alta en el servidor.

 Asi, el esquema quedaria:

 Ubuntu LTSP Server
 Windows 2003 App/Terminal Services   ---------  Equipos Thin Client.

Ya visto esto, te dejo unas paginas que te seran de mucha ayuda:

[https://help.ubuntu.com/community/UbuntuLTSP/LTSPQuickInstall](https://help.ubuntu.com/community/UbuntuLTSP/LTSPQuickInstall) <--- Instalacion rapida de LTSP.

[http://www.linuxtotal.com.mx/index.php?cont=info_otros_006](http://www.linuxtotal.com.mx/index.php?cont=info_otros_006) <--- Seamless RDP y aplicaciones Windows.

Ahora que, puedes explicar que es lo que quieres lograr?

Lo ocupas para un Cyber? para una Empresa? Manejas Directorio Activo? es Proyecto Nuevo? Ya tienes infraestructura de Red?

Estos factores deben ser tomados en cuenta.. puede que cambien las maneras de como trabajar...

---

### Post by angelza on 2010-11-05
ok muchas garcias por la ayuda, pues mira es un proyecto para mi uni,pero mis profes supieron de "virtualizacion de servidores" y lo de los "clientes ligeros"
 y pues mi proyecto es implementar los dos conceptos en uno solo, y pues estuve investigando:
 
necesito:
 
1.-tener todos los servidores en uno con la virtualizacion(servidor correo,ftp,http....ect).
 
2.-que en el servidor tenga 2 sistemas operativos y clientes ligeros puedan elegir con que S.O. kieren trabajar(en este caso 1 windows XP o 1 ubuntu).
 
3.- que los usuarios trabajan con las aplicaciones directamente del servidor.
 
 
pues esto seria lo que nessesito totalmente, en realidad no se si se pueda,pero pues me gustaria saberlo.

---

### Post by emiliano_raso on 2010-11-07
No tengo nada en contra de Ubuntu, pero si de servidores se trata, te recomiendo CentOS

---

### Post by guillermolisi on 2010-11-08
> **emiliano_raso said:**
> No tengo nada en contra de Ubuntu, pero si de servidores se trata, te recomiendo CentOS

Por lo menos explica por que, asi completas la idea, ayudas al interesado y no queda solo como un principio de flame.

---

### Post by granjero on 2010-11-08
hola, viste esto:

[http://www.ulteo.com/home/en/home](http://www.ulteo.com/home/en/home)

me parece que es lo que estás buscando.


salud!

---

### Post by angelza on 2010-11-08
ola dejando todo esto de la virtualizacion, alguen sabe como unir una makina con ubuntu a un dominio de windows server 2003????
 
ma ayudarian mucho

---

### Post by guillermolisi on 2010-11-08
> **angelza said:**
> ola dejando todo esto de la virtualizacion, alguen sabe como unir una makina con ubuntu a un dominio de windows server 2003????
 
ma ayudarian mucho

Abri otro hilo por ese tema ya que es inespecifico a este.

Y por favor, escribi las palabras como son asi no le complicas la vida a quienes recurren a traductores on line para entender que estamos hablando, quieran aportar o no a la solucion.

Gracias

---

### Post by Wiredfixer on 2010-11-09
Viendo los requerimientos, puede que sea algo caprichoso querer lograr todo en poco tiempo.

Mi recomendacion es que te metas de lleno en Software Libre, evita gasto de licencias y solo vas a requerir un servidor de Windows (2003 de Preferencia)

 Si lo que quieres es virtualizar, solo necesitaras un servidor fisico decente, de esto depende el performance de tus equipos Thin Client, asi como las instancias Virtuales que puedas manejar.

 Yo lo haria de la siguiente manera:

- Instalar VMware (es muy simple y aunque cerrado, te asegura mejor funcionamiento de las maquinas virtuales)

- En VMware, crear los servidores virtuales, en este caso, solo ocuparias 2, uno con Ubuntu/Edubuntu que te maneje las terminales y otro con Windows 2003 donde instalaras las aplicaciones Windows que usaras en las terminales.

- Recordemos que la topologia mas simple de esta red seria que el server Ubuntu maneje DHCP para dar IP a tus terminales, las terminales por tanto, deberan ser capaces de arrancar por PXE.

- Para usar las aplicaciones de windows 2003, requerimos solo de SeamlessRDP ([http://www.cendio.com/seamlessrdp/](http://www.cendio.com/seamlessrdp/)) y tener los usuarios de las Thin Client dados de alta en el servidor, asi como tambien las configuraciones necesarias para el uso de Terminal Services / Remote Desktop.

- Las Thin Clients serian ENTERAMENTE Ubuntu Linux, las aplicaciones pueden ser de Windows (Office, Outlook, Etc) y solo lo mas basico se correria en Ubuntu (Pidgin, Firefox, etc)

Hay muchas variantes para este esquema, en lo personal yo use servidores fisicos y una topologia de red distinta, asi que tuve que hacer arreglos muy especificos para mi red.

---

