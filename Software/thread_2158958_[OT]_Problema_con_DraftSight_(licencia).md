---
title: "[OT] Problema con DraftSight (licencia)"
date: 2013-07-01
forum: Software
---

### Post by Senger on 2013-07-01
Hola, qué tal?

Tengo DraftSight instalado desde hace varios meses y siempre vino funcionando bien (algunos problemitas pero no gran cosa). Hoy lo voy a abrir y me dice "Este producto no tiene licencia o ha vencido." y no me deja hacer absolutamente nada.

Hace como 40 minutos que estoy con Google tratando de encontrar alguna solución pero nada. Encima no se cómo desinstalar el programa y volver a instalarlo... ¿Alguien sabe cómo se resuelve?

Gracias de antemano!

---

### Post by gmunioz on 2013-07-01
Esta aplicación, requiere activación del producto, a través del email, previo registro en su sitio, sin números de serie ni complicaciones extra.
Activación, que se debe renovar cada 6 meses.
Evidentemente necesitas renovar la activación.

Visita este sitio:
[http://www.comunidadindustrial.com/viewtopic.php?f=5&p=25493](http://www.comunidadindustrial.com/viewtopic.php?f=5&p=25493)

Visitas el sitio, te registras para poder visualizar los links, descarga el archivo .deb para Ubuntu de unos 148 megas, instálalo con gdebi, te instalará más dependencias, acepta el acuerdo de licencia.
Terminada la instalación, al iniciarlo, me recomendará registrarte, pones tus datos e inmediatamente recibirásí un mail con un link de activación, lo pulsas y ya esta activado.
Periódicamente te enviarán información sobre actualizaciones, mejoras, agregados, etc. etc. totalmente gratis.

---

### Post by Senger on 2013-07-02
Eso lo había visto, pero supuse que si tenía que hacer algo así iba a estar especificado en la pagina oficial ([http://www.3ds.com/es/products/draftsight/free-cad-software/](http://www.3ds.com/es/products/draftsight/free-cad-software/)) donde no encontré nada del estilo.

Mañana de todos modos voy a intentar eso ya que hasta ahora es la única posible solución. 

Gracias por responder! :)

---

### Post by Senger on 2013-07-05
Lo que pusiste en el link me parece que no es lo que busco. Eso es para bajarlo si no lo tenes instalado. Yo necesito re-activarlo.

Creo que tendré que volver al autocad en virtualbox :(

---

### Post by elneo_1 on 2013-12-23
No hace falta volver hacia lo privativo. 

Me pasaba una situación similar, use draftsight durante 3 semanas hace ya mucho tiempo (por lo menos hace 10 meses) y me arrojaba el mismo error que a ti.

Lo que me solucionó el problema era eliminar el draftsight de mi ordenador e instalarlo nuevamente. Te explico como:

Inicia tu ordenador

abre tu terminal y corre este comando que te ayudará a desinstalarlo:

[COLOR=#0000cd][FONT=arial][SIZE=4]sudo dpkg -r dassault-systemes-draftsight
[/SIZE][/FONT][/COLOR][FONT=Verdana]
En la pagina ([/FONT][http://www.3ds.com/es/products-services/draftsight/download-draftsight/](http://www.3ds.com/es/products-services/draftsight/download-draftsight/)[COLOR=#222222][FONT=Verdana]) podrás descargar la versión de DraftSight para Ubuntu. 
Una vez descargada, lo almacenas en un directorio o carpeta. En mi caso fue en el Escritorio

Luego te vas a la terminal y haces:

[/FONT][/COLOR] [FONT=Verdana][/FONT][COLOR=#333333][/COLOR][SIZE=4][FONT=arial][COLOR=#0000cd]cd Escritorio[/COLOR][/FONT][/SIZE][COLOR=#333333]
[/COLOR][FONT=Verdana]
veras todo lo que hay en tu Escritorio o en su defecto lo que hay en el directorio donde almacenes draftsight.deb 
Luego haces:
[/FONT][COLOR=#333333]
[/COLOR][COLOR=#0000cd][SIZE=4][FONT=arial]sudo dpkg -i --force-architecture *deb[/FONT][/SIZE][/COLOR][COLOR=#333333][/COLOR]
[COLOR=#333333]
[/COLOR][FONT=Verdana]Logueas cuando sea necesario y listo Draft Sight de vuelta, asi me funcionó!!![/FONT]

---

