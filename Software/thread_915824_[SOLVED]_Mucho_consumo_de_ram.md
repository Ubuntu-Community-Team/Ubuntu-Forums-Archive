---
title: "[SOLVED] Mucho consumo de ram"
date: 2008-09-10
forum: Software
---

### Post by ramiro_md on 2008-09-10
Gente, en estos dias he tenido problemas de estabilidad con el sistema. Se suele colgar repentinamente unos segundos mientras chateo y escucho musica con amarok. La causa es, lo mas probable, un "alto consumo de ram". Resulta que tengo un applet en la barra de notificacion que me indica la ram usada y la swap. En los momentos donde suceden los cuelgue me informa q llevo usados 751 de 751 megas y que ya esta usando la swap =S..no entiendo a que se debe, si bien tengo el awn y 2 screenlets, no creo q me consuma todos los recursosde la memoria.
Me es extraño porque recien en estos dias anda pasando, intente deshabilitando algunos programas desde "sesiones" pero sigue igual. Les reuerdo que uso hardy 64 bits. Un saludo.

---

### Post by fmsismo on 2008-09-10
Tendrías que ver que aplicación es la que se dispara en memoria (seguramente en procesador también).

Ejecuta el "System Monitor" que esta en "Applications" -> "System Tools".

Eso te va a listar que aplicaciones tenes corriendo, el consumo de procesador y memoria de cada uno.  Podes ordenar por cada item.

Cuanto tengas identificado el programa que se dispara, vamos a tener más información para solucionarlo.

Saludos

---

### Post by niko_3100 on 2008-09-10
> **fmsismo said:**
> Tendrías que ver que aplicación es la que se dispara en memoria (seguramente en procesador también).

Ejecuta el "System Monitor" que esta en "Applications" -> "System Tools".

Eso te va a listar que aplicaciones tenes corriendo, el consumo de procesador y memoria de cada uno.  Podes ordenar por cada item.

Cuanto tengas identificado el programa que se dispara, vamos a tener más información para solucionarlo.

Saludos


Ameeeeennn... hace exactamente eso.

---

### Post by Mister X on 2008-09-10
Que tengas toda la RAM usada no quiere decir que es un problema, esto quiere decir que el sistema tiene muchas cosas cacheadas y por lo tanto cuando las necesita las lee desde la RAM y no desde el disco.

Tenés que fijarte cuanta SWAP llega a usar ya que esto significa que el sistema está paginando a disco (bajando de RAM al HD), esto si puede ser un problema, ya que hace al sistema mas lento y llegado un punto, el kernel empieza a bajar procesos para obtener memoria.

---

### Post by sdennie on 2008-09-10
Debés postear:

```

free -m

```

Como dijo Mister X, linux tiene un cache que, a propósito, consuma toda la RAM disponible (no tiene sentido a tener RAM completamente sin uso).  Si tenés mucho cache y esta usando swap, tambien podés, editar /etc/sysctl.conf y poner:

```

vm.swappiness = 0

```

Despues:

```

sudo sysctl -p

```

Con eso la maquina trata de nunca usar swap.

---

### Post by ramiro_md on 2008-09-10
GRacias por la data, cuando se vuelva loca otra vez la compu, hago todo lo que me sugieren y posteo.

---

### Post by ramiro_md on 2008-09-11
BUeno muchachos, ahora si se puso molesta la cosa xD, no me cierra eso de que me ocupe la memoria libre con caché. Me mata.
Y mas en estos dias donde pinto jugar al urban terror con los muchachos de la comunidad, porque estuve probando el juego, pero se me satura en un punto y se me tilda. =S
Si hay alguna forma de desactivar eso del cahce, pliz, un saludo.

---

### Post by faktorqm on 2008-09-12
No, no lo tenes que desactivar justamente, ese es uno de los puntos fuertes de cualquier gnu/linux, el manejo de memoria. Lo que vos denominas "cache" en realidad se llama prefetcher y lo que hace es "reservar" memoria. Entonces yo por ejemplo en mi pc tengo, no se, 200mb ocuapdos, abro el opera y sigo con el mismo consumo, abro el gedit y lo mismo. Eso esta para mantener el rendimiento general. ahora, que abras el juego y se te cuelge no tiene nada que ver con eso, yo en casa la pc anda 2 meses seguido sin apagarla pero ni bien pongo el quake 3 o el unreal tournament se me cuelga al caño... snif snif. Es todo un tema ese. Hei ku mos va a saber explicar mejor como funciona el prefetcher :D:D:D:KS

---

### Post by niko_3100 on 2008-09-12
si haces un TOP te muestras cuanta memoria esta usando solo para programas o te muestra toda la memoria includio el prefetcher?? Porque el otro dia hice un top y tenia como 1 gb de ram "used" cuando el conky me mostraba que solo tenia 310 megas ocupados.. ahora me agarro la duda.

---

### Post by sdennie on 2008-09-12
> **ramiro_md said:**
> BUeno muchachos, ahora si se puso molesta la cosa xD, no me cierra eso de que me ocupe la memoria libre con caché. Me mata.
Y mas en estos dias donde pinto jugar al urban terror con los muchachos de la comunidad, porque estuve probando el juego, pero se me satura en un punto y se me tilda. =S
Si hay alguna forma de desactivar eso del cahce, pliz, un saludo.

Me parece que es imposible a desactivar el cache.  La única cosa que podés hacer es decir al kernel que use todo el cache por memoria de programas antes de usar swap (que es parecido a desactivarlo en tu caso).  Te dí las direcciones allá arriba (lo de "swappiness = 0").

---

### Post by ramiro_md on 2008-09-12
Gracias muchachos, estaba en necio xD..el problema del juego era otro, hernan-amaya me recomendo desasctivar el compiz y salio andando si cuelgues =)EL sistema en si anda barbaro.
Un saludo.

---

### Post by Hei Ku on 2008-09-12
cuando haces un top te muestra todo el consumo de memoria. Pero si te fijas y sumas todos los programas, vas a ver que no sumas el consumo total.

En general, no deberia molestar, porque lo que hace es utilizar ciclos libres de procesador para cargar datos a memoria que podrias llegar a utilizar, pero si necesita otros los sobreescribe. El momento en que tenes que preocuparte es cuando el swap tambien empieza a llenarte, un sintoma clasico de firefox y flash.

---

