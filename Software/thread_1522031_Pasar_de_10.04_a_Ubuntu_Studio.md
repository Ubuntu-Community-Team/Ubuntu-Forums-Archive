---
title: "Pasar de 10.04 a Ubuntu Studio"
date: 2010-07-01
forum: Software
---

### Post by ketzelleshelle on 2010-07-01
Hola quería preguntar si es posible pasar de Ubuntu 10.04 Lucid Lynx a Ubuntu Studio sin perder nada, como si simplemente hiciera un upgrade de versión.

Muchas Gracias.

---

### Post by guillermolisi on 2010-07-03
> **ketzelleshelle said:**
> Hola quería preguntar si es posible pasar de Ubuntu 10.04 Lucid Lynx a Ubuntu Studio sin perder nada, como si simplemente hiciera un upgrade de versión.

Muchas Gracias.
Las grandes diferencias entre Ubuntu Studio y Ubuntu generico son: Kernel RT (Real Time) y la cantidad de paquetes incluidos en la primera distribucion que estan especializados en multimedia (video, diseño grafico y sonido).

---

### Post by ketzelleshelle on 2010-07-03
Si Guillermo, conozco las diferencias. La pregunta es otra: si puedo hacer el switch simplemente instalando uno sobre otro (como cuando hacemos un update de versión).
Gracias!

---

### Post by joseluis on 2010-07-03
Desde synaptic, en Edicion, Marcar paquetes por tares, tenes opcion de marcar lo que corresponde a Video o Sonido. No es directamente Ubuntu Studio, pero si lo que necesitas son los paquetes esos, ahi tenes una.

Por otro lado, imaigno que pones el Alternate de Studio mientras estas en Ubuntu, suele poner el cartel sobre "actualizar...etc..."

Por otro lado...me interesaría si me explican un poquito al menos eso de Kernel Real Time, ya que tengo ambos isntalados en dos discos (en uno Ubuntu y otro Ubuntu Studio) y no veo la diferencia.

---

### Post by alfplayer on 2010-07-03
Está para averiguar, pero podría ser posible tener los dos instalados al mismo tiempo, booteando el kernel que se necesite.

Seguramente se encuentra información del kernel RT buscando en la web.

---

### Post by guillermolisi on 2010-07-03
> **joseluis said:**
> Desde synaptic, en Edicion, Marcar paquetes por tares, tenes opcion de marcar lo que corresponde a Video o Sonido. No es directamente Ubuntu Studio, pero si lo que necesitas son los paquetes esos, ahi tenes una.

Por otro lado, imaigno que pones el Alternate de Studio mientras estas en Ubuntu, suele poner el cartel sobre "actualizar...etc..."

Por otro lado...me interesaría si me explican un poquito al menos eso de Kernel Real Time, ya que tengo ambos isntalados en dos discos (en uno Ubuntu y otro Ubuntu Studio) y no veo la diferencia.
La diferencia la notas cuando algun programa requiere respuesta en tiempo real por parte del kernel. Eso es, que el proceso empiece y termine sin ningun tipo de interrupcion por parte del SO para darle lugar a otro proceso, dicho rapida y simplemente.

Los programas de uso de escritorio/oficina no requieren, normalmente, de esta caracteristica.

Si utilizas un CD/DVD de Ubuntu Studio se actualizaran aquellos paquetes que tengas instalados cuya version sea anterior a la del CD/DVD, ya que normalmente esta es la configuracion por defecto que queda luego de instalar habiendo otras alternativas para pautar las actualizaciones.

Los paquetes que se han seleccionado para Studio podes instalarlos desde los repositorios, eligiendo los que quieras utilizar solamente, por ejemplo.

El kernel RT tambien lo podes instalar desde los repositorios, asi que, entre una cosa y otra, podrias contar con lo que estas buscando preservando lo que ya tenes.

---

### Post by ginoroman on 2010-07-08
> **ketzelleshelle said:**
> Si Guillermo, conozco las diferencias. La pregunta es otra: si puedo hacer el switch simplemente instalando uno sobre otro (como cuando hacemos un update de versión).
Gracias!

Si, agrega los repositorios de ubuntu studios, luego descarga el kernel rt y por ultimo bajate los programas que vayas a usar.

---

### Post by ketzelleshelle on 2010-07-08
Ok. Instalé el kernel RT, pero ahora al inicio en el grub me sale lo siguiente:

Mount: mounting none on /dev failed no such devicec798565338

De todos modos elijo la opción e inicia, pero no sé darme cuenta de momento si todo funciona como debería o qué...

Alguna sugerencia? Gracias

-----------------------------------------------------------

Alguien?

---

