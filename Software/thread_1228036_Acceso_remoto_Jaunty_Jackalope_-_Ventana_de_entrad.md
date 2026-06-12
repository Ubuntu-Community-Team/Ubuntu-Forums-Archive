---
title: "Acceso remoto Jaunty Jackalope - Ventana de entrada"
date: 2009-07-31
forum: Software
---

### Post by cmarchesin on 2009-07-31
Hola. Estoy algo complicado y no logro resolverlo de ninguna de las maneras que, he leído, podría resolverse. Paso a exponer el problema :

He estado utilizando x11vnc con interfaz http-java para acceder al equipo. El problema es que ahora que tengo mas de una cuenta habilitada en el sistema operativo, no puedo loguearme en él remotamente, es decir, el x11vnc se inicia cuando abro una sesión determinada.  < Necesito acceder remotamente a la ventana de entrada (logueo) de mi Ubuntu >.

*He desistido en el uso de cliente x11vnc web, y estoy utilizando el vnc viewer (supuse que seria para problemas intentar iniciar como proceso el servicio java + x11vnc antes de tener sesion iniciada).

*He intentado colocando un enlace, hacia un script que iniciaba x11vnc, en /etc/rc.local . Me inicia el x11vnc luego de iniciar sesion [en este paso me encontre con otro error, cuando intentaba ejecutar el script que iniciaba el x11vnc en algunos directorios me mostraba "Failed to contact the GConf daemon; exiting" ¿?].

*He intentado añadir el x11vnc a init.d, y luego hacer los enlaces con update-rc.d. Utilicé el template de script skeleton, pero no lo pude hacer andar (no pude armar el script correctamente :(   , tiene una estructura bastante compleja).

*He deshabilitado x11vnc y habilitado el escritorio remoto que trae nativo Ubuntu paro hace exactamente lo miso (no he podido configurarlo para poder acceder a la ventana de entrada). He tocado la configuración desde sistema>>administración>>ventana de entrada habilitando el acceso remoto (acá también toque la config. de  xdmcp poniendo como puerto udp para que escuche el 5900).

No se que más intentar. Como dice le titulo, lo que intento resolver es un acceso remoto incluyendo la ventana de logueo de Ubuntu por lo cual si hay alguna otra herramienta de acceso remoto que permita hacerlo de manera sencilla intento con eso. 

Desde ya muchas gracias !!!! es mi primer post es un foro  !!!! (se que es ultra extenso pero queria dar idea de todo lo que ya he probado). Saludos a todos y todas .

Catriel - beginnig for ever

---

### Post by cmarchesin on 2009-08-19
[responderse a si mismo en un foro no es la idea, pero tal vez a alguien le sirva !!!]

Bueno, no he tenido respuestas, pero le he encontrado la vuelta utilizando un soft llamado freeNX.  El software abre sesiones remotas en el equipo, pero no puede "juntarse" a una sesión ya iniciada. Desde la parte administrator del software se pueden denegar y aceptar usuarios remotos. 
Es más seguro que el acceso remoto por VNC gracias a que encripta el trafico con ssh. El rendimiento también es mejor, la interacción mucho mas veloz. Lo probé y funciona bien. Dejo los links con info y descargas.

 
  [http://www.wikilearning.com/monografia/escritorio_remoto_con_freenx-que_es_freenx/6865-2](http://www.wikilearning.com/monografia/escritorio_remoto_con_freenx-que_es_freenx/6865-2)
   
  [http://es.wikipedia.org/wiki/Tecnolog%C3%ADa_NX](http://es.wikipedia.org/wiki/Tecnolog%C3%ADa_NX)
   
  [http://www.nomachine.com/download.php](http://www.nomachine.com/download.php)
   

-  Catriel -

---

