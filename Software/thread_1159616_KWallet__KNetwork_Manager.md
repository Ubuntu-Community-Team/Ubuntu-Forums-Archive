---
title: "KWallet / KNetwork Manager"
date: 2009-05-14
forum: Software
---

### Post by benjamin_linux on 2009-05-14
Hola,

para variar quise probar Kubuntu y la verdad que ME ENAMORÉ. Más allá de algunas cositas que todavía me parecen raras y que me tengo que acostumbrar, me encontré con un solo problema:

Tras compilar madwifi (hasta ahora ninguna versión me detecta naturalmente mi placa Atheros), me conecto a mi red sin problemas, pero... si elijo que KWallet me guarde la contraseña, cada vez que inicio el sistema tengo que ingresar la contraseña. Y si desactivo KWallet, tras ingresar la información de la red me aparece una nueva ventana de seguridad en la que ponga lo que ponga (la contraseña) me da error y me dice que falla en la conexión, aunque algunas veces después de varios errores me conecta.

Después de googlear encontré dos opciones: desinstalar KWallet o cambiar por wicd. ¿Son las únicas posibilidades que tengo? ¿No hay manera de que KWallet no pida la contraseña cada vez que inicio, o no hay manera de que KNetwork Manager no me detecte fallos?

Gracias!!

---

### Post by guillermolisi on 2009-05-14
> **benjamin_linux said:**
> Hola,

para variar quise probar Kubuntu y la verdad que ME ENAMORÉ. Más allá de algunas cositas que todavía me parecen raras y que me tengo que acostumbrar, me encontré con un solo problema:

Tras compilar madwifi (hasta ahora ninguna versión me detecta naturalmente mi placa Atheros), me conecto a mi red sin problemas, pero... si elijo que KWallet me guarde la contraseña, cada vez que inicio el sistema tengo que ingresar la contraseña. Y si desactivo KWallet, tras ingresar la información de la red me aparece una nueva ventana de seguridad en la que ponga lo que ponga (la contraseña) me da error y me dice que falla en la conexión, aunque algunas veces después de varios errores me conecta.

Después de googlear encontré dos opciones: desinstalar KWallet o cambiar por wicd. ¿Son las únicas posibilidades que tengo? ¿No hay manera de que KWallet no pida la contraseña cada vez que inicio, o no hay manera de que KNetwork Manager no me detecte fallos?

Gracias!!
KWallet es para que ingreses una sola vez la contraseña maestra, la que te habilita como dueño de la "billetera/porta documentos" (wallet) y luego toma de ahi todas las password que tengas para cada programa.

KWallet hace eso y Wicd es para otra cosa que nada que ver, es un reemplazo del Network Manager.

Si Wicd te pide password para la conexion de red (suponiendo que tengas WiFi con seguridad, esta podria incluirse dentro de KWallet (digo podria porque depende de como este armada la aplicacion porque si no esta pensada en esa integracion no va a resultar asi y la verdad es que nunca probe esta combinacion).

KWallet [http://docs.kde.org/stable/es/kdeutils/kwallet/kwalletmanager.html](http://docs.kde.org/stable/es/kdeutils/kwallet/kwalletmanager.html)

---

### Post by benjamin_linux on 2009-05-14
Gracas y
Perdón si no me hice entender:

Ya sé que son dos cosas distintas, ocurre que si tengo activo KWallet -siempre- me pide la contraseña, al ingresar... Y si lo desactivo, KNetwork... me da un error, cuando intento conectarme.

Wicd ni lo tengo instalado, pasa que leí por ahí que recomiendan reemplazar KNet... por Wicd, así no da el mencionado error. (no soy al único que le pasó).

Disculpas de nuevo, leí mi post y parece que lo escribí "abatatado".

---

### Post by Benji86 on 2009-05-14
Mira, yo Kwallet lo uso, pero hasta donde me acuerdo, podes elegir que no guarde las claves y se ocupe la aplicacion en si que la va a usar (KNetworkManager en tu caso).
Es bastante util, quizas lo unico molesto que tiene kwallet es que te ocupa lugar en la systray (se puede cambiar) o si no le metes algo de mano a las opciones te pregunta mas de una vez las claves, pero puede quedar totalmente automatico y guarda de forma mas segura las claves

---

### Post by staar on 2009-05-14
es un problema que me pasó, pero con el gestor de gnome, y también le pasó hace un tiempito a alguien acá en el foro, la solución que le encontramos es cambiar el password maestro de kwallet, por uno en blanco, así no molesta más al iniciar...

saludos

---

### Post by emiliano_raso on 2009-05-15
A mi me ha pasado que tenia instalado tanto KDE3.5.10 y KDE4.x y tenia los Kwallet de ambas versiones y cuando desactivaba uno se activaba el otro xD
Finalmente termine desinstalandolós pero no tenía nada que me guarde las contraseñas :-S

---

### Post by dirty fingers on 2009-05-15
en el kubuntu 9.04 viene una version de KNetwork Manager que anda muy muy mal. no conecta a wpa y wpa2 . te sigue pidiendo la contraseña eternamente. por eso en todos los foros dicen de reemplazarlo por Wicd.

---

### Post by benjamin_linux on 2009-05-15
Perdón por la pregunta staar, pero cómo puedo cambiar la contraseña para dejarla en blanco? Así evitaría sacar el KNetwork Manager, que cuando está KWallet me funciona bien... si no ahí sí, instalo wicd.

---

### Post by Hei Ku on 2009-05-15
Por que no configurar la conexion directamente en el archivo /etc/network/interfaces?
Que tipo de conexion es?

---

### Post by benjamin_linux on 2009-05-15
Wireless con mi router Linksys, tengo mi PC de escritorio conectada por cable y la laptop inalámbricamente.

Configurando manualmente /etc/network/interfaces me evito este embrollo de contraseñas y fallos?

---

### Post by Hei Ku on 2009-05-15
sip. Que tipo de conexion es?

Depende del tipo de seguridad, te puedo pasar como lo tengo armado yo en mi notebook. Pero ahi esta configurada para conectarse apenas arranca a la conexion WEP del router, tambien un linksys.

---

### Post by benjamin_linux on 2009-05-15
Recién termino de cenar :D.
Te copio el el ifconfig, a ver si con eso podés decirme:

```
seretur@dendro:~$ ifconfig
eth0      Link encap:Ethernet  direcciónHW 00:1b:24:fa:52:9a  
          ARRIBA DIFUSIÓN MULTICAST  MTU:1500  Métrica:1      
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0  
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000                        
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)              
          Interrupción:252 Dirección base: 0xc000

lo        Link encap:Bucle local
          inet dirección:127.0.0.1  Máscara:255.0.0.0
          dirección inet6: ::1/128 Alcance:Anfitrión
          ARRIBA LOOPBACK CORRIENDO  MTU:16436  Métrica:1
          RX packets:32 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:0
          RX bytes:1800 (1.8 KB)  TX bytes:1800 (1.8 KB)

wlan0     Link encap:Ethernet  direcciónHW 00:1f:3a:02:c8:ef
          inet dirección:192.168.1.101  Difusión:192.168.1.255  Máscara:255.255.255.0
          dirección inet6: fe80::21f:3aff:fe02:c8ef/64 Alcance:Vínculo
          ARRIBA DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Métrica:1
          RX packets:10049 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5511 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000
          RX bytes:9758138 (9.7 MB)  TX bytes:734049 (734.0 KB)

wmaster0  Link encap:UNSPEC  direcciónHW 00-1F-3A-02-C8-EF-38-65-00-00-00-00-00-00-00-00
          ARRIBA DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Métrica:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

seretur@dendro:~$
```

Gracias!

---

### Post by staar on 2009-05-15
> **benjamin_linux said:**
> Perdón por la pregunta staar, pero cómo puedo cambiar la contraseña para dejarla en blanco? Así evitaría sacar el KNetwork Manager, que cuando está KWallet me funciona bien... si no ahí sí, instalo wicd.

creo que era: abrir kwallet, archivo > cambiar contraseña :-P :-D

saludos

---

### Post by benjamin_linux on 2009-05-15
Ehhh.........................................................

Hecho, gracias. Se conecta automáticamente y no me pide el pass... La verdad que era complicado jaja, pero la verdad que no había visto en ningún lugar que si dejabas en blanco la contraseña dejaba de pedírtela.

Muchíiiiiiiiiiiiiiisimas gracias!

---

### Post by Benji86 on 2009-05-15
La otra era que fueras a Preferencias del sistema -> Preferencias de red y de ahi la configurases. Yo hice asi y puse el plasmoid de la red en el sistray solo de curioso :)

---

### Post by Edfran on 2010-07-22
Para los que an tenido problemas conectándose a wpa y wpa2 en Knetwork manager la solucion es muy simple en el usuario deben escribir:  [SIZE=4]**dominio\Usuario**[/SIZE] ese es todo el problema para conectarse a ese tipo de redes

---

