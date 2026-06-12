---
title: "Ubuntu Studio y Wubi"
date: 2009-10-31
forum: Software
---

### Post by Post Pop on 2009-10-31
Hola gente, soy nuevo.

El tema es el siguiente. Soy usuario de Windows y un "intento" de productor de música electronica.

Pero tenga una extrema fobia con el tema de la seguridad en Windows, además de que no consigo un buen funcionamiento.

Me gustaría probar Ubuntu Studio, pero como soy bastante newbie con el tema linux, quisiera probarlo con Wubi (es decis, instalarlo desde Windows) ya que no tengo ganas de meterme a hacer particiones y demás.

Quiero instalarlo en mi notebook, que tiene un procesador Core Duo, por lo que tendría que instalar la versión de 64 bits. Se puede instalar Ubuntu Studio de 64 bits con Wubi? porque según leí en wikipedia solo se puede instalar la versión de Ubuntu de 32 bits, sin embargo, en la página de Wubi creo haber leído que se puede instalar Ubuntu de 64 bits. 

En segundo lugar, es necesario que Wubi baje la Iso? porque me sería mas comodo si yo pudiera bajar la iso de Ubuntu Studio, y solo instalarla con Wubi. Es posible eso?

Otro tema, yo tengo una placa Maya 44 USB. Esta es una placa de dos canales de entrada y de salida. Es fundamental para mi ya que la utilizaría para DJing. Esta placa tiene unos drivers ASIO de la marca, que no creo poder instalar en linux (o si?). Sin embargo, yo en mi PC esta placa tambien puedo usarla sin instalar estos drivers, es decir, con tan solo los drivers genericos que trae windows ya puedo usarla (aunque sin contrar con los beneficios de ASIO claro). Podré entonces utilizarla con algun driver genérico en Ubuntu? En cuanto al tema de ASIO, leí por ahí que hay algo llamado WineAsio, que es una especie de versión de linux del conocido ASIO4All de Windows, pienso que si pudiera instalar esta placa doble con los drivers genéricos, podría bajar la latencia con eso, es así esto, o me equivoco?


Con respecto a la producción musical, obtendré mejor latencia con Ubuntu que con Windows? es fundamental para mi que el funcionamiento sea óptimo a la hora de producir o de tocar en vivo.

Por último, leí que Wubi tiene problemas con la versión de Windows Vista de la notebook, y alguien me dijo que puede dañarlo de tal manera que para repararlo necesitaría el cd de Vista que no viene con las notebooks, esto es así?

Perdonen la excesiva cantidad de preguntas, es que son realmente determinantes para mi para empezar a probar Ubuntu. 

Muchisimas gracias.

PostPop.

---

### Post by Mauro22 on 2009-10-31
> **Post Pop said:**
> Hola gente, soy nuevo.


Bienvenido! :p

> **Post Pop said:**
> 
Quiero instalarlo en mi notebook, que tiene un procesador Core Duo, por lo que tendría que instalar la versión de 64 bits. Se puede instalar Ubuntu Studio de 64 bits con Wubi? porque según leí en wikipedia solo se puede instalar la versión de Ubuntu de 32 bits, sin embargo, en la página de Wubi creo haber leído que se puede instalar Ubuntu de 64 bits. 


Si vas a empezar con gnu/linux, te recomiendo la de 32bits... no especificas la RAM pero asumo que son >= 2gb... a menos que trabajes con soft realmente pesados (o tengas > 4gb de ram) podes empezar con la de 32 bits... 64 bits tiene "asuntos" que son dificiles de lidiar con pocos conocimientos.

> **Post Pop said:**
> 
En segundo lugar, es necesario que Wubi baje la Iso? porque me sería mas comodo si yo pudiera bajar la iso de Ubuntu Studio, y solo instalarla con Wubi. Es posible eso?


Wubi es solo el instalador. Para instalar un Ubuntu Studio necesitas la ISO correspondiente, quemarlo en un CD o bien montar la ISO en una unidad virtual usando soft (por ejemplo el Daemon Tools). Una vez hecho aparece el asistente de Wubi

> **Post Pop said:**
> 
Otro tema, yo tengo una placa Maya 44 USB. Esta es una placa de dos canales de entrada y de salida. Es fundamental para mi ya que la utilizaría para DJing. Esta placa tiene unos drivers ASIO de la marca, que no creo poder instalar en linux (o si?). Sin embargo, yo en mi PC esta placa tambien puedo usarla sin instalar estos drivers, es decir, con tan solo los drivers genericos que trae windows ya puedo usarla (aunque sin contrar con los beneficios de ASIO claro). Podré entonces utilizarla con algun driver genérico en Ubuntu? En cuanto al tema de ASIO, leí por ahí que hay algo llamado WineAsio, que es una especie de versión de linux del conocido ASIO4All de Windows, pienso que si pudiera instalar esta placa doble con los drivers genéricos, podría bajar la latencia con eso, es así esto, o me equivoco?


Eso ni idea... al instalarlo vas a saber... aunque si con los genéricos en el otro "SO" levantó, aca lo tendría que hacer...


> **Post Pop said:**
> 
Con respecto a la producción musical, obtendré mejor latencia con Ubuntu que con Windows? es fundamental para mi que el funcionamiento sea óptimo a la hora de producir o de tocar en vivo.


GNU/linux administra mucho mejor los recursos que Ventanas... Claro está, que no es garantía que se cumpla en el 100% de los casos. Por lo general van a notar un cambio considerable en velocidad, rendimiento y usar un verdadero "multi-tareas"

> **Post Pop said:**
> 
Por último, leí que Wubi tiene problemas con la versión de Windows Vista de la notebook, y alguien me dijo que puede dañarlo de tal manera que para repararlo necesitaría el cd de Vista que no viene con las notebooks, esto es así?


A mi la notebook me vino con vista y estuve 5 meses con Ubuntu ("Wubizado") y nunca un drama, será porque Vista lo inicié 2 veces? de las cuales 1 se colgó??

> **Post Pop said:**
> 
Muchisimas gracias.



De nada ;)... 

Mi consejo: Antes de instalar sea por Wubi o Normal, quemá el cd De ubuntu Studio, Bootea desde el CD y podras usarlo al 90% sin instalar nada de nada...

---

### Post by Post Pop on 2009-10-31
Hola.

Justamente tengo 4 gb de ram, que lamentablemente no puedo aprovechar al maximo porque curiosamente la notebook me vino con un Vista de 32 bits.

Por lo que entendí, entonces el dvd de Ubuntu Studio ya incluye Wubi para instalar en Windows sin partición? 

Sobre el tema de bootear desde el DVD, ya lo hice hace un tiempo con una vieja versión de Ubuntu, el problema es que leí (aunque era una entrada vieja en otro foro) que no se puede bootear desde Ubuntu Studio, es decir que no se puede usar "live". No se si seguirá siendo así, tal vez ya lo han implementado.

Muchisimas gracias por tu respuesta :D

---

### Post by guillermolisi on 2009-10-31
> **Post Pop said:**
> Hola.

Justamente tengo 4 gb de ram, que lamentablemente no puedo aprovechar al maximo porque curiosamente la notebook me vino con un Vista de 32 bits.

Por lo que entendí, entonces el dvd de Ubuntu Studio ya incluye Wubi para instalar en Windows sin partición? 

Sobre el tema de bootear desde el DVD, ya lo hice hace un tiempo con una vieja versión de Ubuntu, el problema es que leí (aunque era una entrada vieja en otro foro) que no se puede bootear desde Ubuntu Studio, es decir que no se puede usar "live". No se si seguirá siendo así, tal vez ya lo han implementado.

Muchisimas gracias por tu respuesta :D
En los repos de U-Studio 9.10 (oficiales) solo mencionan "alternate" asi que me parece que aun no hay LiveCD/DVD.

---

### Post by Post Pop on 2009-10-31
Hola.

Así es, Ubuntu Studio por lo que acabo de verificar solo viene en "Alternate DVD". Podré entonces instalarlo con Wubi?

Muchas gracias a todos.

Saludos.

*PostPop*

---

