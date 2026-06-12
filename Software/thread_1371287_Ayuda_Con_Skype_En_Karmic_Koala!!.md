---
title: "Ayuda Con Skype En Karmic Koala!!"
date: 2010-01-03
forum: Software
---

### Post by darkside21 on 2010-01-03
diossss alguien que tenga piedad y me ayude....la verdad es que tengo la cabeza rota de tanto pensar y buscar una solucion...recien baje skype 2.1 y luego de instalarlo voy a la configuracion de audio del mic y no logro que haga captura....solo me sale la opcion de Pulse Audio Server y mas nada quien sepa como solucionar esto se lo agradeceria bastanteee ayudenme estoy desesperado y sin saber ya donde buscar :P!!!:(
[IMG]http://img198.imageshack.us/i/jjjjg.jpg/[/IMG]


[IMG]http://img198.imageshack.us/i/jjjjg.jpg/[/IMG][IMG]http://img198.imageshack.us/i/jjjjg.jpg/[/IMG]
[IMG]http://img198.imageshack.us/i/jjjjg.jpg/[/IMG]

---

### Post by rojojuan on 2010-01-03
Probaste llamar a Skype Test Call para ver si tenés sonido?

> **darkside21 said:**
> diossss alguien que tenga piedad y me ayude....la verdad es que tengo la cabeza rota de tanto pensar y buscar una solucion...recien baje skype 2.1 y luego de instalarlo voy a la configuracion de audio del mic y no logro que haga captura....solo me sale la opcion de Pulse Audio Server y mas nada quien sepa como solucionar esto se lo agradeceria bastanteee ayudenme estoy desesperado y sin saber ya donde buscar :P!!!:(
[IMG]http://img198.imageshack.us/i/jjjjg.jpg/[/IMG]


[IMG]http://img198.imageshack.us/i/jjjjg.jpg/[/IMG][IMG]http://img198.imageshack.us/i/jjjjg.jpg/[/IMG]
[IMG]http://img198.imageshack.us/i/jjjjg.jpg/[/IMG]

---

### Post by darkside21 on 2010-01-03
tengo sonidoo...lo que sucede es que no logro configurar el mic e la eleccion de dispositivo solo me da la opcion de pulse local

---

### Post by luks911 on 2010-01-03
> **darkside21 said:**
> tengo sonidoo...lo que sucede es que no logro configurar el mic e la eleccion de dispositivo solo me da la opcion de pulse local

No configures la entrada en Skype porque tiene sólo una opción. Configurala ejecutando en una terminal gstreamer-properties y andá cambiando las opciones y usando el botón test hasta que logres capturar sonido. También, si tenés más de una fuente de captura de audio, podés cambiarla yendo a Sistema > Preferencias > Sonido y tocando las opciones de las pestañas Hardware y Entrada.
Una vez que con el botón test logres capturar sonido desde la entrada que deseas y lo dejes seteado, Skype va a funcionar.
Y lo que te decían más arriba es que en Skype podés llamar a Echo Sound Test Service para probar que funcione.

---

### Post by darkside21 on 2010-01-03
la verdad es que e investigado de todo en internet y no he logrado encontrar una solucion a mi problema e hice cientos de llamadas de pruebas tanto asi que hasta sin sonido me quede por andar probando todo y nada...espero que tu solucion ayude la pruebo y aviso...gracias!!

---

### Post by leonardomdq on 2010-01-04
Lamentablemente esta en fase Beta Skype todavia, lo uso pero tiene sus problemas...

Saludos
Leonardo

---

### Post by darkside21 on 2010-01-05
como lograste que te andara el mic???!?!

---

### Post by rojojuan on 2010-01-05
> **darkside21 said:**
> como lograste que te andara el mic???!?!

Probaste lo que te dice luks911? Tenés que darle más potencia allí al mic

---

### Post by darkside21 on 2010-01-05
he hecho de todooooo y nadaaa :p...si alguien de ustedes lo tiene funcionando digame los pasos que hiso a ver si me falta algo!!

---

### Post by leonardomdq on 2010-01-05
Date una vuelta por aca , creo que es tu problema
[http://www.guia-ubuntu.org/index.php?title=Skype](http://www.guia-ubuntu.org/index.php?title=Skype)

Saludos

---

### Post by luks911 on 2010-01-05
Perdón que insista, pero ¿pudiste capturar sonido con la prueba de gstreamer-properties o con otro programa como el Grabador de Sonidos?
Porque si no pudiste, 1) hay un problema con alguna configuración de las preferencias de sonido y no lográs dar con la adecuada, o 2) si probaste todas las combinaciones posibles hay un problema con el hard, para lo que vendría bien saber qué máquina es y un lspci para saber si hay algo que se pueda hacer para que funcione el mic.

---

