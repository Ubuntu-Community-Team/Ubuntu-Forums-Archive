---
title: "Volumen del microfono en Xubuntu"
date: 2009-01-10
forum: Software
---

### Post by santiagoward2000 on 2009-01-10
Hola gente!
Hoy estaba aburrido y me puse a ver si andaban todas las cosas que mi compu (Dell XPS M1330) tiene y nunca usé, entre ellas, el micrófono interno. Probé con el **gnome-sound-recorder**, y al principio no andaba. Entonces revisé el volumen con el **gnome-volume-control** y vi que todas las posibles entradas (Digital, Capture y Mux) estaban mudas. Entonces las subí, probé de nuevo, y andaba! :p
El tema es que no me guarda esta configuración, cuando volví a abrir el **gnome-sound-recorder**, estaba mudo de nuevo. ¿Alguien sabe por qué se resetea el volumen del micrófono? Con los de los parlantes no pasa.
Saludos!

---

### Post by josecuervo86 on 2009-03-19
Me pasa exactamente lo mismo. Hace tiempo que quiero hacer andar el microfono y no me lo toma

---

### Post by santiagoward2000 on 2009-03-19
> **josecuervo86 said:**
> Me pasa exactamente lo mismo. Hace tiempo que quiero hacer andar el microfono y no me lo toma

En mi caso no es que no me lo toma, es que el volumen está en mudo. Si lo subo anda, pero se vuelve a bajar cada vez que abro el **gnome-sound-recorder**. ¿Te fijaste cómo está el volumen del micrófono?

---

### Post by josecuervo86 on 2009-03-20
A mi tambien me lo toma, pero cada vez que entro en gnome-volume-control me aparece el microfonito desactivado. Y lo peor es que no me guarda la configuración. Ni en la placa de sonido onboard ni en la soundblaster que tengo ahora pude hacer andar el bendito micrófono

---

### Post by josecuervo86 on 2009-03-20
Solucionado. Para el que no pueda hacer andar el mic en una sound blaster audigy 7.1 (capaz que anda para otras placas que tienen la entrada de microfono y line-in compartidas) haga esto:

Abrís la **terminal**. Pone

```
gnome-volume-control
```

o le das doble click al parlantito de la barra de herramientas. Despues te vas a **preferencias** y marcas la casilla donde dice **Shared Mic/Line in**, que es la ultima opcion. Cerras esa ventanita y ahora te aparecio una nueva pestaña que se llama **Opciones**. Ahí seleccionas donde dice **Mic in** y listo. Ya anda el micrófono!!

---

### Post by santiagoward2000 on 2009-05-16
Aparentemente lo mío era algún problema que solucionaron en Jaunty. Ahora está andando perfecto, y el volumen se queda donde está. No estoy del todo seguro igual, porque estuve tocando bastante tratando de hacer salir el sonido por el puerto HDMI (seguro en algunos días empiezo a preguntar sobre eso), y talvez algo que toqué lo arregló, pero me parece poco probable.
Saludos!

---

