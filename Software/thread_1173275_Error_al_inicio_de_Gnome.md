---
title: "Error al inicio de Gnome"
date: 2009-05-29
forum: Software
---

### Post by PedroLuis on 2009-05-29
Hola se me produjo un error al borrar Network Manager y poner Wicd.

Tengo Ubuntu 8.04 en un Pentium 4, CPU 1,70Ghz, Hd 40 Gb, Ram 767Mb.

Como todo el tiempo se me borraban las DNS y tenia que ponerlas manualmente opte por ponerlas estáticas y sacar el networ manager que trae Ubuntu y me baje Wicd, ahora funciona la internet a la primera sin problemas.

Pero cada vez que inicio y entro aparese una rubrica de error y la pc se pone lenta,toma un tiempo largisimo antes que pueda usar el escritorio, incluso en un comienzo,los iconos no son los mismos, después de un largo tiempo se ponen normal , los bordes de ciertas ventanas han cambiado de color, pero hasta en la consola todo va lento,  cuando quiero editar algo no acepta sudo y puedo editar de todas manera sin sudo.

Aqui pongo lo que dice la ventana de error.
Si alguien a tenido este problema o puede solucionarlo, estare agradecido de la ayuda.

---

### Post by PedroLuis on 2009-05-29
> **PedroLuis said:**
> Hola se me produjo un error al borrar Network Manager y poner Wicd.

Tengo Ubuntu 8.04 en un Pentium 4, CPU 1,70Ghz, Hd 40 Gb, Ram 767Mb.

Como todo el tiempo se me borraban las DNS y tenia que ponerlas manualmente opte por ponerlas estáticas y sacar el networ manager que trae Ubuntu y me baje Wicd, ahora funciona la internet a la primera sin problemas.

Pero cada vez que inicio y entro aparese una rubrica de error y la pc se pone lenta,toma un tiempo largisimo antes que pueda usar el escritorio, incluso en un comienzo,los iconos no son los mismos, después de un largo tiempo se ponen normal , los bordes de ciertas ventanas han cambiado de color, pero hasta en la consola todo va lento,  cuando quiero editar algo no acepta sudo y puedo editar de todas manera sin sudo.

Aqui pongo lo que dice la ventana de error.
Si alguien a tenido este problema o puede solucionarlo, estare agradecido de la ayuda.

parese que no se abre el attachment que puse, si es asi, podrian comunicarmelo y lo agrego manual.

---

### Post by moreback on 2009-05-29
Era más facil que pegaras el texto en el mismo post que lo subieras como adjunto.

Da más info que no se te entiende mucho el problema, unos pantallazos serían de gran ayuda, aunque creo que algo mal hiciste al borrar el network-manager.

---

### Post by PedroLuis on 2009-05-29
> **moreback said:**
> Era más facil que pegaras el texto en el mismo post que lo subieras como adjunto.

Da más info que no se te entiende mucho el problema, unos pantallazos serían de gran ayuda, aunque creo que algo mal hiciste al borrar el network-manager.

Gracias por la informacion, aqui pege lo que me sale cada vez que inicio el pc, y entro al escritorio.


   	 	 	 	 	 	  Ha ocurrido un un error al iniciar el demonio del Administrador de Preferencias de GNOME.  
 

 Algunas cosas como las configuraciones de temas, sonidos o fondo de pantalla puede que no funcionen correctamente.  
 

 El último mensaje de error fue:  
 

 Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.  
 

 GNOME seguirá intentando reiniciar el Demonio de Preferencias la próxima vez que inicie una sesión.

---

### Post by PedroLuis on 2009-05-29
> **moreback said:**
> Era más facil que pegaras el texto en el mismo post que lo subieras como adjunto.

Da más info que no se te entiende mucho el problema, unos pantallazos serían de gran ayuda, aunque creo que algo mal hiciste al borrar el network-manager.

En una pagina de internet encontre como solucionar el problema de cambios de las DNS cada vez que iniciaba el pc.
 
Puse "sudo apt-get remove --purge network-manager" , despues arregle para que las DNS quedaran fijas 
 "sudo gedit /etc/resolv.conf" (aqui puse las nameserver)
"sudo gedit /etc/network/interfaces ( aqui puse lo necesario, auto eth0, iface eth0 inet static , address, netmask,gateway, con sus respectivos numeros)

Un problema que veo es que si voy a <Sistma>administracion>red, aparese la ventana de el Network manager que trae Ubunto, es decir una parte de el no se a borrado?
En consola y en el Synaptic, me sale que no esta.

Me da la imprecion que Gnome al estar network manager lo trata de activar, en vez de quedarse solamente con Wicd que es el nuevo network manager que uso.
Habra manera de enlasar Gnome con Wicd o se borrarian ficheros que nesecita Gnome?

---

### Post by moreback on 2009-05-30
Network-Manager en GNOME se compone de dos aplicaciones separadas, por un lado tienes el demonio network-manager que es el que te maneja la creación y administración de las conexiones. Y por otro lado tienes el nm-applet que es el ícono que aparece en el panel. Este último se usa para configurar el demonio de Network-Manager.

Es decir que te falta borrar el nm-applet.

Saludos.

PD: no es por nada pero considero que borrar network-manager es una tontera, muchas aplicaciones de GNOME ya lo usan para saber si tienen o no conexión a Internet. Además que manejar las conexiones vía consola está más que obsoleto para un pc de escritorio.

---

### Post by PedroLuis on 2009-05-30
> **moreback said:**
> Network-Manager en GNOME se compone de dos aplicaciones separadas, por un lado tienes el demonio network-manager que es el que te maneja la creación y administración de las conexiones. Y por otro lado tienes el nm-applet que es el ícono que aparece en el panel. Este último se usa para configurar el demonio de Network-Manager.

Es decir que te falta borrar el nm-applet.

Saludos.

PD: no es por nada pero considero que borrar network-manager es una tontera, muchas aplicaciones de GNOME ya lo usan para saber si tienen o no conexión a Internet. Además que manejar las conexiones vía consola está más que obsoleto para un pc de escritorio.

Al pareser network-manager no era el problema, lo active nuevamente desde synaptic, y se encargo de borrar Wicd, pero el problema sigue.

Puede ser algo directamente relacionado con Gnome, quisiera montar Gnome nuevamente quizas por alguna razon se habra dañado alguna carpeta de este programa, buscando soluciones en alguna parte salia que Gnome  contiene una serie de carpetas, tratare de averiguar nuevamente cuales eran.

En Synaptic al poner Gnome para reinstalar, no encuentro algo que me aclare si es el gruezo del programa, hay un Gnome2, que es este?

Bueno seguire tratando de arreglar,este problemilla.

---

### Post by Carlos C on 2009-05-30
Me parece que ya has hecho muchos cambios y no está claro en qué situación estás ¿Puedes explicar si tienes internet en cuanto inicias y qué tipo de error o comportamiento tiene tu sistema ahora que reinstalaste network-manager?

---

### Post by PedroLuis on 2009-05-31
> **Carlos C said:**
> Me parece que ya has hecho muchos cambios y no está claro en qué situación estás ¿Puedes explicar si tienes internet en cuanto inicias y qué tipo de error o comportamiento tiene tu sistema ahora que reinstalaste network-manager?

Esto lo dejo hasta aqui solamente. Trate de instalar Ubuntu 9.04 con el cd original que recibi de Canonical y me quedo una catastrofe por que hice cosas mal y me sali de la intalacion, es decir la interrumpi, ahora no puedo entrar al pc , me sale que " Grub Loading stager1.5.  GRUB loading, please wait....
Error 15
y de aqui no pasa, buscando en google, sale como solucionar esto pero a mi no me ha resultado, ahora lo unico que ando buscando es como salvar mi lista de direcciones de Evolution, si podria hacerlo desde el LiveCd , despues instalare desde cero Ubuntu 9.04.

Si pueden darme una mano en esto de la lista de direcciones se agradese.

---

### Post by Carlos C on 2009-05-31
Hola de nuevo. Yo no uso evolution, pero según entiendo existe una carpeta oculta en tu home que se llama ".evolution". Debes copiar esa carpeta en tu nueva instalación de ubuntu. También existe una segunda carpeta que creo debes copiar: ".gconf/apps/evolution". Recuerda que deberás montar tu partición "/home" desde el livecd para copiarlas a un dispositivo de almacenamiento, como un pendrive o algo por el estilo. Afortunadamente eso ya sabes hacerlo.
Saludos.

---

