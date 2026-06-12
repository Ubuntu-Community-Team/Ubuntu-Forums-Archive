---
title: "Escritorio &quot;remoto&quot;"
date: 2008-09-09
forum: Software
---

### Post by ramiro_md on 2008-09-09
Holas gente, resulta que hace unos dias mi hermana compro una notebook o laptop, ya me confunde esa definición. La cuestión es que me pareció interesante contectarme a su equipo mediante el servicio de escritorio remoto (vnc).
El problema es que por mas que haya configurado todo lo que vi, aun no puedo conectarme a su escritorio. Les comento un poco el tema de la "configuracion".

Preferencias > Escritorio remoto 
[LIST]
[*]permitir a otros usuarios ver mi escritorio
[*]permitir a otros usuarios controlar tu escritorio
[/LIST]
Luego en una consola tecleeo:
vncserver :1 -daniela -depth 16 -geometry 800x600

Lo cual me devuelve:
New 'daniela-laptop:1 (daniela)' desktop is daniela-laptop:1

Starting applications specified in /home/daniela/.vnc/xstartup
Log file is /home/daniela/.vnc/daniela-laptop:1.log

Yo crei que hasta ahi iba todo ok, pero al ir a una consola em mi computadora y teclear:
vncviewer daniela-laptop:1
me devuelve la siguiente linea:
Couldn't convert "daniela-laptop:1" to host adress.

Que estoy haciendo mal ?? esperom que alguien copado me conteste hehehe.Un saludo,

---

### Post by guillermolisi on 2008-09-09
> **ramiro_md said:**
> Holas gente, resulta que hace unos dias mi hermana compro una notebook o laptop, ya me confunde esa definición. La cuestión es que me pareció interesante contectarme a su equipo mediante el servicio de escritorio remoto (vnc).
El problema es que por mas que haya configurado todo lo que vi, aun no puedo conectarme a su escritorio. Les comento un poco el tema de la "configuracion".

Preferencias > Escritorio remoto 
[LIST]
[*]permitir a otros usuarios ver mi escritorio
[*]permitir a otros usuarios controlar tu escritorio
[/LIST]
Luego en una consola tecleeo:
vncserver :1 -daniela -depth 16 -geometry 800x600

Lo cual me devuelve:
New 'daniela-laptop:1 (daniela)' desktop is daniela-laptop:1

Starting applications specified in /home/daniela/.vnc/xstartup
Log file is /home/daniela/.vnc/daniela-laptop:1.log

Yo crei que hasta ahi iba todo ok, pero al ir a una consola em mi computadora y teclear:
vncviewer daniela-laptop:1
me devuelve la siguiente linea:
Couldn't convert "daniela-laptop:1" to host adress.

Que estoy haciendo mal ?? esperom que alguien copado me conteste hehehe.Un saludo,

Proba poniendo
```
vncviewer ip_address
```

donde ip_address es la direccion ip de la otra notebook.

Si queres utilizar nombres en lugar de direcciones IP tenes que editar y agregar las que uses en el archivo /etc/hosts, Por ejemplo
```
127.0.0.1 localhost
192.168.0.1 daniela-laptop
```

La linea que hace referencia a localhost debe existir siempre, no la tenes que agregar salvo que falte.

Recien con eso podes dejar de hacer referencia a la direccion IP y usar el nombre de la maquina cuando emitis el comando en consola.

---

### Post by ramiro_md on 2008-09-09
Guille gracias por el aporte, pero no va, me sigue tirando:
vncviewer: ConnectToTcpAddr: connect: Connection refused
Unable to connect to VNC server
Algo debo estar haciendo mal en la configuracion.

---

### Post by WanderingKnight on 2008-09-09
Fijate que tengas el puerto abierto en la máquina que escucha... Según leo por ahí VNC escucha en el 5901, en cuyo caso deberías hacer:

```
sudo iptables -A INPUT -p tcp --destination-port 5901 --source x.x.x.x -j ACCEPT
```

En el --source podés poner el nombre que le asignás a la IP en el /etc/hosts.

---

### Post by ramiro_md on 2008-09-09
No, el sistema de escritorio emoto usa el puerto 5900, y efectiovamente esta abierto para la ip de mi hermana en el router. 
De todos modos, corri el iptables con ambos puertos, pero no retorna nada =S

---

### Post by WanderingKnight on 2008-09-09
No "retorna"? A qué te referís con que no retorna?

iptables corre y obviamente no retorna nada porque lo único que hace es agregarle la regla a tu firewall. Lo que tenés que hacer ahora es intentar nuevamente a ver si te tira el mismo error.

---

### Post by ramiro_md on 2008-09-09
jeje grax, disculpa mi ignorancia, probe y me sigue saliendo:
vncviewer: ConnectToTcpAddr: connect: Connection refused
Unable to connect to VNC server

---

### Post by sergiom99 on 2008-09-09
yo lo uso asi:
```
vncviewer 192.168.1.55:4001
```
que seria = ip:_puerto_del_vnc (todo junto)

con esto me conecto a servidores uVNC en XP, W2k y W2k3.

---

### Post by ramiro_md on 2008-09-09
No, tampoco con el numero de puerto, ya no tengo ideas.

---

### Post by sergiom99 on 2008-09-09
del lado del server (es un ubuntu en la laptop?) queda logueado algo?
ese es un buen lugar para buscar.

---

### Post by ramiro_md on 2008-09-09
SI es una laptop sergio, usa hardy, tiene los puertos del router abiertos y la sesion esta iniciada. :confused:

---

### Post by guillermolisi on 2008-09-09
Revisando en el server que tengo en casa con Gnome vi que hay una opcion que posiblemente influya en la aceptacion de este tipo de conexiones.

Pego un screenshot para que veas cual es y pruebes.

Como es un server y accedo directamente a el sin necesidad de VNC y Remote Desktop, la opcion que mencionas en el menu Preferencias no la tengo.

Sí recuerdo haber visto algo en respecto de este problema en los servers del laburo que corren RedHat con Gnome (una version mas vieja que la de Ubuntu).
Mañana me fijo y la paso.

---

### Post by Mister X on 2008-09-10
Si no tenes nada en el medio filtrando paquetes (firewall, router), es muy sencilla la coneccion. Cuando tildas la opcion "Permitir a otros usuarios ver mi escritorio", lo que hace es levantar un servidor en el espacio de tu usuario (vino-server).

Para fijarte si esta corriendo ejecutá en la maquina remota:
```
ps -A|grep vino
```


Para conectarte desde tu maquina:

```
vncviewer <ip remota>
```

---

### Post by ramiro_md on 2008-09-10
Mister x, tengo un router, pero ya le abri el puerto 5900 de vino, y el tema del firewall lo arreglo, quiero creer, con unas lineas que se postearon unos comentarios antes. Un salute.

---

### Post by ramiro_md on 2008-09-24
Bueno, gente, pude hacer andar el escritorio remoto :). Pero, hay algo que no puedo hacer, no se si es limitación del servicio o porque hago algo mal yo, la cuestión es que no me deja copiar algo de mi maquina y pegarlo en la maquina remota ni viceversa :confused: eso realmente me serviria mucho, porque mi hermana tiene grabadora de dvd :) y yo no jejeje.
Si alguien conoce otra forma de compartir datos entre las dos computadoras le agradeceria mucho que lo posteara :).Un saludo.

---

### Post by sergiom99 on 2008-09-24
el UVNC para win tiene para transferir archivos, pero lo hace del alguna manera Xlenta. tal vez lo mas facil sea pasarlo por SCP, lo copias rapidisimo de una a otra en la misma LAN.

---

### Post by ramiro_md on 2008-09-24
A ver, estoy probando con SSH, lei que el SCP es una "opción" del SSH. La cuestión es que instalo el servidor (openssh-server) en la laptop de mi hermana, cuando desde mi computadora (desktop) intento ingresar a la laptop de mi hermana, tecleo en una terminal "*ssh daniela@ip*" o "*shh ip*" y de ambas formas me sale "*ssh: connect to host 192.168.1.102 port 22: Connection refused*" y eso que el puerto 22 lo tengo abierto en el router :(.
También probe con "*scp /home/ramiro/prueba.txt [email]daniela@ip:/home/daniela/prueba.txt[/email]*" y me sale algo parecido:
"[I]ssh: connect to host 192.168.1.102 port 22: Connection refused
lost connection[/I]"

NO estoy muy ducho en esto como podrán ver jejeje.

---

### Post by sergiom99 on 2008-09-25
te esta faltando aceptar conexiones en la laptop.
estoy a mil en el laburo (con Win) asi que esta noche si llego temprano a casa me fijo para pasarte instrucciones.
mientras, busca en google por ese lado, como dar permisos de ssh, etc.

---

### Post by ramiro_md on 2008-09-25
Gracias sergio, ahora ando  leyendo sobre "iptables", y ando jugando un poco con eso y el amule jejeje. Ahora que estoy un poco màs empapado en el tema voy a meter mano con el puerto ssh :). IGualmente cualquier ayuda es bien recibida. GRacias y unn saludo.

---

