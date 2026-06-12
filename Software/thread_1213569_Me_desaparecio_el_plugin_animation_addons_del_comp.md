---
title: "Me desaparecio el plugin animation addons del compiz"
date: 2009-07-15
forum: Software
---

### Post by matias_tati on 2009-07-15
Hola ayer misteriosamente desparecio la opcion del plugin animation add-ons en el compiz lo desinstale y lo vlvi a instalar y sigue igual. Ahora no tengo la animacion del avioncito de papel ni de la ventana que se quema. Directamente no me aparece el icono en el administrador de opciones compizconfig. Si alguien sabe le agradezco

---

### Post by matias_tati on 2009-07-16
Nadie sabe que paso aqui lei por ahi que uno tuvo un problema con java yo recuerdo que instale el jdownloader y mas o meos desde ahi que no veo est plugin.

---

### Post by guillermolisi on 2009-07-16
> **matias_tati said:**
> Nadie sabe que paso aqui lei por ahi que uno tuvo un problema con java yo recuerdo que instale el jdownloader y mas o meos desde ahi que no veo est plugin.
Fijate si es este el thread que recordas:

[http://ubuntuforums.org/showthread.php?t=1172043&highlight=jdownloader](http://ubuntuforums.org/showthread.php?t=1172043&highlight=jdownloader)

---

### Post by matias_tati on 2009-07-16
> **guillermolisi said:**
> Fijate si es este el thread que recordas:

[http://ubuntuforums.org/showthread.php?t=1172043&highlight=jdownloader](http://ubuntuforums.org/showthread.php?t=1172043&highlight=jdownloader)

Si pero a mi es distinto lo que me pasa o parecido en todo caso yo instale java sun como hago para probar si es ese el problema en todo caso pero no quiero resignar e uso del jdownloader tampoco. gracias.

---

### Post by NickCis on 2009-07-17
El problema con el java, es que a veces vos usando el compiz de window manager ves mal las cosas del java.

Si tu problema es que del menu de configuracion de compiz te desaparecio un add on, no tiene nada que ver con el java. 
Proba instalando de vuelta los plugins: "sudo apt-get --reinstall compiz-plugins"

saludos.

---

### Post by matias_tati on 2009-07-17
Me ira esto:

[IMG]http://img291.imageshack.us/img291/294/pantallazomatiasmatias.png[/IMG]

---

### Post by Hei Ku on 2009-07-17
El comando es:
```

sudo apt-get install --reinstall compiz-plugins

```

---

### Post by matias_tati on 2009-07-17
Sigue sin aparecer mas quiero el efecto de quemar. Tendre que reinstalar todo de cero?

[IMG]http://img515.imageshack.us/img515/4259/pantallazoadministrador.png[/IMG]

---

### Post by matias_tati on 2009-07-20
Hola ahora note que me tira un cartel que desaparece al toque al momento de reiniciar el equipo dura unos segundos abtes de que reinicie asi que me costo trabajo de reiniciar varias veces pero lo pude copiar. Dice asi:

[COLOR=Blue]Warning: Screen isn´t composited. Please run compiz (fusion) or another compositing manager.[/COLOR]

Y estas son imagenes de mi problema, para que quede mas claro. Gracias

---

### Post by staar on 2009-07-20
de tu problema ni idea, pero de ese aviso no te preocupes, es porque compiz se cierra antes que AWN, y este último necesita del primero (o de otro programa que haga composite) para funcionar, nada serio...

saludos

---

