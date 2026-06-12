---
title: "Ayuda! no puedo navegar en internet"
date: 2009-08-23
forum: Software
---

### Post by superaldo on 2009-08-23
Saludos, y desde ya un gracias por la ayuda que me puedan brindar.

quisiera saber si es que existe una forma de reseter la configuracion de conexion a internet.

les explico mi problema, soy nuevo con el tema de ubuntu y la verdad que hasta ayer estuve mas que facinado con todo lo que tiene y lo que uno puede hacer, fue la semana en donde solo prendia mi pc para seguir aprendiendo mas y olvidarme de xp.

la cosa es que todo bien llegue a configurar y personalizar 'mi ubuntu a mi gusto' con los programas y funciones mas vistozas, todo una pasada verlo funcionar con los efectos y poder trabajar (trabajo con 3D usando autodesk Maya) .

el problema surgio cuando decidi compartir mi internet con mi laptop, esto lo hacia de lo mas facil con el xp solo le doy click derecho al dispositivo de red conectado (propiedades->permiter que otros equipos se conecten a este red) en fin la cosa que yo queria poder hacerlo tambien en ubuntu, encontre mucha informacion al respecto incluso unas que decia usando un programa que es un firewall para ubuntu, y mucha informacion de configuracion atravez de un Terminal y agregar lines de comando a ciertos archivos dentro del etc/
basicamente segui este tutorial
[http://ubuntuforums.org/showthread.php?t=91370](http://ubuntuforums.org/showthread.php?t=91370)
 
pero al final nada mi laptop se conecta se asigna un ip local (192.1.0.xxx) pero no salia a internet no navegaba, bueno hasta ahi me canse de intentar.
luego reinicie mi PC la que uso para trabajar y sorpreso ahora mi pc se conecta todo normal se asigna un IP pero no navega! ni nada ni me deja entrar al router 192.168.1.1 (se queda estancado tratando de entrar)

ya intente revertir los cambios que hice segun el tutorial pero igual sigo sin navegar.

por eso pregunto si hay alguna forma de reserter la configuracion de iptables o dns, o que se yo para volver a como estaba :(

---

### Post by Hei Ku on 2009-08-23
Podes postear tu archivo /etc/network/interfaces

Como te conectas a internet? Tenes la pc conectada a un router o directo al modem de tu ISP?

---

### Post by superaldo on 2009-08-23
Hola,

me conento a un router de forma inalambrica wireless o por cable aveces, (en ambos casos conecta y el DHCP del router me asiga un ip automaticamente) pero sigo sin navegar o usar otros programas como el xchat o emesene

tengo una wlan0 que uso para conectarme al router y tener internet casi siempre y tambien tengo una eth0 que pensaba usar para darle internet a otra pc pero al intentarlo se malogro todo :(

---

### Post by Hei Ku on 2009-08-23
Por postea tu archivo /etc/network/interfaces

Eso nos va a dar una idea de tu conexion.

---

### Post by superaldo on 2009-08-23
Hola, y gracias por responder, a continuacion lo que contiene mi /etc/network/interfaces


auto lo
iface lo inet loopback


:(

---

### Post by Hei Ku on 2009-08-23
Postea el resultado de ejecutar ifconfig en la terminal.

Que usas para configurar la conexion? El NetworkManager o algun otro?

---

### Post by superaldo on 2009-08-23
Hola y gracias! uso el wicd

[http://www.studioead.com/files/Pantallazo.gif](http://www.studioead.com/files/Pantallazo.gif)
[http://www.studioead.com/files/Pantallazo-1.gif](http://www.studioead.com/files/Pantallazo-1.gif)

Saludos
[ ]("http://www.studioead.com/files/Pantallazo-1.gif")

---

### Post by Hei Ku on 2009-08-23
Primero, en tu archivo /etc/network/interfaces

agrega estas lineas:

auto eth0
iface eth0 inet dhcp

Lo tenes que editar con sudo.

Podes hacer esto:
sudo nano /etc/network/interfaces

Agregar las lineas, y luego apretar Ctrl+x para salir, y apreta Y para confirmar que grabe los cambios.

Luego, pasame el contenido de /etc/resolv.conf

Parece que estas conectado, pero no tenes dns. Andá a las Preferencias de Wicd, tilda donde dice Usar DNS globales, y agregá estos dos:

208.67.222.222
208.67.220.220

---

### Post by guillermolisi on 2009-08-23
> **Hei Ku said:**
> Primero, en tu archivo /etc/network/interfaces

agrega estas lineas:

auto eth0
iface eth1 inet dhcp


Me parece que hay un error en esa indicacion. No es eth0 la interface que tiene que usar ?
Si es asi, entonces es "iface eth0 inet dhcp"

---

### Post by superaldo on 2009-08-23
Gracias, ahorita mismo pruebo, pero creo que guillermolisi tiene razon ya que no eth1 solo eth0 y una wlan0 (que es mi wireless con la que suelo conectarme al router para tener internet)
entonces pregunto antes de ir corriendo a mi ubuntu deveria editar mi /etc/network/interfaces
de esta forma?

auto wlan0
iface eth0 inet dhcp

o alrevez? y es agregar o remplazo lo que existe actualmente en mi /interfaces

y gracias por la ayuda :)

---

### Post by Hei Ku on 2009-08-23
Si, lo puse mal. Es que lo copie de mi config que esta en eth1.

Agregar la wlan0 no te va a hacer efecto, porque la parte de wireless la maneja wicd.

El texto correcto es:

auto eth0
iface eth0 inet dhcp

Y lo agregas al final, no reemplazas nada. Si tenes dudas, postea como quedo el archivo final.

---

### Post by superaldo on 2009-08-24
volvi!

ok al final mi archivo /etc/network/interfaces 
quedo asi:

auto lo
iface lo inet loopback
auto eth0
iface eth0 inet dhcp

salve los cambios y probe, agregue los dns a mi wicd pero igual sigue sin navegar, reinicie la pc y de nuevo me conecte atraves de wirelss, eh igual no navega :(
pero creo que si es muy posible que sean los dns

esto es lo que esta en mi /etc/resolv.conf
nameserver 200.48.225.130
nameserver 200.48.225.146

son los dns que estan dentro de mi router, antes de que pasaron todo esto me conectaba normal con wicd sin configurar ningun dns
pero cuando trate de configurar el comparti internet algo debi haber modificado algo en el dns :(

---

### Post by racerraul on 2009-08-24
Raro... parece que estas recibiendo un DHCP address sin problema...
Trata de anadir el gateway que debe de ser el address de el router a las lista de DNS.

debe de ser 192.168.1.254 o 192.168.1.1.

---

### Post by Hei Ku on 2009-08-24
Agregaste los dns en el wicd? Eso podría ayudar

---

### Post by meirzbi on 2009-08-24
hola el problema es conocido te mando la solucion 

   [LEFT]hola[/LEFT]
  [LEFT] [/LEFT]
  [LEFT]el problema es muy difundido en los distros ubuntu fedora linux mint y otros [/LEFT]
  [LEFT] [/LEFT]
  [LEFT]la solucion es muy simple cambia en cada pais de acuerdo al provedor de internet xdsl adsl dsl [/LEFT]
  [LEFT] [/LEFT]
  [LEFT]todos se conectan po medio de un router y cable en la tarjeta red [/LEFT]
  [LEFT] [/LEFT]
  [LEFT]por lo tanto nos conectamos con el router y no con fedora [/LEFT]
  [LEFT] [/LEFT]
  [LEFT]de acuerdo cada pais y tras consulta con el provedor de internet entramos en el router por ejemplo[/LEFT]
  [LEFT] [/LEFT]
  [LEFT].[http://10.0.0.138](http://10.0.0.138)[/LEFT]
  [LEFT] [/LEFT]
  [LEFT]y procedemos a definir nuestra cuenta usuario contrasena y activamos y cada vez que conectes el router [/LEFT]
  [LEFT] [/LEFT]
  [LEFT]estas en internet [/LEFT]
  [LEFT] [/LEFT]
  [LEFT]chau [/LEFT]
  [LEFT] [/LEFT]
  [LEFT]ricardo[/LEFT]

---

### Post by Hei Ku on 2009-08-24
Eso solo se aplica si fuera ADSL, que me parece que no es el caso.

---

### Post by superaldo on 2009-08-24
hola,

si ya intente poniendo los dns dentro de las preferencias del wicd, pero igual nada de navegar,
y si mi conexion a internet es tipo adsl de telefonica mi router es el que se conecta a internet logueandose y agarrando una ip publica
el problema no es el router porque ahorita estoy en xp conectado y normal, solo cuando paso a ubuntu conecta pero no navega! :(

---

### Post by anarko on 2009-08-24
Une pregunta, podes entrar a la conf. del router y verificar que este realmente conectado? 
Cuando arrancas el XP tenes que hacer algo para que conecte o esta siempre conectado el router?
Para sacarte la duda si son DNS o no pingea a una IP "conocida" 209.85.195.147 = [www.google.com](www.google.com), si te responde el ping son DNS, sino es otro el problema.

Puede que estes conecado a otro router que no sea el tuyo, ya que decis que conectas aveces por lan y aveces por wifi. Proba siempre por lan hasta saber que tenes coneccion a internet a travez de tu router y despues proba por wifi.

Edit: Se me ocurre, puede que por lan estes conectando a tu router y despues por wifi a otro y te cambie la tabla de ruteo el dhcp, eso lo podes ver ejecutando el comando route

Algo asi deberias tener, donde dice 192.168.0.201 deberia estar la Ip de tu router.
```

anarko@Marcos:~$ route
Tabla de rutas IP del núcleo
Destino         Pasarela        Genmask         Indic Métric Ref    Uso Interfaz
192.168.0.0     *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         192.168.0.201   0.0.0.0         UG    100    0        0 eth0

```


PD: Tenes el wifi sin contraseña? porque es la IP 130 y pico que da tu dhcp, si es el que se ve en las screenshot.

---

### Post by superaldo on 2009-08-25
Hola,

una ves que me conecto al router desde ubuntu no puedo entrar a la pagina de configuracion del mismo (192.168.1.1) se queda cargando el firefox, a diferencia de tratar a otras pagina que de inmendiato me sale que no se pudo cargar.

cuando cargo el xp no tengo que hacer nada para conectarme solita mi tarjeta de red se conecta tengo los ip y dns en automatico, ya que mi router que es el que realmente se conecta a mi ISP tiene activado el servidor dhcp y configurados dos dns de la misma telefonica para navegar, asi que el xp me anda normal y tambien mi ubuntu lo hacia hasta hace un dias :(

no me responden los ping a ip o alguna direccion de internet

si estoy seguro en conetarme a mi router sea por lan o por wireless en ambos casos conecta y me asigna una ip local del pool de ip del servicio dhcp del router algo asi como 192.168.1.33 en adelante, sea por lan o por wireless no navega ya lo intente, en xp todo normal pero en ubuntu no navega

pongo una imagen de lo que me salio cuando puse route cuando estoy conectado:
[http://www.studioead.com/files/Pantallazo3.gif](http://www.studioead.com/files/Pantallazo3.gif)

mi router en wireless tiene contraseña y estoy seguro de ponerla bien a la hora de conectarme con el WICD y el ip que me asigna es 192.168.1.35 no 130 o algo (segun mi screenshot) en lan o por wireless me sale que el ip que me da es uno de los que estan dentro del pool de dhcp lo mismo pasa con xp solo que con xp si navego :cry:

pd: gracias por la ayuda que me estan brindando, pero creo que voy a tener que reinstalar mi ubuntu :cry: :cry: :cry: :cry: con todo el esfuerzo que me costo ponerlo bonito y las actualizaciones y programas que le instale :(

---

