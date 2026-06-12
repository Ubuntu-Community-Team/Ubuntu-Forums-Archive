---
title: "Estado de Ubuntu 64 bits?"
date: 2009-08-30
forum: Software
---

### Post by pol666 on 2009-08-30
Ahora que tengo el phenom x4 tenia ganas de ponerle un sistema 64 bit, hace unos años decian que no valia la pena.. me pregunto que tal ahora, el que tenga un 9.04 64 bit que tal anda, hay software que no se consiga o lo esencial esta?.

Capaz me conviene esperar a Octubre? que dicen....

---

### Post by pablo.s on 2009-08-30
De todas maneras, siendo que
instales 32 bits o 64 bits una buena
idea sería compilarle un núcleo con
la opción de Phenom x4, asi vas a 
poder utilizar el procesador a su
potencia real, porque tengo entendido
que los núcleos de 64 bits vienen
con el flag de 2 núcleos.

---

### Post by Hei Ku on 2009-08-30
> **pablo.s said:**
> De todas maneras, siendo que
instales 32 bits o 64 bits una buena
idea sería compilarle un núcleo con
la opción de Phenom x4, asi vas a 
poder utilizar el procesador a su
potencia real, porque tengo entendido
que los núcleos de 64 bits vienen
con el flag de 2 núcleos.

Tengo aca 4 cores Phenom que dicen lo contrario. 

Andan quemando electrones desde Hardy. :lolflag:

---

### Post by pablo.s on 2009-08-30
> **Hei Ku said:**
> Tengo aca 4 cores Phenom que dicen lo contrario.

OK. Pero sabés que cuando
compilás el núcleo te da a elegir
el procesador?
Eso digo.
Supongamos que estás usando
un núcleo que lo compilaron para
un Turion 64 y en esa epoca venian
con ciertas instrucciones. Ahora yo
creo que el Phenom tiene más
instrucciones y por lo tanto podria
desempeñarse mejor con una
compilación mejor adaptada.

---

### Post by Hei Ku on 2009-08-30
Obviamente que compilando para un procesador especifico te puede andar mejor, pero no fue lo que dijiste. Por eso Gentoo o Arch son mas rapidas que Ubuntu. ;)

De todas maneras, el kernel hace mas de un año que hizo una modificacion para que la gran mayoría de cosas queden en generic, y solo lo que realmente es diferente este en las ramas especificas. Hasta antes de eso, las ramas i386 y x86_64 tenían muchas cosas duplicadas.

---

### Post by pol666 on 2009-08-30
Yo estoy tirando la misma instalación que tenia la otra pc por que es el mismo disco, así que imagigen que no hay nada optimizado... pasa que vi que levanto todo y lo deje.

Los 4 cores se me hace que estan trabajando en exceso, no se capaz es cosa del procesador en si..

---

### Post by pablo.s on 2009-08-30
Entonces volviendo a la cuestión
que pregunta Pol:
Vos afirmás que el núcleo que trae
la versión de 64 bits le va a habilitar
los cuatro núcleos del Phenom x4?

Cómo para orientarlo a Pol, porque
si es por nosotros podemos pasar
años hablando del tema...
Grande Hei Ku!

---

### Post by pol666 on 2009-08-30
Intuyo que una instalación desde 0 y aún mas una de 64 bits (y AUN mas compilar el kernel)  va a mejorar el rendimiento de los nucleos, por que si bien anda rápida, noto que trabajan mucho todos (alrededor del 40%) y sin cambios a simple vista en el rendimiento.

---

### Post by pablo.s on 2009-08-30
Ahí también va a estar el tema
de los programas que puedan
hacer provecho del multithreading
que da el procesador.
Hace poco compilé Blender 2.50 y
tiene la opción de activar esa
caracteristica dentro del programa.
Otro que trae esa opción es VLC.

---

### Post by Hei Ku on 2009-08-30
El de 64 bits te toma el multicore automaticamente. Yo tenia un AMD comun, pase a un X2 y a un Phenom X4 todo con la misma instalacion. Saben que no soy amigo de instalar. :D

De hecho, en un caso que no me lo tomaba era problema del firmware del mother. Una vez que lo actualice anduvo barbaro.

---

### Post by sergiom99 on 2009-08-30
Antes habia problemas con el Flash y otras cosas de multimedia en 64 bits.
Estan solucionandos?

---

### Post by josecuervo86 on 2009-08-30
Sergiom99, hace rato que no tengo problemas de flash. Se suele colgar a veces, pero es muy raro.

---

### Post by pol666 on 2009-08-30
de flash no puedo esperar mucho más anda mal en todos lados..

---

### Post by z37a on 2009-09-01
Desde hace un año o mas que soy usuario de 64 bits, si bien no uso multicore(tego un Athlon64 LE), si uso aplicaciones de 64 bits, hasta ahora el principal problema que encontre es el poco soporte en forma directa que hay sobre flash, pero la verdad que el alpha del flash para 64 bits anda muy bien, si bien tiene algun que otro cuelga de vez en cuando eso pasa tambien en la version de 32 bits(tengo otra pc con 32 bits) y bueno el java ya dispone de soporte oficial para dicha arquitectura, asi que en lo que es web no vas a tener drama, hasta ahora solo tengo problemas con el maildito silverlight, si bien no me gusta hay una pagina que visito que lo utiliza y me molesta mucho, peor bueno, eso supongo que pasa tambien con los 32 bits.

---

### Post by oberonking on 2009-09-10
Realmente lo que te ata a elegir uno u otro es la cantidad de Ram que quieres tener.

SO 32bits --> hasta 3 Gb no importa cuantos mas tengas te va a reconocer 3 Gb

SO 64bits --> no recuerdo hasta cuanto te deja, leí por ahí que 16 billones de GB, pero los mothers de hoy, al menos en mi país, soportan un máximo de 32 Gb.

Esa es la gran diferencia, otra cosa es para lo que lo vayas a utilizar.

Si quieres hacer videos, animación, etc; te recomiendo el de 64.
Ahora si lo que vas a hacer es utilizarla de Escritorio, puedes tener cualquiera de los 2, pero si eres de los que salga lo que salga lo prueban.... el de 32bits te va a servir mas (a menos que te guste compilar).

Espero te sirva de algo, saludos.

---

