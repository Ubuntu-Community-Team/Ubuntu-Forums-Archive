---
title: "Compartición de Archivos"
date: 2010-08-11
forum: Software
---

### Post by patraicio on 2010-08-11
Hola:

Tengo montada un grupo de trabajo para compartir archivos entre un pc con Win Xp y un note con Ubuntu 10.04. Tengo Samba y logré configurar una carpeta de /home/usuario/ para que fuera "vista por XP"(por medio de la consola editando el archivo smb.confg [así creo que se llamaba] y luego por el entorno gráfico de samba en Sistema> Administración> Samba). Mi enredo está al momento de querer hacer la relación entre los dos pc's de la RED. 
En Lugares > Red > Red de Windows > CASA(nombre que le puse desde el asistente de WIN XP) puedo ingresar al pc de escritorio y a las carpetas que deje libres para revisar por medio del grupo de trabajo. Todo ese trabajo fue bastante simple desde Windows, ya que no se necesitaba mayor configuración. El problema es que no puedo hacer lo mismo desde Ubuntu; se supone que al configurar esa carpeta en /home/usuario/ para que fuera vista por los equipos de la red, en Mis Sitios de Red dentro de Explorer debía solamente recargar para que apareciera, cosa que no sucede.
La pregunta del millón es ¿qué estoy haciendo mal? Leí por ahí que debía agregar la carpeta por medio de la dirección IP del note, pero no sé si la que estoy introduciendo será correcta (¿como saber cuál es?) Tampoco sé si el lugar desde donde estoy agregando o tratando de visualizar la carpeta será la correcta (hay un link en Mis sitios de red donde dice: Agregar nuevo sitio, ahí ingreso lo siguiente: \\192.168.3.1\home\usuario\Público, pero no sucede nada).
Estoy estancado en ese punto y no sé que hacer, ojalá puedan ayudarme.
Desde ya gracias!

Saludos!

---

### Post by Carlos C on 2010-08-12
Quizás esto te pueda servir:

[http://blockdeubuntu.blogspot.com/2008/07/cmo-configurar-samba-en-ubuntu.html](http://blockdeubuntu.blogspot.com/2008/07/cmo-configurar-samba-en-ubuntu.html)

Saludos.

---

### Post by patraicio on 2010-08-12
Gracias por la ayuda, me sirvieron bastante los puntos que hacía referencia a comprobar la configuración. Al parecer mi problema tiene relación con mi usuario del servidor samba y su contraseña (de echo no lo puedo crear) googlearé un rato y cuento como salió.

Saludos!

---

### Post by patraicio on 2010-08-12
Al parecer sólo estaba escribiendo mal (no noto muy bien los espacios en la consola :P)

Luego de crear un usuario y comprobar la disponibilidad mediante smbclient, obtuve esto:

alvaro@alvaro-note:~$ smbclient -L alvaro-note -Upatraicio
Enter patraicio's password: 
Domain=[CASA] OS=[Unix] Server=[Samba 3.4.7]

	Sharename       Type      Comment
	---------       ----      -------
	print$          Disk      Printer Drivers
	Público        Disk      
	IPC$            IPC       IPC Service (alvaro-note server (Samba, Ubuntu))
Domain=[CASA] OS=[Unix] Server=[Samba 3.4.7]

	Server               Comment
	---------            -------

	Work*****            Master
	---------            -------
	WORK*****            ALVARO-NOTE

print$ e IPC$ son dominios agregados por samba, Público es la carpeta en /home/usuario/ con la que estoy tratando compartir por ahora. No entiendo si porque me sale Domain=[CASA] y WORK***** alvaro-note ... siendo que el grupo de trajo (y así sale en smbd.conf) es CASA.


Saludos!

---

### Post by patraicio on 2010-08-12
Bien, funcionó de perfección. Lo único es que desde windows no puedo entrar la primera vez a la carpeta compartida, tengo que intentar denuevo y ahí si, quizás porqué será.


Gracias!

PD:El mayor cuidado para este tipo de trabajo es fijarse en ingresar correctamente los datos en la consola (por si a alguien le surge el mismo problema que a mi).

---

### Post by Carlos C on 2010-08-15
Me alegro que te haya funcionado. Lo damos por solucionado entonces.

---

