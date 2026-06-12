---
title: "[SOLVED] Menus semitransparentes :("
date: 2009-07-20
forum: Software
---

### Post by jpoeta on 2009-07-20
Mis menus en aplicaciones, etc son todos semitransparentes ya no quiero esto asi quisiera anular la acción pero no se cómo.
En opciones generales del compiz tampoco tengo la opción para reparar ese problema.
Agradesco su ayuda de antemano.
Jpoeta:P

---

### Post by Hei Ku on 2009-07-20
No es un problema, es sólo una opción de Compiz. 

Tenés el plugin de Opacidad?

---

### Post by jpoeta on 2009-07-20
Si lo tengo pero no esta activado lo active y tampoco ningun cambio gracias por el interes:D

---

### Post by jpoeta on 2009-07-20
El menu de los paneles siguen semitranparentes no se que hacer me vuelvo loco:(

---

### Post by Mauro22 on 2009-07-20
Esto??

[http://www.ubunlog.com.ar/blog/panel-y-menu-trasparentes-usando-compiz/](http://www.ubunlog.com.ar/blog/panel-y-menu-trasparentes-usando-compiz/)



Claro que tienes que hacer lo inverso.

---

### Post by jpoeta on 2009-07-21
[IMG]http://img23.imageshack.us/img23/9040/asiseveenmipc.png[/IMG]
[IMG]http://img404.imageshack.us/img404/8007/menussemitrasparentepcj.png[/IMG]

Asi se ve mi pc y no se soluciona aun gracias:(

---

### Post by guisheca on 2009-07-21
Es lo mas raro que vi en mi vida. Ahí tenés el compiz corriendo? porque si al usar metacity solo se soluciona es obvio que es un problema de compiz, y lo unico que se me ocurre es que reinicies todas las configuraciones. Pero si, al usar metacity persiste e problema, se me hace que puede estar activada la composición de ventanas de metacity.
Para usar metacity:

```
metacity --replace
```

Para volver a compiz:

```
compiz --replace
```

A ver que pasa ahí.

---

### Post by staar on 2009-07-21
si, es muy raro, como si no cargara el fondo de los menús, que tema gtk estás usando? le cambiaste algo? con otro tema sigue pasando? con aplicaciones Qt (de las que tenés a la vista, Google Earth y/o K3B) te pasa?

saludos

---

### Post by jpoeta on 2009-07-21
En metacity no tengo ningun problema hay alguna forma de reiniciar todas las configuraciones del compiz ? gracias:confused:

---

### Post by kornykyano on 2009-07-21
Che a mi me gusto como queda :)

En el administrador del compiz, en "preferencia" podras reestablecer los valores por defecto. Sino eliminado los archivos ocultos.

---

### Post by Mauro22 on 2009-07-21
Es medio largo pero a mi me funciono con otra casa de compiz.


Abri el Compiz Settings manager y anda desactivando y probando, si lo sigue haciendo lo activas de vuelta y asi..


De esta forma de tas cuenta que plugin es el que lo causa, y podes investigar mas sobre ese.

---

### Post by jpoeta on 2009-07-23
Restableci los valores por defecto del compiz y ya tengo todo en la normalidad:P

---

