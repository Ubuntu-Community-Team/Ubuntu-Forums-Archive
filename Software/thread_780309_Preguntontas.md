---
title: "Preguntontas"
date: 2008-05-03
forum: Software
---

### Post by _kAz_ on 2008-05-03
Como va gente?

Abro este thread para postear una pregunta que es bastante simple pero que no le encuentro solución. Los invito también a que hagan sus preguntontas y así, además de sacarse la duda, evitamos la proliferación de este tipo de hilos.

Ahí va la mía:

Necesito **acceder como superusuario** pero **gráficamente** y no por consola. En el Dolphin (navegador de archivos) de Kubuntu estaba la opción de "Open as a Root", la cual no encuentro en Ubuntu utilizando el programa equivalente. Como hago?

---

### Post by odiseo77 on 2008-05-03
Si estás en KDE, ejecutas ***kdesu nombre_de_programa***, y si estás en Gnome, ejecutas ***gksu nombre_de_programa***.

---

### Post by Mauro22 on 2008-05-03
Desde consola:

```
sudo nautilus
```

o Alt + F2

```
gksudo nautilus
```

---

### Post by _kAz_ on 2008-05-03
> **odiseo77 said:**
> Si estás en KDE, ejecutas ***kdesu nombre_de_programa***, y si estás en Gnome, ejecutas ***gksu nombre_de_programa***.

> **Mauro22 said:**
> Desde consola:
```
sudo nautilus
```
o Alt + F2
```
gksudo nautilus
```

Ufa... no me va a quedar otra que *escribir*... 

O sea que no hay opción *gráfica*??? Era más directo apretar un icono, je.

---

### Post by margori on 2008-05-03
> **_kAz_ said:**
> Ufa... no me va a quedar otra que escribir... 
O sea que no hay opción gráfica? Era más directo apretar un icnno, je.

Sugiero despegues la mano del ratón, el teclado no muerde.

---

### Post by MeduZa on 2008-05-03
> **_kAz_ said:**
> Ufa... no me va a quedar otra que *escribir*... 

O sea que no hay opción *gráfica*??? Era más directo apretar un icnno, je.

si queres en el futuro hacerlo desde un icono crea un lanzador que tenga el gksudo y listo, la opcion grafica normalmente implica que alguien en el pasado la escribio, solo no existiria, tambien te podes bajar un nautilus action y ahi tendrias tu opcion grafica escrita por otra persona.

---

### Post by _kAz_ on 2008-05-03
> **margori said:**
> Sugiero despegues la mano del ratón, el teclado no muerde.

Lo uso, lo uso... Nomás que sería más ágil tener esa tarea que es bastante simple ya automatizada.

---

### Post by clasificado on 2008-05-03
> **_kAz_ said:**
> Lo uso, lo uso... Nomás que sería más ágil tener esa tarea que es bastante simple ya automatizada.

Mi kubuntu+kde3 la tiene, ¿el tuyo no?

¿Que sistema estas usando? Sé que kubuntu+kde4 no la tiene

clasificado

---

### Post by _kAz_ on 2008-05-03
> **clasificado said:**
> **Mi kubuntu+kde3** la tiene, ¿el tuyo no?

¿Que sistema estas usando? Sé que kubuntu+kde4 no la tiene

clasificado

Precisamente ese era el sistema que estaba utilizando hasta hace menos de una semana pero cambié por Ubuntu.

---

### Post by sergiom99 on 2008-05-04
agrego mi preguntonta>
diferencias entre remove y purge, en el adept.

---

### Post by Mauro22 on 2008-05-04
remove elimina la aplicacion en si. Lo elimina pero deja rastros.

purge borra todo lo que tenga que ver. configuraciones, dependencias, etc. Lo elimina por completo.

---

### Post by pol666 on 2008-05-04
Otra mas...

¿Como hago para aplicar una linea de comandos en un lanzador, para que se ejecuten uno despues del otro pero con un solo click. 


Es que a veces el modem no responde ytengo que resetear la coneccion

sudo poff dsl-provider
sudo pon dsl-provider

¿Como hago para se ejecuten de una en un lanzador del panel?

---

### Post by MeduZa on 2008-05-04
> **pol666 said:**
> Otra mas...

¿Como hago para aplicar una linea de comandos en un lanzador, para que se ejecuten uno despues del otro pero con un solo click. 


Es que a veces el modem no responde ytengo que resetear la coneccion

sudo poff dsl-provider
sudo pon dsl-provider

¿Como hago para se ejecuten de una en un lanzador del panel?

el separador es ; pero yo en ese caso hago un archivo .sh y agrego todo lo que quiero que pase y hago el lanzador hacia el.

---

### Post by pol666 on 2008-05-04
; y espacio o solo ;

En fin si quiero hacer el .sh lo hago en gedit?

---

### Post by Mauro22 on 2008-05-04
si, con gedit hacelo tranquilo.


al prinicipio pone:

#!/bin/bash

si lo vas a programar en bash, obvio


y despues lo que quieras. 
Cuando lo terminas, guardalo, dale permisos de ejecucion y copialo a /usr/bin

---

### Post by faktorqm on 2008-05-05
figurita repetida: al igual que le recomendaste al chabon que se queria comprar un modem y me abstuve de postear, 2 ya es mucho para mi. Por que no configuras el modem para que marque solo y te olvidas de usar software? Si no sabes como se hace pregunta. Lo contestamos 1500 veces eso. No por vos eh! por todos.......

---

### Post by vk-cdg on 2008-05-05
> **Mauro22 said:**
> si, con gedit hacelo tranquilo.

al prinicipio pone:

#!/bin/bash

si lo vas a programar en bash, obvio


y despues lo que quieras. 
Cuando lo terminas, guardalo, dale permisos de ejecucion y copialo a /usr/bin

Agrego mi preguntonta!
Que diferencia hay entre ponerlo en /usr/bin a tenerlo en otro lado, por ejemplo el home?

Yo tengo un par de scripts que me lanzan los screenlets y un par de cosas mas en el /home, de esa forma cuando cambio de versión de ubuntu (hace unos días de 7.10 a 8.04) no los perdo.

Está bien? está mal? conceptualmente hablando digo, porque andar... anda igual.

---

### Post by faktorqm on 2008-05-05
No se trata de que este mal o no, pero en /usr/bin se guardan todos los ejecutables del ubuntu digamos, en /usr/sbin aquellos ejecutables que tiene el bit de SUID en uno, por lo tanto solo pueden ser ejecutados por root o usuarios habilitados en sudo.
"tus cosas" digamos no esta mal ponerlas en el /home.
Si las pones en /usr/bin creo que la ventaja extra que te daba era que podias acceder desde cualquier carpeta donde estes parado (Creo) por que ponerlo ahi es el equivalente en windows a ponerla en alguna carpeta declarada en las variables de entorno.
Salu2!

---

### Post by marianom on 2008-05-05
Me encantó esta sección, muy buena idea. 
El nombre deberia ser "Todo lo que siempre quiso saber y le dió vergüenza preguntar".

---

### Post by ubuntu27 on 2008-05-05
> **_kAz_ said:**
> Como va gente?

Abro este thread para postear una pregunta que es bastante simple pero que no le encuentro solución. Los invito también a que hagan sus preguntontas y así, además de sacarse la duda, evitamos la proliferación de este tipo de hilos.

Ahí va la mía:

Necesito **acceder como superusuario** pero **gráficamente** y no por consola. En el Dolphin (navegador de archivos) de Kubuntu estaba la opción de "Open as a Root", la cual no encuentro en Ubuntu utilizando el programa equivalente. Como hago?

EDIT: LA RESPUESTA:

En hardy instala "nautilus-gksu" eso te permitira abrir como root graficamente :) 

```
sudo apt-get install nautilus-gksu
```
Reinicia nautilus con:
```
killall nautilus
```

Si no aparece en el menu contextual, esta afectado por un bug conocido. la solucion es copiar las librerias encontradas en
/usr/lib/nautilus/extensions-1.0

a /usr/lib/nautilus/extensions-2.0

y reinicia nautilus con

```
killall nautilus
```


Mi Post anterior:

Hace tiempo que no uso GNOME. Cuando yo usaba Ubuntu Fesity Fawn, habia una libreria, tipo -add-on que agregaba funciones a nautilus. Entre ellas habia un paquete para que agrege la opcion de abrir como root en nautilus. No se si sigue habiendo en hardy. Haber busca "nautilus" con synaptic.

Habia otro paquete bueno para GNOME. "nautilus-terminal" creo que se llamaba, te permite abrir el direcotorio desde nautilus en el terminal. Osea que navegas con nautilus a un direcotrio deseaso, haces click derecho, y escoges "abrir directorio en terminal" Listo! Ya no hay necesidad de usar el comando "cd" (change directory).

---

### Post by sergiom99 on 2008-05-05
pongo otra duda q siempre tuve:
si tengo una PC con un RouterOS y le agrego una plaquita de red wireless, hago un AP?
quiero decir, eso es capaz de transmitir como si fuera un router inalambrico?

---

### Post by _kAz_ on 2008-05-06
> **ubuntu27 said:**
> EDIT: LA RESPUESTA:

En hardy instala "nautilus-gksu" eso te permitira abrir como root graficamente :) 

```
sudo apt-get install nautilus-gksu
```
Reinicia nautilus con:
```
killall nautilus
```

Si no aparece en el menu contextual, esta afectado por un bug conocido. la solucion es copiar las librerias encontradas en
/usr/lib/nautilus/extensions-1.0

a /usr/lib/nautilus/extensions-2.0

y reinicia nautilus con

```
killall nautilus
```


Grandeeee!!!! Salió perfecto!!!

Gracias!!!

---

### Post by Tosh78 on 2008-05-06
Bueno, ahi va la mia.
Como hago para hacer que lo que veo en el monitor tambien pueda verlo en la tele con el cable de super video? Tengo que instalar alguna aplicacion que permita elegir el output? Porque en wingarch los mismos drivers tienen un programita especial que te da esa opcion, pero en el ubuntu no pude encontrarlo. La placa de video es una intel. Alguna idea?

---

### Post by Thalskarth on 2008-05-06
> **Tosh78 said:**
> Bueno, ahi va la mia.
Como hago para hacer que lo que veo en el monitor tambien pueda verlo en la tele con el cable de super video? Tengo que instalar alguna aplicacion que permita elegir el output? Porque en wingarch los mismos drivers tienen un programita especial que te da esa opcion, pero en el ubuntu no pude encontrarlo. La placa de video es una intel. Alguna idea?

Eso depende... no se puntualmente con tu placa, ya que no recuerdo que drivers debe usar... pero por ejemplo, los drivers de Nvidia si pones los 'oficiales' (mediante envy o sistema/administracion/controladores de hardware, etc), traen un programita llamado 'nvidia-settings' que te permite configurar eso de modo gráfico y facil (es parecido al de windows incluso).

---

### Post by Mataca on 2008-05-06
Remove, remueve el paquete pero deja los archivos de configuración
Purge: remueve el paquete, borra los archivos de conf.

Corrijanme si me equivoco ya que sistemas no es mi rubro :)


Edit:  UUHHH contesté un post re viejo, sorryyyyy

---

### Post by sergiom99 on 2008-05-08
Agrego una duda:
Comparto una carpeta por SMB.
pero cuando la veo desde otro equipo XP como nombre de la PC o del recurso me muestra "*Samba 3.0.26a (Kubuntu)*" donde Kubuntu es lo que yo ponga en el smb.con en "*netbios name = kubuntu*"

como hago para que me lo muestre con el nombre del host?

---

### Post by guillermolisi on 2008-05-08
Te muestro como lo tengo configurado en la PC de casa y como se ve cuando navegas por la red, asi te das una idea concreta.

```

[global]
netbios name = guillermo
server string = Unimix Kubuntu
workgroup = unimix

```

[IMG]http://i261.photobucket.com/albums/ii63/unimix/samba.png[/IMG]

A esto te referias o entendi cualquier cosa ?

---

### Post by sergiom99 on 2008-05-08
perfecto, gracias.

---

### Post by Chipknot on 2008-05-08
Hoy me dieron una guía para instalar el Linux. La guía es de Ubuntu, pero estoy bajando el Xubuntu 7.10 (por el tema de los requerimientos).
La cosa es que hago el Live CD (lo voy a hacer cuando baje) y luego tengo que hacer la partición, pero no se bien que tengo que hacer... En la guía no entiendo bien, no se que programa es más fácil, mejor y demás... NUNCA instalé ni nada relacionado con el Linux, y eso me complica más y más... No se, tengo el RE despiole :p

---

### Post by sajnox on 2008-05-08
Por que no bajas la 8.04 y pone el CD con windows andando, para que?? te da la opcion de instalar con wubi (wubi=windows ubuntu installer) haces la instalacion sin particionar ni nada, si bien no es lo mas "lindo" seguro que te da una muy buena mano para entrar en Linux, despues ya vas a poder particionar "y todas esas cosas locas".

Por mas informacion date una vuelta por [http://wubi-installer.org/](http://wubi-installer.org/)

---

### Post by santiagoward2000 on 2008-05-08
> **Chipknot said:**
> Hoy me dieron una guía para instalar el Linux. La guía es de Ubuntu, pero estoy bajando el Xubuntu 7.10 (por el tema de los requerimientos).
La cosa es que hago el Live CD (lo voy a hacer cuando baje) y luego tengo que hacer la partición, pero no se bien que tengo que hacer... En la guía no entiendo bien, no se que programa es más fácil, mejor y demás... NUNCA instalé ni nada relacionado con el Linux, y eso me complica más y más... No se, tengo el RE despiole :p

Hola!
Si lo vas a instalar, durante la instalación te va a poner una opción para cambiar el tamaño de la partición (no me acuerdo bien cómo se llama). Seleccionás eso, te aparece una barrita que vos moves al tamaño que quieras y listo. Solo fijate de no seleccionar la opcion de usar todo el disco, o te vas a quedar sin Windows.
Ahora, ¿estas bajando la 7.10 por algo en especial en vez de la 8.04? Los requerimientos son los mismos.
Saludos!

---

### Post by Chipknot on 2008-05-09
No en sí lo bajé porque a la vista vi que ese podía llegar a funcionarme, nada más.
Además vi que la nueva versión del Xubuntu, necesitaba más PC (por ahí flashié)

Saludos y YA voy a comenzar con la instalación :P

---

### Post by silencio65 on 2008-05-09
Yo tengo una pregunta tonta.

Me quedó en la papelera un archivo de texto (se llama _out.txt, por si eso es relevante) de 0 bytes. 
Si vacío la papelera, sigue ahí lo más pancho.
Si abro la papelera y lo quiero borrar, me dice:

Error al borrar.
Hubo un error al obtener la información acerca de «media_sda5_.Trash-1000___out.txt».
Mostrar más detalles:
Error al mostrar información del estado del archivo «/media/sda5/.Trash-1000_/files/out.txt»: No existe el fichero ó directorio.

Si abro una terminal y voy a /media/sda5/.Trash no encuentro ningún archivo.

No es que sea un problema, pero me hincha un poco ver la papelera siempre llena.

Saludos
silencio65

---

### Post by Chipknot on 2008-05-09
Bueno, les estoy hablando desde el Xubuntu ^^
La cosa es que me tiré a configurar mi conexión y milagrosamente andubo, pero no tengo ni messenger, ni para escuchar música ni nada.
¿Alguno me puede recomendar algunos programas utiles para Linux?

Saludos!

---

### Post by santiagoward2000 on 2008-05-10
> **Chipknot said:**
> Bueno, les estoy hablando desde el Xubuntu ^^
La cosa es que me tiré a configurar mi conexión y milagrosamente andubo, pero no tengo ni messenger, ni para escuchar música ni nada.
¿Alguno me puede recomendar algunos programas utiles para Linux?

Saludos!

Hola!
Xubuntu viene con un messenger ya instalado, el Pidgin. Si querés usarlo andá a **Applications/Network/Pidgin Instant Messenger**. Ahí agregás tus cuentas y listo. Otro que escuché que es muy bueno (pero que personalmente nunca usé) es el emesene. Está en los repositorios. Para instalarlo, andá a **Applications>System>Add/Remove...** y buscalo ahí.
Para escuchar música, en Xubuntu está el totem (que en realidad está más pensado para ver videos que escuchar música). Sino, te recomiendo que pruebes el Exaile. También lo podés encontrar en Add/Remove... Acordate que antes tenes que instalar los codecs. Abrí una terminal y escribí:
```
sudo apt-get install xubuntu-restricted-extras
```
Esto te instala la mayoría de los codecs, el Flash y el OpenJava.
Saludos!

---

### Post by Chipknot on 2008-05-10
> **santiagoward2000 said:**
> Hola!
Xubuntu viene con un messenger ya instalado, el Pidgin. Si querés usarlo andá a **Applications/Network/Pidgin Instant Messenger**. Ahí agregás tus cuentas y listo. Otro que escuché que es muy bueno (pero que personalmente nunca usé) es el emesene. Está en los repositorios. Para instalarlo, andá a **Applications>System>Add/Remove...** y buscalo ahí.
Para escuchar música, en Xubuntu está el totem (que en realidad está más pensado para ver videos que escuchar música). Sino, te recomiendo que pruebes el Exaile. También lo podés encontrar en Add/Remove... Acordate que antes tenes que instalar los codecs. Abrí una terminal y escribí:
```
sudo apt-get install xubuntu-restricted-extras
```
Esto te instala la mayoría de los codecs, el Flash y el OpenJava.
Saludos!
Bueno.
Para menssagear unso ese, todavía no provee otro, pero ya lo voy a hacer.
Para escuchar música no me vino ninguno, solo reproductor de videos (que no me permitía escuchar mp3) y un grabador de CD, entonces baje el Amarok (recomendado por ahí) y gracias a Pol666 que me ayudó, lo instale y estoy escuchando música :)
Ah, y ahora estoy haciendo eso de los codecs, ya me esta cargado, muchisimas gracias.

Otra duda:

¿Puede que halla algo para poner TOOOOODO en español, porque el Amarok, Firefox, y algunas herramientas del Xubuntu estan en ingles y tras que no tengo mucha experiencia en linux, si está en ingles se me va a complicar un poco (no quiere decir que no entienda nada ingles, pero se lo básico).

Saludos!

---

### Post by Hei Ku on 2008-05-10
tenes que descargar ademas de los programas los paquetes de traduccion. en general se llaman xxxxx-i18n-es o xxxxx-language-pack-es

i18n es por iNTERNATIONALIZATIOn.
tendrias que bajarte los de KDE, que no vienen en xubuntu por default.

---

### Post by Chipknot on 2008-05-10
Y de donde los puedo conseguir?... Porque no tengo idea de nada.
O de la consola los puedo bajar son el sudo apt-install?

---

### Post by Hei Ku on 2008-05-10
es sudo apt-get install
pero te conviene usar un programa grafico, que te va a hacer mas facil. En Xubuntu tenes el Synaptic. Busca ahi por kde language, y fijate los paquete que terminan con es (por español)

Aclaracion aparte:
Como tenes poca experiencia, fijate primero los programas del menu, no importa lo que te hayan dicho, hoy en dia en Linux la consola la tenes que usar poco, salvo cuando te dan indicaciones, que es mas facil mandarte un comando de consola que explicarte como hacerlo con el mouse.

---

### Post by Chipknot on 2008-05-10
Cuando me meto al "Gesto de Paquetes Synaptic" me dice lo siguiente:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

:/

---

### Post by Hei Ku on 2008-05-10
aparentemente en tu ultima actualizacion hubo algun problema.

hace lo que dice el mensaje, en la consola pone:

sudo dpkg --configure -a

---

### Post by _kAz_ on 2008-05-10
**Segunda preguntonta de mi parte:**

Cómo hago para que con Compiz "se vea" el cubo??? Cuando muevo la rueda del raton pasa de un escritorio a otro y se advierte la forma... Pero lo que yo quiero es que se aleje y se vea el cubo entero (como los print que ponen en "¿Cómo se ve tu SO?"). 

Debe ser una ****** pero no la sé; ya toqué varias cosas de la configuración y no encuentro como hacer.

---

### Post by Mauro22 on 2008-05-10
Hay dos formas:

Apreta y mantena la rueda del mouse (si tenes) y movelo

o

Control + Alt + Click Izquierdo + mover el mouse.

---

### Post by pol666 on 2008-05-10
si asi como te dijeron... para que se achique esta en opciones de cubo

---

### Post by _kAz_ on 2008-05-10
> **pol666 said:**
> si asi como te dijeron... para que se achique esta en opciones de cubo

Precisamente eso estoy intentando :(

En donde está la opción??? Ya busqué en Desktop Cube, Rotate Cube y Cube Caps pero no encuentro nada que diga scale o algo asi ahi.

---

### Post by Mauro22 on 2008-05-11
En rotate cube, la opcion Zoom (la de abajo de todo)

---

### Post by _kAz_ on 2008-05-11
> **Mauro22 said:**
> En rotate cube, la opcion Zoom (la de abajo de todo)

Ahhhh... claro, pensé que "Zoom" era para agrandarlo nomas. Quedo bueno. Ahi va la captura:

---

### Post by sergiom99 on 2008-05-13
como hago para que al bootear me active directamente el wlan0?
Ahora tengo q ir al icono de red y conectarlo siempre a mano...

---

### Post by guillermolisi on 2008-05-13
> **sergiom99 said:**
> como hago para que al bootear me active directamente el wlan0?
Ahora tengo q ir al icono de red y conectarlo siempre a mano...

FIjate en el archivo /etc/network/interfaces 

(podes hacer 
```
$ less /etc/network/interfaces
```en la consola). 

Tenes que ver una linea que diga 
```
auto wlan0
```Esa linea hace que cuando inicias Ubuntu se active la placa de red.

Si no queres usar la consola, podes mediante GUI, pero para darte detalles necesito saber que entorno grafico usas (Gnome, KDE, etc.).

Si no tenes esa linea, hay que editar el archivo mencionado y agregarla despues del bloque que define la configuracion de la placa identificada como wlan0.

Te paso un ejemplo en el cual tenes que cambiar eth1 por wlan0:
```
iface eth1 inet static
address 90.0.0.1
netmask 255.255.255.0

auto eth1
```

---

### Post by sergiom99 on 2008-05-14
Guillermo, uso Kubuntu.
Ahora no estoy con la maquina, pero estoy "casi" seguro que el auto esta.
Pero cuando inicio (sin cable) tengo el icono del wlan pero tengo que conectarla a mano. o sea, creo que la interfaz esta activada, pero para conectarme a la red tengo que seleccionarla y activarla a mano.

---

### Post by sartrejp on 2008-05-14
he visto en las capturas de los escritorios que la consola es transparente, y pueden visualizarse las ventanas que se encuentran debajo. En mi caso, por más que haya diez ventanas abiertas, de fonde de la terminal, como transparencia se ve el papel tapiz del escritorio, y no las ventanas. ¿Saben como solucionarlo?

---

### Post by Hernán-Amaya on 2008-05-14
tenes que tener activado compiz sino y tenes hardy instalado con este comando activas el composite de gnome 

gconftool-2 -s --type bool /apps/metacity/general/compositing_manager true

---

### Post by guillermolisi on 2008-05-14
> **sergiom99 said:**
> Guillermo, uso Kubuntu.
Ahora no estoy con la maquina, pero estoy "casi" seguro que el auto esta.
Pero cuando inicio (sin cable) tengo el icono del wlan pero tengo que conectarla a mano. o sea, creo que la interfaz esta activada, pero para conectarme a la red tengo que seleccionarla y activarla a mano.

A ver. Si hablas de cable, te referis a un cable de red de una segunda interface (ethx) que tambien existe en ese equipo ?

Si es asi (y no es el cable de Fibertel ni el de la alimentacion del sistema :-)  ), te comento que en tres maquinas con WiFi y placa 3Com cableada tuve que hacer un script que al iniciar Kubuntu (Gutsy en este caso, pero ya me pasaba en Feisty), bajara la ethx y subiera la wlan0.

Si la ethx estaba up no me funcionaba la inalambrica (implementada via ndiswrapper).

---

### Post by sergiom99 on 2008-05-14
Hola Guillermo,
si quise poner cable de eth1. Si lo tengo enchufado, arranca con esa interface y no tengo que hacer nada. Pero, si estoy unplugged, tengo que ir al icono de wifi y seleccionar mi red y conectarme "a mano". yo quiero que lo haga solo (como hace el winxp)
dejo mi /etc/network/interfaces:
```
# The loopback network interface
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

# The primary network interface
auto wlan0
#iface eth0 inet dhcp

```

---

### Post by guillermolisi on 2008-05-14
> **sergiom99 said:**
> Hola Guillermo,
si quise poner cable de eth1. Si lo tengo enchufado, arranca con esa interface y no tengo que hacer nada. Pero, si estoy unplugged, tengo que ir al icono de wifi y seleccionar mi red y conectarme "a mano". yo quiero que lo haga solo (como hace el winxp)
dejo mi /etc/network/interfaces:
```
# The loopback network interface
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

# The primary network interface
auto wlan0
#iface eth0 inet dhcp

```

Cuando hablas de conectarte a mano, te referis a levantar la interface (ifconfig wlan0 up) o a conectarte al SSID del AP ?

Esta es la seccion de wlan0 de una de las PCs que te mencione. Usa WPA.
```

auto wlan0
iface wlan0 inet static
address 90.0.0.8
netmask 255.255.255.0
gateway 90.0.0.1
dns-nameservers 90.0.0.1
wpa-driver wext
wpa-ssid IPSI
wpa-ap-scan 1
wpa-proto WPA
wpa-pairwise TKIP
wpa-group TKIP
wpa-key-management WPA-PSK
wpa-psk a8f4e0d279*********************************************
```Fijate que esta incluida la identificacion del SSID (IPSI) al que se tiene que conectar y, recomendable en lo posible, usa IP estatica.

Luego inclui un pequeño script en /etc/init.d/rc.local que desactiva la interface cableada y levanta/activa la wireless.

```
ifconfig eth0 down
ifconfig wlan0 up
```Asi, cada vez que incias la PC queda todo bien dispuesto.

---

### Post by sartrejp on 2008-05-14
Excelente, ya funciona correctamente la trasnparencia de la terminal.
Muchas Gracias

---

### Post by sergiom99 on 2008-05-15
gracias guille, funciono, pero lo volvi a dejar como antes porque se me complicaba un toque usarlo en otras redes.
no es tan grave hacer clic en el iconito de wifi y seleccionar mi SSID.

proximamente mas preguntontas...

---

### Post by agreppi on 2008-05-15
Buenas a todos. Soy nuevo en el mundo Linux, instalé Ubuntu la semana pasada y me estoy interiorizando de algunas cosas.
Acá dejo mi preguntonta, y tiene que ver con los usuarios root y sudo.
Según leí por ahí, Ubuntu por defecto NO asigna permisos de root al usuario que instala el sistema, y esto es para evitar que el mismo usuario haga algo malo en los archivos del SO.
Pero por otra parte, usando sudo es como si estuviera usando el root.
La pregunta es, ¿qué se gana poniendo este comando sudo, si igual puedo entrar con este comando y modificar cualquier cosa como si hubiera entrado con el comando root?

Muchas gracias.
Alejandro

---

### Post by leo_rockway on 2008-05-15
> **agreppi said:**
> 
La pregunta es, ¿qué se gana poniendo este comando sudo, si igual puedo entrar con este comando y modificar cualquier cosa como si hubiera entrado con el comando root?


La diferencia rádica en que a sudo lo estás usando de forma conciente y sabés que cualquier cosa que hagas va a ser con poder de super usuario. Además, para usar sudo es necesario ser sudoer (solo el 1er usuario que se crea es sudoer por default, a los demás hay que darles el privilegio manualmente).

Dicho esto, de todas formas se puede usar "su" (aunque quizás no sea lo más recomendable).

---

### Post by guillermolisi on 2008-05-15
> **sergiom99 said:**
> gracias guille, funciono, pero lo volvi a dejar como antes porque se me complicaba un toque usarlo en otras redes.
no es tan grave hacer clic en el iconito de wifi y seleccionar mi SSID.

proximamente mas preguntontas...

Jajajaaa !!

Otra cosa que podes hacer es instalar algun paquete de administracion de APs via GUI para facilitar la conexion WiFi on the fly.

Probe algunas (que en este preciso momento no recuerdo ni tengo acceso a las PCs con WiFi) que busque en los repositorios como para experimentar. Si te interesa te paso cual fue la que mejores resultado me dio (fueron dos las que mas me gustaron para KDE).

---

### Post by sergiom99 on 2008-05-15
> **guillermolisi said:**
>  Si te interesa te paso cual fue la que mejores resultado me dio (fueron dos las que mas me gustaron para KDE).

Dale espero tu dato asi lo pruebo. Con el Knetworkmanager me va bien, pero tengo que engancharlo al AP a mano, si lo hiciera solo a los "Wifi favoritos" como el WinXP estaria barbaro

---

### Post by _kAz_ on 2008-05-18
Sale otra:

**[SIZE="4"]¿Existe alguna forma de que mi monitor se apague automáticamente cuando se apaga el CPU? [/SIZE]**

Tengo un Samsung SyncMaster 793v. No me refiero a que quede stand-by, sino que se apague completamente. Podía hacer eso con mi anterior monitor (un AOC) pero este último nunca encontré la posibilidad ni siquiera en windows.

Por cierto, he leído en este thread preguntas que no son tan tontas sino que merecerían un tratamiento aparte. Tratemos de mantenerlo simple. Igual es comprensible porque todo el mundo piensa que cualquier pregunta que le surja es tonta, jeje.

---

### Post by faktorqm on 2008-05-21
Creo que no. Igual podés hacer muchas cosas, como por ejemplo agarrar un paralelo, conectar un rele a la pata 25, la otra a la 1, y del otro lado del rele le pones la tension a tu monitor... y haces eso que necesitas vos. rebuscado pero debe funcionar seguro. :D

PREGUNTONTA MIA AHORA: ¿de donde se cambia el tema de iconos? En preferencias -> apariencia a mi no me aparece nada para cambiarlos. (antes era mas facil, o no?) 
Asi que no se como se cambian. Si me responden les agradeceria mucho. Salu2!!

p.d.: no lo puse en el thread que ya esta abierto por el tema de los iconos por que definitivamente era una preguntonta...

EDITO: Estaba tan desesperado que lo encontré, cuando elegís el tema, tenes que hacer click en el boton personalizar y ahi si te abre el cuadro que yo decia que te deja cambiar todo. Grossoo!! Salu2!

---

### Post by Mauro22 on 2008-05-21
> **faktorqm said:**
> 
PREGUNTONTA MIA AHORA: ¿de donde se cambia el tema de iconos? En preferencias -> apariencia a mi no me aparece nada para cambiarlos. (antes era mas facil, o no?) 
Asi que no se como se cambian. Si me responden les agradeceria mucho. Salu2!!


Vas a Sistema -> Preferencia -> Apariencia:

En la pestaña tema, elegis el tema que queres y le das al boton personalizar.
Elegis la solapa (o pestaña) Iconos, y ahi elegis el pack que te guste, manteniendo el tema.

---

### Post by madelaki on 2008-05-21
La mia es preguntonta en serio, pero juro que no encuentro la respuesta. Bajo que plugin se puede configurar la opacidad del menu de Ubuntu (Aplicaciones, Sistema, etc.) dentro del settings-manager de Compiz Fusion? Nunca pude encontrar esa opcion, y lo vi en varios screens.

---

### Post by pol666 on 2008-05-21
anda al compiz settings y en Generals options clickea en la pestaña opacity

ahi pones NUEVO, y ahi pones esto:


> Tooltip | Menu | PopupMenu | DropdownMenu

Yo te recomiento que le pongas entre 70 y 90 de opacidad no sea cosa que te desaparesca el menu ^^

---

### Post by madelaki on 2008-05-21
Funciono perfectamente, en 80 se ve bien y queda lindo. Gracias che. Me imaginaba que era algo asi (me fije en casi todos los plugins y nunca lo vi), pero de los nombres no tenia idea.

---

### Post by pol666 on 2008-05-22
De nada... Con eso podes jugar MUCHISIMO.

podes hacer que cualquier programa se vea con transparencia siempre..Yo lo tengo al emesene con transparencia y el nautilus tambien..queda genial.

---

### Post by santiagoward2000 on 2008-05-22
Uh, me acaba de saltar una duda. En Xubuntu si dejo un programa abierto antes de apagar (como Pidgin o Simdock) este se vuelve a abrir cuando prendo de nuevo. ¿Se puede hacer que uno no se vuelva abrir? O sea, quiero que Pidgin se siga abriendo, pero no Simdock. ¿Hay alguna forma que no sea cerrarlo a mano antes de apagar?
Saludos!

---

### Post by madelaki on 2008-05-23
Este es un problema con el teclado, no una duda, pero igual lo posteo aca porque no es nada serio. El teclado lo tengo configurado con la distribucion de Latino america, pero funciona como si fuera la de USA. La sesion anterior funcionaba lo mas bien.

---

### Post by santiagoward2000 on 2008-05-23
> **madelaki said:**
> Este es un problema con el teclado, no una duda, pero igual lo posteo aca porque no es nada serio. El teclado lo tengo configurado con la distribucion de Latino america, pero funciona como si fuera la de USA. La sesion anterior funcionaba lo mas bien.

Hola!
Puede ser que estes usando XGL? A mí me pasaba lo mismo cuando lo usaba. Lo que hacía era correr este comando en Autostarted:
```
setxkbmap -model pc105 -layout es -variant basic 
``` (mi teclado es español).
Probá correr lo mismo, pero con **la** en vez de **es**.
Suerte!

---

### Post by madelaki on 2008-05-23
Funciono 11 puntos, muchas gracias.

---

### Post by santiagoward2000 on 2008-05-23
> **madelaki said:**
> Funciono 11 puntos, muchas gracias.

De nada! :)

---

### Post by valucha on 2008-05-25
[COLOR="DarkOrchid"]¿Cómo hago para hacer que compiz se me inicie al último?... Porque no sé por qué se inicia antes que los paneles y estos se me ponen encima del conky... tengo que killearlo y despues iniciarlo de nuevo,...

GRacias[/COLOR]

---

### Post by santiagoward2000 on 2008-05-25
> **valucha said:**
> [COLOR="DarkOrchid"]¿Cómo hago para hacer que compiz se me inicie al último?... Porque no sé por qué se inicia antes que los paneles y estos se me ponen encima del conky... tengo que killearlo y despues iniciarlo de nuevo,...

GRacias[/COLOR]

Y... no se si esto entra en las preguntontas, es un poquito mas complicado, pero ya que preguntaste te ayudo! :)
Primero haces un archivito y lo llamas (por ejemplo) startcompiz.sh:
```
gedit startcompiz.sh
```
despues copias esto en el archivo:
```
#!/bin/sh
conky
sleep 4
compiz
```
El 4 es el tiempo que pasa entre que empieza conky y compiz. Talvez tengas que ajustarlo para que tarde un poco mas.
Despues le das el permiso de ejecucion. En una consola pones:
```
chmod a+x startcompiz.sh
```
Por ultimo, pones el archivo este en startup y listo.
Espero que ande! Yo usaba un script parecido para que Adesklets empiecen despues de Beryl hace MUUUCHO. No lo probe con conky, pero supongo que debe andar.
Suerte!

---

### Post by Mauro22 on 2008-05-25
acordate te darle permisos de ejecucion

chmod a+x startcompiz.sh

---

### Post by santiagoward2000 on 2008-05-25
> **Mauro22 said:**
> acordate te darle permisos de ejecucion

chmod a+x startcompiz.sh

Uhh, me olvide!! Gracias!
Ya lo edito!

---

### Post by valucha on 2008-05-25
[COLOR="DarkOrchid"]GRacias chicos, ahroa lo hago, igual era para el conky y yo lo escribí mal, jajaja (esos errores Freudianos, se parecen mucho conky y compiz) pero supongo que funcionará igual...

:)[/COLOR]

---

### Post by santiagoward2000 on 2008-05-25
> **valucha said:**
> [COLOR="DarkOrchid"]GRacias chicos, ahroa lo hago, igual era para el conky y yo lo escribí mal, jajaja (esos errores Freudianos, se parecen mucho conky y compiz) pero supongo que funcionará igual...

:)[/COLOR]

JEJE, si, solo cambia el orden en el archivito. Yo puse conky antes que compiz (creo ;)). Ponelos alrevez y listo.

---

### Post by ignacioml on 2008-05-28
Bueno, con esto de las preguntas tontas, a mi juego me llamaron. Ahí va:

Tengo Ubuntu 7.10 andando de perillas desde hace algo más de un mes. 8) Cada tanto me aparece el ícono que me dice que hay actualizaciones. Yo abro el actualizador y le acepto todas las que vengan. La primera vez bajó 240 megas de actualizaciones y después siempre menos y más chicas. 

Preguntonta 1: ¿Hace falta que ande mirando qué es cada una de las actualizaciones que me propone para eventualmente rechazar alguna? Disculpen el paralelismo pero, por ejemplo, en güindous hay algunas actualizaciones que no las instalo; como todo lo que sea para mejorar o cambiar de versión de Internet Explorer porque no lo uso.

Preguntonta 2: ¿Existe la posibilidad de hacer que Ubuntu instale las actualizaciones automáticamente? 

Para dejar andando Ubuntu 7.10 con mi máquina que es nueva pero tiene un monitor de lo más pedorro tuve que instalar con el alternate CD y configurar la resolución de Gnome y no fué inmediato. El gestor de actualizaciones, arriba del cuadro donde aparecen las actualizaciones para 7.10 también me dice que ya tengo disponible la versión 8.04 y me propone actualizar.

Preguntonta 3: ¿Actualizo? ¿Así nomás?

Estuve viendo que hasta los más baqueanos tuvieron problemas de resolución cuando actualizaron.

Preguntonta 4: ¿La versión 8.04 me va a tomar todos los seteos de resolución como los tengo en mi 7.10? ¿o voy a tener que configurar todo de nuevo?

:-s

---

### Post by Simbiosys on 2008-05-28
¿Donde se guardan los archivos temporales en ubuntu 8.04 HH?

Por ejemplo, descargo un archivo, lo abro en vez de guardarlo... ¿donde queda el temporal? ¿Hay alguna herramienta para limpieza? (puse ese ejemplo, pero no me refiero a la navegación sino en general).

Gracias.

---

### Post by pol666 on 2008-05-31
Mi preguntonta del dia

¿Cual es la direfencia entre Emerald themes y compiz themes?.. por que tengo entendido que ambos son bordes de ventanas.. y yo uso emerald pero tengo compiz asi que no se que es

PD: Pongan este thread Sticky por que es molesto buscarlo para hacer una preunta (:-D)



Edit Simbiosis si podes limpiar el cache del apt- get con esto

**sudo apt-get clean **

---

### Post by tzulberti on 2008-06-01
> **Simbiosys said:**
> ¿Donde se guardan los archivos temporales en ubuntu 8.04 HH?

Por ejemplo, descargo un archivo, lo abro en vez de guardarlo... ¿donde queda el temporal? ¿Hay alguna herramienta para limpieza? (puse ese ejemplo, pero no me refiero a la navegación sino en general).

Gracias.

Depende de que archivo estes hablando. 
Si es un archivo temporal del firefox entonces en la carpeta creo que queda en la carpeta /tmp, por lo que el mismo se borra cuando cierres session.
Sin embargo si es un archivo de instalacion deb entonces los archivos se guardan en /var/cache/apt/archives y se pueden borrar usando apt-get clean o apt-get autoclean.

---

### Post by Thalskarth on 2008-06-01
> **tzulberti said:**
>  y se pueden borrar usando apt-get clean o apt-get autoclean.
Aprovecho esto para hacer mi preguntonta :P

Cual es la diferencia entre el 'clean' y el 'autoclean'??

---

### Post by crosssover on 2008-06-01
yo tengo una, pero creo que mas bien es problema de mi hardware.

Pasa que no nunca pude entrar al modem/router por el navegador con ip de mi puerta de enlace: 192.168.1.1 en el modem huawei Smartax mt882 de Speedy.
cuando en win entra sin problemas.
No se si a alguien le pasa lo mismo, ah tampoco lo pude configurar como router, segui montones de guias pero parece que tiene el firmware muy tocado y solo queda como bridge

---

### Post by SLA_leandrin on 2008-06-04
Buenas a todos, esta es mi preguntonta:

Cuando me conecto a internet por cable con el router (D-Link DSL-500B, proveedor UOL) me pasa que se conecta pero no me anda para navegar por internet, ni wget ni nada, pero si por ejemplo el skype o el deluge. Llamo para preguntar que podía ser y como me imaginaba era un problema de los DNS. El tema es que cada vez que le conecto el cable debo nuevamente configurar manualmente el DNS que me pasaron para poder navegar... esto es muy molesto; como puedo hacer para que se conecte siempre con el DNS que yo quiero, y no con el que asigna la conexión automáticamente??

---

### Post by Simbiosys on 2008-06-06
> **Thalskarth said:**
> Aprovecho esto para hacer mi preguntonta :P

Cual es la diferencia entre el 'clean' y el 'autoclean'??

apt-get clean elimina todo excepto los archivos "lock" de /var/cache/apt/archives/ y /var/cache/apt/archives/partial/. Así, si necesita reinstalar un paquete APT, lo descargará de nueva cuenta.

apt-get autoclean elimina sólo los archivos que no pueden ser descargados de nuevo. 

Saludos.

---

### Post by fedeavila on 2008-06-08
ya que estamos yo hago la mia... en el wubi installer a la hora de elegir la distro a instalar aparecen dos kubuntu's (kubuntu y kubuntu-kde) ... que diferencia hay? cual de los dos supone q viene en el cd que me pedi por shipit?

---

### Post by guillermolisi on 2008-06-08
> **fedeavila said:**
> ya que estamos yo hago la mia... en el wubi installer a la hora de elegir la distro a instalar aparecen dos kubuntu's (kubuntu y kubuntu-kde) ... que diferencia hay? cual de los dos supone q viene en el cd que me pedi por shipit?

Una version es Kubuntu con KDE 3.5.9 y la otra con KDE 4, en ese orden respecto de como las mencionas. 

La diferencia fundamental entre ambas "versiones" es solo el escritorio grafico (que para el caso no es poca cosa).
Si no recuerdo mal, ninguna de las dos es LTS (Long Term Support), cosa que si es 8.04 con Gnome.

---

### Post by guillermolisi on 2008-06-08
> **crosssover said:**
> yo tengo una, pero creo que mas bien es problema de mi hardware.

Pasa que no nunca pude entrar al modem/router por el navegador con ip de mi puerta de enlace: 192.168.1.1 en el modem huawei Smartax mt882 de Speedy.
cuando en win entra sin problemas.
No se si a alguien le pasa lo mismo, ah tampoco lo pude configurar como router, segui montones de guias pero parece que tiene el firmware muy tocado y solo queda como bridge

Que IP tiene la tarjeta de red cuando queres acceder al modem ? (si tenes una sola seguramente esta con IP dinamica/DHCP)

Si no esta en la misma red (por ej. posee una IP publica) nunca vas a poder entrar por estar PC y modem en dos redes distintas.

Asignale una IP estatica a la tarjeta de red que sea por ejemplo 192.168.1.10 255.255.255.0, proba y conta como te fue.

Si queres mas info sobre ese Huawei entra en [http://www.adslzone.net](http://www.adslzone.net)

BTW, Telefonica de Argentina configura los modems por defecto como bridge a diferencia de Telecom que los deja como routers.

---

### Post by xpelaox on 2008-06-18
Holaaa Revivo para hacer una pregunta.
A veces cuando bajo ciertos programas por synaptic o por consola, bajo, instalo pero no se donde garompa quedo, ni como abrirlo, a veces con poner el nombre en la consola basta, pero a veces no, hay alguna forma de buscarlo?

Saludos

---

### Post by sergiom99 on 2008-06-18
mira, a mi me ha pasado que no aparecen en el Kmenu hasta no reiniciar X.
O bien no me aparecio alguno porque era un programa de Gnome y no me lo agregaba por default al Kmenu (ej: GIsomount o algo asi). O porque instale algo que no tiene entorno grafico (ej: fuseiso)

---

### Post by sergiom99 on 2008-06-18
(el foro estuvo colgado unos minutos y me lo duplico entre reintentos. Oops!)

---

### Post by Tosh78 on 2008-06-19
Ahi va mi preguntonta. Como cambio el color de las letras de la barra de menu (la que esta arriba)? Me estuve fijando pero no pude encontrar donde se hace eso.

---

### Post by valucha on 2008-06-20
[COLOR="DarkOrchid"]Tenés que configurar el archivo de configuración del theme que estés usando:
Y acá está tu respuesa: [http://proyectofedora.org/mexico/2008/03/19/%C2%BFcomo-cambiar-el-color-de-la-fuente-del-gnome-panel/](http://proyectofedora.org/mexico/2008/03/19/%C2%BFcomo-cambiar-el-color-de-la-fuente-del-gnome-panel/)[/COLOR]

---

### Post by Tosh78 on 2008-06-20
Muchas gracias, Valucha!

---

### Post by guillermolisi on 2008-06-23
> **sergiom99 said:**
> Dale espero tu dato asi lo pruebo. Con el Knetworkmanager me va bien, pero tengo que engancharlo al AP a mano, si lo hiciera solo a los "Wifi favoritos" como el WinXP estaria barbaro

Primero, mil disculpas por demorar tanto en responderte.

Luego, el que mas me gusto es el KWiFimanager. Esta en los repositorios.

---

### Post by sergiom99 on 2008-06-23
gracias guillermo.
sabes que entre tanto instale HH y ahora conecta solo cuando estoy en mi red, asi que la molestia de conectarme 'a manopla' ya no la tengo.
Igual le voy a pegar una mirada al que me decis.

---

### Post by guillermolisi on 2008-06-23
> **sergiom99 said:**
> gracias guillermo.
sabes que entre tanto instale HH y ahora conecta solo cuando estoy en mi red, asi que la molestia de conectarme 'a manopla' ya no la tengo.
Igual le voy a pegar una mirada al que me decis.

Y ya que tenes un tema resuelto y vas a mirar que mas hay por ahi, fijate este paquete que parece piola (recien lo descubro buscando otra cosa, como suele suceder):

[http://www.kde-apps.org/content/show.php/Wireless+Assistant?content=21832](http://www.kde-apps.org/content/show.php/Wireless+Assistant?content=21832)

---

### Post by fedeavila on 2008-06-29
Hola alguien sabe como hacer que se escuche el sonido en un video .3GP ¿?
Tengo los codecs de restricted-extras, me funca todo al 100% solamente eso de los videos .3GP que segun estuve buscando otras personas tambien tuvieron este problema.

Por "ahi" lei que habia que añadir en source.list los repositorios de Medibuntu, lo hice pero cuando pongo sudo apt-get update me da error que algo de una llave esta bloqueada...

(igual ni se si esto me lo arreglaria...)

alguna sugerencia? graxxx

---

### Post by juanman on 2008-07-01
> **fedeavila said:**
> Hola alguien sabe como hacer que se escuche el sonido en un video .3GP ¿?
Tengo los codecs de restricted-extras, me funca todo al 100% solamente eso de los videos .3GP que segun estuve buscando otras personas tambien tuvieron este problema.

Por "ahi" lei que habia que añadir en source.list los repositorios de Medibuntu, lo hice pero cuando pongo sudo apt-get update me da error que algo de una llave esta bloqueada...

(igual ni se si esto me lo arreglaria...)

alguna sugerencia? graxxx

Es xq te faltó agregar la key del servidor de medibuntu. Copia y pegá esto en consola y hace un apt-get update (o usa synaptic, más facil :P)
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

Ahora instalá el paquete w32codecs y ya debería funcar...

Si seguís teniendo problemas con el repositorio, directamente bajá el paquete de [http://packages.medibuntu.org/pool/non-free/w/w32codecs/w32codecs_20071007-0medibuntu2_i386.deb](http://packages.medibuntu.org/pool/non-free/w/w32codecs/w32codecs_20071007-0medibuntu2_i386.deb) e instalalo

---

### Post by pol666 on 2008-07-01
lo que mas me cuesta es el sonido 5.1, Dejar andando la Virtual Box con todo sus componentes bien, la impresora, y creo que nada mas.

EDIT: ME equivoque de pestaña al contestar un tema ^^ este mensaje borrenlo jeje

---

### Post by El Gaucho on 2008-07-04
> **santiagoward2000 said:**
> Hola!
Xubuntu viene con un messenger ya instalado, el Pidgin. Si querés usarlo andá a **Applications/Network/Pidgin Instant Messenger**. Ahí agregás tus cuentas y listo. Otro que escuché que es muy bueno (pero que personalmente nunca usé) es el emesene. Está en los repositorios. Para instalarlo, andá a **Applications>System>Add/Remove...** y buscalo ahí.
Para escuchar música, en Xubuntu está el totem (que en realidad está más pensado para ver videos que escuchar música). Sino, te recomiendo que pruebes el Exaile. También lo podés encontrar en Add/Remove... Acordate que antes tenes que instalar los codecs. Abrí una terminal y escribí:
```
sudo apt-get install xubuntu-restricted-extras
```
Esto te instala la mayoría de los codecs, el Flash y el OpenJava.
Saludos!

Hola a todos y disculpen mi segunda preguntonta en el foro, pero lei este post y pude bajar la aplicacion Exaile, lo que no se es como hay que hacer con los codec, o sea, lo de abrir terminal, como hago eso? digo lo de escribir ```
sudo apt-get install xubuntu-restricted-extras
``` la verdad no entiendo, es la primera vez que uso Linux Ubuntu y es mi 2 dia con este SO, disculpen mi ignorancia, lo que quiero es escuchar musica mientras leo el foro. Gracias!

---

### Post by pol666 on 2008-07-05
simple, copia y pegalo en la  terminal ;)

sudo es permisos de administrador
apt-get install comando para instalar
blablabla es el paquete que estas instalando.

hacer eso es LO mismo que si lo buscas en el programa synaptic

---

### Post by santiagoward2000 on 2008-07-05
> **El Gaucho said:**
> Hola a todos y disculpen mi segunda preguntonta en el foro, pero lei este post y pude bajar la aplicacion Exaile, lo que no se es como hay que hacer con los codec, o sea, lo de abrir terminal, como hago eso? digo lo de escribir ```
sudo apt-get install xubuntu-restricted-extras
``` la verdad no entiendo, es la primera vez que uso Linux Ubuntu y es mi 2 dia con este SO, disculpen mi ignorancia, lo que quiero es escuchar musica mientras leo el foro. Gracias!

Hola!
No te preocupes por preguntar, para eso estamos!
Para instalar los codecs, podes hacerlo de 2 formas:
1)
  a) Vas a Aplicaciones->Accesorios->Terminal
  b) Escribis: ```
sudo apt-get install xubuntu-restricted-extras
```
  c) Te va a pedir tu contraseña. La pones.
  d) Esperas a que se instale.
  e) Listo!

2)
  a) Vas a Aplicaciones->Sistema->Synaptic.
  b) Buscas **xubuntu-restricted-extras**.
  c) Lo marcas para que se instale.
  d) Haces click en aplicar.
  e) Esperas a que se instale.
  d) Listo!

Espero que te sirva! Sino avisa!
Suerte!

---

### Post by lega on 2008-07-05
en xubuntu no es como en Ubuntu que al intentar reproducir un mp3 por ejemplo, te ofrece instalar los codecs necesarios para reproducir ese archivo?

---

### Post by santiagoward2000 on 2008-07-05
> **lega said:**
> en xubuntu no es como en Ubuntu que al intentar reproducir un mp3 por ejemplo, te ofrece instalar los codecs necesarios para reproducir ese archivo?

Estoy **casi** seguro que no. Jeje. La verdad que yo instalé todos los codecs apenas instalé Xubuntu. Voy a probar con el LiveCD a ver si me lo ofrece y despues te cuento.
Saludos!

_EDIT:_
Recien trate de arir un mp3 con el Totem y me ofrecio instalar los codecs. Pero cuando instale el Exaile y trate de abrirlo, solo me salto un cartel que decia que no lo tengo.

---

### Post by fedeavila on 2008-07-07
> **juanman said:**
> Es xq te faltó agregar la key del servidor de medibuntu. Copia y pegá esto en consola y hace un apt-get update (o usa synaptic, más facil :P)
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

Ahora instalá el paquete w32codecs y ya debería funcar...

Si seguís teniendo problemas con el repositorio, directamente bajá el paquete de [http://packages.medibuntu.org/pool/non-free/w/w32codecs/w32codecs_20071007-0medibuntu2_i386.deb](http://packages.medibuntu.org/pool/non-free/w/w32codecs/w32codecs_20071007-0medibuntu2_i386.deb) e instalalo

Buenas! Gracias por la respuesta! Me baje el archivo y lo instale exitosamente pero... Sigue sin escucharse nadap... Vos como haces para escuchar los videos 3GP en ubuntu?

---

### Post by Mauro22 on 2008-07-08
> **fedeavila said:**
> Vos como haces para escuchar los videos 3GP en ubuntu?

Discupla si ya lo respondiste, probaste con VLC?

---

### Post by fedeavila on 2008-07-09
> **Mauro22 said:**
> Discupla si ya lo respondiste, probaste con VLC?

Sisisi! Ya me lo instale posteriormente al pack de Medibuntu pero... Nada... Gracias igual :)

---

### Post by lega on 2008-07-12
Alguien sabe como tengo que hacer para que los iconos se vean iguales en todos lados? cambie por unos que en ciertos lados se ven los clásicos de gnome, dejo las capturas, la segunda es la que no me muestra los iconos bien.

---

### Post by JorgeGhersa on 2008-07-13
Hola a todos, hace mucho no pasaba por acá... Dejo mi preguntonta, que no sé si es tonta la respuesta al problema, pero sí lo es la importancia del mismo ( muy mínima... ).

Hice una instalación borra-todo de Hardy en mi vieja y querida notebook, que los memoriosos recordarán por [los problemas que me daba con Gutsy]("http://ubuntuforums.org/showthread.php?t=619453") y porque el wifi andaba raro en Feisty. Bueno, todo PERFECTO hoy día, salvo el más minimín detalle.

Vieron que el reloj ahora integra la data del clima si uno quiere? Le puse como Ubicación "Aeroparque", porque la que figura como "Buenos Aires" nunca dice nada, y me pasa los datos bien. Pero al reiniciar la compu y con la conexión andando, no tengo información del clima, y cuando me fijo, es porque al empezar de nuevo asume que nuestro querido Aeroparque queda en la zona horaria... "Indico/Mayotte".

¿Alguna manera de enseñarle geografía al programita?

---

### Post by sergiom99 on 2008-07-14
pregunta casi filosofica:
hay diferencias entre ALSA y PulseAudio? pros & cons?
cualquier data que puedan tirar para ilustrarme sera bienvenida.

---

### Post by Mauro22 on 2008-07-15
Todavia no lo termine de leer :D

ALSA:

[http://es.wikipedia.org/wiki/Arquitectura_de_Sonido_Avanzada_para_Linux](http://es.wikipedia.org/wiki/Arquitectura_de_Sonido_Avanzada_para_Linux)

PulseAudio:

[http://es.wikipedia.org/wiki/PulseAudio](http://es.wikipedia.org/wiki/PulseAudio)

---

### Post by _kAz_ on 2008-07-15
Gente necesito saber la línea de comando para **vaciar la papelera de reciclaje como administrador desde la terminal**.
"Gráficamente" no me deja acceder a la papelera cuando estoy en esa categoría de usuario.

Desde ya, thanks! :)

---

### Post by Mauro22 on 2008-07-15
```
cd /home/usuario/.Trash
```
```
rm -r *
```

:confused::confused:

---

### Post by pol666 on 2008-07-15
> **sergiom99 said:**
> pregunta casi filosofica:
hay diferencias entre ALSA y PulseAudio? pros & cons?
cualquier data que puedan tirar para ilustrarme sera bienvenida.



hasta donde la deduccion me lo permite. Creo yo que alsa son los driver, en cambio Pulceaudio es un cliente de sonido, el que lo gestiona, esto permite tener varios sonidos sonando a la vez cosa que antes con alsa y esd no se podia. tambien tiene una mejor integracion con sonido 5.1, microfonos, juegos, etc.

pulceaudio el mejor invento :D

---

### Post by marianom on 2008-07-15
> **Mauro22 said:**
> ```
cd /home/usuario/.Trash
```
```
rm -r *
```

:confused::confused:

Decían por ahí que la papelera en HH estaba en otro lugar, ya no me acuerdo cual.

---

### Post by Mauro22 on 2008-07-15
Gracias!

seria:

```
cd /home/usuario/.local/share/Trash/files
```

---

### Post by faktorqm on 2008-07-18
De todas maneras les recuerdo que el usuario root **NO DEBE USARSE**, mucho menos para borrar archivos... sólo eso. Salu2!

---

### Post by sergiom99 on 2008-07-18
que != hay entre un sudo y hacerlo como root?
no puedo hacer lo mismo de ambas maneras?

---

### Post by Hei Ku on 2008-07-18
Podes hacer casi lo mismo. Hay ciertas manipulaciones en el kernel que solo podes hacerlas con root. La diferencia es que el acceso con sudo es limitado en tiempo y solo a la aplicacion que corres en ese momento. En cambio el acceso con root es ilimitado.

---

### Post by FlyerDie on 2008-07-18
> **sergiom99 said:**
> que != hay entre un sudo y hacerlo como root?
no puedo hacer lo mismo de ambas maneras?


Es que la idea de sudo es que el comando que tires sea bajo conciencia, osea de forma deliberada...en cambio podes estar logoneado como root y por error tirar un comando critico y no tenes rollback.

En definitiva, al ya tipear sudo es porque sabes que es lo que queres hacer ;)

---

### Post by sergiom99 on 2008-07-18
si, eso es lo que yo pensaba, pero no estaba seguro de que cosas se pueden hacer como root o con sudo.

---

### Post by Darkade on 2008-07-18
Eeey, Saludos desde México y no quiero ofender a nadie pero el español argentino suena taaan distinto, jajaja, claro que supongo q es reciproco. :lolflag:

> **sergiom99 said:**
> que != hay entre un sudo y hacerlo como root?
no puedo hacer lo mismo de ambas maneras?

La diferencia es que cuando loggeas como root las cosas se van a ejecutar con los archivos de configuraciòn de root, sin mencionar que pueden llegar a pasar accidentes. Mientras que si usas sudo las cosas se ejecutan con los archivos de configuración del usuario. Tambien para utilizar apps graficos deberias de utilizar gksudo.

Si quieres saber mas puedes revisar este thread
[http://ubuntuforums.org/showthread.php?t=838542](http://ubuntuforums.org/showthread.php?t=838542)

y esta pagina
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by juanman on 2008-07-22
> **fedeavila said:**
> Buenas! Gracias por la respuesta! Me baje el archivo y lo instale exitosamente pero... Sigue sin escucharse nadap... Vos como haces para escuchar los videos 3GP en ubuntu?

Perdon por el cuelgue, me parece q esto de hacer un thread para preguntontas no funciona... Habria q hacer las preguntas en threads separados...
Como sea, efectivamente no funciona el 3gp con los w32codecs. Yo lo habia instalado para ver rmvb y funcionaron... Para los 3gp tenes q instalar el realplayer (no es libre pero si gratuito). Lo probe y funcionó... Yo lo baje desde la pagina [http://spain.real.com/player/select/](http://spain.real.com/player/select/) y ejecute el .bin desde consola, pero creo q hay algun .deb por ahí... Aunq no encontré ninguno para hardy (probablemente los de gutsy anden, no los probe)...
Otra solucion, para usar software libre, es instalar las ultimas versiones svn de mplayer y ffmpeg, pero vas a tener q compilar...

Saludos

---

### Post by marianom on 2008-07-22
Bueno, el problema no es del thread sino que las preguntas ya no son tan tontas. Aca deberían quedar las preguntas extremadamente sencillas... (¿como me logueo como root? ¿como hago un backup de mi xorg?, etc, etc)

---

### Post by Hei Ku on 2008-07-22
Es que los chicos van creciendo!! :lolflag:

---

### Post by santiagoward2000 on 2008-09-08
Uhh! Me acaba de entrar una duda que creo que podría considerarse **Preguntonta**!
Estoy imprimiendo algo medio largo (unas 12 hojas) y veo que me las imprime en el orden del documento (1,2,3,...,12). El tema es que las hojas quedan alrevés (12,11,10,...,1) porque las que salen van cayendo arriba de las anteriores. ¿Se puede configurar para que se impriman alrevés, así no tengo que ordenarlas a mano después?
Gracias!

---

### Post by valucha on 2008-09-08
[COLOR="DarkOrchid"]Les hago unas preguntas con respecto a KDE...
1)con respecto a los themes en kde look me da opciones de kde4, gtk1.x, y theme manager. El gtk sé que es para gnome, pero qué hace en kde-look?, acaso es para las aplicaciones que usan gtk en kde?, si es así como lo instalo?... Y por otro lado... ¿ENtre el kde4 y el theme manager, cuál es para Kubuntu con KDE4..? Es decir, obviamente que el KDE4 lo puedo instalar y hacer funcionar, pero quñ es el theme manager y cómo lo instalo?.

2) ¿Qué es plasma y plasmoid?... sería algo como lo screenlets?. si es así como se instala= porque haciendo sudo apt-get install plasma o sudo apt-get install plasmoids no está...

3) Hay sistema de archivos comprimidos que no puedo ver, como el rar o el .gz. Me bajé el unrar, 7zip y un montón de descompresores pero sigo sin poder verlos ni mucho menos descomprimirlos... ¿Cuál es el mas completito para poder desxcomprimir y comprimir lo que sea?

Creo que nada más por ahora. Muchas gracias desde ya.


Val[/COLOR]

---

### Post by leo_rockway on 2008-09-08
> **valucha said:**
> Les hago unas preguntas con respecto a KDE...

2) ¿Qué es plasma y plasmoid?... sería algo como lo screenlets?. si es así como se instala= porque haciendo sudo apt-get install plasma o sudo apt-get install plasmoids no está...

Es algo que viene incluido en KDE4: [http://es.wikipedia.org/wiki/Plasma_(KDE](http://es.wikipedia.org/wiki/Plasma_(KDE))

> **valucha said:**
> 
3) Hay sistema de archivos comprimidos que no puedo ver, como el rar o el .gz. Me bajé el unrar, 7zip y un montón de descompresores pero sigo sin poder verlos ni mucho menos descomprimirlos... ¿Cuál es el mas completito para poder desxcomprimir y comprimir lo que sea?

El programa de KDE que se usa para archivos comprimidos se llama Ark.
[http://es.wikipedia.org/wiki/Ark](http://es.wikipedia.org/wiki/Ark)

---

### Post by guillermolisi on 2008-09-08
> 2) ¿Qué es plasma y plasmoid?... sería algo como lo screenlets?. si es así como se instala= porque haciendo sudo apt-get install plasma o sudo apt-get install plasmoids no está...

Plasma ES el escritorio grafico de KDE4 y los plasmoids son sus componentes, equivalentes a los applets/widgets que funcionan bajo Kde3.
En este link, [http://plasma.kde.org/cms/1029](http://plasma.kde.org/cms/1029) (en Ingles), tenes una vision directa de cual es la filosofia y el motor que genero KDE4, Plasma, etc.

> 1)con respecto a los themes en kde look me da opciones de kde4, gtk1.x, y theme manager. El gtk sé que es para gnome, pero qué hace en kde-look?, acaso es para las aplicaciones que usan gtk en kde?, si es así como lo instalo?... Y por otro lado... ¿ENtre el kde4 y el theme manager, cuál es para Kubuntu con KDE4..? Es decir, obviamente que el KDE4 lo puedo instalar y hacer funcionar, pero quñ es el theme manager y cómo lo instalo?.

Es que la gente de KDE es abierta a otras alternativas como Gnome-look (fijate que en el sitio de KDE-look hay links a otros sites y uno es el de Gnome) (es mi suposicion tratando de explicar lo que se observa).

El theme Manager de KDE es para administrar los temas del KDM (display manager). Todavia no se si hay uno para KDE4 (no me preocupe todavia por eso ya que hay otras cosas que faltan que me parecen mas importantes)

El paquete del Theme Manager para KDE dice:
> **theme manager for KDM**
kdmtheme is a theme manager for KDM. It provides a KDE Control Module (KCM)
that allows you to easily install, remove and change your KDM themes.

---

### Post by valucha on 2008-09-08
[COLOR="DarkOrchid"]¿estás seguro que el theme manager es el KDM?.. yo también creia eso pero mirá lo que la gente postea como "theme manager" en kde-look.org  [http://www.kde-look.org/index.php?xcontentmode=8](http://www.kde-look.org/index.php?xcontentmode=8)[/COLOR]

---

### Post by leo_rockway on 2008-09-08
> **valucha said:**
> [COLOR="DarkOrchid"]¿estás seguro que el theme manager es el KDM?.. yo también creia eso pero mirá lo que la gente postea como "theme manager" en kde-look.org  [http://www.kde-look.org/index.php?xcontentmode=8](http://www.kde-look.org/index.php?xcontentmode=8)[/COLOR]

Theme Manager incluye fondos de pantalla, colores, estilos, iconos, fuentes y salvapantallas.

Hace alt+f2 > kcontrol > Appearance & Themes > Theme Manager y lo vas a ver.

EDIT: lo de los temas GTK es, efectivamente, para darle un look nativo a esas aplicaciones.

---

### Post by guillermolisi on 2008-09-08
> **valucha said:**
> [COLOR=DarkOrchid]¿estás seguro que el theme manager es el KDM?.. yo también creia eso pero mirá lo que la gente postea como "theme manager" en kde-look.org  [http://www.kde-look.org/index.php?xcontentmode=8](http://www.kde-look.org/index.php?xcontentmode=8)[/COLOR]

El Theme Manager es para administrar los temas del motor grafico de KDE3 que se llama KDM (el equivalente al GDM de Gnome), tal como bien dijo Leo.

---

### Post by santiagoward2000 on 2008-09-09
> **santiagoward2000 said:**
> Uhh! Me acaba de entrar una duda que creo que podría considerarse **Preguntonta**!
Estoy imprimiendo algo medio largo (unas 12 hojas) y veo que me las imprime en el orden del documento (1,2,3,...,12). El tema es que las hojas quedan alrevés (12,11,10,...,1) porque las que salen van cayendo arriba de las anteriores. ¿Se puede configurar para que se impriman alrevés, así no tengo que ordenarlas a mano después?
Gracias!

Jaja! Ahí vi la opción #-o

---

### Post by WanderingKnight on 2008-09-09
> 1)con respecto a los themes en kde look me da opciones de kde4, gtk1.x, y theme manager. El gtk sé que es para gnome, pero qué hace en kde-look?, acaso es para las aplicaciones que usan gtk en kde?, si es así como lo instalo?

Viene instalado... como dice Leo, KDE trae integrada una opción para aplicar el theme de Qt a las aplicaciones de GTK.

Por qué GNOME todavía no hizo lo propio con Qt es algo que a nunca voy a entender. La única forma de cambiar la apariencia de las aplicaciones de Qt en GNOME es editar los archivos a mano (o instalar KDE y editarlo desde ahí).

PD: Ahora seguro que salta alguno con algún programita que alguien hizo justamente para este fin, en cuyo caso me sorprenderé aún más al ver que GNOME todavía no lo integró...

---

### Post by sajnox on 2008-09-09
Si, basicamente la unica solucion que encontra para integrar el amarok y k3b fue instalar Kcontrol y desde ahi setear

---

### Post by valucha on 2008-09-09
[COLOR="DarkOrchid"]Ya está entendí tutto :) mil gracias chicos.[/COLOR]

---

### Post by emiesteban on 2009-04-20
Pregunta:
Como puedo ver un archivo en stream sin que me lo precachee de la red el dolphin?
si no soy claro explico un poco mas, cuando quiero ver una peli que tengo en la red, accedo al dolphin y accedo al otro pc, cuando ejecuto el archivo, se abre el programa, seguido comienza el cacheo completo de los 700mb o mas por el dolphin,y recien ahi la aplicacion abre el archivo, no solo pasa con peliculas, con cualquier archivo, sea pdf o cualquier otro, y eso quier o evitar, y que lo lea desde la red, como hacia con mi kubuntu 7.04
uso Kubuntu 8.10 y KDE4

---

### Post by luks911 on 2009-04-21
> **emiesteban said:**
> Pregunta:
Como puedo ver un archivo en stream sin que me lo precachee de la red el dolphin?
si no soy claro explico un poco mas, cuando quiero ver una peli que tengo en la red, accedo al dolphin y accedo al otro pc, cuando ejecuto el archivo, se abre el programa, seguido comienza el cacheo completo de los 700mb o mas por el dolphin,y recien ahi la aplicacion abre el archivo, no solo pasa con peliculas, con cualquier archivo, sea pdf o cualquier otro, y eso quier o evitar, y que lo lea desde la red, como hacia con mi kubuntu 7.04
uso Kubuntu 8.10 y KDE4

Creo entender, me ha pasado con FF y el totem un par de veces. Una alternativa, tal vez no sea lo más elegante pero creo que sirve, es buscar la dirección/url del stream (copiando un link, viendo el código de la página en cuestión, depende), copiarla y pegarla en algún reproductor, ya sea totem, mplayer o vlc.

---

### Post by ADICTOALMAXIMO on 2009-04-21
ma gusta la interfas grafica

NO

se que seria sin ella

¬¬

---

### Post by c4d0rn4 on 2009-04-21
> **emiesteban said:**
> Pregunta:
Como puedo ver un archivo en stream sin que me lo precachee de la red el dolphin?
si no soy claro explico un poco mas, cuando quiero ver una peli que tengo en la red, accedo al dolphin y accedo al otro pc, cuando ejecuto el archivo, se abre el programa, seguido comienza el cacheo completo de los 700mb o mas por el dolphin,y recien ahi la aplicacion abre el archivo, no solo pasa con peliculas, con cualquier archivo, sea pdf o cualquier otro, y eso quier o evitar, y que lo lea desde la red, como hacia con mi kubuntu 7.04
uso Kubuntu 8.10 y KDE4

Lo primero que se me ocurre es que directamente montes las carpetas de red a una carpeta tuya. De esa manera va a tomar el recurso de red como si fuera parte de tu pc y no algo de la red.

Lo que sí no se es el tema de quien está haciendo el caché. Creo que kubuntu todavía trae Konqueror; si te trae problemas dolphin hacelo con Konqueror. O de ultima, instalá nautilus... pero no me parece una opción util.

Sabés quien hace el caché?

---

### Post by emiesteban on 2009-04-21
lo hace el dolphin al cache, tendria que ver si el konkeror esta instalado...

---

