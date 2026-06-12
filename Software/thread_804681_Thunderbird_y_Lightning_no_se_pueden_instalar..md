---
title: "Thunderbird y Lightning: no se pueden instalar."
date: 2008-05-23
forum: Software
---

### Post by lushnok on 2008-05-23
"no se pueden" es decir mucho.
Probé desde los repositorios, no funcionó.
Probé desde el thunder, como agregados, no funcionó.
Probé desde la terminal (no recuerdo con que comando) tampoco...

Lo que pasa es lo siguiente: instalo el lighting, reinicio el thunder y no lo abre más. Se pone la pantalla (del thunder) en negro y deja de responder.

Lo hice 2 o 3 veces ya y siempre pasa lo mismo... el caso es que necesito arreglarlo y no sé que hago mal o por donde comenzar a solucionarlo.

Es más, hasta me olvidé como cazzo lo desinstalo! RAH!

---

### Post by euzkoarima on 2008-05-23
Yo lo instalé desde el thunder (la verdad, porque no me di cuenta que estaba en los repositorios, recién con tu post me venga a dar cuenta) y anduvo, pero me acuerdo que tuve 2 problemas:

1. El tema de apariencia que tenía instalado hacía que algunas partes de lightning no se mostraran bien. Quizás te pase lo mismo pero peor. Proba de poner el tema que viene por defecto en thunder y volvé a instalar lighting a ver su así funciona.

2. Tiempo despues con todo andando (y el tema por defecto seleccionado) probé de instalar un agregado para sincronizar con un crm y otra vez tuve problemas con el lighting. Terminé desinstalando lo del crm. O sea, si no te funciona lo primero, quizás tengas otro agregado que sea incompatible.

Suerte.

---

### Post by lushnok on 2008-05-23
La macana es que ahora no puedo ni entrar al thunder, por que directamente no arranca... 
y no sé como comenzar a solucionar :S

---

### Post by Hei Ku on 2008-05-23
arrancalo desde consola, a ver que errores tira en la consola. A partir de eso podemos empezar a darte una mano.

---

### Post by lushnok on 2008-05-23
Pues,en la terminal no aparece nada, ejecuto "thunderbird", lanza el programa, el prompt (o como se llame) queda, digamos en el renglón de abajo, pero no queda disponible para ejecutar nada más. Al cerrar la terminal, se cierra tambien el thunder (y viceversa)

husmeando en sistema>administración llegué al Visor de sucesos del sistema, y se me ocurrió que desde esa "ventana" (perdón).

Ahí, veo varios logs, pero en los que encontré que "marca" los errores cuando ejecuto el thunder son "messages" "syslog" y "user.log".
Respectivamente aparecían estos errores:
messagues: May 23 22:48:06 nazareno-laptop pulseaudio[5760]: protocol-esound.c: pulsecore/protocol-esound.c: Failed to create sink input.
syslog: May 23 22:48:06 nazareno-laptop pulseaudio[5760]: protocol-esound.c: pulsecore/protocol-esound.c: Failed to create sink input.
user.log: May 23 22:48:06 nazareno-laptop pulseaudio[5760]: protocol-esound.c: pulsecore/protocol-esound.c: Failed to create sink input.

Todas cosas que, por supuesto, no cacho un fulbo por ahora.

---

### Post by faktorqm on 2008-05-25
Yo no uso thunderbird, pero al igual que con la mayoria de los paquetea de ubuntu, lo que podes hacer es un "sudo apt-get remove thunderbird --purge" y despues, vas hasta tu /home con el nautilus, y apretas "CTRL + H" Para ver los archivos ocultos. Vas hasta la carpeta ".thunderbird" o similar y la borras por completo. A partir de ahi hacés lo mismo con el lightning sea lo que fuere ese programa y tambien borras la carpeta (si es que creo una, si no no :P).

Luego reinstalas el thunderbird y te deberia andar sin el lightning, luego segui preguntando. Espero que te haya servido. Salu2!!

---

### Post by lushnok on 2008-05-27
> **faktorqm said:**
> Yo no uso thunderbird, pero al igual que con la mayoria de los paquetea de ubuntu, lo que podes hacer es un "sudo apt-get remove thunderbird --purge" y despues, vas hasta tu /home con el nautilus, y apretas "CTRL + H" Para ver los archivos ocultos. Vas hasta la carpeta ".thunderbird" o similar y la borras por completo. A partir de ahi hacés lo mismo con el lightning sea lo que fuere ese programa y tambien borras la carpeta (si es que creo una, si no no :P).

Luego reinstalas el thunderbird y te deberia andar sin el lightning, luego segui preguntando. Espero que te haya servido. Salu2!!

¿eso remueve todo el thunderbird? ergo, perdería mis mails y configuraciones y demas?
¿que es "--purge"?

Me está matando esto... please help!
Quedo pensando, y sin poder resolver, que cazzo es : May 27 02:32:17 nazareno-laptop pulseaudio[5758]: protocol-esound.c: pulsecore/protocol-esound.c: Failed to create sink input.

PD: con ctrl+H fui a la carpeta de extensions del thunder y saqué la única extensión que tenía, que era la del lightning. Puedo arrancarlo, pero no hay nada que hacer con el lightning por ahora...

---

### Post by faktorqm on 2008-05-27
ahh si perdoname, pense que no habias bajado nada. el --purge te borra el programa, las configuraciones, todo todo, los mails no se, pero muy probablemente tambien lo haga. 
Lo del pulse audio es un error que tienen todos, no te preocupes, yo tambien lo tengo, es como el error cuando apagas la compu del driver de la placa de red de nvidia (caso chipset nforceX) yo pense que lo iban a solucionar en HH, pero bueno, parece que hay que esperar.......
Esas cosas de linux..... si sacas el pulseaudio no te anda nada, si lo dejas anda mal... esas cosas de linux......

---

### Post by lushnok on 2008-05-28
No hay caso... 
debe haber algo que esté mal, pero no sé que será.
Tengo todos mis mails (migrados desde windows) y todas las cuentas configuradas y demases...
comienza a ser un tema acuciante.
Si alguien sabe algo, por favor, please, SVP, per fevore... AYDUA! HELP!

---

### Post by euzkoarima on 2008-05-29
Disculpa, hace rato que no me conecto. Podes resumir la situación para ver como podemos ayudarte?
Entiendo que los mails los tenes, lo que no podes es abrir el thunder o no podes abrir thunder+lightning

Es así?

---

### Post by lushnok on 2008-05-30
> **euzkoarima said:**
> Disculpa, hace rato que no me conecto. Podes resumir la situación para ver como podemos ayudarte?
Entiendo que los mails los tenes, lo que no podes es abrir el thunder o no podes abrir thunder+lightning

Es así?

Instalé el thunder 2.0.0.14, migré todo desde el outlook 07 que tenia en vista del otro lado (lo que me costó un huevo y medio y casi una semana... mi primera semana en ubuntu y linux). 
Cuando quise instalar el lighting 0.8 creo que es, desde el thunderbird (herramientas > agregados) lo bajó, lo instaló pero cuando reinicié ya no funcionaba más.

¿qué es "no funcionaba más"? que cuando reinicié Thunder, se colgaba... no inciaba, se ponia negro y no respondía... solo quedaba forzar el cierre.
Más arriba posteé lo único que pude ver como "error"... o algo así...
La verdad es que estoy bastante contrariado con el tema.

Por ahora uso google calendars, pero DEBERIA de poder solucionarse.

Cosas que tengo pendientes:
+ audio, por ahí anda, por ahí no. En la misma sesión.
+ se actualizó el kernel al 17 y desconfiguro el teclado, lo cuadré pero nunca encontré el mismo teclado que usaba (que es el que va)
+ hacer andar la webcam de la laptop y los botones multimedia (ya encontré un tutorial para esto para cuando tenga tiempo!)
+ que TN vuelva a andar!! que el firefox vuelva a poder ver TN!!!

---

### Post by Flechagorda on 2008-05-30
Lushnok, como va....
Te cuento que tuve el mismo problema que vos...
Si podes entrar al Thunderbird, metete y desinstala el agregado del Lightning...
La unica forma que yo encontre para hacerlo andar, es instalar el que figura en Synaptic, la version 0.7...

Si directamente no te abre el Thunderbird, lo que yo hice fue copiar las carpetas que estan en .mozilla-thunderbird 

El nombre es algo tipo 08tshg3.default
Ahi tenes las configuraciones, el almacen de mails etc etc...Fijate que adentro de esa, esta EXTENSIONS...esa yo la borre...

Despues si: sudo apt-get remove thunderbird --purge

Despues a reinstalar Thunderbird...
Una vez que termine de instalar, reemplaze la .mozilla-thunderbird por la que habia guardado antes...Obviamente sin las extensions...
Despues desde synaptic instale lightning 0.7 y la extension en español...

Y listooooooo......

Todo muy lindo, pero es verdad que no pude hacer andar la 0.8.....

Disculpa si no soy muy claro con la explicacion...

Abrazo......

---

### Post by euzkoarima on 2008-05-30
A como viene la mano, adhiero a lo propuesto por Flechagorda
La verdad no se me ocurre otra cosa.

---

### Post by lushnok on 2008-07-02
Pasados los exámenes y con más tiempo para meter los garfios al ubuntu, hice todo lo que Flechagorda recomendó.
Saldo: nada. No arranca el lightning. Primero no arranca nada y me tira un error "las versiones de light y thunder no son compatibles" lo cierro, se desabilita solo, y luego arranca sin el light.

Anexo dos pantallasos.

Flecha? alguien?

---

### Post by lushnok on 2008-09-04
> **Flechagorda said:**
> Lushnok, como va....
Te cuento que tuve el mismo problema que vos...
Si podes entrar al Thunderbird, metete y desinstala el agregado del Lightning...
La unica forma que yo encontre para hacerlo andar, es instalar el que figura en Synaptic, la version 0.7...

Si directamente no te abre el Thunderbird, lo que yo hice fue copiar las carpetas que estan en .mozilla-thunderbird 

El nombre es algo tipo 08tshg3.default
Ahi tenes las configuraciones, el almacen de mails etc etc...Fijate que adentro de esa, esta EXTENSIONS...esa yo la borre...

Despues si: sudo apt-get remove thunderbird --purge

Despues a reinstalar Thunderbird...
Una vez que termine de instalar, reemplaze la .mozilla-thunderbird por la que habia guardado antes...Obviamente sin las extensions...
Despues desde synaptic instale lightning 0.7 y la extension en español...

Y listooooooo......

Todo muy lindo, pero es verdad que no pude hacer andar la 0.8.....

Disculpa si no soy muy claro con la explicacion...

Abrazo......
Por ahí esto da algo de luz sobre el asunto?
En la consola de errores del thunder me salió esto:

No chrome package registered for chrome://calendar/skin/cal-icon32.png .

¿alguna idea? :S

---

### Post by fmsismo on 2008-09-04
Antes que nada hace un backup de tu configuración del mozilla thunderbird.
[INDENT]tar -czfv mozilla_thunderbird.tar.gz ~/.mozilla-thunderbird[/INDENT]
Así después no tenes que mandar a matar a nadie :lolflag:

La aplicación se supone que ya la tenes instalada y en algún momento anduvo.  Si es así, lo que podes hacer es mover tu perfil del mozilla y dejar que cree otro cuando lo ejecutas.
[INDENT]mv ~/.mozilla-thunderbird ~/mozilla-thunderbird-data[/INDENT]

Si te anda es que algo se pincho y tenemos que ver como recuperar tus cosas.  

Si sigue explotando, podes hacer el --purge del remove y ver de largar de vuelta.

Avisa como van resultando las cosas.

---

