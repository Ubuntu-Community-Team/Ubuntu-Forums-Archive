---
title: "Ayuda con VPN"
date: 2009-03-21
forum: Software
---

### Post by z37a on 2009-03-21
Acabo de configurar la VPN para entrar a mi laburo, solo tengo un problema, cuando me onecto via VPN la coneccion a internet sale a traves del gateway de mi trabajo, cosa que no quiero ya que esa salida esta filtrada y no tengo acceso a muchas paginas, alguna idea de que puede ser? ya probe de todo, ojo a traves del gestor de conecciones.

PD: Uso Jaunty en esta PC, antes con Hardy no tenia este problema y lo configure igual!

---

### Post by faktorqm on 2009-03-23
Con que te conectas a la VPN? yo me conecto con un cliente cisco y no tengo ese problema, salu2!

---

### Post by z37a on 2009-03-24
> **faktorqm said:**
> Con que te conectas a la VPN? yo me conecto con un cliente cisco y no tengo ese problema, salu2!

Me conecto a un router que hace uso del mismo protocolo que windows(un router vigor, una maquinita MIPS con un linux) y uso el gestor de conexiones de ubuntu(gnome) con el pptp

---

### Post by z37a on 2009-04-26
Gente perdón que reviva este post así de esta manera, peor no encuentro solución a esto, ahora estoy usando jaunty final, y les puedo decir que el protocolo que utilizo es el pptp que se conecta a un router con VPN(con un linux adentro, uno marca Vigor), ya busque en las configuraciones del pptp pero no encontré nada y me sigue routeando internet a través de la VPN y yo lo que busco es que utilice mi conexión normal si no me quedarían bloqueadas muchas paginas y utilizaría ancho de banda que no es mio al dope.

PD: Cual es el cliente de cisco que me comentastes faktorqm?

---

### Post by clasificado on 2009-04-26
Por acá uso KDE4 (kubuntu) para conectarme al pptp linksys de la oficina

El manager que uso es el KVpnc (que me adorna la conexión ppp a atravéz del pptp)

Dentro de "Preferencias/Configurar kvpnc", ahi en Perfil/Red/Rutas le cambié "Reemplazar la ruta predeterminada" por "mantener la ruta predeterminada"

En los papeles, eso evita el cambio del route, que sino igual se puede arreglar con el comando route en la consola, sin mucha historia (hasta lo podés transformar en un script)

No entendí cual es la herramienta que estas usando para administrar tu conexión pptp

fijate si algo de esto te sirve

clasificado

---

### Post by z37a on 2009-04-27
> **clasificado said:**
> Por acá uso KDE4 (kubuntu) para conectarme al pptp linksys de la oficina

El manager que uso es el KVpnc (que me adorna la conexión ppp a atravéz del pptp)

Dentro de "Preferencias/Configurar kvpnc", ahi en Perfil/Red/Rutas le cambié "Reemplazar la ruta predeterminada" por "mantener la ruta predeterminada"

En los papeles, eso evita el cambio del route, que sino igual se puede arreglar con el comando route en la consola, sin mucha historia (hasta lo podés transformar en un script)

No entendí cual es la herramienta que estas usando para administrar tu conexión pptp

fijate si algo de esto te sirve

clasificado

Yo uso el gestor de conecciones de gnome nomas, pero me parece que voy a instalar hoy a la tarde el que me decis de KDE a ver que onda!!!

---

### Post by guillermolisi on 2009-04-27
> **z37a said:**
> Yo uso el gestor de conecciones de gnome nomas, pero me parece que voy a instalar hoy a la tarde el que me decis de KDE a ver que onda!!!
Quise hacer funcionar una VPN con ese paquete, contra un server que corre OpenVPN en el laburo, y nunca logre que se conecte.
Como tengo otra maquina con KDE use el que mencionaron y salio con fritas (ambas con HH).

---

### Post by z37a on 2009-04-28
Probé el kvpnc, esta muy buena al parecer la aplicación, pero se me re cuelga cuando quiero desconectar!!!!(Igual creo que se cuelga por la placa de vídeo, el driver no es muy bueno, es una ATI).

---

### Post by clasificado on 2009-04-28
> **z37a said:**
> Probé el kvpnc, esta muy buena al parecer la aplicación, pero se me re cuelga cuando quiero desconectar!!!!(Igual creo que se cuelga por la placa de vídeo, el driver no es muy bueno, es una ATI).

A mi también :) Hay algo en jaunty que se rompió.

en principio, para desconectar la red, hago desde consola un **sudo ifconfig ppp0 down** (siendo ppp0 mi conexión vpn, podés fijarte con el ifconfig) y así la hago torta. 

y el programita que no se quiere cerrar, un **killall kvpnc**. Seguramente con alguna actualización vuelva a la normalidad

Joya que te haya funcionado, che

clasificado

---

### Post by z37a on 2009-04-28
> **clasificado said:**
> A mi también :) Hay algo en jaunty que se rompió.

en principio, para desconectar la red, hago desde consola un **sudo ifconfig ppp0 down** (siendo ppp0 mi conexión vpn, podés fijarte con el ifconfig) y así la hago torta. 

y el programita que no se quiere cerrar, un **killall kvpnc**. Seguramente con alguna actualización vuelva a la normalidad

Joya que te haya funcionado, che

clasificado

Es que no me funciono jjajajaja, solo dije que esta bueno por que trae mas opciones que el gestor de gnome nuevo!!!!

---

### Post by clasificado on 2009-04-28
¿y que error te tira? Usemos el mismo procedimiento que para el resto de los programas :P abrilo con la consola y fijate que te dice.

clasificado

---

### Post by z37a on 2009-04-28
> **clasificado said:**
> ¿y que error te tira? Usemos el mismo procedimiento que para el resto de los programas :P abrilo con la consola y fijate que te dice.

clasificado

Ningun error solo que me asigna una mascara de subred de 32 y no puedo entrar a ninguna ip de la red del laburo

---

### Post by clasificado on 2009-04-29
aaaahhh si, eso lo hace y sinceramente todavía no me puse a ver como arreglarlo desde el kvpnc

pasa que lo arreglo directamente haciendo el route con mascara 32 y a otra cosa

mas específicamente: sudo route add -net La.ip.que.quiero.acceder netmask 255.255.255.255 ppp0

por ejemplo, o sino la de mascara 0

clasificado

---

### Post by z37a on 2009-04-29
> **clasificado said:**
> aaaahhh si, eso lo hace y sinceramente todavía no me puse a ver como arreglarlo desde el kvpnc

pasa que lo arreglo directamente haciendo el route con mascara 32 y a otra cosa

mas específicamente: sudo route add -net La.ip.que.quiero.acceder netmask 255.255.255.255 ppp0

por ejemplo, o sino la de mascara 0

clasificado

Si no me parece que voy a pedir en el laburo que se reserve una ip privada asi configuro el ipv4 manualmente y no le meto gateway y ya fue. Lo mas raro es que en el 8.04 me andaba de lujo con el mismo paquete!!! en 8.10 no lo testie, pero me parece que cuando tenga algo de tiempo lo pruebo.

---

