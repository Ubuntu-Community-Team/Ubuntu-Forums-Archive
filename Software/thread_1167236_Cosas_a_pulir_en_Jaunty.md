---
title: "Cosas a pulir en Jaunty"
date: 2009-05-22
forum: Software
---

### Post by losoollenos on 2009-05-22
Ante todo pido disculpas por no encontrar el foro dónde correspondería este thread.
El título dice "pulir" porque no se trata de nada grave, Jaunty anda bárbaro. Se trata de tres problemitas, los tiro juntos para ver si pueden en algún momento, ser tenidos en cuenta por desarrolladores o colaboradores, etc.
Uno es la lentitud con que funcionan las páginas que usan flash, acoto que este problema lo tengo en una máquina que uso Amd, en la que tengo Pentium funciona de 10.
Otro, ya menos molesto, es la fea impresión que da al apagar el sistema; se arma como un revuelo de cosas que se cierran de a una, algún que otro cartelito de error que no alcanzo a leer, se ve cómo muy desordenado. También aclaro que lo tengo "cargadito" al escritorio: AWN, varios screenlets, Compiz, Emerald, efectos de escritorio y creo que nada más. Si bien lo cierra rapidísimo estaría bueno que fuese algo más armónico, si cabe la expresión.
Lo último, realmente menor, que también me pasa en Hardy, es un pantallazo marrón que dura unos segundos y aparece cada cierto intervalo de tiempo. Esto seguro tiene que ver con los screenlets, específicamente con el que te da un reloj digital como fondo de pantalla, al menos eso creo.

Bueno, es mi humilde aporte a mejorar a este maravilloso so.

Saludos y gracias a tod@s !!!

---

### Post by staar on 2009-05-22
estos no son problemas de ubuntu, flash (para linux o para win) es malo porque adobe lo hace así, canonical no tiene nada que ver con su desarrollo, lo del apagado debe ser cosa de tu configuración, a mi me funciona correctamente (hay un efecto de compiz para desvanecer la pantalla al cerrar sesión) y lo del screenlet, también, es problema del screenlet, no de ubuntu...

saludos

---

### Post by losoollenos on 2009-05-22
Gracias por tu respuesta staar !!!
Lo del flash, me dijeron por acá, que se debe a que Jaunty tiene un xorg nuevo y no se lleva bien con los drivers privativos sobre Amd, que es lo que me está pasando a mi, en la otra pc me andan bárbaro; y en esta pc con Hardy también andan joya.
 Si no te jode me decís como se llama ese efecto de compiz?

Gracias y saludos

---

### Post by staar on 2009-05-22
no, no, flash es malo, independientemente de los drivers o de la placa de video...
el problema con Xorg 1.6 (la versión que viene en jaunty) una vez más no es problema de ubuntu, sino de Ati/Amd que no sacan drivers (o sacan, pero malos) compatibles con esta nueva versión del server gráfico...

el efecto de compiz creo que es el Login/Logout (por lo menos así se llamaba en intrepid con el sistema en inglés)

saludos

---

### Post by losoollenos on 2009-05-23
Lo que pasa es que anda lento igualmente antes de instalar drivers privativos (nvidia en mi caso) tambien....

Gracias y saludos

---

### Post by Hei Ku on 2009-05-23
Flash es malo. Es malo en su performance, malo en que permite y promueve tecnicas chapuceras de programacion, y malo en su seguridad.
A veces, anda de manera aceptable, pero eso solo soluciona el problema de la performance. 

Sobre los otros problemas, si nos pudieras dar datos concretos en vez de tirar generalidades, podriamos hacer algo.
De otra manera, lo pasamos a Comunidad y usamos el thread para charlar del clima. ;)

---

### Post by losoollenos on 2009-05-23
Salta a la vista pero les recuerdo que soy un usuario novato, muchos datos técnicos no se aportar, salvo que me indiques qué y cómo.
Del flash sigo sin entender (y perdón por mi cabeza dura) por qué si el problema no es de jaunty (el de la performance, de los otros aspectos obviamente, ni idea) con Amd, en Hardy, en Intrepid y en Jaunty sobre Intel funciona bien.
En relación a lo feo que cierra mucho más no tengo para decir; cuando el sistema está pelado todo bien, pero teniendo instalados awn, compiz, emerald y varios screenlets, se produce un cierre de sistema no muy logrado, que se yo, algún que otro pantallazo blanco, cartelito de error por la zona de la barra awn, el pitido interno suena a veces una otra dos veces como si algo se cerrara mal; esto al tiempo que van cerrando bruscamente los screenlets distribuidos por el escritorio sin ninguna sincronía ni atenuación o algo más progresivo, es que no les pasa?
Lo del screenlets, olvidalo, seguramente ahi se deberá corregir el screenlets. 
Son boludeces y por eso recalco lo de "pulir" estos detalles

---

### Post by pablo.s on 2009-05-23
> **losoollenos said:**
> Del flash sigo sin entender (y perdón por mi cabeza dura) por qué si el problema no es de jaunty (el de la performance, de los otros aspectos obviamente, ni idea) con Amd, en Hardy, en Intrepid y en Jaunty sobre Intel funciona bien.

El interrogante es: cuando hacés
referencia a AMD, es a 64 bits?
Si es así, vas a tener diferencias
con el reproductor Adobe Flash.
Me sumo a lo que comentan los
compañeros: Flash es una de las
tecnologías mas desastrosas que
existen.

> **losoollenos said:**
> En relación a lo feo que cierra mucho más no tengo para decir; cuando el sistema está pelado todo bien, pero teniendo instalados awn, compiz, emerald y varios screenlets, se produce un cierre de sistema no muy logrado, que se yo, algún que otro pantallazo blanco, cartelito de error por la zona de la barra awn, el pitido interno suena a veces una otra dos veces como si algo se cerrara mal; esto al tiempo que van cerrando bruscamente los screenlets distribuidos por el escritorio sin ninguna sincronía ni atenuación o algo más progresivo, es que no les pasa?

Cuando le dás la orden a la máquina
que cierre el sistema, ésta pasa al
nivel de ejecución 6, que envía la
orden kill a todos los procesos que
se están ejecutando. Depende de la
configuración de tu sistema en
particular la forma que se cierren
los procesos.

> **losoollenos said:**
> Lo del screenlets, olvidalo, seguramente ahi se deberá corregir el screenlets.

Es probable. No sabemos con precisión
que modulos tenés cargados, si son una
versión beta, la procedencia (eso importa)
y otros factores. Jaunty es un sistema
integral. Son miles y miles de aplicaciones,
no solamente Flash Player y Compiz.

---

### Post by Hei Ku on 2009-05-23
En /var/logs tenes varios logs que pueden aportar info. En particular, debes tener uno que se llame gdm.log.

A mi Flash me anda relativamente bien en Jaunty con un AMD. Ahi tenemos, anecdota contra anecdota. Mi punto es que es inestable, y a veces puede andar bien y otras mal. Tiene problemas de base que lo hacen inestable, poco seguro y pesimo desde el punto de vista de programacion. Por eso decimos que es malo.

Cuando hablas de screenlets, no mencionas cuáles. Que version de Awn tenes? Como sabes, hay varias, depende de donde lo hayas instalado.

Y parece que a otra gente no le pasa, asi que puede tratarse de un problema especifico de tu instalacion.

Mas informacion, por favor.

---

### Post by guillermolisi on 2009-05-23
> **losoollenos said:**
> Salta a la vista pero les recuerdo que soy un usuario novato, muchos datos técnicos no se aportar, salvo que me indiques qué y cómo.
Del flash sigo sin entender (y perdón por mi cabeza dura) por qué si el problema no es de jaunty (el de la performance, de los otros aspectos obviamente, ni idea) con Amd, en Hardy, en Intrepid y en Jaunty sobre Intel funciona bien.
En relación a lo feo que cierra mucho más no tengo para decir; cuando el sistema está pelado todo bien, pero teniendo instalados awn, compiz, emerald y varios screenlets, se produce un cierre de sistema no muy logrado, que se yo, algún que otro pantallazo blanco, cartelito de error por la zona de la barra awn, el pitido interno suena a veces una otra dos veces como si algo se cerrara mal; esto al tiempo que van cerrando bruscamente los screenlets distribuidos por el escritorio sin ninguna sincronía ni atenuación o algo más progresivo, es que no les pasa?
Lo del screenlets, olvidalo, seguramente ahi se deberá corregir el screenlets. 
Son boludeces y por eso recalco lo de "pulir" estos detalles
A mi no me pasa porque uso KDE4.2.3 (sin Compiz porque no me hace falta) :D

Luego, Compiz esta bonito pero parece que no anda parejo en todas las plataformas.

Se me ocurre que con Screenlets y AWN falta algo de maduracion para adaptarse a los cambios mas profundos introducidos en JJ, especialmente a la nueva version de X-server.

Si combinas todo el resultado que observas cierra con esas diferencias individuales.

En cambio KDE, con todos sus pros y contras, es algo mas integrado para lograr funcionalidades similares a lo que obtenes con Gnome y add-ons juntos (esto es una vieja historia discutida hasta el hartazgo aqui y en la lista, asi que no haria falta una revision historica con pretensiones contemporaneas).

---

### Post by staar on 2009-05-23
bueno, quedando claro que flash es malo, el tema de la performance en tu caso, está pasando por la nueva versión de xorg, y algunos cambios que se hicieron, algunos drivers de intel y ati todavía no fueron actualizados (problema de intel y ati) para esta versión, y se está reportando baja performance en 2D y 3D con los drivers actuales, asi que el tema se va a solucionar cuando las compañias responsables actualizen los correspondientes drivers (o se actualizen los drivers libres)

y lo del apagado, si, es problema de los screenlets y AWN, no de ubuntu...

saludos

---

### Post by losoollenos on 2009-05-23
Ya instalé Kubuntu 9.04 para ver solo lo del flash, pero también anda lento.....

---

### Post by guillermolisi on 2009-05-23
> **losoollenos said:**
> Ya instalé Kubuntu 9.04 para ver solo lo del flash, pero también anda lento.....
Estas usando placa de video ATI o nVidia ?

En las dos maquinas que uso con Kubuntu, ambas el mismo hardware Intel y nVidia, no tengo problemas con Flash.

---

### Post by losoollenos on 2009-05-23
-El interrogante es: cuando hacés
referencia a AMD, es a 64 bits?

Es un Athlon 64x2 5200, Jaunty 32 bit

-Estas usando placa de video ATI o nVidia ?

Nvidia 6100 on board, en la pc que que tengo Jaunty sobre Intel flash va bien, aunque el cierre del sistema es igualmente desordenado

-Cuando hablas de screenlets, no mencionas cuáles. Que version de Awn tenes? Como sabes, hay varias, depende de donde lo hayas instalado.

Instalo todo desde sinaptic en Jaunty, algunos screenlets los bajé de gnome-look. Algunos screenlets no andan muy bien, pronto cualquiera se da cuenta.

-Cuando le dás la orden a la máquina
que cierre el sistema, ésta pasa al
nivel de ejecución 6, que envía la
orden kill a todos los procesos que
se están ejecutando. Depende de la
configuración de tu sistema en
particular la forma que se cierren
los procesos.

No deberían estos paquetes que se instalan desde sinaptic configurar correctamente como cierran los procesos, que hacemos los usuarios comunes?

Gracias a todos y saludos !!!

---

### Post by guillermolisi on 2009-05-23
> **losoollenos said:**
> -El interrogante es: cuando hacés
referencia a AMD, es a 64 bits?

Es un Athlon 64x2 5200, Jaunty 32 bit

-Estas usando placa de video ATI o nVidia ?

Nvidia 6100 on board, en la pc que que tengo Jaunty sobre Intel flash va bien, aunque el cierre del sistema es igualmente desordenado

-Cuando hablas de screenlets, no mencionas cuáles. Que version de Awn tenes? Como sabes, hay varias, depende de donde lo hayas instalado.

Instalo todo desde sinaptic en Jaunty, algunos screenlets los bajé de gnome-look. Algunos screenlets no andan muy bien, pronto cualquiera se da cuenta.

-Cuando le dás la orden a la máquina
que cierre el sistema, ésta pasa al
nivel de ejecución 6, que envía la
orden kill a todos los procesos que
se están ejecutando. Depende de la
configuración de tu sistema en
particular la forma que se cierren
los procesos.

No deberían estos paquetes que se instalan desde sinaptic configurar correctamente como cierran los procesos, que hacemos los usuarios comunes?

Gracias a todos y saludos !!!
Una de las caracteristicas del Software Libre es que los entregables, sean binarios o fuentes, se dan "as is", como estan, como son al momento, y queda bajo la responsabilidad de quien usa la pieza de software hacerse cargo de sus implicancias y consecuencias. Por eso la recomendacion es utilizar software que figura en los repositorios oficiales de Ubuntu (los de Canonical) si la intencion es preservar integridad funcional y seguridad. Instalar cosas hechas por un tercero implica que pueden no adherir a los standards de empaquetamiento (resolucion de dependencias y otras yerbas), condiciones de prueba, documentacion, etc.

De todas formas es sabido que muchas veces el arreglo de algo "viejo" genera otros problemas "nuevos".

---

### Post by pablo.s on 2009-05-23
Cuando hagas cita de un
comentario, sería bueno
que lo hagas como corresponde:
cada autor y cada cita.
Sino se desvirtua todo y
se confunde quien dijo cada
cosa. Gracias.

---

### Post by losoollenos on 2009-05-23
> **pablo.s said:**
> Cuando hagas cita de un
comentario, sería bueno
que lo hagas como corresponde:
cada autor y cada cita.
Sino se desvirtua todo y
se confunde quien dijo cada
cosa. Gracias.

estuve tratando y no lo podía hacer

Gracias y saludos !!!!

---

### Post by juancarlospaco on 2009-05-23
1) **Gnash**
2) agregar **xset dpms force off** al script de apagado

---

### Post by losoollenos on 2009-05-24
> **juancarlospaco said:**
> 1) **Gnash**
2) agregar **xset dpms force off** al script de apagado

Bueno Gnash ya lo probé.......
Me aclararías un poco más el punto 2 por favor?

Gracias y saludos

---

### Post by NickCis on 2009-05-24
Deberias probar Kubuntu, que el mismo escritorio KDE, trae incluido lo que seria screenlets y todas esas cosas. Ademas el manejador de ventanas, Kwin, aunque no tenga tantos efectos de escritorio como Compiz, lo encuentro muy estable y lindo (respecto a los efectos de escritorio Default).

Yo tengo una Nvidia 7300 (pci-e), y con los drivers de privativos de Nvidia 180 (que los tuve que instalar con envy, por que el de drivers de Kubuntu me tiraba errores), anda bien y fluido. El unico problema que encontre es el programa de configuracion de Nvidia, que no puedo guardar ningun cambio por que tira un eror de algo de "parce" el "xorg.conf" y por consola dice "Fallo de Segmentacion". Pero no es problema de Ubuntu, sino de Nvidia,(ademas que podes usar las herramientas de configuracion de Kubuntu).

Saludos.

---

### Post by losoollenos on 2009-05-24
Gracias NickCis !!, si ya probé Kubuntu 9.04 como decía más arriba; el flash también va lento, antes y después de instalar drivers privativos.
Comparto con vos lo estable y bien logrado estéticamente que está Kde, también siempre que lo probé en vesiones anteriores y esta tuve alguna cuestión con los drivers nvidia similares a lo que contás.
Lo que pasa es que me fui familiarizando más con Gnome......aunque siempre pruebo también Kubuntu pero no hay "tanta" info.

Gracias y saludos

---

### Post by pol666 on 2009-05-25
la documentación disponible es la misma.  no hay diferencia entre los tutoriales de uno y otro.

---

