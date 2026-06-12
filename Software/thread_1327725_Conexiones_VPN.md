---
title: "Conexiones VPN"
date: 2009-11-15
forum: Software
---

### Post by Mole_Cba on 2009-11-15
Hola Estimada comunidad, soy un usuario novato de Ubuntu, he instalado la version 9.10.. y quiero configurar una conexion VPN, buscando algo de info en la red vi que necesitaba instalar el protocolo pptp...lo hice y me permite añadir una conexión nueva, seteo los datos de la conexión, pero cuando le doy a conectar me dice que la conexion fallo... si alguien tiene algunos tips para lograr solucionar esto.. se los agradecería....  o si saben de alguna documentación para ponerme más al tanto de este S.O.  Porque quiero migrar completamente a Linux....

---

### Post by josecuervo86 on 2009-11-15
Hola, yo te recomendaría que utilizaras pppoeconf. Este con solo poner tu nombre de usuario y contraseña que te da tu ISP te configura la conexión automáticamente. En unaterminal (**Aplicaciones** > **Accesorios** > **Terminal**) escribí lo siguiente:

```
sudo pppoeconf
```

pone tu contraseña y dale [Enter]. Luego te va a aparecer una ventana que lo que hace es buscar las conecciones y configurarlas.

Saludos!

---

### Post by Mole_Cba on 2009-11-17
Hola JoseCuervo... antes que nada.. gracias por contestar... te comento que aún no probe lo que me has dicho.. pero lo que yo necesito es poder configurar una Red Privada Virtual.. o VPN... por lo que he estado leyendo lo de pppoeconf es para setear la configuración de conexión a mi ISP, yo ya cuento con internet en Linux... no se si soy lo suficientemente claro con mi problema.....

---

### Post by oktubrer on 2009-11-17
Si sos claro.  Hay varios clientes que te pueden servir, dependiendo de las características del concentrador VPN al que te quieras conectar.  Si es cisco, instalando el paquete vpnc te debería habilitar la opción para crear una conexión vpn desde el network-manager en la barra de tareas.  No te puedo guiar mucho porque uso KDE.
Yo traté varias veces de establecer una vpn con mi trabajo pero en mi caso particular necesito que soporte IPSEC sobre TCP, y el vpnc no lo soporta todavía según leí por ahí.  Es lo único que no me permite migrar 100%.

---

### Post by guillermolisi on 2009-11-17
[OpenVPN]("http://openvpn.net/index.php/open-source.html") me parece una buena alternativa para armar VPNs.

Sobre IPSEC (extractado del site de OpenVPN)
> The IPSec protocol is designed to be implemented as a modification to the IP stack in kernel space, and therefore **each operating system requires its own independent implementation of IPSec**.

---

### Post by Mole_Cba on 2009-11-17
muchachos.. muchas gracias por la ayuda... esto es lo que tengo instalado referido a VPN:

[LIST]
[*]openvpn 2.1rc19-1ubuntu2
[*]openvpn-blacklist 0.4
[*]network-manager-openvpn
[*]vpnc 0.5.3-1
[*]network-manager-vpnc
[/LIST]
en el Network Manager puedo agregar una conexion, pero cuando le doy a conectar sale el siguiente error : "Falló la conexión VPN <<null>>  porque el servicio vpn falló al iniciarse" 
 ](*,)

---

### Post by Mole_Cba on 2009-11-19
Hola amigos de la comunidad, les comento que por fin logre conectarme por vpn,  ya cansado de probar, elimine todo lo que tenia que ver con las conexiones vpn y empece de 0. asi que ejecuté esto

```
sudo apt-get install pptpd network-manager-pptp
sudo apt-get install pptpd-linux
```


Luego configure mi conexion VPN, en la cual me parece ademas que anteriormente no le habia habilitado el cifrado punto a punto, y deshabilitado el protocolo EAP, y ademas habilitar el envio de ECO.

Luego 
```
sudo NetworkManager restart 
```

y Listo...logré conectarme... ahora tengo otro problemita, que es el de poder utilizar mi conexion de internet local, no la del equipo remoto..... pero vamos paso a paso... jejeje...  Gracias a Todos..... porque todo lo que hice, fue gracias a uds y a sus aportes en otros post...   :p

---

### Post by guillermolisi on 2009-11-19
Excelente !

Podrias indicar en que threads/posts te basaste ?

Luego, el tema de acceso a Internet localmente ponelo en un thread nuevo en la seccion Software, por favor.

Si la cuestion de este hilo esta solucionada, para lo cual podes tomarte tu tiempo para verificar que efectivamente asi es, por favor marcalo como SOLVED.

---

### Post by Mole_Cba on 2009-11-25
Hola Guillermo, me base en este [post]("http://ubuntuforums.org/showthread.php?t=700285"), y en otra info conseguida por la red que en estos momentos no encuentro, pero en la otra lo que decía es la configuración de la conexión en si :

      *En Avanzado:*

[LIST]
[*] Deshabilitar EAP
[*]**Seguridad y compresión: ***Usar cifrado punto a punto (MPPE)*
[*]*Deshabilitar cifrado de estado completo*
[*]*y tildar todas las demás opciones*
[/LIST]

***A tener en cuenta:***
   Actualmente si me conecto, utiliza la conexión de mi servidor remoto no la local, si entro en Ajustes de IPv4 y voy a Rutas:
   Seleccionando usar esta conexión solo para recursos en su red, se conecta al servidor, pero no me levanta el Escritorio Remoto en el servidor, y si tengo conexión local... aunque eso, después lo seguiré investigando.-

---

### Post by Gondog on 2009-11-27
Hola Gente, soy novato en esto de ubuntu, lo instale y me gusto lo que vi hasta ahora. Voy al grano, siguiendo con el tema, pude conectarme desde el ubuntu 9.10 a un windows server 2003, incluso puedo abrir el escritorio remoto, hasta aca todo joya, mi problema es que cada vez que me conecto a la VPN no me deja  navegar por internet. Alguna sugerencia para resolver esto? Desde ya muchas gracias.

---

### Post by opensas on 2009-12-03
Gondog, me podrías pasar la configuración exacta que usaste para conectarte a una vpn de windows?

'chas gracias, por ahora me está saliendo un mensaje

La conexión "xxx" ha fallado porque porque el servicio vpn ha fallado al iniciarse

alguien me puede ayudar a recolver esto?

muchas gracias....

---

### Post by quantico on 2009-12-08
en cuanto al problema de no lograr navegar, a mi se me ocurre que estableciéndole un proxy a tu browser podría resultar, pero a mi en definitiva ya probé con lo que han comentado en este foro hasta el momento y me sigue dando el mismo erro de fallo el servicio vpn al iniciarse, asi que no puedo establecer ni siquiera la conexión, ¿quien me puede dar una manita con esto?

---

