---
title: "problema con rapidshare y megaupload"
date: 2009-05-24
forum: Software
---

### Post by infernus92 on 2009-05-24
bueno... la verdad no sabia si este post va aca... pero como no lo puedo patear, lo puse aca...
cuando intento bajar algo de megaupload o rapidshare o alguno similar, tengo el problema que (a veces) aunque no este descargando nada, me dice que desde mi IP ya se esta descargando algo y no me deja bajar...
no tengo internet a traves de router, tengo un modem 3G
la verdad ya se me acabaron las ideas asi que pido ayuda aca...
no se si hace falta que postee algo, por favor avisenme...

Saludos

---

### Post by z37a on 2009-05-24
Cual es tu ip publica y mascara de subred, puede ser que ya que empiezan a escasear las ip publicas los ISP te estén dando una ip privada nateada, son muy capaces esos tipos!!!

---

### Post by infernus92 on 2009-05-25
perdon por la ignorancia... no se como fijarme el IP publico ni la mascara de subred... pero la pagina de rapidshare me da este IP 200.49.201.26 pero no se cual sera...

---

### Post by z37a on 2009-05-25
> **infernus92 said:**
> perdon por la ignorancia... no se como fijarme el IP publico ni la mascara de subred... pero la pagina de rapidshare me da este IP 200.49.201.26 pero no se cual sera...


En donde estan las conexiones hace click derecho y pone "Informacion de la conexion", ahi te va a decir que direccion ip te esta dando el dispositivo 3G, posteala, si esta empiesa con 10 o 192 es privada y te estan nateando, o sea una ip publica se la dan a 255 usuarios(o mas).

PD: Creo que si empiesa con 172 tambien es privada, peor no recuerdo bien!!!!

---

### Post by Hei Ku on 2009-05-25
Sobre redes IP privadas, pueden ver aca: 
[http://en.wikipedia.org/wiki/Private_ip_address](http://en.wikipedia.org/wiki/Private_ip_address)

A mitad del texto pueden ver los rangos de IP que son privados por definicion.

---

### Post by z37a on 2009-05-26
> **Hei Ku said:**
> Sobre redes IP privadas, pueden ver aca: 
[http://en.wikipedia.org/wiki/Private_ip_address](http://en.wikipedia.org/wiki/Private_ip_address)

A mitad del texto pueden ver los rangos de IP que son privados por definicion.

Gracias pro el dato, yo la verdad muy definido no lo tenia, sabia que era la 10, la 172 y 192, pero no esactamente.

Entonces seria privada si tu ip comienza con 10, 172.16(al 172.31) o 192.168

---

### Post by guillermolisi on 2009-05-26
Si bien la publicidad de los servicios 3G dicen que es tarifa plana "sin limites", en la practica hay un momento que disminuyen el ancho de banda efectivo si te pasas de cierto limite de Mbytes descargados dentro del mes cubierto por el abono.
Esto no impide que te conectes, pero si resentira el rendimiento de servcios como los del asunto.

---

### Post by infernus92 on 2009-05-28
dice:

Dirección IP: 10.61.201.201
Dirección de difusión: 10.61.201.201
Máscara de subred: 255.255.255.255
Ruta predeterminada: 10.64.64.64

si las que empiezan con 10 son privadas, esta seria privada... no?

y eso de "sin límites" no le tengo ninguna confianza a movistar

Saludos

---

### Post by Hei Ku on 2009-05-28
Si, eso es una direccion privada.

---

### Post by pabloatilio on 2009-05-28
> **infernus92 said:**
> bueno... la verdad no sabia si este post va aca... pero como no lo puedo patear, lo puse aca...
cuando intento bajar algo de megaupload o rapidshare o alguno similar, tengo el problema que (a veces) aunque no este descargando nada, me dice que desde mi IP ya se esta descargando algo y no me deja bajar...
no tengo internet a traves de router, tengo un modem 3G
la verdad ya se me acabaron las ideas asi que pido ayuda aca...
no se si hace falta que postee algo, por favor avisenme...

Saludos

Probablemente te pasa porque estás saliendo a internet a través de algún equipo que concentra a varios usuarios y alguno de ellos también está descargando desde el mismo sitio. En mi caso, con adsl lo puedo solucionar reconectándome, dado que así por lo general obtengo otra dirección ip distinta. También sirve junto con lo anterior borrar las cookies. Desconozco como es en el caso de 3G.Quizás si se puede hacer la maniobra de reconectar funcione. Suerte. Saludos.

Pablo A

---

### Post by infernus92 on 2009-05-28
no se si tendra que ver... pero me parece que si.
cada vez que me conecto cambio manualmente los DNS del network manager porque el archivo que los tendria que contener se vacia cada vez que conecto
los DNS que uso son
primario: 194.179.1.100
secundario: 194.179.1.101

y siempre son los mismos. tendra algo que ver??

Saludos

---

### Post by Mauro22 on 2009-05-28
Los DNS sirven para resolver las direcciones. Nunca cambian (a menos por fuerzas mayores)

No deberia tener nada que ver con tu problema.

---

### Post by z37a on 2009-05-28
Consulta, te conectas mediante un modem 3G USB verdad? y esa IP que pusistes es una que te tiro en el moemento?

Siu la respuesta a ambas es Si, entonces te estan re ..., ejem estafando quise decir, los del proveedor de internet, por que te estan nateando con una ip privada, es como si en una cuadra pusieras un router hogareño y le vendieras a los vecinos una conexion a internet, que en realidad no es tan asi, pro que al no tener una ip publica, tu equipo no esta en internet si no en una LAN con internet!!!!(medio confuso el tema).

PD: Me entro una duda a mi nomas, netmask 32(255.255.255.255), alguno que entienda bien, pro que siempre me marean estos calculos, es posible? como sale al GW si solo existe una IP?

---

### Post by josecuervo86 on 2009-05-28
Che, entonces a mi tambien me estan robando? mi ip tambien comienza con 192.168...

---

### Post by z37a on 2009-05-29
> **josecuervo86 said:**
> Che, entonces a mi tambien me estan robando? mi ip tambien comienza con 192.168...

Si, a menos que tengas un router y no estes usando un modem USB 3G directo a la PC como mencione atras!!!!!

---

### Post by staar on 2009-05-29
> **josecuervo86 said:**
> Che, entonces a mi tambien me estan robando? mi ip tambien comienza con 192.168...

y que operadora tenés? a mi, con claro, me dan ip común...

saludos

---

### Post by josecuervo86 on 2009-05-29
Ah... entonces eso solo es valido para conexion 3G. Como veran no entiendo nada de redes :D

---

### Post by infernus92 on 2009-05-29
> **z37a said:**
> Consulta, te conectas mediante un modem 3G USB verdad? y esa IP que pusistes es una que te tiro en el moemento?

Siu la respuesta a ambas es Si, entonces te estan re ..., ejem estafando quise decir, los del proveedor de internet, por que te estan nateando con una ip privada, es como si en una cuadra pusieras un router hogareño y le vendieras a los vecinos una conexion a internet, que en realidad no es tan asi, pro que al no tener una ip publica, tu equipo no esta en internet si no en una LAN con internet!!!!(medio confuso el tema).

PD: Me entro una duda a mi nomas, netmask 32(255.255.255.255), alguno que entienda bien, pro que siempre me marean estos calculos, es posible? como sale al GW si solo existe una IP?


Las respuestas son si y si, y eso que decis explica perfectamente el problema (al menos a mi entender)
entonces... no puedo hacer nada??

Saludos

---

### Post by Hei Ku on 2009-05-29
La unica solucion que veo es que "rebotes" a traves de otra direccion antes de conectarte a rapidshare. Una alternativa para eso es usar Tor, aunque no es de buena persona usarlo para bajar archivos. La otra opcion es un server amigo que te permita hacer el ruteo.
Ninguna de las dos opciones son de lo mas simples. La otra es ir a insultarlos a los de Telefonica, o no usar rapidshare. :D

---

### Post by guisheca on 2009-05-29
No tengo internet por 3G ni tengo este problema ni nada por el estilo. Pero estuve siguiendo el hilo y la verdad me indigna como manosean al usuario a su antojo. No pueden ser tan delincuentes.

---

### Post by z37a on 2009-05-29
> **guisheca said:**
> No tengo internet por 3G ni tengo este problema ni nada por el estilo. Pero estuve siguiendo el hilo y la verdad me indigna como manosean al usuario a su antojo. No pueden ser tan delincuentes.

Perdon pro el off pero es un tema comun en mi laburo ahora!!!

Fijate como maltratan a los clientes que grupo clarin, en especifico datamrkets migro y esta migrando de prepo a todos sus clientes a fibertel, y los clientes corporativos de fibertel que tienen ips publicas estaticas, se las cambiaron por que si y no te reconocen tu vieja ip asi que tenes que cambiarla si o si!!! Y lo mejor de todo es que la alternativa a estas conexiones en el 90% de las veces son empresas tambien de clarin!!!!!
Me llego el dato de una empresa tambien que vende productos corporativos, se pone en un a cuadra yun router y te dan ips privadas!!!
Eso es basurear al cliente enserio.

Vuelvo a decirlo, perdon pro el offtopic!!!

Ahora con o del 3G todo depende de la empresa y tal vez el plan contratado, habria que ver que te ofrecen en su plan, peor la verdad que te limiten la bajada y ensima no te den ip publica es un insulto enserio.

---

### Post by edier88 on 2010-06-04
> **infernus92 said:**
> bueno... la verdad no sabia si este post va aca... pero como no lo puedo patear, lo puse aca...
cuando intento bajar algo de megaupload o rapidshare o alguno similar, tengo el problema que (a veces) aunque no este descargando nada, me dice que desde mi IP ya se esta descargando algo y no me deja bajar...
no tengo internet a traves de router, tengo un modem 3G
la verdad ya se me acabaron las ideas asi que pido ayuda aca...
no se si hace falta que postee algo, por favor avisenme...

Saludos


Pues, no sé cual puede ser tu problema pero intenta agregar DNS's a ver que pasa, sigue las instrucciones de esta pagina:


 [https://store.opendns.com/setup/operatingsystem/ubuntu](https://store.opendns.com/setup/operatingsystem/ubuntu)
 

Eso me resolvió un problema que tenía con que no abrían ni megaupload ni rapidshare, ahora ya abren :D  si aun así no has solucionado tu problema, lo que puedes hacer es burlar a rapidshare y megaupload bajandote el JDownloadre para Linux. Baja las cosas de ahí.

---

