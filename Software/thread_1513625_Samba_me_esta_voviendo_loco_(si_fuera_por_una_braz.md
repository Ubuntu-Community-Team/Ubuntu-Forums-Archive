---
title: "Samba me esta voviendo loco (si fuera por una brazuca vaya y pase )"
date: 2010-06-19
forum: Software
---

### Post by bronto64 on 2010-06-19
Hola gente, mi problema es el siguiente, tengo en casa una red inalambrica con dos maquinas con ubuntu lucid y tres con win2, quiero compartir desde mi maquina (ubuntu) a las otras las fotos, musica y películas que tengo almacenadas para que mis hijos tengan acceso, puedan guardar sus cosas y mirar pelis sin tener información redundante en las maquinas. Hasta acá la situación, y ahora el bolonqui, he leido/instalado/desinstalado/configurado samba y sus amigos y utilidades (swat, gadminsamba y otros) y no doy pie con bola. tengo configurados en la maquina los mismos usuarios que en la red pero por alguna razon siempre algo no funciona. Podría alguien darme una mano?
Gracias
Federico

---

### Post by alfplayer on 2010-06-20
En un tema de hace unas semanas yo explico cómo compartir con Samba. Podés buscar ese tema (está también en el foro de Argentina Team).

---

### Post by bronto64 on 2010-06-25
Gracias buscare y pondre en practica lo que diga el tuto a ver como me va.
Federico.

---

### Post by alfplayer on 2010-06-26
> **guillermon said:**
> Hola , aprovecho el post para hacer una pregunta sobre samba. Yo tengo dos pc en mi casa, ambas con ubuntu solamente, acceden a internet con un router inalámbrico linksys. En la nueva, donde la conexión a internet funciona muy bien (he hecho descagas de más de 300 kb/s), cuando he compartido carpetas, e instalando el servicio de samba, así por defecto cuando copio archivos no supera la velocidad de 60 KiB/s. Algo no está bien y no sé qué es (ni me imagino por dónde empezar). las búsquedas que he hecho no me han orientado. Pido disculpas si la respuesta es obvia o está en otro post. desde ya gracias...

Es para nuevo thread.

---

### Post by guillermolisi on 2010-06-26
> **alfplayer said:**
> Es para nuevo thread.
Abierto [aqui]("http://ubuntuforums.org/showthread.php?t=1518393")

---

### Post by bronto64 on 2010-06-27
Bueno, de verdad no se ya que mas hacer, hago todo lo que dice el tuto, me baje el faq de la pagina de samba, y nada , el error es no puedo descargar la lista del servidor. Cuando voy a compartir carpetas no me deja tildar arriba donde dice compartir archivos me dice que faltan instalar paquetes, no se cuales ya que instale samba, openssh, y nfs que mas debo hacer, ayuda por favor si no puedo resolver esto debere volver a win2, la red de mi casa la usan mis hijos y si no puedo compartir archivos no me sirve para nada linux :(
Fede.
Si sugieren desisntalar todo me dicen que , estoy mas perdido que turco en la neblina.

---

### Post by guillermolisi on 2010-06-27
Empezaria por ver el contenido del /etc/samba/smb.conf asi que si podes, mostranoslo aqui.

---

### Post by bronto64 on 2010-06-27
[global]
    netbios name = Samba24
    server string = Samba file and print server
    workgroup = brontos
    security = share
    hosts allow = 127. 192.168.0. 30.30.30.
    interfaces = 127.0.0.1/8 192.168.0.0/24 30.30.30.
    bind interfaces only = yes
    remote announce = 192.168.0.255 30.30.30.
    remote browse sync = 192.168.0.255 30.30.30.
    printcap name = cups
;    load printers = yes
    cups options = raw
    guest account = smbguest
    log file = /var/log/samba/samba.log
    max log size = 1000
    null passwords = yes
    username level = 6
    password level = 6
    encrypt passwords = no
    unix password sync = yes
    socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
    local master = no
    domain master = no
    os level = 33
    logon drive = m:
    logon home = \\%L\homes\%u
    logon path = \\%L\profiles\%u
    logon script = %G.bat
    name resolve order = wins lmhosts bcast
    dns proxy = no
    client use spnego = no
    client signing = no
    client schannel = no
    server schannel = no
    allow trusted domains = no
    obey pam restrictions = yes
    enable spoolss = yes
    follow symlinks = no
    update encrypted = yes
    passwd chat timeout = 120
    passwd program = /usr/bin/passwd '%u'
    passwd chat = *New*password* %n\n *ReType*new*password* %n\n *passwd*changed*\n
    add user script = /usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null '%u'
    add user to group script = /usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null -g '%g' '%u'
    add group script = /usr/sbin/groupadd '%g'
    delete user script = /usr/sbin/userdel '%u'
    delete user from group script = /usr/sbin/userdel '%u' '%g'
    delete group script = /usr/sbin/groupdel '%g'
    add machine script = /usr/sbin/useradd -d /dev/null -g sambamachines -c 'Samba Machine Account' -s /dev/null -M '%u'
    machine password timeout = 120
    idmap uid = 16777216-33554431
    idmap gid = 16777216-33554431
    template shell = /dev/null
    winbind use default domain = yes
    winbind separator = @
    winbind cache time = 360
    winbind trusted domains only = yes
    winbind nested groups = no
    winbind nss info = no
    guest ok = yes

[homes]
    comment = Home Directories
    path = /home
    read only = no
;    available = yes
;    browseable = yes
    guest ok = yes
;    printable = no
    locking = no
    strict locking = no

[netlogon]
    comment = Network Logon Service
    path = /home/netlogon
    read only = no
;    available = yes
;    browseable = yes
;    guest ok = no
;    printable = no
    locking = no
    strict locking = no

[profiles]
    comment = User Profiles
    path = /var/samba/profiles
    read only = no
;    available = yes
    browseable = no
;    guest ok = no
;    printable = no
    create mode = 0600
    directory mask = 0700
    locking = no
    strict locking = no

[printers]
    comment = All Printers
    path = /var/spool/samba
;    browseable = yes
;    writable = No
    guest ok = yes
    printable = yes
    locking = no
    strict locking = no

[pdf-documents]
    path = /home/pdf-documents
    comment = Converted PDF Documents
;    available = yes
;    browseable = yes
    writeable = yes
    guest ok = yes
    locking = no
    strict locking = no

[pdf-printer]
    path = /tmp
    comment = PDF Printer Service
    printable = yes
    guest ok = yes
    use client driver = yes
    printing = bsd
    print command = /usr/bin/gadmin-samba-pdf %s %u
    lpq command = 
    lprm command = 

[fotos]
    path = /media/multimedia/fotos
    writeable = yes
;    browseable = yes
    guest ok = yes

[musica]
    path = /media/multimedia/musica
    writeable = yes
;    browseable = yes
    guest ok = yes

[peliculas]
    path = /media/multimedia/peliculas
    writeable = yes
;    browseable = yes
    guest ok = yes




El volumen media es un ntfs , el grupo es brontos y la red interna es 30.30.30. Si necesitas mas datos solo decime, desde ya gracias por la onda y la ayuda.

---

### Post by guillermolisi on 2010-06-27
Decis que tenes una LAN interna en el bloque 30.30.30 o estoy interpretando mal ?
Para mi la LAN que estas usando esta en el bloque 192.168.0.
Algo que hice para no tener problemas con los nombres de Netbios es agregar una entrada por maquina en /etc/hosts y en cada maquina Windows, asi cuando referencias a una maquina/recurso tiene una forma rapida de resolver el nombre.

Un buen libro de cabecera sobre Samba lo podes encontrar [aqui]("http://guillermolisi.com.ar/?q=node/13").

---

### Post by bronto64 on 2010-06-27
Si la interna es 30.30.30. y esta esta conectada al modem adsl que tiene 192.168.1., gracias por el enlace. voy a probar dejando solo la interna, de todos modos el router es el unico que deberia ver el modem no?.

---

### Post by bronto64 on 2010-07-02
Bueno despues de haber leido parte del libro (es como para administradores de red) y modificado todo tal cual ahi, no puedo ver ni conectar las otras maquinas, ellas me ven pero no pueden acceder a nada. He notado que no tengo el icono de samba en sistema solo puedo entrar con el gadmin para configurar. Probe con la consola, pero cuando llego a la parte de reiniciar samba desde init.d me dice que el comando no existe. Evidentemente hay algo que no estoy haciendo bien, pero no me doy cuenta que es.](*,) 
Podrian decirme como desisnstalo e instalo completamente todo y comenzar de nuevo (si ese fuera un buen comienzo) o en todo caso donde debo comenzar a mirar. No puedo creer que no pueda con esto, he trabajado en soporte muchos años y tengo el primer año del ccna hecho, pero esto me esta poniendo a la altura de un noob absoluto y me resisto a la idea de armar una particion win2 para jugar y compartir archivos (se supone que este ES el so por excelencia para las redes no? )
Gracias de antemano.
Federico.

---

### Post by bronto64 on 2010-07-03
Bueno, de a poco va queriendo, las maquinas de mis hijos ya pueden ver las unidades que comparto y usarlas, no pude todavía hacer que vean la impresora y sigo sin verlos a ellos (fallo en la lista de compartición del servidor) es el mensaje que me aparece en cuanto quiero explorar la red ( me aparece hasta el grupo de trabajo, de ahí en mas el mensaje)
Algún tip para ir toqueteando?
Desde ya gracias.
Federico.

---

### Post by guillermolisi on 2010-07-03
> **bronto64 said:**
> Bueno, de a poco va queriendo, las maquinas de mis hijos ya pueden ver las unidades que comparto y usarlas, no pude todavía hacer que vean la impresora y sigo sin verlos a ellos (fallo en la lista de compartición del servidor) es el mensaje que me aparece en cuanto quiero explorar la red ( me aparece hasta el grupo de trabajo, de ahí en mas el mensaje)
Algún tip para ir toqueteando?
Desde ya gracias.
Federico.
Si las PCs Win tienen IP fija, agrega en /etc/hosts la lista de IPs y nombres de esas PCs para que aparezcan cuando nevegas la LAN (salvo que tengas un DNS interno).

---

### Post by bronto64 on 2010-07-03
Las pc win tiene ip dinamica, voy a ver si las cambio y agrego al hosts. Si no funciona que debo hacer cuando son dinamicas? 
Federico.

---

### Post by guillermolisi on 2010-07-04
> **bronto64 said:**
> Las pc win tiene ip dinamica, voy a ver si las cambio y agrego al hosts. Si no funciona que debo hacer cuando son dinamicas? 
Federico.
Si son dinamicas lo unico que conozco es configurar el servicio DHCP para que asigne las mismas direcciones IP a las mismas maquinas (MAC address) siempre y ahi podes implementar la resolucion de nombres via /etc/hosts, o configurar un DNS interno que resuelva en conjunto con el DHCP.

---

