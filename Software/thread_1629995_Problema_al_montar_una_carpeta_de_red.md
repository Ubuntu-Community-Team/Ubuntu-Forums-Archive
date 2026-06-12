---
title: "Problema al montar una carpeta de red"
date: 2010-11-24
forum: Software
---

### Post by diego_diaz on 2010-11-24
Hola, tengo un pequeño problema al montar una carpeta de red al iniciar el sistema y quisiera pedirles ayuda para poder solucionarlo. El tema es asi; tengo istalado Ubuntu 10.10 conectada a una red, entrando por Nautilus Lugares--> Red--> Red de windows--> LINUX-->diservel01-->publica-->Z siendo Z la carpeta que quiero montar, no tengo ningun inconveniente. Al llegar a este punto me fijo las propiedades de la carpeta y en Lugar me indica que la carpeta se encuentra en smb//diservel01/publica/Z. Ahora yo quiero que esa carpeta sea montada desde el inicio del sistema, con lo que voy a modificar el archivo fstab agregando la siente linea;
smb//diservel01/publica/Z /mnt/comparida auto rw 0 0
y cuando quiero montar desde la consola con el comando; sudo mount -a esta me devuelve que el lugar smb//diservel01/publica/Z no existe. Pueden darme alguna sugerencia o indicarme que estoy haciendo mal?
Desde ya muchas gracias.

---

### Post by gmunioz on 2010-11-24
la línea es:

//diservel01/publica/Z  /mnt/compartida  smbfs  guest,uid=1000,iocharset=utf8,codepage=unicode,unicode  0  0

---

### Post by diego_diaz on 2010-11-25
Hola, antes que nada queria agradecerte la ayuda. Ahora, inserto la linea al fstab y desde terminal intento montar la carpeta y me devuelve lo siguiente:
diego@diego-desktop:~$ sudo mount -a 
[sudo] password for diego: 
[mntent]: la línea 15 de /etc/fstab es incorrecta 
diego@diego-desktop:~$

Mi fstab quedó asi despues de agregar esa linea que me indicaste.

# /etc/fstab: static file system information. 
# 
# Use 'blkid -o value -s UUID' to print the universally unique identifier 
# for a device; this may be used with UUID= as a more robust way to name 
# devices that works even if disks are added and removed. See fstab(5). 
# 
# <file system> <mount point>   <type>  <options>       <dump>  <pass> 
proc            /proc           proc    nodev,noexec,nosuid 0       0 
# / was on /dev/sda5 during installation 
UUID=0d482139-fb6c-46ba-9e39-dc85878901eb /               ext4    errors=remount-ro 0       1 
# swap was on /dev/sda6 during installation 
UUID=f5c83fd8-b516-43df-9f33-4b75f2c275c6 none            swap    sw              0       0 
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0 

//diservel01/publica/Z /mnt/compartida smbfs guest,uid=1000,iocharset=utf8,codepage=unicode,uni code 0 0

---

### Post by gmunioz on 2010-11-25
prueba con esta línea:

//diservel01/publica/Z  /mnt/compartida  cifs  defaults,guest 0 0

---

### Post by diego_diaz on 2010-11-29
Hola, probé con esa linea y la respuesta fue esta.

diego@diego-desktop:~$ sudo gedit /etc/fstab
[sudo] password for diego: 

** (gedit:1580): CRITICAL **: gedit_spell_checker_language_to_key: assertion `lang != NULL' failed
diego@diego-desktop:~$ sudo mount -a
mount error: could not resolve address for diservel01: No address associated with hostname
diego@diego-desktop:~$

---

### Post by gmunioz on 2010-11-29
Pues ahora, la líneas esta correcta, pero el recurso
no aparece:

mount error: could not resolve address for diservel01: No address associated with hostname

Prueba cambiar el nombre por la IP que le corresponde

para que quede por ejemplo asi:


//192.168.1.33/publica/Z /mnt/compartida cifs defaults,guest 0 0
__________________

---

### Post by diego_diaz on 2010-11-30
Pongo la IP en la linea y el terminal me tira esto;

diego@diego-desktop:~$ sudo mount -a 
mount error(101): Network is unreachable 
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs) 
diego@diego-desktop:~$

Pero paso a explicarte algo que no sabia hasta hoy, la carpeta que quiero montar se encuentra en una maquina con SO Debian que es el servidor principal, hay otro servidor con windows para impresoras,que a su vez tiene montada la carpeta de la PC con Debian, Mi PC con Ubuntu y a travez de Nautilus entra a esta carpeta, pero lo hace a travez del servidor para impresoras con windows.
Ahora una nueva pregunta, como puedo conectarme al servidor con Debian?

Saludos.

Desde ya te agradezco la ayuda que me estas brindando, es muy importante que pueda hacer esto ya que si lo logro migramos toda la oficina a Ubuntu.

---

### Post by gmunioz on 2010-11-30
Se parte de la base que red esta compuesta por 2 equipos:

    * Un servidor con Debian
    * Un cliente con Ubuntu

Que utilizan direcciones de red reservadas (no utilizables en Internet) de clase C (192.168.x.x).

Las máquinas se identifican como:

    * Debian -> 192.168.1.1 (Servidor)
    * Ubuntu -> 192.168.1.2 (Cliente)

El grupo de trabajo es grouplinux

La dirección de red, es la 192.168.1.0
La dirección de "broadcast" 192.168.1.255
La máscara de subred 255.255.255.0

La red ya fue configurada y se encuentra funcionando.

El usuario ubuntu es ubuser y pertenece al grupo grouplinux

El directorio a compartir que se encuentra en la máquina 
Debian es /home/comun

Se necesita tener instalados los siguientes paquetes:

samba  smbclient samba-common smbfs system-config-samba

Configuración:

Alta de usuario.

Las cuentas entre el servidor y los clientes deben estar
sincronizadas. El usuario y su clave de una máquina cliente
con Ubuntu en el servidor samba Debian debe existir con ese nombre y esa clave. 
Los usuarios que acceden a samba no requieren acceso al interprete de comandos, por lo que no es necesario asignar clave de acceso con el mandato passwd.

Se debe definir /sbin/nologin o bien /bin/false como intérpete de comandos para la cuenta del usuario cliente

En consola del servidor Debian
su
useradd -s /sbin/nologin ubuser 
smbpasswd -a ubuser
touch /etc/libuser.conf

El archivo de configuración de Samba es /etc/samba/smb.conf

Es necesario el archivo /etc/samba/lmhost
Archivo lmhosts

Para resolver localmente los nombres NetBIOS se los asocia con direcciones IP correspondientes, esto se hace en el archivo /etc/samba/lmhosts.

su
nano /etc/samba/lmhosts

En donde encontraremos lo siguiente:

127.0.0.1       localhost

Se deben añadir los nombres asociados a la dirección IP que se tenga dentro de la red local, separados con un espacio de tabulador, quedando así:

127.0.0.1	localhost
192.168.1.1	Debian
192.168.1.2	Ubuntu

Archivo smb.conf.
Editar el archivo /etc/samba/smb.conf

su
nano /etc/samba/smb.conf

Dentro de este existe información de utilidad comentada con un #

Y ejemplos comentados con ;
El grupo de trabajo
workgroup permite asignar el grupo de trabajo deseado:

workgroup = grouplinux

Descripción del servidor
server string para hace un comentario breve del servidor.

server string = Servidor Samba %v en %L

Parámetros de seguridad.
security = user hace necesario ser dado de alta en el sistema para acceder a los archivos del directorio compartido requiriendose nombre de usuario y contraseña para acceder. Para el acceso irrestricto se utiliza security = SHARE, no aconsejable
 
security = user

hosts allow permite determinar la lista de control de acceso que definirá que máquinas o redes podrán acceder hacia el servidor:

hosts allow = 127.0.0.1 192.168.1.2

interfaces permite establecer desde que interfaces de red del sistema se escucharán peticiones. Samba no responderá a peticiones provenientes desde cualquier interfaz no especificada. Esto es útil cuando Samba se ejecuta en un servidor que sirve también de puerta de enlace para la red local, impidiendo se establezcan conexiones desde fuera de la red local.

interfaces = 192.168.1.254/24

Impresoras.

Las impresoras se comparten de modo predeterminado.

Si se permite acceder hacia la impresora como usuario invitado sin clave de acceso, basta con añadir public = Yes

[printers]         
comment = El comentario que guste.         
path = /var/spool/samba         
printable = Yes         
browseable = No         
writable = no         
printable = yes         
public = Yes

Windows 9x suele tener problemas para comunicarse con Samba para poder imprimir, para evitar estos problemas habría que agregar algunos parámetros que resolverán cualquier eventualidad:

[printers]         
comment = Impresoras.         
path = /var/spool/samba         
printable = Yes         
browseable = No         
writable = no         
printable = yes         
public = Yes         
print command = lpr -P %p -o raw %s -r         
lpq command = lpstat -o %p        
lprm command = cancel %p-%j

Compartir directorios

Este es un ejemplo que funciona en general:

Nombre del recurso a compartir 
[comun]  

Comentario acerca del recurso                 
comment = Directorio compartido  

Ruta completa del recurso         
path = /home/comun

Permitir o no el acceso como usuario invitado. El valor puede ser Yes o No.

guest ok = Yes

Otra forma de permitir el acceso como usuario invitado. El valor puede ser Yes o No.

public = Yes	

Permitir mostrar el recurso en las listas de recursos compartidos. El valor puede ser Yes o No.

browseable	= Yes

Permitir la escritura, es opuesto a read only. El valor puede ser Yes o No. «writable = Yes» es lo mismo que «read only = No».
"security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html
# in the samba-doc package for details.
;   security = user
writable = No
read-only = yes

usuarios o grupos que pueden acceder al recurso compartido. Los valores pueden ser nombres de usuarios separados por comas o bien nombres de grupo antecedidos por una @.
valid users = ubuser,@ubusers	

Define que permiso en el sistema tendrán los subdirectorios creados dentro del recurso.

directory mask  = 0755

Define que permiso en el sistema tendrán los nuevos archivos creados dentro del recurso.

create mask = 0644 	

Se permite en el ejemplo el acceso a cualquiera como recurso de solo lectura salvo para el usuario winuser. Todo directorio nuevo que sea creado en su interior tendrá permiso 755 y todo archivo que sea puesto en su interior tendrá permiso 644.


En el siguiente ejemplo se compartirá a través de Samba el recurso denominado comun, el cual está localizado en el directorio /home/comun del disco rígido del servidor. 
Se permitirá el acceso a cualquiera pero será un recurso de solo lectura salvo para los usuarios administrador y ubuser. Todo directorio nuevo que sea creado en su interior tendrá permiso 755 y todo fichero que sea puesto en su interior tendrá permiso 644.

[comun]
	comment = Directorio Compartido
	path = /home/comun
	guest ok = Yes
	read only = Yes
	write list = ubuser, administrador
	directory mask = 0755
	create mask = 0644

Ocultar y denegar acceso a archivos.

Se utiliza hide dot files para mantener ocultos los archivos de sistema que comienzan con un punto:

hide dot files = Yes  

Es necesario cambiar en smb.conf

local master = no
domain master = no

por

local master = yes
domain master = yes
preferred master = yes


Es necesario editar el archivo /etc/nsswitch.conf
su 
nano /etc/nsswitch.conf


Buscar la línea que dice

hosts: files mdns4_minimal [NOTFOUND=return] dns mdns4

Agrega wins antes de dns, para que quede asi

hosts: files mdns4_minimal [NOTFOUND=return] wins dns mdns4


Montar unidades de red.

Previo a editar el archivo /etc/fstab en Ubuntu, terminada la
configuración verificar desde el entorno de Gnome que incluye un módulo para Nautilus que permite acceder hacia los recursos compartidos a través de Samba sin necesidad de modificar cosa alguna en el sistema. Hacer clic en Servidores de red en el menú de Gnome.

Si esta todo bien y se accede al servidor sin problemas, editar
el archivo agregando la línea pero refiriendose al servidor Debian .

---

### Post by diego_diaz on 2010-11-30
Muchas gracias, voy a probar, despues te cuento como  me fue. De no poder avanzar voy a instalarle Ubuntu 10.04 a la PC con Devian e instalarle los paquetes necesarios para que funcione como servidor.

Muchas gracias una vez mas.

Un abrazo.

---

### Post by the dsc on 2011-01-05
Muchas gracias!

---

