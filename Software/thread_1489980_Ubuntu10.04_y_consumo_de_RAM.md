---
title: "Ubuntu10.04 y consumo de RAM"
date: 2010-05-21
forum: Software
---

### Post by hectorivand on 2010-05-21
Estimados, alguien me puede explicar el consumo de memoria terrible que tiene, (50%) haciendo **nada**!

De paso les muestro un Screenshot de hace un rato, estaba instalando flash player, copiando archivos, escuchando música (se entrecortaba) y llego a consumir 1.4gb de memoria y estaba super inestable hasta incluse después de haber terminado los procesos, alguna idea?

Los leo. Gracias.

---

### Post by juancarlospaco on 2010-05-21
[I]Flash siempre es come RAM, se la come mal...
Por eso HTML5[/I]

---

### Post by hectorivand on 2010-05-21
> **juancarlospaco said:**
> [I]Flash siempre es come RAM, se la come mal...
Por eso HTML5[/I]

No padre, la instalación del paquete nada más! ahora con Firefox y tres pestañas el 61%.

Para más información las pestañas estan cargadas, Escritorio Wordpress, Gmail y Este foro. nada más.

Alguna idea?

---

### Post by alfplayer on 2010-05-21
Hola.

Podés ver con el monitor de sistema que usa memoria. Es mejor decir que la memoria se usa antes que se consume.

Con aplicaciones abiertas la memoria se usa aunque no hagas nada.

Lo de inestable tendrías que explicarlo mejor.

---

### Post by hectorivand on 2010-05-21
Alf gracias por comentar, lo de inestable era cuando tenia varios procesos corriendo, copiando archivos, escuchando música con ryth... e instalando un paquete, el consumo de memoria era muy alto para las tareas o no? 1.3gb de ram me parece una locura para tres procesos activos.

Lo veo con el monitor del sistema, estoy viendo que procesos levanta y el consumo que tienen, pero quiero entender porque tanto consumo de memoria, por más que las aplicaciones no se esten usando?

Saludos
Nacho

---

### Post by alfplayer on 2010-05-21
> **hectorivand said:**
> Alf gracias por comentar, lo de inestable era cuando tenia varios procesos corriendo, copiando archivos, escuchando música con ryth... e instalando un paquete, el consumo de memoria era muy alto para las tareas o no? 1.3gb de ram me parece una locura para tres procesos activos.

Sería bueno ver qué procesos usan memoria, pero en ese momento exacto, "adivinar" después se hace más difícil.

No se a qué le estás llamando inestable. Muchas veces se usa esa palabra cuando está fallando algo, pero no se si algo está fallando o qué está sucediendo.

> **hectorivand said:**
> Lo veo con el monitor del sistema, estoy viendo que procesos levanta y el consumo que tienen, pero quiero entender porque tanto consumo de memoria, por más que las aplicaciones no se esten usando?

Eso es una pregunta de computación, no solo de Ubuntu, y puede ser un tema complejo. Básicamente es porque la memoria (RAM de sistema) es para mantener datos del sistema como datos de aplicaciones, para que puedan ser accedidos (lectura/escritura) por programas (el acceso es más rápido, por ejemplo, que el acceso a datos en el disco rígido).

---

### Post by hictio on 2010-05-21
El uso del RAM, de todo el RAM, en Linux es normal.
No tiene sentido tener RAM sino se usa :) Realmente tenés que preocuparte si se usa el swap -porque a grosso modo- significa que el RAM no es suficiente, y swappea a disco, lo que hace que el sistema se ponga más lento.

---

### Post by alfplayer on 2010-05-21
> **hictio said:**
> No tiene sentido tener RAM sino se usa

Esto es lo que quise decir antes, un uso alto puede no ser importante. Pero también es cierto que los programas tienen que usar racionalmente la memoria disponible. Hay programas que toman mucha más memoria de la que realmente usan (en windows Exchange hace esto).

> **hictio said:**
> Realmente tenés que preocuparte si se usa el swap -porque a grosso modo- significa que el RAM no es suficiente, y swappea a disco, lo que hace que el sistema se ponga más lento.

Esto se puede ajustar con un valor que es *swappiness*, pero esa optimización se puede dejar más adelante.

---

### Post by hictio on 2010-05-21
> **alfplayer said:**
> ~snip~
Hay programas que toman mucha más memoria de la que realmente usan (en windows Exchange hace esto).


Totalmente de acuerdo, en Linux, sin ir más lejos, Firefox es notable por morfar RAM.

---

### Post by alfplayer on 2010-05-21
> **hictio said:**
> Totalmente de acuerdo, en Linux, sin ir más lejos, Firefox es notable por morfar RAM.

Porque el uso de memoria de Firefox puede ser muy alto son populares los ajustes "tweaks" para regular el uso de memoria de Firefox.

---

### Post by hectorivand on 2010-05-22
Bueno gente, más allá de los comentarios que dejarón los cuales le agradezco pero, tal vez soy yo, pero me tratan como un infeliz al que le discuten, si su procesador realmente es de x64 o si se para que sirve la ram.

Les cuento que encontre lo que me generaba el consumo de memoria y procesamiento (importante) y es el controlador de ATI, sin hacer nada, el equipo se va a más de 900mb de consumo y 20% de uso de CPU.

Actualmente mi Ubuntu esta con el driver que viene con la distro y el consumo esta en 450mb y el procesador en 18% (estoy descargando e instalando paquetes) asi que me voy a quedar con el driver "original" funciona excelente porque tengo los efectos activados al maximo y ni muuuu

En fin, dejo esto como referencia para el que tenga el mismo problema.

Nuevamente gracias por comentar.

Saludos
Nacho

---

### Post by alfplayer on 2010-05-22
> **hectorivand said:**
> Bueno gente, más allá de los comentarios que dejarón los cuales le agradezco pero, tal vez soy yo, pero me tratan como un infeliz al que le discuten, si su procesador realmente es de x64 o si se para que sirve la ram.

Esto es Ubuntu, no es personal.

---

### Post by guillermolisi on 2010-05-22
Hector

Lamento que tomes parte de los comentarios de la forma en que decis sentir.

No veo esa intencion en el desarrollo de este thread y de ningun otro y es parte de mi responsabilidad marcar esos desvios (del espiritu de esta comunidad) cuando sucedan o crea oportuno.

Algunas preguntas que hacemos parecen tontas pero preferimos ese punto de entrada para conocer en detalle la situacion y asegurarnos de ir con bases firmes a la solucion. Practicamente ninguno sabe cual es el verdadero nivel de conocimientos de los demas, salvo casos que se perfilan con su participacion a traves del tiempo, y por eso tambien se hacen preguntas que para algunos pareceran obvias y asi tener una idea de los conocimientos del otro (salvo que el caso se exponga con detalles suficientes como para entender que el otro sabe de que esta hablando).

Tal como te han dicho, nada personal, solo es un foro sobre Ubuntu y nadie aqui esta para juzgar los conocimientos del otro ni se requiere ser o aparentar ser un genio. Ayudar, aprender y colaborar son los lineamientos que rigen su funcionamiento.

Dicho esto, relajate, disfruta tu estadia aqui y de tu sistema con Ubuntu que cada vez funciona mejor.

---

### Post by hectorivand on 2010-05-22
> **guillermolisi said:**
> Hector

Lamento que tomes parte de los comentarios de la forma en que decis sentir.

No veo esa intencion en el desarrollo de este thread y de ningun otro y es parte de mi responsabilidad marcar esos desvios (del espiritu de esta comunidad) cuando sucedan o crea oportuno.

Algunas preguntas que hacemos parecen tontas pero preferimos ese punto de entrada para conocer en detalle la situacion y asegurarnos de ir con bases firmes a la solucion. Practicamente ninguno sabe cual es el verdadero nivel de conocimientos de los demas, salvo casos que se perfilan con su participacion a traves del tiempo, y por eso tambien se hacen preguntas que para algunos pareceran obvias y asi tener una idea de los conocimientos del otro (salvo que el caso se exponga con detalles suficientes como para entender que el otro sabe de que esta hablando).

Tal como te han dicho, nada personal, solo es un foro sobre Ubuntu y nadie aqui esta para juzgar los conocimientos del otro ni se requiere ser o aparentar ser un genio. Ayudar, aprender y colaborar son los lineamientos que rigen su funcionamiento.

Dicho esto, relajate, disfruta tu estadia aqui y de tu sistema con Ubuntu que cada vez funciona mejor.

Gracias Guillermo, gracias por el tiempo en el comentario. Tal cual como vos decis! pero por eso, en el otro tema, había puesto una parte de mi historia como para darle un contexto y no recibir mensajes del tipo, "fijate si esta conectado el cable de power".

De todos modos, también hago un mea culpa y se que tengo poca paciencia, con lo cual, si ofendi a alguien, disculpas!

Saludos, muchas gracias y nos estamos leyendo.

Buen fin de semana.
Héctor

---

### Post by jpmiranda on 2010-06-20
Os contaré que a mí me pasa igual en mi ordenador.
Placa base ASUS M2N SLI, 2GB RAM DDR 800, swap de 2GB, Gráfica NVidia 7300SE.
Prácticamente no tiengo aceleración gráfica (190fps con glxgears). Después de un para de horas funcionando (firefox, flashplayer, etc.) tengo la ram a un 97% y la swap al 100% usando Sysinfo.
Como antecedente os cuento que siempre ha funcionado correctamente con ubuntu 9.04 y 9.10.
No he podido instalar la 10.04 con entorno gráfico. He tenido que hacer uso de los CDs "alternate" de Ubuntu e instalar en modo texto. Después, desinstalar todo lo relacionado con nouveau e instalar el driver privativo de nvidia.
Siempre con él he tenido aceleración gráfica. Pues ahora no, a trancas y barrancas y al final consumo de ram y swap.
No sé si es problema del kernel y nouveau, pero con mi hardware va fatal.
Así es que...ya somos dos.
Saludos, y si tenéis alguna sugerencia...bien venida!!

---

### Post by alfplayer on 2010-06-20
> **jpmiranda said:**
> Os contaré que a mí me pasa igual en mi ordenador.
Placa base ASUS M2N SLI, 2GB RAM DDR 800, swap de 2GB, Gráfica NVidia 7300SE.
Prácticamente no tiengo aceleración gráfica (190fps con glxgears). Después de un para de horas funcionando (firefox, flashplayer, etc.) tengo la ram a un 97% y la swap al 100% usando Sysinfo.
Como antecedente os cuento que siempre ha funcionado correctamente con ubuntu 9.04 y 9.10.
No he podido instalar la 10.04 con entorno gráfico. He tenido que hacer uso de los CDs "alternate" de Ubuntu e instalar en modo texto. Después, desinstalar todo lo relacionado con nouveau e instalar el driver privativo de nvidia.
Siempre con él he tenido aceleración gráfica. Pues ahora no, a trancas y barrancas y al final consumo de ram y swap.
No sé si es problema del kernel y nouveau, pero con mi hardware va fatal.
Así es que...ya somos dos.
Saludos, y si tenéis alguna sugerencia...bien venida!!

Mi sugerencia es buscar información específica de la instalación de drivers y funcionamiento de la 7300 SE en Ubuntu 10.04. Si la información en la web no es suficiente se puede crear un tema específico para el problema.

---

