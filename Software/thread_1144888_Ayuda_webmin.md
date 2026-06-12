---
title: "Ayuda webmin"
date: 2009-05-01
forum: Software
---

### Post by KaKuS on 2009-05-01
Gente, instale el webmin para administrar un seudo server con el que estoy practicando y aprendiendo pera después pasarlo a un servidor serio.

Una utilidad muy buena para controlar el servidor sin interfaz gráfica es el webmin, lo instale y lo configure (creo). Entrando al localhost funciona perfecto, pero cuando quiero entrar desde afuera (via internet) no puedo.

En la página oficial del webmin dice que hay que agregar una linea al iptables para permitir la entrada por el puerto 10000. La agregue a pesar de no tener activo el Firewall de Linux y sigo sin poder usar la interfaz web desde mi casa, por ejemplo.

Desde cualquier lado entro tranquilamente con SSH, FTP y hasta en el servidor de Trasmission (torrents) por lo que no creo que sea un problema de conexion sino que me falto habilitar algo por ahí.

Seguramente alguno ya paso por esto, se agradece cualquier ayuda.

---

### Post by juancarlospaco on 2009-05-01
Tenes que configurar tu Modem Router para que deje pasar el puerto 10.000,
no la PC, el aparatito, si no tenes idea llama a soporte del ISP y comentales, podes buscar info en internet tambien.

---

### Post by guillermolisi on 2009-05-01
> **KaKuS said:**
> Gente, instale el webmin para administrar un seudo server con el que estoy practicando y aprendiendo pera después pasarlo a un servidor serio.

Una utilidad muy buena para controlar el servidor sin interfaz gráfica es el webmin, lo instale y lo configure (creo). Entrando al localhost funciona perfecto, pero cuando quiero entrar desde afuera (via internet) no puedo.

En la página oficial del webmin dice que hay que agregar una linea al iptables para permitir la entrada por el puerto 10000. La agregue a pesar de no tener activo el Firewall de Linux y sigo sin poder usar la interfaz web desde mi casa, por ejemplo.

Desde cualquier lado entro tranquilamente con SSH, FTP y hasta en el servidor de Trasmission (torrents) por lo que no creo que sea un problema de conexion sino que me falto habilitar algo por ahí.

Seguramente alguno ya paso por esto, se agradece cualquier ayuda.
El firewall de Linux esta siempre activo con las reglas que vienen por defecto, salvo que se le haya modificado/agregado/quitado alguna, simplemente porque esta dentro del kernel.

Habiltaste el port 10000 UDP para entrar y para salir ? Porque puede ser que llegues a la maquina pero si no puede contestar (porque la vuelta no esta habilitada) del otro lado te va a parecer que no conecto.

Dale una revisada a la configuracion de Webmin en Webmin - Webmin Configuration - Port and Addresses y demas modulos que hablan de conectividad.

---

### Post by KaKuS on 2009-05-01
> **juancarlospaco said:**
> Tenes que configurar tu Modem Router para que deje pasar el puerto 10.000,
no la PC, el aparatito, si no tenes idea llama a soporte del ISP y comentales, podes buscar info en internet tambien.

Estoy conectado directamente en el Nod del ISP, y el "aparatito", el router que hace de gateway no tiene ninguna regla que bloquee, esta todo en ALLOW. Tengo todos los puertos liberados, además probé cambiando el 10000 por otros mas "conocidos" pero nada.

> **guillermolisi said:**
> El firewall de Linux esta siempre activo con las reglas que vienen por defecto, salvo que se le haya modificado/agregado/quitado alguna, simplemente porque esta dentro del kernel.

Habiltaste el port 10000 UDP para entrar y para salir ? Porque puede ser que llegues a la maquina pero si no puede contestar (porque la vuelta no esta habilitada) del otro lado te va a parecer que no conecto.

Dale una revisada a la configuracion de Webmin en Webmin - Webmin Configuration - Port and Addresses y demas modulos que hablan de conectividad.

Este es mi iptables -L, que le tengo que agregar?
Chain INPUT (policy ACCEPT)
```
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             "la ip de mi equipo" tcp dpt:webmin 

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

Chain webmin (0 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             "la ip de mi equipo" tcp spt:webmin dpt:webmin 
```

Gracias por contestar, sigo investigando :P

---

### Post by guillermolisi on 2009-05-01
> **KaKuS said:**
> Estoy conectado directamente en el Nod del ISP, y el "aparatito", el router que hace de gateway no tiene ninguna regla que bloquee, esta todo en ALLOW. Tengo todos los puertos liberados, además probé cambiando el 10000 por otros mas "conocidos" pero nada.



Este es mi iptables -L, que le tengo que agregar?
Chain INPUT (policy ACCEPT)
```
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             "la ip de mi equipo" tcp dpt:webmin 

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

Chain webmin (0 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             "la ip de mi equipo" tcp spt:webmin dpt:webmin 
```Gracias por contestar, sigo investigando :P
Mira, no soy un experto en primitivas de iptables (uso Firestarter porque me resulta mas amigable y comodo) pero hay tres cosas que me hacen ruido en la salida que acabas de enviar:

[LIST]
[*]Webmin, por lo que pude ver en mi configuracion, usa UDP, no TCP.
[*]Deberias habilitar ese port y protocolo en las cadenas de INPUT y OUTPUT y no en una cadena especifica que se llame Webmin (por favor, si alguien la tiene mas clara, que intervenga y opine sobre esto).
[*]No se si esa salida es la de la maquina remota o la de la maquina donde corre Wbmin.
[/LIST]
FIjate en la configuracion del Webmin al que queres entrar remotamente para ver si coincide en los parametros y formas con las que estas probando (inclusive si no esta deshabilitado para acceso remoto).

---

### Post by z37a on 2009-05-01
Che que webmin usan? el que uso yo usa pro defecto TCP, no UDP.

Ahora con lo del problema, si conectas un equipo a la misma lan que pasa? o es que tenes una IP publica directamente? Pro si las dudas proba de limpiar el iptables, solo para probar, usando el "iptables -F" asi tendrias todo abierto.

---

### Post by guillermolisi on 2009-05-01
> **z37a said:**
> Che que webmin usan? el que uso yo usa pro defecto TCP, no UDP.

Ahora con lo del problema, si conectas un equipo a la misma lan que pasa? o es que tenes una IP publica directamente? Pro si las dudas proba de limpiar el iptables, solo para probar, usando el "iptables -F" asi tendrias todo abierto.
Donde te fijaste para saber que el que tenes usa TCP ? En que parte de la configuracion de Webmin ?

Cuando mencione lo de UDP me fije en las reglas de iptables y en la seccion que adjunto como screenshot del Webmin que uso (1.470, ultima version al dia). Obviamente, via UDP escucha paquetes de broadcast.

Aclaro que no filtro IPs en el acceso al Webmin porque el server que lo tiene instalado esta detras de un gateway que tambien oficia de Firewall para la LAN.

---

### Post by guillermolisi on 2009-05-01
Acabo de hacer una prueba entre el server y una PC en la LAN de mi casa para ver si lograba informacion sobre la conexion remota a un servidor Webmin.

Ambos equipos estan en una LAN de total confianza, como mencione antes, ya que el gateway posee dos placas de red, una privada y una publica. Con esto saco de juego cualquier tema de firewalling.

Desde la PC tire un "nmap" hacia el server y, entre todo lo que mostro, aparecio esto en el port que usa Webmin para aceptar conexiones:```
10000/tcp open  snet-sensor-mgmt
```Asi que queda confirmado el tema de que usa TCP (ademas de UDP si se lo habilita para broadcasting)

---

### Post by z37a on 2009-05-01
> **guillermolisi said:**
> Donde te fijaste para saber que el que tenes usa TCP ? En que parte de la configuracion de Webmin ?

Cuando mencione lo de UDP me fije en las reglas de iptables y en la seccion que adjunto como screenshot del Webmin que uso (1.470, ultima version al dia). Obviamente, via UDP escucha paquetes de broadcast.

Aclaro que no filtro IPs en el acceso al Webmin porque el server que lo tiene instalado esta detras de un gateway que tambien oficia de Firewall para la LAN.

Lo que hize fue redirigir el TCP 10000 en mi router a la ip privada de mi server con webmin, si fuera udp no podria ingresar via wan, pero me anda de 10!

Igualmente si podes tira un nmap a tu servidor para ver que puertos tenes abiertos

---

### Post by KaKuS on 2009-05-03
Esta es mi iptables ahora:

```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

```

Tire el nmap, y encontré esta línea 
```

10000/tcp open     snet-sensor-mgmt
```

Desde el server entro bien, pero desde afuera el navegador me dice
```

Falla de conexión

Firefox no puede establecer una conexión con el servidor en "la ip de mi server":10000.        

Aunque el sitio parece válido, el navegador no puede conectarse.

    * ¿Puede ser que el sitio no esté disponible temporariamente? Intente nuevamente después.
    * ¿No puede navegar otros sitios?  Verifique la conexión a la red de su computadora.
    * ¿Su computadora o red están protegidas por un firewall o proxy? Una configuración incorrecta puede interferir con la navegación.
```


Sigo probando, eventualmente lo vamos a sacar :P

---

### Post by z37a on 2009-05-03
> **KaKuS said:**
> Esta es mi iptables ahora:

```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

```

Tire el nmap, y encontré esta línea 
```

10000/tcp open     snet-sensor-mgmt
```

Desde el server entro bien, pero desde afuera el navegador me dice
```

Falla de conexión

Firefox no puede establecer una conexión con el servidor en "la ip de mi server":10000.        

Aunque el sitio parece válido, el navegador no puede conectarse.

    * ¿Puede ser que el sitio no esté disponible temporariamente? Intente nuevamente después.
    * ¿No puede navegar otros sitios?  Verifique la conexión a la red de su computadora.
    * ¿Su computadora o red están protegidas por un firewall o proxy? Una configuración incorrecta puede interferir con la navegación.
```


Sigo probando, eventualmente lo vamos a sacar :P

No tenes ningun proxy en la red, verdad????

---

### Post by KaKuS on 2009-05-05
> **z37a said:**
> No tenes ningun proxy en la red, verdad????

Del lado server no, del lado cliente probé desde varios equipos, con y sin proxy.


Por ahora sigo igual, lo raro es que probé instalando un webmin en un cliente y si le agrego el servidor a mano, lo agrega pero al querer accederlo se cuelga.

Hoy si puedo pruebo conectandole otro acceso, que tiene otra salida, otra puerta de enlace, otro nodo. A ver si me están limitando algo por ahí.

---

