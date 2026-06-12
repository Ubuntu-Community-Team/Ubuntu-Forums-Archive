---
title: "No puedo solucionar el problema de &quot;Waiting for network configuration&quot;"
date: 2012-01-21
forum: Software
---

### Post by 53RG10 on 2012-01-21
Hola a todos.
Me imagino que varios conocerán este problema al arrancar Ubuntu (aunque yo tengo Kubuntu 11.10):
Primero aparece durante un minuto“Waiting for network configuration”,  después “Waiting an additional 60 seconds for network configuration” y  termina con "Booting system without full network configuration".
Yo busqué la solución en Google primero, como siempre  [IMG]http://www.kubuntu-es.org/sites/all/modules/smileys/packs/esdebian/icon_smile.gif[/IMG] , pero tengo un problema.
La solución que utilicé fue la siguiente, que no recuerdo de qué página la saqué, porque la guardé en un .txt:
 > Editamos el archivo Interface
sudo nano /etc/network/interfaces
--- en el archivo veremos esto (depende de cuantas placas de red tengan) :
auto lo
iface lo inet loopback
 auto wlan0
iface wlan0 inet dhcp
 auto eth0
iface eth0 inet dhcp
 bueno , lo unico que deben hacer es poner un simbolo cardinal (#)  delante de todo menos de las dos primeras lineas, osease, les quedara de  esta manera :
 auto lo
iface lo inet loopback
 #auto wlan0
#iface wlan0 inet dhcp
 #auto eth0
#iface eth0 inet dhcp
 - Guardan el archivo , y reinician... 
 Bueno, mi archivo quedó así:
 ```
auto lo
iface lo inet loopback #auto dsl-provider
#iface dsl-provider inet ppp
#pre-up /sbin/ifconfig nas0 up # line maintained by pppoeconf
#provider dsl-provider
 #auto nas0
#iface nas0 inet manual

``` Cuando reinicié no aparecieron los mensajes, pero cuando volví a  reiniciar, volvieron, y revisando el archivo me había quedado así:
 ```
auto lo
iface lo inet loopback #auto dsl-provider
#iface dsl-provider inet ppp
#pre-up /sbin/ifconfig nas0 up # line maintained by pppoeconf
#provider dsl-provider
  #auto nas0
#iface nas0 inet manual
 auto dsl-provider
iface dsl-provider inet ppp
provider dsl-provider auto nas0
iface nas0 inet manual

``` Como tengo un módem USB para usar con Telefónica, yo al inicio, para conectarme, tengo que poner lo siguiente en la Terminal:
 # br2684ctl -b -c 0 -a 8.35
  br2684ctl[3826]: Interface "nas0" created sucessfully
  br2684ctl[3826]: Communicating over ATM 0.8.35, encapsulation: LLC
  br2684ctl[3826]: Interface configured 4- # pppoeconf

 Así me conecto siempre, entonces ahí está mi problema, si cada vez  que me conecte se me agrega esa línea que me hace perder 2 minutos al  inicio, ¿cómo hago para solucionarlo?
No soy novato, pero casi, sólo llevo unos meses en Linux.
Espero haber sido claro, sino acá estoy para las preguntas.
Saludos

---

### Post by BC59 on 2012-01-21
Lo he visto como solución hace mucho y la verdad es que nunca lo he probado, pero intenta lo, es fácil:

```
sudo apt-get remove network-manager
sudo apt-get install wicd

```

Si no funciona el truco, lo pones al reves:

```
sudo apt-get remove wicd
sudo apt-get install network-manager

```

---

### Post by 53RG10 on 2012-01-21
> **BC59 said:**
> Lo he visto como solución hace mucho y la verdad es que nunca lo he probado, pero intenta lo, es fácil:

```
sudo apt-get remove network-manager
sudo apt-get install wicd

```Si no funciona el truco, lo pones al reves:

```
sudo apt-get remove wicd
sudo apt-get install network-manager

```
Gracias, tenía instalado los 2, así que desinstalé el network-manager (ya que en un principio tenía instalado este solo y el problema estaba) y el problema sigue. Lo que pude confirmar es que cada vez que utilizo pppoeconf para conectarme (no pude conseguir otra forma de hacerlo), me agrega esas líneas que son las que me hacen perder los 2 minutos al inicio.
No sé qué otra cosa puedo hacer para que no me las agregue o para que no me tarde los 2 minutos.
Gracias otra vez, y ojalá encuentren la solución, porque es bastante molesto tener que esperar 2 minutos, y 20 segundos para arrancar, cuando Kubuntu, en mi máquina por lo menos, lo hace en 20 segundos.

---

### Post by mama21mama on 2012-01-21
Lo que menciona aparece en el [bug #811441]("https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/811441")

Todavia no le dieron una solucion definitiva, me parece.

Si es molesto.

---

### Post by 53RG10 on 2012-01-21
> **mama21mama said:**
> Lo que menciona aparece en el [bug #811441]("https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/811441")
Todavia no le dieron una solucion definitiva, me parece.
Si es molesto.
Sí, el bug lo conozo, y probé varias soluciones que hay en internet al respecto, aunque es probable que no esté solucionada del todo como bien decís.
La solución que puse yo al principio debe servir para cualquier conexión a internet que no sea con el pppoeconf, porque si yo realizo esa solución, y no uso el pppoeconf, no tarda los 2 minutos. Pero mi problema es las líneas que me crea el pppoeconf cuando lo ejecuto.
Por eso mi pregunta va más que nada por ese lado, a ver si a alguien se le ocurre como puedo hacer para que no me cree esas líneas.
Saludos

---

### Post by mama21mama on 2012-01-21
Podes hacer con tu config

```
sudo chattr +i /etc/network/interfaces
```

Esto hace inmutable a ese archivo e impide que se escriba por NetworkManager

Para dejarlo mutable (que se pueda escribir) usa -i

Saludos

---

### Post by 53RG10 on 2012-01-21
> **mama21mama said:**
> Podes hacer con tu config

```
sudo chattr +i /etc/network/interfaces
```Esto hace inmutable a ese archivo e impide que se escriba por NetworkManager

Para dejarlo mutable (que se pueda escribir) usa -i

Saludos
Gracias por el intento, pero no estaba seguro si necesitaba escribir el archivo para conectarse, ahora me doy cuenta que sí:
```
# pppoeconf
mv: no se puede mover «/tmp/interfaces.pppoeconf.6qehGG» a «/etc/network/interfaces»: Operación no permitida
```Así que tuve que volver a hacerlo mutable, y tendré que seguir con el arranque lento :(
Saludos

---

### Post by 53RG10 on 2012-01-25
Se me ocurrió una única solución, pero no sé si existe :confused:.
Quedó claro que lo que me genera el problema (o molestia) a mí, es cuando uso el pppoeconf. Bueno, quisiera saber si hay algún otro programa que me permita conectarme de esta manera, porque yo no encontré ninguno.
Espero sugerencias ;)
Saludos

---

### Post by guillermolisi on 2012-01-26
> **53RG10 said:**
> Se me ocurrió una única solución, pero no sé si existe :confused:.
Quedó claro que lo que me genera el problema (o molestia) a mí, es cuando uso el pppoeconf. Bueno, quisiera saber si hay algún otro programa que me permita conectarme de esta manera, porque yo no encontré ninguno.
Espero sugerencias ;)
Saludos
La otra solucion es configurar el modem ADSL como router, si es que esta como bridge, y utilizar la conexion Ethernet (si posee) en lugar de la USB.

De esta forma el mismo modem se encarga de establecer la conexion y tu PC solamente debe tener configurada la placa de red para que use la IP del modem (router) como gateway (asi sabe por donde recibir y enviar paquetes de datos).

---

### Post by 53RG10 on 2012-01-26
> **guillermolisi said:**
> La otra solucion es configurar el modem ADSL como router, si es que esta como bridge, y utilizar la conexion Ethernet (si posee) en lugar de la USB.

De esta forma el mismo modem se encarga de establecer la conexion y tu PC solamente debe tener configurada la placa de red para que use la IP del modem (router) como gateway (asi sabe por donde recibir y enviar paquetes de datos).
Gracias. Es que el modem es un ARESCOM que sólo tiene entrada de red, y no salida, así que sólo puedo conectarme por acá. Además tengo usuario y contraseña, que cada vez que uso el pppoeconf, tengo que poner la contraseña.
No sé si estoy equivocado, no soy un experto en la materia, porque nunca tuve un router, siempre me conecté directamente porque tengo una sola PC.
Saludos

---

### Post by guillermolisi on 2012-01-27
> **53RG10 said:**
> Gracias. Es que el modem es un ARESCOM que sólo tiene entrada de red, y no salida, así que sólo puedo conectarme por acá. Además tengo usuario y contraseña, que cada vez que uso el pppoeconf, tengo que poner la contraseña.
No sé si estoy equivocado, no soy un experto en la materia, porque nunca tuve un router, siempre me conecté directamente porque tengo una sola PC.
Saludos
Es un modem ADSL ?
Entonces lo que mencionas como salida de red es lo que tenes que usar luego de verificar si esta en modo bridge o router.

El user y pass se ingresa en los comapos correspondientes del modem (estando como router) para que realice la conexion por cuenta propia, liberandote y liberando a la PC de tener que realizarla.

Si no tenes el manual, Google y tambien ADSLZone.

---

### Post by 53RG10 on 2012-01-27
> **guillermolisi said:**
> Es un modem ADSL ?
Entonces lo que mencionas como salida de red es lo que tenes que usar luego de verificar si esta en modo bridge o router.

El user y pass se ingresa en los comapos correspondientes del modem (estando como router) para que realice la conexion por cuenta propia, liberandote y liberando a la PC de tener que realizarla.

Si no tenes el manual, Google y tambien ADSLZone.
Muchísimas gracias, encontré la solución en [este post]("http://www.adslzone.net/postt42.html") de la página de ADSLZone: En el 3er mensaje (que es del mismo que creó el tema), pone lo siguiente:
> pues lo he arreglado yo solito jejejeje... 
 
Cada vez que configuraba la cuenta, con la tarjeta, el proveedor... 
al final se abría el kinternet, y hacía como que se conectaba... pero nada. 
Si le daba a cerrar el kinternet me preguntaba si quería que se volviese  a inciar junto con el sistema, y yo ingenuamente, le daba que si. 
 
Así que lo solucioné así de fácil, le dije que no en una ocasión, y así cada vez que conecto tengo internet. Ahí también recordé que el pppoeconf, en un momento me preguntaba si quería que se conecte al inicio, pero yo hacía todo tan automático ya, que ni me fijaba y ponía todo que sí. Ahora a esa pregunta le pongo que no y el sistema me carga en 30 segundos. La única diferencia es que yo tengo que seguir usando el pppoeconf para conectarme con su respectivo nombre de usuario y contraseña, pero lo que yo quería solucionar, era el tema del arranque molesto.
Nuevamente, muchísimas gracias, ya empezaba a pensar que no tenía solución.
Saludos

---

### Post by hectorivand on 2012-01-28
Te recomiendo que te compres un Modem ADSL Ethernet, te vas a evitar futuros problemas y en Mercadolibre encontras usados desde 50 pesos, si no queres gastar le pedís a Telefónica o a quien sea tu proveedor un cambio de Modem. 

Los Modems ADSL USB ni en Windows funcionan bien. Me acuerdo del Amigo, una terrible porquería.

[http://www.google.com.ar/search?q=modem+amigo+usb&um=1&ie=UTF-8&hl=es&tbm=isch&source=og&sa=N&tab=wi&ei=mxQkT7vUJsa2tweQ2fGZDw&biw=1280&bih=675&sei=phQkT4LvJ4mltwffjK2jCw](http://www.google.com.ar/search?q=modem+amigo+usb&um=1&ie=UTF-8&hl=es&tbm=isch&source=og&sa=N&tab=wi&ei=mxQkT7vUJsa2tweQ2fGZDw&biw=1280&bih=675&sei=phQkT4LvJ4mltwffjK2jCw)

---

### Post by 53RG10 on 2012-01-28
> **hectorivand said:**
> Te recomiendo que te compres un Modem ADSL Ethernet, te vas a evitar futuros problemas y en Mercadolibre encontras usados desde 50 pesos, si no queres gastar le pedís a Telefónica o a quien sea tu proveedor un cambio de Modem. 

Los Modems ADSL USB ni en Windows funcionan bien. Me acuerdo del Amigo, una terrible porquería.

[http://www.google.com.ar/search?q=modem+amigo+usb&um=1&ie=UTF-8&hl=es&tbm=isch&source=og&sa=N&tab=wi&ei=mxQkT7vUJsa2tweQ2fGZDw&biw=1280&bih=675&sei=phQkT4LvJ4mltwffjK2jCw](http://www.google.com.ar/search?q=modem+amigo+usb&um=1&ie=UTF-8&hl=es&tbm=isch&source=og&sa=N&tab=wi&ei=mxQkT7vUJsa2tweQ2fGZDw&biw=1280&bih=675&sei=phQkT4LvJ4mltwffjK2jCw)
Gracias por el consejo, empiezo a darme cuenta que es así como decís... Lo que pasa, es que estoy esperando a Telecentro, que ya pasó los cables por la puerta de mi casa, para cambiarme, por eso no cambio el módem. Y te comento que el que ellos me dieron es ese "querido" Amigo, y no lo pude hacer andar ni en Windows. Por suerte tenía este en casa que hace mucho me quedó de algún proveedor de Internet.
Saludos

---

