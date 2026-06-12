---
title: "Instale KDE 4.3.2 en U 9.04 ... algunos problemas"
date: 2009-10-08
forum: Software
---

### Post by sitiomatic on 2009-10-08
Hola, desde ayer que estaba encaprichado en instalar kde en ubuntu 9.04
Hice lio, me quede sin nada, ni gnome ni kde, y despues de invertirle toda la tarde lo arregle..........ufff
Al final, me quedaron algunos problemas en Kde que me gustaria resolver si me dan una mano
1) Como desinstalo en network-manager de kde para instalar wicd (el wifi no anda con el manager)
2) kde esta en ingles y no me deja instalar otro idioma. Clickeo en instalar idioma y no pasa nada
3) Cuando instalo un nuevo widget da el siguiente error: Could not create a python ScriptEngine for the xxxx widget.
4) Cuando instalo un nuevo splash theme, dice que lo isntalo pero no se ve en donde se selecciona el tema.
Como varias cosas tienen que ver con instalaciones me quede pensando si no habra algo mal con python......ni idea.
Bueno.........esto para empezar :)
Agradecere efusivamente consejos y ayudas, me gusta mucho kde 
Saludos

Actualizo:
Corri el gestor de actualizaciones y tambien sale un error diciendo que no se puede instalar todo
Los paquetes que quedan sin marcar son:
python-qt4
python-sip4

---

### Post by faktorqm on 2009-10-08
ok, por las dudas hace

```
sudo apt-get autoremove
```

que eso te saca todos los paquetes que ya no vas a usar mas.

Para instalar el wi-cd, si es que viene en los repositorios, tengo entendido que simplemente cuando lo instalas, te instala todas las dependencias que necesita y te desintala automaticamente el network-manager. 

Para instalar el kde en español, deberias buscar un paquete que se llama o es parecido a kde-i18n-es (pone aptitude search kde de ultima y fijate por que capaz hay es-es y es-ar o es-la)

Para lo del python pueden ser 1000000 de cosas, pero yo empezaria por mirar en la misma busqueda que antes paquetes del estilo pykdeextensions o python-kde4 o algo parecido. Estos paquetes se llaman asi para la version 3 de kde, para la 4 no se por eso te digo que busques algo asi.

Del 4 ni idea. salu2!

---

### Post by emiliano_raso on 2009-10-09
A mi una vez me pasó que instalé KDE4.1 y me pedía que haga autoremove despues de instalar.

Lo hice y me desinstaló todo Gnome y sus aplicaciones. Porque? No tengo idea...

Que es lo que hace apt-get autoremove?

---

### Post by guillermolisi on 2009-10-09
> **sitiomatic said:**
> Hola, desde ayer que estaba encaprichado en instalar kde en ubuntu 9.04
Hice lio, me quede sin nada, ni gnome ni kde, y despues de invertirle toda la tarde lo arregle..........ufff
Al final, me quedaron algunos problemas en Kde que me gustaria resolver si me dan una mano
1) Como desinstalo en network-manager de kde para instalar wicd (el wifi no anda con el manager)
2) kde esta en ingles y no me deja instalar otro idioma. Clickeo en instalar idioma y no pasa nada
3) Cuando instalo un nuevo widget da el siguiente error: Could not create a python ScriptEngine for the xxxx widget.
4) Cuando instalo un nuevo splash theme, dice que lo isntalo pero no se ve en donde se selecciona el tema.
Como varias cosas tienen que ver con instalaciones me quede pensando si no habra algo mal con python......ni idea.
Bueno.........esto para empezar :)
Agradecere efusivamente consejos y ayudas, me gusta mucho kde 
Saludos

Actualizo:
Corri el gestor de actualizaciones y tambien sale un error diciendo que no se puede instalar todo
Los paquetes que quedan sin marcar son:
python-qt4
python-sip4
Fijate si tenes paquetes en conflicto, rotos, pendientes de aplicar.

Que repositorio de KDE estas usando ?

---

### Post by guillermolisi on 2009-10-09
> **emiliano_raso said:**
> A mi una vez me pasó que instalé KDE4.1 y me pedía que haga autoremove despues de instalar.

Lo hice y me desinstaló todo Gnome y sus aplicaciones. Porque? No tengo idea...

Que es lo que hace apt-get autoremove?
> te saca todos los paquetes que ya no vas a usar mas

O sea, los que el sistema ya no necesita porque hay otros equivalentes que los reemplazan.

---

