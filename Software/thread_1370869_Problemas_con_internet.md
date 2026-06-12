---
title: "Problemas con internet"
date: 2010-01-02
forum: Software
---

### Post by nyko513 on 2010-01-02
Tengo problemas con internet. es medio complicado de explicar, dado que el problema en si ya es muy extraño. La conexión se cuelga, o sea internet me funciona lo mas bien. pero de un momento a otro.. internet se queda cargando.. y no responde. y por ahi arranca de golpe y sigue andando lo mas bien (tarda unos 10 segunos o un poco mas) ... esto me lo hace a cada rato. 

aca dejo una pantalla con ping a [www.google.com](www.google.com) 


[URL="http://www.subirimagenes.com/privadas-pantallazo-804617.html"][IMG]http://s2.subirimagenes.com/privadas/previo/thump_804617pantallazo.png[/IMG]
[/URL]

si observan con detalle.. abajo a la derecha se ve el monitor de la red (color amarillo, debajo del mouse) ahi se puede ver que el ping se colgo, o sea q no me tira error. sino que simplemente se cuelga.

Por otra parte, tengo Speedy con un modem Huawei (routeado, funcionando siempre bien.. sin problemas) y un router Encore para repartirlo a 2 pc. Una por wifi y otra por LAN.

la wifi usa windows y anda lo mas bien. la otra usa ubuntu 9.10 y es la que me pasa esto. tengo windows instalado tambien y me funciona bien (la red! porque windows me anda muy mal! ) 

probe poniendo la maquina que usa ubuntu por wifi y sucede lo mismo.


Se les ocurre que puede ser ? .. es muy molestoo .. no quiero usar windows

---

### Post by z37a on 2010-01-02
> **nyko513 said:**
> 
Por otra parte, tengo Speedy con un modem Huawei (routeado, funcionando siempre bien.. sin problemas) y un router Encore para repartirlo a 2 pc. Una por wifi y otra por LAN.


Si no te entendí mal ahí tenes un error. El modem deberia estar en modo bridge, no en modo router, y luego el router debería tener configurado en su WAN(o acceso a internet) la cuenta "pppoe", de lo contrario tendrias una ip privada dentro de otra y a la hora de redirigir algun puerto se genera un lindo problema!!!!!

Ahora lo que me llama la atención es que la misma pc bajo la misma red en windows te funcione y con ubuntu no, siempre me paso lo contrario, algún virus en windows estaba usando la PC como zombie enviando mails y abriendo conexiones a lo loco, y como si fuese poco con los módems que da telefonica y telecom se cuelgan enseguida.

---

### Post by nyko513 on 2010-01-02
> **z37a said:**
> Si no te entendí mal ahí tenes un error. El modem deberia estar en modo bridge, no en modo router, y luego el router debería tener configurado en su WAN(o acceso a internet) la cuenta "pppoe", de lo contrario tendrias una ip privada dentro de otra y a la hora de redirigir algun puerto se genera un lindo problema!!!!!

Ahora lo que me llama la atención es que la misma pc bajo la misma red en windows te funcione y con ubuntu no, siempre me paso lo contrario, algún virus en windows estaba usando la PC como zombie enviando mails y abriendo conexiones a lo loco, y como si fuese poco con los módems que da telefonica y telecom se cuelgan enseguida.


lo que hice es poner el modem para que se conecte solo y poner el router wifi en modo bridge para que lo comparta. Me estaba funcionando bien. hasta que empece a usar ubuntu. 

lo hice asi porque antes habia una sola pc y de esta forma la pc ni bien la prendia tenia internet. no tenia que conectarla. despues agregue el router wifi y teoricamente si lo pongo en modo brige deberia repartir internet o no?

---

### Post by z37a on 2010-01-02
> **nyko513 said:**
> lo que hice es poner el modem para que se conecte solo y poner el router wifi en modo bridge para que lo comparta. Me estaba funcionando bien. hasta que empece a usar ubuntu. 

lo hice asi porque antes habia una sola pc y de esta forma la pc ni bien la prendia tenia internet. no tenia que conectarla. despues agregue el router wifi y teoricamente si lo pongo en modo brige deberia repartir internet o no?

Sigo sin entender bien que fue lo que hicistes, pero te comento un poco mas que deberias tener armado:

- El módem debería estar configurado como viene de fabrica por telefonica/telecom.
- El modem deberia estar conectado a la boca de internet/wan del router.
- El router deberia tener configurado como conexion a internet PPPoE.
- Todas las pcs deberian estar conectadas al router(en forma inalambrica o no).

Esa seria para mi la configuración que mejor funciona. Ahora no entendí bien como es que la hicistes, pero igualmente esto va mas allá del problema, tal vez ayude a solucionarlo, peor no creo que venga por acá.

---

### Post by nyko513 on 2010-01-02
El tema es que para conectarme uso usuario y contraseña.. con PPPoE puedo configurar Speedy sin problemas !?

---

### Post by z37a on 2010-01-03
> **nyko513 said:**
> El tema es que para conectarme uso usuario y contraseña.. con PPPoE puedo configurar Speedy sin problemas !?

Esactamente, es pra eso, ccreo que el significado de PPPoE es "Point to Point Protocol over Ethernet" que es lo mismo que esta haciendo tu modem a como lo tenes configurado hoy en dia. Igualmente al poner PPPoE en tu router te aparecera unos cuadros pidiendo usuario y contraseña.

---

### Post by nyko513 on 2010-01-06
Ya lo solucione.. puse q marque el router Encore (o sea lo puse en modo Pppoe) y quedo bien.. y deje el modem de Speedy tal cual me lo dio la empresa. un consejo. no reseteen nunca el modem de Speedy (por lo menos mi caso, un Huawei MT880). porque si haces un reset no funca mas. ! me paso a mi. y tube que esperar a que me trajeran otro

---

### Post by z37a on 2010-01-07
> **nyko513 said:**
> Ya lo solucione.. puse q marque el router Encore (o sea lo puse en modo Pppoe) y quedo bien.. y deje el modem de Speedy tal cual me lo dio la empresa. un consejo. no reseteen nunca el modem de Speedy (por lo menos mi caso, un Huawei MT880). porque si haces un reset no funca mas. ! me paso a mi. y tube que esperar a que me trajeran otro


Parece ser que ademas de las limitaciones que le pone speedy al modem se olvidaron de arreglar eso jaja, que bizarros. Bueno ahora de seguro va a andar mejor, aparte no te va a ser dificil configurar puertos para NAT y demas.

PD: Desactiva el UPnP en el router(por si viene activado), por mas que uses Linux es inseguro tenerlo activado!!!!

---

