---
title: "Problema re loco, una página enloquese a mi ubuntu"
date: 2011-12-28
forum: Software
---

### Post by N3RI on 2011-12-28
Esto es muy loco, entro a la página [www.minijuegos.com]("http://www.minijuegos.com") y mi ubuntu se vuelve loco, le pasa esto:

[[IMG]http://i.imgur.com/fyXNQs.png[/IMG]]("http://imgur.com/fyXNQ")


[[IMG]http://i.imgur.com/l1s3Ts.png[/IMG]]("http://imgur.com/l1s3T")

[[IMG]http://i.imgur.com/XeuZbs.png[/IMG]]("http://imgur.com/XeuZb")

[[IMG]http://i.imgur.com/Fn7w7s.png[/IMG]]("http://imgur.com/Fn7w7")

y tengo que reiniciar, porque cerrando sesión sigue pasando, también reiniciando X. 

No me ha pasado con otras páginas.

---

### Post by guillermolisi on 2011-12-28
Posiblemente tenga que ver con Java. En la ultima actualizacion se desinstalaba Java porque Oracle le cambio la licencia a ese producto.
En su reemplazo hay que instalar la version libre.

Cual de las dos alternativas estas usando ?

---

### Post by jeros1712 on 2011-12-29
Es muy cierto lo de java, pero veo que las barras del panel tambien fallan ? podria ser un problema de video...esa web esta super cargada de animaciones y puede saturar....


Yo he tenido problemas similares por placas de video que calentaban

---

### Post by guillermolisi on 2011-12-29
Pueden ser muchas mas cosas, fuente inclusive. Pero mi supuesto partio de lo que expusiste respecto de cuando ingresas en minijuegos.com

---

### Post by N3RI on 2011-12-29
> **jeros1712 said:**
> Es muy cierto lo de java, pero veo que las barras del panel tambien fallan ? podria ser un problema de video...esa web esta super cargada de animaciones y puede saturar....


Yo he tenido problemas similares por placas de video que calentaban

si, falla todo, el escritorio se ve igual, cierro sesión y el menú de inicio de sesión se ve igual de mal, todo. 

No me ha pasado con ninguna otra página, ni viendo pelis ni nada; pero entro a esa página y se enloquece.

---

### Post by juancarlospaco on 2011-12-29
Veo una placa de video sobrecalentada en tu futuro...
:)

---

### Post by mama21mama on 2011-12-29
Comparto en lo que dice juancarlospaco.

Teste el sensor de la placa de video a ver que temperaturas alcansa.

Si es una desktop, le llego la hora que la abras a ver si giran los cooler y desempolvarla.

Si...trata siempre de usar el privativo driver de tu placa de video si es la ultima version mejor.

Luego de todo esto....
Comenta a ver como te fue.

---

### Post by jeros1712 on 2011-12-30
> **juancarlospaco said:**
> Veo una placa de video sobrecalentada en tu futuro...
:)

> **mama21mama said:**
> Comparto en lo que dice juancarlospaco.

Teste el sensor de la placa de video a ver que temperaturas alcansa.

Si es una desktop, le llego la hora que la abras a ver si giran los cooler y desempolvarla.

Si...trata siempre de usar el privativo driver de tu placa de video si es la ultima version mejor.

Luego de todo esto....
Comenta a ver como te fue.


para agegar una pista mas ... si es una placa de video onboard, revisa el mother a ver si no tenes capacitores inchados...mira con mucho cuidado los que esten a la izquierda de tu micro...otra cosa mas, si es una de estas placas de video de la nueva generacion que vienen con una alimentacion extra de 4 pines tambien deberias considerar revisar la fuente ;)

---

### Post by N3RI on 2011-12-30
Cosas que probé:  en Windows 7, firefox, misma placa (nvidia gforce 9500 GT) NO PASA NADA RARO  en Ubuntu, firefox, distinta placa (onboard) NO PASA NADA RARO  en Ubuntu, misma placa, pero con Chromium NO PASA NADA  o sea, el problema es en ubuntu, en firefox, con la plaga nvidia, y sólo con el sitio [www.minijuegos.com](www.minijuegos.com).  El hardware está bien, no calienta, está limpio el cooler y gira silencioso y tranquilo.  Instalé los addons Flashblock y NoScript y ahora al entrar a minijuegos, pestañea la pantalla un segundo, pero no se vuelve loco como antes.  El tema es que aparentemente NoScript no me deja elegir qué scripts dejar que ejecute y qué no, por lo que no sé cuál es el que da problemas. Sólo dice que bloqueó 19 scripts y 0 objetos. Tengo que fijarme si me deja elegir qué bloquear y qué no, para ir afinando más la búsqueda hasta encontrar el culpable.  Pero evidentemente hay un script que enloquece a mi pobre Ubuntu.

---

### Post by N3RI on 2011-12-30
jajaja terminé de escribir eso, pasé a la pestaña de minijuegos y se enloqueció todo, con Noscript y FlashBlock instalados, pasa igual.  No sé qué pensar.  EDIT: bueno, probé un par de veces más, ahora con estos bloqueadores activados, entro a la página y directamente se cuelga, se freeza, no responde más ni al teclado ni al mouse y la imagen en la pantalla queda congelada. O sea, que es peor.

---

### Post by N3RI on 2011-12-30
> **mama21mama said:**
> Comparto en lo que dice juancarlospaco.

Teste el sensor de la placa de video a ver que temperaturas alcansa.

Si es una desktop, le llego la hora que la abras a ver si giran los cooler y desempolvarla.

Si...trata siempre de usar el privativo driver de tu placa de video si es la ultima version mejor.

Luego de todo esto....
Comenta a ver como te fue.

 Uso el driver privativo. El sensor da bien la temperatura, es una desktop que tiene coolers por todos lados y la limpio regularmente, no tiene polvo.

---

### Post by N3RI on 2011-12-30
> **guillermolisi said:**
> Posiblemente tenga que ver con Java. En la ultima actualizacion se desinstalaba Java porque Oracle le cambio la licencia a ese producto.
En su reemplazo hay que instalar la version libre.

Cual de las dos alternativas estas usando ?

 vos decís que tiene que ver con java? pero si la página no tiene applets de java (al menos no en su home). Tengo instalada la versión free.

---

