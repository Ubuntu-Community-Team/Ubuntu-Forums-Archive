---
title: "Unir Ubuntu a Red Windows"
date: 2009-05-21
forum: Software
---

### Post by leavai on 2009-05-21
Hola a todos!!! este es mi primer post en el foro y ayer fue la primera vez que tuve contacto con un Ubuntu (en realidad es mi primer linux). Lo que estoy necesitando es poder ver las pc de mi red en windows con mi Ubuntu. Mi idea es sacar todos los windows, pero estoy en una fase de prueba, tengo unas 50 pc en la red y me interesaria que se vieran junto con el Ubuntu. Ayuda!!!!!!! si hay algun post que explique estos pasos desde cero se los agradeceria, yo no lo encontre. 
 
Gracias a todos y espero puedan ayudarme para erradicar todos mis windows!!! ;)
 
 
Abrazo

---

### Post by Hei Ku on 2009-05-21
Cualquier proyecto de migracion es algo de cuidado, y sobre todo con tecnologia que te es nueva. Yo te recomendaria calma y paciencia (y un vocabulario educado ;) )

Acá tenés un tutorial basico de samba, que es lo que necesitas para compartir entre windows y linux.

[http://ubuntu-ar.org/tutoriales/samba](http://ubuntu-ar.org/tutoriales/samba)

---

### Post by leavai on 2009-05-21
Muchisimas gracias por la pronta respuesta, perdon por el vocabulario, estoy acostumbrado a otros foros, pero este es uno de verdad jeje, ya me pongo con lo que me pasate y te pregunto si tengo alguna duda.
 
Gracias

---

### Post by harryscode on 2009-05-21
Hola Leavai, fijate después de haber leido el art de Samba, este post, ya que me pasó lo mismo que a mucha gente con el 9.04, quizas a vos no te ocurre, pero me parece que es algo que puede suceder. Acá hay un fix para solucionar un problemita de "compatibilidad" por decirlo de algún modo (perdón pero no le encuentro otra explicación) y si te ocurre ya sabes donde fijarte.
[http://ubuntuforums.org/showthread.php?t=1135842](http://ubuntuforums.org/showthread.php?t=1135842)

---

### Post by leavai on 2009-05-26
Amigos, la instalacion del Samba fue un exito, puedo ver mis carpetas compartidas en ubuntu desde windows, pero lo que necesito es ver las carpetas que estan en windows desde ubuntu. Cuando voy a lugares->red, puedo ver mi red pero no me deja ingresar, como tengo que hacer?
 
Gracias!

---

### Post by pablo.s on 2009-05-26
> **leavai said:**
>  lo que necesito es ver las carpetas que estan en windows desde ubuntu. Cuando voy a lugares->red, puedo ver mi red pero no me deja ingresar, como tengo que hacer?
 
Gracias!

Las carpetas en Windows
también tienen que ser
compartidas. El dominio
tiene que tener el mismo
nombre.

---

### Post by leavai on 2009-05-27
> **pablo.s said:**
> Las carpetas en Windows
también tienen que ser
compartidas. El dominio
tiene que tener el mismo
nombre.
 
Ya estan compartidas y el nombre de dominio es el mismo.... algo me esta faltando, por ejemplo, no puedo configurar el samba, sera eso? le doy a configurar y no hace nada, ayuda!!!!

---

### Post by leavai on 2009-05-27
Ya pude ver las pc de mi dominio y acceder a sus carpetas!!!!!!! ahora estoy en la etapa de poder correr un archivo de DOS con el Dosemu. Por lo que estuve viendo tengo que colocar mi ejecutable en la carpeta drive_z, el tema es que necesito acceder a un archivo de mi red. Lo que hice fue ejecutar el archivo desde la red con el dosemu, pero cuando hago algun movimiento en el programa no encuentra los archivos que necesita.... que puedo hacer :( ?
 
Gracias a todos!

---

### Post by aledruetta on 2009-05-28
Hola,

Yo estoy intentando lo siguiente: quiero acceder sin restricciones a la partición C: del XP que tengo en la máquina virtual (VirtualBox 2.2.2) de Ubuntu Jaunty. Coloqué, en las propiedades de C:, la opción compartir con otros usuarios de la red, pero, cuando voy a Lugares-->Red y quiero abrir "Red de Windows", me sale un cuadro de diálogo que dice "No se pudo montar el lugar. Falló al obtener la lista de compartición del servidor".

---

### Post by gmunioz on 2009-05-29
Hola:

1- En principio es necesario que esten instalados:

```
samba samba-common smbclient winbind
```

2- Luego editar el archivo /etc/samba/smb.conf

```
sudo gedit /etc/samba/smb.conf
```

A los cambios necesarios para adaptar el sistema, segun los

tutoriales de samba es necesario tener presente que:

a- Donde dice workgroup = WORKGROUP, reemplazar WORKGROUP por el 

nombre de grupo de trabajo de los ordenadores que debe ser el mismo.

b- Borrar el ";" de la linea: 

name resolver order = lmhosts hosts wins bcast

3- Editar el archivo /etc/nsswitch.conf

```
sudo gedit /etc/nsswitch.conf
```

Buscar la linea que dice:

hosts: files mdns4_minimal [NOTFOUND=return] dns mdns4

Agregar wins antes de dns

para que la línea quede asi:

hosts: files mdns4_minimal [NOTFOUND=return] wins dns mdns4

Saludos.

---

### Post by aledruetta on 2009-06-01
Hola gmunioz,

Bueno, después de muchas horas, siguiendo tus consejos y algunas otras cosas que fui encontrando por ahí, estoy en la siguiente situación:

Tengo creada una red INICIOMS que aparece -en el XP virtualizado- en "Mis sitios de red"-->"Toda la red"-->"Red de Microsoft Windows"-->"Inicioms". Aquí adentro puedo ver la PC Win y la PC Ubuntu.

y también -en Ubuntu- en "Lugares"-->"Red"-->"Red de Windows"-->"INICIOMS". Aquí adentro, únicamente la carpeta compartida de Ubuntu. Y, a veces se monta y otras veces me responde que no se pudo montar porque falló la carga del servidor.

Hasta ahí llegué haciendo lo que vos me sugeriste, abriendo los puertos que indicaba en este post: [aquí]("http://www.mey-online.com.ar/blog/index.php/archives/reglas-de-firewall-para-samba") y desactivando el firewall en windows.

Pero, bueno, no consigo lo que me propongo que es tener acceso a la máquina windows desde ubuntu.

¿Se les ocurre algo más?

Esto es lo que devuelve el testparm:

```
Load smb config files from /etc/samba/smb.conf
Processing section "[printers]"
Processing section "[print$]"
Processing section "[Red]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
    workgroup = INICIOMS
    netbios name = PC_UBUNTU
    server string = %h server (Samba, Ubuntu)
    security = SHARE
    encrypt passwords = No
    map to guest = Bad User
    obey pam restrictions = Yes
    passdb backend = tdbsam
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    name resolve order = lmhosts host wins bcast
    dns proxy = No
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    browseable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers

[Red]
    path = /home/alejandro/Red
    guest ok = Yes

```

Saludos y muchas gracias,
Alejandro.

---

