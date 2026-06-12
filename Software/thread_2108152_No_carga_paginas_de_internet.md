---
title: "No carga paginas de internet"
date: 2013-01-23
forum: Software
---

### Post by GrecoSCS on 2013-01-23
Al abrir el navegador, no carga ninguna pagina, la conexion a internet esta activa y abre paginas https como google o facebook, pero toda pagina que tenga http no la carga. La terminal funciona correctamente, puedo actualizar y bajar paquetes, JDownloader no descarga.

Revise la configuracion a internet con mi proveeder y esta todo correcto.

Tengo instalado como sistema operativo Ubuntu 10.04, el navegador que utilizo es Chrome (en firefox, directamente no abre nada), les agradeceria mucho que me ayuden con este problema, por favor.

---

### Post by papibe on 2013-01-23
Hola GrecoSCS.

Pueder ejecutar estos commandos y publicar sus resultados?
```
ifconfig

nslookup ubuntu.com

dig ubuntuforums.org

route -n
```
Saludos.

---

### Post by guillermolisi on 2013-01-24
Estas usando 10.04 con Gnome y NetworkManager o lo cambiaste por otro gestor de redes tipo WiCD o similar ?

Por lo que comentas que en consola/terminal podes actualizar y bajar paquetes pareceria un problema relacionado con algun componente del escritorio grafico que realiza la gestion de red.

Solo para probar, podrias abrir un navegador web y colocar la IP en lugar de la URL de algun sitio conocido, como por ejemplo google.com ? (su IP es 173.194.42.0 entre otras)

Contanos que resultado obtuviste.

Si funciona, claramente el problema esta en la asignacion de los DNS del gestor de redes grafico (NManager o el que estes usando).

---

### Post by GrecoSCS on 2013-01-24
[COLOR="Red"]papibe[/COLOR]: te mando los resultados

ifconfig

eth0      Link encap:Ethernet  direcciónHW 44:87:fc:1d:7b:86  
          Direc. inet:192.168.1.33  Difus.:192.168.1.255  Másc:255.255.255.0
          Dirección inet6: fe80::4687:fcff:fe1d:7b86/64 Alcance:Enlace
          ACTIVO DIFUSIÓN FUNCIONANDO MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:633 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:679 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:466269 (466.2 KB)  TX bytes:75907 (75.9 KB)
          Interrupción:27 Dirección base: 0x8000 

lo        Link encap:Bucle local  
          Direc. inet:127.0.0.1  Másc:255.0.0.0
          Dirección inet6: ::1/128 Alcance:Anfitrión
          ACTIVO BUCLE FUNCIONANDO  MTU:16436  Métrica:1
          Paquetes RX:654 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:654 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:0 
          Bytes RX:32740 (32.7 KB)  TX bytes:32740 (32.7 KB)

wlan0     Link encap:Ethernet  direcciónHW 68:a3:c4:b9:06:b0  
          ACTIVO DIFUSIÓN MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:0 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:0 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupción:17 Memoria:f8090000-f8090100


nslookup ubuntu.com

Server:		192.168.1.1
Address:	192.168.1.1#53

Non-authoritative answer:
Name:	ubuntu.com
Address: 91.189.94.156


dig ubuntuforums.org

; <<>> DiG 9.7.0-P1 <<>> ubuntuforums.org
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 33904
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;ubuntuforums.org.		IN	A

;; ANSWER SECTION:
ubuntuforums.org.	473	IN	A	91.189.94.12

;; Query time: 34 msec
;; SERVER: 192.168.1.1#53(192.168.1.1)
;; WHEN: Thu Jan 24 19:07:51 2013
;; MSG SIZE  rcvd: 50


route -n

Tabla de rutas IP del núcleo
Destino         Pasarela        Genmask         Indic Métric Ref    Uso Interfaz
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0


[COLOR="Green"]guillermolisi[/COLOR]: no cambie a ningun otro gestor de redes, intente ingresar con las IP y no me dio resultado, solo la de google pero como mencione anteriormente me abre por ser una https, al igual que facebook y hotmail.


Gracias a ambos por su colaboracion.

---

### Post by papibe on 2013-01-24
Gracias.

Tu configuración se ve bien. Estoy empezando a pensar que puede ser el browser en vez de la configuración del sistema mismo.

Probemos si desde el terminal puedes acceder páginas sin htpps:
```
wget http://www.ubuntu.com/
```
Avísanos si te da error o si se baja bien la página.

Saludos.

---

### Post by guillermolisi on 2013-01-24
Tambien tengo la misma sospecha sobre el browser y su configuracion.

GrecoSCS, hay alguna posibilidad de probar con otro navegador web en esa misma maquina. Si esta recien instalado, nuevito y sin usar, mejor.

---

### Post by GrecoSCS on 2013-01-24
Disculpen la demora, es que estoy desde windows 7 por el internet y tardo en reiniciar y volver a ubuntu y luego regresar a windows de nuevo, y eso se lleva tiempo.
Probe el codigo tal cual escribiste, pero no resulto:

alumno@Marioli:/usr/bin$ &#65279;wget [http://www.ubuntu.com/](http://www.ubuntu.com/)
wget: orden no encontrada

Lo intente cambiando la direccion, resulto esto:
alumno@Marioli:/usr/bin$ wget http:/www.ubuntu.com
--2013-01-24 20:52:53--  [ftp://http//www.ubuntu.com](ftp://http//www.ubuntu.com)
           => «[www.ubuntu.com»](www.ubuntu.com»)
Resolviendo http... 208.70.188.15
Conectando a http|208.70.188.15|:21... falló: No hay ruta hacia el host.


Probe con firefox, pero no ingresa a ninguna pagina, ni siquiera las https que en chrome si las abre.

---

### Post by papibe on 2013-01-24
Parece que tenemos algo.

ubuntu.com es 91.189.94.156 y no 208.70.188.15 (compáralo con los resultados de tu replay #4).

Me parece que tienes configurado un http proxy. Abre la aplicación 'Network Proxy' (o equivalente en español) y desabilita el proxy.

Otra manera de verlo es si en el terminal tienes definadas variables de proxy:
```
env | grep -i proxy
```
Saludos.

---

### Post by GrecoSCS on 2013-01-24
Hola, no se si lo hice bien, pero en Preferencia del proxy de la red me sale esto:

>> Configuracion del proxy
Habilitada Conexion directa a Internet

>>Anfitriones ignorados
localhost
127.0.0.0/8
*.local

Y lo de la terminal me salio esto:

alumno@Marioli:/usr/bin$ env | grep -i proxy
alumno@Marioli:/usr/bin$ 

No creo que sea solo un problema de navegadores, ya que JDownloader tampoco accede para iniciar las descargas.

---

### Post by guillermolisi on 2013-01-24
Estas pruebas las estas haciendo utilizando la conexion de red cableada o la inalambrica ?

Pregunto porque si es la inalambrica hay un problema: No tiene asignada una direccion IP.

---

### Post by GrecoSCS on 2013-01-25
Solo utilizo la red cableada ya que el proveedor de internet que tengo es speedy, modem zyxel p-600 series, si te sirve de algo esos datos.

De todas formas, aclaro que ya lo hable con los del servicio tecnico de Speedy y lo que es conexion esta todo ok, en windows 7 corre sin problemas y en ubuntu lo dico, no funciona en ningun navegador, salvo chrome y las https.

---

### Post by guillermolisi on 2013-01-25
Es una portatil o de escritorio ?
Si es una portatil, seria mucha molestia probar con otra conexion a Internet que no sea Speedy ?

Hay antecedentes no muy lejanos sobre problemas similares con conexiones como Speedy. Con otros sistemas operativos funcionaba todo bien pero los que usaban la conexion con Linux sufrian (sufrieron) varios meses, jDownloader incluido.

---

### Post by papibe on 2013-01-25
Tienes instalado algun anti virus (como Zone Alarm por ejemplo), o un firewall como ufw, o iptables?

Regards.

---

### Post by GrecoSCS on 2013-01-25
[COLOR="Green"]guillermolisi[/COLOR]
En una portatil, netbook para ser más exacto. Intentare probar con otro servicio de internet,por el momento lo unico que tengo disponible es la que tengo ahora.

Sobre los problemas con Speedy, no creo que sea la causa, ya que este problema empezo hace unos dias y antes de eso todo iba bien, normal, ningun problema de conexion.


[COLOR="Red"]papibe[/COLOR]
Antivirus hay uno pero no recuerdo el nombre del mismo, deja lo reviso y te doy el nombre exacto. Firewall no tiene, de ninguno que al menos reconozca.

---

### Post by guillermolisi on 2013-01-26
> **GrecoSCS said:**
> [COLOR="Green"]guillermolisi[/COLOR]
En una portatil, netbook para ser más exacto. Intentare probar con otro servicio de internet,por el momento lo unico que tengo disponible es la que tengo ahora.


Un bar con WiFi en zona de Telecom, Telecentro o Fibertel podria ser una alternativa a algo equivalente en casa de un amigo o pariente.

---

### Post by biale on 2013-01-27
El Zytel 600 podría estar filtrando cosas segun la direccion de ip. 

Para descartarlo una idea sería hacer coincidir a mano los parámetros que muestre un "ipconfig /all" de W7 hacia Linux. Sobre todo la dirección de ip, en forma exacta.

---

