---
title: "problema en VirtualBox"
date: 2008-09-18
forum: Software
---

### Post by benjamin_linux on 2008-09-18
El problema, como dice bien el topic, es en VirtualBox, pero les pregunto a ustedes a ver si me pueden dar una mano... 
Creo la máquina virtual, elijo el sistema (OpenSolaris, que elegí virtualizar y evitar el problema que-si-reconoce-que-si-no-reconoce-el-grub), creo el disco virtual, le doy 10g de espacio,512 de ram, todo perfecto.

Cuando pongo Configuración me dice "could not load the host usb proxy service"... y no creo que tenga nada que ver, pero en fin el problema es que cuando pongo iniciar, se queda al 0% y no hace -nada-, se cuelga y tengo que cerrar VB por la fuerza.

¿Alguien sabe qué puedo hacer, o me recomienda dónde preguntar?
Perdón por postear algo no extrictamente ubuntero
y gracias :)

---

### Post by sartrejp on 2008-09-18
Hey, hace un tiempo tuve el mismo problema.
Dicen que para solucionarlo hay que ir a /etc/udev/rules.d/40-permissions.rules* editar el archivo como sudo y
modificar la linea que dice:

# USB devices (usbfs replacement)
SUBSYSTEM=="usb_device", MODE="0664"

por

* # USB devices (usbfs replacement)
SUBSYSTEM=="usb_device", MODE="0666"*

La verdad lo hice dos veces, la primera me funcionó y la segunda (ubuntu 8.04)no se solucionó así y lo arreglé agregando al /etc/fstab la siguiente línea al final

none /proc/bus/usb usbfs devgid=1002,devmode=664 0 0

Con eso, anduvo lo más bien.
Espero te sirva.
Suerte

---

### Post by benjamin_linux on 2008-09-18
Había hecho lo que me dijiste y nada, pero

actualicé Hardy y... ahora me funciona!

Gracias! :D

---

### Post by sartrejp on 2008-09-20
No será que reiniciaste la pc y se montaron las particiones? porque después de agregar la línea en el fstab había que desmontar las particiones y montarlas todas. Se me escapó el detalle....
Da igual, buenisimo que funcione

---

### Post by benjamin_linux on 2008-09-20
Había reiniciado, porque actualicé al otro día recién. Capaz tomó los cambios hechos recién cuando actualicé? Como sea, gracias!

---

### Post by lord-metal on 2008-09-25
yo tengo un problema,instale virtual box,instale win 2003 server y algunas maquinas virtuales con xp,esto lo hice para poder practicar la administracion de red en el server,ya que donde trabajo utilizan este tipo de sistema,el problema esta en la configuracion de red y no puedo ver las maquinas que estan en mi red virtual porque no hay comunicacion entre ellas,ya probe varias cosas pero ninguna me funciono,si alguien tiene la respuesta,y me puede ayudar,le voy  a estar agradecido.
:guitar:

---

### Post by sartrejp on 2008-09-26
Yo nunca pude conectar el windows virtualizado que tenía con Ubuntu (y lo tuyo es mucho más ambicioso). Lo que te recomendaría es que lo escribas en otro post, con un título más específico, a ver si alguien sabe como hacer eso.
Suerte y sorry :(

---

### Post by guillermolisi on 2008-09-28
> **lord-metal said:**
> yo tengo un problema,instale virtual box,instale win 2003 server y algunas maquinas virtuales con xp,esto lo hice para poder practicar la administracion de red en el server,ya que donde trabajo utilizan este tipo de sistema,el problema esta en la configuracion de red y no puedo ver las maquinas que estan en mi red virtual porque no hay comunicacion entre ellas,ya probe varias cosas pero ninguna me funciono,si alguien tiene la respuesta,y me puede ayudar,le voy  a estar agradecido.
:guitar:

Para llevar a cabo lo que queres practicar mi recomendacion es que hagas lo mismo pero con VMware, no con VBox.

VMware te permite hacer bridge y ver toda la red, dominio incluido, cosa que con VBox no logras (por lo menos con la misma facilidad).
Ademas, podes administrar la VM desde cualquier maquina que tenga instalada la VMware console.

---

### Post by sebaxxxtian on 2008-09-29
> **guillermolisi said:**
> Para llevar a cabo lo que queres practicar mi recomendacion es que hagas lo mismo pero con VMware, no con VBox.

VMware te permite hacer bridge y ver toda la red, dominio incluido, cosa que con VBox no logras (por lo menos con la misma facilidad).
Ademas, podes administrar la VM desde cualquier maquina que tenga instalada la VMware console.

alguien sabe de donde bajar el vm ware y un buen tutorial para emular un XP? necesito si o si windows para correr aplicaciones laborales y con wine no hubo caso. el virtual box no lo pude configurar y me dijeron q vmware es mejor.

gracias

---

### Post by guillermolisi on 2008-09-29
> **sebaxxxtian said:**
> alguien sabe de donde bajar el vm ware y un buen tutorial para emular un XP? necesito si o si windows para correr aplicaciones laborales y con wine no hubo caso. el virtual box no lo pude configurar y me dijeron q vmware es mejor.

gracias

El VMware lo bajas gratis del siguiente enlace;

[http://www.vmware.com/download/server/](http://www.vmware.com/download/server/)

Ahi tenes el server, la consola y las tools (o sea, todo lo necesario para virtualizar y administrar las VMs que tengas en tu equipo y en otros tambien a traves de la consola).

Vas a necesitar serials para usar en tiempo de instalacion. Si te registras (gratuitamente y no te rompen los pies con mails) te dan los que necesites hasta un limite (que no recuerdo cuanto es).
Si no te queres registrar, search for them with Google.

Cuando estes instalando hay una buena cantidad de preguntas a contestar (para configurar el server). Algunas respuestas vienen con valores por defecto y otras no.

Tambien vas a necesitar los headers del kernel que los podes bajar de los repos de Ubuntu (build-essentials, etc., etc.)
Tal vez si procuras alguna guia de instalacion de VMware en Internet (Google) te aclare el panorama antes de comenzar.

Una vez en marcha usas tu imagen ISO o el CD del XP para iniciar e instalar el Windows, tal como si fuera una maquina real, ni mas ni menos.

Configuras Network (en la VM) como bridge asi podes formar parte de un dominio y/o ver las PCs del entorno de red.

Los productos de virtualizacion NO emulan, son maquinas con una plataforma operativa (igual que una maquina real).
Las VMs no tienen (por ahora) aceleracion de video asi que jueguitos se pueden usar pero que no requieran de esa funcion.

---

