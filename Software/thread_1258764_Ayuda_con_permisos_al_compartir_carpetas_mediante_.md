---
title: "Ayuda con permisos al compartir carpetas mediante SAMBA"
date: 2009-09-05
forum: Software
---

### Post by panchoarq on 2009-09-05
Hola, yo hace un tiempo les escribí.Soy arquitecto y estoy instalando en un servidor Dell PowerEdgeT100 un servidor de archivos e impresión con Ubuntu para elresto delos equipos, todos con windows Vista Ultimate 64 Bits. Como no me manejo con la linea de comandos,baje Ubuntu Desktop que es mas amigable para alguien como yo e instale los paquetes de Samba para realizar este servicio. Cree los usuarios y los shares (que es un concepto que aun no entiendo mucho) para poder operar. Al probarlo,efectivamente podia ver el servidor samba desde los pcs y para pobar cree carpetas. El problema se me produjo cuando trate de borrar esas carpetas y no me deja porque me dice que no tengo privilegios,que el usuario es root. Ahi empieza mi duda grande. 

1.-¿Como opera Linux cuando un usuario desde otro pc crea carpertas en el servidor y por que al revisarlas como adminsitrador no me deja borrarlas?
2.-Cuando yo creo un Share y defino los usuarios que acceden a el,estos últimos solo acceden a los shares a los que están autorizados o pueden navegarpor elservidor libremente?
3.-Cuando yo creo un usuario en Samba,qué carpetas crea por defecto en el servidor?.Porlo que vi en la carpeta Home aparece una carpeta con el nombre del usuario y dentro de ella otras mas.
4.-¿Cómo funciona el concepto de Shares?
5.-¿En qué carpeta yo debiera crear el espacio de trabajo para toda la oficina y ahi crear las carpetas de cada proyecto? 
6.-Duda general de metodologia de uso de un servisor ¿cuando se ocupa un servidor, lo usual es que los usuarios no creen ni borren cosas ahí,solo saquen información que está centralizada y en caso de necesitar que se cree algo lo hace el administrador?

Muchas Gracias por su tiempo

---

### Post by gmunioz on 2009-09-05
Hola pan...:

Puede que en este sitio encuentres respuestas

amplias a tus planteos:

[http://es.tldp.org/htmls/manuales.html](http://es.tldp.org/htmls/manuales.html)

---

### Post by panchoarq on 2009-09-05
Gabriel,
Muchas gracias por tu respuesta. Hay varios manuales interesantes ahi pero la mayoria necesitan de un nivel de conocimiento que al parecer no tengo.Quizás me puede ayudar con esta pequeña duda. 
Al iniciar la interfaz grafica de Samba y crear un Share,este queda por defecto creado por el usuario root y me niega a mi (con la cuenta de usuario que inicie Ubuntu) la capacidad de eliminar esa carpeta. ¿Hay alguna manera de poder hacer eso? ¿Porque si estoy con mi cuenta de usuario este creacion de shares la hace bajo el usuario root?

Muchas gracias por tu tiempo y ayuda.

---

### Post by Carlos C on 2009-09-05
> **panchoarq said:**
> 
Al iniciar la interfaz grafica de Samba y crear un Share,este queda por defecto creado por el usuario root

¿Qué interfaz gráfica de Samba estás usando?

Mira, puedes ver acá algunos tips para usar samba, está todo bastante simplificado, te puede ayudar a entender un poco mejor los manuales:

[http://blockdeubuntu.blogspot.com/2008/07/cmo-configurar-samba-en-ubuntu.html](http://blockdeubuntu.blogspot.com/2008/07/cmo-configurar-samba-en-ubuntu.html)

Saludos.

---

### Post by gmunioz on 2009-09-05
Hola pan...:

1 - En principio, te sugiero si piensas administrar el

sistema que leas los manuales con tranquilidad, pues te

seran de utilidad, no necesitas conocimientos previos.

2- Todas las modificaciones que realices en un sistema

GnuLinux, que no sean dentro de tu /home/usuario, las debes

hacer como administrador del sistema. Los usuarios solo

pueden leer y escribir, crear y eliminar en el directorio

/home/usuario/ y en los que cree como usuario.

En Ubuntu por razones de seguridad, el usuario administrador,

root, esta deshabilitado, por lo que el usuario que instaló

el sistema, puede actuar con permisos temporarios de administrador

mediante el uso del comando sudo, que antes de ejecutar la orden 

solicita la contraseña del usuario.

sudo su

sudo -i

Permiten loguearse como root y continuar ejecutando comandos como 

administrador.

sudo comando

Permite ejecutar el comando como administrador.

sudo tiene una cierta latencia, que luego de su uso no solicita

nuevamente la contraseña por un período corto de tiempo.

Para habilitar otro usuario, que no sea el que instaló el

sistema, para que accione con permisos temporarios de administrador

es necesario editar el archivo /etc/sudoers, con el editor vi .

---

### Post by panchoarq on 2009-09-06
Carlos,
estoy usando creo que dos, una que es muy básica llamada system-config-samba que es para manejar shares y usuarios y la otra es Gadmin-Samba que me permite hacer mas cosas. El problema es que con el primero creo los shares, los usuarios y les doy los privilegios para cada share. Luego en el otro configuro un poco mejor los permisos pero al momento de ver las carpetas desde windows en el servidor, no me deja que los usuarios creen carpetas en sus shares. 
Otro tema extraño es que en las pruebas que he hecho, he creado distintos shares para probar desde system-config-samba pero ahora no me deja borrarlas ya que el propietario es root. Elimine los shares que crearon esas carpetas pero al ver el servidor dsde un pc windows aparecen todas, en algunas puedo escribir, crear y borrar carpetas y archivos desde los usuarios windows y en otras no hay posibilidad. ¿como puedo controlar eso si ya no tengo los shares y si veo las propiedades de las carpetas estan creadas por root? cómo se explica que el algunas se pueda y en otras no?

---

### Post by Carlos C on 2009-09-06
Creo que lo mejor es que tomes en consideración lo que dice gmunioz. Es bueno tener claro como funcionan los permisos en linux cuando uno quiere compartir carpetas por samba. Te sugiero que leas la Guía Ubuntu, que está pensada para quienes no tienen conocimientos previos en linux:

[http://www.guia-ubuntu.org/index.php?title=Samba](http://www.guia-ubuntu.org/index.php?title=Samba)

Respecto a los problemas que tienes, esto es una opinión personal, puedes estar en desacuerdo, pero yo no usaría esos programas, sino que aprendería a editar el archivo "smb.conf". Es la manera más segura, versátil y que te ahorra la mayor cantidad de problemas. En la Guía está todo lo que necesitas saber. En el enlace que antes te puse están los datos básicos que, creo, uno necesita manejar para que samba funcione. Si lees ambos enlaces tus problemas se solucionarán, en serio.

---

