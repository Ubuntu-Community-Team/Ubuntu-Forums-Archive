---
title: "[SOLVED] FIrefox no abre (casi) ninguna página!!!!!!"
date: 2008-09-24
forum: Software
---

### Post by valucha on 2008-09-24
[COLOR="DarkOrchid"]Al igual que mucha gente yo no puedo entrar a google aveces, pero no es solo eso, tampoco puedo entrar a muchas otras páginas. Mercadolibre, gmail, youtube y todas esas que parecen de google ;). Y es realmente muy molesto.
Reinstalé el flash, reinstalé Ubuntu, borré el caché, y no hay caso, me queda la página en blanco con el cartelito abajo que dice "listo".

Ya ni sé que hacer, quería instalar Chrome en Ubuntu, pero con WIne no anda y compilandolo, nosé si hago algo mal o qué pero en la parte de sincronizar está horas enteras haciendo algo que no entiendo (y tampoco explican en las páginas donde te enseñan a hacerlo) y nunca llego a compilarlo.

Tengo FIbertel, un router D-link, una placa integrada a la ASUS M2N4-MX conexión alámbrica desde mi compu al router, Ubuntu con gnome (y con KDE) y Firefox 3.0. Esto me pasaba de antes de FF 3.0, masomenos desde que usaba el beta.

Sé que no es ni FIbertel, ni el router, ni la conexión porque en WIndows entro sin problemas, pero... por otro lado, mi viejo desde su notebook con wifi y ubuntu con firefox 3.0 entra perfecto!!!...

¿Qué puede ser?


Muchisismas gracias desde ya, y avisen si rompo mucho las bolas :)[/COLOR]

---

### Post by sajnox on 2008-09-24
Por el momento, bahh si te gusta tambien definitivo

```
sudo apt-get install opera
```

Veamos que pasa con otro navegador....

---

### Post by leo_rockway on 2008-09-24
Ehem... Opera no es libre... Konqueror es libre... jaja.

Hacé como dice Miguel y fijate si con otro navegador te anda. Yo iría un poco más lejos e instalaría lynx que no tiene javascript, ni flash, ni java.

Si no podés visualizar Google en modo texto algo raro pasa...

---

### Post by santiagoward2000 on 2008-09-24
> **leo_rockway said:**
> Ehem... Opera no es libre... Konqueror es libre... jaja.

Hacé como dice Miguel y fijate si con otro navegador te anda. Yo iría un poco más lejos e instalaría lynx que no tiene javascript, ni flash, ni java.

Si no podés visualizar Google en modo texto algo raro pasa...

¿Y si prueba con w3m que ya viene instalado?

---

### Post by leo_rockway on 2008-09-24
No sabía que w3m venía instalado. Yo dije lynx porque es el que suelo usar por ssh.

---

### Post by sajnox on 2008-09-24
Interesante, nunca habia usado un navegador en modo texto.

Valucha, en castellano te dicen que en una terminal ejecutes

w3m [www.clarin.com](www.clarin.com)

---

### Post by juanman on 2008-09-25
> **valucha said:**
> [COLOR="DarkOrchid"]Al igual que mucha gente yo no puedo entrar a google aveces, pero no es solo eso, tampoco puedo entrar a muchas otras páginas. Mercadolibre, gmail, youtube y todas esas que parecen de google ;). Y es realmente muy molesto.
Reinstalé el flash, reinstalé Ubuntu, borré el caché, y no hay caso, me queda la página en blanco con el cartelito abajo que dice "listo".[/COLOR]


Yo supongo q debe influir el problema general q hay con los DNS (el q convierte las direcciones en letras en IPs. Ej: cuando escribis google.com, primero se conecta al servidor DNS de Fibertel, q le dice q google.com es 72.14.207.99). Hubo un fallo grave del protocolo DNS hace un par de meses, y recien ahora lo estan solucionando por estos lares... Asi q hasta q no lo terminen de arreglar, vamos a seguir con problemas :S
Soluciones, muchas no hay. Una seria usar otro servidor DNS. Mucha gente esta usando OpenDNS, pero tambien dicen q anda lento y ademas [filtra las busquedas que hacemos]("http://www.kriptopolis.org/adios-opendns")
Como sea, aca te explica como configurar OpenDNS en Ubuntu: [http://www.gotocosmik.com/wp/?p=52](http://www.gotocosmik.com/wp/?p=52)

> **valucha said:**
> [COLOR="DarkOrchid"]
Ya ni sé que hacer, quería instalar Chrome en Ubuntu, pero con WIne no anda y compilandolo, nosé si hago algo mal o qué pero en la parte de sincronizar está horas enteras haciendo algo que no entiendo (y tampoco explican en las páginas donde te enseñan a hacerlo) y nunca llego a compilarlo.
[/COLOR]

Lo mas facil para usar chrome en linux es con el crossover chromium: [http://www.codeweavers.com/services/ports/chromium/](http://www.codeweavers.com/services/ports/chromium/)
Es un port q hizo la gente de codeweavers basandose en la version de chrome de windows y su producto basado en wine... Hay paquets deb para ubuntu... OJO! Es solo para probarlo, no es recomendable usarlo como navegador por defecto...

Saludos

---

### Post by valucha on 2008-09-25
[COLOR="DarkOrchid"]Bueno, primeramente tengo que decir que pongo todas las fichas en el Firefox. Bajé Opera 9 tal comome dijeron y no solo que ya no tengo más problema con ninguna página, sino que además que anda muchisimo más rápido. Hasta me atrevería a decir que mejora la velocidad que tiene Chrome en Windows en mi misma máquna.


Haciendo w3m [www.google.com.ar](www.google.com.ar), o w3m [www.clarin.com.ar](www.clarin.com.ar), etc, entra también sin problemas a las páginas.


No lo quiero dar como solvedporque yo la solución la encontré cambiando de explorador, pero qué hay de aquel que quiera usar Firefox?




Edito: me estuve fijando y en un foro muy conocido la gente se quejaba d e lo mismo echandole toda la culpa a Fibertel .Tal vez sea casualidad que dejó de pasar y justo yo instalé y usé el Opera. Pero bueno, descubri que es mucho mejor navegador así que me quedo con este :)[/COLOR]

---

### Post by leo_rockway on 2008-09-25
> **valucha said:**
> Bajé Opera 9 tal comome dijeron y no solo que ya no tengo más problema con ninguna página, sino que además que anda muchisimo más rápido. Hasta me atrevería a decir que mejora la velocidad que tiene Chrome en Windows en mi misma máquna.

Edito: me estuve fijando y en un foro muy conocido la gente se quejaba d e lo mismo echandole toda la culpa a Fibertel .Tal vez sea casualidad que dejó de pasar y justo yo instalé y usé el Opera. Pero bueno, descubri que es mucho mejor navegador así que me quedo con este :)

Estoy casi seguro que el problema debía andar por Fibertel y no por FF. De todas formas, y a pesar de que va en contra del software libre, yo sigo diciendo que Opera es el mejor navegador web que existe. Eso sí... lo sigue muy de cerca Konqueror, la navaja suiza xD.

---

### Post by WanderingKnight on 2008-09-25
Fibertel ayer hasta las 22:30 más o menos no anduvo ni para adelante ni para atrás, así que apoyo la idea de Leo de que era culpa de eso.

---

### Post by pol666 on 2008-09-25
jjajaja no valu fue problema de tu ISP, Fibertel y speedy estuvieron con problemas.

---

### Post by valucha on 2008-09-25
[COLOR="DarkOrchid"]Jajaja eso demuestra una vez más mi ansiedad de no esperar y postear acá inmediatamente :$ ajja[/COLOR]

---

### Post by InsektO on 2008-09-26
De hecho, ayer si llamabas a la noche a FiberTel (entre las 20-23 horas) y seleccionabas la opción de "Soporte técnico", no te atendía ningún operador, sino que directamente te salía una grabación que decía "El servicio de navegación no se encuentra disponible"... :/

---

### Post by valucha on 2008-09-26
E[COLOR="DarkOrchid"]s que no puedo llamar a Fibertel, como tengo LInux ellos "no dan soporte tecnico a Linux"[/COLOR]

---

### Post by InsektO on 2008-09-26
> **valucha said:**
> E[COLOR="DarkOrchid"]s que no puedo llamar a Fibertel, como tengo LInux ellos "no dan soporte tecnico a Linux"[/COLOR]

Yo llamo simplemente para quejarme. Y eventualmente, si necesitan hacer alguna prueba (que no saben más que decirte que pruebes unos pings o cosas así muy básicas - que supongo que ni ellos entienden, pero tienen ese disquito preparado -), me paso al Win XP.

De todas formas, el motivo principal de llamar, además de quejarme, y exigir el número de ticket para que quede en el historial mi reclamo, es solicitar que me den la bonificación correspondiente del abono al tiempo que el servicio no funciona correctamente. Y lo hacen sin protestar. Serán 4 ó 5 pesos en Argentina, que es poco, pero no pienso pagarles por un servicio defectuoso como si fuera perfecto. :)

---

### Post by valucha on 2008-09-26
[COLOR="DarkOrchid"]Jajajaja vos si que tenés suerte... A mi esas cosas de "devolveme lo que me diste mal" no me funcionan. En mi intento de pasarme a Arnet proque un día me llamaron y me convencieron con una promo y yo estaba harta de fibertel, tuve que esperar 1 mes a que me digitalizaran la linea (y ya hasta me habia llegado el router y todo) y mientras me cobraban. Al mes y 1 semana me cansé, llamé los re putié y lo di de baja, y no podía, tenía que esperar 3 meses o me cobraban una suma enorme... Le conté a mi papá quien, por suerte, conocía a alguien que tabajaba ahi y nos dieron de baja cobrandonos el mes que supuestamente tuve Arnet pero no me pude conectar NI UN DÍA, porque la linea no estaba digitalizada...


Buehm, igual me fui al ******. Pongo esto como solved y listo.[/COLOR]

---

### Post by santiagoward2000 on 2008-09-26
> **valucha said:**
> [COLOR="DarkOrchid"]Jajajaja vos si que tenés suerte... A mi esas cosas de "devolveme lo que me diste mal" no me funcionan. En mi intento de pasarme a Arnet proque un día me llamaron y me convencieron con una promo y yo estaba harta de fibertel, tuve que esperar 1 mes a que me digitalizaran la linea (y ya hasta me habia llegado el router y todo) y mientras me cobraban. Al mes y 1 semana me cansé, llamé los re putié y lo di de baja, y no podía, tenía que esperar 3 meses o me cobraban una suma enorme... Le conté a mi papá quien, por suerte, conocía a alguien que tabajaba ahi y nos dieron de baja cobrandonos el mes que supuestamente tuve Arnet pero no me pude conectar NI UN DÍA, porque la linea no estaba digitalizada...


Buehm, igual me fui al ******. Pongo esto como solved y listo.[/COLOR]

Uh, pensé que era sólo acá! A mí cuando me pasé de Arnet (dialup) a Speedy (que recién instalaban acá en Bariloche) no me querían cortar Arnet! Estuvieron cómo 6 meses mandando facturas a casa...

---

