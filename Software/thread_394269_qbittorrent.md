---
title: "qbittorrent"
date: 2007-03-26
forum: Software
---

### Post by undiaperfecto on 2007-03-26
Alguien de aca usa qbittorrent? O Recomiendan algun otro cliente? Yo lo instale porque azureus me funcionaba muy mal, pero ahora que le presto atencion, me esta bajando demasiado lento, nunca pasa de los 10k de bajada, en cambio con la subida no hay problema.
Probe bajar el mismo torrent desde win con utorrent y llega/supera los 80k de bajada. Alguien tiene idea de si hay que tocar la configuracion o algo para que baje un poquito mas decentemente?

---

### Post by lavaramano on 2007-03-26
yo suelo usar al cliente que viene por defecto.
no tengo ni idea de como se llama (?) pero va como trompada.

es cuestion de elegir un torrent con bastantes seeds.. creo. el victor torres (?) jamas me convencio igualmente.

---

### Post by javier.der on 2007-03-26
yo uso ktorrent y anda de lujo

---

### Post by beuno on 2007-03-26
deluge a muerte.
hecho en python, liviano y completo.
se gano mi corazon.

---

### Post by Tinchio on 2007-03-27
> **javier.der said:**
> yo uso ktorrent y anda de lujo


Idem, anda de 10 :)

---

### Post by tzulberti on 2007-03-27
Yo uso bittornado... Como dijo lavaramano, lo mas importante es el torrent en si

---

### Post by felipelerena on 2007-03-27
Deluge. Zarpado

---

### Post by spg76 on 2007-03-27
Deluge está muy bueno y evoluciona muy rápido, mi único problema es que muchos trackers privados todavía no lo aceptan. Igual esto es más un incoveniente de esos trackers que de Deluge.

---

### Post by kowal on 2007-03-28
Otro voto para **Ktorrent**. Aunque creo que también deberías tener en cuenta: a) la cantidad de seeds b) tener abiertos los puertos correspondientes.

---

### Post by undiaperfecto on 2007-03-28
Voy a probar con deluge que parece que es el mas recomendado, el que viene por defecto esta bueno, pero no se, lo veo muy flaco. 
Ojala que deluge funcione bien con demonoid.com

---

### Post by ttakun on 2007-03-28
Yo hasta el otro día usaba **[COLOR="Navy"]rtorrent 0.7.1[/COLOR]**, que se ejecuta directamente desde el terminal. Nada de ventanas. Muy ligero. muy estable y ofrece mucha infromación, a pesar de que haya que hacerlo todo a través de comandos. La única pega puede ser que parece hay problemas con los trackers privados (demonoid, ...) para actualizar los ratios de bajada/subida.
Ayer me bajé e instale [COLOR="Navy"]**Deluge**[/COLOR], para ver si mi ratio se actualiza correctamente. Por ahora estoy encantado con él. Instalación y funcionamiento, sin problemas, a pesar de estar todavía en la versión 0.5.0.

---

### Post by Benji86 on 2007-03-28
BitTornado anda muy bien

---

### Post by undiaperfecto on 2007-03-29
Deluge me anduvo perfecto, pero el problema sigue siendo demonoid, esta muuuuy lento, pero el programa es barbaro.

---

### Post by godzeus on 2007-03-31
Ktorrent, sin dudarlo, lo mejor.

---

### Post by jpmorelli on 2007-03-31
Jamás lo probé en Linux ( en Win si y es lo mejor !!! ), pero las malas lenguas andan diciendo por ahí que el utorrent ejecutado via wine la rompe como ningún cliente nativo... ver para creer.

---

### Post by undiaperfecto on 2007-04-01
y como se lehace?

---

### Post by spg76 on 2007-04-01
> **jmorelli said:**
> Jamás lo probé en Linux ( en Win si y es lo mejor !!! ), pero las malas lenguas andan diciendo por ahí que el utorrent ejecutado via wine la rompe como ningún cliente nativo... ver para creer.

A mi particularmente es lo que mejor me funciona.

> **undiaperfecto said:**
> y como se lehace?

Si tenes Wine instalado (sino hace "sudo apt-get install wine"), baja utorrent desde [acá]("http://download.utorrent.com/1.6.1/utorrent.exe").
Hace clic derecho > "Abrir con otra aplicación" > "Usar uncomando personalizado", ahí escribí "wine" y listo.
Espero que te sirva.

---

### Post by undiaperfecto on 2007-04-01
voy a dejar bajando algo y mañana te cuento como me fue
gracias por el dato.

---

### Post by juandeargentina on 2009-11-10
> **undiaperfecto said:**
> voy a dejar bajando algo y mañana te cuento como me fue
gracias por el dato.

Se que este post es viejiiiisimo pero la verdad como no esta cerrado decidi repreguntar. 

Tengo exactamente el mismo problema que vos. 

Use el bittorrent, Deluge y Azureus. Todos no llegan a bajar en mas de 80 kB/s. 

Con el uTorrent bajo Win supera con creces esa velocidad. Mi pregunta es si con el Wine te funciono igual de bien o es solo un mito.

Abrazo
Gracias de antemano

---

### Post by guillermolisi on 2009-11-11
Si con cualquiera de esos programas logras el mismo resultado, entonces la limitacion no esta en ellos sino en tu conexion a Internet con lo cual no veo razon como para que cualquiera de ellos bajo Wine funcionen mejor (con una tasa de transferencia mayor que la lograda nativamente en Linux).

---

### Post by Brath-ga on 2009-11-11
Yo en estos momentos tengo qbittorrent solamente porque tiene un buscador de torrents implementado, aunque el que mejor me funcionó fue el utorrent por wine pero no tiene el buscador.
Después de haber probado muchos, tengo comrobado que la diferencia en las transferencias no depende solo de la conexión que se tenga, sinó del propio cliente.

---

### Post by SLA_leandrin on 2009-11-11
> **juandeargentina said:**
> Se que este post es viejiiiisimo pero la verdad como no esta cerrado decidi repreguntar. 

Tengo exactamente el mismo problema que vos. 

Use el bittorrent, Deluge y Azureus. Todos no llegan a bajar en mas de 80 kB/s. 

Con el uTorrent bajo Win supera con creces esa velocidad. Mi pregunta es si con el Wine te funciono igual de bien o es solo un mito.

Abrazo
Gracias de antemano

Tal vez tengas algún puerto cerrado? No se... yo logro velocidades **superlativas** en estos momentos con **Transmission**[SIZE="1"](1)[/SIZE] que es el cliente que viene por defecto en Ubuntu. Excelentes resultados con **ktorrent** y **deluge** en Kubuntu.

[SIZE="1"](1) En estos momentos 160 Kbs[/SIZE]

---

### Post by juandeargentina on 2009-11-11
Antes que nada, gracias a todos por responder. 

El tema es que como bien dijo Brath... sí depende del cliente. Desconozco las razones técnicas.

Voy a poner mejor en contexto el tema.
Antes tenia WinXP y uTorrent. 

Ej. 1:
Mismo tracker seeds a full (>200) bajaba una peli (aprox. 4 GB) en 2 o 3 horas.
Ej. 2: 
Mismo ejemplo que el anterior entre 10 y 50 seeds una peli me bajaba en 24 horas maximo.

Entiendo que existen muchos factores en el medio que pueden llegar a dar esto ( ancho de banda de upload del seed/peer, etc). Pero probe con todos las variables posibles. En conclusión...NO puede ser que en el ej. 1 este tardando mas de una semana. 

Descartado de plano la conexión y/o FW porque en el router de Arnet te permite establecer una DMZ y agregue la IP de ese equipo. 

Por el lado de FW instale el ufw y me dijo que el fw de ubuntu estaba deshabilitado. El testeo de los puertos da OK.

Ayer a la noche dejé instalando el Wine, cuando llegue a mi casa lo voy a probar. 

La verdad es que estoy un poco decepcionado porque me pase de win a Ubuntu precisamente porque me servia de excusa para comparar funcionalidades "de usuario". Espero salvar este escollo para poder seguir probando. 

Saludos a todos.

---

### Post by guillermolisi on 2009-11-11
> **juandeargentina said:**
> 

Por el lado de FW instale el ufw y me dijo que el fw de ubuntu estaba deshabilitado. El testeo de los puertos da OK.


Un aclaracion al respecto:

En Linux el FW es parte del kernel y se administra externamente ya sea con instrucciones en linea de comando (consola) o mediante alguna herramienta grafica (tipo Firestarter, por ejemplo).

El FW esta siempre activo porque el kernel lo esta al inciar y funcionar la maquina, y "de fabrica" viene con todos los puertos cerrados que se abren cuando inicias algun servicio que demande comunicacion con el exterior. O sea, para salir tenes via libre pero para entrar no podes a menos que hayas abierto exprofeso o un servicio este escuchando a traves de un port.

De hecho, para usar adecuadamente KTorrent y aMule tuve que habilitar varios ports para lograr maxima funcionalidad en ambos casos.

---

### Post by juandeargentina on 2009-11-11
> **guillermolisi said:**
> Un aclaracion al respecto:

En Linux el FW es parte del kernel y se administra externamente ya sea con instrucciones en linea de comando (consola) o mediante alguna herramienta grafica (tipo Firestarter, por ejemplo).

El FW esta siempre activo porque el kernel lo esta al inciar y funcionar la maquina, y "de fabrica" viene con todos los puertos cerrados que se abren cuando inicias algun servicio que demande comunicacion con el exterior. O sea, para salir tenes via libre pero para entrar no podes a menos que hayas abierto exprofeso o un servicio este escuchando a traves de un port.

De hecho, para usar adecuadamente KTorrent y aMule tuve que habilitar varios ports para lograr maxima funcionalidad en ambos casos.

Bien, ultima prueba entonces. ¿Sabes como deshabilitar completamente el fw?

---

