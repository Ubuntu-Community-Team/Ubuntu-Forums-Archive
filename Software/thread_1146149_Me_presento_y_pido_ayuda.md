---
title: "Me presento y pido ayuda"
date: 2009-05-02
forum: Software
---

### Post by maty_pincha on 2009-05-02
Buenos dias gente del foro, me presento, me llamo matias. Soy bastante nuevo en esto de linux, si bien hace unos años tuve en una pc una particion con mandriva, por problema economicos duró poco, ya que tuve que vender la pc.

Ahora, despues de algun tiempo vuelvo con ganas de instalar Ubuntu. pero tengo un problema. al iniciar con el CD (que cree con la iso que bajé de la pag oficial, segun veo es la version8.04), arranca normalmente, pero se empieza a enlentizar la cosa. a tal punto que todo tarda y tarda, pero al menos avanza. Pasa lo de la ubicacion, pasa lo del teclado y se "moria" hasta que llega a la parte que uno debe elegir como particionar.

Les comento que se trababa mas y ni llegaba a esto, o mejor dicho me cansaba y apagaba la pc despues de varias horas de que iba a avanzando la barra de % pero que nunca llegaba a terminar; pero leí en un lado que alguien puso en los parametros de boot el siguiente codigo antes de elegir la manera de instalar:  pnpbios=off acpi=off noapic

Con este codigo la cosa anduvo mas rapido, pero igualmente se trababa y nuedo finalizar la instalacion.

Ayuda por favor, soy muyy nuevo en linux. Será problema de Hard? (Sempron algo viejito, 256 MB ram, que corria xp sin problemas), será problema de la iso que bajé? (por las dudas estoy bajandola nuevamente otra vez).

Saludos y gracias!

---

### Post by guillermolisi on 2009-05-02
> **maty_pincha said:**
> Buenos dias gente del foro, me presento, me llamo matias. Soy bastante nuevo en esto de linux, si bien hace unos años tuve en una pc una particion con mandriva, por problema economicos duró poco, ya que tuve que vender la pc.

Ahora, despues de algun tiempo vuelvo con ganas de instalar Ubuntu. pero tengo un problema. al iniciar con el CD (que cree con la iso que bajé de la pag oficial, segun veo es la version8.04), arranca normalmente, pero se empieza a enlentizar la cosa. a tal punto que todo tarda y tarda, pero al menos avanza. Pasa lo de la ubicacion, pasa lo del teclado y se "moria" hasta que llega a la parte que uno debe elegir como particionar.

Les comento que se trababa mas y ni llegaba a esto, o mejor dicho me cansaba y apagaba la pc despues de varias horas de que iba a avanzando la barra de % pero que nunca llegaba a terminar; pero leí en un lado que alguien puso en los parametros de boot el siguiente codigo antes de elegir la manera de instalar:  pnpbios=off acpi=off noapic

Con este codigo la cosa anduvo mas rapido, pero igualmente se trababa y nuedo finalizar la instalacion.

Ayuda por favor, soy muyy nuevo en linux. Será problema de Hard? (Sempron algo viejito, 256 MB ram, que corria xp sin problemas), será problema de la iso que bajé? (por las dudas estoy bajandola nuevamente otra vez).

Saludos y gracias!
Queres instalar desde la sesion que arma el Live-CD ?
Con 256Mb RAM mi recomendacion es hacer una instalacion directamente del CD, sin iniciar una sesion Live ya que eso te consume memoria y la recomendacion para esos casos es minimo 384Mb RAM, algo mas de los 256 que tenes.

Tambien puede ser que el CD no este grabado para que la lectora lo puede "digerir" sin reintentos, que podria ser parte de las demoras a medida que avanza la instalacion.

Graba los CDs a la velocidad mas baja que puedas y luego corre la opcion de revisar la consistencia del CD grabado por si algo quedo mal.

Igual en la epoca de 7.04 y 7.10 hubo casos de instalacion en maquinas con poca memoria que duraron toda una noche y parecia que el proceso se habia colgado.

---

### Post by maty_pincha on 2009-05-02
Gracias por contestar!! pero que me recomendas que haga? algo que ni dije es que la particion que tenia windows esta rota, windows no inicia.
Ni bien baje el .iso de ubuntu, lo grabo a la velocidad mas baja e intento nuevamente.
otra manera de instalarlo no hay no?

gracias.

---

### Post by nemodot on 2009-05-02
Si tenés alguna partición de windows estropeada es posible que durante la configuración para la instalación usando el live cd se vuelva muy lenta la cosa.

A mi me ha pasado eso con una partición FAT32 de windows que tenía. El menu para particionar tardaba 40 minutos en pasar a la ventana siguiente.

Podrías probar dandole un formato limpio al disco, aunque no estoy seguro que eso arregle tus problemas.

Saludos!

---

### Post by maty_pincha on 2009-05-02
ok, con format c: ? jaja no en serio, como me decis que lo haga?

De paso comento que ya bajé de nuevo y grabé a velocidad baja nuevamente el ubuntu, pero al tratar de instalarlo, paso lo mismo :? lento, lento, lento... parece muerto, inclusive la pantalla se puso negra de golpe y el cd sigue leyendo!l, sigue haci desde hace un rato :(

---

### Post by pablo.s on 2009-05-02
Para tu caso, la sugerencia es:
bajar la ISO de Alternate cd, que
tiene un proceso de instalación
por ventanitas graficas muy simples
(parece texto). Con este CD tiene
que instalar en no más de 40 minutos
total.

PD para los que digan que si es texto: 
La instalación del Alternate no es
en modo texto, está diagramado
con ncurses, que es una libreria
gráfica. Si quieren ver una instalación
en modo texto, prueben instalar
Gentoo...

---

### Post by arashiko28 on 2009-05-02
Al momento de la primera pantalla que ves, tienes varias opciones, de que si lo pruebas sin instalar, allí mismo presiona F4 o la opción que te de allí debajo y tendrás la instalación alterna sin necesidad de bajar otro CD, otra forma es seleccionar la instalación sin Live CD, lo siento, pero tienes poca RAM para el Live CD, por eso no lo logras así.
Suerte!

---

### Post by maty_pincha on 2009-05-02
> Al momento de la primera pantalla que ves, tienes varias opciones, de que si lo pruebas sin instalar, allí mismo presiona F4 o la opción que te de allí debajo y tendrás la instalación alterna sin necesidad de bajar otro CD, otra forma es seleccionar la instalación sin Live CD, lo siento, pero tienes poca RAM para el Live CD, por eso no lo logras así.
Suerte!mmm mirá presionando F4 me sale:
NORMAL
SAFR GRAPHICS MODE
USE DRIVER UPDATE CD
OEM INSTALL (FOR MANUFACTURES)

solo esas 4 opciones! pero no creo que sea alguna de ellas las que me dices ¿?¿?

---

### Post by maty_pincha on 2009-05-03
Bueno al final me bajé el Alternate cd. y arrancó perfecto, sin problemas ni demoras (bahh comparado con lo que me pasaba).
Particione, espero haberlo hecho bien, sino ya veré. Y todo arrancó perfecto luego.
Ya tengo mi Ubuntu!!!!!!!!!!!!

Gracias a todos por la ayuda y recomendaciones, igualmente no se van a salvar tan facil de que los siga molestando con algunas otras cosas... como dije, soy nuevo con linux"

Saludos!:)

---

### Post by dirty fingers on 2009-05-03
felicitaciones mati, eso es ponerle ganas !

---

### Post by faktorqm on 2009-05-05
que version de ubuntu instalaste? con 256mb de ram te conviene xubuntu 9.04 alternate. no? las particiones como las hicistE? salu2!

---

