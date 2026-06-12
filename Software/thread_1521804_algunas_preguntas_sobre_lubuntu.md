---
title: "algunas preguntas sobre lubuntu"
date: 2010-07-01
forum: Software
---

### Post by joseluis on 2010-07-01
hola..estoy usando lubuntu y tengo un par de preguntas que espero puedan ayudarme a resolver.

1. No puedo ver algunos sitios con flash ¿es conveniente instalar el ubuntu-restricte-extras? si lo instalo no me relentizará el sistema ligero lubuntu?  En lugar de estos "extras", ¿como encuentro el plug in de flash en Synaptic? porque hay un par y no se cual poner.

2. la misma cuestión sobre si instalo OpenOffice ¿lo hará mas lento?

espero que puedan ayudarme, gracias

---

### Post by harryscode on 2010-07-01
> **joseluis said:**
> hola..estoy usando lubuntu y tengo un par de preguntas que espero puedan ayudarme a resolver.

1. No puedo ver algunos sitios con flash ¿es conveniente instalar el ubuntu-restricte-extras? si lo instalo no me relentizará el sistema ligero lubuntu?  En lugar de estos "extras", ¿como encuentro el plug in de flash en Synaptic? porque hay un par y no se cual poner.

2. la misma cuestión sobre si instalo OpenOffice ¿lo hará mas lento?

espero que puedan ayudarme, gracias

Hola Jose, en mi experiencia openoffice me enlenteció la pc bastante. Es un gran comedor de recursos, sobre todo para pc limitadas. Yo lo probé en un pII con 256 de ram y se noto muchísimo. Por eso sigo optando por abiword y gnumeric. Lo de flash.. ahi no te digo nada porque no probé usar nada de flash.. seguro que igual que con OO bajará el rendimiento.

---

### Post by alfplayer on 2010-07-01
En cuanto a la velocidad del sistema, creo que es más fácil probar que hacer la pregunta, teniendo en cuenta que las aplicaciones se pueden desinstalar después que son instaladas para volver al estado anterior.

Un plugin de un navegador como el de Flash no depende directamente del entorno de escritorio (como el de Ubuntu, Lubuntu, Kubuntu), por lo tanto el paquete que hay que instalar debe ser el mismo para cualquiera. Recomiendo seguir los mismos pasos que para Ubuntu (casi seguramente está explicado en un hilo anterior).

---

### Post by julicabrini on 2010-07-02
Siempre algo que instales te va a consumir mas recursos y por ende te va a andar más lento el S.O. La cosa está en probar como dice alfplayer porque hay aplicaciones que consumen más recursos que otros..

Saludos!

---

### Post by alfplayer on 2010-07-02
> **julicabrini said:**
> Siempre algo que instales te va a consumir mas recursos y por ende te va a andar más lento el S.O. La cosa está en probar como dice alfplayer porque hay aplicaciones que consumen más recursos que otros..

Saludos!

Si está pensando en la velocidad del sistema cuando **no** están ejecutando las aplicaciones hay que decir que la velocidad es casi siempre la misma, que es algo que expliqué en un hilo anterior.

---

### Post by joseluis on 2010-07-02
muy clara las respuestas. Les comento que instalé el flash tal como dicen algunas paginas y anduvo bárbaro.
También le instalé Ooo y el SO en su rendimiento general no se vio afectado. Es decir, es como si no hubiera hecho nada, al menos mientras no lo use. y aún asi, me parece (sin mucho cuidado) que anda igual aún con Ooo corriendo.
Además, por cuestion de trabajo tuve que SI O SI instalar win virtualizado con Virtual Bok, y anda mucho mejor que con Ubuntu.
Es decir, hasta ahora, el Lubuntu no redujo su perfomance a pesar de lo que instalé.

---

### Post by joseluis on 2010-07-02
> **alfplayer said:**
> Si está pensando en la velocidad del sistema cuando **no** están ejecutando las aplicaciones hay que decir que la velocidad es casi siempre la misma, que es algo que expliqué en un hilo anterior.

si..me parece que lo voy viendo así luego de estas pruebas. Ocurre que acá no pasa lo que pasa en Win, me parece

---

### Post by alfplayer on 2010-07-02
> **joseluis said:**
> si..me parece que lo voy viendo así luego de estas pruebas. Ocurre que acá no pasa lo que pasa en Win, me parece

Con Windows sucede lo mismo que con las distribuciones en mi opinión: es conveniente controlar las aplicaciones y servicios que se inician con el sistema para no dejar programas en ejecución que no se necesitan. Esto es así porque en muchos casos el desarrollador de la aplicación no conoce si la aplicación o parte de la aplicación como algunas funciones deben estar disponibles para ser accedidas rápidamentes, y esto es porque el uso de las aplicaciones varía dependiendo del usuario.

También pueden deshabilitarse drivers, pero eso puede ser hilar muy fino para un usuario principiante.

En windows además, puede estar el problema del registro de Windows contaminado, aunque no sé si es un problema serio (no creo).

---

### Post by joseluis on 2010-07-03
me refiero a que en win, me parece, instalar muchos programas engorda el regsitro y eso hace mas lento todo. Es lo que siempre experimente. Es decir, formateo el disco C, instalo win y todo ahi bien, meto un Office, y aunque no esté corriendo se ahce mas lento todo, meto un photoshop y se hace MAS lento, meto un winzip y asi lo mismo. Es lo que he experimentado. Nunca el SO Win anda igual a la media hora de haber tenido win limpito.
En cambio con linux tuve la otra experiencia. Independientemente de cuanto instala, si no corre, no lo hace mas lento. Puede hacerlo mas lento si esta corriendo.
Bueno, es lo que he experimentado yo.

---

### Post by alfplayer on 2010-07-03
> **joseluis said:**
> me refiero a que en win, me parece, instalar muchos programas engorda el regsitro y eso hace mas lento todo. Es lo que siempre experimente. Es decir, formateo el disco C, instalo win y todo ahi bien, meto un Office, y aunque no esté corriendo se ahce mas lento todo, meto un photoshop y se hace MAS lento, meto un winzip y asi lo mismo. Es lo que he experimentado. Nunca el SO Win anda igual a la media hora de haber tenido win limpito.
En cambio con linux tuve la otra experiencia. Independientemente de cuanto instala, si no corre, no lo hace mas lento. Puede hacerlo mas lento si esta corriendo.
Bueno, es lo que he experimentado yo.

No estoy al tanto, pero Photoshop y OpenOffice son justamente dos aplicaciones que cargan el inicio del sistema, Photoshop creo que instala unos servicios para chequeos de "autenticidad" y OpenOffice instala para hacer "inicio rápido".

---

