---
title: "Duda con red local"
date: 2010-12-08
forum: Software
---

### Post by Fak89 on 2010-12-08
Como estan muchachos?
Se me presento un problema el cual me trajo una duda..
Como podría poner mi pc con ubuntu 10.04 en una red local de windows? vivo en una residencia, por lo tanto no tengo acceso a los servidores. En Win, basicamente tenía que cambiar el ipv4 por 192.168.1.algo y listo, estaba en la red, pero en ubuntu?
La otra duda es si "emulando" un juego con wine podría ver las partidas creadas en esta red?

Gracias gente!

---

### Post by gmunioz on 2010-12-09
Pulsando:
Con el botón derecho en el icono de red.
Seleccionando del menu emergente Editar las conexiones.....
En la ventana emergente seleccionando pestaña cableada
En la pestaña desplegada, la tarjeta seguramente Auto eth0
A la derecha seleccionando editar
En la nueva ventana emergente pestaña Ajustes IPv4
Abajo en método Manual
Seleccionando luego añadir
Poniendo los parámetros que corresponden
Pulsando Aplicar

La contraseña para desbloquear es la del usuario que
instaló el sistema.

---

### Post by Fak89 on 2010-12-09
> **gmunioz said:**
> Pulsando:
Con el botón derecho en el icono de red.
Seleccionando del menu emergente Editar las conexiones.....
En la ventana emergente seleccionando pestaña cableada
En la pestaña desplegada, la tarjeta seguramente Auto eth0
A la derecha seleccionando editar
En la nueva ventana emergente pestaña Ajustes IPv4
Abajo en método Manual
Seleccionando luego añadir
Poniendo los parámetros que corresponden
Pulsando Aplicar

La contraseña para desbloquear es la del usuario que
instaló el sistema.

Eso es lo que hice, pero cuando entro a red\red de windows me dice "Falló al obtener la lista de compartición del servidor"

---

### Post by granjero on 2010-12-09
hola, lo que te pasa a vos es que tenés red pero no ves las comparticiones de win? Fijate si en synaptic tenes instalados los siquientes paquetes...

smbclient
smbfs
samba
libsmbclient
samba-common
winbind

salud!

---

### Post by Fak89 on 2010-12-09
> **granjero said:**
> hola, lo que te pasa a vos es que tenés red pero no ves las comparticiones de win? Fijate si en synaptic tenes instalados los siquientes paquetes...

smbclient
smbfs
samba
libsmbclient
samba-common
winbind

salud!

Faltaban algunos, los instale pero sigue tirando el mismo cartel :/

---

### Post by juancarlospaco on 2010-12-09
Lugares--->Conectar con el servidor... --->Eleji arriba de todo "Compartido de Windows"--->IP de la otra PC--->Conectar

Wine no es un Emulador, pero si tiene conectividad Ethernet con IP.

---

### Post by Fak89 on 2010-12-09
> **juancarlospaco said:**
> Lugares--->Conectar con el servidor... --->Eleji arriba de todo "Compartido de Windows"--->IP de la otra PC--->Conectar

Wine no es un Emulador, pero si tiene conectividad Ethernet con IP.

Esta bien, pero eso me sirve para conectarme a una pc específica, lo que yo intento hacer es conectarme a la red y poder ver a todos los usuarios, como uno hace en windows..

---

### Post by Fak89 on 2010-12-09
> **juancarlospaco said:**
> Lugares--->Conectar con el servidor... --->Eleji arriba de todo "Compartido de Windows"--->IP de la otra PC--->Conectar

Wine no es un Emulador, pero si tiene conectividad Ethernet con IP.

Esta bien, pero eso me sirve para conectarme a una pc específica, lo que yo intento hacer es conectarme a la red y poder ver a todos los usuarios, como uno hace en windows..

---

### Post by hectorivand on 2010-12-10
> **Fak89 said:**
> Esta bien, pero eso me sirve para conectarme a una pc específica, lo que yo intento hacer es conectarme a la red y poder ver a todos los usuarios, como uno hace en windows..

Hola, entonces si tenes Samba y todos sus agregados instalados, cuando le das a Lugares > Red, te debería aparecer Red de Windows.

Eso no aparece?

Saludos
Nacho

---

### Post by gmunioz on 2010-12-10
1- Edita el archivo archivo lmhosts

Para resolver localmente los nombres NetBIOS se los asocia con direcciones IP correspondientes, esto se hace en el archivo /etc/samba/lmhosts, en una consola (Aplicaciones - Accesorios - Terminal) ejecutas

sudo gedit /etc/samba/lmhosts

En donde encontraras lo siguiente:

127.0.0.1       localhost

Se deben añadir los nombres asociados a la dirección IP que se tenga dentro de la red local, separados con un espacio de tabulador, quedando así:

127.0.0.1	localhost
192.168.1.1	nombre-de-tu-PC
192.168.1.2	Windows1
192.168.1.3	Windows2

donde a cada máquina de la red se la identifica por su nombre e IP

2- Edita el archivo smb.conf

En una consola (Aplicaciones - Accesorios - Terminal) ejecutas

sudo gedit /etc/samba/smb.conf

Dentro de este existe información de utilidad comentada con un # Y ejemplos comentados con ;

Debes establecer el grupo de trabajo al que pertenecen todas las máquinas

workgroup es el item permite asignar el grupo de trabajo deseado:

workgroup = el-grupo-de-trabajo

Se deben cambiar las líneas

local master = no
domain master = no

por

local master = yes
domain master = yes
preferred master = yes

3- Edita el archivo nsswitch.conf
En una consola (Aplicaciones - Accesorios - Terminal) ejecuta

sudo gedit /etc/nsswitch.conf

Busca la línea que dice

hosts: files mdns4_minimal [NOTFOUND=return] dns mdns4

Agrega wins antes de dns, para que quede asi

hosts: files mdns4_minimal [NOTFOUND=return] wins dns mdns4

Terminadas las configuraciones y reiniciado el sistema 

Nautilus debería ya permitir acceder hacia los recursos compartidos por los otros ordenadores a través de Samba

---

### Post by Fak89 on 2010-12-10
> **hectorivand said:**
> Hola, entonces si tenes Samba y todos sus agregados instalados, cuando le das a Lugares > Red, te debería aparecer Red de Windows.

Eso no aparece?

Saludos
Nacho

Aparece, antes igual. Pero me sigue dando el error ese que puse mas arriba.

> **gmunioz said:**
> 
local master = no
domain master = no

por

local master = yes
domain master = yes
preferred master = yes


Ahí edite, pero de estas lineas, la unica que tenía era "domain master" (que estaba en forma de comentario).

---

### Post by faktorqm on 2010-12-14
y si pones en el nautilus

```
smb:///direccion_IP/carpeta_compartida
```

tampoco? donde dice direccion_IP debes poner la direccion ip de la computadora con windows. y donde dice carpeta_compartida debes poner el nombre de como compartiste la carpeta en la red (no siempre son iguales) salu2!

---

### Post by Fak89 on 2010-12-14
> **faktorqm said:**
> y si pones en el nautilus

```
smb:///direccion_IP/carpeta_compartida
```tampoco? donde dice direccion_IP debes poner la direccion ip de la computadora con windows. y donde dice carpeta_compartida debes poner el nombre de como compartiste la carpeta en la red (no siempre son iguales) salu2!

Claro, el problema es que yo no se ni las IPs ni los nombres de las carpetas. Es una red, donde estan las computadoras de otros departamentos. No es una red que hice yo con otra computadora..
pd. aprobecho para darle las gracias a todos los que me vienen ayudando

---

