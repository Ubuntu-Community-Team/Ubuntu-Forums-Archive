---
title: "Firefox 3 re lento solusionado"
date: 2008-12-31
forum: Software
---

### Post by javier-2714 on 2008-12-31
No se si alguien mas le pasa pero firefox 3 me andaba re lento había paginas que no abría se me quedaba colgado no abría etc un desastre me baje opera es pasable pero no me gusta así que se me ocurrió desinstalarlo firefox desde sinaptic luego busque en forma manual todo lo que había en el sistema con la palabra firefox y mozilla hay muchas cosas que quedan y las elimine una por una después me descargue firefox desde la pagina [http://www.mozilla-europe.org/es/firefox/](http://www.mozilla-europe.org/es/firefox/)  tengo dos máquinas una con feisty y la otra hardy primero en hardy no esta opt cree el directorio y le di permisos de lectura y escritura esto para que se actualice solo sin problemas lo descomprimí en este directorio , cree un enlace simbólico  “sudo ln -s /opt/firefox/firefox  /usr/bin” luego los lanzadores en el escritorio instale flash player 10 les puedo asegurar en las dos máquinas es impresionante la diferencia que hay vuela y abro 4 pestañas youtube clarin gmail yahoo y perfecto ningún problema ya lo ice en barias máquinas mas me dio muy buenos resultados con respecto a los plugin los busque antes de desinstalarlo y los copie en una carpeta luego los copie en opt/firefox plugin y funcionan sin problemas lo mismo con thunderbird espero que les sirva a mi me soluciono el problema.
si alguien necesita los plugin se los paso pesan 13 mb.

---

### Post by Hei Ku on 2008-12-31
No se te ocurrio desinstalarlo con --purge para que borre realmente todo?

PD: Movido a Software

---

### Post by javier-2714 on 2008-12-31
Si pero igualmente hay cosas que quedan no se por que por ejemplo usr/lib/mozilla y otra seguia quedando no se borraban.

---

### Post by Cristiandley on 2009-01-01
A mi me pasaba algo parecido....pero despues de una noche que deje descargando las actualizaciones e instalarlas, corrio y volvi a navegar comunmente. (Me pasaba que tardaba mucho y el scroll del mause se re tildaba al bajar por web's)

---

### Post by Hei Ku on 2009-01-01
Probablemente te haya faltado desinstalar otro paquete ademas de firefox. Cosas como el xulrunner son utilizadas por varios programas, asi que no lo desinstala si le mandas a sacar firefox solamente.

Lo que digo es que con ese metodo tenes muchas posibilidades de tener problemas durante la siguiente actualizacion. Entiendo tu motivacion, pero hiciste algo a las apuradas y sin entender por qué lo hacías. Podés tener problemas a futuro, y es parte de lo que vas aprendiendo. El tema es que le recomiendes a otros que hagan algo que no está bien, y entonces ahí otros también van a tener problemas. Y eso ya no me gusta.

---

### Post by javier-2714 on 2009-01-01
Esto lo hice hace 3 meses y con la versión 3.04 y se actualizo perfecto igual que thumderbird yo soy un usuario normal pero lo probé bien andes de "recomendarlo"mas que esto quise contar mi experiencia  por ahí vos tenes muchos mas conocimientos cosas que yo no conozco por ahí de seguridad pero a mi me soluciono el problema y lo uso bastante no me dio ningún problema igualmente es una opción que yo probé y cambia terriblemente párese otro navegador el desempeño no se la parte mas técnica digamos bueno esta es mi experiencia saludos.

---

### Post by Hei Ku on 2009-01-01
Entiendo tu punto, pero estás rompiendo la integridad del gestionador de paquetes sin una buena razón, y sin saber realmente lo que estás haciendo. Sólo hiciste algo, y tu evidencia anecdótica muestra que te funcionó, pero no sabes por qué.

Más allá de todo, te agradezco la intención del aporte. Solamente estoy en desacuerdo que alguien siga tu recomendación.

---

### Post by fedeavila on 2009-01-01
Yo "ahora" tengo ese problema... Con Firefox... Pero me di cuenta que es Flash solamente el que hace que se ponga lerdo... Y tengo una buena maquina (AMD Athlon64 X2 2.2GHz con 2GB RAM). Me bajé el Opera para comparar pero cuando quiero jugar algun jueguito de los de Playfish me sale como la pantalla corrida para la izquierda... Máximo dos pestañas puedo tener abierto, y no tengo plugins ni themes ni extensiones ni nada... 

Todavía estoy a la espera de que una actualización milagrosa lo arregle :P

_PD:_ Feliz año para todos! En especial a "**Hei Ku**" a ver si para este 2OO9 le ponemos un poco de mejor onda a las respuestas jajja

---

### Post by Hei Ku on 2009-01-01
Flash es un problema. Siempre lo fue, y seguira siendolo. Defective by design.

Y el tema es que si vos das esa clase de consejos, los que vamos a tener que dar soporte despues somos nosotros. Mala onda hubiera sido cerrarte el thread. Lo único que hice fue dejar bien en claro que este consejo esta mal.

---

### Post by fedeavila on 2009-01-01
> **Hei Ku said:**
> Flash es un problema. Siempre lo fue, y seguira siendolo. Defective by design.

Y el tema es que si vos das esa clase de consejos, los que vamos a tener que dar soporte despues somos nosotros. Mala onda hubiera sido cerrarte el thread. Lo único que hice fue dejar bien en claro que este consejo esta mal.

Lo que haga con el thread me tiene sin cuidado Sr. **Hei Ku**, yo no fui el que lo creó, jamás aconsejé seguir los pasos de **javier-2714**; de hecho si tuviera que dar uno sería más bien para ud; póngale más onda a sus comentarios. Nada más que eso!

Es que vengo leyendo los otros threads y denoto un tono un poco amargo de su parte... Será la dieta?

---

### Post by Hei Ku on 2009-01-01
Tenés razon, me confundí. No fuiste vos el que dio el consejo. En cuanto a la dieta, no sé a qué te referís. :D

---

### Post by M_NUS on 2009-01-06
que exeso de faltas ortograficas!

de todos modos esta bueno el aporte para adentrarse en como se podria "solucionar" un problema de soft en ubuntu.

---

### Post by kornykyano on 2009-01-10
Para redondear, con...
```
sudo apt-get remove --purge firefox
```Firefox queda **_totalmente_** desintalado? o que dan rezagos en alguna parte..

---

### Post by Hei Ku on 2009-01-10
Hay dependencias que puede o no sacar, dependiendo si la usa otro programa. Un ejemplo de eso es el xulrunner, que es un motor de mozilla.

```

Depends: debianutils (>= 1.16), fontconfig, libatk1.0-0 (>= 1.20.0), libc6 (>= 2.4), libcairo2 (>= 1.6.0), libgcc1, libglib2.0-0 (>= 2.12.0), libgtk2.0-0 (>= 2.12.0), libnspr4-0d (>= 1.8.0.10), libpango1.0-0 (>= 1.20.1), libstdc++6 (>= 4.1.1-21), psmisc, xulrunner-1.9 (>= 1.9.0.1)

```
Si tenes thunderbird, el xulrunner va a seguir instalado, se entiende?

---

