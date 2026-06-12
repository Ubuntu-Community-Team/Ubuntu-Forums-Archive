---
title: "GRUB 2 ¿No era gráfico?"
date: 2009-10-12
forum: Software
---

### Post by Andyvec on 2009-10-12
Hola a todos

Les comento que instalé Karmic BETA, funciona muy bien, arranca notoriamente más rápido.

El único problema que tengo es que GRUB 2 sigue siendo por consola (en realidad, no gráfico).

Intenté reinstalarlo, cambiar la imagen de fondo y actualizarlo mediante update-grub pero no hay forma de que ver una sola imagen.

¿Alguien sabe qué hay que hacer?

---

### Post by pablo.s on 2009-10-12
Te recomiendo leer [URL="http://ubuntuforums.org/showthread.php?t=1221784"]este
EXCELENTE post[/URL] de Gabriel
sobre Grub 2.

---

### Post by Andyvec on 2009-10-12
Gracias, la verdad que es un muy buen post. Sobre todo porque de GRUB 2 aún no hay documentación oficial ni suficiente información.

Sin embargo no responde a mi problema ¿Todo ven el inicio gráfico en GRUB 2?

---

### Post by pablo.s on 2009-10-12
> **Andyvec said:**
> Sin embargo no responde a mi problema ¿Todo ven el inicio gráfico en GRUB 2?

Hay un problema con grub2:
Tiene que llenar el lugar que
va a dejar grub legacy y por
eso mismo, no hay muchos
avances en la materia. Para
explicarlo mejor: Hace aprox.
siete u ocho años (si no más)
que grub legacy se viene
utilizando. Con lo cual se han
desarrollado muchas mejoras
y agregados para hacerlo lo más
bonito posible.
Por el otro lado, grub2 solo tiene
un año de uso, aunque ha sido
diseñado para ser muchisimo más
sofisticado que su predecesor, en
todo sentido.
Fijate en una búsqueda de Google
con la palabra "grub2 grafico", que
seguro hay implementaciones 
de lo que estás buscando.

---

### Post by Andyvec on 2009-10-13
La verdad es que ya busqué en Google y en todos los foros de ayuda, (dato curioso, si busco "grub2 grafico" ¡el cuatro resultado es este post!) pero todo lo que aparece es como instalarlo desde cero.

Los que probaron Karmic BETA ¿Ven el GRUB 2 con inicio gráfico?
Pues en mi caso si se instaló correctamente pero es muy similar al GRUB Legacy en cuanto a que es todo texto.

---

### Post by pablo.s on 2009-10-13
> **Andyvec said:**
> (dato curioso, si busco "grub2 grafico" ¡el cuatro resultado es este post!) pero todo lo que aparece es como instalarlo desde cero.

Fijate [acá]("http://grub.gibibit.com/").

> **Andyvec said:**
> Los que probaron Karmic BETA ¿Ven el GRUB 2 con inicio gráfico?

No, es lo mismo que tenés vos.

---

### Post by Andyvec on 2009-10-13
> **pablo.s said:**
> 
No, es lo mismo que tenés vos.

Ahhh... Entonces por ahora GRUB 2 no es gráfico.

Yo solamente encontré como poner una imagen de fondo, pero esto se podía hacer también en GRUB 1, lo que faltaría es como instalar un THEME como los que se ven acá:

[IMG]http://grub.gibibit.com/Theme_collage.png[/IMG]

---

### Post by pablo.s on 2009-10-13
> **Andyvec said:**
> lo que faltaría es como instalar un THEME como los que se ven acá:

El código para tener estos temas
lo ha publicado el autor en un
sistema de control de versiones 
que se llama Bazaar. Pero si de
veras tenés ganas de probarlo,
hay un [PPA que tiene paquetes]("https://launchpad.net/%7Edinxter/+archive/experimental")
compilados. Conste que [COLOR=Red][B]NO ME
HAGO RESPONSABLE DE LO
QUE HAGA A TU SISTEMA [/B]
[/COLOR]puesto que no los he probado yo
mismo.

---

### Post by Andyvec on 2009-10-13
Muchas gracias, son exactamente los paquetes que buscaba. Puede instalarlos pero pero no &#347;e como hacerlos andar, seguiré intentando.

Saludos

---

### Post by gmunioz on 2009-10-14
Sumimasen por la intromisión:

Esta es la página oficial del Grub2

[http://www.gnu.org/software/grub/grub-2-support.en.html](http://www.gnu.org/software/grub/grub-2-support.en.html)

Esta es la página de su manual

[http://grub.enbug.org/Manual](http://grub.enbug.org/Manual)

Obviamente en inglés.

---

