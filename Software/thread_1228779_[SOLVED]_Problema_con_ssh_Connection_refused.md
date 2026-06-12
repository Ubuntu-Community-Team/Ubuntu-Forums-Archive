---
title: "[SOLVED] Problema con ssh Connection refused"
date: 2009-08-01
forum: Software
---

### Post by totolinux on 2009-08-01
Hola: Mi problema es el siguiente
tengo dos pc's conectadas con un cable cruzado, las dos se pueden ver, 
la primera kubuntu 9.04 y la segunda ubuntu 9.04 en modo texto (proyecto de mediacenter que le falta teclado, ratón y monitor). mi idea era conectarme por ssh y hacer toda la instalación del software desde la 1º pc servidora. Aclaro que tengo firestarter en la servidora con el puerto 22 habilitado para ssh.
el error es este:

root@diego-desktop:~# ssh 192.168.0.2

ssh: connect to host 192.168.0.2 port 22: Connection refused

encontré el mismo error en otros lados pero no se nada de ingles gracias.

---

### Post by Mauro22 on 2009-08-01
trataste con:


```
ssh usuario@host
```

Y proba al reves, de esa pc a la otra.


Si te da refused es porque o no tenes permiso (ejecuta con sudo) o esta ocupado (chequea que no haya dos queriendo usar el mismo puerto.

---

### Post by totolinux on 2009-08-01
Que foro este, al ratito nomas hay ayuda 
aca esta el resultado

root@diego-desktop:~# ssh mediacenter@192.168.0.2

ssh: connect to host 192.168.0.2 port 22: Connection refused
 
igual che pero de la otra no puedo porque no tiene monitor nada de nada

---

### Post by Mauro22 on 2009-08-01
Probaste con sudo?? 

El ping te responde??

El iptables esta configurado para el 22 para entrada y salida?? sea UDP y TCP??

---

### Post by W4l0ck on 2009-08-01
Looks like the server denied your request.

---

### Post by W4l0ck on 2009-08-01
Try a different port

---

### Post by totolinux on 2009-08-01
> **Mauro22 said:**
> Probaste con sudo?? 

El ping te responde??

El iptables esta configurado para el 22 para entrada y salida?? sea UDP y TCP??

1 si con sudo es igual
2 el ping  ok
3 en firestarter: normativa para el trafico saliente>permisivo por omisión,  tráfico en lista negra

---

### Post by totolinux on 2009-08-01
> **W4l0ck said:**
> Looks like the server denied your request.

Gracias por tu ayuda, pero no hablo Inglés

---

### Post by marianom on 2009-08-01
Dispensarás si te pregunto algo tan evidente... pero tenés instalado el openssh-server en tu servidor no?
De ser así, ¿qué dice /etc/ssh/sshd_config?

---

### Post by totolinux on 2009-08-01
openssh-server ya está en su versión más reciente


> **marianom said:**
> Dispensarás si te pregunto algo tan evidente... pero tenés instalado el openssh-server en tu servidor no?
De ser así, ¿qué dice /etc/ssh/sshd_config?

# Package generated configuration file
# See the sshd(8) manpage for details

# What ports, IPs and protocols we listen for
Port 22
# Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress ::
#ListenAddress 0.0.0.0
Protocol 2
# HostKeys for protocol version 2
HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key
#Privilege Separation is turned on for security
UsePrivilegeSeparation yes

# Lifetime and size of ephemeral version 1 server key
KeyRegenerationInterval 3600
ServerKeyBits 768

# Logging
SyslogFacility AUTH
LogLevel INFO

# Authentication:
LoginGraceTime 120
PermitRootLogin yes
StrictModes yes

RSAAuthentication yes
PubkeyAuthentication yes
#AuthorizedKeysFile	%h/.ssh/authorized_keys

# Don't read the user's ~/.rhosts and ~/.shosts files
IgnoreRhosts yes
# For this to work you will also need host keys in /etc/ssh_known_hosts
RhostsRSAAuthentication no
# similar for protocol version 2
HostbasedAuthentication no
# Uncomment if you don't trust ~/.ssh/known_hosts for RhostsRSAAuthentication
#IgnoreUserKnownHosts yes

# To enable empty passwords, change to yes (NOT RECOMMENDED)
PermitEmptyPasswords no

# Change to yes to enable challenge-response passwords (beware issues with
# some PAM modules and threads)
ChallengeResponseAuthentication no

# Change to no to disable tunnelled clear text passwords
#PasswordAuthentication yes

# Kerberos options
#KerberosAuthentication no
#KerberosGetAFSToken no
#KerberosOrLocalPasswd yes
#KerberosTicketCleanup yes

# GSSAPI options
#GSSAPIAuthentication no
#GSSAPICleanupCredentials yes

X11Forwarding yes
X11DisplayOffset 10
PrintMotd no
PrintLastLog yes
TCPKeepAlive yes
#UseLogin no

#MaxStartups 10:30:60
#Banner /etc/issue.net

# Allow client to pass locale environment variables
AcceptEnv LANG LC_*

Subsystem sftp /usr/lib/openssh/sftp-server

UsePAM yes

---

### Post by marianom on 2009-08-01
Algo no me cierra: decís que tenes firestarter configurado pero firestarter -si no me equivoco- es una GUI para iptables. Si tu servidor no tiene ni siquiera monitor no entiendo como pudiste configurarlo.

Agradecería una aclaración al respecto para desburrarme (yo hago todo con iptables directamente por línea de comandos).

---

### Post by totolinux on 2009-08-01
si mira: 
mi primer máquina (servidor) esta completita  de periféricos con kubuntu 9.04 y firestarter tiene 2 placas de red una con internet "eth1" y la otra "eth0" a una vieja pc con ubuntu 9.04 modo texto recién instalado.
yo trato de acceder a la pc2 (la viejita) desde el servido pc1 a través de ssh.
gracias de antemano por tu interés
preguntame sino entendés.

---

### Post by marianom on 2009-08-01
> **totolinux said:**
> si mira: 
mi primer máquina (servidor) esta completita  de periféricos con kubuntu 9.04 y firestarter tiene 2 placas de red una con internet "eth1" y la otra "eth0" a una vieja pc con ubuntu 9.04 modo texto recién instalado.
yo trato de acceder a la pc2 (la viejita) desde el servido pc1 a través de ssh.
gracias de antemano por tu interés
preguntame sino entendés.

si, tengo un par de preguntas más :)
tu viejita va a ser las veces de servidor, en ella instalaste un ubuntu en modo texto (primera pregunta: ¿que significa eso? ¿que instalaste un ubuntu server?). Ahora bien, el ssh-server que te preguntaba antes tiene que estar en la viejita porque a ella vos te querés conectar, tu nueva pc solo tiene que tener ssh-client (disculpá si digo cosas evidentes pero quiero estar seguro que estamos hablando de lo mismo para poder ayudarte). Vos me dijiste que tenías el ssh-server pero como me mostraste el sshd_config y todo y decís que no tiene monitor me queda la duda.
Si instalaste el server en la viejita por defecto debería tener los puertos cerrados y vos deberías abrirlos con iptables (no con firestarter ya que como la máquina no tiene X Server instalado no podés usar una GUI).
Si tenés todo como te pregunto (máquina vieja con ssh server e iptables con puerto 22 abierto) y aún así no te podes conectar, creo que se me acabaron las ideas: deberías revisar el secure log en /var/log del servidor a ver que error tira.

---

### Post by totolinux on 2009-08-01
> **marianom said:**
> si, tengo un par de preguntas más :)
tu viejita va a ser las veces de servidor, en ella instalaste un ubuntu en modo texto (primera pregunta: ¿que significa eso? ¿que instalaste un ubuntu server?). Ahora bien, el ssh-server que te preguntaba antes tiene que estar en la viejita porque a ella vos te querés conectar, tu nueva pc solo tiene que tener ssh-client (disculpá si digo cosas evidentes pero quiero estar seguro que estamos hablando de lo mismo para poder ayudarte). Vos me dijiste que tenías el ssh-server pero como me mostraste el sshd_config y todo y decís que no tiene monitor me queda la duda.
Si instalaste el server en la viejita por defecto debería tener los puertos cerrados y vos deberías abrirlos con iptables (no con firestarter ya que como la máquina no tiene X Server instalado no podés usar una GUI).
Si tenés todo como te pregunto (máquina vieja con ssh server e iptables con puerto 22 abierto) y aún así no te podes conectar, creo que se me acabaron las ideas: deberías revisar el secure log en /var/log del servidor a ver que error tira.
1 la vieja tiene instalado en modo texto y desde un cd de ubuntu alternate
2 me quiero conectar desde la nueva a la vieja que esta peladita desde la instalación.
3 el sshd_config es de la nueva pc1
4 me parece que esto es demasiado para mi cerebro voy a tratar de poner un monitor y dejarme de *****.
esto arranco desde que quise hacer el mediacenter de forat [http://www.forat.info/category/vinocenter/](http://www.forat.info/category/vinocenter/)
el unico paso que se me complica es el de ssh nunca me pude conectar al otro pc  [http://www.forat.info/2008/11/25/vinocenter-vol5-comunicaciones-en-linux-ubuntu-alternate/](http://www.forat.info/2008/11/25/vinocenter-vol5-comunicaciones-en-linux-ubuntu-alternate/)
si estoy fuera del tarro contame

---

### Post by sergiom99 on 2009-08-01
otra cosa que podes probar es desactivar iptables/firestarter en la pc vieja (ssh-server) y ver si podes conectarte desde Kubuntu (ssh-client).
Si no tenes firewall habilitado y el ssh-server esta corriendo no deberias tener ningun problema, siempre y cuando pongas bien el usuario y contraseña ;-)

---

### Post by marianom on 2009-08-01
No, es fácil, en serio. no pierdas la paciencia que se aprende rápido y luego nunca se olvida.
El tema es que vos tenes que tener el ssh-server en tu máquina vieja porque sino no puede escuchar conexiones que le mande la nueva. Una vez instales ssh-server en la máquina vieja (me temo que le vas a tener que poner el monitor), el ssh te va a andar.
Adicionalmente yo no instalaría un alternate si quiero tener un servidor porque te va a instalar cosas que nunca en tu vida vas a usar en un servidor y te va a ocupar memoria al cuete. Yo instalaría un ubuntu server en la máquina vieja y arriba de eso le iría tirando el software que necesite para hacer lo que vos quieras.

---

### Post by staar on 2009-08-01
> **marianom said:**
> Adicionalmente yo no instalaría un alternate si quiero tener un servidor porque te va a instalar cosas que nunca en tu vida vas a usar en un servidor y te va a ocupar memoria al cuete. Yo instalaría un ubuntu server en la máquina vieja y arriba de eso le iría tirando el software que necesite para hacer lo que vos quieras.
una pequeña aclaración, el alternate puede instalar un sistema base de solo consola, que trae lo mínimo (desde jaunty, solo usando el 'Modo experto'), y, siendo que totolinux está armando un mediacenter (creo que lo aclaró en el primer post) me parece más adecuado, por el tema del kernel que trae la versión server...

saludos

---

### Post by totolinux on 2009-08-01
gracias por los consejos ahora voy a buscar un monitor que me presta un amigo y los voy a tener una al lado de la otra y voy a descargar el cd server asi arranco de nuevo.
mi única fin es aprender y ver peliculas:D
mañana arranco de nuevo y sigo el thread saludos..

---

### Post by marianom on 2009-08-01
> **staar said:**
> una pequeña aclaración, el alternate puede instalar un sistema base de solo consola, que trae lo mínimo (desde jaunty, solo usando el 'Modo experto'), y, siendo que totolinux está armando un mediacenter (creo que lo aclaró en el primer post) me parece más adecuado, por el tema del kernel que trae la versión server...

saludos

Te agradezco la corrección.

---

### Post by marianom on 2009-08-01
> **totolinux said:**
> mi única fin es aprender y ver peliculas:D

Entonces vas bien con la primera parte, que yo sepa esta es la única forma de aprenderlo :)

---

### Post by totolinux on 2009-08-04
Retomo el thread para contarles que he resuelto el problema.
en la pc 2 (viejita intento de mediacenter) Reinstale ubuntu alternate 9.04
sin entorno grafico.
luego 
$ sudo apt-get update
$ sudo apt-get upgrade
$ sudo apt-get install ssh

y luego en la pc1 en Konsole

diego@diego-desktop:~$ ssh media@192.168.0.2
media@192.168.0.2's password:               
Linux ubuntu 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.                   

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.                                                     

To access official Ubuntu documentation, please visit:
[http://help.ubuntu.com/](http://help.ubuntu.com/)                               
Last login: Tue Aug  4 11:21:19 2009                  
media@ubuntu:~$ 
siiiiiissisisisisisisi
 
en definitiva no se que fue lo que pasó pero funciona GRACIAS a TODOS (SOLVED) :D

---

### Post by sergiom99 on 2009-08-04
Me alegra q lo hayas resuelto. Ahora te dejo un tip para poder hacerle ssh a la pc sin necesidad de poner la clave:
En diego-desktop:
```

$ ssh-keygen -b 4096 -t rsa
(te va a pedir un passphrase, dejalo vacio apretando Enter)
$ ssh-copy-id media@192.168.0.2

```

Ahora con esto, solo poniendo ssh media@192.168.0.2 se conecta directamente.
(y si el nombre de usuario fuera el mismo, ni te hace falta aclararlo antes del @)

Otra cosa que yo hago es crear un alias en el .bashrc de esta manera:
```

alias media='ssh media@192.168.0.2'

```
Entonce solo usando la "orden" media, me conecta de una.

Suerte!
-Sergio

---

### Post by totolinux on 2009-08-05
muy bueno gracias colega de gran utilidad.. saludos

---

### Post by Brath-ga on 2009-12-02
Hola a tod@s.

Veo que controlais mucho de ssh y para mí es la primera vez que lo intento.

Paso a explicarme a ver si alguien me dice que hago mal.

Tengo un sobremesa y un netbook conectados mediante un cable ethernet, al hacer ping desde cada extremo se ven.

Instalé el paquete ssh en el sobremesa y si desde el netbook le hago un ssh puedo entrar en el sobremesa, pero si le hago ssh desde el sobremesa al netbook me da error : Connection refused lost connection.

Al poder acceder al sobremesa intento copiar ficheros al netbook con scp, pero me dice que no puede con el mismo error.

Al final logré conectarlos gráficamente con la opción "conectar con el servidor" a través de ssh, pero para copiar 31 GB me da solo una velocidad de 1.6 GB/seg y por lo tanto son 5 horas :-\"

No creo que tenga que instalar el paquete ssh completo en el netbook, o me equivoco?

---

### Post by marianom on 2009-12-02
A través de nautilus solo tenés un frontend a ssh que realiza los mismos pasos: si podes por nautilus, deberías poder por ssh normalmente: ¿algún parametro mal ingresado tal vez?

---

### Post by Brath-ga on 2009-12-03
Creo que no marianom.
Como ya expliqué, el problema surge al intentar acceder al netbook tanto si no especifico puerto con lo cual tendría que funcionar or el 22, como si modifico el puerto y se lo indico.

Es decir, puedo entrar en el sobremesa que hace de servidor, pero no me permite copiar los ficheros de este en el netbook.

---

### Post by Brath-ga on 2009-12-03
Os cuento los avances que tengo hecho.

Descubrí que la conexión iba lenta porque la hacía a traves de wifi.

Al desconectar la wifi en el netbook se perdía el ping.

Tengo en el sobremesa una tarjeta de red ethernet integrada en placa, una wirelees en PCI y otra tarjeta ethernet en PCI que es con la que quiero comunicarme con el netbook.

Al ejecutrar ifconfig -a, no logro ver la 2ª Ethernet:

xoan@pinki-fixo:~$ ifconfig -a
eth0      Link encap:Ethernet  direcciónHW 00:13:8f:d0:5a:bc  
          Direc. inet:192.168.0.12  Difus.:192.168.0.255  Másc:255.255.255.0
          Dirección inet6: fe80::213:8fff:fed0:5abc/64 Alcance:Enlace
          ACTIVO DIFUSIÓN FUNCIONANDO MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:3531 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:3106 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:3778535 (3.7 MB)  TX bytes:434801 (434.8 KB)
          Interrupción:36 Dirección base: 0xa000 

lo        Link encap:Bucle local  
          Direc. inet:127.0.0.1  Másc:255.0.0.0
          Dirección inet6: ::1/128 Alcance:Anfitrión
          ACTIVO LOOPBACK FUNCIONANDO  MTU:16436  Métrica:1
          Paquetes RX:156 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:156 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:0 
          Bytes RX:14520 (14.5 KB)  TX bytes:14520 (14.5 KB)

vboxnet0  Link encap:Ethernet  direcciónHW 0a:00:27:00:00:00  
          DIFUSIÓN MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:0 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:0 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  direcciónHW 00:13:f7:49:fe:fc  
          DIFUSIÓN MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:0 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:0 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  direcciónHW 00-13-F7-49-FE-FC-00-00-00-00-00-00-00-00-00-00  
          [NO FLAGS]  MTU:0  Métrica:1
          Paquetes RX:0 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:0 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:0 (0.0 B)  TX bytes:0 (0.0 B)

Sin embargo al ejecutar lspci | grep Ethernet si la veo

xoan@pinki-fixo:~$ lspci | grep Ethernet
00:09.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)
00:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)

Por favor, indicarme que debería hacer?

---

### Post by prof_pc666 on 2009-12-08
Hola, tengo el mismo problema. Ayer al configurar algunas cosas en el server, sin querer ejecuteCHMOD 777 /* en el raiz. Ya restaure los permisos en /usr/bin/sudo y /etc/sudoers, el server anda bien solo que no puedo entrar por ssh. Como hago para que ande de nuevo?

---

### Post by josh771 on 2012-03-27
Mira, lo que puedes hacer es dentro de tu servidor, al cual vas a acceder mediante ssh, verifica que el puerto de entrada del ssh sea el 22 y la ip de tu servidor tambien se encuentre alli. Todo esto dentro del archivo /etc/ssh/sshd.config.

Una vez hecho esto, reinicia el ssh, con el siguiente comando:

/etc/init.d/ssh restart

Y prueba de nuevo con un usuario diferente, por ejemplo:

ssh usuarionuevo@<ip_servidor>

Espero te haya servido de ayuda...

---

### Post by yefry on 2012-08-28
jejejej lo mas facil erra q en el server del ssh te vayas a /etc/hosts.deny y borres las ips que hay ahi o ingreses una ip en /etc/hosts.allow :D  Mi primer comentario en Ubuntu forums, Ubuntu Rules y que vivan los LTS :D

---

