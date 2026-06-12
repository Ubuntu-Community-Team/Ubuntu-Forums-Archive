---
title: "No puedo conectar a TS de Windows Server desde XP en VM"
date: 2011-02-28
forum: Software
---

### Post by rva1945 on 2011-02-28
Jamás pude conectarme como remote desktop al Windows Server 2003 R2 de la oficina ni con TS client, ni con Rdesktop, ni con GRDC remote desktop, etc, con ningún cliente Linux, siempre me da que la conexión fue rechazada. Entonces para ello booteaba con partición XP (tengo disco particionado con XP y Ubuntu, conexión ADSL de Speedy) y accedia con el mstsc.exe.

Resulta que se arruinó el boot de XP, imposible arreglarlo, no me quedó otra que instalar una VM en Ubuntu con el VirtualBox y ahi puse el XP. Por NAT (settings-network de la VM) navega al toque "heredando" la conexión desde Ubuntu, por decirlo en términos familiares.

PERO...cuando voy al mstsc, nada, no conecta, se cae por timeout. PING al server funciona, y sé que está activo y atendiendo.

Estimados, en el sitio en inglés nadie me dió solución, a ver si entre los argentos lo sacamos: qué puedo hacer?

Acaso el Windows Server "sabe" que no me conecto desde un miembro de la familia Windows, aunque sea una VM, pues el host es Linux?

De paso, cómo demonios entro al SpeedTouch? ifconfig en terminal me tira 127.0.0.1 pero no me da bola el Firefox, no entra. Cómo sé la address del modem?

Gracias muchachos por la ayuda que puedan brindar.

Robert

---

### Post by guillermolisi on 2011-02-28
Me fijaria como esta configurado el cliente de TS en Win y verificaria los paramteros equivalentes en alguno de los programas que mencionaste para Linux.

Por dar un ejemplo, con Remmina y KRDC me conecto sin problemas a un server de las mismas caracteristicas que mencionas.

Por el tema del modem, fijate que seguramente en [adslzone]("http://www.adslzone.net/") encontras informacion util.

---

### Post by rva1945 on 2011-02-28
> **guillermolisi said:**
> Me fijaria como esta configurado el cliente de TS en Win y verificaria los paramteros equivalentes en alguno de los programas que mencionaste para Linux.

Por dar un ejemplo, con Remmina y KRDC me conecto sin problemas a un server de las mismas caracteristicas que mencionas.

Por el tema del modem, fijate que seguramente en [adslzone]("http://www.adslzone.net/") encontras informacion util.

Para ver como esta confiogurado el cliente TS en Win, supongo te referís a opciones de la ventana de mstsc, pero más que usuario, password y dominio no tengo. No tengo solapa Avanzadas.

Remmina no conozco, lo instalo del repositorio?

Con KRDC voy a Connect to a Windows Remote Desktop, pongo todos los datos, que se me pide, usuario y password, y se queda en connecting to (nombre del server)

Gracias

---

### Post by guillermolisi on 2011-02-28
Remmina se instala desde los repositorios y, para mi, es algo mas completo que KRDC. Tuve mejores resultados cuando tengo un WinServer del otro lado.

Con KRDC tenes que elegir que protocolo vas a usar, VNC o RDP. Fijate porque hay un valor por defecto y posiblemente no sea el adecuado.

Luego, si haces ping desde Linux a la URL o a la IP del servidor, que respuesta tenes para cada caso ?

---

### Post by rva1945 on 2011-02-28
> **guillermolisi said:**
> Remmina se instala desde los repositorios y, para mi, es algo mas completo que KRDC. Tuve mejores resultados cuando tengo un WinServer del otro lado.

Con KRDC tenes que elegir que protocolo vas a usar, VNC o RDP. Fijate porque hay un valor por defecto y posiblemente no sea el adecuado.

Luego, si haces ping desde Linux a la URL o a la IP del servidor, que respuesta tenes para cada caso ?

Probaré Remmina en instantes.

El protocolo es el RDP, eso es claro.

Tengo la URL del server y el ping me informa los paquetes recibidos al toque.

Saludos

---

### Post by rva1945 on 2011-02-28
> **guillermolisi said:**
> Remmina se instala desde los repositorios y, para mi, es algo mas completo que KRDC. Tuve mejores resultados cuando tengo un WinServer del otro lado.

Con KRDC tenes que elegir que protocolo vas a usar, VNC o RDP. Fijate porque hay un valor por defecto y posiblemente no sea el adecuado.

Luego, si haces ping desde Linux a la URL o a la IP del servidor, que respuesta tenes para cada caso ?

Te aclaro que no dejo de ser novato en Linux. Busqué Remmina en Ubuntu software center, no lo encontré. FUí a este sitio [http://remmina.sourceforge.net/downloads.shtml](http://remmina.sourceforge.net/downloads.shtml), creo que segui los pasos

sudo add-apt-repository ppa:llyzs/ppa (tengo Karmic)
y
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 5A0FA8F1

este es todo el output:

**robert@rvasystem:~$ sudo add-apt-repository ppa:llyzs/ppa**
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv BFFDC4056409A18A98249B87D7260B8F5A0FA8F1
gpg: requesting key 5A0FA8F1 from hkp server keyserver.ubuntu.com
gpg: key 5A0FA8F1: public key "Launchpad Remmina" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
**robert@rvasystem:~$ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 5A0FA8F1**
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys 5A0FA8F1
gpg: requesting key 5A0FA8F1 from hkp server keyserver.ubuntu.com
gpg: key 5A0FA8F1: "Launchpad Remmina" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1

pero no aparece en ningñun lado. Busqué luegoi remmina en Synaptic pero nada.

---

### Post by rva1945 on 2011-02-28
> **guillermolisi said:**
> Remmina se instala desde los repositorios y, para mi, es algo mas completo que KRDC. Tuve mejores resultados cuando tengo un WinServer del otro lado.

Con KRDC tenes que elegir que protocolo vas a usar, VNC o RDP. Fijate porque hay un valor por defecto y posiblemente no sea el adecuado.

Luego, si haces ping desde Linux a la URL o a la IP del servidor, que respuesta tenes para cada caso ?

Probé bajando y descomprimiendo el 0.9 de acá:

[http://sourceforge.net/projects/remmina/files/](http://sourceforge.net/projects/remmina/files/)

luego en terminal pme posicioné, corrí ./configure, tiró varias líneas incluyendo esto

configure: error: Package requirements (
    glib-2.0 >= 2.20.0
    gtk+-2.0 >= 2.16.0
    gmodule-2.0
) were not met:
No package 'gtk+-2.0' found

algunas líneas más y hasta ahi llegó.

---

### Post by rva1945 on 2011-02-28
Instalé Remmina:

Unable to connect to RDP server 200.55.63.181

Ya no tengo más argumentos.

---

### Post by guillermolisi on 2011-02-28
Si, es cierto, no esta en los repos de Ubuntu, my fault.

Ahora, esa IP publica es la misma a la que apuntas desde Windows ? (supongo que si, pero a veces hasta al mas despierto se le escapa la liebre).

Luego, podras consultar con el admin de ese server para que te asesore respecto de algo que pueda haber configurado en particular ?

A mi tambien me rebota la conexion desde algun cliente TS en Linux, asi que supongo que algo en particular en ese server debe existir para que suceda esto.

---

### Post by rva1945 on 2011-03-01
> **guillermolisi said:**
> Si, es cierto, no esta en los repos de Ubuntu, my fault.
 
Ahora, esa IP publica es la misma a la que apuntas desde Windows ? (supongo que si, pero a veces hasta al mas despierto se le escapa la liebre).
 
Luego, podras consultar con el admin de ese server para que te asesore respecto de algo que pueda haber configurado en particular ?
 
A mi tambien me rebota la conexion desde algun cliente TS en Linux, asi que supongo que algo en particular en ese server debe existir para que suceda esto.
 
 
Dese luego, es la que he conectado desde XP siempre.
 
Resulta que sí pude conectar a otro server 2003 de la empresa, pero desafortunadamente no tengo login en ese. Este es un WS 2003, el que no puedo conectar es WS 2003 R2, ahi está eltema, creo que la actualización a Windows Server 2003 R2 es la que no acepta clientes Linux.

---

### Post by guillermolisi on 2011-03-01
No, seguro que no es por ese motivo.
Adjunto prueba conectado con Remmina.

---

### Post by rva1945 on 2011-03-01
> **guillermolisi said:**
> No, seguro que no es por ese motivo.
Adjunto prueba conectado con Remmina.
 
 
No quise decir que WS2003R2 no acepta clientes Linux, encontré información de que "algo" hay que hacer tras actualizar un server 2003 a R2 para que acepte clientes Linux.
 
[http://blog.scottlowe.org/2006/04/27/linux-ad-integration-with-windows-server-2003-r2/](http://blog.scottlowe.org/2006/04/27/linux-ad-integration-with-windows-server-2003-r2/)
 
Pero acá en la empresa no dan el brazo a torcer, me darán una IP fija en la PC para que acceda directamente a ella desde afuera.
 
Saludos

---

### Post by guillermolisi on 2011-03-02
> **rva1945 said:**
> De paso te consulto: se j***ó el arranque de WXP, tengo disco particionado con XP y Ubuntu. Si quiero botear en XP cuando aparece Windows y la barra de progreso luego se rebootea una y otra vez. No quiero j***r a Ubuntu en el intento.

Sí puedo acceder al disco de XP desde Ubuntu.

Saludos
Esta en un [nuevo thread]("http://ubuntuforums.org/showpost.php?p=10510966&postcount=1") ya que cambiste el tema que dio origen a este.

---

### Post by hectorivand on 2011-03-02
Es un tema de configuración, de como configuraron R2 cuando le dieron el rol de Servidor de Escritorios Remotos (Remote Desktop Services)

Especificamente habrán seleccionado que la autenticación también sea a nivel de red con lo cual solo deja conectar a equipos que corren versiones de Windows y de Conexión a Escritorio Remoto especificas que soporten el tipo de autenticación. (Vista, Seven, 2008, 2008r2)

Para que se pueda conectar un Ubuntu o cualquier otro sistema/programa non-windows/windowsxp, tienen que cambiar a un nivel de autenticación que no requiera la misma a nivel de red.

Edit.: Dejó información al respecto de la autenticación a nivel de red.: [http://technet.microsoft.com/es-es/library/cc742818(v=ws.10).aspx](http://technet.microsoft.com/es-es/library/cc742818(v=ws.10).aspx)

Saludos
Nacho

---

