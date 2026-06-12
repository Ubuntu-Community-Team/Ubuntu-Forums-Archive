---
title: "problema con flash y juegos y videos en facebook"
date: 2009-06-04
forum: Software
---

### Post by pennyhume on 2009-06-04
bueno, paso a explicar..tengo el ultimo ubuntu, creo que es 9.04...instalado con wubi como una aplicacion en windows...tengo un problema con flash..me pasan las siguientes cosas...

-cuando entro a una pagina por ejemplo con menues de navegacion en flash, veo el loguito de flas, cuando hago click, me sale un loguito como de play, y ahi al hacer click nuevamente puedo ver las cosas en flash..

-en facebook..me pasa que por ejemplo si intento entrar a un juego, me sale el mismo loguito de flash pero al hacer click, se me queda el sector de la pantalla en que va el juego en un azul oscuro y no hace nada...

-en facebook tambien, cuando quiero ver un video cargado en facebook, no como enlace de youtube..me dice que no esta disponible, que fue quitado, cuando se que desde otra pc todo el mundo lo ve.

Probe con los que me comentaron de instalar los extras restringidos de ubuntu..pero sigue igual..

si me falto alguna info diganme..al que me responda desde ya gracias, y le agradeceria si puede ser claro, y no da por sentado cosas sobre ubuntu, porque sinceramente soy muy nueva en esto, y me tire de cabeza digamos porque tampoco tengo grandes conociemientos sobre computacion o eso..

---

### Post by anarko on 2009-06-04
Debes tener instalado algun plugin de Firefox para reproducir flash alternativo al oficial de Macromedia, proba desde el synaptic ( Sistema -> Administracion -> Gestor de paquetes synaptic ) buscar todo lo referente al flash y desinstalarlo, luego instalar el pluguin oficial de flash desde ahi mismo en el synaptic que se llama adobe-flashplugin ( version 10.0.algo.algo )

PD: cualquier cosa chifla, vuelvo en un rato :p

---

### Post by juancarlospaco on 2009-06-04
Tenes instalado el Flash-Block, que como su nombre indica, bloquea los flash, 
yo lo uso pero es gusto personal, fijate en tu Synaptic y busca Flash Block y desinstalalo.

---

### Post by pennyhume on 2009-06-05
bueno vamos mejorando...desinstale ese block flash, y cuando entro a una pagina con flash no tengo que hacer click para ver los flash..pero los jugos de face siguen igual..no es algo tan terrible ya que no soy muy adicta a jugar ni nada..pero me gustaria solucionarlo..ahora cuando entreo directamente me aparece el sector de la pantalla en azul..
tengo instalado supuestamente el plugin de adobe..

---

### Post by SlowEmotion on 2009-06-22
> **pennyhume said:**
> 
-en facebook tambien, cuando quiero ver un video cargado en facebook, no como enlace de youtube..me dice que no esta disponible, que fue quitado, cuando se que desde otra pc todo el mundo lo ve.

Eso me esta dando una bronca terrible locoooooooo!!!! que bronca no poder ver los videos hosteados en facebook!

Instale la version 9.4 netbook de Ubuntu.. y estoy mas que chocho porque al fin no hay ningun otro sistema operativo mas que el... vengo luchando con muchos problemitas y solucionandolos de a poco googleando mucho ^^

Pero esta me vencio.. Alguien logro solucionar este problema?

Saludos, y muchas gracias por tanta ayuda este foro es genial :popcorn:

---

### Post by dirty fingers on 2009-06-22
A mi me anda. Con un rendimiento de ****** pero logre que todo lo flash funcionara en firefox instalando desde la pagina de adobe el plugins.

---

### Post by Huno129 on 2009-07-03
Hola, yo tenia el mismo problema, eh hice lo siguiente... ya que, se tiene problema con los plugins flash libres. 

sudo aptitude remove flashplugin-nonfree gnash gnash-common ubufox

luego intales el flash de adobe flash (privativo). y eso soluciono el problema...

---

