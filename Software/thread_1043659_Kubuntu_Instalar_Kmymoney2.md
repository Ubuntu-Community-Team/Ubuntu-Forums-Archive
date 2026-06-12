---
title: "Kubuntu: Instalar Kmymoney2"
date: 2009-01-18
forum: Software
---

### Post by sergiom99 on 2009-01-18
Hola gente, 
bajé e instalé KmyMoney2. Tenía ganas de probarlo y ver que tal, sabiendo que Hei Ku es desarrollador del mismo le tengo bastante fe.
Bajé la versión 0.9.2-1 del site, lo compilé e instalé sin problemas.
Cuando lo inicié por primera vez, me apareció un Asistente para configurar algunos datos y ahí ya me "faltó" algo: hay para seleccionar tipos pre-definidos de cuentas, por paises, y no hay nada de Argentina.

Pero lo mas grave es que no puedo cambiar el idioma. Voy a "Help\Switch Application Language" y sólo me aparece para elegir "American English"
Vi que Alvaro hizo la traducción al español de Argentina, pero no se como cambiarlo.
Hei Ku, como puedo hacerlo? Me falta bajar algo más? El lenguaje del Kubuntu es Castellano\Argentina.

Gracias!

---

### Post by Hei Ku on 2009-01-18
los tipos pre-definidos de cuentas es algo que me falta traducir.

En cuanto al idioma, es raro. Te aparece todo en ingles, o mitad y mitad? Porque el Kubuntu trae en realidad todo puesto para español, asi que KMyMoney toma la traduccion española, que no estaba muy completa.

---

### Post by sergiom99 on 2009-01-18
todo el kmymoney en inglés.
Y como idioma para elegir solo American English.

---

### Post by Hei Ku on 2009-01-18
Es raro porque eso en realidad llama a un dialogo de KDE.

Probá de desinstalarlo e instalarlo desde acá, que es un paquete armado para Kubuntu.

[https://edge.launchpad.net/~claydoh/+archive](https://edge.launchpad.net/~claydoh/+archive)

---

### Post by sergiom99 on 2009-01-18
si lo instale desde el tar.bz2, cual es la mejor manera de desinstalarlo?

---

### Post by Hei Ku on 2009-01-18
En la misma carpeta de donde lo instalaste, pone "sudo make uninstall"

---

### Post by sergiom99 on 2009-01-18
Gracias! Ahora si quedo OK, la mayor parte en español (solo Español, no Español Argentina o algo asi) como habias dicho.
(Puedo ayudarte de alguna forma a terminar de traducirlo?)

PS: No se porque no funcionan hoy, asi que te debo una medallita.

---

### Post by Hei Ku on 2009-01-19
Podes probar arrancarlo de esta manera:

kmymoney --lang=es_AR

Ahi va a utilizar el español/argentino.

Y sí, siempre hace falta ayuda, si estas interesado. Es solo sentarse con el KBabel y traducir lo que falta.

---

### Post by sergiom99 on 2009-01-19
> **Hei Ku said:**
> Podes probar arrancarlo de esta manera:

kmymoney --lang=es_AR

Ahi va a utilizar el español/argentino.

Y sí, siempre hace falta ayuda, si estas interesado. Es solo sentarse con el KBabel y traducir lo que falta.

Ahora parece que si arranco en español.
gracias!

PS: Le pego una mirada al Kbabel.

---

