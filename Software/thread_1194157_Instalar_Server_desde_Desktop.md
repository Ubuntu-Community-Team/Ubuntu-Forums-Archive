---
title: "Instalar Server desde Desktop"
date: 2009-06-22
forum: Software
---

### Post by panchoarq on 2009-06-22
Hola,
necesito ayuda en la instalación y configuración de Ubuntu como server de archivos e impresion. Para que tengan una idea de porque pido ayuda les cuento un poco:
Yo soy arquitecto y tengo una oficina dedicada a proyectos. Todo el tema tecnologico lo veo yo y hasta ahora no he tenido problemas. Ahira necesito, por el software que utilizamos, instalar unservidor que maneje los archivos y la impresion de un plotter y otras impresoras. Mi conocimiento de redes mas pto es nulo, me manejaba bien con la lan tipica pero un poco mas alla se me hace cuesta arriba. tengos equipos workstation con vista 65 bits ulltimate edition y acabamos de comprar un servidor basico para que haga las labores de administracion que les comente. Por otra referencia de un arquietcto y tambien por los costos involucrados en habilitar windos server me llamo la atencion el Ubuntu y como mi experiancia es nula segui su consejo de instalar la version desktop ya que la instalcion server es muy criptica e implica una interfaz que se basa en el terminal y despues instalarle los paquetes necesarios para que sea el server que necesito. Ya fue enorme mi sorpresa al ver la calidad grafica y facilidad de uso (se autoconfiguro todo) de la version desktop. Se me complico cuando empecé a ller sobre como trasnformarlo en un servidor de archivos y empezaroa a aparecer tutoriales diversoso que implicaban utilizar el terminal. Hasta estas son mis dudas:
[LIST=1]
[*]Debe estar instalado Samba. Revise los paquetes y aparece instalado pero tambien aparecen varias otras cosas con el nombre samba no instaladas. ¡debo instalarlas?
[*]¿Hay una interfaz grafica para confogurar samba graficamente y no mediante terminal?
[*]¿una vez instalado Samba cómo lo configuro para que cree el dominio y maneje las cuentas de usuario? Tienen que tener en cuenta que la terminología deredes de Windows (aparte de lo basico de lAN) no la domino.
[*]¿Esto implica que cuando prenda algunas de las estaciones de trabajo hay que ingresar un password y user para comenzar a trabajar?
[*]¿cómo puedo admisnitrar el servidor desde otro pc pero con una interfaz gráfica, sinterminal?
[/LIST] 
Bueno, espero que puedan ayudarme. 
 
Muchas Gracias:)

---

### Post by guillermolisi on 2009-06-22
> Debe estar instalado Samba. Revise los paquetes y aparece instalado pero tambien aparecen varias otras cosas con el nombre samba no instaladas. ¡debo instalarlas?
¿Hay una interfaz grafica para confogurar samba graficamente y no mediante terminal?
¿una vez instalado Samba cómo lo configuro para que cree el dominio y maneje las cuentas de usuario? Tienen que tener en cuenta que la terminología deredes de Windows (aparte de lo basico de lAN) no la domino.
¿Esto implica que cuando prenda algunas de las estaciones de trabajo hay que ingresar un password y user para comenzar a trabajar?
¿cómo puedo admisnitrar el servidor desde otro pc pero con una interfaz gráfica, sinterminal?


Para contar con un servidor Samba tenes que instalar samba-server y las dependencias necesarias para que funcione correctamente (que seran resueltas por el administrador de paquetes que utilices).

Dado que necesitan que funcione casi como un controlador de dominio, administrando y validando los accesos de usuarios y las impresiones, vas a tener que trabajar bastante configurandolo hasta que quede operativo para produccion. Inclusive y para hacer algo bien completo, tal vez convenga instalar y configurar LDAP tambien.

Tambien habria que verificar que el plotter funcione correctamente tanto para las maquinas clientes en Windows como bajo Ubuntu.

No te quiero desalentar, porque nada me gustaria mas que puedas poner en marcha todo ese proyecto, pero con los conocimientos que dices tener, me parece demasiado ambicioso para ponerlo en marcha en un plazo razonable (un par de semanas, por ejemplo).

Para administrar una maquina desde otra en Ubuntu tenes VNC que es un utilitario bastante liviano y sencillo. Si la maquina a administrar no posee escritorio grafico, tenes ssh (por linea de comando) que, ademas de ser seguro, es muy eficiente.

---

### Post by Carlos C on 2009-06-23
Thread movido al subforo software, ya que es el lugar que le corresponde ;)

---

### Post by panchoarq on 2009-06-23
Muchas Gracias guillermo por tu respuesta,
efectivamente es una tarea titanica para alguien que no se dedica al tema ni que sabe Linux pero de a poco voy progresando. Te cuento lo que he logrado hasta ahora y algunas dudas que tengo:
[LIST]
[*]Instalar Ubuntu Desktop
[*]Instalar paquetes Samba y configuradores graficos de este
[*]Crear los Shares para utilizar
[*]Crear los usuarios y sus claves
[/LIST]Cada vez que un usuario de Windows ve su red aparece el servidor como un equipo mas y para aceder a el le pide user y password. De esa manera accede a las carpetas que he efinido en Ubuntu para ese Share.  Hasta el momento me ha funcionado bien.
 
Ahora tratare que Ubuntu actue como un controlador de dominio primario y pueda administrar el control de acceso a los share, las impresoras y el ploter. Con respecto a esto último, tengo algunas dudas sobre que es mas óptimo en el momento de instalarlas, en términos de carga de trabajo para el servidor:
 
1.- Instalar el equipo directamente en el servidor (el trabajo de impresion lo hace el)
2.-Instalr los equipo en la red mediante tarjetas NIC y administrarlos conel servidor (¿el trabajo tambiénlo hace el servidor?)
3.-Instalar el equipo en un computador que no sera usado y compartirlo, utilizandolo como servidor de impresion.
 
Atentamente
 
 
Francisco

---

### Post by guillermolisi on 2009-06-24
> **panchoarq said:**
> Muchas Gracias guillermo por tu respuesta,
efectivamente es una tarea titanica para alguien que no se dedica al tema ni que sabe Linux pero de a poco voy progresando. Te cuento lo que he logrado hasta ahora y algunas dudas que tengo:
[LIST]
[*]Instalar Ubuntu Desktop
[*]Instalar paquetes Samba y configuradores graficos de este
[*]Crear los Shares para utilizar
[*]Crear los usuarios y sus claves
[/LIST]Cada vez que un usuario de Windows ve su red aparece el servidor como un equipo mas y para aceder a el le pide user y password. De esa manera accede a las carpetas que he efinido en Ubuntu para ese Share.  Hasta el momento me ha funcionado bien.
 
Ahora tratare que Ubuntu actue como un controlador de dominio primario y pueda administrar el control de acceso a los share, las impresoras y el ploter. Con respecto a esto último, tengo algunas dudas sobre que es mas óptimo en el momento de instalarlas, en términos de carga de trabajo para el servidor:
 
1.- Instalar el equipo directamente en el servidor (el trabajo de impresion lo hace el)
2.-Instalr los equipo en la red mediante tarjetas NIC y administrarlos conel servidor (¿el trabajo tambiénlo hace el servidor?)
3.-Instalar el equipo en un computador que no sera usado y compartirlo, utilizandolo como servidor de impresion.
 
Atentamente
 
 
Francisco
Francisco

Una aclaracion de forma: Ubuntu no sera el controlador de dominio sino que sera el Samba que corra en el quien se convierta en tal cosa.

Me parece muy buena actitud la tuya para encarar el tema de convertir Samba en un controlador de dominio.

Sobre las impresoras, mi preferencia es, siempre que se pueda, usarlas en red. De esta forma cada impresora puede ser direccionada por su IP evitando el uso de otros protocolos para lograr acceso a ellas.

De esta forma cada trabajo de impresion que se envie sera procesado por la PC que requirio el servicio, es decir usara su cola de impresion propia.

Luego, si esta alternativa no te es funcional, se puede definir que el server sea, ademas. controlador de impresion. Entonces la PC dialoga con el controlador de impresion y es este ultimo el que lidia con las impresoras y utiliza su cola de impresion.

Suponiendo trabajos de impresion voluminosos (en bytes), por la actividad que realizan, es importante considerar contar con generoso espacio en disco para que la cola de impresion en el servidor no se vea afectada negativamente.

Tambien podes intentar una solucion mixta entre impresoras con placas de red y un servidor de impresion que atienda ciertos requerimientos de gran magnitud (plotter por ejemplo).

---

