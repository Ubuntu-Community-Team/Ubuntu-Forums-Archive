---
title: "[SOLVED] Sobre Redes en general"
date: 2008-12-09
forum: Software
---

### Post by andy_91 on 2008-12-09
hola, tengo una consulta sobre redes.

resulta que en el edificio donde vivo quieren hacer una red para compartir la conexión a Speedy:

Duda a: si la velocidad es 1 mb por Ej, todas las maquinas tienen 1mb compartido o 500kb por decir un numero cada maquina, ¿la velocidad aumenta si el resto no esta usando su maquina?

Duda B: esto no es mucha duda, pero hardy  ¿trae todos lo paquetes para hacer red con WinDos?

Duda c: ¿que sistema de conexión es mas conveniente para mi que uso ubuntu wi-fi,  eth u otro ?

cualquier otra cosa que quieran agregar sera bienvenida, por que no se nada de redes

a los dto que se van a unir son entre 3 y 5 Apx y creo que c/u tiene un solo ordenador

---

### Post by c4d0rn4 on 2008-12-09
> **andy_91 said:**
> hola, tengo una consulta sobre redes.

resulta que en el edificio donde vivo quieren hacer una red para compartir la conexión a Speedy:

Duda a: si la velocidad es 1 mb por Ej, todas las maquinas tienen 1mb compartido o 500kb por decir un numero cada maquina, ¿la velocidad aumenta si el resto no esta usando su maquina?

Duda B: esto no es mucha duda, pero hardy  ¿trae todos lo paquetes para hacer red con WinDos?

Duda c: ¿que sistema de conexión es mas conveniente para mi que uso ubuntu wi-fi,  eth u otro ?

cualquier otra cosa que quieran agregar sera bienvenida, por que no se nada de redes

a los dto que se van a unir son entre 3 y 5 Apx y creo que c/u tiene un solo ordenador
un mega 3 a 5 apartamentos... no alcanza.

La red lo más cómodo-barato sería wi-fi; pero dudo que se pueda por tema de la distancia-infrastructura. No se cual es el alcance de una red ad-hoc wi-fi, pero tal vez, puede ser una solución. 

El tema del cableado y que poner: Bueno, si mal no entiendo quieres poner una segunda placa de red, que se conecte a switch?

Desde allí podes compartir la conexión eth0 con eth1 (la segunda placa de red); el tema de las limitaciones desconozco como se hará, pero seguro se puede. Y el tema de como distribuir las conexiones supongo que te refieres QoS?

fuera cual fuera el caso, te diría que miraras que programas traen las distribuciones de linux dedicadas a router. Te dejo un link

[http://en.wikipedia.org/wiki/List_of_Linux_router_or_firewall_distributions](http://en.wikipedia.org/wiki/List_of_Linux_router_or_firewall_distributions)

mirando esta me resulto interesante ajaj xD
[http://en.wikipedia.org/wiki/Floppyfw](http://en.wikipedia.org/wiki/Floppyfw)
no necesitas disco rigido; cualquier sobra de pc te sirve para armarla.

---

### Post by DrKenobi on 2008-12-09
Vas a compartir el ancho de banda, y si todos se ponen a usarla a pleno (todos bajando peliculas y subiendo mucho a algun lugar), se te va a hacer lenta la coneccion. Con el router vos poder administrar muchas cosas, fijate si hay alguno que te distribuya el ancho de banda (debe existir).

Wi-fi es lejos lo mas comodo, pero no tiene gran alcanze (por lo menos los routers normales, de 300 pesos. Hay otros mucho mas caros que tienen mejor alcanza, pero son caros). Si armas una red con cables es lo mismo, solo que tenes que comprar los metros de cables y cablear.

Si el router esta en una habitacion, a la de al lado la señal llega bien, pero a la siguiente le va a costar llegar. Vas a tener buena coneccion si el router esta en una habitacion, y vos estas en la misma pero en el piso de arriba o abajo.

Despues, no importa que sistema operativo estes usando. Porque si usas un router "alambrico" o "inalambrico" (wi-fi) te va a andar. Yo en mi casa tengo 4 PC: 1 linux, 1 windows y 2 mac. Comparto la coneccion a internet, la impresora y tamien archivos.

Por ultimo, fijate de tener cuidado para que nadie se te pueda meter en tu PC, porque estas compartiendo una red.

Suerte!

---

### Post by andy_91 on 2008-12-09
mhh es difisil sobretodo por que la maquina principal no va ser la mia, lo que entendi es que la coneccion va a ser muy mala, pero ¿que velocidad recomiendan?

yo no voy a hacer la coneccion ami me toca nomas enchufar el cable, lo que se va a hacer es contratar un servicio nuevo y dar de baja el actual.

como que nadie se pueda meter :S eso no me gusta, igual creo que el que mas sabe del edificio soy yo y mucho tampoco se del tema asi que por ese lado creo que esta bien :confused:

---

### Post by vk-cdg on 2008-12-10
Yo en tu lugar, lo primero que me preguntaría es cuantos usuarios van a ser?

Mas de 3 o a lo sumo 5... gracias, paso! Son muchas manos, muchas mulas y muchos torrents como para que ande decente y puedas ver cualquier web.

El otro tema es cuantos pisos tiene tu edificio. Si tiene mas de 3 pisos, me tiraría por una instalación cableada, wifi ya no sería una solución aceptable. Tené en cuenta que habría que conprar cierto equipamiento, un router o un switch mas los metros de cable.

Finalmente tenés el tema de la administración, que es otra historia. Tienen que confiar en manos de quien la dejan y cada uno individualmente tomar los recaudos de seguridad respecto de los accesos a su equipo.

Ahhh, me olvidaba de un tema mas, a Speedy lo van a notificar de esta instalación? porque si no es así, cada vez que haya un problema y tengan que llamar al service van a tener que hacer desaparece todo eso.

---

### Post by vk-cdg on 2008-12-10
> **andy_91 said:**
> ... igual creo que el que mas sabe del edificio soy yo y mucho tampoco se del tema asi que por ese lado creo que esta bien :confused:

Tenés que tener en cuenta que además de los problemas que puedan tener con el servicio (que requieran visita de un técnico) puede haber problemas con la red de ustedes, y eso no te lo va a solucionar alguien de speedy, sino que tendría que ser alguien que conozca la instalación.


Sin ánimos de desmoralizar, yo no me metería. Una cosa es compartir una acceso wifi con mi vecino y que me tire unos pesos y otra cosa es armar algo como lo que me imagino que quieren armar.

---

### Post by c4d0rn4 on 2008-12-10
> **andy_91 said:**
> mhh es difisil sobretodo por que la maquina principal no va ser la mia, lo que entendi es que la coneccion va a ser muy mala, pero ¿que velocidad recomiendan?

yo no voy a hacer la coneccion ami me toca nomas enchufar el cable, lo que se va a hacer es contratar un servicio nuevo y dar de baja el actual.

como que nadie se pueda meter :S eso no me gusta, igual creo que el que mas sabe del edificio soy yo y mucho tampoco se del tema asi que por ese lado creo que esta bien :confused:

mmm... me parece que lo que te vas a ahorrar en pesos, te lo vas a gastar tres o más veces en dolores de cabeza.

La verdad que de una conexión de un mega a 3 o 5 no hay tanta diferencia de dinero. Si hay disponiblidad de esos anchos de banda para 5 personas 3 megas está bien (si solo si se limita el up y el down)


...................

[QUOTE=vk-cdg]y eso no te lo va a solucionar alguien de speedy[/QUOTE]Alguna vez solucionaron algo? :lolflag:
Para llamar a speedy y pedir una queja lo unico que hay que hacer es llamar y
dejar tacitamente explicito que usas windows xp :rolleyes:
y cuando te piden ipconfig, decir la ip publica si importar tu ip de red.
En los tracert no contar el primer salto que es al router,
y listo el pollo ajaja xD

---

### Post by andy_91 on 2008-12-10
bueno el tecnico lo pone la persona de la idea (la que va a tener el ordenador principal)

el edificio tiene 3 pisos mas la planta baja.

a mi speedy con Linux nunca me soluciona nada

pero les voy a latear esto a ver que dicen

---

### Post by DrKenobi on 2008-12-10
> **vk-cdg said:**
> Finalmente tenés el tema de la administración, que es otra historia. Tienen que confiar en manos de quien la dejan y cada uno individualmente tomar los recaudos de seguridad respecto de los accesos a su equipo.

Ahhh, me olvidaba de un tema mas, a Speedy lo van a notificar de esta instalación? porque si no es así, cada vez que haya un problema y tengan que llamar al service van a tener que hacer desaparece todo eso.

El router tiene una clave, y cualquiera desde un navegador (firefox) en cualquier PC puede entrar a modificar el seteo del mismo. No entiendo lo de la maquina principal, creo que no hay cosas asi. Para mi es "Internet llega al router, este la distribuye y listo".

Seguramente lo que haces es "ilegal", no aceptado por speede, pero si algun dia algun tecnico lo ve, no te va a decir naaada. A mi me pasa con Fibertel. Al principio escondia todo. Desp un dia mi vieja llamo, no escondio nada y desde ese dia no escondo nada porque no te dicen nada.

Andy: lo que quieren hacer ustedes se puede, pero es medio rebuscado.... Compartir internet entre todo el edificio es raro, si fuesen 2  o 3 nomas seria mas facil

Ah otra cosa, los routers de precios normales (entiendase los que compramos nosotros) se cuelan seguido, asi que el que tiene el router va a tener que resetearlo cada vez que se cuelge. (si el del router se fue de vacaciones, a esperar a que vuelva pa resetearlo jaja). Entonces deberia estar en un lugar comun, a la vista.....bue no se

Suerte

---

### Post by tomasp on 2008-12-10
Pueden probar un Linksys WRT54GL flasheado con dd-wrt (un firmware alternativo), este te permite incluso poner un par de estos linksys separados un par de deptos y que entre los dos te amplifiquen el rango de la señal

---

### Post by c4d0rn4 on 2008-12-10
En realidad creo que si pone las placas wi-fi en modo ad-hoc la más alejada haria "sapito" por las pc hasta llegar a la principal. Incluso así podría obiar el router wifi. Se compran en una tienda varias placas pcmcia buenas y a otra cosa. Obvio, eso requiere  que las pc estén conectadas y prendidas.

No se si es así, es lo que tengo entendido.

@DrKenobi
En cuanto a los routers... la verdad he escuchado cosas así, pero los que he probado (encore y dlink la linea más barata) se la aguantan lo más que bien y no hablo de compartir internet sino uso de la intranet (lan) a todo dar. 5 personas no son tanto y si es solo para compartir internet menos aún.

A mi lo unico que me da un poquitito de problema es el modem que con los calores se le salta la termica y se tilda  ajaja xD

_____

Que raro que no haya nadie por acá que haga routers con distros de linux =S

---

### Post by z37a on 2008-12-10
> **andy_91 said:**
> Duda a: si la velocidad es 1 mb por Ej, todas las maquinas tienen 1mb compartido o 500kb por decir un numero cada maquina, ¿la velocidad aumenta si el resto no esta usando su maquina?

Siempre uso un ejemplo que me enteinden todos de 10 para responder a esta pregunta(que la preguntan muchisimos)


Imaginate una manguera donde pasa agua a una precion nomral. Si la pinchas en el medio para sacar agua al final del recorrido llega menos, y a medida que vas pinchando mas partes para sacar en otros lados cada vez va a salir menos en todos lados. Asi pasa con internet. Ahora con lo de si 1MB alcanza, bueno depende de que uso se le de, si solo van a chatear y navegar por web te va a alcanzar para 10 o mas puestos!!!! Ahora si empiesan a bajar cosas o usar ftp, rapidshare etc... 1MB te va a alcanzar para 4 o 5, y si usan p2P(amule, torrents, etc...) 1MB no te alcanza ni para 1 solo puesto!!!!!

---

### Post by andy_91 on 2008-12-11
ok creo que ya entendi que es mala idea, solo me lo sugirieron y la verdad no sabia como era

por lo que me dijeron es legal pero nose sera cuestion de ver  

gracias por todo

---

