---
title: "limitar ancho de banda de un usuario"
date: 2010-03-22
forum: Software
---

### Post by mama21mama on 2010-03-22
Hola,

les comento tengo en mi pc 3 usuarios en mi karmic, hasta ahí todo bien.
El problema es el hijo de mi novia que usa amule, tucan, peliculas on line que se las olvida y me deja el navegador activado con la peli.

por ejemplo la sulucion que encontré fue, para con el amule.
> 
sudo chattr +i /home/rebeldeway/.aMule/amule.conf
antes claro que le deje de bajada 20kib y 5 de subida

pero el tipo aludió esa que encontré yo y la sube en preferencias :mad:

podre usar Wondershaper o iptables para hacer que "rebeldeway" no pase de 20kib de bajada en mi ancho de banda y 5 de subida?

La idea es iniciar mi usuario y poder navegar, mirar mail, etc. Pero "rebeldeway" limitarle el consumo de internet.


PD: Un pc, 3 usuarios.

---

### Post by juancarlospaco on 2010-03-22
Si, tambien ponerle como de solo lectura ese archivo y no va a poder editarlo.

Tambien fijate **python-pydirector**
:)

---

### Post by sebastianabate on 2010-03-22
En casos como los tuyos es muy complicado limitar el ancho de banda a un usuario, ya que tenés una sola PC, y la única forma de diferenciar el tráfico es por usuario (limitar por puertos no tiene sentido porque la mayoría de los programas permiten cambiar el puerto usado o usan un puerto común como el 80, y limitar los permisos de escritura sobre los archivos de configuración es una pesadilla por la cantidad de programas que existen para hacer lo mismo, y la facilidad que hay para hacerlos correr)

Para limitar ancho de banda por usuario con una sola PC lo único que conozco es bloquear toda la salida con iptables e instalar squid en modo transparente autenticando usuarios y usando pools (pero no te imaginas lo complicado que es y los contratiempos que trae)

En casos como el tuyo lo ideal es usar la ingeniería social, entablando un diálogo constructivo y clarificador, del tipo:

ENTENDELO BIEN DE UNA VEZ POR TODAS , SI SEGUÍS USANDO TODO EL ANCHO DE BANDA TE MATOOOOOOOO... (los procesos)

y para cumplir con la consigna planteada podés usar el comando nethogs

sudo apt-get install nethogs
sudo nethogs

que te va a mostrar un listado de procesos con el uso en tiempo real del ancho de banda que hace cada uno (tanto de subida como de bajada). Cuando tenés idetificados los PIDs de cada uno de los procesos, no te queda más que hacer un

kill -9 NRO_DE_PID

y hacés un kill -9 porque en la charla anterior también aclaraste que

Y ADEMÁS DE MATARTE (los procesos), LO VOY A HACER DE LA PEOR MANERA, ABRUPTAMENTE Y SIN AVISAR, COMO PARA QUE NO HAYA POSIBILIDADES DE RECUPERACIÓN... ENTENDISTE????!!!!!!

y así lográs, por medio de la ingeniería y la psicología juntas, el objetivo que buscabas.

---

### Post by mama21mama on 2010-03-22
> ENTENDELO BIEN DE UNA VEZ POR TODAS , SI SEGUÍS USANDO TODO EL ANCHO DE BANDA TE MATOOOOOOOO... (los procesos)
 

lol

si es algo de iptables pero no allo respuestas en google por eso acudí al foro :(

---

### Post by sebastianabate on 2010-03-22
Con iptables podés controlar al ancho de banda por usuario, pero solo de subida, no de bajada (esto es porque cuando los paquetes llegan no contienen información de usuario de destino, solo de protocolo y puerto; pero cuando salen se los puede marcar previamente con el modificador "-m owner")

Por eso te decía lo de usar squid, porque lo podés configurar para que pida autenticación antes de hacer cualquier conexión, y a apartir de eso ya podés controlar todo (saliente y entrante) con delay pools.

Acá tenés algo con qué empezar (en inglés)

[http://tldp.org/HOWTO/Bandwidth-Limiting-HOWTO/install.html](http://tldp.org/HOWTO/Bandwidth-Limiting-HOWTO/install.html)
[http://wiki.squid-cache.org/Features/Authentication?action=show&redirect=SquidFaq%2FProxyAuthentication#How_do_I_use_authentication_in_access_controls.3F]("http://wiki.squid-cache.org/Features/Authentication?action=show&redirect=SquidFaq%2FProxyAuthentication#How_do_I_use_authentication_in_access_controls.3F")

---

### Post by mama21mama on 2010-07-23
Bueno, gracias por la data.
Comenzare a ver un poco.


Saludos

---

