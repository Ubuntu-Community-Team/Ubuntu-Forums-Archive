---
title: "LUBUNTU, compartir carpetas, SAMBA"
date: 2010-11-23
forum: Software
---

### Post by McPato on 2010-11-23
Hola, soy tan nuevo en Linux que estoy un poco desorientado.
Mi problema es que instale LUBUNTU 10.10 con el proposito de ver su funcionalidad. La idea es que consegui unas cuantas pc en desuso que se donaran a una escuela rural y quisiera intalar en ellas LUBUNTU.
Para experimentar lo hice en una maquina mia, una Pentium III con 640 MB, y debo reconocer que me encanta!!!
Pero tengo el siguiente problema: No se como hacer para acceder en una pequeña red local de maquinas que tienen XP, o Windows 2000, a las carpetas compartidas. Y si es posible ver los equipos del grupo de trabajo.
O por lo menos compartir una carpeta en una de esas maquinas y acceder desde LUBUNTU.
Las maquinas xp y win 2000 no tendrian restricciones raras, solo una carpeta publica con todos los derechos para modificar, eliminar, agregar archivos etc.
Las maquinas tienen ip dinamica.
Y no se que mas puedo decir para que les sirva de guia.
Intente instalar SAMBA, lo baje de la red, fui al File manager, hice doble click sobre el archivo bajado, me aparece una ventana cuyo titulo es, instalador de paquetes - samba.
Pero al iniciarse la instalacion aparece una ventana que dice: Dispone de la misma version en un canal de software. Se recomienda que instale el software desde el canal.
PERO NO SE COMO HACERLO!!!
Por favor... como diria la madre de plaza de mayo a los periodistas de aquella epoca: USTEDES SON MI UNICA ESPERANZA.. ASHUDENMEEEEE ASHUUUDENMEEEE...
Eso es para agregarle buena onda.
Gracias

---

### Post by gmunioz on 2010-11-24
Este es uno de los tantos procedimientos existentes para compartir archivos en una red de máquinas Linux y Windows
Se parte de la base que red esta compuesta por 2 equipos:
    * Un servidor, Linux
    * Una máquina con Windows
Que utilizan direcciones de red reservadas (no utilizables en Internet) de clase C (192.168.x.x).
Las máquinas se identifican como:
    * Ubuntu -> 192.168.1.1 (Máquina Linux)
    * Windows -> 192.168.1.2 (Máquina Windows)
El grupo de trabajo es winlinux
La dirección de red, es la 192.168.1.0
La dirección de "broadcast" 192.168.1.255
La máscara de subred 255.255.255.0
La red ya fue configurada y se encuentra funcionando.
El usuario windows es winuser y pertenece al grupo winlinux
El directorio a compartir que se encuentra en la máquina Linux es /home/comun
Se necesita tener instalados los siguientes paquetes:

samba  smbclient samba-common smbfs system-config-samba

Se instalan ejecutando en consola (terminal)
sudo su
apt-get update
apt-get install samba  smbclient samba-common smbfs system-config-samba

Configuración:
Alta de usuario.
Las cuentas entre el servidor Samba y las máquinas Windows deben estar sincronizadas. El usuario y su clave de una máquina con Windows en el servidor Samba debe existir con ese nombre y esa clave. Los usuarios que acceden a samba no requieren acceso al interprete de comandos, por lo que no es necesario asignar clave de acceso con el mandato passwd.
Se debe definir /sbin/nologin o bien /bin/false como intérpete de comandos para la cuenta del usuario Windows.
Ejecutando en consola (terminal)
sudo su
useradd -s /sbin/nologin winuser 
smbpasswd -a winusuer


El archivo de configuración de Samba es:
/etc/samba/smb.conf

Archivo lmhosts
Para resolver localmente los nombres NetBIOS se los asocia con direcciones IP correspondientes, esto se hace en el archivo /etc/samba/lmhosts.
Se edita ejecutando en consola (terminal)
sudo su 
nano /etc/samba/lmhosts

Enel se encuentra este contenido:

127.0.0.1       localhost

Se deben añadir los nombres asociados a la dirección IP que se tenga dentro de la red local, separados con un espacio de tabulador, quedando así:

127.0.0.1	localhost
192.168.1.1	Linux
192.168.1.2	Windows

Archivo smb.conf.
Para editar el archivo /etc/samba/smb.conf
se ejecuta en consola (terminal)
sudo su
nano /etc/samba/smb.conf

Dentro de este existe información de utilidad comentada con un #
Y ejemplos comentados con ;

El grupo de trabajo
workgroup permite asignar el grupo de trabajo deseado:

workgroup = winlinux

Descripción del servidor
server string para hace un comentario breve del servidor.

server string = Servidor Samba %v en %L

Parámetros de seguridad.
security = user hace necesario ser dado de alta en el sistema para acceder a los archivos del directorio compartido requiriendose nombre de usuario y contraseña para acceder. 
Para el acceso irrestricto se utiliza security = SHARE 

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

Se puede definir a un usuario o a un grupo (@winlinux) para la administración de las colas de las impresoras:

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
printer admin = winuser, @winlinux

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

valid users = winuser,@winusers	

Usuarios o grupos que pueden acceder con permiso de escritura. Los valores pueden ser nombres de usuarios separados por comas o bien nombres de grupo antecedidos por una @.

write list = winuser

Usuarios o grupos que pueden acceder con permisos administrativos para el recurso. Es decir, podrán acceder hacia el recurso realizando todas las operaciones como super-usuarios. Los valores pueden ser nombres de usuarios separados por comas o bien nombres de grupo antecedidos por una @.

admin users = winuser

Define que permiso en el sistema tendrán los subdirectorios creados dentro del recurso.

directory mask  = 0755

Define que permiso en el sistema tendrán los nuevos archivos creados dentro del recurso.

create mask = 0644 	

Se permite en el ejemplo el acceso a cualquiera como recurso de solo lectura salvo para el usuario winuser. Todo directorio nuevo que sea creado en su interior tendrá permiso 755 y todo archivo que sea puesto en su interior tendrá permiso 644.


En el siguiente ejemplo se compartirá a través de Samba el recurso denominado comun, el cual está localizado en el directorio /home/comun del disco duro. Se permitirá el acceso a cualquiera pero será un recurso de solo lectura salvo para los usuarios administrador y winuser. Todo directorio nuevo que sea creado en su interior tendrá permiso 755 y todo fichero que sea puesto en su interior tendrá permiso 644.

[comun]
	comment = Directorio Compartido
	path = /home/comun
	guest ok = Yes
	read only = Yes
	write list = winuser, administrador
	directory mask = 0755
	create mask = 0644

Ocultar y denegar acceso a archivos.

Se utiliza hide dot files para mantener ocultos los archivos de sistema que comienzan con un punto:

hide dot files = Yes  

Se utiliza veto files para especificar la lista, separada por diagonales, de aquellas cadenas de texto que denegarán el acceso a los archivos cuyos nombres contengan estas cadenas. Por ejemplo, denegar el acceso a los archivos cuyos nombres incluyan la palabra «Security» y a los que tengan extensión «.tmp»:

veto files = /*Security*/*.tmp/  

Cambiar 

local master = no
domain master = no

por

local master = yes
domain master = yes
preferred master = yes

Archivo /etc/nsswitch.conf
Editar el archivo /etc/nsswitch.conf

sudo su
nano /etc/nsswitch.conf

Buscar la línea que dice

hosts: files mdns4_minimal [NOTFOUND=return] dns mdns4

Agrega wins antes de dns, para que quede asi

hosts: files mdns4_minimal [NOTFOUND=return] wins dns mdns4

---

