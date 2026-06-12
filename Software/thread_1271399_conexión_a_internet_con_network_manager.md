---
title: "conexión a internet con network manager"
date: 2009-09-20
forum: Software
---

### Post by Camilow on 2009-09-20
He instalado el ubuntu 9.04 para 64 bit, tengo una conexión adsl de telefónica y no he podido lograr que network manager la reconozca. Me conecto a través de la terminal... pero la primera vez que pongo el comando 'sudo pon dsl-provider' intento abrir el firefox y no está conectado. Normalmente se soluciona desconectandome y volviendo a conectarme. Esto debo hacerlo siempre. Este metodo me parece algo engorroso y preferiría que lo hiciera el network manager (entiendo que puede hacerlo).

agradezco cualquier ayuda, pues soy completamente nuevo en esto y el primer par de días con ubuntu me la he pasado tratando de solucionar esto.

gracias y saludos

---

### Post by nopersona on 2009-09-21
Si configuraste la cuenta con pppoeconf podría ser los permisos de tu usuario para la conexión, recuerdo que la primera vez que instalé jaunty tuve este problema, a algunos más les pasó. Revisalos en sistema, usuarios, hay una pestaña de permisos de tales y cuales cosas, no recuerdo bien, estoy en KDE, burp. 

A todo esto, te conectas con sudo pon dsl-provider, o con pon dsl-provider?

---

### Post by moreback on 2009-09-21
**pon dsl-provider** levanta la conexión adsl saltándose el Network-Manager. Para que te funcione con NM tienes que configurar todo con NM, Editar conexiones..., pestaña DSL.

---

### Post by AlexDDR on 2009-09-22
claro como dice moreback, para que te funcione con networkmanager tiene que borrar la configuracion del archivo de texto de la conexiones ya que ahi creo la conexion ppoeconf , creo que era el siguiente archivo el que hay que editar para  quitar la parte del pppoeconf


en la consola escribes 
> gedit /etc/network/interfaces


y borrar la conexion perteneciente a ppp y dejas solo esto que tengo yo 

auto lo
iface lo inet loopback


Ahora despues de eso no se si es que hay uqe reinicia o hacer logout pero mejor reinicia por si las dudas

 despues configuras tu conexion adsl por el network manager que es el que esta al lado del reloj  con el boton derecho "editar conexiones" agregando una conexión en la pestaña  DSL que es la ultima, la creas con tu usuario y contraseña de adsl y seleccionas conectar automaticamente y le creas un nombre que te resulte familiar, despues te vas a la pestaña CABLEADA y editas la "Auto Eth0" y desmarcas la opcion conectar automaticamente y aceptas, con eso lograras que cada vez que te loguees en tu cuenta conecte automaticamente a internet si tene que pinchar sobre el icono red y pinchar sobre la conexion adsl para conectar


espero te sirva , ya que si te puedes conecta por pppoeconf te tiene que poder conectar por el Networkmanager


saludos

---

### Post by Camilow on 2009-09-22
Muchas gracias por la ayuda gente amable. Finalmente borré el registro pppoeconf como me lo indicaba Alex y después configuré desde el Network Manager... y resultó. Le quité la conexión automática a Auto Eth0 y ahora me conecta a internet en cuanto abro sesión.

Muchas gracias por la ayuda.

---

### Post by Camilow on 2009-11-05
los molesto otra vez...

La conexión me ha funcionado muy bien... hasta que actualicé a ubuntu 9.10. Después de eso ya no me conecta a pesar que la configuración no fue afectada en la actualización (al menos aparece tal y como lo dejé según los consejos de alexddr).

Ya no se que hacer... ayuda plis
gracias

---

### Post by Mattos on 2009-11-07
Hola a todos,

Al fin encuentro a alguien que se conecta de esta misma forma ;) en estos tiempos. No sabes cuanto trabajo me ha resultado poder tener internet. Bueno yo me conecto y desconecto por terminal siempre con sudo pon dsl-provider. Entonces al querer hacerlo con el network manager que explican aqui, que le pones en el campo **servicio** de la configuracion del ADSL. Cuando creo una nueva me sale los campos Usuario, Servicio y Contraseña. y en las otras pestañas ajustes PPP, Ajustes IPV4 Debo dejarlos en blanco?

Sorry por lo nooby pero lo único que asimilo es el usuario y la contraseña :P

Quiero hacerlo por este método ya que la otra idea era por medio de un script pero al parecer este método de conexión ya esta des actualizada. He buscado miles de paginas que expliquen, pero siempre ya estan inactivas y la ultima que encontré fue una del año 2001 pero estaba copiada de otro manual e incompleto.

Saludos,

Ubuntu 9.04 32bits

---

### Post by AlexDDR on 2009-11-07
Segun recuerdo (es que ahora me compre un router, jejee ALWAYS ON), todo se deja tal cual y por lo menos para telefonica speedy ingresaba solo el usuario y la contraseña. Pero de todas formas siempre debes tener en cuanta la foma en que te conectas desde windows, por ejemplo para modificar cualquiera de  las dos opciones. Para conectar despues de configurada la cuenta solotiene que pinchar en el icono nuevamente peor esta vez con el boton izquierdo del mouse y elegir la conexion adsl que creaste.

Tambien puedes hacer que se conecte automaticamente como explico arriba.

saludos.


@Camilow: pienso que deberias borrar tus configuraciones y configurarlas nuevamente. La verdad es que no todo me ha quedado fino con la actualizacion de la 9.04 a la 9.10 asi que preferi reinstalar.

---

### Post by Mattos on 2009-11-08
Muchas gracias por el dato. Voy a intentarlo y ver que tal me va. ):P

> **AlexDDR said:**
> Segun recuerdo (es que ahora me compre un router, jejee ALWAYS ON)

Ya digo yo, que el debe hacer todo el trabajo para la conexion es el router y no yo :p Haber si puedo hacerme de uno de esos.

---

### Post by AlexDDR on 2009-11-09
jaja sip, me compre un DLINK dir-280 con wifi en pcfactory, el mas barato que encontre (falta de $$$$) para hacer una minired en mi casa y ahora no me preocupo de internet, pruebo live cds y ya no tengo que nadar configurando nada. es bastante comodo, pero creo que si uno quiere algo bueno deberia ir por uno un poco mas caro que lo que tengo, pero para uso "home" esta de pelos.

pensar que pa ponerme el router en telefonica (ahora movistar )me cobraban 2o 3 mil pesos mensuales


saludos

---

